# 亚洲导演风格锚点库 · Asian Director Style Anchors

> 用途：把"我想要某某导演那种感觉"翻译成**可执行的镜头参数**，写进 MiniMax H3 提示词。
> 铁律：**只写导演名字是无效的**（模型对人名的理解不稳定）。必须拆成"镜长 + 景别 + 运镜 + 色温 + 光位 + 质感"这些可执行词，导演名最多作为附加锚点放在风格句尾。
> 每位导演只取 **2–3 个最具辨识度的特征**叠加，超过 3 个会互相打架。
>
> 欧美导演见 `director-anchors-western.md`；摄影指导见 `dp-cinematographer-anchors.md`。

---

## 使用方式（三步）

1. 从下表选定 1 位主导演做**主锚点**，最多再借 1 位做**副锚点**（副锚点只借一个维度，如"借他的色彩"）。
2. 把该导演的「可执行参数」整行抄进提示词的镜头/光影/色彩描述里。
3. 把「锚点句（中/英）」贴到风格句尾，**放在最后**，不要放开头。

> 本册特别提醒：东方风格最容易被写空。**"意境"不是参数**。凡想写"意境/东方美学/禅意"，一律替换为：
> `前景遮挡 + 大面积负空间 + 单一自然光源 + ASL ≥6s + 环境声取代配乐`
> 英文：`foreground occlusion, large negative space, single natural light source, average shot length over 6 seconds, ambient sound instead of score`

---

# 一、华语 · 武侠动作

## 1. 徐克 Tsui Hark — 抽帧顿挫·垂直 Z 轴·快切必保全景

（本册**重点条目**：技能内 `action-wuxia` 手册的默认动作语法即来自此人）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **快切但必保全景**：每 3–5 个特写/中近景之后，必插 1 个交代全局的全景（这是港式动作与好莱坞晃镜的分水岭——观众永远知道谁在哪、打到第几招）；构图常用斜对角贯穿画面 | `every 3-5 close shots must be followed by a clean wide establishing shot of the whole fight, diagonal composition across frame` |
| 运镜 | **威亚吊拍的垂直 Z 轴调度**：打斗在立体空间展开而非平面——人上屋顶、下井、贴墙、倒挂；机器跟着人做上下升降与俯仰，而不是左右平移 | `wire-work vertical staging along the Z axis, camera cranes up and tilts down following the fighters onto rooftops and beams, not lateral panning` |
| 节奏 | 极快，ASL **0.6–1.5s**（近身缠斗段可到 0.4s），但全景镜留 1.5–2.5s 让观众"回气"；快慢交替形成呼吸 | 分段：快切段 0.6s×5 + 全景 2s，循环 |
| 升降格 | **抽帧顿挫（不是纯升格）**：实速 → 突然抽掉几帧形成"顿" → 再回实速；关键交手的一格定格 2–3 帧；慢快慢的弹性 | `stutter frame-drop on impact (step-skip, not smooth slow motion), 2-3 frame freeze at the moment of contact, then snap back to full speed` |
| 色彩 | 高饱和对撞：赤红 + 金 + 墨黑；夜戏冷蓝 3200K 打底 + 火把琥珀 2000K 点缀 | `saturated crimson and gold against ink black, 3200K cold blue base with 2000K torch accents` |
| 光影 | 硬光造轮廓，逆光穿过飞叶与烟雾；光比 4:1–8:1；剪影瞬间大量出现 | `hard rim light through flying leaves and smoke, 4:1 to 8:1 contrast ratio, frequent silhouettes` |
| 胶片/画幅 | 35mm 质感；广角 21–28mm 贴身拍打击 + 长焦 85–135mm 压缩人群，**中间焦段几乎不用**；2.35:1 | `21mm close-in for impacts intercut with 135mm compression, 2.35:1, 35mm film grain` |
| 音乐 | 中式打击乐（鼓、锣、板）咬住每一次落点；唢呐/笛作为主题动机；鼓点与抽帧同帧命中 | `Chinese percussion (drum, gong, clapper) hitting exactly on each frame-drop, suona motif` |
| 表现手法 | **飞叶与烟雾作为速度的可视化**（人看不清有多快，就让空气告诉你）；布料/发辫/衣摆延迟半拍；重力可被短暂无视 | `flying leaves, dust and smoke as the visual proof of speed, fabric and hair lagging half a beat behind the body` |
| 招牌镜头 | 屋顶间垂直跃迁 / 竹梢立足俯拍 / 剑气掀起漫天落叶 / 倒挂视角反打 |
| 代表作 | 《笑傲江湖之东方不败》《新龙门客栈》（监制）《黄飞鸿》《狄仁杰》系列 |

**锚点句（中）**：0.8 秒极快切但每五镜必回一个交代全局的全景，威亚吊拍沿垂直方向上下调度，打击瞬间抽帧顿挫并定格两帧，飞叶与烟尘充满空气以显示速度，硬逆光剪影，中式鼓点同帧命中。
**锚点句（英）**：`ultra-fast cutting at 0.8s ASL but a clean wide shot of the whole fight every fifth cut, wire-work vertical Z-axis staging with crane up and tilt down, stutter frame-drop and 2-frame freeze on impact, air filled with flying leaves and dust to visualize speed, hard backlit silhouettes, Chinese drum hits locked to the frame-drops, 21mm intercut with 135mm, 2.35:1`

**⚠️ 不要与之叠加**：平滑连续升格（会杀死"顿"）、手持晃动求纪实（他的乱是剪出来的不是抖出来的）、去饱和灰调、长镜头一镜到底。

---

## 2. 胡金铨 King Hu — 竹林·极短镜头拼贴·锣鼓节拍

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 竹林纵向切割画面成条状栅格；人物常被竹竿/门框分隔；**留白与突然的静止**：打完立刻回到空镜 | `vertical bamboo stalks slicing the frame into strips, figures separated by verticals, cut to an empty landscape immediately after the clash` |
| 运镜 | 静止机位为主 + 突然的快速摇摄（whip pan）追踪跃起；很少推轨 | `locked-off frame broken by a sudden whip pan following the leap` |
| 节奏 | **极短镜头拼贴**：动作段 ASL **0.3–0.8s**，一次跃起由 3–5 个不同角度的短镜拼成；静场段 ASL 5–8s，反差极大 | 动作段 0.4s×4 拼一个动作，接静场 6s |
| 升降格 | 不用平滑慢动作；用**垂直跳跃的错觉剪辑**——起跳镜 + 空中镜 + 落地镜分别拍，剪在一起造出超人跳跃 | `impossible leap built from three separate shots: push-off, mid-air, landing, cut together with no slow motion` |
| 色彩 | 自然竹绿与土黄，饱和适中；客栈内昏黄 2800K，林间日光 5600K | `natural bamboo green and earth ochre, 2800K lantern interior against 5600K forest daylight` |
| 光影 | 林间斑驳漏光（dappled light）、正午顶光穿透竹叶、光比 3:1 | `dappled sunlight through bamboo canopy, noon top light, 3:1 ratio` |
| 胶片/画幅 | 35mm；标准 40–50mm 为主，跳跃用广角 24mm 仰拍；2.35:1 | `40mm standard lens, 24mm low-angle for leaps, 35mm film, 2.35:1` |
| 音乐 | **京剧锣鼓节拍剪辑**：剪辑点严格落在锣、鼓、板的重音上，无旋律配乐 | `Peking-opera percussion (gong, drum, wooden clapper) with every cut landing on a percussion accent, no melodic score` |
| 表现手法 | 侠客先"亮相"再动手（戏曲程式）；静—动—静的三段呼吸；杀招不见血 | `opera-style pose before action, still-action-still breathing structure` |
| 招牌镜头 | 竹梢立人俯拍 / 竹林中的伏击仰角 / 客栈木梯对峙 / 打完后的空镜山林 |
| 代表作 | 《侠女》《龙门客栈》《空山灵雨》 |

**锚点句（中）**：竹林纵向条状切割构图，0.4 秒极短镜头拼贴出一次不可能的跃起，京剧锣鼓重音上剪辑，斑驳漏光，打斗结束立刻切一个 6 秒空镜山林。
**锚点句（英）**：`vertical bamboo stalks slicing the frame, an impossible leap assembled from 0.4s fragment shots at three angles, cuts landing on Peking-opera gong and drum accents, dappled canopy light, then an abrupt 6-second empty landscape shot after the clash`

**⚠️ 不要与之叠加**：平滑升格、连续跟拍长镜、霓虹与现代光源、密集弦乐配乐。

---

## 3. 程小东 Ching Siu-tung — 飘逸吊威亚·织物飞舞·逆光尘埃

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物常悬于画面上三分之一，脚不沾地；大量仰角看飘浮；空间被布幔与雾填满 | `figures suspended in the upper third of frame, feet off the ground, low angle looking up at floating bodies` |
| 运镜 | 吊臂随人升起、镜头绕着悬空人物做弧线环绕；跟随织物飘动方向摇摄 | `crane rising with the airborne figure, arcing orbit around a suspended body` |
| 节奏 | 中快，ASL **1.2–2.5s**；升格段拉长到 3–4s 让飘浮被看足 | 实速段 1.5s，飘浮段 3.5s |
| 升降格 | **大量升格**：1/2–1/3 速为主，织物与长发在慢速中展开；起落瞬间回实速 | `1/2 to 1/3 speed slow motion for all airborne moments, back to full speed on landing` |
| 色彩 | 冷月白蓝 + 一抹血红/朱砂；雾气使画面整体偏低饱和高明度 | `moonlit blue-white haze with a single crimson accent, low saturation high key from fog` |
| 光影 | **逆光尘埃**：强逆光穿雾造可见光柱，尘埃与飞絮全部被点亮；光比 6:1 剪影化 | `hard backlight through fog creating visible god rays with every dust particle glowing, 6:1 silhouette lighting` |
| 胶片/画幅 | 35mm；广角 24–35mm 仰拍飘浮，2.35:1；轻微柔焦滤镜 | `24mm low angle, soft-focus filter, 2.35:1` |
| 音乐 | 女声吟唱 + 弦乐飘荡，鬼魅感；节拍松散不咬点 | `ethereal female vocalise over floating strings, loose non-percussive rhythm` |
| 表现手法 | **飞舞织物**（白绫、水袖、幔帐、长发）作为动作的延长线；人像羽毛一样落地无声 | `long white silk ribbons and hair extending every movement, weightless silent landings` |
| 招牌镜头 | 白绫缠绕升空 / 树梢间飘移 / 幔帐中穿行 / 逆光雾中剪影对峙 |
| 代表作 | 《倩女幽魂》《东方不败》（动作导演）《英雄》（动作导演） |

**锚点句（中）**：人物悬在画面上三分之一脚不沾地，1/2 升格中白绫与长发缓缓展开，强逆光穿雾形成可见光柱与发亮尘埃，冷月蓝白配一抹朱砂，女声吟唱。
**锚点句（英）**：`figure suspended in the upper third with feet off the ground, 1/2 speed slow motion as white silk ribbons and long hair unfurl, hard backlight through fog forming visible god rays with glowing dust, moonlit blue-white with one crimson accent, ethereal female vocalise`

**⚠️ 不要与之叠加**：写实重量感、手持纪实、抽帧顿挫（与他的平滑飘逸直接冲突）、高饱和暖调。

---

## 4. 袁和平 Yuen Woo-ping — 实打长镜·中景为主·不靠剪辑造假

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **中景为主**（膝盖以上到全身），保证观众看得见手脚起止；水平机位，眼平高度 | `medium-full shot from knees up keeping both fighters' hands and feet visible, camera at eye level` |
| 运镜 | 机器跟着招式做小幅左右微移与轻摇，始终保持双人同框；不抢戏 | `subtle lateral reframing to keep both fighters in one frame, camera never steals the move` |
| 节奏 | **实打长镜头**：一组连招 4–8s 不切，ASL **2.5–5s**；只在换招式套路时切 | 一个完整招式套路一镜到底，8s 内不切 |
| 升降格 | 极少升格；偶尔在收招定势用 1/2 速 0.5s 强调，随即回实速 | `almost no slow motion; at most a 0.5s half-speed beat on the finishing pose` |
| 色彩 | 自然写实，中性 5600K 日光或练功房暖木色；饱和适中不做风格化 | `naturalistic grade, neutral 5600K daylight or warm wood-tone dojo interior` |
| 光影 | 均匀高调布光，让动作清晰可读；光比 2:1–3:1，不做剪影 | `even high-key lighting for readability, 2:1 to 3:1 ratio, no silhouettes` |
| 胶片/画幅 | 35mm 或数字；35–50mm 标准焦段（避免广角变形破坏招式真实比例）；1.85:1 / 2.35:1 | `35-50mm standard lens to preserve true body proportions, 1.85:1` |
| 音乐 | 打击乐点缀落点，但音乐让位于**衣料摩擦与拳风的实录音效** | `foley-forward: cloth friction and fist wind over minimal percussion` |
| 表现手法 | **不靠剪辑造假**——招式的起、承、转、合完整呈现；演员真做，一镜内完成 3–5 招 | `3-5 consecutive strikes completed within one unbroken take, no cutting to fake the technique` |
| 招牌镜头 | 双人同框中景连招 / 木人桩训练侧机位 / 兵器缠斗一镜到底 |
| 代表作 | 《醉拳》《黑客帝国》（动作导演）《卧虎藏龙》（动作导演）《叶问》 |

