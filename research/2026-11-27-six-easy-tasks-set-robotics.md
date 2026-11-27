# PACK 2026-11-27 six-easy-tasks-set-robotics

## 0. Meta
- Seed URL / post id: https://x.com/robocurve/status/2125754721847988381
- Mode: research
- Status: COMPLETE
- Time window: 2026-11-25 to 2026-11-27
- What was skipped: 完整视频帧级分析（因工具限制未逐帧抽取）；第三方独立复现跑分（无公开第三方跑通记录）

## 1. Question
前沿编码智能体（GPT-6.2 Astra / Claude Fable 5.2）在真实双臂机器人上完成“人类100%成功率的简单操作任务”为何全军覆没（0/72），而人类遥操作可100%完成？这揭示了通用模型在物理操作上的具体能力缺口。

## 2. Timeline
- 2026-07-01: Robocurve X账号创建。来源: X用户搜索。
- 2026-09-14: 宣布$10M种子轮，由Initialized Capital领投。来源: robocurve.org/blog/seed-raise/ 与多家独立报道（Dealroom、SV Post等）。
- 2026-11-24: Jay Chooi宣布因Codex在RoboDojo-RC Tier 1达97%而退休该基准。来源: https://x.com/chooi_jeq/status/2125032552239087627。
- 2026-11-25: 官网发布SET博文。来源: https://robocurve.org/blog/six-easy-tasks/。
- 2026-11-26 00:53 UTC: @robocurve发主帖及线程介绍SET。来源: 主帖ID 2125754721847988381。

## 3. Actors
- Jay Chooi (@chooi_jeq): Robocurve联合创始人/CEO。哈佛CS/Math+统计硕士、Rhodes Scholar、前MATS Fellow、UK AISI经历。激励：公共评估与物理自动化预测。来源: chojeq.com、YC页面、MATS Substack。
- Christopher Leet (@leet_codes): SET主要作者之一。来源: 博文作者列表与X喊话。
- 其他作者: Anton de la Fuente, Drew Nguyen, Achu Menon, Tzu Kit Chan。未独立核实全职状态。
- Robocurve PBC: 旧金山公共福利公司（YC S26），使命是独立评估物理AI。激励：第三方审计，非实验室自报。来源: 官网与融资公告。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 六任务（拧瓶盖、塞信封、开挂锁、放笔记本进背包、开容器、开拉链袋取笔）人类直接操作100%，遥操作100%，前沿编码智能体0% | 主帖及线程视频 | https://robocurve.org/blog/six-easy-tasks/ 表格与描述 | high | 第三方独立复现出现>0成功率 |
| C2 | GPT-6.2 Astra (Codex, Ultrafast, high) 与 Claude Fable 5.2 (Claude Code, Fast, high) 各36次试验全失败，共72/72=0 | 线程“failed at all 72 real-world trials” | 博文表格 + all-runs页面显示Six Easy Tasks 72 runs 0.0% | high | all-runs或原始日志显示非零 |
| C3 | 硬件为I2RT YAM双臂（左右），CAN总线，i2rt Python驱动，三相机（overhead + 左右腕） | 无直接数字 | 博文“YAM arms from I2RT” + I2RT官网YAM规格（$2999, 6DOF, CAN） | high | 实际使用非YAM硬件被证实 |
| C4 | 每任务6分钟时限，代理写代码控制，结束时需复位 | 线程隐含 | 博文明确“Each task trial has a 6 minute limit”及提示词 | high | 协议文档显示不同时限 |
| C5 | 评分员为GPT-6.2 Astra (high)，基于前后相机照片，可输出UNSURE | 无 | 博文完整grader prompt | high | 评分协议不同 |
| C6 | 代理有部分进展（如拿起钥匙、打开部分卡扣），但端到端完成率为0 | 线程具体失败描述（瓶盖未拧紧、钥匙掉落等） | 博文Caveats段 | high | 原始轨迹显示完整完成 |
| C7 | 公司为PBC，独立于前沿实验室 | 主帖bio | 官网“Public Benefit Corporation”“Independence and neutrality” + 融资公告 | high | 股权或控制权被实验室持有被证实 |
| C8 | $10M种子轮（2026-09-14，Initialized领投，YC等参与） | 无 | 官网博文 + Dealroom/PitchBook/SV Post多源 | high | SEC或官方否认 |
| C9 | 人类遥操作者视角不同（旁观者视角 vs 代理顶/腕相机），且有练习时间 | 无 | 博文Caveats | high | 无差异被证实 |
| C10 | RoboDojo-RC Tier 1上编码智能体曾达高分（如Codex 97%），但SET全零 | Jay Chooi帖 + 官网趋势表 | 官网主页表格与all-runs | high | 数据不一致 |

