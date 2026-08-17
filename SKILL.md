---
name: minimax-h3-prompt
description: 把用户的简单故事情节/创意，转换为符合 MiniMax H3 规范的视频生成提示词（中英双语）。覆盖 6 种模式：文生视频、单图生视频、首尾帧、多图参考（全能参考）、视频编辑、数字人/虚拟人口播。运行时先确认模式，为参考素材逐一分配角色，嵌入统一音频块与 PRESERVE/AVOID 约束，生成前用官方检查清单自检，产出「中英双语提示词 + 简短中文说明 + 一次只改一个变量迭代指引」。内置四层影像参考库 + 两维正交叠加：L1 题材镜头语法（14 个专类 + 长尾 5 主题子集共 52 子类，含母题动词/ASL/光位色温/光比/升降格/声音/翻车点）、L2 商业广告 8 种叙事结构范式（与题材正交叠乘）、L3 导演风格锚点库（western/asian 导演 + dp 摄影指导，已拆分三份）、L4 介质语法（手机自拍/监控DV/运动相机）；两维正交为视觉风格 visual-style（16 画风，含日式赛璐璐/吉卜力与美式 TV 卡通/迪士尼等动漫根）与年代 era-period（12 时代）。写作前按「题材→结构→风格」顺序加载，介质/画风/年代在确定题材后叠加；默认先给 A/B/C 三条风格路线供选择。当用户用自然语言说"帮我生成海螺/H3 视频提示词""把这个故事写成 MiniMax 提示词"或调用 /minimax-h3 时触发。
compatibility: Portable to any agent that can read local files — no external API calls, MiniMax Hub tools, or proprietary runtime required. This skill mirrors the official h3-prompt-writing skill's portability: the genre/structure/style libraries and the [Shot n] / <d> conventions are pure local markdown consumed by the agent during composition, not by H3 at inference. The final prompt fields (integrated_multimodal_description / overall_soundscape / non_diegetic_music) follow the official H3 convention so generated prompts parse correctly.
---

# MiniMax H3 视频提示词生成器

把一句简单故事 → 符合 MiniMax H3 规范的视频生成提示词（中英双语）。
依据规范文档《Minimax视频提示词生成规范与技巧.md》。

## 何时使用

- 用户给了一个故事/画面创意，想要可落地的 MiniMax H3 视频提示词。
- 用户提到"海螺 3 / H3 / MiniMax 视频提示词"。
- 用户调用 `/minimax-h3`。
- 输入可以是：纯文字故事、故事＋可选参数（时长/画幅）、故事＋素材文件（图/视频/音频）、或直接在对话里粘贴/上传的图片。

## 核心原则（来自官方规范）

1. **分层，不要糊成一整段**。官方公式：完整提示词 = 参考素材说明 + 核心创意 + 分段过程描写。绝大多数失败来自不分层的文字。
2. **六要素**嵌进核心创意句：主体 + 动作 + 环境 + 镜头 + 光线/风格 + 限制。动作必须按时间顺序写。
3. **每个参考素材都要声明角色+用途，且只用带括号的顺序 token、绝不写文件路径**。素材由用户上传，平台按上传顺序自动映射为 `<Picture 1> / <Video 1> / <Audio 1>` 等带括号固定 token；素材说明与正文一律引用该 token（如 `<Picture 1>：角色参考——锁定人脸/发型`），**不写本地/网络路径**；token 在中文版与英文版提示词中保持不变（不翻译，类型词始终为 `Picture/Video/Audio`，不用"图片/视频/音频"）。每个 token 后必须接"`——作用说明`"。未声明用途的素材会被模型无视。  **用途必须由 Agent 先用提问向用户逐一确认（见步骤 1.5 阻塞步骤），不得由 Agent 自行默认整张图全参考。**
4. **中英文都吃**。本技能默认输出**中英双语版**（中文叙述 + 英文运镜术语；英文镜头词歧义更小）。
5. **一次只改一个变量**迭代。
6. **【铁律·分镜编号】每一个分镜前必须加 `[Shot n]`**（n 为镜头序号，从 1 开始连续递增），**中文版与英文版都必须加，格式完全一致**（都写 `[Shot 1]`，不译成"镜头 1"）。单镜片子也要写 `[Shot 1]`。详见步骤 4「格式铁律」。
7. **【铁律·台词包装】镜头里人物说话时，台词本体必须用 `<d>[语言] 台词</d>` 包装**，语言标签取决于**用户输入脚本里台词原本用的语言**：中文台词 → `<d>[Chinese] 我需要下一站下车</d>`；英文台词 → `<d>[English] I get off at the next station.</d>`。**同一个 `<d>` 块在中文版与英文版提示词里逐字相同、不翻译、不改标点**。详见步骤 4「格式铁律」。

## 格式铁律（不可协商 · 每次输出都必须满足）

这两条是**输出格式硬约束**，与题材、模式、时长、粒度无关，任何一种模式（①②③④⑤⑥）都适用。违反即视为交付失败，必须重写。

### 铁律 A · 分镜必须带 `[Shot n]` 编号

- **每一个分镜的最前面**都要写 `[Shot n]`，n 从 1 开始连续递增，不跳号、不重复。
- **中英文版格式完全一致**：两版都写 `[Shot 1]` / `[Shot 2]`，**英文不写 `Shot One`，中文不写"镜头 1""第 1 镜"**。
- 与时间戳共存时，**`[Shot n]` 在最前，时间戳紧随其后**：
  - 中文：`[Shot 3] 4.2–5.6s：MS 中景。她抬手指向餐桌。镜头随手势向右摇。`
  - 英文：`[Shot 3] 4.2–5.6s: MS. She raises her hand pointing at the table. Camera pans right with the gesture.`
- **不带时间戳时同样要写**：`[Shot 1] MCU 中近景。她抬头微笑。镜头极缓推入。`
- **单镜（一镜到底）也要写 `[Shot 1]`**，不能因为只有一个镜头就省略。
- 编号是提示词正文的一部分，**必须在可复制代码块内**，不是给用户看的注释。

### 铁律 B · 台词必须用 `<d>[语言] 台词</d>` 包装

- 只要镜头里有人物说话（对白、独白、旁白由角色说出、口播、唱词），**台词本体必须写成**：
  - 中文台词：`<d>[Chinese] 我需要下一站下车</d>`
  - 英文台词：`<d>[English] I get off at the next station.</d>`
- **语言标签由用户输入脚本的台词语言决定，不由提示词版本决定**：
  - 用户脚本里台词是中文 → 中文版和英文版**都**插入 `<d>[Chinese] 中文原句</d>`；
  - 用户脚本里台词是英文 → 中文版和英文版**都**插入 `<d>[English] English line.</d>`；
  - **禁止为了"英文版"把中文台词翻译成英文**，也禁止把英文台词译成中文。台词是要被模型念出来的音频内容，翻译即改词。
- **只包台词本体**，"她说 / She says" 这类说话动作描写留在 `<d>` 外面：
  - 中文：`[Shot 2] CU 特写。她笑着说 <d>[Chinese] 我今天太高兴了</d>，视线落向画外左侧。`
  - 英文：`[Shot 2] CU. She smiles and says <d>[Chinese] 我今天太高兴了</d>, gaze off-frame left.`
- **不再用引号写台词**（旧写法 `她说："你来了。"` 已作废），一律用 `<d>` 包装。
- 多句台词分属不同镜头时，**各自放在所属 `[Shot n]` 段落内**，不要把整段台词堆在开头。同一镜头内多句可写多个 `<d>` 块。
- 台词只包一次，**不要在 `[PRESERVE]` 里重复整句**；`PRESERVE` 只写"口型与 `<d>` 内台词严格对齐"这类约束。
- 若用户脚本里**混用中英**（如中文对话夹一句英文），按**每句台词各自的语言**分别打标签。

### 说话人稳定 ID（多说话人必做 · 官方约定）

当视频有 ≥2 个会发声的角色（对白、合唱、群声、画外音），给每个发声源分配**全局稳定 ID** `(S1)` `(S2)`，多人同说用复合 `(S1,S2)`。规则（与官方 `h3-prompt-writing` 一致）：

- **首次出现**时在视觉/音频语境里给足身份锚点（角色类型、年龄、性别、是否在画内、音高、音色、语速、口音），把"说话人识别语 + ID + 动作"写在 `<d>` **外面**，`<d>` 内只放语言标签与原台词：
  - 中文：`[Shot 2] CU。扎马尾的年轻女孩（S1）笑着说 <d>[Chinese] 我今天太高兴了</d>，视线落向画外左侧。`
  - 英文：`[Shot 2] CU. The young girl with a ponytail (S1) says with a light, breathy voice, <d>[Chinese] 我今天太高兴了</d>, gaze off-frame left.`