**锚点句（中）**：眼平中景保持两人同框，一镜到底完成三到五招不切，均匀高调布光让招式清晰可读，35mm 标准焦段无变形，衣料摩擦与拳风的实录音效压过配乐。
**锚点句（英）**：`eye-level medium-full shot keeping both fighters in frame, three to five consecutive strikes in one unbroken take with no cuts, even high-key lighting for full readability, 35mm standard lens with no wide-angle distortion, foley of cloth and fist wind over music`

**⚠️ 不要与之叠加**：0.5s 快切、广角贴脸、大量升格、剪影逆光、抽帧顿挫。

---

# 二、华语 · 作者电影

## 5. 王家卫 Wong Kar-wai — 抽帧·霓虹·广角变形

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 残缺构图，人物被门框/柱子/栏杆/镜面切掉一半；大量前景遮挡；主体常被挤到画面边缘 | `fragmented framing, subject half-cut by doorframes and railings, heavy foreground occlusion, figure pushed to frame edge` |
| 运镜 | 手持贴身广角（摄影 杜可风）、沿墙滑行、镜面反射二次成像、失焦前景穿过 | `handheld wide-angle pressed close to the face, sliding along walls, mirror double-image, out-of-focus foreground swiping past` |
| 节奏 | ASL **1.5–3s**；同一动作反复重演三次；对白段可拉长到 6s 配独白 | 快段 1.5s，独白段 5–6s |
| 升降格 | **抽帧印片 step-printing**（低帧率拍 + 逐格重印）→ 人物动作拖影而背景清晰，是他最强签名；配合慢门 1/8s 拖尾；偶尔突然定格 | `step-printed motion blur trails on the moving figure while the background stays sharp, 1/8s shutter drag, sudden freeze frame` |
| 色彩 | 霓虹绿 / 品红 / 琥珀，高饱和滤色片直接怼在镜头前；冷暖极端混色 2000K 钨丝对 7000K 霓虹 | `saturated neon green and magenta from on-lens color filters, 2000K tungsten against 7000K neon` |
| 光影 | 狭窄空间的实用光、走廊灯管、雨夜霓虹反射在湿地面；光比 6:1，暗部有色不死黑 | `in-frame practical fluorescent tubes, neon reflected in rain-slick pavement, 6:1 ratio with colored shadows` |
| 胶片/画幅 | 35mm，1.85:1；广角 **9.8mm 极端畸变**（Kinoptik）与 25mm 交替；颗粒明显 | `9.8mm extreme wide-angle distortion, 35mm film grain, 1.85:1` |
| 音乐 | 同一首曲子在片中反复播放（《California Dreamin'》《Yumeji's Theme》）；音乐先于画面进入 | `one single song looping throughout, music entering before the cut` |
| 表现手法 | 画外独白 + 时间数字（"1960年4月16日下午3点"）、错过与重复、罐头食品与钟表作为时间物证 | `wistful voice-over with precise dates and times, motif of missed encounters` |
| 招牌镜头 | 走廊抽帧擦身而过 / 面摊前的独白 / 楼梯间旗袍背影 / 镜中双重人像 |
| 代表作 | 《重庆森林》《花样年华》《堕落天使》《春光乍泄》 |

**锚点句（中）**：手持 9.8mm 广角贴身畸变，抽帧印片使人物拖影而背景清晰，霓虹绿与品红高饱和，雨夜湿地面反射，门框切割的残缺构图，反复出现的画外独白。
**锚点句（英）**：`step-printed motion blur trails against a sharp background, handheld 9.8mm wide-angle distortion, saturated neon green and magenta, rain-slick reflections, fragmented framing cut by doorframes, repeated wistful voice-over, 1.85:1 35mm grain`

**⚠️ 不要与之叠加**：对称构图、去饱和写实、锁死静止长镜、均匀平光。

---

## 6. 侯孝贤 Hou Hsiao-hsien — 固定长镜远观·自然光·人物进出画

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **远观**：机位远、景别宽，人物只占画面小部分；门框套画（frame within frame）；**人物进出画**而机器不追 | `distant wide observational framing, subject small in frame, doorway framing the room, characters walk in and out of frame while the camera stays` |
| 运镜 | 绝对固定（tripod locked-off）；极偶尔一次缓慢横摇，速度慢到几乎察觉不到 | `locked-off tripod, at most one imperceptibly slow pan per scene` |
| 节奏 | 极慢，ASL **20–90s**，一场一镜；不给反打，不给特写 | 单镜到底，全片无特写 |
| 升降格 | 完全不用 | 禁写 slow motion |
| 色彩 | 自然写实，室内钨丝 3000K 偏黄、室外阴天 6500K 偏青；低饱和 | `naturalistic grade, 3000K tungsten interior against 6500K overcast exterior, low saturation` |
| 光影 | **只用自然光与实用光**：窗户是唯一主光，室内暗部大面积欠曝也不补光；光比 8:1 | `available light only, window as sole key, interiors allowed to fall into underexposure, 8:1 ratio` |
| 胶片/画幅 | 35mm；**长焦 75–100mm 远距离拍摄**（演员不知道镜头在哪）；1.85:1 | `75-100mm telephoto shot from a distance, 35mm film, 1.85:1` |
| 音乐 | 几乎无配乐；**生活声景**：电扇、麻将、火车、蝉鸣、远处电视 | `no score, dense ambient soundscape: electric fan, mahjong tiles, cicadas, distant TV` |
| 表现手法 | 事件在画外发生，画内只见余波；日常动作被完整保留（吃饭、洗碗、等车）；不解释 | `the dramatic event happens off-screen, only the aftermath is shown, mundane actions play out in full` |
| 招牌镜头 | 门框内的一家人吃饭 / 火车驶过的长镜 / 屋檐下的雨 / 空椅子 |
| 代表作 | 《悲情城市》《童年往事》《刺客聂隐娘》《恋恋风尘》 |

**锚点句（中）**：固定机位不动的 40 秒远观长镜，75mm 长焦从远处拍，门框套画构图，只有窗户自然光室内大面积欠曝，人物自行走出画面而镜头不追，无配乐只有电扇与蝉鸣。
**锚点句（英）**：`locked-off 40-second observational wide shot, 75mm telephoto from a distance, doorway framing the room, window as the only light source with interiors falling into shadow, characters exit the frame while the camera never follows, no score with only fan hum and cicadas`

**⚠️ 不要与之叠加**：快切、手持、推轨、特写反打、配乐煽情、补光。

---

## 7. 蔡明亮 Tsai Ming-liang — 极端静止长镜·水与潮湿·几乎无对白

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 正面平视固定框，人物在画面中央长时间不动或做重复动作；空间被墙面切成方块 | `frontal locked frame, a single figure motionless or repeating one action at frame center, walls dividing the space into blocks` |
| 运镜 | **零运镜**：整场无推拉摇移 | `absolutely static camera, zero movement for the entire scene` |
| 节奏 | 极端慢，ASL **60–360s**（数分钟一镜）；镜头在人物离开后仍继续停留 | 单镜 2 分钟以上，人走后再停 15s |
| 升降格 | 不用；时间的漫长本身就是效果 | 禁写 slow motion |
| 色彩 | 潮湿霉绿与冷灰蓝，低饱和；霓虹时偶有品红点缀 | `damp mildew green and cold grey-blue, low saturation, occasional magenta neon accent` |
| 光影 | 单一实用光源（走廊灯、电视屏、浴室灯）；大面积暗部；光比 10:1 | `single practical source such as a corridor bulb or TV screen, vast dark areas, 10:1 ratio` |
| 胶片/画幅 | 35mm / 数字；35–50mm；1.85:1；不追求锐利 | `35mm lens, 1.85:1, soft unglamorous image` |
| 音乐 | **完全无配乐**；只有水声——滴水、冲水、暴雨、水管漏水 | `no score at all, only water: dripping, flushing, rain, leaking pipes` |
| 表现手法 | **水与潮湿**贯穿（漏水的天花板、泡水的地板、洗澡、喝水）；**几乎无对白**（全片台词可少于 20 句）；孤独的身体 | `water everywhere: leaking ceilings, flooded floors, near-total absence of dialogue` |
| 招牌镜头 | 漏水的房间静止长镜 / 独自吃饭 / 浴缸 / 走廊尽头的人影 |
| 代表作 | 《爱情万岁》《洞》《郊游》 |

**锚点句（中）**：完全静止的正面固定机位两分钟长镜，人物在中央重复一个动作，单一走廊灯为唯一光源大面积暗部，潮湿霉绿冷灰调，无配乐只有滴水声，全程无对白。
**锚点句（英）**：`completely static frontal locked frame held for two minutes, a single figure repeating one action at center, one practical corridor bulb as the only light with vast darkness, damp mildew-green and cold grey grade, no score and no dialogue, only the sound of dripping water`

**⚠️ 不要与之叠加**：任何运镜、配乐、快切、明亮布光、对白密集。

---

## 8. 贾樟柯 Jia Zhangke — 县城纪实·变焦推·流行歌当时代标记

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 手持中景为主，人物置于真实县城环境中（拆迁工地、录像厅、汽车站）；环境与人同等重要 | `handheld medium shot with the subject embedded in a real small-town Chinese environment: demolition sites, bus stations, karaoke halls` |
| 运镜 | **变焦推（zoom-in）代替推轨**——纪录片式的、略显笨拙的变焦，这是他的签名；缓慢横摇扫过环境 | `documentary-style slow zoom-in instead of a dolly, slightly clumsy and hand-operated, plus slow pans across the environment` |
| 节奏 | 慢，ASL **12–40s**；长镜跟随人物穿过街道 | 单镜 20s+，跟随行走 |
| 升降格 | 不用；偶有超现实插入（UFO、飞碟、纪念碑升空）打破写实 | 禁 slow motion；可写 `one surreal element intrudes into the realist frame` |
| 色彩 | 灰蓝雾霾感、水泥灰、褪色的红色标语；低饱和；日光 6000K 偏冷 | `hazy grey-blue small-town palette, concrete grey and faded red slogans, low saturation, 6000K cool daylight` |
| 光影 | 全自然光/阴天散射；室内荧光灯青绿；光比 3:1 平淡不戏剧 | `overcast diffused daylight, green fluorescent interiors, flat 3:1 ratio` |
| 胶片/画幅 | DV/数字质感（早期刻意的低画质）；1.85:1；变焦镜头 28–100mm | `digital video texture, 28-100mm zoom lens, 1.85:1` |
| 音乐 | **流行歌当时代标记**：画内音源（收音机、卡拉OK、街头喇叭）播放特定年代金曲 | `period pop songs playing diegetically from radios, karaoke machines and street speakers as time markers` |
| 表现手法 | 非职业演员、方言、长镜纪实；时代变迁写在背景的建筑上 | `non-professional actors, regional dialect, social change visible in the background architecture` |
| 招牌镜头 | 拆迁墙前的人 / 站台等待 / 卡拉OK包间 / 缓慢变焦推向发呆的脸 |
| 代表作 | 《小武》《站台》《三峡好人》《江湖儿女》 |

**锚点句（中）**：手持中景把人放进真实县城拆迁环境，纪录片式笨拙变焦缓慢推近，阴天散射光低饱和灰蓝雾霾调，画内收音机播放年代金曲，20 秒长镜跟随行走。
**锚点句（英）**：`handheld medium shot placing the figure in a real Chinese small-town demolition site, documentary slow hand-operated zoom-in, overcast diffused light with hazy grey-blue low-saturation grade, a period pop song playing diegetically from a radio, 20-second walking long take`

**⚠️ 不要与之叠加**：精致布光、稳定器滑轨、高饱和风格化调色、非画内配乐。

---

