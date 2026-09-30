# PACK 2026-09-30 robinhood-agents-in-app

## 0. Meta
- Seed URL / post id: https://x.com/RobinhoodApp/status/2105074572722679839 （2026-09-29 23:17 UTC，HOOD Summit 当晚官方帖）
- Mode: research
- Status: COMPLETE
- Time window: 2026-05-27（MCP 开放）→ 2026-09-30（站内 Agents 宣布后约 12h）
- What was skipped: 未看 HOOD Summit 全程视频；未打开 FINRA/SEC 原始 filing；WSJ「Schwab/LPL/JPM 因 agent 搬家现金而跌」只见二手转述，未打开 WSJ 原文；未独立复现 30M tool-calls 计数器。

## 1. Question
Robinhood 在 9/29 HOOD Summit 把「自建站内 Agents」当成主力产品，它到底是把 5 月 MCP 沙盒做成大众消费品，还是把责任、模型账单和 herd 交易风险一起塞进零售券商？

## 2. Timeline
- 2023：Robinhood 24 Hour Market 上线（周日 20:00 ET–周五 20:00 ET，数百只股票/ETF）。来源：Summit 新闻稿回溯。
- 2026-03-31：Public.com 先推出 AI agent 交易（股票/期权/加密）。来源：The Synthesis 综述。
- 2026-05-27：Robinhood 新闻稿 *Robinhood is Now Open to Agents*——Agentic Trading + Agentic Credit Card，经 MCP 接第三方 agent；交易端 beta，仅股票；独立 agentic account。
- 2026-05 至夏：Finder 复盘称 setup/鉴权当时 desktop-only；agent 对全部账户有读权限、只能在 agentic 账户下单。
- 2026-06-15：YouTube *Agentic Trading Demo*，产品 VP Abhishek Fatehpuria 讲解 MCP；描述称已向全部客户开放股票，期权随后。
- 2026-08-17：@RobinhoodApp 宣布 crypto agentic trading 向合格用户 rollout（MCP + dedicated account）；8/31「100% rolled out」，NY 不可用。
- 2026-08-20：agent 可读 order book、标支撑阻力。
- 2026-08-21 / 09-15：加密 24/7 agent 营销帖。
- 2026-09-29 Houston，George R. Brown Convention Center，HOOD Summit 2026「Engines of Creation」：宣布 Robinhood Agents（App 内嵌）、Agent Apps 市场、Loops（即将）、周末股票交易（监管审查）、美永续、财报二元合约、期权时长延长、4x 日内保证金、OCO、Helios。
- 2026-09-29 23:17 UTC：官方 X 帖「Introducing Robinhood Agents… Coming soon.」~1.9k likes / 16.7 万浏览（抓取时）。
- 2026-09-29 当晚：Agent Apps、Loops、Legend October 帖连发。
- 2026-09-29/30：Yahoo Finance David Hollerith、CoinDesk、MarketBeat、Investing.com 转写；Summit 现场即开，其余用户随机分周 rollout。
- 2026-09-30：Polymarket 等转述「Robinhood launches AI agents that can trade stocks on your behalf」。

## 3. Actors
- **Vlad Tenev** / CEO & co-founder Robinhood；Harmonic 执行董事长。激励：HOOD 股价、活跃交易者定位、Summit 叙事。Summit 穿 Star Trek 式服装（Yahoo 引 X）。
- **Abhishek Fatehpuria** / VP Product Management。Summit 与 Yahoo 采访主讲人。原话（Yahoo）：把体验做得「100 倍更容易」，就能从 15 万做到数百万。
- **Steve Quirk** / Chief Brokerage Officer。周末交易发言人；引用官方帖。
- **Jason Wallach** / CEO Bruce Markets。周末盘 ATS 提供方。
- **OpenAI / Anthropic**：首批站内模型供应商。Luna/GPT-Luna 年底前免费；公司拒答是否分成（Yahoo）。
- **Agent Apps 供应商**：Unusual Whales ($30/mo)、Nasdaq Investor Intelligence ($10)、SpotGamma ($10)、Wendy ($10)、Quiver Quant ($10)、Token Terminal ($10)、Visual Crossing ($5)、SkyFi 即将、Narravance ChatterFlow ($8)、Carbon Arc / Fiscal.ai 即将。
- **Cboe**：earnings contracts 通道；年底前 Cboe/RH 宣称不收合约费（待监管）。
- **Robinhood Derivatives + Bitstamp**：美客户永续。
- **顾客**：法律上对 agent 下单自负；RH「尚未比较 agentic vs 非 agentic 投资结果」（Yahoo）。
- **传统券商（Schwab / LPL / RJ / JPM）**：sweep cash 被 AI 搬家的叙事自 2026 春存在；与本次 Summit 的因果未用 WSJ 原文钉死。