- **ID 跨镜不变**：同一发声源在后续每个镜都复用同一个 `(Sx)`；**从不发声的角色不分配** ID。
- **参考主体同时发声**：当说话人正是参考素材锁定的主体，写 `<Subject N> (Sx)`（见步骤 4 多图/数字人模板）。
- **画外音（voiceover）**：用 `says in an off-screen voiceover`，并在 `<d>` 后立刻声明画内角色嘴唇保持闭合：
  - 英文：`(S1) says in an off-screen voiceover: <d>[Chinese] 我仍记得那条路</d> while his lips remain completely closed.`
- **台词跨镜延续 / 被截断**：同一句台词跨切点时，在两端连接处各写 `<scenetrans>` 并声明"音频跨镜连续"（continues seamlessly across the cut / carries over from the previous shot）；台词在片尾被截断时用 `<cutoff>`。

## 工作流（严格按顺序）

### 步骤 0 · 先确认模式（必须，不能自动判断）

开场就问用户要哪种模式。用户即使带了素材，也可能想纯文生（借图做参考却要文生风格），所以**不要**自动判断，先问。

展示 6 种模式与适用场景，让用户选：

| 模式 | 是否需要素材 | 适用场景 |
|---|---|---|
| ① 文生视频 | 否 | 纯文字创意、无参考图/视频 |
| ② 单图生视频 | 是（1 张图） | 让一张图里的人物/产品动起来，图作首帧 |
| ③ 首尾帧 | 是（1–2 张图） | 产品展示、状态变化、场景转换，锁住开头与结尾画面 |
| ④ 多图参考（全能参考） | 是（图/视频/音频混合） | 手上有明确资产要保留（脸、运镜、嗓音、风格图） |
| ⑤ 视频编辑 | 是（源视频） | 对已有视频做替换（换物体/换背景/换对白），保持运镜光线背景 |
| ⑥ 数字人 / 虚拟人口播·唱歌 | 是（1 张角色图，可选声音/背景） | 虚拟人/数字人口播、带货、讲解、新闻播报、唱歌/MV/虚拟偶像；锁定形象、脚本原文写入、口型对齐、肢体动作丰富、镜头合理切换卡声画节拍 |

**素材与模式不匹配的处理**（硬规则）：
- 用户选了需素材模式（②③④⑤⑥）却**没传任何文件** → 提示"该模式需要上传 [具体素材]，否则无法锁定主体/运动"，并询问是否改走①文生视频。不要硬生成不可控结果。
- **音频不能作为唯一参考**：若用户只给音频，必须要求至少补一张图或一段视频。

### 步骤 1 · 素材收集与能力感知（Q18 / Q19）

确定模式后处理素材：

- **内联图片（用户粘贴/上传、Agent 已可见）**：若当前运行时具备视觉读图能力（如 WorkBuddy/Trae/Codex/Claude Code 配视觉模型），**主动读图**，提取人物/物体/场景特征（性别、年龄、发型、服饰、体型、表情、标志性配饰、材质、颜色、构图），写入"参考素材说明"的对应角色行与核心创意的主体描写，再让用户确认或修正。这是本技能相比纯文本接口的最大优势。
- **无视觉读图能力时（纯文本运行时）**：明确告知"我暂时看不到这张图"，请用户用文字描述人物/物体特征（仍按 `<Picture 1>` 等带括号顺序 token 写素材说明，由用户自行对应上传顺序）。**绝不编造图中内容，也不要让用户填路径**。
- **视频素材**：H3 不能直接"看懂整段视频"。引导用户截取关键帧（首帧/动作帧/尾帧）作为图片上传，或用文字描述运动。
- **编号与引用**：按用户上传顺序用 `<Picture 1 / Video 1 / Audio 1>` 带括号顺序 token 在素材说明与正文就地引用；**写 token，不写路径**。
- **只列实际文件**：参考素材说明块只写用户实际提供的文件，不强制要视频/音频；缺哪类就不写哪类行。
- **文件上限**：最多 9 张图 / 3 段视频 / 3 条音频；视频与音频各自总时长 ≤ 15s。

### 步骤 1.5 · 确认素材用途（⚠️ 阻塞步骤 · 硬规则）

- **这是硬规则，不是建议**：用户每上传一张图/视频/音频，**必须先用一句话向用户询问这张素材具体要参考/承担什么角色**，并**等待用户明确答复**；**未逐一确认前禁止进入步骤 4 写提示词**。用户说"随便/你定/按你上次那样"才算确认，沉默或只上传了文件不算。
- **为什么必须问（血泪翻车点）**：模型会学习参考图的**整体构图**。若把整张图默认当成全图参考，图中**非用户意图的元素**（背景里的其他人物、包围/战斗状态、无关物件、特殊光线）也会被一并复现，造成"赵云被魏军包围""莫名出现第二个人"等翻车。**默认不要整张图全参考，必须拆到具体元素再确认**。
- **每张素材必须明确到一个用途**（从下方「参考素材角色词典」选，可多选但需用户确认）：首帧 / 尾帧 / 角色参考（锁定某人脸或形象）/ 物体参考（锁定产品道具）/ 场景参考（锁定地点）/ 风格参考（匹配观感）/ 构图参考（取景）/ 动作参考（锁动作，来自视频）/ 运镜参考（锁镜头，来自视频）/ 声音参考（锁音色）。
- **多元素图必须显式拆分（关键防翻车）**：当一张图包含多个元素（如「主体人物 + 背景 + 图中其他人物/战斗/包围」），必须问清**「参考其中哪个元素、忽略哪些」**。示例：一张「赵云骑白马陷于魏军包围」的图，需让用户明确「只参考赵云本人（银甲白马/白长发/婴儿/布囊/长枪），忽略图中的魏军士兵、火光、包围圈与战斗姿态」——否则模型会把包围场景一起复现进视频。
- **确认后落到 `[参考素材说明]`**：每张素材写一行，格式 `<token>：<用途>——<具体要保留/提取的特征>；（若图中含需忽略的元素）并显式声明"忽略 <图中其他元素>"`。多元素图的"忽略声明"必须写入，不可省略。

### 步骤 2 · 补齐单薄信息

若用户故事只有一句话（如"雨夜女孩奔跑"），**主动追问最关键的 1–2 个问题**补全——从【主体外貌 / 动作细节 / 环境 / 镜头 / 声音】里挑最缺的问，不过度审问。例如问："女孩穿什么？奔跑中发生什么？镜头怎么拍？" 得到答复后再生成。

### 步骤 3 · 确认时长与画幅（⚠️ 阻塞步骤 · 硬规则）

- **这是硬规则，不是建议**：在步骤 0 选定模式后，必须先用一句话向用户确认「时长」与「画幅」，并**等待用户明确答复**；**未确认前禁止直接套用默认值进入步骤 4 写提示词**。用户说"随便/你定"才算确认，沉默或只给了故事不算。
- **时长**：所有模式都向用户确认（默认 10s，可改）。
- **画幅**：
  - ① 文生 / ② 单图 / ④ 多图参考 / ⑤ 视频编辑 / ⑥ 数字人 → 用户确认（可选 21:9 / 16:9 / 4:3 / 1:1 / 3:4 / 9:16）。单图模式即使图只是参考人物形象，画幅仍要确认；数字人默认 9:16 或 16:9。
  - ③ 首尾帧 → 由素材决定，不另设。
- 画幅与时长是**必须写进提示词骨架首行的硬字段**（统一用 `[时长/画幅]`，如 `10s / 16:9`）。所有模式（①②③④⑤⑥）的交付物都不得省略该字段——这是防止“已向用户确认却在输出里丢失”的核心约束。末尾的简短中文说明也照常记录一份。

### 步骤 3.4 · 题材语法加载（必做 · 第一优先）

**任何故事都要先过这一步。** 加载顺序固定为 **题材 → 结构 → 风格 → 正交维度**，不能跳级。

1. **先读 `references/genre-index.md`**（一页，极小）。
2. 按索引的关键词表**命中题材** → **只加载那一个** `references/genre/<题材>.md`（题材层只取一个，避免参数打架）。
   - 命中不了 → 用索引第六节的**插值指南**，从最近的核心题材按「节奏/光色/景别/结构」四维度拼。
   - **题材层不要一次加载多个文件**（浪费上下文，且参数会打架）。