## 9. 毕赣 Bi Gan — 长镜梦游·绿与红·潮湿岩洞

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 跟随一个人在真实空间里连续穿行，空间自己不断变化；主体常背对镜头带路 | `following a single figure from behind through continuously transforming real spaces` |
| 运镜 | **超长跟随一镜到底**（数十分钟级），手持 + 稳定器 + 索道 + 无人机接力；**旋转跟随**围绕人物 | `extended one-take following shot, handheld into gimbal into cable-cam relay, orbiting rotation around the subject` |
| 节奏 | 极慢，ASL **60s–数十分钟**；梦游速度，人物走得比正常慢 | 单镜到底，人物步速放慢 |
| 升降格 | 不用慢动作；用"漂浮"的运镜速度制造梦感 | `dreamlike floating camera speed instead of slow motion` |
| 色彩 | **绿与红对撞**：苔绿、灯箱红、暗蓝夜；高饱和但低亮度 | `mossy green against sign-board red, deep blue night, saturated but dark` |
| 光影 | 极低照度，实用光源（矿灯、灯泡、摩托车灯、KTV 灯球）为唯一光；光比 12:1 | `extreme low light, practicals only: bare bulbs, motorbike headlight, mirror ball, 12:1 ratio` |
| 胶片/画幅 | 数字大画幅（可写 3D 段落）；广角 18–24mm 保证空间感；1.85:1 / 2.39:1 | `18-24mm wide angle for spatial continuity, large-format digital, 2.39:1` |
| 音乐 | 缓慢的电子低鸣 + 民谣吉他；诗的旁白 | `slow electronic drone with folk guitar, poetic voice-over` |
| 表现手法 | **潮湿岩洞**、湿墙、滴水、雨；现实与记忆无缝衔接（不切镜就换了时空）；诗句作旁白 | `wet cave walls and constant dripping, memory and present merging without a cut` |
| 招牌镜头 | 洞穴中穿行 / 摩托车夜行跟拍 / 旋转的房间 / 台球厅红灯 |
| 代表作 | 《路边野餐》《地球最后的夜晚》 |

**锚点句（中）**：超长一镜到底跟随人物背影穿过不断变化的潮湿岩洞与小镇，旋转环绕运镜如梦游漂浮，苔绿与灯箱红对撞的极低照度，唯一光源是裸灯泡与摩托车灯，缓慢电子低鸣配诗的旁白。
**锚点句（英）**：`extended single-take following a figure from behind through wet cave walls and a shifting small town, orbiting floating camera at dreamlike speed, mossy green against sign-board red in extreme low light, bare bulbs and a motorbike headlight as the only sources, slow electronic drone with poetic voice-over`

**⚠️ 不要与之叠加**：快切、明亮布光、去饱和写实、静止机位。

---

## 10. 姜文 Jiang Wen — 高饱和阳光·快速对话调度·荒诞热烈

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **仰角**看人（人物比天大）、饱满的画面塞满人与物；群戏中人物层层叠叠站位 | `low camera angle looking up at the characters against sky, densely packed frames with layered ensemble staging` |
| 运镜 | 快速横移与推进跟着台词跑；机器随情绪突然加速；环绕群像 | `camera moves accelerating with the dialogue, sudden fast dolly-in on a punchline, orbit around a group` |
| 节奏 | 快，ASL **1.5–3s**；**快速对话调度**：台词像机关枪，剪辑咬住每句尾字 | 对白段 1.5s 一切，切点落在句尾 |
| 升降格 | 偶用 1/2 升格给荒诞高潮（爆炸、马队、抛洒的钱）；不用于抒情 | `1/2 speed only on absurd spectacle: explosions, galloping horses, cash thrown in the air` |
| 色彩 | **高饱和阳光**：金黄麦浪、赤红旗帜、湛蓝天空；对比强烈；日光 5000K 加暖 | `high-saturation sunlight, golden wheat, crimson banners, deep blue sky, warm 5000K` |
| 光影 | 正午强硬光，人物脸上有明确阴影；光比 5:1；反对柔光 | `harsh noon sunlight with hard facial shadows, 5:1 ratio, no soft fill` |
| 胶片/画幅 | 35mm；24–35mm 广角仰拍 + 长焦压缩群像；2.35:1 | `24mm low-angle wide, 35mm film, 2.35:1` |
| 音乐 | 铜管齐奏、进行曲、《太阳照常升起》式的宏大主题；音乐几乎不停 | `brass-heavy march, relentless triumphant orchestral theme` |
| 表现手法 | 荒诞与热烈并置；台词双关；仪式化的群体动作（列队、骑马、宴席） | `absurdist bravado, ritualized group action: formations, horse charges, banquets` |
| 招牌镜头 | 仰角逆光的人物与烈日 / 马队奔驰 / 长桌鸿门宴 / 抛洒漫天钞票 |
| 代表作 | 《阳光灿烂的日子》《让子弹飞》《鬼子来了》 |

**锚点句（中）**：低机位仰角把人拍得比天大，正午强硬光造脸部明确阴影，高饱和金黄与赤红配湛蓝天空，1.5 秒一切咬住台词尾字的快速对话剪辑，铜管进行曲不停。
**锚点句（英）**：`low-angle camera making the figures loom against the sky, harsh noon sun with hard facial shadows, high-saturation golden and crimson against deep blue sky, rapid 1.5s dialogue cutting landing on the end of each line, relentless brass march`

**⚠️ 不要与之叠加**：柔光美颜、低饱和冷调、静默无配乐、缓慢长镜。

---

# 三、华语 · 商业与类型

## 11. 张艺谋 Zhang Yimou — 单色块·人海阵列·仪式感

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 大规模整齐阵列（千人击缶、万箭齐发）、绝对对称仪式构图；人被简化为图案的一个点 | `massive symmetrical human formation filling the frame, individuals reduced to pattern elements, ceremonial axial symmetry` |
| 运镜 | 升降机大俯拍揭示阵列规模、横向长距离平移扫过队列、缓慢推向单一人物 | `high crane overhead reveal of the formation, long lateral track across the ranks, slow push-in on the lone figure` |
| 节奏 | 段落按**颜色**分章（《英雄》红/蓝/白/绿/黑各一段）；动作段 ASL **1.5–3s**，仪式段 4–6s | 按颜色分段，每段内色不变 |
| 升降格 | **1/4 升格 + 飘落物**（银杏叶、箭雨、水滴、丝绸）——升格永远配一个在空中的东西 | `1/4 speed slow motion always paired with something falling: leaves, arrows, water droplets, silk` |
| 色彩 | **每段只用一个主色填满整个画面**，饱和到极致；红 = 欲望，蓝 = 回忆，白 = 真相 | `a single saturated color floods the entire frame (crimson / cobalt / pure white), no competing hues` |
| 光影 | 大面积均匀色光 + 逆光穿透丝绸/水幕/纱帐；光比 2:1（求色不求反差） | `large-area even colored light plus backlight penetrating silk and water curtains, low 2:1 ratio` |
| 胶片/画幅 | 35mm；长焦 85–200mm 压缩阵列纵深 + 广角俯拍全景；2.35:1 | `85-200mm telephoto compressing the ranks, intercut with wide overhead, 2.35:1` |
| 音乐 | 谭盾/久石让式：鼓阵 + 二胡 + 人声吟唱；打击乐与箭雨同步 | `massive drum ensemble with erhu and wordless vocal, percussion synced to the arrow volley` |
| 表现手法 | 仪式化群体动作；自然物（叶、水、沙、绸）作为情绪载体；以量取势 | `ritualized mass choreography, natural elements as emotional carriers, scale as meaning` |
| 招牌镜头 | 万箭穿空俯拍 / 红叶林中对决 / 水面点踏 / 千人击缶方阵 |
| 代表作 | 《英雄》《十面埋伏》《大红灯笼高高挂》《满城尽带黄金甲》《影》 |

**锚点句（中）**：单一饱和色（赤红）填满整个画面，千人对称方阵，升降机大俯拍揭示规模，1/4 升格中银杏叶漫天飘落，逆光穿透丝绸，鼓阵与二胡轰鸣。
**锚点句（英）**：`a single saturated color floods the entire frame (crimson red), massive symmetrical human formation, high crane overhead reveal, 1/4 slow motion with falling ginkgo leaves, backlight through silk, thunderous drum ensemble with erhu, 85mm compression, 2.35:1`

**⚠️ 不要与之叠加**：低饱和写实、手持纪实、多色混杂、暗部压死的低照度。

---

## 12. 杜琪峰 Johnnie To — 静止对峙·群像站位·冷蓝夜

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **枪战里的静止**——人不动、只有枪口和眼神动（《枪火》商场戏）；群像按几何点位站开，像棋盘布子 | `frozen standoff, bodies completely still while only eyes and gun barrels move, an ensemble arranged as geometric chess-piece positions` |
| 运镜 | 几乎全静止长镜（locked-off wide），横移只在调度群像换位时使用 | `locked-off wide shot, lateral track used only when the ensemble repositions` |
| 节奏 | **极长的静默对峙 → 0.3s 内爆发 → 立刻回归静止**；对峙段 ASL **5–10s** | 静止 8s + 爆发 0.3s + 静止 5s |
| 升降格 | **不用慢动作，用"静止"代替慢动作**（这是他与吴宇森的分水岭） | 禁写 slow motion，改写 `absolute stillness in place of slow motion` |
| 色彩 | 冷蓝夜景 + 路灯钠黄点缀，低饱和；3200K 夜蓝对 2200K 钠灯 | `cold blue night at 3200K with 2200K sodium streetlight accents, low saturation` |
| 光影 | 单侧硬光造脸部半明半暗，霓虹与车灯做轮廓光；光比 8:1 | `single-side hard key leaving half the face dark, neon and headlights as rim, 8:1 ratio` |
| 胶片/画幅 | 35mm / 数字；中长焦 50–85mm 保持距离感；2.35:1；深景深让群像全清晰 | `50-85mm keeping distance, deep focus so the whole ensemble stays sharp, 2.35:1` |
| 音乐 | 极简爵士鼓刷 / 贝斯拨弦，留白极多；开枪前音乐先停 | `minimal jazz brush and plucked bass, music cutting out completely just before the first shot` |
| 表现手法 | 空间调度即叙事（谁站哪里就是权力关系）；宿命感；沉默取代台词 | `spatial blocking as narrative — position equals power; silence replaces dialogue` |
| 招牌镜头 | 商场五人站位对峙 / 走廊尽头开枪 / 路灯下的等待 / 一枚滚动的易拉罐 |
| 代表作 | 《枪火》《放·逐》《暗花》《毒战》《黑社会》 |

**锚点句（中）**：锁死的静止全景，五人按几何点位站开身体完全不动，只有眼神和枪口在动，冷蓝夜配钠黄路灯，单侧硬光让半张脸沉入黑暗，音乐先停再爆发 0.3 秒。
**锚点句（英）**：`frozen standoff, bodies completely still while only eyes and gun barrels move, locked-off wide shot with the ensemble in geometric positions, cold blue night with sodium-yellow streetlight accents, single-side hard key with half the face in shadow, minimal jazz bass cutting out, sudden 0.3-second burst of violence`

**⚠️ 不要与之叠加**：慢动作、手持晃动、快切、暖调柔光、密集配乐。

---

## 13. 李安 Ang Lee — 克制的对称·情感张力·水与绿

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **克制的对称**：构图规整但不炫技，人物居中略偏；门窗回廊做二次框；留一段空间给"未说出口的话" | `restrained near-symmetrical composition, subject slightly off-center, doorways and corridors as inner frames, deliberate empty space beside the face` |
| 运镜 | 缓慢推进与轻微跟随；情绪高点反而**停止运动**；很少手持 | `slow deliberate push-in that stops moving at the emotional peak, minimal handheld` |
| 节奏 | 中慢，ASL **5–9s**；对话留白，切点晚于台词结束 0.5–1s | 每镜结束后多留 1s 再切 |
| 升降格 | 极少；武侠段落用 1/2 升格给腾空一瞬（《卧虎藏龙》竹梢） | `1/2 speed only at the instant of weightless suspension` |
| 色彩 | **水与绿**：竹绿、湖水青、宣纸米白；温润低对比；室内暖 3400K，室外青 6000K | `bamboo green, lake teal and rice-paper cream, gentle low-contrast grade, 3400K interior against 6000K exterior` |
| 光影 | 柔和方向光，窗纸/纱帘做柔光板；光比 3:1；肤色保护良好 | `soft directional light diffused through paper screens and gauze, 3:1 ratio, protected skin tones` |
| 胶片/画幅 | 35mm（也做过 120fps 4K 3D 实验）；50–85mm 中长焦人像；1.85:1 / 2.35:1 | `50-85mm portrait lens, 35mm film, 2.35:1` |
| 音乐 | 谭盾式大提琴（马友友）+ 鼓；东西方乐器融合；旋律克制不满溢 | `solo cello over Chinese percussion, restrained melodic line` |
| 表现手法 | **跨文化质感**（东方礼节 + 西方戏剧结构）；情感全靠压抑后的一次微表情；水面/雨作为情绪出口 | `cross-cultural texture, emotion released only through one micro-expression after long suppression, water surfaces as emotional outlet` |
| 招牌镜头 | 竹梢对峙 / 隔着门帘的对话 / 水面倒影 / 转身前的一次停顿 |
| 代表作 | 《卧虎藏龙》《饮食男女》《断背山》《色·戒》《少年派的奇幻漂流》 |

