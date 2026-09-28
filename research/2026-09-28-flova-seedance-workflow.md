# PACK 2026-09-28 flova-seedance-workflow

## 0. Meta
- Seed URL / post id: https://x.com/Hope_Ai01/status/2104214749609439444
- Mode: research
- Status: COMPLETE
- Time window: Seedance 2.5 出现在 Flova 工作流教程约 2026-08 下旬 → 主帖 2026-09-27 14:21 UTC → 本包 2026-09-28
- What was skipped: 未用 view_x_video 逐帧看 60s 成片（工具未跑）；未注册 Flova 复现「分镜→成片」；未核 Hope 与 Flova 的 CPP 合同金额；技能页 https://www.flova.ai/en/skill/ 抓取几乎空白。

## 1. Question
这条「电影级高铁劫案」热帖，证明的是生成模型质变，还是 Flova 把 Seedance 2.5 包进 Agent + Skill + 分镜工作流之后的分发能力？

## 2. Timeline
- 2026-08-22 前后：YouTube 出现 Flova + Seedance 2.5 教程（3D/纪录片工作流，免费额度话术）。
- 2026-08-24/25：教程强调 Script-to-Video、分镜、角色一致性、Skill 保存（JaxPrompten 等频道，带 refCode）。
- 2026-09-12：seedance.tv 博客写 Flova 上 Seedance 2.5 的 agent 工作流，强调先锁交付物再生成、片段级修改（Emma Chen）。
- 2026-09-27 14:21 UTC：@Hope_Ai01 发 60s 动作片，标注 Storyboard + Script-to-Video，Powered by Seedance 2.5，带项目链接、Skill 链接、注册链接。
- 同日跟帖只丢技能页 URL。回复稀、赞约 1k、转 150、收藏 62（相对播放/观感，收藏远低于 supermemory / Yarchi）。

## 3. Actors
- Hope Ai（@Hope_Ai01）：Bio 写 Ai Creator，并写 CPP：@higgsfield @ImagineArt_X @itsPolloAI @Hailuo_AI @Flovaai。激励：带货与分成，不是实验室发布。
- Flova（flova.ai / @Flovaai / @Flovaai_Japan）：把多模型（含 Dreamina Seedance 2.5）放进 Agent 画布，卖 Skill 模板与额度。
- Seedance / Dreamina：Flova 产品页写「Dreamina Seedance 2.5」。生成模型提供方；本帖不是模型官方账号发布。
- 教程生态：JaxPrompten 等频道描述里带 `refCode=`，与主帖同结构（作品 + 工作流 + 注册）。
- 未验证：Hope 是否员工、成片有多少镜头是人工重绘、音频是否全站内生成。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
|----|-------|----------|--------------|------------|----------------|
| C1 | 成片在 Flova 上用 Storyboard + Script-to-Video 流程做 | 主帖生产行 | Flova 教程与 51CTO 复盘同一流程 | med | 作者承认外链剪辑软件完成时间线 |
| C2 | 视频模型是 Seedance 2.5 | 主帖 Powered by | flova.ai/en/video-models/seedance-2-5/ 提供该模型 | high | 成片元数据指向其他模型 |
| C3 | Seedance 2.5 在 Flova 上单段最长约 30 秒 | — | Flova 产品页「up to 30 seconds」；seedance.tv 同 | high | 官方改上限或实测稳定更长 |
| C4 | 最多约 50 路多模态参考 | — | 同一产品页 | med | 文档改数字或实际 cap 更低 |
| C5 | 支持 R2V（绿幕/白模控动作） | — | 产品页 R2V 节 | med | 仅为营销页、工作区无入口 |
| C6 | Flova 把模型放进 Agent：先出规格/分镜，再生成，再局部改 | 主帖「Storyboard + Script-to-Video」 | 51CTO《画中人》复盘；YouTube 章节「storyboard first / targeted revision」 | high | 默认路径是一键出片无中间稿 |
| C7 | 主帖作者是 Flova CPP / 推广号 | bio 明示 CPP @Flovaai | 未找到员工页；与带 refCode 的教程同构 | high | Flova 声明其非联盟、为员工作品 |
| C8 | 本片证明「电影级长片已可一键生成」 | 文案 cinematic thriller | 产品页单段 30s；60s 成片至少要拼接 | high（反向） | 官方提供原生 60s+ 且无拼接 |
| C9 | 新用户有免费额度，但不是无限生产 | 注册 CTA | seedance.tv：「free credits ≠ unlimited」 | high | 官方改成免费无限 |
| C10 | Skill 可保存并复用工作流 | 主帖 Skill link | YouTube「Saving the Workflow as a Skill」；Flova 技能页存在但抓取空 | med | Skill 只是提示词包不能复现分镜 |

