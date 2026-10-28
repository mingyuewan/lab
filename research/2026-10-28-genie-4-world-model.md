# PACK 2026-10-28 genie-4-world-model

## 0. Meta
- Seed URL / post id: https://x.com/GoogleDeepMind/status/2115114028338962672
- Mode: research
- Status: COMPLETE
- Time window: 2026-10-27 16:10 UTC 公告起至 2026-10-28 约 02:30 UTC
- What was skipped: 无独立第三方定量评测（模型刚发，无公开 leaderboard 或论文）；未跑实际 API（研究预览）；视频帧未逐帧 view_x_video（已确认有 demo 视频，但以文字与官方描述为主）。

## 1. Question
Genie 4 作为 Google DeepMind 最新实时交互世界模型，其相对 Genie 3 的真实进步（原生音频、实时自然语言 steering、Gemini 规划环、物理与人物自然度）与官方承认的短会话一致性/漂移限制，在研究预览阶段对机器人训练与创意原型的实际可用性边界是什么？

## 2. Timeline
- 2024-12：Genie 2 发布，10–20 秒交互、360p。来源：Wikipedia 与早期报道。
- 2025-08-05：Genie 3 研究预览，720p / 24 fps，视觉记忆约 1 分钟，连续交互“数分钟”，无原生音频。来源：DeepMind Genie 3 blog、The Verge、Ars。
- 2026-01-29：Project Genie 对 US Google AI Ultra 订阅者开放，基于 Genie 3，单次探索限制 60 秒。来源：Google blog、TechCrunch hands-on。
- 2026-05：Project Genie 接入 Street View。来源：TechCrunch。
- 2026-10-27 16:10 UTC：Google DeepMind 在 X 发布 Genie 4 主帖与功能列表。来源：https://x.com/GoogleDeepMind/status/2115114028338962672 及 follow-up 帖。
- 2026-10-27：DeepMind 官方 blog “Genie 4: A new generation of world simulation” 上线，作者 Raia Hadsell、Diego Rivas、Hang Qi。来源：deepmind.google。
- 2026-10-27：TechCrunch、Ars Technica 等报道，引用 briefing 中 “up to two minutes” 一致性与 Gemini 3.8 Flash 规划角色。来源：techcrunch.com、arstechnica.com。
- 2026-10-27–28：Raia Hadsell、Tejas Kulkarni（DeepMind research director）等在 X 转发/评论，Kulkarni 展示创意工作流 demo。来源：X。

## 3. Actors
- Google DeepMind：发布方，激励为推进世界模型作为 AGI 路径中的安全模拟环境，同时为 Project Genie / Gemini API 积累用户与数据。
- Raia Hadsell：VP of Research @googledeepmind，Genie 4 blog 共同作者，X 上确认发布并提及 Release Notes 访谈。任期长期，激励与机构一致。
- Diego Rivas、Hang Qi：blog 共同作者；Rivas 在 TechCrunch 被引为强调早期阶段与实时对 ideation/storyboarding 的价值。
- Tejas Kulkarni：DeepMind research director（Solving World Models），前 CSM.ai CEO，MIT PhD；在 briefing 中提出 hybrid world models 愿景，并在 X 展示 Genie 4 + Argon + Blender 原型流程。
- 可信测试者（trusted testers）：当前唯一能实际使用的群体，官方未公开名单。
- 媒体（TechCrunch Rebecca Bellan、Ars Ryan Whitwam 等）：二手报道，依赖官方 briefing。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | Genie 4 是 DeepMind 首个原生生成音频的实时世界模型（环境音、音乐、互动对话） | DeepMind 主帖与 follow-up 明确列出 Native audio | DeepMind blog 原文：“Genie 4 is our first real-time world model to generate audio natively”；TechCrunch、Ars 确认 | high | 若有更早公开的 DeepMind 世界模型已原生音频 |
| C2 | 基于 Gemini Omni 做外观/行为锚定，Gemini 模型（报道称 3.8 Flash）做规划与连贯性维护 | DeepMind 功能帖：“Built on Gemini Omni… Gemini reasoning: Plans multi-step events” | DeepMind blog：“Gemini Omni anchors… other Gemini models provide the complex reasoning”；Ars：“leverages Gemini 3.8 Flash as a guiding agent”；TechCrunch 同 | med | 官方未在公开 blog 精确写出 “3.8 Flash”，仅媒体 briefing |
| C3 | 支持实时自然语言 steering（改天气、镜头、加人物/物体），不需重启 | DeepMind 帖与 demo 描述 | DeepMind blog 详细描述并附 prompt 示例；TechCrunch、Ars 确认 | high | 若实测显示必须重启或延迟极高 |
| C4 | 一致性时长约达 2 分钟，为 Genie 3 的两倍 | 无直接 X 数字（官方用 “short sessions”） | TechCrunch：“up to two minutes, double its predecessor’s limit”；多源（superintelligencenews、Ars 等）重复；Genie 3 官方为 “few minutes” / 记忆 ~1 min | med | 官方未公开精确数字；Genie 3 “few minutes” vs 媒体 1 min 存在表述差 |
| C5 | 物理（空气动力学、碰撞）与人物运动更自然 | DeepMind 功能列表 | DeepMind blog：“simulates real-world physics scenarios, such as aerodynamics, collisions”；Ars 同 | med | 无独立物理评测，仅官方 demo |
| C6 | 当前仅研究预览给 trusted testers，随后给 Google AI Ultra 订阅者（Project Genie）与 Gemini API / AI Studio 早期伙伴 | DeepMind 帖明确 | DeepMind blog + Google blog + TechCrunch 均同；有 waitlist 链接 | high | 若更快或更慢公开时间表 |
| C7 | 所有视频与音频带 SynthID 水印 | 间接（官方一贯做法） | 多家报道（okaynews、sqmagazine 等）引用官方文档；DeepMind 长期 SynthID 政策 | med | 若官方明确说 Genie 4 不加水印 |
| C8 | 承认限制：长跑细节/物体漂移、音频准确性未完全解决、世界内文字可读性差、空间精度与长期一致性仍是研究中 | X 上有人指出一致性问题 | TechCrunch：“Details and objects can drift… haven’t quite figured out how to ensure the audio will be accurate and any in-world text will be legible”；DeepMind blog 与多源确认 | high | 若后续独立测试显示限制已被大幅缓解 |
| C9 | 与 Gemini 4 Argon 配对做机器人模拟实验（如 Apptronik Apollo 下国际跳棋） | 间接提及 | TechCrunch、Techstrong 等报道 briefing | med | 官方 blog 未展开实验细节 |
| C10 | 目标用例包括机器人/Agent 安全训练环境、影视预演、游戏原型 | DeepMind 帖：“safe virtual environments to see how agents and robots navigate” | DeepMind blog 与 TechCrunch 均强调 | high | 无 |