**锚点句（中）**：克制的近对称构图人物略偏中心，纱帘柔化的方向光 3:1 光比，竹绿与湖水青的温润低对比，缓慢推进在情绪高点停住，切点比台词晚一秒，大提琴独奏。
**锚点句（英）**：`restrained near-symmetrical framing with the subject slightly off-center, soft directional light diffused through gauze at a 3:1 ratio, gentle bamboo-green and lake-teal low-contrast grade, slow push-in that halts at the emotional peak, cut held one second after the line ends, solo cello`

**⚠️ 不要与之叠加**：高饱和色块、快切、手持晃动、强硬光剪影。

---

## 14. 陈可辛 Peter Chan — 特写驱动·暖调市井·时代群像

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **人物特写驱动**：情绪靠脸推进，大量胸像与面部特写；群像戏里也总有一个人被单独框出 | `close-up driven storytelling, chest-up and facial close-ups carrying the emotion, one face isolated even within a crowd` |
| 运镜 | 轻微手持呼吸感 + 缓慢推向面部；跟随人物穿过市井街巷 | `subtle breathing handheld with a slow push toward the face, following the character through crowded streets` |
| 节奏 | 中速，ASL **3–5s**；情绪段放慢到 6–8s | 情绪段延长至 8s |
| 升降格 | 时代蒙太奇用 1/2 升格 + 老照片定格；情感高点微升格 3/4 | `1/2 speed montage of the era, 3/4 subtle ramp at the emotional peak, freeze into a photograph` |
| 色彩 | 暖调市井：琥珀灯箱、旧木、褪色招牌；暖 3200K 为主，怀旧偏黄 | `warm street-market palette of amber signage and aged wood, nostalgic 3200K yellow cast` |
| 光影 | 柔和暖光 + 环境实用光；光比 3:1；脸部永远有光 | `soft warm key plus in-frame practicals, 3:1 ratio, the face is always lit` |
| 胶片/画幅 | 35mm 或数字仿胶片；85mm 浅景深人像；1.85:1 / 2.35:1 | `85mm shallow depth of field portraiture, film emulation, 2.35:1` |
| 音乐 | 时代金曲 + 弦乐；歌声与人物命运同步（《甜蜜蜜》） | `period Chinese pop song woven with strings, the lyric mirroring the character's fate` |
| 表现手法 | **时代群像**：小人物命运折射大时代；南来北往的漂泊感；结尾一次重逢 | `ordinary lives refracting a whole era, the ache of migration, a final reunion` |
| 招牌镜头 | 街头单车并行 / 电视机前的人群 / 拥挤楼梯间的告别 / 泪光特写 |
| 代表作 | 《甜蜜蜜》《投名状》《亲爱的》《中国合伙人》《夺冠》 |

**锚点句（中）**：85mm 浅景深胸像特写驱动情绪，轻微呼吸感手持缓慢推向面部，琥珀市井暖调 3200K 怀旧偏黄，柔光 3:1 脸上永远有光，时代金曲与命运同步。
**锚点句（英）**：`close-up driven emotion on an 85mm shallow-focus portrait, subtle breathing handheld pushing slowly toward the face, warm amber street-market grade at 3200K with a nostalgic cast, soft 3:1 key keeping the face always lit, a period pop song mirroring the character's fate`

**⚠️ 不要与之叠加**：冷峻疏离长镜、去饱和、静止远观（他必须靠近脸）。

---

## 15. 刁亦男 Diao Yinan — 黑色霓虹雪夜·荒诞冷幽默·长镜追随

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物淹没在霓虹招牌与雪夜街景中；不对称构图，主体常被环境挤压到角落 | `figure submerged in neon signage and snowy night streets, asymmetric framing pushing the subject into a corner` |
| 运镜 | **长镜追随**：跟着人物走进溜冰场、动物园、发廊，一镜换数个空间；缓慢横移 | `long following take walking the character through a skating rink or a hair salon in one shot, slow lateral tracking` |
| 节奏 | 中慢，ASL **8–20s**；暴力发生得突兀又短促（0.5s） | 长镜 15s + 突发暴力 0.5s |
| 升降格 | 极少；用突发与静止的落差代替 | `no slow motion; abruptness replaces it` |
| 色彩 | **黑色电影霓虹**：品红 + 青绿 + 冰蓝雪白；高饱和霓虹嵌在低饱和雪夜里 | `film-noir neon: magenta and cyan-green against icy blue snow, saturated signage inside a desaturated night` |
| 光影 | 混合色温实用光（霓虹 6500K 与钨丝 2700K 同框）；光比 8:1；暗部保留细节 | `mixed color temperature practicals, 6500K neon beside 2700K tungsten, 8:1 ratio` |
| 胶片/画幅 | 数字；35–50mm；2.39:1；轻微颗粒 | `35-50mm, digital with light grain, 2.39:1` |
| 音乐 | 几乎无配乐；广场舞音乐、老歌、火车声等画内音；偶尔一段廉价电子舞曲 | `almost no score, diegetic square-dance music and cheap electronic dance tracks` |
| 表现手法 | **荒诞冷幽默**（在最紧张时插入一件滑稽小事）；命运的偶然；雪、冰、水 | `deadpan absurdist humor inserted at the tensest moment, snow and ice as texture` |
| 招牌镜头 | 溜冰场追杀 / 霓虹发廊 / 雪夜巷口 / 突然的横向暴力 |
| 代表作 | 《白日焰火》《南方车站的聚会》 |

**锚点句（中）**：霓虹招牌与雪夜街景吞没人物的不对称构图，15 秒长镜跟随走过溜冰场，品红与青绿霓虹嵌在低饱和冰蓝雪夜里，混合色温实用光 8:1，画内广场舞音乐，暴力在 0.5 秒内突然发生。
**锚点句（英）**：`asymmetric framing with the figure swallowed by neon signage and snowy streets, a 15-second following take through a skating rink, saturated magenta and cyan-green neon inside a desaturated icy-blue night, mixed 6500K/2700K practicals at 8:1, diegetic square-dance music, violence erupting in half a second`

**⚠️ 不要与之叠加**：暖金柔光、快切、对称仪式构图、交响配乐。

---

## 16. 乌尔善 Wuershan — 东方奇幻的实拍质感

（"东方奇幻 / 仙侠特效场面"槽位取此位；若需更硬派武侠动作可换用徐克）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 巨物压迫式神话构图（神像、龙、巨兽与人的体量对比）；对称祭祀场面 | `mythic scale composition contrasting a human against a colossal statue or beast, symmetrical ritual staging` |
| 运镜 | 大幅度环绕与升降揭示规模；战斗中稳定器跟随 + 短促手持交替 | `sweeping crane and orbit revealing scale, gimbal following intercut with short handheld bursts` |
| 节奏 | 中快，ASL **1.5–3s**；奇观镜头留 3–4s 让观众看清 | 动作 1.5s，奇观 3.5s |
| 升降格 | 1/3 升格给法术释放与巨兽落地；升格必须伴随尘土/火星 | `1/3 speed on spell release and the beast's landing, always with dust or embers in the air` |
| 色彩 | 青铜金 + 朱砂红 + 玄黑；高饱和但压暗；火光 1800K 对夜蓝 4000K | `bronze gold, cinnabar red and deep black, saturated but dark, 1800K firelight against 4000K night` |
| 光影 | 火把与法术光作为动机光源；强烟雾造光柱；光比 6:1 | `torches and magic glow as motivated sources, heavy haze forming volumetric beams, 6:1 ratio` |
| 胶片/画幅 | 数字大画幅，**实景搭建 + 实体道具优先**（追求特效不像特效）；2.39:1 | `large-format digital, practical sets and physical props so VFX reads as real, 2.39:1` |
| 音乐 | 编钟、大鼓、低音号；仪式感强的东方史诗编制 | `bianzhong bells, war drums and low brass in an Eastern epic arrangement` |
| 表现手法 | 神话质感依赖**材质**：青铜锈、皮革、丝绸、汗与泥；避免塑料感 CG | `materials carry the myth: bronze patina, leather, silk, sweat and mud; avoid plastic CG sheen` |
| 招牌镜头 | 仰拍巨型神像 / 火把长廊 / 骑兽冲阵 / 法阵俯拍 |
| 代表作 | 《封神第一部》《寻龙诀》 |

**锚点句（中）**：仰拍人与巨型青铜神像的体量对比，实景搭建与实体道具的材质质感（青铜锈、皮革、汗泥），火把 1800K 对夜蓝 4000K，浓烟中的可见光柱，1/3 升格伴随火星，编钟与大鼓。
**锚点句（英）**：`low-angle scale contrast between a human and a colossal bronze statue, practical sets and physical props with bronze patina, leather, sweat and mud, 1800K torchlight against 4000K night blue, volumetric beams through heavy haze, 1/3 speed ramp with flying embers, bianzhong bells and war drums`

**⚠️ 不要与之叠加**：粉彩柔光、去饱和纪实、静止长镜、明显 CG 词汇（`render`, `game engine`）。

---

# 四、日本

## 17. 黑泽明 Akira Kurosawa — 多机位长焦·风雨尘为角色·横向队列

（原速查行升格为完整条目）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **三角构图**（三人成三角，纵深错位站位）；**群像横向队列**（一排人平行于画面横向奔跑/行走）；**剪影树林**（前景树干竖线切割画面） | `triangular three-figure blocking in depth, a horizontal line of figures moving parallel to the frame, foreground tree trunks slicing the frame into vertical bands` |
| 运镜 | **多机位长焦同时拍**（三台机同时开，长焦捕捉真实反应，剪辑时可无缝跨接）；横向平移跟随奔跑；很少推轨 | `three cameras rolling simultaneously with long lenses on the same action, lateral tracking parallel to running figures` |
| 节奏 | 中速偏快，ASL **3–6s**；战斗段 1–2s；**突然定格**：动作顶点插入一个静止画面 | 战斗 1.5s，交代 5s，顶点插 1 个静止帧 |
| 升降格 | 极少慢动作；死亡瞬间偶用 1/2 速（《七武士》倒地）；更常用的是**突然的完全静止** | `1/2 speed only at the moment of death; more often an abrupt total freeze` |
| 色彩 | 黑白片：极端黑白反差、灰阶丰富；彩色期（《乱》《影武者》）用**纯色旗帜方阵**红/黄/黑对撞 | `high-contrast black and white with rich mid-greys; or pure primary-color banner armies in red, yellow and black` |
| 光影 | 硬顶光与逆光；雨中打灯让**雨丝可见**（雨里掺墨汁增强对比）；剪影大量出现；光比 8:1 | `hard backlight making every raindrop visible, ink-darkened rain, frequent silhouettes, 8:1 ratio` |
| 胶片/画幅 | 35mm；**长焦 100–250mm 压缩**（他把长焦引入动作片）；1.37:1（早期）与 2.35:1（后期） | `100-250mm telephoto compression, 35mm film, 1.37:1 academy or 2.35:1` |
| 音乐 | 早坂文雄 / 武满彻：西洋管弦 + 能乐笛鼓；**声音先行**（马蹄声先于画面） | `Western orchestra fused with Noh flute and drum, hoofbeats entering before the image` |
| 表现手法 | **风、雨、尘、雾作为角色**——每一场天气都在演戏；人物在极端天气中挣扎；横扫的风带动衣袍与旗帜 | `wind, rain, dust and fog as active characters, robes and banners whipped by constant wind` |
| 招牌镜头 | 暴雨中的村口决战 / 风中摇曳的芦苇与人 / 森林剪影骑行 / 旗帜方阵对峙 |
| 代表作 | 《七武士》《罗生门》《乱》《影武者》《用心棒》 |

**锚点句（中）**：长焦 200mm 压缩的横向队列奔跑，三角站位群像，强逆光让每一根雨丝可见的暴雨，风把衣袍与旗帜整片吹起，前景树干竖线切割画面，动作顶点突然完全静止。
**锚点句（英）**：`200mm telephoto compression on a horizontal line of running figures, triangular three-figure blocking, torrential rain hard-backlit so every raindrop is visible, wind whipping robes and banners, foreground tree trunks slicing the frame, an abrupt total freeze at the peak of the action, 8:1 contrast`

**⚠️ 不要与之叠加**：静止无风的空气、柔光平光、广角贴脸、平滑升格慢镜。

---

