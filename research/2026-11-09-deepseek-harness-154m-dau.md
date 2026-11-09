# PACK 2026-11-09 deepseek-harness-154m-dau

## 0. Meta
- Seed URL / post id: https://x.com/DeepSeekHarness/status/2119431663642153128 (official update) ; Bloomberg coverage https://x.com/business/status/2119492660926808355
- Mode: research
- Status: COMPLETE
- Time window: 2026-08-13 launch to 2026-11-09
- What was skipped: independent third-party telemetry or audit of DAU/token counts; full paid Bloomberg body (paywalled); DeepSeek internal cost or revenue figures; direct comparison runs against Claude Code / Codex agent sessions on same hardware.

## 1. Question
DeepSeek Harness 在不到三个月内自我报告的 154 万日活、每日约 92 万亿 token 与约 3.5 万第三方插件，是否构成开源 agent 基础设施对封闭实验室（Anthropic Claude Code、OpenAI Codex 等）的实质性生态挑战，抑或仍是官方 API 口径下的未验证增长叙事？

## 2. Timeline
- 2026-08-13：DeepSeek Harness v0.1 开发者预览上线，MIT 许可，GitHub 开源，基于 Cordis “一切皆插件” 架构。官方站点与 VentureBeat、Global Times 同期报道。来源：https://github.com/deepseek-ai/deepseek-harness 、https://venturebeat.com/technology/deepseek-harness-launches-as-open-source-rival-to-claude-code-alongside-v4-pro-on-api-with-higher-prices 、https://www.globaltimes.cn/page/202608/1368269.shtml
- 2026-08-27：GitHub stars 突破 20 万，创软件仓库最快纪录（15 天）。来源：star-history 分析及多家媒体。
- 2026-09-29 / 30：桌面端（macOS / Windows）发布。来源：官方 X 文章与站点。
- 2026-09-30：官方 API 用户 7 日均值约 27.1 万。来源：DeepSeekHarness 11-08 X 帖与 IT之家 11-05 报道。
- 2026-10-07：7 日均值约 42.9 万。
- 2026-10-14：约 66.5 万。
- 2026-10-17：DeepSeek-V4.1-Flash-1017 发布（与增长加速时间窗口重合）。
- 2026-10-21：约 113 万。
- 2026-10-28：约 140 万。
- 2026-11-04：单日 DAU 154 万（官方 API 口径），每日 token 约 92 万亿；MAU 约 548 万（部分中文源与图表脚注）。来源：@DeepSeekHarness status/2119431663642153128 、https://www.ithome.com/1/023/011.htm 、Yicai Global、FourWeekMBA 图表。
- 2026-11-05 晚：官方在中文渠道同步披露数据并宣布插件市场与作者支持计划。IT之家同日报道。
- 2026-11-08：英文 X 长文完整披露，Bloomberg 跟进报道。GitHub stars 约 27.6–27.7 万。

## 3. Actors
- DeepSeek / DeepSeek Harness 团队（杭州）：产品与数据披露方。激励：开源拉量、绑定官方 API 消耗、插件生态锁定、潜在 IPO 叙事。任职与股权细节未公开。
- @DeepSeekHarness（X 官方账号，约 8.3 万粉）：主要披露渠道。
- 第三方插件作者（例：woniuniuniu、op7418、bowenliang123、Phil-Fan 等）：激励为 token 补贴、流量与作品沉淀。
- Bloomberg、Yicai、IT之家、FourWeekMBA、Pandaily 等：二次报道与翻译。
- 封闭实验室对照：Anthropic（Claude Code）、OpenAI（Codex / agent 表面）——产品未开源，无公开同类 DAU。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 截至 2026-11-04，官方 API 口径 DAU 达 154 万 | https://x.com/DeepSeekHarness/status/2119431663642153128 | IT之家 https://www.ithome.com/1/023/011.htm ；Yicai Global；Bloomberg 摘要 | high（自报一致） | 独立 telemetry 或第三方审计显示显著更低 |
| C2 | 每日 token 消耗约 92 万亿（官方 API） | 同上官方帖 | 同上多家中文源 + FourWeekMBA 转述 | high（自报） | 官方更正或外部计量 |
| C3 | 第三方插件约 3.5 万个；约 60% 活跃用户创建或安装至少一款 | 官方帖列出案例 | IT之家、Yicai | med-high | 插件目录公开统计或安全审计 |
| C4 | v0.1 于 2026-08-13 上线，桌面端 09-29 | 官方历史帖与站点 | GitHub 创建日、VentureBeat 08-13、官方站点 | high | 无 |
| C5 | 从 09-30 约 27.1 万（7 日均）增至 11-04 154 万 | 官方增长叙述 | FourWeekMBA 图表（IT之家数据） | med | 口径混用（单日 vs 7 日均）被官方澄清 |
| C6 | MAU 约 548 万（部分源） | 未在主英文帖强调 | FourWeekMBA、Gate、部分中文报道（IT之家未突出） | med | 官方主帖未明确；或后续更正 |
| C7 | “一切皆插件”架构，模型/工具/循环均可替换 | 官方 bio 与长文 | GitHub README、官方站点、Cordis 论文引用 | high | 无 |
| C8 | GitHub stars 约 27.6 万（截至 11-08/09） | 社区讨论 | GitHub 页面实时显示 276k+ | high | 无 |
| C9 | 筹备官方插件市场与作者 token 激励计划 | 官方帖明确 | IT之家、Yicai | high | 计划取消或延迟超期 |
| C10 | 数据仅覆盖官方 API 用户，自运行其他模型不计入 | 官方帖“counting users on the official API” | 所有转述均强调 | high | 官方扩大口径 |