## 5. X fieldwork
主帖为线程：主帖声明人类100%/AI 0%，后续帖逐任务失败视频（瓶盖掉落、信封被挡、钥匙掉落、背包滑动、容器整体抬起、拉链袋抓握失败），并链接官网。作者历史：@robocurve为PBC账号，持续发布真实硬件评估。引用与反方：回复多为“好指标”“模拟外真实难”，无明显技术反驳；有用户提及部分进展。专家邻域：Jay Chooi（创始人）与@leet_codes互动；此前有METR相关人员（如Nikola Jurkovic）在官网testimonials中提及。帖内链接：https://robocurve.org/blog/six-easy-tasks/ 与all-runs。

## 6. Off-X fieldwork
- 官网博文：完整任务描述、材料清单（Amazon链接水瓶、挂锁、容器）、提示词、评分prompt、Caveats。引用关键句：“Frontier coding agents controlling robot arms score 0% on.”“A human teleoperator controlling the same robot arms scores 100% on.”
- all-runs页面：确认Six Easy Tasks 72 runs, 0.0% mean score。
- 融资：官网seed-raise博文与Dealroom等多独立源确认$10M。
- 硬件：I2RT官方文档确认YAM为6DOF CAN臂，Python SDK，价格约$2999。
- 创始人背景：chojeq.com、YC、MATS Substack交叉验证哈佛、Rhodes、MATS、AISI经历。
- 相关先前工作：官网显示RoboDojo-RC上编码智能体高分，与SET形成对比。

## 7. Contradictions
- 同一组织在RoboDojo-RC Tier 1上编码智能体可获高分（Codex 97%），但在SET（更“日常”操作）上0%。可能因任务选择（需精细力控、对向抓握、持续夹持）不同，或代理接口差异。
- 代理有部分进展，但主指标为严格端到端；人类遥操作有练习与不同视角，可能高估人类基线。
- 评分依赖另一GPT模型看照片，可能存在视觉盲区（博文允许UNSURE）。
- 公司声称独立，但依赖前沿模型API进行控制与评分，潜在循环依赖。

## 8. Mechanism
前沿通用模型（尤其编码智能体）通过工具调用写代码控制机器人，缺乏专用VLA训练。失败模式集中在精细操作：对向抓握力不足（拉链袋）、持续夹持防滑（背包）、螺纹旋转（瓶盖）、小物体插入（钥匙）。相机视角受限+无力反馈导致闭环困难。6分钟时限内无法充分试错。人类优势在于先验物理直觉与多模态反馈。SET专门选择需“常识操作”而非纯抓放的任务，暴露通用模型物理接地缺口。

## 9. Open questions
- 原始轨迹与代码是否完全公开可复现？
- 若给代理更多试错轮次或更好相机，成功率是否提升？
- 专用VLA或微调模型在SET上表现如何（公司称将发布）？
- 评分一致性：人工评分 vs GPT评分差异？
- 下一必抓源：all-runs原始JSON或视频完整日志，以及任何独立复现。

## 10. Do not write yet
- 角度1：编码智能体在“饱和”基准上高分，在日常物理任务上归零，暴露评估选择偏差。
- 角度2：精细力控与对向操作是当前通用模型物理世界的硬缺口。
- 角度3：独立PBC硬件评估的价值与局限（视角、练习、评分器依赖）。

（证据字数约2800+汉字，覆盖主帖/作者史/官网/融资多源/硬件规格/矛盾点。）