## 18. 小津安二郎 Yasujirō Ozu — 榻榻米低机位·绝对正面·空镜

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **tatami shot**：机位约离地 60–90cm（跪坐视线高度）平视；水平线严格；室内由拉门与柱子分割成几何格 | `tatami shot: camera 60-90cm above the floor at seated eye level, dead-level horizon, sliding shoji screens dividing the frame into rectangles` |
| 运镜 | **完全静止**：不摇不移不推（晚期作品几乎零运镜） | `absolutely static camera, no pan, no tilt, no dolly` |
| 节奏 | 中慢，ASL **6–12s**；对话段严格一人一镜交替 | 对话每句一镜，各 6–8s |
| 升降格 | 完全不用 | 禁写 slow motion |
| 色彩 | 彩色期：茶褐、米白、榻榻米黄绿，点缀一只红色水壶/毛巾（每场必有一点红）；低饱和 | `tea brown, off-white and tatami yellow-green with one small red object in every scene, low saturation` |
| 光影 | 均匀柔和的散射光，纸门透光；光比 2:1；几乎无阴影戏剧性 | `even diffused light through paper screens, 2:1 ratio, no dramatic shadows` |
| 胶片/画幅 | 35mm；**固定 50mm 一镜到底不换焦段**；1.37:1 学院画幅 | `single fixed 50mm lens for the entire film, 35mm, 1.37:1 academy ratio` |
| 音乐 | 轻快的弦乐小品，每场开头结尾各一段；情绪不随剧情起伏 | `light recurring string motif bookending each scene, emotionally neutral` |
| 表现手法 | **绝对正面对话**：说话者直视镜头（视线略偏），违反 180° 轴线规则；**空镜 pillow shot**：场与场之间插入无人的走廊/晾衣杆/烟囱/火车 3–5s | `frontal dialogue with the speaker looking almost directly into the lens, breaking the 180-degree rule; pillow shots of empty corridors, laundry poles and chimneys between scenes` |
| 招牌镜头 | 低机位榻榻米房间全景 / 正面说话的人 / 空走廊 / 远处的烟囱 |
| 代表作 | 《东京物语》《晚春》《秋刀鱼之味》 |

**锚点句（中）**：离地 80cm 的跪坐视线高度绝对静止机位，50mm 固定焦段，纸门散射均匀柔光 2:1，说话者近乎正对镜头，茶褐与榻榻米黄绿中一点红，场间插入 4 秒无人空镜。
**锚点句（英）**：`absolutely static tatami shot 80cm above the floor at seated eye level, fixed 50mm lens, even diffused light through paper screens at 2:1, the speaker looking almost straight into the lens, tea-brown and tatami-green palette with one small red object, a 4-second empty pillow shot between scenes, 1.37:1`

**⚠️ 不要与之叠加**：手持运镜、推轨、广角、低照度高反差、快切、大特写。

---

## 19. 是枝裕和 Hirokazu Kore-eda — 生活流长镜·饭桌群像·儿童视角

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **饭桌群像**：一家人围坐同框，谁也不给特写；**儿童视角**机位降到 100–120cm；门框与走廊做内框 | `family gathered around a low dining table all kept in one frame, camera lowered to a child's eye height of 100-120cm, doorways as inner frames` |
| 运镜 | 轻微手持或固定；跟随孩子小步移动；不做戏剧性运动 | `gentle handheld or locked-off, small reframes following a child, no dramatic camera moves` |
| 节奏 | 慢，ASL **8–20s**；一顿饭一镜；对白重叠自然 | 一场饭 20s 一镜，允许台词重叠 |
| 升降格 | 完全不用 | 禁写 slow motion |
| 色彩 | 自然生活色：木质暖褐、洗旧的棉布、夏日绿；中低饱和；室内 3800K，窗外 5600K | `naturalistic domestic palette of warm wood and faded cotton, summer green, 3800K interior against 5600K window` |
| 光影 | **自然光为主**，窗户柔光 + 天花板顶灯；光比 3:1；不打人物光 | `available window light plus a ceiling fixture, 3:1 ratio, no character-specific lighting` |
| 胶片/画幅 | 数字或 35mm；35–50mm 中焦，景深适中让全家清晰；1.85:1 | `35-50mm mid focal length with enough depth to hold the whole family, 1.85:1` |
| 音乐 | 极简钢琴或原声吉他，只在段落转换出现；大量无配乐 | `sparse piano or acoustic guitar only at transitions, long stretches with no score` |
| 表现手法 | **克制不煽情**：最悲伤的时刻反而不给音乐不给特写；生活细节（切菜、剪指甲、洗澡）承担情感 | `emotional restraint: the saddest moment gets no music and no close-up, feeling carried by mundane details like cooking and cutting nails` |
| 招牌镜头 | 一家人低桌吃饭 / 孩子背影走在堤岸 / 晾晒的衣物 / 夏日蝉鸣的午后 |
| 代表作 | 《步履不停》《小偷家族》《无人知晓》《海街日记》 |

**锚点句（中）**：一家人围低桌同框的 20 秒生活流长镜，机位降到儿童视线 110cm，窗户自然光 3:1 不打人物光，木质暖褐与夏日绿的自然色，最悲伤处不给音乐不给特写。
**锚点句（英）**：`a 20-second observational take of a family around a low table all held in one frame, camera lowered to a child's eye height of 110cm, available window light at 3:1 with no character lighting, naturalistic warm-wood and summer-green palette, no music and no close-up at the saddest beat`

**⚠️ 不要与之叠加**：煽情弦乐、推向脸的特写、风格化调色、快切。

---

## 20. 北野武 Takeshi Kitano — 暴力与静止交替·Kitano blue·无配乐沉默

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **正面固定机位**平视，人物并排站/坐，构图简单到近乎笨拙；大量留白的海与天 | `frontal locked-off eye-level framing, figures standing side by side in a deliberately plain composition, large empty expanses of sea and sky` |
| 运镜 | 几乎零运镜；暴力发生时机位也不动（不追、不摇） | `static camera even during the violence, the camera never chases the action` |
| 节奏 | **突然的暴力与静止交替**：静止段 ASL **8–15s** → 暴力 0.2–0.5s（常在画外或一击结束）→ 立即回到静止 | 静 10s + 暴力 0.3s + 静 8s |
| 升降格 | 完全不用；暴力越快越好，慢动作会毁掉突兀感 | 禁写 slow motion |
| 色彩 | **Kitano blue**：海蓝、天青、洗白的浅蓝构成主调，低饱和高明度；配一点血红 | `Kitano blue: sea-blue and pale washed-out azure dominating the palette at low saturation and high key, with one splash of blood red` |
| 光影 | 明亮均匀的自然日光，海滩强反射；光比 2:1；不做低照度 | `bright even natural daylight with strong beach reflection, 2:1 ratio` |
| 胶片/画幅 | 35mm；50mm 标准焦段正面拍；1.85:1 | `50mm standard lens shooting frontally, 1.85:1` |
| 音乐 | 久石让极简钢琴主题；但**关键暴力段完全无配乐**，只有环境声与突兀的枪响 | `Joe Hisaishi-style minimal piano theme, but total silence during the violence with only ambient sound and a sudden gunshot` |
| 表现手法 | 面无表情的黑色幽默；沉默取代台词；海滩、烟花、玩闹与死亡并置 | `deadpan gallows humor, silence instead of dialogue, beach games juxtaposed with death` |
| 招牌镜头 | 海边并排站立的背影 / 正面枪击 / 沙滩上的玩闹 / 空镜的海 |
| 代表作 | 《花火》《坏孩子的天空》《菊次郎的夏天》《座头市》 |

**锚点句（中）**：正面平视锁死机位，人物并排站在海边构图简单留白极大，Kitano blue 洗白浅蓝低饱和高明度，明亮均匀日光 2:1，静止十秒后 0.3 秒突发暴力且全程无配乐只有环境声。
**锚点句（英）**：`frontal locked-off eye-level shot, figures standing side by side by the sea with large empty negative space, washed-out pale Kitano blue at low saturation and high key, bright even daylight at 2:1, ten seconds of stillness broken by 0.3 seconds of sudden violence with no score, only ambience and one gunshot`

**⚠️ 不要与之叠加**：慢动作、手持晃动、低照度霓虹、连续配乐、快切。

---

## 21. 岩井俊二 Shunji Iwai — 过曝逆光柔雾·青春回忆·高调白

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物置于窗边/雪原/操场，背后是大片白；近距离半身像，构图松散随意 | `subject placed against a large white field of window light or snow, loose casual medium framing` |
| 运镜 | **手持轻微晃动**（呼吸感而非纪实感）；缓慢绕行；跟随奔跑的少年 | `subtle breathing handheld, slow arcing moves, following a running teenager` |
| 节奏 | 中速，ASL **2.5–5s**；回忆段用碎片短切 1s | 现实 4s，回忆碎片 1s |
| 升降格 | 3/4 微升格给奔跑与回头；不做重度慢镜 | `subtle 3/4 speed on a run or a turn of the head` |
| 色彩 | **高调白**：整体提亮、白位溢出、低对比；肤色偏粉，绿色偏青；色温 6000–7000K 偏冷但柔 | `high-key white with lifted blacks and blown-out highlights, low contrast, pinkish skin and cyan-leaning greens, 6000-7000K` |
| 光影 | **过曝逆光柔雾**：强逆光直射镜头形成雾化光晕（flare + halation）；正面加柔光板；光比 1.5:1 | `heavy backlight blown into a hazy bloom with halation, soft frontal fill, very low 1.5:1 ratio` |
| 胶片/画幅 | 16mm/35mm 质感，颗粒明显；50–85mm 浅景深；1.85:1；柔焦滤镜 | `grainy 16mm feel, 85mm shallow focus, soft-focus filter, 1.85:1` |
| 音乐 | 钢琴 + 弦乐的清澈主题（《Love Letter》）；歌曲整段铺满 | `clear piano-and-strings theme playing uninterrupted over whole sequences` |
| 表现手法 | **青春回忆感**：信件、雪、图书馆、自行车、未说出口的告白；时间在此刻被凝住 | `nostalgic adolescence: letters, snow, school library, bicycles, an unspoken confession` |
| 招牌镜头 | 雪原上呼喊 / 窗边逆光侧脸 / 图书馆窗帘飞起 / 自行车并行 |
| 代表作 | 《情书》《四月物语》《花与爱丽丝》 |

**锚点句（中）**：强逆光过曝成雾化光晕，整体高调提亮低对比 1.5:1，肤色偏粉绿色偏青，85mm 浅景深加柔焦滤镜与明显颗粒，轻微呼吸感手持，3/4 微升格给回头一瞬。
**锚点句（英）**：`hard backlight blown into a hazy bloom with halation, high-key lifted image at a very low 1.5:1 contrast, pinkish skin and cyan-leaning greens, 85mm shallow focus with soft filter and visible grain, subtle breathing handheld, 3/4 speed ramp on the turn of the head`

**⚠️ 不要与之叠加**：暗部压死、高饱和霓虹、硬阴影、静止机位对称构图。

---

## 22. 三池崇史 Takashi Miike — 极端风格化暴力美学

（"极端风格化暴力"槽位取此位；若需更抒情诡异的变体可换园子温）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 突然的极端景别跳跃（大全景直接切鼻尖特写）；漫画式夸张构图与倾斜地平线 | `abrupt jumps from extreme wide to extreme close-up, manga-like exaggerated framing with tilted horizons` |
| 运镜 | 混用：静止 → 突然甩摇 → 手持疾走；机位常做不合常规的位置（地面、天花板） | `static frames broken by sudden whip pans and running handheld, camera placed at floor or ceiling level` |
| 节奏 | 极不均匀，ASL **0.8–2s**（暴力段）与 10s+（诡异静场）反复对撞 | 静场 10s 与 0.8s 快切交替 |
| 升降格 | 短促 1/2 升格给喷溅与断肢的一瞬，随即回实速；也用快放（2×）制造荒诞 | `brief 1/2 speed on the splatter instant, plus 2x fast motion for absurdity` |
| 色彩 | 高饱和：血红 + 荧光绿 + 电视机蓝；对比极强 | `high-saturation blood red, fluorescent green and CRT blue, extreme contrast` |
| 光影 | 硬光直打、色纸灯（gel）大面积染色；光比 8:1；舞台化布光 | `hard direct key with heavy colored gels, 8:1 ratio, theatrical lighting` |
| 胶片/画幅 | 数字/35mm；广角 21–28mm 变形；1.85:1 / 2.35:1 | `21-28mm wide-angle distortion, 2.35:1` |
| 音乐 | 反差配乐：欢快歌谣配屠杀；或完全静音只留环境声 | `cheerful song over a massacre, or total silence with only ambient sound` |
| 表现手法 | 暴力被推到荒诞的临界点后变成喜剧；仪式化的残酷；突然打破类型 | `violence pushed past absurdity into comedy, ritualized cruelty, sudden genre rupture` |
| 招牌镜头 | 榻榻米上的血泊俯拍 / 一镜内的极端景别跳跃 / 面无表情的施暴者特写 |
| 代表作 | 《切肤之爱》《杀手阿一》《十三刺客》 |