## 5. X fieldwork
主帖 https://x.com/DeepSeekHarness/status/2119431663642153128（2026-11-08 14:07 UTC）为长文，点赞 4k+、浏览 35 万+。结构：增长数据 → 插件案例（dsh-media-desk、dsh-guizang-design、dsh-context、agentero-dsh）→ 市场与支持计划 → “Agent 时代操作系统”定位。

作者历史：@DeepSeekHarness 账号专注产品更新，09-30 桌面端、11-02 Creator Mode 视频帖（25k+ 赞）。官方站点 deepseek.com/harness 同步。

引用与反方：Bloomberg 帖引发“付费墙”抱怨；部分用户指出数据仅官方 API、未独立验证；安全相关帖引用 SAFETY.md 警告无安全审计、建议 disposable VM。

专家邻域：插件作者公开案例；社区有对 creator mode 上下文不足的反馈；对照讨论集中在开源 vs 封闭 agent 表面。

帖内链接：Feishu 兴趣表单、GitHub 插件包名、官方站点。

## 6. Off-X fieldwork
- 官方站点 https://www.deepseek.com/harness/ ：预览版、npx 启动、一切皆插件、桌面下载。已打开。
- GitHub https://github.com/deepseek-ai/deepseek-harness ：MIT、README 引用 Cordis arXiv:2608.25512、开发者预览声明、约 276k stars、25k+ commits。已打开 README。
- IT之家 https://www.ithome.com/1/023/011.htm （2026-11-05）：完整数字 154 万 DAU、92 万亿 token、3.5 万插件、60%、市场计划。已打开。
- Yicai Global：同数据 + 对 Claude Code 对照。已打开。
- Bloomberg 摘要（paywall 外）：确认官方 X 披露与数字。
- FourWeekMBA 图表与分析：7 日均曲线、单日 vs 均值口径差异、约 60M token/日/用户算术。
- VentureBeat 08-13 发布报道：对标 Claude Code、MIT、npx 命令。
- 安全：社区引用 SAFETY.md 无审计警告。

数字至少两个独立源：DAU/token 由官方 X + IT之家/Yicai 交叉；stars 由 GitHub 页面确认。

## 7. Contradictions
1. 口径混用：增长曲线早期为 7 日均值，11-04 为单日峰值，部分头条用 468%（154/27.1），官方或图表用更高基数对比。FourWeekMBA 明确指出。
2. 自报未独立验证：所有数字来自官方，仅官方 API；外部无 telemetry。AI Weekly 等明确标注。
3. MAU 5.48M 在部分中文/分析源出现，主英文官方帖未突出；IT之家正文未强调。
4. 高 token 消耗（约 60M/用户/日）暗示 agent 工作流成本远高于聊天，但开源免费入口与官方 API 变现路径之间存在张力；公司未披露成本或付费转化。
5. 安全与生态速度：快速插件增长 vs SAFETY 文档自承无审计、可执行模型生成代码。

## 8. Mechanism
DeepSeek 以开源 harness（而非仅模型）作为 agent 入口，通过官方 API 计量拉量。桌面端降低门槛后，Creator Mode 与插件系统允许用户自建工作流，形成正反馈（60% 用户有插件行为）。增长加速与 V4.1-Flash 发布时间窗口重合，但官方未因果归因。插件市场与 token 激励旨在将社区开发者转化为生态锁定，对标封闭实验室的专有 agent 表面。机制核心是“模型可换 + 官方 API 消耗绑定 + 一切可插件”。

## 9. Open questions
- 独立 DAU/token 审计或第三方监控？
- 插件质量分布、恶意插件比例、安全事件？
- 官方 API 收入、成本、付费转化率？
- 非官方模型用户规模（本地/其他 API）？
- 插件市场上线时间、分成条款、token 激励具体额度？
- 与 Claude Code / Codex 的真实任务完成率与留存对比？

## 10. Do not write yet
1. 开源 harness 作为“操作系统”是否真能把价值从模型迁移到生态，还是仍被官方 API 定价权锁住。
2. 60M token/日/用户 是否预示 agent 经济的单位经济压力，还是证明长任务已成主流。
3. 插件生态速度 vs 安全审计缺口：社区信任能撑多久。