3. 若出现 **广告 / TVC / 品牌片 / 卖点 / 转化 / 信息流 / slogan / logo** → **额外**加载 `references/commercial-ad-structures.md`，与题材语法**正交叠乘**（题材管风格，结构管顺序）。
4. 只有用户**点名导演/影片/"XX 那样的感觉"**时，才走步骤 3.7 读 L3 导演库。
5. **正交维度叠加（题材确定后按需加载，不受「只加载一个」限制）**：
   - 用户点名**画风**（吉卜力/迪士尼/水墨/像素/赛璐璐…）→ 加载 `references/visual-style.md`（画风层，须写进提示词首句）。
   - 用户点名**年代**（80 年代/民国/赛博 2099/废土…）→ 加载 `references/era-period.md`（年代层，色板/颗粒/画幅偏移）。
   - 用户点名**介质**（手机自拍/监控 DV/运动相机）→ 加载 `references/medium/*.md` 对应文件（介质层，会覆盖部分运镜与画质设定）。
   - 这三层与题材**正交**，是「在已加载题材文件之外**额外加载**」，触发关键词与写法见 genre-index 第五、六节。
   - 做**跨题材插值**时还需加载 `references/genre/long-tail-genres.md`（跨题材综合示例与插值硬规矩）。

**为什么必须先读题材文件**：题材文件给的是**具体可执行参数**（ASL 秒数、开尔文色温、光比、fps、光位名、禁用运镜）与**母题动词**。跳过它写出来的提示词必然是"电影感/高级感"这类模型无法执行的空话。

**参数必须"以效果织入"而非"以文字列出"**：读到的具体参数（色温开尔文、光比、ASL、禁用运镜、母题动词）必须落到提示词的对应字段里——色温/光比写进 `integrated_multimodal_description:` 的光线描写与 `[PRESERVE]`；禁用运镜写进 `[AVOID]`；母题动词写进 `integrated_multimodal_description:` 的主体与 `[Shot n]` 动作。这样参考文件既"起作用"又"不污染可复制提示词"（见步骤 6 纯净化规则）。

### 步骤 3.5 · A/B/C 三方案（默认执行 · 灵感点火）

**除非用户已明确指定风格、导演或给了具体画面描述**，在写完整提示词前先甩三条**截然不同**的路线，每条 ≤3 行：

```
A · 写实纪实向  —— 一句话画面 ｜ ASL / 光色 / 关键手法
B · 风格化作者向 —— 一句话画面 ｜ ASL / 光色 / 关键手法
C · 极简高级向  —— 一句话画面 ｜ ASL / 光色 / 关键手法
```

规则：
- 三条**必须真的不同**（节奏 + 光色 + 景别策略三者都要有差异），不能是同一方案换措辞。
- 参数从步骤 3.4 加载的题材文件里取，不要凭空编。
- 用户说"随便 / 你定" → 选 A，并用一句话说明理由。
- 用户已点名风格/导演，或已给出足够具体的画面 → **跳过此步**直接写。
- 三条路线各自可附一颗该题材文件里的**灵感种子**做具体化。

### 步骤 3.6 · 广告结构叠加（命中广告关键词时）

从 `commercial-ad-structures.md` 的 8 种范式里**选一种**（问题—解决 / 一镜到底日常 / 对比 / 情感微电影 / 产品即主角 / 反转幽默 / KOL 口播 / 快闪节奏），按其结构曲线切分时间轴，再把题材语法的光色节奏填进去。

三条广告硬约束必须落到提示词里：**① 第 1 镜是钩子不是 logo ② 产品英雄镜 + PRESERVE 锁产品外观 ③ 最后一镜能停住**。

### 步骤 3.7 · 风格锚点加载（L3 · 用户点名导演/影片时才读）

若用户提到**任何导演名、影片名、"某某那种感觉"、"电影感/广告感/港片味/武侠味"**，
**先读 `references/director-anchors-western.md` 或 `director-anchors-asian.md`**（电影/电视剧/广告导演，按华语/亚洲 vs 欧美选），把风格拆成可执行参数再写；摄影指导风格另读 `references/dp-cinematographer-anchors.md`。

判定关键词：导演名（诺兰/王家卫/韦斯·安德森/芬奇/张艺谋…）、片名、"XX 风格"、"XX 那种感觉"、"电影质感"、"广告大片感"、"复古胶片"、"港风"。

三条硬规则（不读就会犯）：
1. **只写导演名字无效** —— 必须拆成「镜长 + 景别 + 运镜 + 色温 + 光位 + 质感」写进正文，导演名只放风格句**末尾**做附加锚点。
2. **最多叠加 3 个特征、最多借 2 位导演**，且**一个维度只服从一位**（色彩听 A、运镜听 B，不能抢）。
3. **禁忌组合要拦**（如库布里克+快切、韦斯·安德森+手持、芬奇+暖阳柔光），命中就提醒用户并给替代方案。
4. **题材铁律 > 导演风格（冲突裁决）**：导演签名手法若与步骤 3.4 加载的题材铁律冲突，**一律以题材为准，裁掉冲突项、只借不冲突的维度**，并在交付物里附一张「冲突裁决说明」表（导演签名 ｜ 是否采用 ｜ 原因）。
   典型冲突：王家卫手持广角/抽帧拖影 × 美食（禁手持、需高锐度油光）；芬奇冷调 × 美食（冷色杀食欲）；杜琪峰静止 × 动作快切；诺兰宏大交叉剪辑 × 产品静物。

导演库已拆分为三份：`director-anchors-western.md`（欧美电影/剧/广告导演十维拆解 + 禁忌组合）、`director-anchors-asian.md`（华语与亚洲导演，含王家卫/张艺谋/徐克等）、`dp-cinematographer-anchors.md`（摄影指导，按光影/色调/器材维度拆解）。每份含十维拆解（分镜·运镜·节奏·升降格·色彩·光影·胶片画幅·音乐·表现手法·招牌镜头）、中英双语锚点句、ASL/色彩/光比横向对照、允许与禁止的组合规则。

### 步骤 3.8 · 动作场景专项校验（打斗/追逐/对决必做）

若故事属于**高强度动作场景**（武侠打斗、格斗、追车、追逐、竞技对抗、战争），
步骤 3.4 会命中并加载 `references/genre/action-wuxia.md`；**该文件必须读完再进入步骤 4**。

判定关键词：打斗 / 对决 / 交手 / 厮杀 / 追逐 / 追车 / 格斗 / 快节奏动作 / 快切 / 武侠 / 动作片。

该参考解决三个高频翻车点（不读就会犯）：
1. **均匀等分时间戳**（0–2 / 2–4 / 4–6…）→ 机械感，是"电视剧节奏"不是电影节奏。必须**长短交错**。
2. **景别扁平**（全程中景近景）→ 必须做 ELS/WS/MS/MCU/CU/ECU 阶梯调度，**相邻镜头景别至少跳 2 级**。
3. **缺少动作片语法** → 需要动作中切、升格重音（speed ramp）、甩镜转场、插入空镜、轴线一致、亮相定格。

硬约束速记：**镜头数 ÷ 时长 ≤ 1.5 镜/秒**（10s 建议 11–13 镜）；ASL 落在 0.7–1.0s；开场静、结尾静。

### 步骤 4 · 套骨架生成（中英双语）

统一三段式骨架，按模式切换细节。下方为**可复制代码块**结构（中文版与英文版结构完全一致，仅叙述语言不同）：