## 4. Claim table
| ID | Claim | X signal | Off-X record | Confidence | Flip condition |
| C1 | 2026-09-29 HOOD Summit 宣布 App 内 Robinhood Agents | https://x.com/RobinhoodApp/status/2105074572722679839 | https://robinhood.com/us/en/newsroom/hood-summit-2026/ | high | 新闻稿撤回或产品页消失 |
| C2 | 自 5 月 MCP 上线以来 >150,000 客户开过 agentic trading account | Summit 转述帖（AllocatorPJ 等） | 官方稿一字不差；Yahoo 独立复述 company said；Investing.com 现场讲稿同样数字 | high（数字同源公司，第二源是记者复述而非第二计数器） | 10-Q/股东信给出不同累计开户数 |
| C3 | agents 每天使用 Robinhood tools 约 3,000 万次 | 同上 | 官方稿 + MarketBeat 引 Fatehpuria + Investing.com 讲稿 | med | 分母含 MCP ping/读盘而非下单；季报拆「tool call vs order」 |
| C4 | 站内 Agents ≠ 取代 MCP：MCP 仍给自带第三方 agent | 官方「no linking required」vs 8 月 MCP crypto 帖 | 稿：「Trading MCP we launched this summer is still there」；产品页 External agent access | high | 日后关掉 MCP |
| C5 | 交易默认需人工批准，可关闭；资金仅限 dedicated agentic account | 官方帖 bullet | 稿 + 产品页 + Yahoo「approval on by default… can turn off」 | high | 默认改为关闭或允许动用主账户/保证金 |
| C6 | 首批模型：OpenAI + Anthropic；GPT-Luna / Luna 2026 年底前免费 | AllocatorPJ「GPT-6 Luna free til EOY」 | 稿写 OpenAI GPT-Luna 年底免费；Yahoo：Anthropic + OpenAI，Luna free remainder of 2026 | med（Luna 与「GPT-6 Luna」营销名未在官网并列定义） | 定价页列出模型目录与计费 |
| C7 | Loops（24/7 常驻策略）在宣布时仍是 coming soon | https://x.com/RobinhoodApp/status/2105074709519888560 | 稿与产品页均「Coming soon」；MarketBeat「very soon」 | high | 全量用户可建 Loop |
| C8 | 周末美股交易：early next year，pending regulatory review，走 Bruce ATS | Quirk 引用帖 | 稿明确 pending regulatory review + Bruce ATS | med-high（产品意图高，上线日低） | ATS/监管批准文件或推迟公告 |
| C9 | 加密永续：合格美客户，BTC/ETH 最高 10x，其余 3x；Bitstamp；年底前 1bp | 市场转述 | 稿列出标的 BTC ETH SOL XRP DOGE ADA LINK HYPE 与杠杆/费率 | med | 产品条款与稿不一致 |
| C10 | 顾客对 agent 交易自负；RH 不保证输出、不审计第三方 agent | 少有用户读 disclaimer | 5 月稿与 9 月产品页大段相同免责：RH does not control, supervise, monitor, recommend, or audit these AI agents | high | 若被认定为 discretionary RIA/robo 而改披露 |
| C11 | Fatehpuria 目标从 15 万做到数百万，靠降低摩擦 | — | Yahoo 采访直接引语 | med | 下季 funded agentic accounts 数字 |
| C12 | 公司尚未度量 agentic vs 非 agentic 投资结果 | — | Yahoo：hasn’t yet measured or compared outcomes | high | 公布对照绩效 |
| C13 | Agent Apps 是付费数据层，不是模型本身 | https://x.com/RobinhoodApp/status/2105075198869282905 | 稿列出月费 $5–$30 | high | 改成订阅打包进 Gold |
| C14 | 「Coming soon」与 Summit 现场已开通并存 | 主帖写 Coming soon | Yahoo：Houston 与会者立即开通，其余随机分周 | high | 全国开关一次拉齐 |

## 5. X fieldwork
**主帖结构。** @RobinhoodApp 2105074572722679839 是四条产品弹的第一条：Agents → Loops（2105074709519888560）→ Agent Apps（2105075198869282905）→ 稍早 Legend October（2105064995063222708）。措辞全是产品营销：「few taps」「24/7」「dedicated account and trade approvals」「Coming soon」。没有数字。150k / 30M 出现在新闻稿和 keynote，不在这条爆帖正文。