**锚点句（中）**：大全景直切鼻尖特写的极端景别跳跃，色纸灯把画面染成血红与荧光绿，硬光 8:1 舞台化布光，静场十秒后 0.8 秒快切爆发，喷溅瞬间 1/2 升格，欢快歌谣配屠杀。
**锚点句（英）**：`abrupt jump from extreme wide to extreme close-up, heavy colored gels flooding the frame in blood red and fluorescent green, hard theatrical key at 8:1, ten seconds of stillness then 0.8s rapid cutting, brief 1/2 speed on the splatter, a cheerful song playing over the carnage`

**⚠️ 不要与之叠加**：自然光写实、克制留白、低饱和、稳定长镜。

---

# 五、韩国

## 23. 奉俊昊 Bong Joon-ho — 横向平移揭示阶层·垂直空间隐喻·类型混搭

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **精确构图**（他有全片手绘分镜）；**垂直空间隐喻**：楼梯、半地下室、天台——上下位置即阶级位置；人物常被楼梯栏杆水平切分 | `meticulously pre-planned framing, vertical class metaphor with staircases and semi-basement levels, characters divided by stair railings` |
| 运镜 | **横向平移揭示社会阶层**：一个缓慢横移从一端摇到另一端，把两个阶层放进同一镜；升降跟随楼梯上下 | `a slow lateral track revealing two social classes within one continuous shot, vertical crane following the staircase` |
| 节奏 | 中速，ASL **4–7s**；揭示性长镜可到 15s；类型转折处节奏突变 | 常规 5s，揭示镜 15s |
| 升降格 | 少量；灾难/暴力关键点 1/2 升格 0.5s；更常用突然的实速冲击 | `1/2 speed for half a second at the key impact only` |
| 色彩 | 冷绿灰 + 暖木黄的阶层对照（地下 = 冷绿霉，地上 = 暖木金）；中等饱和 | `cold mildew-green for the basement against warm wood-gold for the upper house, moderate saturation` |
| 光影 | 上层大面积柔和自然光（落地窗），下层单一荧光灯与地面反射；光比上层 2:1、下层 6:1 | `soft floor-to-ceiling window light upstairs at 2:1 versus a single fluorescent tube downstairs at 6:1` |
| 胶片/画幅 | 数字（ARRI）；35–50mm 为主，**2.35:1 宽画幅利于横向阶层并置** | `35-50mm, digital, 2.35:1 widescreen for lateral juxtaposition` |
| 音乐 | 郑在日式弦乐圆舞曲，优雅与荒诞并置；配乐在类型切换时变奏 | `elegant string waltz set against grotesque imagery, the theme mutating at each genre shift` |
| 表现手法 | **类型混搭**：喜剧→惊悚→悲剧在同一场内切换；雨作为阶级的分水岭；气味/台阶等具体符号 | `genre shifting from comedy to thriller to tragedy within one scene, rain as the dividing line between classes` |
| 招牌镜头 | 暴雨中一路向下走的长阶梯 / 半地下室窗口平视街面 / 长桌俯拍 / 横移串联两个空间 |
| 代表作 | 《寄生虫》《杀人回忆》《母亲》《雪国列车》 |

**锚点句（中）**：一次缓慢横移把两个阶层放进同一个 2.35:1 画面，楼梯与半地下室的垂直空间隐喻，上层落地窗柔光 2:1 对下层单管荧光 6:1，冷绿霉对暖木金，优雅弦乐圆舞曲配荒诞画面。
**锚点句（英）**：`a slow lateral track revealing two social classes inside one 2.35:1 frame, vertical staircase and semi-basement class metaphor, soft window light at 2:1 upstairs against a single fluorescent tube at 6:1 below, cold mildew-green versus warm wood-gold, an elegant string waltz over grotesque imagery`

**⚠️ 不要与之叠加**：手持混乱、极端风格化色块、无构图纪实。

---

## 24. 朴赞郁 Park Chan-wook — 华丽运镜·对称暴力美学·镜面反射

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **对称与暴力美学**：古典对称构图里发生残酷之事；**镜面与反射**（镜子、玻璃、水面、刀面）造双重人像；极端俯拍平面构图 | `classical symmetry containing brutal action, doubled portraits through mirrors, glass, water and blade reflections, extreme overhead flat compositions` |
| 运镜 | **华丽复杂运镜**：一镜内从室内穿到室外、从这个人的过去滑到另一个人的现在；360° 环绕；镜头穿过窗与洞 | `elaborate continuous camera moves gliding from interior to exterior and across time within a single take, 360-degree orbits, camera passing through windows and holes` |
| 节奏 | 中速，ASL **3–6s**；著名的走廊横向打斗为 2D 平面横移一镜 **25s+** | 常规 4s；横向平面打斗一镜 25s |
| 升降格 | 1/2 升格给唯美暴力瞬间；也用定格 + 章节字卡 | `1/2 speed on the aestheticized violent moment, freeze frame with chapter title card` |
| 色彩 | **饱和绿与红**：墨绿墙纸、酒红丝绒、金饰；高饱和高对比 | `saturated deep green wallpaper against wine-red velvet and gold, high saturation and contrast` |
| 光影 | 精致的舞台式布光，硬边光 + 色纸；光比 5:1；高光反射在金属与镜面上 | `precise theatrical lighting with hard-edged gelled sources at 5:1, specular highlights on metal and mirrors` |
| 胶片/画幅 | 数字/35mm；广角 24mm 华丽运镜 + 85mm 特写交替；2.35:1 | `24mm for the elaborate moves intercut with 85mm close-ups, 2.35:1` |
| 音乐 | 巴洛克/古典弦乐与华尔兹，与残酷画面形成反讽；重复的主题动机 | `baroque strings and waltz ironically scoring cruelty` |
| 表现手法 | 复仇三部曲式的宿命结构；情色与暴力同构；道具的仪式化使用（锤、剪刀、章鱼） | `ritualized use of props, eroticism and violence sharing the same visual grammar` |
| 招牌镜头 | 走廊 2D 横移打斗一镜 / 镜中双重人像 / 俯拍平铺的房间 / 慢镜落下的物件 |
| 代表作 | 《老男孩》《小姐》《亲切的金子》《分手的决心》 |

**锚点句（中）**：古典对称构图中发生残酷，镜面与刀面造双重人像，24mm 一镜华丽穿过窗户从室内滑到室外，墨绿与酒红高饱和硬边色纸光 5:1，巴洛克弦乐反讽，唯美暴力瞬间 1/2 升格。
**锚点句（英）**：`classical symmetry containing brutal action, doubled portraits in mirrors and blade reflections, an elaborate 24mm continuous move gliding through a window from interior to exterior, saturated deep green and wine red under hard gelled light at 5:1, baroque strings scoring the cruelty, 1/2 speed on the violent beat, 2.35:1`

**⚠️ 不要与之叠加**：纪实手持、低饱和自然光、简陋构图、静止长镜。

---

## 25. 李沧东 Lee Chang-dong — 长镜纪实·自然光·留白结尾

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 松散的纪实构图，不追求美；人物在真实空间里被环境包围；常从背后跟拍 | `loose documentary framing with no beautification, the figure surrounded by a real environment, frequently followed from behind` |
| 运镜 | 缓慢手持跟随或固定；镜头保持礼貌距离，不侵入 | `slow handheld following or locked-off, the camera keeping a respectful distance` |
| 节奏 | 慢，ASL **15–45s**；著名的黄昏起舞长镜可达数分钟 | 单镜 30s+，情绪段不切 |
| 升降格 | 完全不用 | 禁写 slow motion |
| 色彩 | 完全自然：黄昏金 2900K、阴天青 6500K；低饱和无风格化调色 | `entirely naturalistic, 2900K golden dusk or 6500K overcast, low saturation with no stylized grade` |
| 光影 | **只用自然光**，包括黄昏 magic hour 逐渐变暗的真实过程；光比随天光变化 | `available light only, including a real magic-hour fade where the light genuinely dies during the take` |
| 胶片/画幅 | 35mm/数字；35–75mm；1.85:1 / 2.35:1 | `35-75mm, 1.85:1` |
| 音乐 | 极少配乐；一段爵士小号或环境声；关键处完全静默 | `almost no score, one jazz trumpet cue at most, silence at the key moment` |
| 表现手法 | **去戏剧化**：高潮被推到画外或干脆省略；**留白结尾**：不解释、不回答，停在一个无解的画面 | `de-dramatized structure with the climax withheld or off-screen, an open unresolved final image that explains nothing` |
| 招牌镜头 | 黄昏中的舞蹈长镜 / 田野尽头的奔跑 / 背影跟拍 / 停在空景的结尾 |
| 代表作 | 《燃烧》《诗》《密阳》《绿洲》 |

**锚点句（中）**：30 秒缓慢手持跟拍背影的纪实长镜，只用黄昏自然光并让光在镜头内真实变暗，2900K 金色低饱和无调色，无配乐只有风声，结尾停在一个不作解释的空景。
**锚点句（英）**：`a 30-second slow handheld documentary take following the figure from behind, available magic-hour light genuinely fading during the shot, 2900K golden low-saturation with no stylized grade, no score except wind, ending on an open unresolved empty frame`

**⚠️ 不要与之叠加**：风格化调色、配乐煽情、快切、人工布光、慢动作。

---

## 26. 罗泓轸 Na Hong-jin — 类型片紧张调度·泥泞追逐

（"类型片紧张调度"槽位取此位；若需丧尸/密闭空间灾难可换延尚昊）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 狭窄巷弄与坡道的压迫构图；追逐中主体常被前景遮挡半掩；信息不完整 | `oppressive framing in narrow alleys and steep slopes, the subject repeatedly half-hidden behind foreground obstacles during the chase` |
| 运镜 | **手持疾走跟拍**，摄影机与被摄者同样喘息；突然的甩摇丢失目标再找回 | `breathless handheld running with the subject, whip pans that lose and re-find the target` |
| 节奏 | 快，追逐段 ASL **1–2s**；铺垫段拉到 8–12s 形成落差 | 铺垫 10s → 追逐 1.5s 连切 |
| 升降格 | 极少；关键刺击 1/2 速 0.3s；主要靠实速的粗暴 | `1/2 speed for 0.3s at the stabbing only` |
| 色彩 | 雨夜青灰、泥褐、荧光灯绿；低饱和脏调 | `rainy blue-grey, mud brown and fluorescent green, dirty low saturation` |
| 光影 | 低照度实用光（路灯、手电、车灯）；雨幕反光；光比 8:1 | `low-light practicals — streetlamps, flashlights, headlights — through rain, 8:1 ratio` |
| 胶片/画幅 | 数字；24–35mm 贴身广角；2.35:1；高感光噪点可接受 | `24-35mm close handheld wide, 2.35:1, noise acceptable` |
| 音乐 | 打击乐脉冲 + 不谐和弦；追逐时音乐停只留喘息与脚步 | `percussive pulse and dissonant strings, dropping to breath and footsteps during the chase` |
| 表现手法 | **体力的真实消耗**（跑到跑不动）；暴力笨拙而非帅气；泥、雨、血混在一起 | `real physical exhaustion, clumsy unglamorous violence, mud, rain and blood mixed together` |
| 招牌镜头 | 雨夜坡道追逐 / 巷口撞击 / 手电筒扫过的林中 / 喘息的近景 |
| 代表作 | 《追击者》《黄海》《哭声》 |

**锚点句（中）**：手持疾走跟拍与被摄者一样喘息，狭窄雨夜坡道 1.5 秒连切，路灯与手电为唯一光源 8:1 低照度，泥褐与荧光绿脏调，追逐时音乐停只留脚步与喘息。
**锚点句（英）**：`breathless handheld running alongside the subject, 1.5s rapid cutting through narrow rainy alleys and slopes, streetlamps and flashlights as the only sources at 8:1 low light, dirty mud-brown and fluorescent-green grade, music dropping out to leave only footsteps and gasping`

**⚠️ 不要与之叠加**：稳定器优雅滑行、对称构图、明亮布光、抒情配乐。

---

# 六、日本动画（画风锚点）

> 本节维度与真人不同。动画不存在"胶片感光"与"实拍光比"，请改用六维：
> **线条 / 上色 / 背景 / 光效 / 运动规律 / 摄影机**。
> 提示词写法上，动画锚点必须先声明媒介（`2D hand-drawn anime`），否则模型会滑向真人。