```
[参考素材说明]      ← 仅 ②③④⑤⑥ 模式；① 文生省略此块。只写顺序 token + 作用，绝不写路径
<Picture 1>：<角色类别——需保留/提取/匹配的具体特征>
<Video 1>：<角色类别——需提取/匹配的具体特征>
<Audio 1>：<角色类别——需匹配/复用的具体内容>
（token 固定英文、不随中英文变化；缺哪类就不写哪行；类别名见下方角色词典，作用写具体）

integrated_multimodal_description:   ← 官方主字段名（中英双语都用这个英文标签）
[时长/画幅]         ← 必写首字段！值为步骤 3 已确认的时长+画幅（如 10s / 16:9），不得留空或省略
[主体外貌] 位于 [环境]，[动作]，[运镜]，[光线/氛围]。（首句建议带风格标签：Live-action, cinematic / 2D-animated / 3D CG…）
[Shot 1] [景别]。[动作]。[运镜]。[声音]。（第 1 镜不带时间戳，直接写动作；说话人加 (S1) 稳定 ID）
[Shot 2] At 00:03.500, the camera cuts to [景别]。[(S1) 动作，含"她说"] <d>[Chinese] 台词原句</d>。[运镜]。[声音]。（第 2 镜起用绝对时间戳 At MM:SS.mmm + 官方切镜动词；台词用 <d> 包装）
（每个分镜必带 [Shot n]，铁律 A；台词必用 <d>[语言]…</d> 包装，铁律 B；多说话人用 (S1)(S2) 复合 (S1,S2)）

overall_soundscape: [具体声音，或 N/A]
non_diegetic_music: [风格/情绪，或 N/A]

PRESERVE: [需保持不变的：身份/颜色/构图/产品细节……]
AVOID: [需规避的：面部变形/闪烁/跳变/多余手指/相邻镜头主体或事件无铺垫跳变……]
```

> **字段名约定（与官方 `h3-prompt-writing` 完全一致）**：主体描述与分镜统一放在 `integrated_multimodal_description:` 之下；`overall_soundscape` / `non_diegetic_music` / `PRESERVE` / `AVOID` 都是**英文标签**，中英两版都用同一标签（标签不翻译）。**不要再**用 `[核心创意]` / `[分段过程]` / `[声音设计]` 这类中文标签包住正文——它们不在官方字段表里，H3 无法识别，会拖累解析。风格标签建议写英文（`Live-action, cinematic` / `2D-animated` / `claymation` / `vintage film`…），与官方示例一致；中文版也可写中文风格词。

**通用规则：**
- **文生视频（①）省略「参考素材说明」块**，视觉描写写得更细（至少覆盖：主体外貌 + 场景 + 动作 + 风格）。
- **音频块所有模式统一带**。无音频文件时纯文字描述 `overall_soundscape` 声景，或写 `N/A`；不要音乐写 `non_diegetic_music: N/A`。**不要一行要配乐另一行禁音乐**（官方明列失败模式）。
- **立体声左右定位为可选项**：在声音设计里提示"可指定左/右声道位置"（如 footsteps pan left→right），不强制。
- **分镜编号（铁律 A · 见上文「格式铁律」）**：每个分镜前必须写 `[Shot n]`，中英文版格式一致（都写 `[Shot 1]`），与时间戳共存时 `[Shot n]` 在前、时间戳紧随。单镜也写 `[Shot 1]`。
- **对白（铁律 B · 见上文「格式铁律」）**：台词本体必须用 `<d>[语言] 台词</d>` 包装，语言标签取决于**用户脚本里台词的原语言**（中文台词 → `[Chinese]`，英文台词 → `[English]`），**中文版与英文版插入的 `<d>` 块逐字相同、绝不翻译**；"她说 / She says" 等说话动作写在 `<d>` 外。示例：`[Shot 2] CU 特写。她笑着说 <d>[Chinese] 我今天太高兴了</d>。` / `[Shot 2] CU. She smiles and says <d>[Chinese] 我今天太高兴了</d>.`
- **PRESERVE / AVOID：所有模式默认带**（① 文生可写"无特殊约束"）。参考/首尾帧/数字人模式强制锁身份。
- **时间戳分段（官方格式）**：`[Shot 1]` 不带时间戳；**第 2 镜起用绝对时间戳 `At MM:SS.mmm`**（如 `At 00:03.500`），并紧跟官方切镜动词（`the camera cuts to` / `the shot cuts to` / `the shot transitions to` / `the shot switches to`；用户明确要求时可用 cross-dissolve / fade / wipe）。中文版可用对应中文动词（"镜头切到"/"镜头转向"/"镜头过渡为"）。切镜必须引入新信息（主体/空间/状态/视角/时间之一）。仅改距离或轻微角度时优先用运镜而非切镜。
  **动作场景例外**：打斗/追逐必须分段，且时间戳**精确到 0.1s**、**镜头时长长短交错**（禁止等分），并为每镜写全「景别 + 单一动作 + 单一运镜 + 切换方式/速度标记」四件套（详见 `references/genre/action-wuxia.md`）。——**动作戏默认详细逐镜头分镜，不向用户询问粒度选择**（详见该文件「提示词粒度」一节）。
- **运镜**：一个镜头/节拍只用一种主要运镜，把运动写成具体可见动作 + 方向 + 幅度/速度，并与画面揭示绑定，不要用空泛质量词。多镜头快切时，此规则按**单镜**执行——每镜一种运镜，镜头之间可以不同。
- **画面内文字（on-screen text）**：实际出现在画面里的横幅/招牌/字幕/霓虹字，用**英文双引号**原样保留、不翻译（如 `a red neon sign reading "营业中"`）。只包可见文字本身，描述文字性质与位置放在引号外。
- **镜头连贯性 / 因果链（多镜必做 · 高频翻车点）**：一旦 `integrated_multimodal_description` 内写了 ≥2 个分镜，相邻镜头 Shot N → Shot N+1 必须构成连续的因果链，**禁止"断点跳转"**。逐对校验三条：
  - **主体连续**：Shot N+1 的主体必须是 Shot N 已出现/已建立的主体，或 Shot N 画面中已可见/提及的次要主体。**禁止凭空冒出全新主体**（新物体/新角色/新场景元素）。若必须引入（如撞向某建筑），须让 Shot N 先以空镜/摇镜/台词铺垫它的存在与方位。
  - **动作因果**：Shot N+1 的动作必须是 Shot N 动作的**直接结果或自然延续**，不能无故中断、替换为另一条无关事件线（上一条动作线必须被交代去向）。
  - **时空连续**：镜头间空间关系、时间流向默认连贯，除非有显式转场（空镜、切场景、字幕、时间跳）。
  - 写之前先在草稿排一条**事件因果链**（用箭头连），每出现一个新元素就标它在哪一镜被"建立"。
  - **反面教材（必须杜绝）**：上一镜"汽车追近摩托、前保险杠贴上摩托后轮开始撞击" → 下一镜"汽车撞到了亭子"。错在两点——① 亭子是凭空冒出的物体（上一镜从未建立它的存在与位置）；② "撞击摩托"这条动作线被无交代地吞掉、替换为撞亭子。正确写法：上一镜"前保险杠贴上摩托后轮、撞击发生" → 下一镜"摩托急扭把闪避、汽车擦过失控，撞向路边**已在画面一侧出现过的**报刊亭"，或"汽车撞击后 rebound 方向偏移、追尾前方卡车"。

**产出两份**：一份**中文版**（中文叙述，供你阅读核对），一份**英文版**（英文叙述 + 英文运镜术语 + 英文风格标签）。**两份结构完全一致**，都使用官方字段名 `integrated_multimodal_description:` / `overall_soundscape:` / `non_diegetic_music:` / `PRESERVE:` / `AVOID:`。**提交给 MiniMax H3 的正式版本是英文版**——官方规范明写"提示词正文用英语书写、台词/歌词/画面文字保留原始语言"，英语正文在 H3 上的解析与表现更稳定；中文版用于你确认人物、动作、台词是否写对。若只给中文版，表现可能不及英文版。

### 步骤 5 · 生成前自检（官方检查清单，逐条过）

生成最终提示词前，逐条核对，不满足就改：

1. 只保留一个主要主体 + 一个主要动作。
2. 动作按时间顺序写。
3. 环境只写会影响镜头的部分。
4. 第一次只用一种主要运镜。
5. 描述**可见**光线/风格，不写"高质量"等空泛词。
6. 需要时明确保持身份/颜色/布局/产品细节。
7. 已向用户逐一确认每份素材的用途（多元素图已显式拆分「参考什么 / 忽略什么」），而非由 Agent 默认整张图全参考。
8. 写了清楚的结束状态（最后停在哪）。
9. 全文无互相冲突的要求（尤其音乐开关、运镜静止 vs 运动）。
10. 计划"看到结果后一次只改一个变量"。

