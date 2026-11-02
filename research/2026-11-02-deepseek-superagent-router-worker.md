# 研究包：DeepSeek Super-agent Router-Worker 架构

## 主线
- X 主帖：https://x.com/DeepSeekHarness/status/2116857257245987236 （8700+ likes）
- 文章：Exploring Super-agent Design: Towards a More Autonomous Agent System（DeepSeek Harness 团队，2026-10-31）
- 原型：https://github.com/deepseek-ai/dsh-superagent-prototype （MIT，研究代码，非官方产品）
- Harness：https://github.com/deepseek-ai/deepseek-harness 与 https://www.deepseek.com/en/harness/

## 关键事实
- 四特征：连续、高效、主动、持久
- 五模块：双层（Router 不执行 / Worker 隔离）、事件驱动（两级过滤 + 订阅直通）、全双工多信道、存算分离、Watchdog
- 实验（合成，5 次，约300 消息 / 20 请求）：Super-agent p50/p95 = 12.4/15.7 min；中性单 Session p95 = 29.5 min
- 直通去掉：Router 决策 +30%，cache-read token +37%（23.2M → 31.8M）

## 证据来源
- X 帖全文与英译（thread fetch）
- GitHub README、docs/000-philosophy.md、docs/007-architecture.md
- 二手：MarkTechPost、搞金、爱范儿、Global Times、Sina 等转述数字一致
- 官方 Harness 站点与仓库

## 未核验
- 实验无独立复现，未测真实代码质量
- 原型与文章实现差异
- 内部实例长期数据
- 安全章节完整版