## 27. 宫崎骏 Hayao Miyazaki — 手绘水彩·飞行动线·留白的"间"

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 线条 | 均匀细黑描边，粗细变化小；角色圆润无锐角；手绘轻微抖动感 | `even thin black outlines with minimal line weight variation, rounded character shapes, subtle hand-drawn line wobble` |
| 上色 | 平涂 + 两级阴影（本影 + 一级暗部），不做渐变；肤色偏暖米白 | `flat cel shading with only two tones (base plus one shadow), no gradients, warm cream skin` |
| 背景 | **手绘水彩背景**，笔触与纸纹可见；饱和自然绿的草地与森林；比角色精细度更高 | `hand-painted watercolor backgrounds with visible brush texture and paper grain, saturated natural greens, backgrounds more detailed than characters` |
| 光效 | 柔和自然的天光；**云的体积感**（层积云被画成有厚度的实体）；不用镜头光晕 | `soft natural daylight, volumetric cumulus clouds painted as solid masses, no lens flare` |
| 运动规律 | **飞行动线**：滑翔、俯冲、上升气流有明确弧线；食物与风的动画格外用力；重量感真实 | `clear arcing flight paths of gliding and diving, exaggerated care on food and wind animation, believable weight` |
| 摄影机 | 缓慢横摇与推近；**留白的"间"（ma）**：动作之间插入 3–5s 无事发生的静止镜（发呆、云过、风吹草） | `slow pans and gentle push-ins, plus a 3-5 second "ma" pause shot where nothing happens — clouds drifting, grass in the wind` |
| 代表作 | 《龙猫》《千与千寻》《天空之城》《风之谷》 |

**锚点句（中）**：2D 手绘动画，均匀细描边配两级平涂上色，手绘水彩背景可见笔触与纸纹，饱和自然绿，云被画成有厚度的实体，缓慢横摇后插入 4 秒风吹草的静止空镜。
**锚点句（英）**：`2D hand-drawn anime, even thin outlines with two-tone flat cel shading, hand-painted watercolor backgrounds with visible brush texture and paper grain, saturated natural green, volumetric cumulus clouds as solid masses, a slow pan followed by a 4-second still "ma" shot of grass in the wind`

**⚠️ 不要与之叠加**：镜头光斑与耀斑、3D 渲染感、高对比赛博色、快切。

---

## 28. 新海诚 Makoto Shinkai — 光晕耀斑·极致天空·雨与玻璃

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 线条 | 细锐清晰描边，角色线条比宫崎骏更硬；细节密度高 | `crisp sharp thin outlines, higher detail density than classic hand-drawn` |
| 上色 | 平涂 + 多级渐变叠加，**高饱和青蓝与橙**的互补配色；肤色通透带反光 | `cel shading layered with gradients, highly saturated cyan-blue complemented by orange, translucent skin with rim reflections` |
| 背景 | **极致天空与云**：占画面 50% 以上的天空，云层层次极多；城市背景照片级写实（电线、护栏、自动贩卖机） | `sky occupying more than half the frame with extremely layered clouds, photoreal urban backgrounds with power lines, guardrails and vending machines` |
| 光效 | **超写实光晕与镜头光斑**：anamorphic 横向光斑、逆光耀斑、光晕溢出（bloom + halation）；**雨滴与玻璃反射**、水面折射 | `photoreal bloom and anamorphic lens flare, strong backlit glare, raindrops on glass with refraction and reflection` |
| 运动规律 | 角色动作偏克制写实；**环境动画极繁**（雨、风、飘落物、光斑移动）；节奏靠环境而非角色 | `restrained realistic character motion against extremely busy environmental animation of rain, wind and drifting particles` |
| 摄影机 | 大量模拟真实镜头行为：浅景深虚化、焦点转移、轻微手持晃动、仰角望天 | `simulated real-camera behavior: shallow depth of field, rack focus, subtle handheld drift, low-angle looking up at the sky` |
| 代表作 | 《你的名字。》《言叶之庭》《天气之子》《秒速五厘米》 |

**锚点句（中）**：2D 动画但模拟真实镜头，天空占据一半以上画面且云层极多，超写实光晕与横向镜头光斑，雨滴挂在玻璃上折射反光，高饱和青蓝配橙，浅景深与焦点转移，仰角望天。
**锚点句（英）**：`2D anime with simulated real-camera optics, sky filling over half the frame with heavily layered clouds, photoreal bloom and anamorphic lens flare, raindrops on glass refracting the light, saturated cyan-blue against orange, shallow depth of field with rack focus, low angle looking up`

**⚠️ 不要与之叠加**：去饱和写实调、水彩纸质感、平光无光斑、极简背景。

---

## 29. 今敏 Satoshi Kon — 匹配剪辑跳转·密集城市·心理蒙太奇

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 线条 | 写实人体比例，线条硬朗；面部表情夸张变形用于心理外化 | `realistic body proportions with firm hard lines, faces distorting for psychological effect` |
| 上色 | 中等饱和写实上色，阴影分级细；不追求梦幻通透 | `moderately saturated realistic shading with fine shadow steps` |
| 背景 | **密集城市细节**：堆满杂物的房间、招牌林立的街道、垃圾与电线；信息量极大 | `dense urban clutter, rooms overflowing with objects, streets crammed with signage, wires and trash` |
| 光效 | 写实室内光与霓虹混合；不做大面积光晕 | `realistic mixed interior and neon light, no heavy bloom` |
| 运动规律 | 现实动作写实；幻想段落物理规则突变（坠落、追逐、变形） | `realistic motion in reality, physics breaking in the fantasy passages` |
| 摄影机 | **现实与幻想的匹配剪辑跳转**（match cut）：动作/形状/颜色相同的两个镜头直接对接，一秒换时空；**心理蒙太奇**：0.3–0.8s 碎片连切 | `match cut between reality and fantasy on identical motion, shape or color, switching time and space in a single frame; psychological montage of 0.3-0.8s fragments` |
| 代表作 | 《千年女优》《未麻的部屋》《红辣椒》《东京教父》 |

**锚点句（中）**：2D 动画写实人体与硬朗线条，堆满杂物与招牌的密集城市背景，通过动作与形状完全一致的匹配剪辑在一帧内从现实跳进幻想，0.5 秒碎片连切的心理蒙太奇。
**锚点句（英）**：`2D anime with realistic proportions and firm lines, dense cluttered urban backgrounds packed with signage and objects, a match cut on identical motion and shape jumping from reality into fantasy within a single frame, psychological montage of 0.5-second fragments`

**⚠️ 不要与之叠加**：留白静止的"间"、水彩柔背景、缓慢长镜、高调柔光。

---

## 30. 押井守 Mamoru Oshii — 低饱和青灰赛博·静止长镜·水面倒影

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 线条 | 精密机械线条，硬表面细节极多；角色面部克制少表情 | `precise mechanical linework with dense hard-surface detail, restrained expressionless faces` |
| 上色 | **低饱和青灰**为主调，接近单色；金属反光冷硬 | `desaturated blue-grey near-monochrome palette, cold hard metallic speculars` |
| 背景 | 潮湿的亚洲城市（招牌、运河、旧楼）；**机械细节**（管线、装甲、义体接口）密度极高 | `humid Asian cityscape of signage, canals and aging blocks, extremely dense mechanical detail of pipes, armor and cyber ports` |
| 光效 | 阴天散射与冷荧光；**雨与水面倒影**贯穿；偶有强逆光剪影 | `overcast diffusion and cold fluorescent light, constant rain and water reflections, occasional hard backlit silhouette` |
| 运动规律 | 动作极少但一旦发生极快极准；**静止长镜**中只有雨、水波、旗帜在动 | `almost no movement, then sudden precise action; in the still long takes only rain, ripples and flags move` |
| 摄影机 | 静止或极慢横移；城市空镜蒙太奇段落可长达 3 分钟无对白 | `static or extremely slow lateral pans, a wordless three-minute city montage` |
| 代表作 | 《攻壳机动队》《空中杀手》《人狼》 |

**锚点句（中）**：2D 动画，低饱和青灰接近单色，潮湿亚洲城市与极密机械管线细节，阴天散射与冷荧光，持续的雨与水面倒影，静止长镜中只有水波在动，无对白的城市空镜蒙太奇。
**锚点句（英）**：`2D anime in a desaturated blue-grey near-monochrome palette, humid Asian cityscape with extremely dense mechanical pipe detail, overcast diffusion and cold fluorescent light, constant rain and water reflections, static long take where only the ripples move, a wordless city montage`

**⚠️ 不要与之叠加**：高饱和暖调、镜头光斑、快切、明亮高调。

---

## 31. 现代 TV 动画风（京都动画式）— 细腻日常光影·逆光通透

（非单一作者，作为"现代日常系 TV 动画"的通用画风槽位）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 线条 | 细腻均匀的清晰描边，发丝分股细致；角色比例偏可爱但不夸张 | `clean even fine outlines with individually separated hair strands, gently stylized proportions` |
| 上色 | 平涂 + 柔和渐变，**肤色通透带血色**；发梢有反射高光环 | `cel shading with soft gradients, translucent skin with warm blush, glossy highlight band on hair` |
| 背景 | 精细写实的日常空间（教室、便利店、电车、河堤）；透视严谨；季节感明确 | `finely rendered everyday spaces — classroom, convenience store, train car, riverbank — with strict perspective and clear seasonal cues` |
| 光效 | **细腻日常光影**：窗光斜射的光斑、树影、**逆光通透感**（耳廓与发梢透光）；轻度 bloom | `delicate daylight patches through windows, leaf shadows, translucent backlight glowing through ears and hair tips, light bloom` |
| 运动规律 | 高帧率的细微动作（眨眼、手指、呼吸、衣摆）；日常动作被认真作画 | `high-frame-rate micro-motion of blinking, fingers, breathing and hems; mundane actions fully animated` |
| 摄影机 | 模拟真实镜头的浅景深与轻微推移；低角度桌面视点；固定镜为主 | `simulated shallow depth of field with gentle push-ins, low tabletop viewpoints, mostly locked frames` |
| 代表作 | 现代日常系 TV 动画通用风格 |

**锚点句（中）**：2D TV 动画风，细腻均匀描边与分股发丝，肤色通透带血色，教室窗光斜射的光斑与树影，逆光下耳廓与发梢透光，眨眼与衣摆的高帧率微动作，浅景深轻推。
**锚点句（英）**：`modern 2D TV anime style, clean fine outlines with separated hair strands, translucent skin with warm blush, slanted window light patches and leaf shadows in a classroom, backlight glowing through ears and hair tips, high-frame-rate micro-motion of blinking and clothing hems, shallow depth of field with a gentle push-in`

**⚠️ 不要与之叠加**：粗犷线条、低饱和赛博灰、暴力风格化、密集快切。

---

# 七、一行式速查（随取随用）

| 导演 | 地区/领域 | 一行锚点（可直接贴进提示词） |
|---|---|---|
| 陈英雄 Tran Anh Hung | 越南/法语 | 湿热绿荫的室内、纱帘过滤的柔光、食物与手部特写、缓慢横移、雨声与蝉鸣、ASL 8–15s |
| 许鞍华 | 香港 | 市井实景纪实、自然光与荧光灯、中景不炫技、女性日常长镜、ASL 6–10s、无风格化调色 |
| 关锦鹏 | 香港 | 幽暗华丽的旧式室内、镜面与帘幕层叠、暖钨丝 2800K 配冷夜、旗袍质感特写、缓慢推近 |
| 张婉婷 | 香港 | 温润怀旧暖调、书信与旁白、跨地域时代感、柔光人像 85mm、金曲铺底 |
| 李屏宾 | —— | **见 DP 册**（`dp-cinematographer-anchors.md`）：他是摄影指导，不作导演锚点使用 |
| 宁浩 | 内地 | 多线索黑色喜剧、快速交叉剪辑 ASL 1.5–2.5s、手持中近景、西北土黄与荧光绿、荒诞巧合 |
| 陈思诚 | 内地 | 高饱和异域街景（唐人街）、快节奏商业剪辑、俯拍城市、推理定格闪回、明亮通透打光 |
| 饺子（《哪吒》） | 内地动画 | 3D 渲染但保留东方水墨元素、夸张变形表情、高速动作拖影、火焰与法术粒子、赤红与青金对撞 |
| 田晓鹏（《大圣归来》） | 内地动画 | 写意山水背景配 3D 角色、毛发与布料细节、金红主色、大场面仰角、传统纹样 |
| 汤浅政明 | 日本动画 | 扭曲变形的线条与透视、大胆撞色平涂、液态流动的运动、极端夸张肢体、跳脱物理规律 |
| 细田守 | 日本动画 | 明亮高调的夏日、清澈蓝天与白云、极简干净的背景、家庭群像、几何化数字空间 |
| 庵野秀明 | 日本动画 | 突然的静止定格数秒、极端字幕排版插入、仰角与俯角对撞、单色红黑闪切、电线杆与十字架剪影 |
| 金基德 | 韩国 | 极少对白、水面与孤岛、原始残酷的诗意、自然光低饱和、静止长镜 ASL 15s+ |
| 洪常秀 | 韩国 | 廉价数字质感、固定机位加突兀的变焦推、饭桌喝酒长对话、自然光、同一情节重复变奏 |
| 滨口龙介 | 日本 | 长时间正反打对话、朗读式平淡表演、车内双人镜、自然光、ASL 10–20s、无配乐 |
| 河濑直美 | 日本 | 手持贴近身体与手部、逆光透过树叶、自然与身体的触感、纪录与虚构混合、16mm 颗粒 |
| 张律 | 中/韩 | 边界与异乡感、固定长镜、冷灰低饱和、空旷街道、留白结尾 |
| 万玛才旦 | 藏地 | 高原强紫外线硬光、极远景中的小人、藏红与土黄、固定长镜 ASL 20s+、方言与风声 |
| 魏书钧 | 内地 | 青年迷惘的手持中景、夏日过曝、自嘲式冷幽默、片场/县城质感、松散节奏 |