**格式铁律追加 3 条（所有模式 · 不满足禁止交付）**：
- ⓐ **每个分镜是否都以 `[Shot n]` 开头**、序号从 1 连续递增无跳号，**且中文版与英文版都写了、格式一致**（都是 `[Shot 1]` 而非"镜头 1"/`Shot One`）？单镜是否也写了 `[Shot 1]`？`[Shot n]` 是否在时间戳之前？第 2 镜起是否用了绝对时间戳 `At MM:SS.mmm`？
- ⓑ **所有台词是否都用 `<d>[语言] 台词</d>` 包装**、语言标签是否与**用户脚本里台词的原语言**一致？**中英两版的 `<d>` 块是否逐字相同、没有被翻译**？是否只包了台词本体（"她说/She says"留在外面）、没有残留引号写法、没有在 PRESERVE 里重复整句台词？多说话人是否加了稳定 `(Sx)` ID？
- ⓒ **是否用了官方主字段 `integrated_multimodal_description:` 包裹主体描写与全部分镜**（中英两版都用此英文标签，不写 `[核心创意]`/`[分段过程]` 这类中文标签）？`overall_soundscape:` / `non_diegetic_music:` 是否为**独立字段行**（不在正文里混写）？提交 H3 的版本是否为**英文版**？

**镜头连贯性追加（所有多镜 / 分段场景）**：① 逐对检查相邻镜头——Shot N+1 的主体是否在 Shot N 已出现/已建立（无凭空冒出的新物体/新角色）？② Shot N+1 的动作是否承接 Shot N 的结果/状态，而非无故中断、替换为另一条事件线？③ 任一为否 → 重写 Shot N（铺垫新元素的存在与方位）或重写 Shot N+1（改为承接上一条线），**禁止"断点跳转"**。典型反例：上一镜"汽车撞击摩托" → 下一镜"汽车撞亭子"（亭子凭空出现、撞摩托的线被吞掉）。

**风格锚点追加 3 条**（用户提了导演/风格时）：① 风格是否已拆成可执行参数而非只写人名；② 叠加的导演是否 ≤2 位、特征 ≤3 个；③ 是否命中 `director-anchors-western.md` / `director-anchors-asian.md` 的禁忌组合节。

**题材校验追加 3 条**（所有场景）：① 是否已加载对应 `genre/*.md` 并取用了它的**具体参数**（ASL 秒数 / 色温开尔文 / 光比 / 光位 / 禁用运镜），而非写"电影感"这类空话；② 是否用了该题材的**母题动词**而非形容词堆砌；③ 是否逐条过了该题材文件末尾的**自检清单**，尤其"绝对禁止"项（如美食的顶光/冷调、汽车的静止车、恐怖的看得太清）。

**广告追加**：命中广告关键词时，过 `commercial-ad-structures.md` 末尾的 10 条广告专用清单。

**动作场景追加 10 条**：见 `references/genre/action-wuxia.md` 第九节（镜长是否长短交错、有无 <0.9s 爆发镜、有无升格重音、景别是否跳 2 级、开场结尾是否静、镜头密度是否 ≤1.5 镜/秒、轴线是否写进 PRESERVE 等）。动作场景两套清单都要过。

### 步骤 6 · 交付物

向用户输出（**重要：提示词代码块要能原样复制进视频工具，参考溯源必须放在代码块之外**）：

1. **可复制提示词（独立代码块 · 纯净化 · 硬规则）**：每段提示词放进独立 ``` 代码块，块内**只含标准字段**（`[参考素材说明]` / `[时长/画幅]` / `[核心创意]` / `[分段过程]` / `[声音设计]` / `[PRESERVE]` / `[AVOID]`）。**严禁把参考文件名、素材加载过程、溯源说明写进代码块**——多一个字都会污染进 MiniMax H3 的输入。参考文件的具体参数只能以"效果"形式隐式织入字段（见步骤 3.4）。

2. **生成依据 / 参考溯源（独立段落 · 明确标注不复制）**：在代码块**之外**另写一段，标题用「生成依据」，首行写清：**"以下内容为生成依据说明，请勿复制进视频工具"**。逐条列出：① 本次读取了哪些参考文件（如 `references/genre/war-military.md`、`references/era-period.md` 中国古代节）；② 借用了其中哪些**具体参数**（如"禁用轨道稳定推拉""冷兵器色温 1800–2000K""中国古代日光 5000–5500K / 2.35:1 / 85mm 长焦"）；③ 这些参数落在了提示词哪一段（如"色温写进 0–2s 光线描写，禁用运镜写进 `[AVOID]`"）。这一段是给你看"参考文件确实起作用"的证据，**不属于交付给工具的提示词**。

3. **简短中文说明**：本次模式 + 素材分工 + 时长/画幅 + 关键约束（PRESERVE/AVOID 要点）。

4. **迭代指引**："看到结果后，一次只改一个变量（见下方单变量修复表），重新生成对比。"

## 参考素材角色词典（12 类，只标注用到的）

| 角色类别 | 用途 | 推荐写法（顺序 token + ——作用，不写路径） |
|---|---|---|
| 角色参考 character | 锁定一张脸/形象 | <Picture 1>：角色参考——锁定这位女性的脸、发型、身材比例 |
| 物体参考 object | 锁定产品/道具 | <Picture 2>：物体参考——锁住香水瓶、含标签 |
| 场景参考 scene | 锁定地点 | <Picture 3>：场景参考——保留阴天石板巷 |
| 关键帧 keyframe | 锁定一帧 | <Picture 1>：首帧——锁住开场姿态/构图；<Picture 2>：尾帧——锁住结束姿态 |
| 声音参考 sound | 锁定音色 | <Audio 1>：声音参考——古琴古典配乐音色 |
| 动作参考 action | 从视频锁动作 | <Video 1>：动作参考——使用其中的剑舞动作 |
| 运镜参考 camera | 锁镜头运动 | <Video 1>：运镜参考——跟它的推镜节奏 |
| 风格参考 style | 匹配观感 | <Picture 1>：风格参考——保留平涂色板与粗墨线 |
| 构图参考 composition | 匹配取景 | <Picture 1>：构图参考——匹配取景与版面 |
| 音频复用 audio reuse | 音轨直接用 | <Audio 1>：音频复用——把这条音轨直接用作视频声音 |
| 视频编辑 video edit | 待修改视频 | <Video 1>：源视频——保留其人物/运镜，仅改背景 |
| 分镜稿 storyboard | 按故事板生成 | 分镜稿：按故事板画面生成镜头 |

## 六种模式字段模板

### ① 文生视频（省略参考块）
```
中文版：
integrated_multimodal_description:
[时长/画幅], [风格]。
[主体外貌] 位于 [环境]。
[Shot 1] 先发生 [动作1]。镜头以 [速度] 进行 [一种运镜]。
[Shot 2] At 00:0X.XXX, 镜头切到 [动作2]（若有台词：(S1) 她说 <d>[Chinese] 台词原句</d>）。[运镜]。
[可见光线/氛围]。最后停在 [明确结束状态]。
overall_soundscape：[具体声音]；non_diegetic_music：[风格 或 N/A]
PRESERVE：[…]  AVOID：[…]

英文版：
integrated_multimodal_description:
[Duration/aspect], [style].
[Subject] is in [environment].
[Shot 1] [Action1]. Camera [one camera move] at [speed].
[Shot 2] At 00:0X.XXX, the camera cuts to [Action2] (with dialogue: (S1) she says <d>[Chinese] 台词原句</d> — same <d> block as the Chinese version, never translated). [camera move].
[Visible light/mood]. End on [clear end state].
overall_soundscape: […]; non_diegetic_music: [… or N/A]
PRESERVE: […]  AVOID: […]
```

### ② 单图生视频（图作首帧 · I2VA）
```
中文版：
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description:
[时长/画幅]
[Shot 1] [主体] 先做 [第一个小动作]，再连续完成 [主要动作]（若有台词：(S1) 她说 <d>[Chinese] 台词原句</d>）。镜头进行 [一种运镜]，同时 [背景或光线变化]。
[可选结尾状态]。
overall_soundscape：[…]；non_diegetic_music：[… 或 N/A]
PRESERVE：[锁定图中特征]  AVOID：[面部变形/闪烁…]

英文版：
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description:
[Duration/aspect]
[Shot 1] [Subject] does [small action], then [main action] (with dialogue: (S1) she says <d>[Chinese] 台词原句</d> — identical <d> block, never translated). Camera [one move] while [bg/light change].
overall_soundscape: […]; non_diegetic_music: [… or N/A]
PRESERVE: […]  AVOID: […]
```

### ③ 首尾帧（图1首/图2尾 · FL2VA）
```
中文版：
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 0.00-second mark of the target video; <Picture 2> (from [Shot N]) aligns with the [X.XX]-second mark of the target video.