**作者史。** @RobinhoodApp 从 5 月起把 agentic 当成连续战役而非一次性发布：8/17 MCP+crypto、8/20 order book、8/21「agent era」、8/31 100% crypto rollout、9/15「Crypto doesn't sleep」。与 9/29「anyone can now build… no technical setup」形成「先极客 MCP、再大众 UI」的两段式。@vladtenev 近帖是 Summit 预热（「Pack light」2103225146068897994），不是产品条款。

**引用与反方。** 引用流以生态吃红利为主：@SteveQuirk_ 把 Agents 与周末盘/永续绑成「hedge fund in your pocket」；@AgentwareMarket 把站内 agent 接到 Robinhood Chain 上的付费 inference；meme/链上账户把帖当 AGI 信号。实质反方弱、但有两条硬刺：
1. @myrrazor（2105113800470888457）：若大众都说「给我能赚钱的组合」，模型会不会把同一批股票顶上天，以及偏差的法律含义。
2. @DougButdorf（2104200346641830026，Summit 前）：OpenAI Astra/openclaw 以 safety 拒单，前一天同一模型能下单——模型层安全策略与券商「你自负」之间已经打架。
Ross Gerber / Adam Aron 的高互动批评指向 tokenized stock，不是 Agents 本身，但说明 RH 监管信誉在同一周并不干净。

**专家邻域。** 产品侧是 Fatehpuria + Quirk。分析侧：Yahoo 的 Hollerith（采访到 VP）；CoinDesk 把 Agents 放进「抢活跃交易者 + 加密剧本」；The Synthesis（6 月）早就把 Public=feature / Robinhood=platform 分开；Barron’s/Mint 春夏写 sweep-cash 被 AI 搬家。X 上 AllocatorPJ、KryptonCGO 把 150k+30M+周末盘写成交易 desk note，数字全部回流官方稿。

**帖内链接。** 官方帖本身无外链。必须离开 X 打开的：`robinhood.com/us/en/newsroom/hood-summit-2026/`、`robinhood.com/us/en/agents/`、`robinhood.com/us/en/newsroom/robinhood-is-now-open-to-agents/`、Yahoo 稿、CoinDesk 稿、产品 MCP docs 入口。

## 6. Off-X fieldwork
**官方 Summit 稿（已打开）。** 关键句：「Since launch, over 150,000 customers have opened agentic trading accounts and now, agents use Robinhood’s tools almost 30 million times a day。」「usage on OpenAI GPT-Luna will be free until the end of the year。」「You can choose to manually approve each trade, which is a setting shown during setup and defaults to on。」「Coming soon, we’ll launch Loops。」周末交易「pending regulatory review」「powered by Bruce ATS」。永续：Bitstamp + Robinhood Derivatives，BTC/ETH 至 10x，其余 3x，年底前 1bp。Earnings contracts：Cboe 二元，需期权许可。免责编号 5972263。加密批准在 CT/NY/CA 必须开启。

**5 月开放稿（已打开）。** MCP BYO-agent；独立账户；当时 equities-only beta。免责比营销更重：「Robinhood does not control, supervise, monitor, recommend, or audit these AI agents. Once your data is shared with an AI provider of your choice, it leaves Robinhood's security environment。」「Customers are responsible for…」「You assume all risk。」这段 9 月产品页几乎原样保留——说明法律形态没从「第三方 agent + 顾客本人」改成「RH 管的顾问」。

**产品页 agents（已打开）。** 「From idea to agent in seconds」「Loops … Coming soon」「Trade approvals … on by default」「Connect external agents via MCP」。底部仍称「third-party AI agent」。站内模型若由 RH 代开账单，和「third-party / we don’t audit」之间有张力。

**Yahoo Finance（已打开，Hollerith）。** 独立于新闻稿的采访点：① 随机分周 rollout，Summit 与会者立即开通；② Anthropic + OpenAI；③ Luna 今年余下免费；④ 拒答与模型商分成；⑤ **尚未比较 agentic 与非 agentic 投资结果**；⑥ Fatehpuria「100x easier → 15 万到数百万」。