---

# 八、亚洲导演横向对照表

| 导演 | 平均镜长 ASL | 运镜性格 | 色彩 | 光比 | 升格用法 |
|---|---|---|---|---|---|
| 徐克 | 0.6–1.5s（全景 2s） | 垂直吊拍升降 | 赤红+金+墨黑高饱和 | 高（4:1–8:1 硬逆光） | 抽帧顿挫+2 帧定格 |
| 胡金铨 | 动作 0.3–0.8s / 静场 5–8s | 静止 + 突然甩摇 | 竹绿土黄自然 | 中（3:1 斑驳光） | 不用，靠拼贴造跃 |
| 程小东 | 1.2–2.5s（飘浮 3.5s） | 吊臂环绕升起 | 冷月蓝白+一抹朱砂 | 高（6:1 逆光剪影） | 大量 1/2–1/3 |
| 袁和平 | 2.5–5s | 微移保双人同框 | 自然中性 | 低（2:1–3:1 高调） | 几乎不用 |
| 王家卫 | 1.5–3s | 手持广角贴身 | 霓虹绿品红高饱和 | 中高（6:1） | 抽帧拖影 |
| 侯孝贤 | 20–90s | 绝对固定远观 | 自然低饱和 | 高（8:1 只用窗光） | 不用 |
| 蔡明亮 | 60–360s | 零运镜 | 潮湿霉绿冷灰 | 极高（10:1 单实用光） | 不用 |
| 贾樟柯 | 12–40s | 手持 + 变焦推 | 灰蓝雾霾低饱和 | 低（3:1 阴天） | 不用 |
| 毕赣 | 60s–数十分钟 | 旋转跟随一镜 | 苔绿对灯箱红 | 极高（12:1 裸灯） | 不用，靠漂浮运镜 |
| 姜文 | 1.5–3s | 随台词加速 | 金黄赤红湛蓝高饱和 | 高（5:1 正午硬光） | 1/2 只给荒诞奇观 |
| 张艺谋 | 1.5–3s / 仪式 4–6s | 大俯拍 + 长平移 | 单色填满极饱和 | 低（2:1 均匀色光） | 1/4 + 飘落物 |
| 杜琪峰 | 5–10s | 锁死静止 | 冷蓝 + 钠黄低饱和 | 高（8:1 单侧硬光） | 用静止代替 |
| 李安 | 5–9s | 缓推至情绪点停住 | 竹绿湖水青温润 | 中低（3:1 纱帘柔光） | 1/2 只给腾空一瞬 |
| 陈可辛 | 3–5s（情绪 8s） | 呼吸手持推向脸 | 琥珀市井暖调 | 低（3:1 柔光） | 3/4 情感高点 |
| 刁亦男 | 8–20s | 长镜追随 | 霓虹品红青绿嵌雪夜 | 高（8:1 混色温） | 几乎不用 |
| 乌尔善 | 1.5–3s（奇观 3.5s） | 环绕升降揭示规模 | 青铜金+朱砂红压暗 | 高（6:1 火光烟雾） | 1/3 + 火星尘土 |
| 黑泽明 | 3–6s（战斗 1.5s） | 多机长焦 + 横移 | 高反差黑白 / 纯色旗阵 | 高（8:1 雨中逆光） | 少；改用突然定格 |
| 小津安二郎 | 6–12s | 完全静止 | 茶褐米白 + 一点红 | 低（2:1 纸门散射） | 不用 |
| 是枝裕和 | 8–20s | 轻手持 / 固定 | 木质暖褐夏日绿 | 低（3:1 窗光） | 不用 |
| 北野武 | 静 8–15s / 暴力 0.3s | 完全静止不追 | Kitano blue 高明度低饱和 | 低（2:1 明亮日光） | 不用 |
| 岩井俊二 | 2.5–5s（回忆 1s） | 轻微呼吸手持 | 高调白 + 粉青 | 极低（1.5:1 过曝逆光） | 3/4 微升格 |
| 三池崇史 | 暴力 0.8–2s / 静场 10s+ | 静止 → 甩摇 → 疾走 | 血红荧光绿电视蓝 | 高（8:1 色纸硬光） | 1/2 喷溅瞬间 + 2× 快放 |
| 奉俊昊 | 4–7s（揭示 15s） | 横移揭示阶层 | 冷绿霉 vs 暖木金 | 分层（上 2:1 / 下 6:1） | 1/2 仅 0.5s |
| 朴赞郁 | 3–6s（横向打斗 25s） | 华丽穿越式长镜 | 墨绿酒红高饱和 | 中高（5:1 舞台光） | 1/2 唯美暴力 |
| 李沧东 | 15–45s | 缓慢手持跟背影 | 自然黄昏金低饱和 | 随天光变化 | 不用 |
| 罗泓轸 | 追逐 1–2s / 铺垫 8–12s | 手持疾走喘息 | 雨夜青灰泥褐 | 高（8:1 路灯手电） | 1/2 仅 0.3s |

> 动画五位不进本表（无实拍光比）。选动画风格时直接用第六节的六维锚点。

---

# 九、⚠️ 本册内部禁忌组合

| 冲突组合 | 为什么冲突 |
|---|---|
| 小津安二郎 + 手持运镜 | 他的全部语言建立在"机位绝对不动"上，一晃就不是他了 |
| 杜琪峰 + 慢动作 | 他刻意用"静止"替代慢动作，这是他与吴宇森的分水岭 |
| 侯孝贤 + 快切 | 他的意义产生于时间的堆积，切碎后只剩空景 |
| 新海诚 + 去饱和写实 | 他的核心是高饱和光晕与耀斑，去饱和等于删掉他 |
| 徐克 + 平滑连续升格 | 他要的是"顿"（抽帧），平滑慢镜会把顿挫抹平成程小东 |
| 程小东 + 抽帧顿挫 | 反过来同理：飘逸与顿挫互相抵消，输出会变成普通打斗 |
| 袁和平 + 0.5s 快切 | 他的价值就是"不靠剪辑造假"，快切直接否定其存在意义 |
| 蔡明亮 + 任何运镜/配乐 | 零运镜与无配乐是他仅有的两条规则 |
| 北野武 + 慢动作暴力 | 他的暴力必须突兀而短，慢镜会变成吴宇森式浪漫 |
| 黑泽明 + 静止无风的空气 | 风雨尘是他的角色，空气一静整套语法失效 |
| 王家卫 + 对称构图 | 残缺遮挡构图与对称是根本对立 |
| 张艺谋 + 多色混杂 | 他的规则是"一段只用一个主色"，混色即失效 |
| 李沧东 + 风格化调色与配乐 | 他的力量来自"看起来没有被处理过" |
| 宫崎骏 + 镜头光斑 | 手绘水彩体系里出现 lens flare 会直接跳成新海诚 |
| 押井守 + 高饱和暖调 | 他的赛博感建立在近单色青灰上 |
| 任意真人导演 + 任意动画画风 | 媒介冲突，模型会输出"3D 塑料感"的四不像 |
| 同时叠加 3 位以上导演 | 特征互相抵消，输出变成平庸平均值 |

## ✅ 本册推荐的互补组合

- **徐克（动作语法）+ 张艺谋（单色块）** → 高概念东方武侠广告
- **杜琪峰（静止对峙）+ 王家卫（霓虹色彩）** → 港式黑色（只借色彩，不借抽帧）
- **侯孝贤（固定长镜）+ 李屏宾式自然光** → 华语文艺（光见 DP 册）
- **奉俊昊（横移揭示）+ 刁亦男（霓虹雪夜）** → 东亚社会派惊悚
- **是枝裕和（生活流）+ 岩井俊二（高调逆光）** → 日系青春家庭片
- **黑泽明（风雨群像）+ 乌尔善（材质质感）** → 东方史诗战争

---

# 十、东方影像的三个独有语法

> 这三条不属于任何单一导演，是整册的底层语法。**它们最容易被写成空话，所以每条都给出可执行参数**。

## 1. 留白与"间"（ma 間）

- **不是**"很有意境"，**而是**：在两个事件之间插入一个 **3–6s 什么都不发生的镜头**（空院、云、风吹帘、水面），画面主体占比 <20%，其余为负空间；此镜无对白、无配乐，只有环境声。
- 参数化：`ASL ≥6s + 主体占画面 <20% + 负空间 >60% + 无配乐仅环境声 + 静止机位`
- **中文写法**：切入一个 5 秒空镜，画面里只有随风摆动的帘子，人物已离开，无配乐只有风声与远处犬吠。
- **英文写法**：`cut to a 5-second empty shot, only a curtain moving in the wind, the character already gone, no score, only wind and a distant dog`

## 2. 垂直构图与卷轴式横移

- **不是**"东方美学构图"，**而是**：借山水立轴的**上下经营**（前景近石 → 中景人 → 远景山，三层沿画面竖直排列），或借长卷的**匀速横移**（摄影机以恒定速度横移 8–15s，景物如卷轴般依次展开，不停顿不加速）。
- 参数化：`三层纵向堆叠构图 + 长焦 85–135mm 压缩层次`，或 `恒速横移 8–15s，速度不变、不推不拉`
- **中文写法**：前景山石剪影、中景独行者、远景云雾山峦沿垂直方向三层堆叠，85mm 长焦压缩；或摄影机以恒定速度横移十二秒，如展开长卷。
- **英文写法**：`three layers stacked vertically — foreground rock silhouette, mid-ground lone figure, distant misty peaks — compressed with an 85mm lens` / `a perfectly constant lateral track for 12 seconds, unrolling the landscape like a hand scroll, no acceleration and no zoom`

## 3. 自然物（雨/雪/花/风）作为情绪载体

- **不是**"充满诗意"，**而是**：把人物**不表演**的情绪外包给一个自然元素——人物面无表情静止，由雨/雪/落花/风来"演"这场戏；该元素必须被**逆光点亮**才可见。
- 参数化：`人物静止面无表情 + 一个持续运动的自然元素（雨丝/雪片/落花/吹动的衣袍）+ 硬逆光使其可见 + 光比 ≥6:1 + 无配乐`
- **中文写法**：人物静止不动、面无表情，只有漫天落花在强逆光中被点亮并持续飘过前景，光比 6:1，无配乐只有风声。
- **英文写法**：`the character stands completely still with a blank expression while falling petals, lit by hard backlight, drift continuously across the foreground, 6:1 contrast, no score, only wind`

---

## 与本技能其他文件的关系

- 欧美导演锚点：`references/director-anchors-western.md`
- 摄影指导（含李屏宾、杜可风、Roger Deakins 等）：`references/dp-cinematographer-anchors.md`
- 动作/打斗场景的**镜长节奏与景别调度**：`references/genre/action-wuxia.md`（本文件负责"风格"，那份负责"剪辑数学"）。徐克、胡金铨、程小东、袁和平四条与该文件配套使用：先用那份定节奏曲线，再用本册挑风格锚点填色彩/光影/质感。

## 🔧 转译三原则（与欧美册一致）

1. **拆参数优先于报人名**：先写 `locked-off wide, cold blue night, 8:1 single-side key`，再在句尾加 `in the style of Johnnie To's standoffs`。
2. **一个维度只服从一位导演**：色彩听 A 的，运镜听 B 的，不要两个人抢同一个维度。
3. **最多取 3 个特征**：超过 3 个，模型开始平均化，风格反而消失。