integrated_multimodal_description:
[时长/画幅]
[Shot 1] 使用一个连续镜头完成变化：开始时 [<Picture 1> 的姿势/服装/构图/光线]；
[中间逐步发生的动作路径]；最终准确落在 <Picture 2> 的 [姿势/状态/构图/光线]。
镜头 [一种运镜]。（一镜到底也必须写 [Shot 1]）
overall_soundscape：[…]；non_diegetic_music：[… 或 N/A]
PRESERVE：[图1图2 间应稳定的元素]  AVOID：[跳变/闪烁…]

英文版：
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 0.00-second mark; <Picture 2> (from [Shot N]) aligns with the [X.XX]-second mark.

integrated_multimodal_description:
[Duration/aspect]
[Shot 1] One continuous shot: begin in <Picture 1>'s [pose/costume/composition/lighting];
[gradual mid-path actions]; end exactly on <Picture 2>'s [pose/state/composition/light].
Camera [one move]. overall_soundscape: […]; non_diegetic_music: [… or N/A]
PRESERVE: […]  AVOID: […]
```
注意：首尾帧与 reference 素材不能混在同一请求；两帧差异不宜过大；中间必须有足够动作路径。FL2VA 通常**偏好单一连续镜头**以便模型从首帧插值到尾帧，仅在用户明确要求多镜时才拆分。

### ④ 多图参考（全能参考 · Ref2VA 简化版）
```
中文版：
integrated_multimodal_description:
[时长/画幅]
[参考素材说明]
<Picture 1>：角色参考——锁定人脸/发型/身材
<Picture 2>：物体参考——锁住颜色/扣件/材质
<Video 1>：运镜参考——跟它的推镜节奏
<Audio 1>：音频复用——把这条音轨直接用作声音

[主体] 在 [场景] 中 [动作]，[运镜风格]，[光线/氛围]。
[Shot 1] [景别]。[动作]。[运镜]。[声音，引用 <Audio 1> 节奏]。
[Shot 2] At 00:0X.XXX, 镜头切到 [景别]。[动作（有台词时：(S1) 她说 <d>[Chinese] 台词原句</d>）]。[运镜]。
PRESERVE：[每条点名要保留的特征]  AVOID：[…]
```
（进阶：若需严格锁定多个参考主体及其保留/迁移关系，改用官方 Ref2VA 六段式——`subject_definitions` / `summary` / `retention_analysis` / `detailed_description` / `overall_soundscape` / `non_diegetic_music`，标签用 `<Subject N>` / `<Picture N>` / `<Video N>` / `<Audio N>`，关系标记 `fully_preserved` / `partially_preserved` / `attribute_transfer` / `weak_reference`（音频整段复用另用 `fully_copy`，见 ⑥-B 数字人音频复用）。）

### ⑤ 视频编辑（对已有视频替换）
```
中文版：
integrated_multimodal_description:
[时长/画幅]
<Video 1> 是源视频（保留其 [人物外观/表演/运镜/时序]，仅改 [目标]）。
<Picture 1> 是 [新背景/新物体——保留其具体特征]。
把 <Video 1> 中的 [旧物体] 替换为 [新物体/新背景]，重打光使 [主光方向] 匹配新背景。
[Shot 1] [景别]。[替换后的动作]。[保留的原运镜]。
[Shot 2] At 00:0X.XXX, 镜头切到 [景别]。[替换后的动作]。
overall_soundscape：[…]；non_diegetic_music：[… 或 N/A]
PRESERVE：[源视频需原样保留的部分]  AVOID：[穿帮/光线错位…]

英文版：
integrated_multimodal_description:
[Duration/aspect]
<Video 1> is the source clip (preserve its [appearance/performance/camera/timing]; only [target] changes).
<Picture 1> is the [new background/object — preserve its specifics].
Replace [old] in <Video 1> with [new], relight to match [key light direction].
[Shot 1] [shot size]. [action after replacement]. [original camera move preserved].
[Shot 2] At 00:0X.XXX, the camera cuts to [shot size]. [action after replacement].
overall_soundscape: […]; non_diegetic_music: [… or N/A]
PRESERVE: […]  AVOID: […]
```
（例：Replace the cat in the video with a golden retriever. Keep the camera move, lighting and background unchanged. 若源视频含对白且需改词，新对白用 <d>[语言] 台词</d> 包装，语言标签按脚本原语言。）

### ⑥ 数字人 / 虚拟人口播（角色图 + 可选声音 / 背景）

> 数字人片「恐怖谷」分水岭是**形象稳定 + 随机眨眼 + 口型对齐**。命中 `long-tail-media.md` 的「虚拟人/数字人口播」「数字人进阶」「口播/知识博主」三节，必读完再生成。三节已升级为**既支持口播也支持唱歌/MV**，且允许**丰富肢体动作 + 合理镜头切换（卡在说话停顿或歌曲节拍上）**，不再是"一镜到底的固定死板机位"。开拍前先让用户**二选一写实路线或风格化虚拟形象路线**（写实做不到微表情就退风格化，别骑墙）。若用户**同时给「角色图 + 原声（本人录音 / 唱歌 / 说唱）」**要做锁脸复刻，走下方 **⑥-B 严格锁脸锁声（Ref2VA 六段式）**，按表演类型选 变体一（口播）/ 变体二（唱歌）/ 变体三（说唱）。

```
中文版：
integrated_multimodal_description:
[时长/画幅]
<Picture 1>：数字人角色参考——锁定人脸/发型/服装/虚拟形象造型，全程不变
[可选] <Audio 1>：声音参考——口播音色/语速匹配这条音轨，或唱歌/伴奏的节奏与咬字基准，或直接用作配音
[可选] <Picture 2>/<Video 1>：背景/场景参考——锁定演播厅/舞台/直播间/虚拟背景
数字人（S1）面向镜头，但允许贴合语义的丰富肢体动作：口播时手势挥动、身体前倾强调、侧身指向、小幅走动、拿起道具；唱歌/MV 时加入律动摇摆、打拍、小幅舞蹈。形象与服装全程锁定同一人。
镜头不必一镜到底——可在「说话的停顿/句尾呼吸处」或「歌曲的乐句换气处/强拍」切换景别与角度（正面 MCU → 侧 15–45° → 过肩 → 低角度仰拍 → 手部/乐器 ECU 插入镜）；每次切换主体仍是同一个数字人，切点用插入镜或景别跳变自然过渡，绝不切在咬字或歌词中途。
[Shot 1] 正面 MCU。她（S1）面向镜头微笑开口，右手小幅上抬  <d>[Chinese] 口播脚本第一句原文</d>。镜头极缓推入。
[Shot 2] At 00:0X.XXX, 镜头切到 侧 30° MS。她（S1）身体前倾强调，左手向画面右侧指向  <d>[Chinese] 口播脚本第二句原文</d>。镜头静态。
（切点落在两句之间的语义停顿处；台词逐字照抄用户脚本，不改写、不翻译、不合并）
光色以柔和正面蝶光为主（5600K，两侧 −1.5 档补光，光比 1.3:1），允许机位角度带来的光位自然偏移；避免会照出建模转折面的硬侧光/顶光。
口播 ASL 3–6s，剪辑点卡在语义停顿；唱歌随节拍，剪辑点卡在乐句换气/重拍。口型对齐误差 <80ms，随机眨眼（每 3–5 秒一次、间隔不规律），每 10s 至少一次非语义微动作。
overall_soundscape：[…]；non_diegetic_music：[… 或 N/A]
PRESERVE：[数字人形象/服装稳定，口型与各 <d> 块内台词逐字对齐、误差 <80ms，随机眨眼，主体始终是同一人]  AVOID：[形象漂移/口型错位/台词被改写或翻译/面部变形/等间隔机械眨眼/硬侧光/在咬字或歌词中途切镜]