## 5. X fieldwork
- 主帖 https://x.com/Hope_Ai01/status/2104214749609439444 。60s 视频：高铁劫案、女特工、面具、屋顶追逐、倒计时公文包。文案是预告片语法，不是架构文。
- 互动结构：赞过千、收藏只有几十，和「可复用方法帖」相反（Yarchi / supermemory 收藏是赞的数倍）。
- 作者史：工具推荐 + CPP 列表。同一账号也会推其他视频模型，不是 Flova 专页。
- 反方几乎没有技术拆解；@XChupacabar「best Ai video」无信息量。
- 帖内链接：项目页、Skill 页、注册页。Skill 页 browse 几乎无正文，项目页未在本包逐页打开（短链）。

## 6. Off-X fieldwork
- https://www.flova.ai/en/video-models/seedance-2-5/ ：30s、最多 50 references、R2V、Dreamina Seedance 2.5。
- https://www.seedance.tv/blog/flova-ai-seedance-2-5 ：先锁交付与验收，再整段看，再只改弱镜头。
- YouTube JaxPrompten（2026-08-25）：参考视频 → 分镜 → 局部修 → 时间线拼接 → 存 Skill；描述含推广码。
- 51CTO 中文复盘：Agent 先出规格文档和 6 镜分镜，再把元素图当后续锚点；称 Skill 比裸模型直出更稳。这是使用者叙述，不是官方评测。

## 7. Contradictions
- 「一部电影」vs 30s 原生上限：60s 热帖必然是多段拼接。能力在工作流，不在单次采样长度。
- 作者身份：看起来像创作者分享，bio 是 CPP。信息价值在演示，不在中立评测。
- 收藏/赞比：传播靠画面，不靠可抄架构。不能和 Palantir / Company Brain 帖放在同一「方法论」桶而不加标记。
- Skill 页打不开有效正文：主帖把「可复现」指向一个当前抓取为空的页面。
- 未看视频帧：运动连续性、脸一致性、物理错误本包不评分。

## 8. Mechanism
Seedance 2.5 提供较长单段和多参考；Flova 把「导演笔记」做成 Agent 状态（规格 → 分镜 → 元素锚点 → 逐镜生成 → 局部返工 → 时间线），再把流程存成 Skill 分发。联盟作者用成片当广告。X 看到的是预告片；可迁移的部分是：先禁止直接出片，先写分镜和验收，再只重做失败镜头。

## 9. Open questions
- 本片镜头数、每镜时长、失败重试次数、总费用。
- Hope 与 Flova 的具体合作条款。
- Seedance 2.5 官方（Dreamina/字节系）对 Flova 封装是否授权及是否同权重。
- Skill 链接是否只对登录用户可见。
- 角色跨镜头一致性是参考图约束还是人工选帧。

## 10. Do not write yet
1. 别把预告片写成模型发布——发布的是工作流封装和分发。
2. 可抄的是「分镜先行 + 局部返工」，不是「Seedance 已经能拍长片」。
3. 看收藏数：画面帖和架构帖不要用同一套「热」来决定是否写成稿。
