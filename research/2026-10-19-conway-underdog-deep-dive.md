---
title: "Conway Research / Underdog：个人本地 Agent 的产品、模型与执行架构"
date: 2026-10-19
type: technical-research
status: published-research
topics: [personal-agent, on-device-ai, inference-engine, browser-use, BOX-AI]
sources_checked: 2026-10-19
---

# Conway Research / Underdog：个人本地 Agent 的产品、模型与执行架构

> **核心判断**：Underdog 真正的差异化不是“本地聊天”，而是把 **个人工作流、任务专用的小模型、模型专用推理引擎、隐私与商业闭环** 尝试纵向打通。但公开资料尚不足以证明其具备成熟的持久任务、跨设备执行或可审计安全 Harness。

**证据等级**：A = 官方产品/技术文档或可检查模型卡；B = 当事人采访/官方自测，尚未独立复现；C = 根据公开线索推断。涉及性能的数字均为供应商自测，不构成第三方独立评测。

## 1. 公司、产品与商业模式

- Conway Research 的公开定位是构建高效率模型、推理引擎与设备端个人 AI；首款产品 Underdog。资料：[Conway 官网](https://conway.tech/)（A）。
- **2026-10-02**：a16z 发布投资文章，明确公开投资 Conway，创始人为 Sigil Wen。[a16z](https://a16z.com/announcement/investing-in-conway-the-creator-of-underdog/)（A）。
- **2026-10-06**：TechCrunch 报道 Underdog 邀请制 beta，Mac/Windows PC 可用，Linux/iPhone/Android 在当日报道时为规划方向。[TechCrunch](https://techcrunch.com/2026/10/06/silicon-valleys-ai-wunderkind-launches-underdog-the-most-private-instinct-muse-competitor-yet/)（B；后续平台状态可能变化）。
- 出资人还包括 Khosla Ventures、Hummingbird、SV Angel、Anthology Fund 及个人投资者。**Anthology Fund 是 Anthropic 与 Menlo Ventures 的合作基金，不应直接等同于 Anthropic 主体领投**。（B）
- 商业模式设想为前期免费、无广告、设备端承担主要推理成本，后续对经 Agent 完成的购物交易收取小额分成；这仍是创始人公布的规划，实际费率与商业规模不明确。（B）

## 2. 功能能力与证据边界

| 能力 | 用户价值 | 公开证据与成熟度 |
|---|---|---|
| 本地聊天与个人上下文 | 不把每次私密对话发给云端 LLM | 官方主张/采访；未获独立端到端流量审计 |
| Email Agent | 读取、整理邮件，辅助回复 | 官方产品介绍与采访 |
| Calendar Agent | 日程管理、会议准备 | 官方产品介绍；具体 API scope 未全面披露 |
| Meeting Notes & Dictation | 会议转录、总结、任务抽取 | 官方产品介绍；Bark 语音模型仓库可查 |
| Browser Agent | 搜索、比较、网页表单及操作 | Woof Selector/Text Filler 模型卡公开 |
| PII 检测与脱敏 | 本地识别敏感信息 | PII-30M 仓库公开；**不等于已证明全产品路径强制启用** |
| 购物与支付 | 从任务执行走向可计费交易 | 商业方向明确，具体用户授权/退款闭环仍需验证 |
| 长期 Memory / 主动通知 | 跨事件推断用户需求 | 产品方向可以看到，内部 Schema、触发器和任务状态机未知 |

**不能把“模型在本地推理”推出“所有执行操作都不联网”**：Email、浏览器、支付天然依赖外部服务。

## 3. 本地模型矩阵

| 资产 | 技术角色 | 可复用性 |
|---|---|---|
| [Underdog Saluki 27B 1.0](https://huggingface.co/ConwayResearch/Underdog-Saluki-27B-1.0) | 27B 的混合 2-bit GGUF，面向推理/工具调用 | Apache-2.0；stock llama.cpp / Ollama |
| [Underdog Woof 4B 1.1](https://huggingface.co/ConwayResearch/Underdog-Woof-4B-1.1) | 小模型推理与 Agent 事务 | 以具体模型卡许可为准 |
| [Woof Selector 4B v2.1](https://huggingface.co/ConwayResearch/woof-selector-4B-4bit-v2.1) | 对浏览器状态选择动作和目标 | Apache-2.0；MLX/GGUF |
| [Woof TextFiller 0.8B](https://huggingface.co/ConwayResearch/woof-textfiller-0.8B-4bit-v2.1) | 为表单/输入动作填充文本值 | 核对模型卡 |
| [Underdog Bark 3.0](https://huggingface.co/ConwayResearch/Underdog-Bark-3.0) | 端侧语音识别能力 | 具体运行时/许可证逐项核对 |
| [PII 30M](https://huggingface.co/ConwayResearch/pii-30M-mlx-4bit-v1.0) | 28.5M 参数 BERT 标签模型，识别 PII | Apache-2.0；MLX |
| [Husky Flash](https://huggingface.co/ConwayResearch/husky-flash) | Woof 专用打包权重与 draft 模型 | 其权重遵从 Woof 授权；并非完整 Husky 引擎源码 |

这一矩阵提示 Conway 不再依赖一套通用 LLM 完成全部任务，而是按**任务难度、时延敏感度、隐私需求**组合模型。

## 4. Saluki 27B：低比特量化并保留 Tool Calling

公开模型卡称：基于 Qwen3.8-27B 的 GGUF，混合量化权重文件 **7.89 GB**，对应全精度模型文件约 **54 GB**，九项基准平均保留 **96%** 表现。文档将该文件定位为 stock llama.cpp 兼容，而非必须使用 Husky。

| 供应商测项 | Saluki | 全量 Qwen3.8 27B | 解释 |
|---|---:|---:|---|
| Tool Calling（BFCL v4 衍生，120题）| 88 | 84 | 仅 120 个任务，差距可能在抽样波动范围内 |
| Parallel Tool Calls（100题）| 42 | 35 | 约五分之一输出可能有小格式问题 |
| SWE-bench Verified（50题子集）| 30 | 33 | 不可外推至整套 SWE-bench |
| AIME 2025 avg@4 | 79.2 | 96.7 | **数学推理明显下降** |
| AIME 2026 avg@4 | 80.0 | 94.6 | 进一步说明平均保留率不能代表全部能力 |

这意味着选型时不能只看“96%”，要从**任务分布**入手：邮件/简单工具调用可以优先本地，复杂数学和高责任决策需要升级路由。

来源：[Saluki 模型卡](https://huggingface.co/ConwayResearch/Underdog-Saluki-27B-1.0)。

## 5. Husky：从通用运行时转向 MSI（Model-Specific Inference）

Husky 官方定义为针对固定模型形状优化的引擎。其优化组合：

1. **Model-shaped Metal kernels**：为 Woof 的矩阵尺寸编译专用内核；
2. **4-bit weight packing**：权重以专用 kernel 消费布局存放，减少转换；
3. **INT8 KV cache & prefix cache**：缓存布局与注意力内核匹配，跨轮复用；
4. **Prompt lookup**：文本改写任务从输入复制可验证的候选 token；
5. **Husky Flash draft**：独立草稿模型预测候选 token，主模型单次验证多个 token；
6. **GPU pipelining**：提前排队下一轮推理，减少 CPU/GPU 空等。

官方 Apple M5 Max + Woof 固定权重测试：

| 任务 | MLX tok/s | Husky Flash tok/s | 倍率 |
|---|---:|---:|---:|
| 短邮件 | 151 | 260 | 1.72× |
| 会议摘要 | 162 | 211 | 1.30× |
| 发票转 JSON | 164 | 496 | 3.02× |
| 编写函数 | 155 | 545 | 3.52× |
| 修改函数 | 163 | 730 | **4.48×** |

**4.5× 属于特定编辑任务的峰值，不是平均提速**。Flash draft 使用 Woof 内部状态训练，官方称训练数据覆盖约 13.9 万段对话。结果取自厂商特定硬件与设置，尚无公开一致性复现。

来源：[Husky 技术报告](https://husky.underdog.ai/)、[Husky Flash 模型卡](https://huggingface.co/ConwayResearch/husky-flash)。

## 6. Browser Agent：Selector / TextFiller / Harness 三段式

候选执行流程：

```text
User Task + Page Observation + Available Actions
                │
         Woof Selector 4B
     [choose operation + target]
                │
          Woof TextFiller
       [fill parameters/text]
                │
         Browser Executor
     [click/type/navigate/scrape]
                │
          Observe + Verify
                └────── back to Selector
```

模型卡明确描述 selector 负责决定**做什么、对哪里做**，filler 负责**输入什么**，浏览器 Harness 执行后读取新状态并发起下一步。

- 10 项公开浏览器任务：Selector + TextFiller **7/10 = 70%**；样本很小。
- 54 项 live-web DOM-only 任务：**26/54 = 48.1%**；使用 LLM-as-judge 判定，含反机器人阻断因素。
- 因此无需夸大为“通用电脑操作已解决”。应将失败归因拆为：感知、动作选择、参数生成、页面状态漂移、反自动化、验收器误判。

来源：[Woof Selector 模型卡](https://huggingface.co/ConwayResearch/woof-selector-4B-4bit-v2.1)。

## 7. 架构重建（公开证据 + 推断，非官方内部图）

```text
L5  EXPERIENCE     Desktop / Voice / Email / Calendar / Browser
                         │
L4  AGENT          Task Planner / Context / Memory / Routing (C: implementation not public)
                         │
L3  TOOL & POLICY  Email / Calendar / Browser Executor / Payment (policy internals not public)
                         │
L2  INFERENCE      Woof ─ Husky Flash / MLX
                   Saluki ─ llama.cpp / GGUF
                   Selector + TextFiller ─ Browser Harness
                   Bark ─ Speech       PII ─ Local Redaction
                         │
L1  DEVICE         Mac / Windows / Device Data / GPU / OS Credentials
```

**明确区分**：

- **已经公开**：模型权重/推理 Benchmark、多个任务模型、产品端侧推理主张、产品覆盖方向。
- **不能下定论**：Harness 是否 Rust、是否有 VM sandbox、Agent 与执行环境的持久绑定、Memory 后端、审批日志模式、云端执行回退、跨设备任务接力。
- **安全未证明**：PIN/PII 小模型公开不等于数据从不出设备；令牌加密亦不等于越权 Tool 无法使用。

## 8. 与 Dots、Muse、Today 的架构路线区别

| 维度 | Underdog | Dots 路线 | Muse 路线 | Today 路线 |
|---|---|---|---|---|
| 差异化 | 端侧模型与低成本推理 | 持久任务/多电脑环境绑定 | 云端个人 Agent 与长程代办 | 本地上下文主动发现 |
| 设备离线时继续跑 | 未证实普适能力 | 支持在所绑定云端环境继续 | 云端环境按服务策略运行 | 取决于实现 |
| 隐私边界 | 模型推理尽量在设备 | 视绑定执行环境、连接器权限而定 | 云端执行与服务控制 | 视本地读取和联网策略 |
| 主要风险 | 设备资源和模型质量 | 云端权限、凭证与持久化 | 云端代理外部行动 | 主动通知噪声和过度感知 |

这不是统一标准下的产品功能评分，而是**架构路线**比较。结论：本地智能和持久执行环境可以互补，无需二选一。

## 9. BOX AI 的落地建议

| 优先级 | 组件 / 任务 | 推荐实现 | 核验指标 |
|---|---|---|---|
| P0 | Local Model Router | Rust Harness 统一 llama.cpp / MLX / Cloud adapter | Tool call schema 有效率、时延 P95、失败回退率 |
| P0 | Browser Action Pipeline | Selector → TextFiller → Executor → Verifier | 端到端任务完成率、误触发率、成本 |
| P0 | Permission & Approval Gateway | allowlist、工具参数策略、审批、凭证注入、trace | 未授权动作拦截率、可核验审计链 |
| P1 | Personal Context & Memory | 文件/邮件/会议索引，Task 与 Memory 分离 | 检索准确率、数据删除与权限撤销生效 |
| P1 | Environment Binding | Task → Local / Cloud / Sandbox | 断点恢复、设备离线接力、租户隔离 |
| P2 | MSI / Flash Optimization | 优先验证模型固定时的收益，不盲目自研内核 | 实际业务分布的吞吐与端到端时延 |
| P2 | Agentic Commerce | 基于支付授权的受限交易，初期不自动付款 | 金额匹配、审批留痕、失败回滚 |

### 三项 POC

**POC-A / Saluki**：stock llama.cpp 接 7.89GB GGUF，跑 BFCL 风格工具调用 + 实际 BOX AI 工具集；与云端路由对照，不要复刻厂商自测标题。

**POC-B / Browser**：用 Selector 与 TextFiller 走 Playwright，验证动作枚举、参数 JSON schema、敏感网页屏蔽、UI 状态漂移后的重试与人工接管。

**POC-C / Personal Context**：Bark/本地 PII + 邮件/日历事件入知识索引，区分 Memory 与 Prefix Cache，只对有行动价值的事件生成建议，涉及写操作时必须审批。

## 10. 仍需证实的问题

1. Underdog Agent Harness 完整代码、运行时与进程/沙箱边界是什么？
2. 长期 Memory 存储、删除、检索及个人知识索引语义是否有可复现文档？
3. 浏览器动作选择失败后的重试、状态验收、人工接管策略是什么？
4. Husky 是否可用于第三方模型，还是只为 Woof 尺寸优化？
5. 购物支付的最终审批、凭证与退款/争议边界如何实现？
6. 手机平台与桌面平台的功能是否等价？电池、散热、前台/后台行为如何？
7. 27B 本地模型在中文邮件、国内网页、长文本合同与隐私实体识别上实际效果如何？

## 11. 关键来源

1. [Conway Research 官方主页](https://conway.tech/)
2. [a16z 投资 Conway 公告，2026-10-02](https://a16z.com/announcement/investing-in-conway-the-creator-of-underdog/)
3. [TechCrunch 创始人采访，2026-10-06](https://techcrunch.com/2026/10/06/silicon-valleys-ai-wunderkind-launches-underdog-the-most-private-instinct-muse-competitor-yet/)
4. [Conway 模型总目录](https://huggingface.co/ConwayResearch/models)
5. [Saluki 27B 模型卡与完整自测表](https://huggingface.co/ConwayResearch/Underdog-Saluki-27B-1.0)
6. [Husky 技术报告与分任务吞吐](https://husky.underdog.ai/)
7. [Husky Flash 模型卡](https://huggingface.co/ConwayResearch/husky-flash)
8. [Woof Selector 模型卡与浏览器评测](https://huggingface.co/ConwayResearch/woof-selector-4B-4bit-v2.1)
9. [PII-30M MLX 模型卡与代码](https://huggingface.co/ConwayResearch/pii-30M-mlx-4bit-v1.0)

*校验日期：2026-10-19。文中 Benchmark 属厂商自报；产品 API/支持平台/许可证可能更新。*