## 5. X fieldwork
主帖 https://x.com/GoogleDeepMind/status/2115114028338962672 （约 16k likes，1.8M views）+ 紧随功能帖 https://x.com/GoogleDeepMind/status/2115114030503166385 列出 Photorealism (Gemini Omni)、Advanced physics、Real-time controls、Native audio、Gemini reasoning。作者历史：Raia Hadsell（@RaiaHadsell）转发并补充 “real-time text controls, audio, Gemini reasoning, plus better physics and photorealism”，并提到与 Logan Kilpatrick、Diego Rivas、Hang Qi 的 Release Notes。Tejas Kulkarni 展示从 Nanobana 图 → Genie 4 动画 → Argon 参考 → Blender 的创意流程。反方/谨慎声：有用户指出 “Does the world stay consistent when you turn around”，以及 “Genie 4 is frontier research that will occasionally make mistakes… cannot be the final safety check”。专家邻域：Kulkarni（世界模型方向）、Hadsell（研究 VP）、Parker-Holder（此前 Project Genie）等。帖内链接指向 DeepMind blog。

## 6. Off-X fieldwork
- 官方 DeepMind blog（已 browse）：明确 “natively multimodal… audio-like music, ambient noises, and interactive dialogue”；Gemini Omni 锚定外观，其他 Gemini 提供推理以维持连贯；实时自然语言修改；已开始给 trusted testers 研究预览，随后 Project Genie Ultra 与 API/AI Studio；附大量 demo prompt 与视频。
- Google blog 短公告：同日，强调 “unprecedented realism and native audio”。
- TechCrunch（已 browse）：引用 briefing，“up to two minutes, double its predecessor’s limit”；Gemini 作为 director 规划步骤并检查帧；Kulkarni 谈 hybrid world models；Rivas 强调早期、ideation/storyboarding 价值；明确承认 drift 与音频/文字问题。
- Ars Technica（已 browse）：Gemini 3.8 Flash 作为 guiding agent；一致性 “a couple of minutes before they forget how things started”；更好物理与人物；原生音频；访问将分阶段到 Ultra。
- Genie 3 官方 blog 与 Wikipedia/早期报道：720p/24fps，记忆约 1 分钟，无原生音频。
- 无公开论文或 GitHub repo（研究预览）。

## 7. Contradictions
- 一致性时长：官方 blog 用 “short sessions” 并强调漂移；媒体（TechCrunch、Ars 等）统一写 “up to two minutes / double Genie 3”。Genie 3 官方说 “few minutes”，媒体与 Wikipedia 常记为约 1 分钟记忆。数字来源是 briefing 而非公开规格表，存在表述弹性。
- 分辨率/帧率：Genie 3 明确 720p/24fps；Genie 4 官方与主要报道均未公布，无法直接比较计算效率或视觉质量。
- “更真实物理”仅来自官方 demo 与 self-report，无独立物理引擎对比或定量指标。
- 访问：“soon” 给 Ultra 与 API，但无具体日期；Project Genie 此前对 Genie 3 就限制 60 秒，Genie 4 实际用户会话长度未知。

## 8. Mechanism
DeepMind 把世界模型定位为 AGI 路径上的关键：提供无限、安全、可变的模拟环境，用于机器人与 Agent 训练，同时服务创意工具。Genie 4 的机制是混合系统——Gemini Omni 负责视觉/行为锚定，另一 Gemini（报道 3.8 Flash）在环内做规划、分步与帧级检查以维持连贯，Genie 本身生成下一帧视觉与原生音频。这让实时 steering 成为可能，但自回归生成的计算成本与记忆限制仍把连贯窗口压在短会话（媒体称 ~2 分钟）。SynthID 水印是责任层。当前研究预览是为了收集反馈，再决定产品形态（Project Genie 消费者端 + API 开发者端）。

## 9. Open questions
- 精确技术规格（分辨率、FPS、延迟、参数量）。
- 独立第三方评测（物理一致性、音频准确性、长期对象永久）。
- 实际 Ultra 用户会话时长与定价。
- 机器人实验的定量结果（仿真到真机迁移率）。
- 与 Runway GWM Worlds 2、其他世界模型的直接对比。

## 10. Do not write yet
- 角度 1：Genie 4 作为“混合世界模型”的工程选择（Gemini 规划环 + Genie 生成）而非单纯规模放大。
- 角度 2：短会话限制对“机器人训练环境”叙事的实际约束。
- 角度 3：从研究预览到 Project Genie/API 的产品化路径与水印责任。