**CoinDesk / MarketBeat / Investing.com。** CoinDesk：Loops = standing instructions；与永续、周末盘同场。MarketBeat：zero-data-retention 与实验室协议、对话保持私密（公司自称，未见协议文本）。Investing.com 现场讲稿：Fatehpuria 承认 MCP「complicated… multiple devices… slow and brittle」，这是做站内 Agents 的内部理由；演示称「create it in less than 60 seconds」。

**Finder（7 月，MCP 期）。** 重要未在 Summit 强调的点：agent 可读全部账户数据（含账号），只能在 agentic 账户交易；IRA 不可；当时鉴权 desktop-only。若 9 月站内版仍保留跨账户读权限，隐私边界比「独立账户」营销更宽。

**产业对照。** Public.com 3/31 先做 agent 交易。JPMorgan 的 agent 是对内覆盖客户，不是把下单权交给零售模型。Barron’s：Schwab sweep 0.01% vs 货基约 3.44%，AI 搬家现金是春季抛售叙事。不能把春季股价叙事直接当成 9/29 因果，除非打开 WSJ。

## 7. Contradictions
1. **「Coming soon」vs 已在现场开通。** 主帖对全球观众写 Coming soon；Yahoo 写 Houston 立即开通、其余随机。营销时间线与可用性时间线不是同一句话。
2. **「安全默认开」vs「可一键关掉批准」。** 产品把 default-on 当安全故事；真正 24/7 Loops 的卖点需要用户关掉批准。安全控件和自动化卖点互相拆台。
3. **「独立账户」vs「读全部账户」。** 下单沙盒是真的；Finder 记录的跨账户只读在 9 月稿里被低调处理。数据离开 RH、受模型商条款约束——与 MarketBeat「zero-data-retention / private」并读，需要协议原文才能和解。
4. **「我们不审计 agent」vs「我们在 App 里卖模型位」。** 5 月免责针对 BYO Claude/ChatGPT。 9 月 RH 代选 OpenAI/Anthropic 并代收费，仍用同一套「third-party / not responsible」。法律形态像 BYO，产品形态像托管。
5. **150k 开户 ≠ 150k 在用、更 ≠ 赚钱。** 公司自己说没做绩效对照。30M/day 是 tool use，不是单量、不是盈亏。
6. **Luna 命名。** 官网 GPT-Luna；X 交易员写 GPT-6 Luna；OpenAI 侧当日另有 Dots/Astra/Muse 口误噪音。模型身份未用两份非 RH 源钉死。
7. **监管角色。** 周末盘明确 pending review；Agents 本身被写成 self-directed + 顾客授权，不像新牌照申请。若 Loops 关掉批准后大规模自动交易，FINRA 对「谁在做投资决定」的认定可能与披露不一致——目前没有监管信函。

## 8. Mechanism
这是一条「分发」而不是「新模型」新闻。5 月 RH 用 MCP 把券商变成 agent 的交易所适配器，代价是多设备、脆连接、极客市场。Summit 把适配器藏进 App：选模型、开子账户、聊天下单，再用 Agent Apps 把 Unusual Whales / Nasdaq 等数据收月费。Loops 把「每次提示」变成 cron。经济引擎仍是交易频次 + 数据订阅 + 模型计量（Luna 免费到年底是获客补贴）+ 未来周末盘/永续的活跃交易者钱包。责任引擎刻意停在 2010 年代 self-directed 模板：沙盒资金、默认批准、免责声明。系统压力会出在三处：关掉批准后的 herd 下单、模型商 safety 拒单与券商「已授权」冲突、以及 30M tool-call 里有多少是空转。

## 9. Open questions
- 10-Q / shareholder letter 会不会把 150k 拆成 funded / 有过成交 / 仍活跃？
- 30M/day 的定义（MCP list_positions vs place_order）？
- 站内版是否仍对主账户只读？零保留协议文本？
- Luna 的官方模型卡与价格，RH 与 OpenAI/Anthropic 合同是转售还是分成？
- Loops GA 日期与「批准关闭」用户占比？
- 周末盘监管卷宗、Bruce ATS 标的名单。
- 有无 FINRA 问询把 agent 当成 discretionary。
- agentic vs 对照账户的收益/回撤——公司已承认没测。

## 10. Do not write yet
1. 「MCP 是管道，Agents 是收银台」——摩擦下降，法律责任模板没换。
2. 真正要盯的 KPI 不是 likes，是关掉批准的 Loop 数量和那些账户的成交分布是否塌缩到同一批 ticker。
3. 和 OpenAI Dots / Meta Muse 比「谁更像员工」之前，先问券商谁承担拒单和第二天反悔。