英文版：
integrated_multimodal_description:
[Duration/aspect]
<Picture 1>: digital human character reference — preserve face/hair/costume/avatar look, unchanged throughout.
[opt] <Audio 1>: voice/music reference — match its timbre/pace or song beat & enunciation; or use directly as voiceover.
[opt] <Picture 2>/<Video 1>: background/scene reference — studio/stage/livestream/virtual set.
Digital human (S1) faces camera with semantically motivated body movement (hand gestures, lean-in to emphasize, turn to point, small steps, pick up a prop; for singing/MV add sway, beat-tapping, light choreography). Same avatar & costume locked across all shots.
Camera need not hold one take — cut on spoken pauses/breaths or on song phrase-breaths/downbeats, varying angle & size (frontal MCU → 15–45° side → over-shoulder → low-angle → hand/instrument ECU insert); subject stays the same digital human every cut, transitions hidden by inserts or size jumps, never cut mid-word or mid-lyric.
[Shot 1] Frontal MCU. She (S1) smiles into lens, right hand lifts slightly, saying  <d>[Chinese] 口播脚本第一句原文</d>. Camera pushes in very slowly.
[Shot 2] At 00:0X.XXX, the camera cuts to 30° side MS. She (S1) leans in for emphasis, left hand points frame-right, saying  <d>[Chinese] 口播脚本第二句原文</d>. Static camera.
(Cut on the semantic pause between lines; <d> blocks are copied verbatim from the user's script — never rewritten, translated or merged.)
Soft frontal butterfly key ~5600K, -1.5 stop side fill, 1.3:1; avoid hard/raking light that reveals mesh facets.
Talking-head ASL 3–6s with cuts on semantic pauses; singing cuts on phrase-breaths/beats. Lip-sync <80ms, irregular blink every 3–5s, one non-semantic micro-movement per 10s.
overall_soundscape: […]; non_diegetic_music: [… or N/A]
PRESERVE: [stable avatar/costume, lip-sync locked verbatim to each <d> block within <80ms, irregular blink, same subject every cut]  AVOID: [identity drift/mismatch/rewritten or translated lines/facial morph/robotic blink/hard light/cut mid-word or mid-lyric]
```

#### ⑥-B 数字人 + 音频复用（Ref2VA 严格「锁脸 + 复刻原声」版）

> 适用：用户**同时给「角色图 `<Picture 1>` + 一段原声 `<Audio 1>`」**，要数字人长成图里那样、且**一字不差复刻原声的表演内容 / 节奏 / 停顿 / 重音**（真人形象 + 本人声音复刻、口播搬运、给已有录音配脸、给唱歌/说唱录音配脸）。这是官方 Ref2VA 六段式的数字人落地版，比 ⑥ 默认「写脚本 + 对齐口型」更硬——身份锁 `<Picture 1>`、声音锁 `<Audio 1>`，正文**改用六段式**而非 `integrated_multimodal_description` 单块（与 ④ 进阶注记一致，是 Iron Rule C 的官方豁免场景）。下方提供三套变体，按表演类型选用：**变体一口播（讲话）/ 变体二唱歌（演唱）/ 变体三说唱（Rap）**。
> 关系标记补充：在 ④ 进阶注记的 `fully_preserved / partially_preserved / attribute_transfer / weak_reference` 之外，音频另用 **`fully_copy`**（原声完整复制：讲话·演唱·说唱的 内容 / 节奏 / 停顿 / 重音 / 总时长一字不改）。
> **Iron Rule B 豁免**：⑥-B 的讲话 / 演唱 / 说唱均由 `<Audio 1>` 承载（fully_copy），**不写 `<d>` 台词块**——语音来自音频而非书写脚本。若另需屏幕字幕 / 额外口播句，再补 `<d>[语言] …</d>`。

**变体一 · 口播（讲话）**

中文版：
subject_definitions:
<Subject 1> 是 <Picture 1> 中的主要人物，作为本段分镜中讲话的主角。
<Audio 1> 是 <Subject 1> (S1) 的完整参考音频，提供原始讲话内容、时间、节奏和停顿。

summary:
[reference generation + audio reuse] 本段保留 <Subject 1> 来自 <Picture 1> 的身份与外观，完整复用 <Audio 1> 中的讲话内容、节奏和停顿。

retention_analysis:
<Subject 1>（出现在 [Shot 1]）：fully_preserved - 人物面部身份、发型、服装、可见配饰、身体比例均来自 <Picture 1>。
<Audio 1>：fully_copy - 完整保留原始音频的讲话、节奏、停顿、重音和总时长。

detailed_description:
[Shot 1]
<Subject 1> (S1) 完整执行 <Audio 1> 中的讲话内容。嘴唇、下颌、脸颊和下半脸肌肉与每个音素、音节、元音、辅音、停顿、重音和语速变化精确同步。
停顿与静音段保持闭嘴或放松，不产生机械式重复张嘴。
眼神、眉毛和头部动作自然克制，重音处有对应表情。
镜头保持稳定，延续 <Picture 1> 的景别与构图；表演开始于 <Audio 1> 开始时，结束于 <Audio 1> 结束时，自然收口并短暂停留。

overall_soundscape:
<Audio 1> 中原有的环境声、表演声、呼吸声均完整保留，不引入额外音效。

non_diegetic_music:
<Audio 1> 中如无原始配乐则为 N/A，不另行添加新配乐。

英文版：
subject_definitions:
<Subject 1> is the main person in <Picture 1>, the speaking lead of this shot.
<Audio 1> is the complete reference audio for <Subject 1> (S1), providing the original speech content, timing, rhythm and pauses.

summary:
[reference generation + audio reuse] This segment preserves <Subject 1>'s identity and appearance from <Picture 1>, and fully reuses the speech content, rhythm and pauses from <Audio 1>.

retention_analysis:
<Subject 1> (in [Shot 1]): fully_preserved — face identity, hairstyle, costume, visible accessories and body proportions all come from <Picture 1>.
<Audio 1>: fully_copy — the original audio's speech, rhythm, pauses, stress and total duration are kept intact.

detailed_description:
[Shot 1]
<Subject 1> (S1) performs the full speech content from <Audio 1>. Lips, jaw, cheeks and lower-face muscles sync precisely to every phoneme, syllable, vowel, consonant, pause, stress and pacing change.
During pauses and silence, keep the mouth closed or relaxed — no mechanical repetitive opening.
Eyes, brows and head move naturally and with restraint; stress points get a matching expression.
Camera stays stable, continuing <Picture 1>'s shot size and composition; the performance starts when <Audio 1> starts and ends when <Audio 1> ends, closing naturally with a brief hold.

overall_soundscape:
The ambient sound, performance sound and breathing originally in <Audio 1> are fully preserved; no extra SFX added.

non_diegetic_music:
N/A if <Audio 1> has no original score; do not add new music.

**变体二 · 唱歌（演唱）**

> 与变体一差异：口型按**旋律 + 元音口型**同步（长音维持稳定元音口型、乐句结束自然放松）；纯伴奏/无人声段闭嘴或放松；表情随声音强弱变化；头与上半身随节奏轻微摆动；`non_diegetic_music` 为**原曲背景配乐完整保留**（不再写 N/A）。`retention_analysis` 的 `<Subject 1>` 额外锁「麦克风或可见道具」。

中文版：
subject_definitions:
<Subject 1> 是 <Picture 1> 中的主要人物，作为本段分镜中演唱的主角。
<Audio 1> 是 <Subject 1> (S1) 的完整参考音频，提供原始歌声、时间、节奏、停顿和情绪变化。

summary:
[reference generation + audio reuse] 本段保留 <Subject 1> 来自 <Picture 1> 的身份与外观，完整复用 <Audio 1> 中的歌声内容、节奏和表演结构。

retention_analysis:
<Subject 1>（出现在 [Shot 1]）：fully_preserved - 人物面部身份、发型、服装、可见配饰、身体比例、麦克风或可见道具均来自 <Picture 1>。
<Audio 1>：fully_copy - 完整保留原始音频的歌声、节奏、停顿、情绪变化和总时长。

detailed_description:
[Shot 1]
<Subject 1> (S1) 完整演唱 <Audio 1>。嘴唇、下颌、脸颊和面部肌肉与每个音节、元音、辅音、旋律、停顿、强度变化精确同步。
长音维持稳定的元音口型，乐句结束时自然放松嘴唇与下颌。
纯伴奏与无人声段落保持闭嘴或放松状态，不随意张嘴。
表情跟随声音强弱自然变化，眼神和眉毛轻微克制。
头部和上半身随节奏轻微摆动，镜头保持稳定延续 <Picture 1> 的景别与构图。表演开始于 <Audio 1> 开始时，结束于 <Audio 1> 结束时，自然收口并短暂停留。

overall_soundscape:
<Audio 1> 中原有的环境声、表演声、呼吸声和观众声均完整保留，不引入额外音效。

non_diegetic_music:
<Audio 1> 中原有的背景配乐完整保留，不替换、不重排、不添加新配乐。

英文版：
subject_definitions:
<Subject 1> is the main person in <Picture 1>, the singing lead of this shot.
<Audio 1> is the complete reference audio for <Subject 1> (S1), providing the original vocals, timing, rhythm, pauses and emotional changes.

summary:
[reference generation + audio reuse] This segment preserves <Subject 1>'s identity and appearance from <Picture 1>, and fully reuses the vocal content, rhythm and performance structure from <Audio 1>.

retention_analysis:
<Subject 1> (in [Shot 1]): fully_preserved — face identity, hairstyle, costume, visible accessories, body proportions, microphone or visible prop all come from <Picture 1>.
<Audio 1>: fully_copy — the original audio's vocals, rhythm, pauses, emotional changes and total duration are kept intact.

detailed_description:
[Shot 1]
<Subject 1> (S1) sings the full <Audio 1>. Lips, jaw, cheeks and facial muscles sync precisely to every syllable, vowel, consonant, melody, pause and dynamics change.
Sustain notes with a stable vowel mouth shape; relax the lips and jaw naturally at the end of each phrase.
During purely instrumental or non-vocal sections, keep the mouth closed or relaxed — no random opening.
Expression follows the vocal dynamics naturally; eyes and brows move subtly and with restraint.
Head and upper body sway gently with the rhythm; camera stays stable, continuing <Picture 1>'s shot size and composition. The performance starts when <Audio 1> starts and ends when <Audio 1> ends, closing naturally with a brief hold.

overall_soundscape:
The ambient sound, performance sound, breathing and audience sound originally in <Audio 1> are fully preserved; no extra SFX added.

non_diegetic_music:
The original background score in <Audio 1> is fully preserved — do not replace, reorder or add new music.

**变体三 · 说唱（Rap）**

> 与变体一差异：口型按**快速音节 / 辅音 / 元音 / 换气 / 节奏点**精确映射，快嘴段**不可简化成重复嘴型**；头与上半身可轻微跟节奏但**避免持续机械点头与夸张挥手**；`non_diegetic_music` 为**原曲背景配乐完整保留**（不再写 N/A）。

中文版：
subject_definitions:
<Subject 1> 是 <Picture 1> 中的主要人物，作为本段分镜中说唱的主角。
<Audio 1> 是 <Subject 1> (S1) 的完整参考音频，提供原始说唱内容、节奏、重音和换气位置。

summary:
[reference generation + audio reuse] 本段保留 <Subject 1> 来自 <Picture 1> 的身份与外观，完整复用 <Audio 1> 中的说唱内容、节奏和表演结构。

retention_analysis:
<Subject 1>（出现在 [Shot 1]）：fully_preserved - 人物面部身份、发型、服装、可见配饰、身体比例均来自 <Picture 1>。
<Audio 1>：fully_copy - 完整保留原始音频的说唱、节奏、重音、换气和总时长。

detailed_description:
[Shot 1]
<Subject 1> (S1) 完整演绎 <Audio 1> 中的说唱。每个快速音节、辅音、元音、停顿、重音、换气和节奏点对应精确的嘴唇与下颌动作。
快速说唱段不被简化为重复的嘴型动作。
头部和上半身可轻微跟随节奏，避免持续机械点头和夸张挥手。
眼神、眉毛和表情克制自然，镜头保持稳定延续 <Picture 1> 的景别与构图，表演开始于 <Audio 1> 开始时，结束于 <Audio 1> 结束时，自然收口并短暂停留。

overall_soundscape:
<Audio 1> 中原有的环境声、表演声、呼吸声均完整保留，不引入额外音效。

non_diegetic_music:
<Audio 1> 中原有的背景配乐完整保留，不替换、不重排、不添加新配乐。

英文版：
subject_definitions:
<Subject 1> is the main person in <Picture 1>, the rapping lead of this shot.
<Audio 1> is the complete reference audio for <Subject 1> (S1), providing the original rap content, rhythm, stress and breath positions.

summary:
[reference generation + audio reuse] This segment preserves <Subject 1>'s identity and appearance from <Picture 1>, and fully reuses the rap content, rhythm and performance structure from <Audio 1>.

retention_analysis:
<Subject 1> (in [Shot 1]): fully_preserved — face identity, hairstyle, costume, visible accessories and body proportions all come from <Picture 1>.
<Audio 1>: fully_copy — the original audio's rap, rhythm, stress, breaths and total duration are kept intact.

detailed_description:
[Shot 1]
<Subject 1> (S1) performs the full rap from <Audio 1>. Every fast syllable, consonant, vowel, pause, stress, breath and rhythmic hit maps to a precise lip and jaw motion.
Fast rap passages must not be reduced to a repeated mouth shape.
Head and upper body may follow the rhythm slightly — avoid continuous mechanical nodding and exaggerated hand-waving.
Eyes, brows and expression stay restrained and natural; camera stays stable, continuing <Picture 1>'s shot size and composition. The performance starts when <Audio 1> starts and ends when <Audio 1> ends, closing naturally with a brief hold.

overall_soundscape:
The ambient sound, performance sound and breathing originally in <Audio 1> are fully preserved; no extra SFX added.

non_diegetic_music:
The original background score in <Audio 1> is fully preserved — do not replace, reorder or add new music.

## 运镜词汇表（英文术语，歧义更小）

| 术语 | 含义 | 自然写法 |
|---|---|---|
| Push in / pull out | 摄像机实体靠近/远离主体 | 镜头缓慢推向她手中的信 |
| Zoom in / out | 只改焦距 | 镜头拉远，露出整个房间 |
| Pan left / right | 原地水平摇 | 镜头向右摇，露出门口 |
| Truck left / right | 水平侧移 | 镜头在骑车人身旁向左平移 |
| Tilt up / down | 原地垂直摇 | 镜头从鞋向上摇到脸 |
| Arc shot | 绕主体走弧线 | 镜头绕雕塑半圈 |
| Tracking shot | 跟随移动主体 | 低机位跟拍纸船 |
| Static shot | 机位焦距不动 | 跑者离画时保持静态广角 |
| POV | 主体视角 | 副驾驶主观镜头 |
| Steadicam follow | 稳定器跟拍 | 稳定器跟拍角色背影 |
| Rack focus | 移焦 | 从前景虚化转到背景实焦 |
| Dutch angle | 荷兰角 | 画面微倾制造不安 |

> **运镜写法（官方约定）**：一个完整的运镜动作由**运动类型 + 幅度 + 速度**三维度组成，写成镜头内的自然英文动作，而非句尾堆标签。幅度（`with small/large amplitude`）与速度（`at slow/fast speed`）只在有意义时才写，中等幅度/常速通常省略。例：`The camera pushes in with small amplitude at slow speed toward the folded letter.` / `The camera pans right with large amplitude at fast speed, revealing the open doorway.` 中文版对应写"镜头缓慢小幅度推向折好的信""镜头大幅快速向右摇，露出敞开的门口"。

## 常见错误与单变量修复（生成跑偏时，只改一项）

| 现象 | 常见原因 | 只改一项 |
|---|---|---|
| 画面几乎不动 | 只写外观没写随时间变化 | 加一个有起点终点的可见动作 |
| 主体身份变化 | 新增外貌与参考冲突 | 删新增外貌，只写须保持部分 |
| 运镜随机 | 短镜头塞多种移动 | 保留一种与揭示相关的运镜 |
| 结尾中断 | 有动作没结束态 | 加明确姿态/位置/构图 |
| 首尾帧跳变 | 只重复两静图 | 写清两帧间逐步变化 |
| 参考素材混合 | 用路径代替 token / 无明确职责 | 只用 <Picture 1> 等顺序 token（不写路径），点名每个素材用途 |
| 对白被改写 / 被翻译 | 对白混在长描述里，或英文版把台词翻译了 | 用 `<d>[语言] 台词</d>` 单独包裹台词本体，中英两版逐字相同不翻译 |
| 否定无效 | 自然语言否定非硬控制 | 改正向状态并删冲突要求 |

## 出片后先看四项（交付时附给用户）

1. 从头到尾是不是同一个人？（看完整条片，走形常从中段开始）
2. 动作做完了没有？（手势起头就切走是短时长常见翻车）
3. 口型对不对得上？（仅写了台词时看）
4. 最后一帧能不能接下一个镜头？（要剪辑的话写清收在什么画面）

一项不对就改一处：改一个变量 → 重新生成 → 对比。一次改三个，你不知道哪个起作用。

## 触发示例

- "帮我把'雨夜女孩奔跑'写成海螺 H3 视频提示词"
- "/minimax-h3 一个赛博朋克侦探在雨巷拉下全息护目镜"
- "用这张人物图（粘贴）生成单图生视频提示词，让她转头微笑"
