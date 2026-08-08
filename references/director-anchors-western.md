# 欧美导演风格锚点库 · Western Director Style Anchors

> 用途：把"我想要某某导演那种感觉"翻译成**可执行的镜头参数**，写进 MiniMax H3 提示词。
> 铁律一：**只写导演名字是无效的**（模型对人名的理解不稳定）。必须拆成"镜长 + 景别 + 运镜 + 色温 + 光位 + 质感"这些可执行词，导演名最多作为附加锚点放在风格句尾。
> 铁律二：**一切拆成可执行参数**——给 ASL 秒数区间、色温开尔文、焦段 mm、光比、fps、画幅比。禁写"很有电影感""氛围感强"。
> 铁律三：每位导演只取 **2–3 个最具辨识度的特征**叠加，超过 3 个会互相打架。
>
> 📎 亚洲导演见 `director-anchors-asian.md`；摄影指导见 `dp-cinematographer-anchors.md`。

---

## 使用方式（三步）

1. 从下表选定 1 位主导演做**主锚点**，最多再借 1 位做**副锚点**（副锚点只借一个维度，如"借他的色彩"）。
2. 把该导演的「可执行参数」整行抄进提示词的镜头/光影/色彩描述里。
3. 把「锚点句（中/英）」贴到风格句尾，**放在最后**，不要放开头。

---

# 一、电影 · 作者性导演

## 1. 斯坦利·库布里克 Stanley Kubrick — 对称·冷峻·缓慢逼近

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 一点透视（one-point perspective）、绝对居中、走廊/长桌纵深消失点 | `one-point perspective, subject dead center, corridor vanishing point` |
| 运镜 | 斯坦尼康低机位跟随（《闪灵》）、缓慢后退拉出、极慢推进 | `low-angle steadicam follow at knee height, slow dolly back` |
| 节奏 | 极慢，ASL 8–20s，长镜头堆压迫感，反类型片剪辑 | 单镜到底，不分段；若分段每段 ≥4s |
| 升降格 | 几乎不用升格；靠**镜头时长**而非慢动作制造凝滞 | 禁写 slow motion |
| 色彩 | 高饱和三原色块（红厕所、蓝夜、白诊室），大面积单色墙 | `saturated single-color wall (blood red / clinical white)` |
| 光影 | 实用光源入镜（practical lights）、《巴里·林登》全烛光（Zeiss 50mm f/0.7，约 1800K）、均匀高调白光 | `visible practical light fixtures in frame, candlelit only at 1800K, flat high-key white` |
| 胶片/画幅 | 35mm，1.66:1 / 1.85:1，超广角 18mm 制造空间畸变 | `18mm wide angle, shot on 35mm film, 1.85:1` |
| 音乐 | 古典乐反差配置（《蓝色多瑙河》配太空、《雨中曲》配暴行）、György Ligeti 不和谐人声 | `classical waltz over violent imagery, dissonant choral drone` |
| 表现手法 | "库布里克凝视"（低头抬眼直视镜头）、对称仪式感、人变成建筑的一部分 | `Kubrick stare: head tilted down, eyes up into lens` |
| 招牌镜头 | 走廊推轨 / 浴室对称 / 会议长桌顶光 / 婴儿脸大特写 |
| 代表作 | 《2001太空漫游》《闪灵》《发条橙》《全金属外壳》《巴里·林登》 |

**锚点句（中）**：绝对对称一点透视构图，超广角低机位缓慢推进，实用光源入镜，高饱和单色墙面，库布里克式冷峻凝视。
**锚点句（英）**：`symmetrical one-point perspective, 18mm wide low-angle slow dolly-in, in-frame practical lights, saturated monochrome walls, shot on 35mm 1.85:1, Kubrick-style cold detachment`

**⚠️ 不要与之叠加**：快切（他的一切建立在长镜头上）、手持晃动、暖黄柔光、浅景深虚化。

---

## 2. 克里斯托弗·诺兰 Christopher Nolan — 实拍·大画幅·交叉剪辑

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 大画幅满构图、人物置于巨大实景中显渺小、极少空镜 | `IMAX-scale composition, human figure dwarfed by practical set` |
| 运镜 | 稳定器/车载实拍跟拍、手持但克制、俯冲航拍、旋转走廊（机械装置实拍） | `handheld but stabilized tracking, rotating corridor practical rig` |
| 节奏 | 交叉剪辑三条时间线并行加速（《敦刻尔克》一周/一天/一小时），ASL 2–4s，越接近高潮切换越密 | 分段时**多线并行**：A线/B线交替，段长逐段缩短 |
| 升降格 | 关键节点用 1/4–1/8 升格（面包车坠河、走廊翻转），**慢动作只给"物理事件"不给情绪** | `1/4 speed ramp on the physical collision only` |
| 色彩 | 低饱和冷蓝灰 + 钢青（约 5600–6500K 偏冷），几乎不做风格化调色 | `desaturated cool blue-grey at 6500K, naturalistic grade` |
| 光影 | 强调自然硬光、阴天顶光、实景灯，反对棚拍柔光；光比约 4:1–8:1 | `hard natural daylight, overcast top light, no studio softbox look` |
| 胶片/画幅 | IMAX 65mm / 70mm 大画幅，1.43:1 与 2.20:1 **段落间切换**，颗粒真实 | `shot on IMAX 65mm film, fine grain, 1.43:1 aspect switching` |
| 音乐 | Hans Zimmer / Ludwig Göransson，谢泼德音调（无限上升错觉）、滴答秒针、低频推进 | `Shepard tone rising infinitely, ticking clock pulse, sub-bass swell` |
| 表现手法 | 实拍优先（真炸真翻真旋转）、非线性时间结构、信息延迟揭示 | `all-practical effects, no CGI look` |
| 招牌镜头 | 走廊零重力打斗 / 城市折叠 / 逆行子弹 / 螺旋桨主观 |
| 代表作 | 《盗梦空间》《星际穿越》《敦刻尔克》《信条》《奥本海默》 |

**锚点句（中）**：IMAX 大画幅实拍质感，低饱和冷蓝灰，自然硬光，关键碰撞瞬间 1/4 升格，低频推进配乐。
**锚点句（英）**：`IMAX 65mm large-format practical realism, desaturated cool blue-grey 6500K, hard natural light 6:1 ratio, 1/4 speed ramp on impact, sub-bass driving score, 1.43:1`

**⚠️ 不要与之叠加**：高饱和风格化调色、卡通感、明显 CGI 词汇（`CGI`, `render`）、柔焦。

---

## 3. 韦斯·安德森 Wes Anderson — 对称·粉彩·平面调度

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 绝对中轴对称、平面化正面构图（planimetric，人物永远正对或正侧 90°） | `perfectly symmetrical frontal composition, planimetric staging, subject facing lens straight-on` |
| 运镜 | 90° 甩摇（whip pan）、横向平移轨道（像玩具屋剖面）、急速变焦（snap zoom）、顶视插入镜头 | `90-degree whip pan, lateral dollhouse tracking, snap zoom, overhead flat-lay insert` |
| 节奏 | 中速但**极规整**，ASL 3–5s 且每镜时长接近相等（唯一允许"等分"的风格），章节标题卡分段 | 允许等长镜头，配 `chapter title card` |
| 升降格 | 结尾群像慢走 1/2 升格 + 整曲配乐，标志性收尾 | `half-speed slow motion group walk in final shot` |
| 色彩 | 粉彩三色板（芥末黄 + 婴儿粉 + 薄荷绿 / 或 红白蓝），每部片一套固定色卡 | `pastel palette: mustard yellow, baby pink, mint green` |
| 光影 | 无影平光、正面均匀布光、光比 1.5:1 以下 | `flat frontal even lighting, 1.5:1 ratio, no harsh shadows` |
| 胶片/画幅 | 35mm 与定格动画混用；2.35:1 与 1.37:1 按时代切换；40mm 定焦为主；Futura / Archer 字体 | `35mm film, 40mm prime, 1.37:1 academy ratio, Futura typeface title card` |
| 音乐 | 英伦老摇滚点唱（The Kinks / Rolling Stones）+ 弦乐拨奏 Alexandre Desplat | `1960s British rock needle-drop, pizzicato strings` |
| 表现手法 | 面无表情式幽默（deadpan）、微缩模型、章节结构、道具正面平铺展示 | `deadpan expression, miniature model set, prop flat-lay` |
| 招牌镜头 | 中轴对称走廊 / 顶视桌面道具排列 / 横移剖面屋 / 群像正面排排站 |
| 代表作 | 《布达佩斯大饭店》《月升王国》《犬之岛》《法兰西特派》 |

**锚点句（中）**：绝对中轴对称正面构图，粉彩三色板，无影平光，90° 甩摇与横向平移，面无表情式幽默。
**锚点句（英）**：`perfectly centered symmetrical frontal framing, pastel three-color palette, flat shadowless lighting 1.5:1, 90-degree whip pan and lateral tracking, 40mm prime, 1.37:1, deadpan tone`

**⚠️ 不要与之叠加**：手持晃动、低照度暗部、写实纪录感、脏污质感。

---
## 4. 保罗·托马斯·安德森 Paul Thomas Anderson (PTA) — 穿行长镜·70mm·弦乐不安

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物贴近画面边缘、环境把人吞掉；大量中景走动构图，室内纵深穿门过厅 | `medium shot with the subject drifting toward frame edge, deep interior threading through doorways` |
| 运镜 | **持续推轨穿行长镜**（Steadicam/dolly 跟人穿过整栋建筑）、缓慢横移、偶尔失控般加速逼近 | `continuous steadicam走位: dolly follows the character through multiple rooms in one take` |
| 节奏 | 慢中带压，ASL 6–12s；一场戏常只切 2–3 刀，靠人物走位换景别 | 单镜 8–15s，中途换景别不换镜头 |
| 升降格 | 极少慢动作；只在"崩溃/顿悟"瞬间给 1/2 升格，其余靠镜头长度施压 | `1/2 speed only at the emotional break, otherwise real time` |
| 色彩 | 70 年代加州暖褐 + 芥末黄 + 干枯绿；肤色偏橙，阴影带绿 | `1970s California warm sepia-brown, mustard and dried-green accents, orange skin tones` |
| 光影 | 大面积柔和窗光 + 实用台灯；光比 3:1，暗部保留细节不压死 | `soft window key with practical table lamps, 3:1 ratio, open shadows` |
| 胶片/画幅 | 65mm/70mm（《大师》）或 35mm 仿旧；1.85:1 与 2.39:1；35mm–50mm 中焦为主，靠近人脸 | `shot on 70mm film, 40mm lens, 1.85:1, fine organic grain` |
| 音乐 | Jonny Greenwood：弦乐不协和刮奏、持续音渐强、突然抽走；音乐早于事件出现 | `Greenwood-style dissonant string scrape, sustained crescendo that cuts to silence` |
| 表现手法 | 长时间不切的表演压力、突然的情绪爆裂、家庭/权力的封闭系统 | `unbroken take holding on a rising emotional outburst` |
| 招牌镜头 | 穿越夜总会/片场的长镜 / 两人对坐审问 / 车内跟拍侧脸 / 房间尽头的人物剪影 |
| 代表作 | 《不羁夜》《血色将至》《大师》《魅影缝匠》 |

**锚点句（中）**：连续推轨穿行长镜头，人物走位穿过数个房间，70mm 暖褐加州色调，柔和窗光配实用台灯，弦乐不协和持续音渐强。
**锚点句（英）**：`continuous steadicam long take threading through multiple rooms, 1970s warm sepia-brown grade, soft window key with practical lamps at 3:1, shot on 70mm 40mm lens 1.85:1, dissonant sustained strings building underneath`

**⚠️ 不要与之叠加**：密集快切、冷蓝数字质感、对称构图、无配乐留白。

---

## 5. 丹尼斯·维伦纽瓦 Denis Villeneuve — 巨物剪影·雾霾橙·低频轰鸣

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **巨物 vs 蝼蚁**：人只占画面 1/10 以下，巨大几何体占满其余；极简空旷，负空间统治画面 | `monumental structure filling the frame, tiny human silhouette occupying under one-tenth of frame` |
| 运镜 | 极慢无声推进或缓降航拍；机器几乎不给情绪，冷静如仪器；直升机大俯拍揭示规模 | `imperceptibly slow push-in, high aerial descent revealing scale, clinical camera` |
| 节奏 | 极慢，ASL 6–12s；大量静默段落，事件之间留空 | 段长 ≥6s，事件间插 3s 空镜 |
| 升降格 | 罕用慢动作；用"慢速运镜 + 长镜"制造凝滞感，爆炸/坠落偶给 1/2 | `no slow motion; slowness comes from camera speed, 1/2 only on a collapse` |
| 色彩 | 雾霾橙（《银翼杀手2049》拉斯维加斯）、水泥灰、单色沙尘；同一场景只允许一个主色 | `sandstorm orange haze OR concrete grey monochrome, one dominant hue per scene` |
| 光影 | 大面积柔和顶光/雾中散射光，或单一强逆光造纯剪影；光比要么极低（雾）要么极高（剪影） | `diffused fog light with no visible source, or hard backlight creating pure black silhouette` |
| 胶片/画幅 | ARRI Alexa（与 Roger Deakins 合作）；2.39:1；长焦 75–135mm 压缩巨物 | `Alexa digital, 2.39:1, 100mm telephoto compressing the monolith` |
| 音乐 | Jóhann Jóhannsson / Hans Zimmer：**低频轰鸣 sub-bass drone**、金属摩擦声、次声压迫 | `oppressive sub-bass drone, metallic groan, almost infrasonic pressure` |
| 表现手法 | 信息克制、沉默胜台词、宗教式敬畏感、雾/沙/雨作为空间填充物 | `awe through silence and scale, fog and dust filling the volume` |
| 招牌镜头 | 沙尘暴中的巨型雕像 / 飞行器悬停于巨墙前 / 逆光走廊剪影 / 水面倒影全景 |
| 代表作 | 《银翼杀手2049》《沙丘》《降临》《边境杀手》 |

**锚点句（中）**：巨型建筑占满画幅、人物只剩极小剪影，雾霾橙单色调，雾中无源散射光或纯逆光剪影，长焦压缩，极慢无声推进，低频轰鸣。
**锚点句（英）**：`colossal monolith dominating the frame with a tiny human silhouette, sandstorm-orange monochrome haze, diffused sourceless fog light with hard backlit silhouettes, 100mm telephoto compression, imperceptibly slow push-in, 2.39:1, oppressive sub-bass drone`

**⚠️ 不要与之叠加**：快切、手持晃动、多彩色板、密集对白、暖金柔光。

---

## 6. 泰伦斯·马力克 Terrence Malick — 魔幻时刻·贴地游走·旁白呢喃

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 超广角贴地/贴身，天空占 2/3；人物常背对或走出画外，构图故意"不完整" | `ultra-wide low camera near the ground, sky filling two-thirds, subject drifting out of frame` |
| 运镜 | **持续游走的手持广角**：摄影机像第三个人绕着角色打转，永不停止，无固定机位 | `never-still handheld wide lens circling and drifting around the characters` |
| 节奏 | 印象派剪辑，ASL 2–4s 但镜头之间不讲因果，靠情绪串联；大量插入自然空镜 | 短镜串联，每 3 镜插 1 个自然空镜（麦浪/树冠/水面） |
| 升降格 | 轻微 3/4 升格用于风吹麦浪、手掠过草尖；不做戏剧性慢动作 | `subtle 3/4 speed on wind through wheat and a hand brushing grass` |
| 色彩 | 自然色不做重调；黄昏金橙（约 2800–3200K）+ 草绿 + 天蓝，肤色通透 | `natural unfiltered grade, golden-hour 3000K warmth against green fields and blue sky` |
| 光影 | **只用自然光，且几乎只拍 magic hour**（日出后/日落前 20–40 分钟）；逆光穿指缝、镜头炫光 | `magic hour natural light only, backlit through fingers, lens flare, no artificial fill` |
| 胶片/画幅 | 65mm 或 35mm；1.85:1 / 2.39:1；14–21mm 超广角为主 | `shot on 65mm, 16mm ultra-wide, 2.39:1` |
| 音乐 | 古典乐大段使用（Górecki、Wagner）+ 环境自然声；音乐盖过对白 | `full classical orchestral passage over natural ambience, dialogue buried` |
| 表现手法 | **画外旁白呢喃**（低语式提问，与画面不直接对应）、无常规叙事、自然神性 | `whispered inner-monologue voice-over unrelated to the visible action` |
| 招牌镜头 | 逆光穿过指缝 / 麦田中回望 / 仰拍树冠光斑 / 孩子在草地奔跑的背影 |
| 代表作 | 《生命之树》《天堂之日》《细细的红线》《通往仙境》 |

**锚点句（中）**：超广角贴地持续游走手持，黄昏魔幻时刻自然光逆光穿过指缝，天空占三分之二，轻微升格的风吹草浪，低语式画外独白。
**锚点句（英）**：`ultra-wide 16mm handheld drifting continuously at ground level, magic-hour natural backlight flaring through fingers, sky filling two-thirds of a 2.39:1 frame, subtle 3/4 speed on wind-blown grass, whispered voice-over`

**⚠️ 不要与之叠加**：棚拍布光、对称构图、锁死机位、强风格化调色、夜景低照度。

---

## 7. 阿方索·卡隆 Alfonso Cuarón — 超长手持一镜·65mm 黑白·全景声

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 宽画幅横向调度，主体常在中景，**重要事件发生在画面边缘或背景**；不给特写解释 | `wide frame, action unfolding in the background while the subject stays mid-ground` |
| 运镜 | **超长不间断镜头**：360° 横摇、跟随人物走过整条街、车内环绕；镜头自己决定看什么 | `unbroken long take, slow 180-degree pan following action across the street, no cuts` |
| 节奏 | 极慢，ASL 15–60s（部分段落单镜 4 分钟以上）；张力来自"不切" | 单镜 15s+，中途允许主体离开画面再回来 |
| 升降格 | 不用；一切实时发生，慢动作会破坏"真实时间"的核心 | 禁写 slow motion |
| 色彩 | 《罗马》纯黑白（数字 65mm）；彩色作品用低饱和自然色，天空常灰白过曝 | `high-resolution digital black and white, or desaturated natural grade with blown grey sky` |
| 光影 | 自然光 + 天光柔和大面积；室内靠窗；光比 2:1–4:1，暗部通透 | `available light, large soft window source, 3:1 ratio, open shadows` |
| 胶片/画幅 | Alexa 65 数字大画幅；2.39:1；21–35mm 广角保持深焦，全画面清晰 | `Alexa 65, 21mm wide, deep focus f/8, 2.39:1` |
| 音乐 | **常常没有配乐**；用杜比全景声的环境声定位（狗叫、飞机、街市在画外精确移动） | `no score; immersive spatial ambience with sounds moving off-screen` |
| 表现手法 | **水与雨**反复出现（洗地、海浪、暴雨）；日常动作被完整拍完不省略 | `water motif: wet floor reflections, rain, waves; mundane action shown in full duration` |
| 招牌镜头 | 洗地板水面倒影开场 / 海浪中的救援长镜 / 车内 360° 环绕 / 街头骚乱穿行 |
| 代表作 | 《罗马》《人类之子》《地心引力》 |

**锚点句（中）**：超长不间断手持一镜，缓慢 180° 横摇跟随，65mm 数字黑白，自然窗光深焦，水面反射，无配乐只有环绕环境声。
**锚点句（英）**：`unbroken long take with a slow 180-degree pan following the action, Alexa 65 digital black and white, available window light at 3:1 with deep focus f/8, wet reflective floor, no score with immersive off-screen ambience, 2.39:1`

**⚠️ 不要与之叠加**：快切、慢动作、强风格化调色、密集配乐、浅景深虚化背景。

---

## 8. 达米恩·查泽雷 Damien Chazelle — 音乐驱动剪辑·鼓点对齐·单色追光

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 乐器/手/嘴/汗的极端特写 与 舞台全景交替；人物被追光从黑暗中切出来 | `extreme close-up of hands on the instrument intercut with a full stage wide, spotlit figure carved out of black` |
| 运镜 | 围绕表演者的 360° 环绕推轨、跟随舞步的连续横移、突然的甩镜 | `360-degree orbit dolly around the performer, lateral tracking with the dance, whip pan on the accent` |
| 节奏 | **剪辑点严格对齐鼓点/重拍**；高潮段 ASL 0.3–0.8s（鼓戏），叙事段 ASL 3–5s | 剪点＝节拍点；高潮 0.3–0.8s 一刀，抒情段 4s |
| 升降格 | 极少；偶尔在腾空/旋转顶点给 1/2 升格再弹回实速 | `1/2 speed at the top of the leap, snapping back to real time on the downbeat` |
| 色彩 | 高饱和单色追光（品红/宝蓝/翠绿）打在黑背景上；或 CinemaScope 洛杉矶黄昏紫橙 | `saturated single-color spotlight (magenta / royal blue) against pure black, or purple-orange LA dusk` |
| 光影 | 极高光比（10:1 以上）舞台追光；面部只亮一半，汗珠反光 | `hard theatrical spotlight, 10:1 ratio, half-lit sweating face` |
| 胶片/画幅 | 35mm CinemaScope 2.55:1（《爱乐之城》）或 2.39:1；长焦压缩舞台 | `shot on 35mm CinemaScope 2.55:1, 85mm telephoto` |
| 音乐 | **音乐先于画面存在**，整段按曲谱分镜；爵士鼓 solo / 大乐队 / 百老汇编曲 | `edit locked to a jazz drum solo, every cut lands on a snare hit` |
| 表现手法 | 旋转舞台/旋转房间、汗与血、追求完美的自毁、一镜歌舞段落 | `rotating stage, blood on the drum kit, one-take musical number` |
| 招牌镜头 | 鼓槌血迹特写 / 追光下的独舞 / 黄昏天文台旋转升空 / 环绕钢琴 360° |
| 代表作 | 《爆裂鼓手》《爱乐之城》《巴比伦》 |

**锚点句（中）**：剪辑点严格对齐鼓点，围绕表演者 360° 环绕推轨，纯黑背景上的高饱和单色追光，10:1 极高光比，腾空顶点 1/2 升格弹回实速。
**锚点句（英）**：`every cut landing exactly on the drum hit, 360-degree orbit dolly around the performer, saturated magenta spotlight against pure black at 10:1 ratio, 85mm on 35mm CinemaScope 2.55:1, 1/2 speed at the peak of the leap snapping back on the downbeat`

**⚠️ 不要与之叠加**：无配乐留白、纪录式手持、平光、慢节奏长镜。

---
# 二、电影 · 类型片大师

## 9. 昆汀·塔伦蒂诺 Quentin Tarantino — 后备箱仰拍·脚部特写·对峙三角

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **后备箱视角**（trunk shot：从箱底仰拍两三人俯视镜头）、**墨西哥对峙三角**（三人互相持枪的三角站位）、脚部特写作为出场式 | `trunk shot: low box-level POV looking up at two men peering down; Mexican standoff triangle; feet-first character intro` |
| 运镜 | 长对白戏用缓慢环绕推轨；暴力前用**急速变焦推（snap zoom）**；桌下/椅下低机位穿行 | `slow orbiting dolly during dialogue, sudden snap zoom before violence, under-table low tracking` |
| 节奏 | **两极分化**：对白段 ASL 8–20s（几乎不切），爆发段 ASL 0.5–1.5s | 对白单镜 10s+，暴力段 0.5–1s 密集切 |
| 升降格 | 极少慢动作；仅用于"角色慢走登场"（1/2 升格配点唱歌曲） | `1/2 speed hero walk-in synced to a needle-drop track` |
| 色彩 | 70 年代剥削片调：暖橙红 + 深褐 + 高饱和血红；黄色字幕卡 | `1970s grindhouse warm orange-red, deep brown, hyper-saturated blood red, yellow title card` |
| 光影 | 室内实用光 + 硬顶光；夜戏偏暖钠黄（约 2700K）；光比 4:1 | `hard practical top light, 2700K sodium interior, 4:1 ratio` |
| 胶片/画幅 | 35mm（部分 70mm Ultra Panavision 2.76:1）；**明显胶片颗粒、划痕、跳帧**；2.35:1 | `shot on 35mm with heavy grain and reel-change cue marks, 2.35:1` |
| 音乐 | **点唱式配乐（needle-drop）**：老 soul / 意大利西部片配乐 / 冲浪摇滚，与画面情绪故意错位 | `surf-rock needle-drop over a violent scene, spaghetti-western cue` |
| 表现手法 | 章节标题卡、非线性时序、长段闲聊对白、突然的极端暴力、致敬式画面引用 | `chapter title card, sudden extreme violence after long banter` |
| 招牌镜头 | 后备箱仰拍 / 三人对峙环绕 / 脚部特写 / 血溅白墙 |
| 代表作 | 《低俗小说》《落水狗》《无耻混蛋》《被解救的姜戈》《杀死比尔》 |

**锚点句（中）**：后备箱底部仰拍两人俯视镜头，墨西哥三角对峙，70 年代剥削片暖橙红高颗粒 35mm 质感，暴力前急速变焦推，冲浪摇滚点唱配乐。
**锚点句（英）**：`trunk shot from inside the boot looking up at two men, Mexican standoff triangle blocking, 1970s grindhouse warm orange-red with heavy 35mm grain 2.35:1, snap zoom before the violence, surf-rock needle-drop`

**⚠️ 不要与之叠加**：冷蓝数字干净质感、极简留白、无声环境、对称粉彩。

---
## 10. 科恩兄弟 Coen Brothers — 广角低机位·荒诞对称·冷幽默静止

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 广角低机位仰拍（把普通人拍成雕像）、荒诞对称、大量正面直视；人物被空旷环境包围显得可笑 | `18mm low-angle looking up at an ordinary man, absurdly symmetrical framing, subject swallowed by empty landscape` |
| 运镜 | 贴地推轨极速前冲（"科恩推轨"）、锁死静止长镜、缓慢升起俯拍 | `fast low dolly rushing along the ground, otherwise locked-off static frames` |
| 节奏 | 慢-静-荒诞，ASL 4–8s；笑点靠"多停 1 秒"制造尴尬 | 每个笑点镜尾多留 1s 静止 |
| 升降格 | 几乎不用；用静止和停顿代替 | 禁写 slow motion，改写 `hold the static frame one beat too long` |
| 色彩 | 两套极端：雪原白 + 褐色大衣（《冰血暴》）／ 沙漠土黄 + 血褐（《老无所依》） | `snow-white expanse with brown coats, or dust-yellow desert with dried-blood brown` |
| 光影 | 平淡自然光刻意"不美化"；室内荧光顶光泛绿；雪地反射打亮下巴 | `flat unflattering daylight, greenish fluorescent interior top light, snow bounce under the chin` |
| 胶片/画幅 | 35mm（长期搭档 Roger Deakins）；1.85:1 / 2.39:1；14–24mm 广角为主 | `shot on 35mm, 21mm wide, 1.85:1` |
| 音乐 | Carter Burwell：极简民谣旋律、单一乐器反复；大量段落无配乐只留风声 | `sparse folk motif on a single instrument, long stretches with only wind` |
| 表现手法 | 命运的荒诞、暴力发生得毫无仪式感（突然、笨拙、真实）、方言口音喜剧 | `violence that happens abruptly and clumsily, no dramatic build-up` |
| 招牌镜头 | 雪原中的小人影 / 广角仰拍谈判 / 静止长镜里的尴尬沉默 / 血溅在白雪上 |
| 代表作 | 《冰血暴》《老无所依》《谋杀绿脚趾》《严肃的男人》 |

**锚点句（中）**：18mm 广角低机位仰拍普通人，荒诞对称构图，雪原白配褐色，平淡不美化的自然光，锁死静止长镜并在笑点后多停一拍。
**锚点句（英）**：`21mm wide low-angle looking up at an ordinary man, absurdly symmetrical framing, snow-white and brown palette, flat unflattering natural light, locked-off static frame held one beat too long, shot on 35mm 1.85:1`

**⚠️ 不要与之叠加**：华丽运镜、高饱和霓虹、密集配乐、浅景深柔美。

---

## 11. 乔治·米勒 George Miller — 中心构图追车·抽帧加速·饱和橙蓝

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **"眼睛永远在画面正中"**（crosshair framing）：无论怎么切，主体视觉焦点始终锁在正中央，让观众在极速剪辑中不迷失 | `crosshair framing: the subject's eyes stay dead center of frame in every single shot` |
| 运镜 | 车载 pursuit rig 并行跟拍、车头/车尾硬架机位、横向穿越车队、镜头随撞击弹跳 | `vehicle-mounted parallel tracking at speed, hard-mounted hood cam, camera jolted by impact` |
| 节奏 | 极快但可读，ASL 0.8–2s；因为中心构图所以快切不晕 | 0.8–2s 一刀，每刀主体都在正中 |
| 升降格 | **抽帧加速（undercranking，以 18–22fps 拍摄后正常播放）**制造癫狂加速感；关键腾空给 1/2 升格 | `undercranked at 20fps for frantic speed-up, 1/2 speed ramp at the peak of the jump` |
| 色彩 | 极端饱和橙沙漠 + 电蓝夜（数字重调，故意不写实） | `hyper-saturated orange desert day and electric teal-blue night, deliberately unnatural grade` |
| 光影 | 正午顶光暴晒，硬阴影；夜戏蓝调月光；光比 8:1 | `blazing noon top light with hard shadows, 8:1 ratio, blue moonlight nights` |
| 胶片/画幅 | 数字（Alexa/RED）；2.39:1；广角 21–35mm 贴近车体 | `24mm close to the vehicle body, 2.39:1` |
| 音乐 | Junkie XL：军鼓与低音提琴狂奏、失真吉他、打击乐持续推进 | `pounding percussion with distorted guitar, relentless driving rhythm` |
| 表现手法 | **真实车辆特技与实体爆炸**、怪诞角色设计、几乎无对白靠动作叙事 | `real vehicle stunts and practical explosions, near-wordless action storytelling` |
| 招牌镜头 | 沙暴中的车队 / 杆上摇摆的战士 / 车顶对打 / 正面对冲 |
| 代表作 | 《疯狂的麦克斯：狂暴之路》《疯狂的麦克斯2》《幸福路上》 |

**锚点句（中）**：主体眼睛永远锁在画面正中的中心构图，车载并行高速跟拍，极端饱和橙色沙漠与电蓝夜，20fps 抽帧加速，实体爆炸与真实车辆特技。
**锚点句（英）**：`crosshair framing with the subject's eyes dead center in every shot, vehicle-mounted parallel tracking at speed, hyper-saturated orange desert against electric teal night, undercranked 20fps frantic speed-up, practical explosions, 24mm, 2.39:1`

**⚠️ 不要与之叠加**：静止长镜、去饱和灰调、柔光、留白极简。

---
## 12. 迈克尔·贝 Michael Bay — 360° 环绕·逆光光晕·英雄仰角

> ⚠️ **滥用风险最高的一位**。这套语言极易变成"廉价预告片感"：一旦同时叠加环绕 + 光晕 + 慢镜 + 金黄夕阳，输出会立刻沦为汽车广告套路。**建议只取 1 个特征**（通常是"低机位英雄仰角"或"逆光光晕"），其余维度交给别的导演。

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 低机位英雄仰角（相机贴地 30cm 仰拍人物走来）、人物永远在画面黄金分割且顶天立地 | `camera 30cm off the ground looking up at the hero walking toward lens, low heroic angle` |
| 运镜 | **360° 环绕推轨（Bay-hem orbit）**：绕着站立人物快速转一整圈；直升机贴地掠过；急速推入 | `fast 360-degree orbit around the standing hero, low helicopter fly-by, aggressive push-in` |
| 节奏 | 极快，ASL 1–2s；几乎不给静止镜头 | 1–2s 一刀，禁止超过 3s 的镜头 |
| 升降格 | **英雄时刻 1/2 升格**（转身、戴墨镜、爆炸背后走出）；升格镜与实速镜密集交替 | `1/2 speed hero turn walking away from the explosion` |
| 色彩 | 金黄夕阳（约 2500–3000K）+ 青蓝阴影的极端 teal & orange 分离 | `extreme teal-and-orange split: 2800K golden sunset highlights against cyan shadows` |
| 光影 | **强逆光 + 镜头光晕（anamorphic lens flare 水平蓝条）**；背光轮廓打亮发丝与尘埃 | `hard backlight with horizontal anamorphic lens flare, rim-lit dust in the air` |
| 胶片/画幅 | 变形宽银幕 anamorphic 2.39:1；35mm 或数字；广角贴近 + 长焦压缩交替 | `anamorphic 2.39:1, 28mm close-up alternating with 135mm compression` |
| 音乐 | 军鼓+铜管的爱国式推进、电子低频；每个剪辑重音都有音效撞击 | `military snare and brass swell, audio hit on every cut` |
| 表现手法 | 实体爆炸（真火真爆）、军事装备崇拜、旗帜/夕阳/尘土三件套 | `real fireball explosions, flag and dust and sunset` |
| 招牌镜头 | 爆炸前慢镜走出 / 环绕仰拍集结 / 夕阳剪影列队 / 直升机逆光掠过 |
| 代表作 | 《变形金刚》《绝世天劫》《勇闯夺命岛》《危机13小时》 |

**锚点句（中）**：贴地 30cm 低机位英雄仰角，快速 360° 环绕，强逆光水平变形镜头光晕，金黄夕阳配青蓝阴影，英雄转身 1/2 升格。
**锚点句（英）**：`low heroic angle 30cm off the ground, fast 360-degree orbit around the hero, hard backlight with horizontal anamorphic flare, 2800K golden sunset against cyan shadows, 1/2 speed hero turn, anamorphic 2.39:1`

**⚠️ 不要与之叠加**：极简留白、静止长镜、去饱和自然主义、柔和平光、文艺慢节奏。**且本条自身四个特征不要全上，最多取两个。**

---

## 13. 詹姆斯·卡梅隆 James Cameron — 水下实拍·蓝绿冷调·规模揭示三段式

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **规模揭示三段式**：先给局部细节特写 → 拉开到中景显示所处位置 → 再拉到全景揭示真正体量 | `three-beat scale reveal: detail close-up, pull back to mid, then wide revealing the true colossal scale` |
| 运镜 | 缓慢后拉揭示、水下环绕漂移、跟随下潜的垂直运动、机械臂精确轨迹 | `slow pull-back reveal, underwater orbital drift, vertical descent follow` |
| 节奏 | 中速，ASL 2.5–4.5s；动作段 1–2s；规模揭示镜留足 4–6s | 揭示镜 ≥4s，动作段 1–2s |
| 升降格 | 水下动作天然带 1/2 慢感；爆破/坠落给 1/2–1/4 升格 | `1/2 speed on the underwater impact and debris` |
| 色彩 | 蓝绿冷调（水下 5000–7000K 偏青）+ 橙色警示灯/焊花做对比点 | `cyan-green underwater grade at 6500K punctuated by orange warning lights` |
| 光影 | 水下强指向光束（潜水灯/探照灯穿过悬浮颗粒）、体积光；光比 6:1 | `hard underwater beam light cutting through suspended particles, volumetric shafts` |
| 胶片/画幅 | 数字 3D 立体拍摄 / 35mm；2.39:1；广角 18–24mm 贴近大机械 | `24mm wide close to massive machinery, 2.39:1, stereoscopic depth` |
| 音乐 | James Horner / Simon Franglen：合成器与人声吟唱、民族笛、巨大铜管揭示动机 | `ethereal wordless vocal over synth pad, huge brass motif on the reveal` |
| 表现手法 | **大机械与人体的尺度对比**（外骨骼、潜水器、飞船）、真实水下拍摄、工程细节可信 | `human body dwarfed by functional heavy machinery, real underwater photography` |
| 招牌镜头 | 潜水器灯光扫过残骸 / 外骨骼与人对峙 / 巨轮下沉全景 / 水面破出 |
| 代表作 | 《泰坦尼克号》《阿凡达》《深渊》《终结者2》《异形2》 |

**锚点句（中）**：三段式规模揭示（细节特写→中景→全景巨物），水下实拍蓝绿冷调，探照灯光束穿过悬浮颗粒的体积光，大机械与人体尺度对比。
**锚点句（英）**：`three-beat scale reveal from detail close-up pulling back to a colossal wide, cyan-green underwater grade at 6500K with orange warning lights, hard beam light through suspended particles, human dwarfed by heavy machinery, 24mm 2.39:1`

**⚠️ 不要与之叠加**：手持纪录晃动、暖褐复古颗粒、快切、极简空景。

---
## 14. 乔丹·皮尔 Jordan Peele — 正面凝视·日光恐怖·缓慢推脸

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **正面凝视镜头**：角色正对镜头中心、微微仰头、不眨眼；对称构图 + 单人居中 | `subject facing the lens dead center, unblinking direct gaze into camera` |
| 运镜 | **极缓慢推向面部**（30s 内只推进一点点）、锁死静止、偶尔缓慢横移揭示背景里的异常 | `imperceptible slow push toward the face, locked-off static, slow pan revealing something wrong in the background` |
| 节奏 | 慢，ASL 5–9s；恐惧来自"镜头不肯切开" | 单镜 6s+，异常出现后再多停 2s |
| 升降格 | 罕用；关键"下沉"时刻用 1/2 升格 + 后拉（沉入虚空的错位感） | `1/2 speed with a simultaneous slow pull-back at the moment of dissociation` |
| 色彩 | **明亮日光下的恐怖**：自然日光、草坪绿、白墙、粉蓝天；恐怖不靠黑暗 | `bright natural daylight, green lawn and white suburban walls, horror in full sun` |
| 光影 | 大面积柔和日光，光比 2:1；刻意不给阴影藏东西——威胁是可见的 | `soft even daylight at 2:1, nothing hidden in shadow, the threat is fully lit` |
| 胶片/画幅 | 35mm 或数字仿胶片；2.39:1；40–50mm 接近人眼视角，推近时不畸变 | `shot on 35mm, 40mm lens, 2.39:1` |
| 音乐 | Michael Abels：斯瓦希里语人声吟唱、扭曲的民谣、弦乐尖锐持续音；也常用欢快老歌反讽 | `distorted choral chanting in an African language, or an upbeat oldies track played ironically` |
| 表现手法 | **不安的静止**（人站着一动不动地笑）、社会隐喻、日常场景的微小错位 | `a person standing perfectly still, smiling and not moving, uncanny stillness` |
| 招牌镜头 | 泪流满面却直视镜头 / 草坪上远处静止的身影 / 缓推入眼睛 / 全家福式对称站位 |
| 代表作 | 《逃出绝命镇》《我们》《不》 |

**锚点句（中）**：角色正对镜头中心不眨眼凝视，极缓慢推向面部，明亮自然日光下的恐怖，草坪绿与白墙，远景中一个一动不动的身影。
**锚点句（英）**：`subject staring unblinking directly into the lens dead center, imperceptibly slow push toward the face, bright even daylight at 2:1 with green lawn and white suburban walls, a motionless figure standing far in the background, 40mm 2.39:1`

**⚠️ 不要与之叠加**：低照度暗调、手持晃动、快切惊吓、浓雾。

---

## 15. 蒂姆·波顿 Tim Burton — 哥特螺旋·黑白紫·广角畸变

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 倾斜荷兰角、螺旋与条纹图案、尖顶歪斜建筑；人物瘦长被广角拉变形 | `dutch-angle tilt, spiral and stripe patterns, crooked pointed architecture, elongated distorted figure` |
| 运镜 | 缓慢螺旋上升/环绕、推轨穿过弯曲走廊、机械式规整移动 | `slow spiraling crane up, dolly through a warped corridor` |
| 节奏 | 中速，ASL 3–5s；奇观镜留 4–6s | 常规 3–5s，奇观揭示 5s |
| 升降格 | 定格动画段落本身即"非实时"；实拍偶用 3/4 升格给飘落物 | `stop-motion cadence, 3/4 speed on falling ash or leaves` |
| 色彩 | **高对比黑白 + 单点紫/毒绿/血红**；或整体去色只留一个饱和色 | `high-contrast black and white with a single saturated accent: violet, toxic green or blood red` |
| 光影 | 硬侧光造长影、月光冷蓝（约 7000K）、下巴打光造怪诞感；光比 8:1 以上 | `hard side light casting long shadows, 7000K moonlight, uplight from below, 8:1 ratio` |
| 胶片/画幅 | 35mm；1.85:1 / 2.39:1；14–21mm 超广角贴脸造畸变 | `18mm ultra-wide close to the face causing distortion, 1.85:1` |
| 音乐 | Danny Elfman：圆舞曲式木管、童声合唱、钟琴（celesta）、马戏团进行曲 | `Elfman-style waltzing woodwinds, children's choir, celesta and circus march` |
| 表现手法 | **定格动画质感**（关节顿挫感的动作）、大眼睛苍白角色、童话与死亡并置 | `stop-motion puppet texture, jerky articulated movement, pale big-eyed character` |
| 招牌镜头 | 螺旋山丘剪影 / 月下歪斜大门 / 条纹地板走廊 / 大眼特写 |
| 代表作 | 《剪刀手爱德华》《圣诞夜惊魂》《僵尸新娘》《蝙蝠侠归来》 |

**锚点句（中）**：荷兰角倾斜构图配螺旋与条纹图案，18mm 超广角贴脸畸变，高对比黑白只留一点毒紫，硬侧光长影配 7000K 冷月光，定格动画式顿挫动作。
**锚点句（英）**：`dutch-angle framing with spiral and stripe motifs, 18mm ultra-wide facial distortion, high-contrast black and white with a single violet accent, hard side light long shadows under 7000K moonlight at 8:1, stop-motion jerky puppet movement`

**⚠️ 不要与之叠加**：写实纪录感、自然柔光、低对比灰调、对称平光。

---

## 16. 吉尔莫·德尔·托罗 Guillermo del Toro — 青绿琥珀双色·机械与有机

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 满构图繁复美术，每个角落有细节；生物与人同框做尺度对比；圆形/拱形取景框 | `densely detailed production design filling every corner, arched doorway framing, creature and human in the same frame` |
| 运镜 | 缓慢横移穿过布景展示细节、环绕生物揭示全貌、俯视旋转 | `slow lateral track revealing the set detail, orbit around the creature` |
| 节奏 | 中慢，ASL 4–7s；给观众时间看美术 | 4–7s，奇观镜 6s+ |
| 升降格 | 3/4 微升格用于水中漂浮、羽毛/灰烬飘落 | `3/4 speed on floating in water and drifting ash` |
| 色彩 | **青绿（teal-green）与琥珀金（amber）双色系统**：环境冷青绿，人造光源暖琥珀，两者永不混合 | `strict two-tone system: teal-green environment lit by warm amber practical sources, never blended` |
| 光影 | **蜡烛/煤油灯暖光（2000–2400K）对撞窗外冷月光（7000K）**；体积光穿过灰尘 | `2200K candle warmth clashing with 7000K cold moonlight through the window, volumetric dust beams` |
| 胶片/画幅 | 35mm 或数字仿胶片；1.85:1 / 2.39:1；32–50mm 中焦保留美术纵深 | `shot on 35mm, 35mm lens, 1.85:1, deep production-design depth` |
| 音乐 | Alexandre Desplat / Javier Navarrete：手风琴、口哨童谣旋律、竖琴与弦乐圆舞曲 | `accordion and whistled lullaby melody, harp and string waltz` |
| 表现手法 | **机械与有机的混合**（齿轮长进血肉、发条心脏）、实体特效化妆、童话残酷性 | `mechanical gears fused into organic flesh, practical creature makeup, fairy-tale cruelty` |
| 招牌镜头 | 蜡烛照亮的生物脸部 / 水中漂浮 / 齿轮转动的机械装置 / 拱门下的小女孩 |
| 代表作 | 《潘神的迷宫》《水形物语》《地狱男爵2》《匹诺曹》 |

**锚点句（中）**：青绿环境与琥珀暖光双色系统，2200K 烛光对撞 7000K 冷月光，机械齿轮与有机血肉融合的生物，繁复美术满构图，缓慢横移展示细节。
**锚点句（英）**：`strict teal-green environment against warm amber practical light, 2200K candlelight clashing with 7000K moonlight, volumetric dust beams, mechanical gears fused into organic flesh, densely detailed set, slow lateral reveal, 35mm 1.85:1`

**⚠️ 不要与之叠加**：极简留白、单色去饱和、现代冷峻数字感、快切。

---
## 17. 大卫·林奇 David Lynch — 红帘幕·工业嗡鸣·诡异日常

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 红丝绒帘幕背景、黑白人字纹地板（zig-zag chevron）、正面对称舞台式构图；大特写占满画面 | `red velvet curtain backdrop, black-and-white zig-zag chevron floor, frontal stage-like symmetry` |
| 运镜 | **极慢变焦推进（slow zoom，非推轨）**、贴地缓慢前行、静止长镜；镜头运动带来生理不适 | `very slow optical zoom-in (not dolly), low creeping forward move, otherwise locked-off` |
| 节奏 | 极慢，ASL 8–15s；镜头停留远超"必要时长"，制造错误感 | 单镜 10s+，比"该切的时候"晚 3s 再切 |
| 升降格 | 少用慢动作；用"倒放 + 慢速"的诡异运动（人倒着说话再倒放） | `reversed-then-forward playback creating unnatural motion` |
| 色彩 | 红（帘幕/灯）与深黑对撞；日间段落刻意用 50 年代明快色（白栅栏、玫瑰）反衬 | `deep red against pure black, or artificially cheerful 1950s pastel suburbia` |
| 光影 | 单一实用光源（台灯/车灯/舞台灯）在纯黑中；闪烁的荧光灯；光比 12:1 以上 | `single practical lamp in total darkness, flickering fluorescent, 12:1 ratio` |
| 胶片/画幅 | 35mm；1.85:1 / 2.39:1；显著颗粒；数字作品刻意用低画质 DV 质感 | `shot on 35mm with visible grain, 1.85:1` |
| 音乐 | Angelo Badalamenti：慵懒爵士（贝斯 + 颤音吉他）；**持续工业低频嗡鸣（room tone drone）**贯穿全片 | `Badalamenti-style lounge jazz with tremolo guitar, over a constant industrial low-frequency hum` |
| 表现手法 | **诡异日常**：正常场景中一个元素错位（说话延迟、灯忽明忽暗、笑得太久）；梦境逻辑 | `an ordinary scene with one element wrong: delayed speech, a lamp flickering, a smile held too long` |
| 招牌镜头 | 红帘幕房间 / 公路夜行黄线 / 缓慢推入耳朵/物件 / 舞台上的歌手 |
| 代表作 | 《穆赫兰道》《双峰》《蓝丝绒》《妖夜慌踪》 |

**锚点句（中）**：红丝绒帘幕与黑白人字纹地板，纯黑中的单一实用光源，极慢光学变焦推进，工业低频嗡鸣持续贯穿，日常场景中一个元素明显错位。
**锚点句（英）**：`red velvet curtains and black-and-white chevron floor, a single practical lamp in total darkness at 12:1, very slow optical zoom-in, constant industrial low-frequency drone, one element of the ordinary scene subtly wrong, 35mm grain 1.85:1`

**⚠️ 不要与之叠加**：快切、明亮平光、手持纪录感、清晰因果叙事。

---

## 18. 马丁·斯科塞斯 Martin Scorsese — 长镜穿行·定格旁白·滚石点唱

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物在人群中穿行的跟拍中景、酒吧/餐厅的密集群像、突然的手部/物件插入特写 | `steadicam medium shot following a man threading through a crowded club, sudden insert of hands and objects` |
| 运镜 | **长镜穿行进入场所**（Copacabana 式：从后门穿过厨房走进大厅）、**推轨+变焦反向组合**、快速横摇扫过群像 | `unbroken steadicam entering through the back door, through the kitchen, into the main room; dolly-in combined with reverse zoom` |
| 节奏 | 双模式：长镜段 20–60s（一镜进场）与快切蒙太奇段 ASL 0.8–2s（旁白介绍人物） | 进场长镜 20s+；人物介绍蒙太奇 1s 一刀 |
| 升降格 | **快速定格（freeze frame）+ 旁白**介绍人物；偶尔 1/2 升格给暴力瞬间 | `sudden freeze frame holding on the face while the voice-over names him` |
| 色彩 | 饱和暖红（餐厅/夜店红灯）+ 深棕；70 年代柯达暖调，肤色偏橙 | `saturated warm red club lighting over deep brown, 1970s Kodak warmth` |
| 光影 | 实用光源为主（吊灯、霓虹、台灯），光比 5:1；夜店段落彩色光混合 | `practical chandeliers and neon as key, 5:1 ratio, mixed color club light` |
| 胶片/画幅 | 35mm；1.85:1；广角跟拍 + 长焦人群压缩交替 | `shot on 35mm, 27mm steadicam follow alternating with 85mm compression, 1.85:1` |
| 音乐 | **点唱式老摇滚**（The Rolling Stones、Phil Spector 制作的 60s 流行曲）；音乐与暴力并置 | `Rolling Stones needle-drop running over the entire sequence` |
| 表现手法 | 第一人称旁白解说规则与流程、天主教罪与罚、突然爆发的街头暴力 | `first-person voice-over explaining the rules of the world` |
| 招牌镜头 | 后门进夜总会一镜 / 定格+旁白介绍 / 推轨变焦（Vertigo effect）/ 俯拍尸体 |
| 代表作 | 《好家伙》《出租车司机》《赌城风云》《爱尔兰人》《华尔街之狼》 |

**锚点句（中）**：斯坦尼康长镜从后门穿过厨房进入大厅，饱和暖红实用光源，70 年代柯达暖调，快速定格配第一人称旁白，滚石老摇滚贯穿整段。
**锚点句（英）**：`unbroken steadicam entering through the back door and kitchen into a crowded club, saturated warm red practical lighting at 5:1, 1970s Kodak warm grade, sudden freeze frame with first-person voice-over, Rolling Stones needle-drop, 35mm 1.85:1`

**⚠️ 不要与之叠加**：冷蓝极简、静止锁死机位、无配乐留白、对称构图。

---
## 19. 史蒂文·斯皮尔伯格 Steven Spielberg — Spielberg Face·景深调度·dolly zoom

> ⭐ **本册对 AI 视频价值最高的一条，务必细读。**
> **Spielberg Face** = 人物仰头 + 一束光打在脸上 + 摄影机缓慢推入 + 表情从困惑转为敬畏。
> 它的核心机制是：**观众通过演员的脸"看见"了那个从未展示的奇观**。对 AI 视频生成而言这是降维打击——你不需要真的渲染出恐龙、飞船、洪水（AI 渲染大奇观极易穿帮），只需要拍一张被光照亮的、缓慢推近的、逐渐睁大眼睛的脸，观众自己会脑补出奇观。**遇到"预算不够/模型渲染不出的宏大场面"，一律改用这招。**

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **① Spielberg Face**：中景到近景，人物微微仰头 15–20°，视线投向画外上方；**② 一镜内前中后景信息调度**：同一画面里前景动作、中景主体、背景事件同时进行，用调度代替剪辑 | `medium close-up, head tilted up 15 degrees, eyes fixed on something above and outside the frame; simultaneous foreground, mid-ground and background action in one unbroken frame` |
| 运镜 | 缓慢推入（push-in）到脸；**dolly zoom**（推轨前进同时变焦拉远，背景膨胀而主体不变）；跟随人物穿行的连续调度长镜 | `slow dolly-in to the face; dolly zoom: track forward while zooming out so the background stretches; continuous staging long take` |
| 节奏 | 中速，ASL 3–6s；**反应镜头永远比奇观镜头长**（脸给 4–6s，奇观只给 1–2s 甚至不给） | 反应脸 4–6s，奇观一瞥 1–2s；不给奇观全景也成立 |
| 升降格 | 极少慢动作；靠推入速度和演员表情节奏控制时间感 | `no slow motion; the slow push-in does the work` |
| 色彩 | 两套：奇观片用暖金 + 天蓝（约 3200K 暖光源）；战争片用去饱和青灰 | `warm 3200K golden key against sky blue, or desaturated cyan-grey for war` |
| 光影 | **画外强光源打在脸上**（门缝溢光、飞船底光、手电、火光），发丝逆光 + 烟雾体积光；光比 6:1 | `hard off-screen light source hitting the face from above, hair backlight, volumetric haze, 6:1 ratio` |
| 胶片/画幅 | 35mm（长期搭档 Janusz Kamiński）；1.85:1 与 2.39:1；**战争片用约 45° 快门角 + 去饱和 + 漂白留银**质感 | `shot on 35mm, 1.85:1; for war: 45-degree shutter angle staccato motion, desaturated bleach-bypass` |
| 音乐 | John Williams：主题动机（leitmotif）在"脸"上升起，木管起弦乐接铜管；**音乐先于奇观出现** | `John Williams-style leitmotif rising on the reaction shot, woodwind into strings into brass` |
| 表现手法 | 通过反应而非展示叙事、儿童视角高度、家庭缺失母题、日常场景中降临的非凡 | `tell it through the reaction, never show the spectacle in full` |
| 招牌镜头 | 仰头被光照亮的脸 / dolly zoom 惊觉 / 门缝溢出的强光 / 水杯震动的涟漪（用小物件暗示巨物） |
| 代表作 | 《E.T.》《侏罗纪公园》《第三类接触》《拯救大兵瑞恩》《辛德勒的名单》 |

**锚点句（中）**：中景人物仰头 15°，一束画外强光从上方打亮面部，摄影机缓慢推入，表情由困惑转为敬畏，发丝逆光配烟雾体积光，约翰·威廉姆斯式主题动机随之升起——奇观本身不出现在画面里。
**锚点句（英）**：`medium close-up, head tilted up 15 degrees, hard off-screen light from above illuminating the face, slow dolly-in, expression shifting from confusion to awe, hair backlight with volumetric haze at 6:1, warm 3200K, the spectacle itself never shown, 35mm 1.85:1`

**锚点句（英 · dolly zoom 变体）**：`dolly zoom — camera tracks forward while the lens zooms out, background stretching and warping behind a fixed-size subject, sudden realization on the face, 35mm 2.39:1`

**锚点句（英 · 战争质感变体）**：`45-degree shutter angle staccato motion blur, desaturated bleach-bypass cyan-grey, handheld shaky camera with debris hitting the lens, 35mm`

**⚠️ 不要与之叠加**：冷酷疏离（他的核心是情感共鸣）、极端快切（推入需要时间）、暗部压死看不清脸、平光（脸上必须有明确光源）。

---
# 三、电视剧

## 20. 文斯·吉利根 Vince Gilligan — 广角物件视角·静默张力

（《绝命毒师》《风骚律师》主创，与常驻导演 Michelle MacLaren、摄影 Michael Slovis 共同确立的视觉体系）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **物件主观视角**（POV from inside a shovel / fridge / oil drum / 扫地机器人）、极端仰拍与俯拍、把人挤到画面边角 | `extreme wide-angle POV from inside an object looking up at the character` |
| 运镜 | 大量锁死静止机位（locked-off），运动时才是重音；缓慢俯仰摇 | `locked-off static frame, then a single slow tilt reveal` |
| 节奏 | **慢-静-爆**：长时间静默铺陈 → 突然暴力；冷开场（cold open）不解释、后回收 | 分段建议：静止段 3–5s + 爆发段 0.5s |
| 升降格 | 天空/云/影子延时摄影（time-lapse）做转场，几乎不用慢动作 | `time-lapse of clouds racing over desert as transition` |
| 色彩 | 新墨西哥黄沙滤镜（墨西哥段落强黄）、角色色彩编码（人物随堕落从米色→黑色） | `sun-baked desert yellow filter, color-coded costume progression` |
| 光影 | 硬顶光、正午无遮挡日晒、室内窗格光斑、深焦；光比 8:1 | `harsh noon sun, deep focus, hard window-slat shadows, 8:1 ratio` |
| 胶片/画幅 | 35mm 胶片拍摄（《绝命毒师》），16:9，超广角 14–21mm | `shot on 35mm, 16:9, 14mm ultra-wide` |
| 音乐 | 长段无配乐 + 环境声放大；突然插入吉他滑弦 / 墨西哥民谣（narcocorrido） | `no score, amplified ambient hum, sudden slide guitar sting` |
| 表现手法 | 象征物预示（粉色泰迪熊、蓝色晶体）、章节式冷开场、"上帝视角"俯拍宣判 | `symbolic object insert shot foreshadowing` |
| 招牌镜头 | 铲子坑底仰拍 / 车顶俯拍开门 / 桶内视角 / 沙漠天空延时 |
| 代表作 | 《绝命毒师》《风骚律师》 |

**锚点句（中）**：超广角物件内部主观视角仰拍，锁死静止机位，正午硬光深焦，沙漠黄调，长时间无配乐只留环境声。
**锚点句（英）**：`ultra-wide 14mm POV from inside an object looking up, locked-off static camera, harsh noon sun deep focus at 8:1, desert-yellow grade, no score with amplified ambience, shot on 35mm 16:9`

**⚠️ 不要与之叠加**：柔光美颜、连续运镜、密集配乐。

---

## 21. 大卫·芬奇 David Fincher — 精密·暗部·无摩擦运镜

（《纸牌屋》《心灵猎人》，电影《七宗罪》《社交网络》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 几何精确、水平垂直严格、人物置于负空间偏侧、对话用严格正反打 | `geometrically precise framing, strict horizon, subject offset in negative space` |
| 运镜 | **无摩擦感移动**：电脑控制的缓慢推轨、镜头像浮在轨道上；**绝不手持** | `imperceptibly slow motion-control dolly-in, absolutely no handheld` |
| 节奏 | 对白驱动的精确剪辑，ASL 3–5s，剪在语气停顿而非动作；不给观众喘息 | 分段按对白节拍，不按动作 |
| 升降格 | 极少；偶尔用极缓推进代替慢动作 | 禁写 slow motion，改写 `extremely slow push-in` |
| 色彩 | 病态黄绿（《七宗罪》《纸牌屋》）或青橙分离，**暗部压死到接近纯黑**，高光不过曝 | `sickly yellow-green grade, crushed blacks, protected highlights` |
| 光影 | 低照度、单一光源、光比 10:1 以上、面部半边入暗、顶光留眼窝阴影 | `single-source low-key lighting, 10:1 contrast ratio, half-face in shadow` |
| 胶片/画幅 | 全数字（RED / ARRI），2.39:1（剧集也用宽画幅），无颗粒极干净；40–75mm | `digital cinema clean image, 2.39:1, zero grain, 50mm` |
| 音乐 | Trent Reznor & Atticus Ross：合成器低鸣、脉冲电子、不给旋律给"不安" | `Reznor-style pulsing synth drone, no melody, unease` |
| 表现手法 | 隐形 VFX（数字修补、数字背景无痕）、大量重拍求精确、冷酷客观视角 | `invisible seamless VFX, clinical objective observation` |
| 招牌镜头 | 极缓推进到人脸 / 雨夜低照度街景 / 两人对坐权力构图 / 直视镜头打破第四面墙 |
| 代表作 | 《纸牌屋》《心灵猎人》《七宗罪》《社交网络》《消失的爱人》 |

**锚点句（中）**：几何精确构图，电脑控制的极缓推进，单光源低照度暗部压死，病态黄绿调，合成器低鸣。
**锚点句（英）**：`geometrically precise framing, imperceptibly slow motion-control push-in, single-source low-key with crushed blacks at 10:1, sickly yellow-green grade, clean digital 2.39:1, pulsing synth drone`

**⚠️ 不要与之叠加**：手持、快切、暖阳柔光、高饱和。

---

## 22. 米格尔·萨波奇尼克 Miguel Sapochnik — 混战主观·信息盲区

（《权力的游戏》"艰难堡""私生子之战""长夜"）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 把观众绑在**一个主角的视线高度**上，战场信息永远不完整；结尾才给全景解释 | `camera locked to one protagonist's eye level in chaos, withhold the wide shot until the end` |
| 运镜 | 手持跟随长镜头（oner）在人群中穿行、360° 环绕、突然被撞开偏移 | `handheld oner weaving through the melee, 360-degree orbit, camera jostled by passing bodies` |
| 节奏 | **窒息式递进**：先长镜头累积压迫（10s+）→ 短切爆发 → 停在静止喘息 | 长镜段 + 0.4–0.8s 爆发段 + 静止段 |
| 升降格 | 关键死亡/落马瞬间 1/3 升格，其余保持实速 | `1/3 speed only at the moment of the fatal blow` |
| 色彩 | 去饱和冷灰、泥血褐、雪白与暗蓝夜战 | `desaturated cold grey, mud-and-blood brown, blue-hour snow` |
| 光影 | 自然低照度（火把/月光唯一光源，约 1800K 火光）、剪影逆光、烟尘中的光柱 | `1800K firelight as only source, silhouettes against smoke, backlit dust beams` |
| 胶片/画幅 | ARRI 数字，2:1 / 1.78:1，长焦压缩人群 + 广角贴身交替 | `telephoto crowd compression intercut with 18mm in-your-face` |
| 音乐 | Ramin Djawadi：单一大提琴主题反复堆叠 → 全乐团；**关键时刻声音全部抽空** | `single cello ostinato building to full orchestra, then total sound dropout` |
| 表现手法 | 泥泞真实质感、群演真实碰撞、被踩踏的主观压迫、俯拍揭示合围 | `crane up to reveal encirclement, subjective trampling` |
| 招牌镜头 | 泥地中被踩踏起身 / 骑兵对冲长镜 / 尸墙俯拍 / 火焰剪影 |
| 代表作 | 《权力的游戏》战役集、《末日困兽》 |

**锚点句（中）**：手持贴身长镜头在混战中穿行，主角视线高度，去饱和冷灰泥血调，火光为唯一光源，致命一击时 1/3 升格并抽空声音。
**锚点句（英）**：`handheld oner weaving through chaotic melee at protagonist eye level, desaturated cold grey mud-and-blood grade, 1800K firelight as sole source, 1/3 speed ramp with full sound dropout at the fatal blow, 2:1`

**⚠️ 不要与之叠加**：对称构图、静止机位、明亮均匀布光。

---
## 23. 加里·福永 Cary Joji Fukunaga — 不间断长镜·斯坦尼康交接·实时紧张

（《真探》第一季"Who Goes There"六分钟长镜头；《无境之兽》《007：无暇赴死》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 主角背后跟随的过肩中景，观众与主角获得**完全相同的信息量**；空间在移动中自然揭示 | `over-the-shoulder follow at walking pace, the space revealing itself only as the character moves` |
| 运镜 | **单镜不间断穿越多个空间**：斯坦尼康跟人翻墙、穿房、下坡、上车；操作员之间隐形交接机器 | `unbroken steadicam take following the character over a fence, through a house, across a yard and into a car` |
| 节奏 | 单镜 60–360s（不切），紧张来自"没有剪辑点可以逃"；进入长镜前用短镜铺垫 | 一镜到底 ≥30s；前置 2–3 个 2s 短镜建立环境 |
| 升降格 | **绝不使用**——慢动作会摧毁"实时性"这个唯一卖点 | 禁写 slow motion，全程 real time |
| 色彩 | 路易斯安那潮湿绿褐、低饱和；夜戏靠钠黄路灯（2000K）与手电白光混合 | `humid Louisiana green-brown desaturated grade, 2000K sodium street light mixed with white torch` |
| 光影 | 现场可见光源为主（车灯、门廊灯、手电），随机器移动光比不断变化，允许瞬间过曝或欠曝 | `available practical light only, exposure shifting naturally as the camera moves, momentary clipping allowed` |
| 胶片/画幅 | 数字（Alexa）；1.78:1 / 2.39:1；广角 21–28mm 保证移动中不晕 | `Alexa digital, 24mm wide for stable movement, 1.78:1` |
| 音乐 | 长镜内**几乎无配乐**，靠呼吸声、脚步、枪声、犬吠定位空间 | `no score during the take, only breathing, footsteps, distant dogs and gunfire` |
| 表现手法 | 真实地理连续性（观众能画出平面图）、危险感来自"退不出去"、南方哥特氛围 | `unbroken spatial geography, no escape from the frame, southern gothic dread` |
| 招牌镜头 | 穿越街区的六分钟长镜 / 翻越围栏跟拍 / 车内一镜对话 |
| 代表作 | 《真探》第一季、《无境之兽》、《007：无暇赴死》 |

**锚点句（中）**：斯坦尼康过肩跟随的不间断长镜头，连续穿越围墙、房屋与院子，仅用现场可见光源且曝光随移动自然变化，潮湿绿褐低饱和，全程无配乐只有呼吸与脚步。
**锚点句（英）**：`unbroken steadicam over-the-shoulder long take following the character over a fence, through a house and into a car, available practical light only with exposure shifting naturally, humid desaturated green-brown grade, no score, only breathing and footsteps, 24mm 1.78:1, strictly real time`

**⚠️ 不要与之叠加**：慢动作、快切、棚拍布光、对称构图。

---

## 24. 约翰·雷克 Johan Renck — 去饱和灰绿·苏联工业·静默恐惧

（《切尔诺贝利》全 5 集导演；音乐录影带出身）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 人物被巨大工业结构/官僚空间压住；对称的会议室与走廊；中景为主，很少特写 | `figures dwarfed by brutalist industrial structures, symmetrical committee rooms, mostly medium shots` |
| 运镜 | 缓慢横移与极缓推进，机器冷静如旁观者；手持只用于混乱现场 | `slow lateral track and very slow push-in, dispassionate observer camera` |
| 节奏 | 慢，ASL 5–9s；恐惧靠"什么都没发生"的等待累积 | 5–9s，灾难信息用静止长镜承载 |
| 升降格 | 几乎不用；灰烬飘落用实速即可（像雪一样落下更可怕） | `no slow motion; falling ash at real speed` |
| 色彩 | **去饱和灰绿（desaturated grey-green）**：肤色发青、混凝土灰、军装橄榄绿；几乎无暖色 | `desaturated grey-green grade, sickly cyan skin tones, concrete grey and olive drab, almost no warm hues` |
| 光影 | 阴天散射柔光 + 室内荧光灯管（4000K 发绿）；光比 3:1，整体压暗不通透 | `overcast diffused daylight plus 4000K green fluorescent tubes, 3:1, generally underexposed` |
| 胶片/画幅 | 数字加**明显颗粒**模拟 80 年代苏联影像；2:1 / 1.78:1；35–50mm 中焦 | `digital with heavy added grain emulating 1980s Soviet footage, 2:1, 40mm` |
| 音乐 | Hildur Guðnadóttir：**用核电站实地录音做的音乐**（金属摩擦、蒸汽、嗡鸣），无旋律；大量剂量计咔哒声 | `musique-concrète drone built from industrial recordings, no melody, dosimeter clicking` |
| 表现手法 | 看不见的威胁（辐射）用声音与身体反应表现、官僚冷漠、纪实感群像 | `an invisible threat expressed only through sound and physical symptoms` |
| 招牌镜头 | 反应堆上空的电离蓝光 / 灰烬如雪飘落 / 屋顶清理兵 90 秒 / 会议室长桌 |
| 代表作 | 《切尔诺贝利》《太空堡垒卡拉狄加》《打破边界》 |

**锚点句（中）**：去饱和灰绿调与发青肤色，4000K 绿荧光灯管配阴天散射光，人物被粗野主义工业结构压住，明显颗粒模拟 80 年代苏联影像，无旋律的工业噪音配乐与剂量计咔哒声。
**锚点句（英）**：`desaturated grey-green grade with sickly cyan skin tones, 4000K green fluorescent tubes under overcast diffused light at 3:1, figures dwarfed by brutalist industrial structures, heavy grain emulating 1980s Soviet footage, melody-free industrial drone with dosimeter clicks, 40mm 2:1`

**⚠️ 不要与之叠加**：暖金色调、高饱和、英雄仰角、激昂配乐。

---

## 25. 让-马克·瓦雷 Jean-Marc Vallée — 0.2 秒碎片闪回·自然光手持·耳机音源

（《大小谎言》《利器》，电影《达拉斯买家俱乐部》《涉足荒野》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 松散的手持构图，允许失焦与不完美；大量透过门框/后视镜/玻璃的偷窥式取景 | `loose handheld framing, imperfect focus, shooting through doorframes, mirrors and glass` |
| 运镜 | 手持轻微漂移、跟随日常动作、不打灯不铺轨；像纪录片摄影师在房间里 | `light handheld drift following mundane action, documentary presence` |
| 节奏 | 主线 ASL 3–5s，中间**随机插入 0.2–0.5s 的记忆碎片**（一个眼神、一片水面、一只手），不做转场标记 | 主线 3–5s；每 15–20s 插 1–3 个 0.2–0.5s 闪回单帧 |
| 升降格 | 不用；闪回靠"极短"而非"慢速"起作用 | `no slow motion; flashbacks work by being brutally short` |
| 色彩 | 自然色轻调，加州阳光暖白 / 密苏里闷热青；肤色真实带瑕疵 | `naturalistic grade, warm California white daylight or humid cyan Missouri` |
| 光影 | **只用自然光与现场灯**，窗光为主，逆光允许过曝糊掉；光比 2:1–4:1 | `natural window light only, backlight allowed to blow out, 2.5:1` |
| 胶片/画幅 | 数字手持；1.78:1 / 2:1；35mm 左右中焦，浅景深 | `handheld digital, 35mm lens, shallow depth, 1.78:1` |
| 音乐 | **配乐全部是"来源音乐"（diegetic）**：角色耳机、车载音响、房间音箱在放；镜头切走后音乐继续 | `all music is diegetic, coming from the character's headphones or car stereo, continuing across cuts` |
| 表现手法 | 创伤记忆的非自愿闪现、女性内心视角、日常细节堆叠出压抑 | `involuntary intrusive memory fragments interrupting the present` |
| 招牌镜头 | 戴耳机开车 / 海边回望 / 0.2s 闪回插入 / 浴室镜中自视 |
| 代表作 | 《大小谎言》《利器》《达拉斯买家俱乐部》《涉足荒野》 |

**锚点句（中）**：松散自然光手持，透过门框与镜面的偷窥式取景，主线镜头中突然插入 0.2 秒的记忆碎片单帧，音乐全部来自角色耳机等画内音源。
**锚点句（英）**：`loose handheld under natural window light at 2.5:1, framing through doorframes and mirrors, sudden 0.2-second intrusive memory fragments cut into the present with no transition, all music diegetic from the character's headphones, 35mm shallow focus, 1.78:1`

**⚠️ 不要与之叠加**：稳定器精密运镜、棚拍布光、交响配乐、对称构图。

---
# 四、商业广告

> 广告与影视的根本差别：**时长 15–90s，必须在前 3s 抓人、最后 2s 落品牌**。所有导演的手法都服务于"单一记忆点"。

## 26. 雷德利·斯科特 Ridley Scott — 烟雾光束·史诗质感

（广告出身，RSA Films 创始人；苹果《1984》、香奈儿、百威）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 多层纵深（前景剪影 + 中景主体 + 背景光源）、宏大布景压人 | `layered depth: silhouetted foreground, lit mid-ground subject, glowing background` |
| 运镜 | 多机位同时拍摄、缓慢横移揭示规模、低角度英雄仰拍 | `slow lateral track revealing the scale, low hero angle` |
| 节奏 | 广告 60s 结构：**建立世界 20s → 冲突 25s → 品牌落点 15s**；镜头偏长偏重，ASL 2–4s | 段长 2–4s，最后一镜留足 2s 给 logo |
| 升降格 | 关键破坏/冲击瞬间 1/2 升格（《1984》铁锤飞出、屏幕爆炸） | `1/2 speed on the hammer release and shatter` |
| 色彩 | 青蓝冷调 + 琥珀暖点光对撞（teal & amber 的源头之一） | `cold teal environment punctuated by amber practical lights` |
| 光影 | **烟雾 + 强逆光 = 可见光柱（God rays）**，这是他最强的签名；光比 8:1 | `heavy atmospheric haze with hard backlight creating visible volumetric god rays, 8:1` |
| 胶片/画幅 | 35mm 胶片质感、大量长焦压缩（85–200mm）、2.35:1 | `35mm film texture, 135mm telephoto compression, 2.35:1` |
| 音乐 | 史诗合成器（Vangelis）/ 交响推进；节拍与画面重击同步 | `epic synth swell, orchestral hit synced to impact` |
| 表现手法 | 世界观先行（一条广告造一个世界）、寓言式叙事、极端质感（雨、烟、蒸汽、尘） | `rain, steam, dust and haze constantly in the air` |
| 招牌镜头 | 逆光烟雾中的人物剪影 / 巨大空间的渺小个体 / 慢镜锤击 |
| 代表作 | Apple《1984》、Chanel No.5《Share the Fantasy》、《银翼杀手》《角斗士》 |

**锚点句（中）**：浓重烟雾中的强逆光可见光柱，青蓝冷调配琥珀点光，前中后三层纵深，长焦压缩，史诗合成器推进。
**锚点句（英）**：`heavy atmospheric haze with hard backlight forming volumetric god rays at 8:1, cold teal with amber practical accents, three-layer depth staging, 135mm telephoto compression, epic synth swell, 35mm 2.35:1`

**⚠️ 不要与之叠加**：平光、干净通透空气、极简白背景。

---

## 27. 斯派克·琼斯 Spike Jonze — 一镜到底·身体动能·实拍奇观

（Apple《Welcome Home》、Kenzo《Kenzo World》、Fatboy Slim《Weapon of Choice》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 让身体填满画面、随舞者动线重构空间；空间本身是角色 | `space itself deforms and stretches around the dancer` |
| 运镜 | **跟随舞蹈的连续长镜头**、机器随人体加速减速、几乎无剪辑点 | `continuous single-take camera following the dancer, accelerating with the body` |
| 节奏 | 音乐节拍即剪辑节拍；一条广告常只有 1–3 个切点，ASL 8–15s | 少切多动：一镜 8–15s，动作自身提速 |
| 升降格 | 变速在**同一镜头内**发生（实拍 + 相机内变帧），突然放慢再弹回 | `in-camera speed ramp within the single take` |
| 色彩 | 自然暖调、真实肤色优先，少调色；偶尔高饱和爆发（Kenzo 的荧光绿） | `natural warm grade, true skin tones, one saturated accent color` |
| 光影 | 柔和自然光 + 实景灯；不追求电影感反差，追求"真实发生过"；光比 2:1 | `soft naturalistic light, in-frame practical lamps, 2:1` |
| 胶片/画幅 | 数字为主，1.85:1；广角 24mm 贴近拍身体 | `24mm close to the body, 1.85:1` |
| 音乐 | **音乐是结构本体**（先有歌再有片），编舞严格对拍 | `choreography strictly locked to the beat, music drives every movement` |
| 表现手法 | 实拍魔法（真做机关、真拉伸布景），拒绝纯 CG；幽默 + 天真 + 一点忧郁 | `practical in-camera magic, no CGI` |
| 招牌镜头 | 舞者带动房间变形 / 走廊里跳跃穿行的一镜 / 突然打破空间规则 |
| 代表作 | Apple HomePod《Welcome Home》、Kenzo World、《她》《变脑》 |

**锚点句（中）**：跟随舞者的连续一镜到底，空间随身体拉伸变形，自然柔光真实肤色，镜内变速，动作严格咬住音乐节拍。
**锚点句（英）**：`continuous one-take following a dancer, the room stretching and deforming around the body, soft naturalistic light with true skin tones at 2:1, in-camera speed ramp, movement locked to the beat, 24mm 1.85:1`

**⚠️ 不要与之叠加**：密集快切、冷酷低照度、静止机位。

---

## 28. 道格尔·威尔逊 Dougal Wilson — 情感叙事·90 秒微电影

（John Lewis 圣诞广告《Man on the Moon》《Monty the Penguin》《Bear & the Hare》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | 以**角色面部反应**为核心，儿童/动物视角高度；构图简单不炫技 | `camera at a child's eye height, framing centered on the face reaction` |
| 运镜 | 极简：缓推、缓摇、静止；把注意力全留给表演 | `gentle slow push-in, otherwise static; camera stays out of the way` |
| 节奏 | 90s 三幕：**建立温暖日常 30s → 制造缺失/渴望 40s → 情感兑现 20s**；ASL 2.5–4s | 段长 2.5–4s，情感兑现镜留 3s |
| 升降格 | 温和 3/4 微升格用于"心动瞬间"（礼物拆开、眼神相遇） | `subtle 3/4 speed at the moment of realization` |
| 色彩 | 暖金色圣诞调（2700K）、室内壁炉橙 + 窗外冷蓝雪夜（7000K）的暖冷对比 | `warm 2700K golden interior against 7000K cold blue snowy window` |
| 光影 | 柔和大面积光、发丝逆光、圣诞灯串做前景虚焦光斑；光比 2:1 | `soft wrapping light, hair backlight, out-of-focus fairy-light bokeh in foreground, 2:1` |
| 胶片/画幅 | 35mm 或数字仿胶片、浅景深、16:9 / 1.85:1；50–85mm | `35mm film look, 85mm shallow depth of field, 1.85:1` |
| 音乐 | **著名歌曲的慢速翻唱**（女声钢琴版），副歌与情感高点精确对齐 | `slow female-vocal piano cover of a famous song, chorus hits at the emotional peak` |
| 表现手法 | 一个简单的善意行为撑起全片；不解释、靠画面自证；片尾一句品牌标语 | `one simple act of kindness carries the whole story, no dialogue` |
| 招牌镜头 | 孩子望向窗外 / 拆礼物的手部特写 / 雪夜暖窗外景 / 结尾拥抱 |
| 代表作 | John Lewis 系列圣诞广告、Nike、Samsung |

**锚点句（中）**：儿童视线高度的简洁构图，缓慢微推，暖金室内对比窗外冷蓝雪夜，前景圣诞灯串虚焦光斑，钢琴女声慢速翻唱在情感高点进入。
**锚点句（英）**：`simple framing at a child's eye height, gentle slow push-in, warm 2700K golden interior against 7000K cold blue snow outside, foreground fairy-light bokeh, 85mm shallow focus, slow piano-and-female-vocal cover swelling at the emotional peak`

**⚠️ 不要与之叠加**：高对比硬光、快切、冷峻疏离。

---
## 29. 乔纳森·格雷泽 Jonathan Glazer — 单一超现实隐喻·黑白史诗慢镜

（健力士《Surfer》、Levi's《Odyssey》；电影《皮囊之下》《利益区域》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **一条片只讲一个隐喻画面**；巨大自然力量与渺小人体并置；构图庄严、近乎宗教画 | `one single surreal metaphor image carried through the whole film, vast natural force against a small human body` |
| 运镜 | 长焦定点凝视 + 缓慢横移；或完全静止的监控式机位（《利益区域》固定机位）；绝不炫技 | `locked-off telephoto stare, slow lateral drift, or fixed surveillance-style framing` |
| 节奏 | 慢起快收：铺陈段 ASL 4–8s，隐喻爆发段用连续慢镜 6–10s，最后 2s 硬切品牌 | 铺陈 4–8s → 慢镜高潮 8s → logo 2s |
| 升降格 | **1/4–1/2 升格是核心语言**：巨浪化为白马、身体在浪中翻滚，慢到能看清水的结构 | `1/4 speed on the breaking wave so the water structure reads as galloping white horses` |
| 色彩 | 高对比黑白，或极度去饱和只留一个色（Levi's 的蓝）；深黑与亮白无中间灰 | `high-contrast black and white with crushed blacks and blown whites, or near-monochrome with a single blue` |
| 光影 | 自然光为主，强调轮廓逆光与水雾反光；光比 10:1，剪影优先 | `natural hard backlight through sea spray, 10:1, silhouette-first` |
| 胶片/画幅 | 35mm 高速摄影机（拍慢镜用 120–240fps）；2.35:1；长焦 200mm+ 压缩浪墙 | `shot at 200fps on 35mm, 200mm telephoto compressing the wave wall, 2.35:1` |
| 音乐 | 打击乐渐强（Leftfield《Phat Planet》式），或人声吟诵；音乐与画面同步爆发 | `pounding percussive build with tribal drums, exploding in sync with the wave` |
| 表现手法 | 等待与释放的结构（"good things come to those who wait"）、隐喻而非说明、极少对白 | `structure of waiting then release, metaphor over explanation, no dialogue` |
| 招牌镜头 | 巨浪化白马 / 冲浪者仰望浪壁 / 静止凝视的人脸 / 无声的宏大自然 |
| 代表作 | Guinness《Surfer》、Levi's《Odyssey》、《皮囊之下》《利益区域》 |

**锚点句（中）**：一个贯穿全片的超现实隐喻画面，200fps 高速摄影的 1/4 升格让浪花显出白马形态，高对比黑白剪影，200mm 长焦压缩巨浪，打击乐渐强与浪墙同步爆发。
**锚点句（英）**：`one sustained surreal metaphor, 200fps high-speed 1/4 slow motion revealing galloping white horses inside the breaking wave, high-contrast black and white with crushed blacks and blown whites, 200mm telephoto compression, hard natural backlight through spray at 10:1, pounding percussive build exploding in sync, 2.35:1`

**⚠️ 不要与之叠加**：粉彩柔美、密集快切、暖调温情、多个隐喻并列。

---

## 30. 塔西姆·辛 Tarsem Singh — 美术奇观·单帧即海报·珠宝色

（Nike、Pepsi、L'Oréal；电影《坠入》《入侵脑细胞》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **每一帧都按静态海报构图**：绝对对称、几何图形化的人群排列、极端俯拍把人排成图案 | `every frame composed as a still poster: perfect symmetry, human bodies arranged into geometric patterns, extreme overhead forming a mandala` |
| 运镜 | 缓慢升降揭示图案全貌、静止长镜让美术说话、缓慢环绕巨型道具 | `slow crane up revealing the full pattern, locked-off frames showcasing the design` |
| 节奏 | 中速，ASL 2–4s；每个镜头都是一个"新世界"，靠奇观密度而非叙事推进 | 2–4s 一刀，每刀换一个奇观场景 |
| 升降格 | 1/2 升格给飘落的布料、洒落的颜料、腾空的舞者 | `1/2 speed on flowing fabric and falling pigment` |
| 色彩 | **珠宝色（jewel tones）**：宝石红、皇家蓝、翡翠绿、金；高饱和且大面积铺满 | `saturated jewel tones: ruby red, royal blue, emerald green and gold filling large areas` |
| 光影 | 均匀高调布光让美术全可见（光比 2:1），或强顶光造戏剧感；不藏细节 | `even high-key lighting at 2:1 so every design detail reads, or hard top light for drama` |
| 胶片/画幅 | 35mm；2.39:1；广角 24mm 拍宏大布景 + 长焦拍材质特写 | `24mm for the grand set, 100mm for material detail, 35mm film, 2.39:1` |
| 音乐 | 世界音乐/民族打击乐、恢弘人声；节拍与画面切换严格同步 | `world-music percussion with soaring vocals, cuts locked to the beat` |
| 表现手法 | **实景实搭实拍**（真去异国实景、真做服装）、超现实场景拼贴、无对白靠视觉 | `real exotic locations and real elaborate costumes, no CGI backdrop, wordless visual storytelling` |
| 招牌镜头 | 俯拍人体组成图案 / 沙漠中的红衣人群 / 巨型建筑前的对称站位 / 布料飞舞 |
| 代表作 | 《坠入》、Nike 系列广告、Pepsi《Dance》、《入侵脑细胞》 |

**锚点句（中）**：每一帧按静态海报构图，极端俯拍将人体排成几何图案，宝石红与皇家蓝等珠宝色大面积铺满，均匀高调布光让美术全可见，缓慢升降揭示图案全貌。
**锚点句（英）**：`every frame composed as a still poster, extreme overhead arranging human bodies into a geometric mandala, saturated jewel tones of ruby red royal blue and gold filling the frame, even high-key lighting at 2:1, slow crane up revealing the full pattern, real locations and elaborate costumes, 24mm 2.39:1`

**⚠️ 不要与之叠加**：手持纪录感、去饱和灰调、低照度暗部、随意构图。

---

## 31. 罗曼·加夫拉斯 Romain Gavras — 大规模群众·手持追随·泥土烟火

（Adidas《Break Free》、Nike、M.I.A.《Bad Girls》、Jay-Z & Kanye《No Church in the Wild》；电影《雅典娜》）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **大规模真实群众场面**（数百人同框奔跑/对峙）；主体在人群中被淹没又浮现；广角贴身 | `hundreds of real people surging in one frame, the protagonist swallowed and re-emerging from the crowd` |
| 运镜 | **手持追随冲进人群**、长镜头连续穿越骚乱、镜头被撞被烟遮挡也不停 | `handheld charging into the crowd, unbroken take pushing through a riot, camera struck and obscured but never stopping` |
| 节奏 | 快而不碎，ASL 1.5–3s；或用 60s+ 的一镜到底承载整场骚乱 | 1.5–3s 密切，或单镜 60s 骚乱长镜 |
| 升降格 | 关键抛掷/腾空/火焰爆开给 1/2 升格，立刻回实速；不做全片慢镜 | `1/2 speed on the thrown molotov arc, snapping back to real time` |
| 色彩 | 泥土褐 + 烟火橙 + 沥青灰；中低饱和但橙色火光极亮，肤色偏暖 | `earth brown and asphalt grey with intense orange flare light, medium-low saturation` |
| 光影 | 自然光 + 燃烧的照明弹/烟雾弹作为主光；烟中体积光；光比 6:1，允许过曝 | `daylight plus burning flares as key, volumetric light in smoke, 6:1, clipping allowed` |
| 胶片/画幅 | 35mm 或数字加颗粒；2.39:1；广角 18–28mm 贴身进人群 | `18mm handheld inside the crowd, grainy 35mm texture, 2.39:1` |
| 音乐 | 电子/嘻哈/歌剧的反差混搭；鼓点与群众动作同步；低频强推 | `operatic vocal over hip-hop drums, bass hits synced to the crowd surge` |
| 表现手法 | **粗粝史诗感**：真人真烟真泥，无 CG 群众；青年亚文化、街头对抗、集体亢奋 | `raw physical epic: real crowds, real smoke, real dirt, no CGI extras` |
| 招牌镜头 | 烟雾弹中奔跑的人群 / 举火把的青年剪影 / 骚乱一镜穿越 / 群体腾空跳跃 |
| 代表作 | Adidas《Break Free》、Nike《Nothing Beats a Londoner》风格系、《雅典娜》 |

**锚点句（中）**：数百人真实群众场面，18mm 广角手持冲进人群的连续长镜，燃烧照明弹作为主光在烟雾中形成体积光，泥土褐与沥青灰配炽烈橙色火光，抛掷瞬间 1/2 升格后立刻回实速。
**锚点句（英）**：`hundreds of real people surging in frame, 18mm handheld charging into the crowd in one unbroken take, burning flares as key light with volumetric smoke at 6:1, earth-brown and asphalt-grey palette with intense orange flare, 1/2 speed on the thrown arc snapping back to real time, grainy 35mm 2.39:1`

**⚠️ 不要与之叠加**：棚拍干净背景、对称构图、柔光美颜、静止机位、极简留白。

---
## 32. 马丁·德·图拉 Martin de Thurah — 北欧超现实·冷灰自然光·缓慢诡异

（丹麦导演；时尚与情绪型广告，Hennessy、Sonos、Carlsberg 等）

| 维度 | 特征 | 提示词可执行写法 |
|---|---|---|
| 分镜/构图 | **大量留白**：主体只占画面一小块，其余是空墙、空田野、空天空；人物常背对或侧对 | `subject occupying a small part of the frame, vast empty wall or field taking the rest, figure turned away` |
| 运镜 | 极缓推进或极缓横移（几乎察觉不到）、静止长镜；偶尔轻微手持呼吸感 | `barely perceptible slow push-in, long static holds, faint handheld breathing` |
| 节奏 | 慢，ASL 4–8s；镜头之间不解释因果，靠情绪串联；广告 60s 只有 8–12 个镜头 | 4–8s 一镜，全片 8–12 镜 |
| 升降格 | **1/2–3/4 升格用于"不该慢的东西"**：一个人缓慢转头、鸟群突然升起、水滴悬停 | `1/2 speed on an ordinary gesture such as a head slowly turning, making it uncanny` |
| 色彩 | 北欧冷灰：灰蓝、苔绿、灰白；低饱和，肤色苍白；只允许一个暖色小点 | `Nordic cold grey-blue and moss green, low saturation, pale skin, one small warm accent` |
| 光影 | **阴天散射自然光**（无明显方向）、窗光大面积柔和；光比 2:1，整体略欠曝 | `overcast diffused daylight with no visible direction, soft window light, 2:1, slightly underexposed` |
| 胶片/画幅 | 16mm/35mm 胶片颗粒或数字仿胶片；1.85:1 / 2.39:1；50–85mm 中长焦浅景深 | `16mm film grain, 85mm shallow focus, 1.85:1` |
| 音乐 | 极简钢琴单音、环境电子铺底、女声无词吟唱；大量静音留白 | `sparse single-note piano over ambient pad, wordless female vocal, long silences` |
| 表现手法 | **缓慢诡异的动作**（人以不自然的慢速做日常事）、超现实事件被平静接受（屋里下雨、人漂浮） | `an uncanny event treated as ordinary: rain falling indoors, a body slowly levitating` |
| 招牌镜头 | 空旷田野中的单人背影 / 缓慢转头的面孔 / 室内落雨 / 鸟群骤起 |
| 代表作 | Hennessy 系列、Sonos、Carlsberg 情绪广告、多支北欧时尚短片 |

**锚点句（中）**：主体只占画面一小块、其余大面积留白，阴天无方向散射自然光略欠曝，北欧冷灰蓝与苔绿低饱和，日常动作以 1/2 升格缓慢进行而显诡异，超现实事件被平静接受。
**锚点句（英）**：`subject small in frame with vast empty negative space, overcast directionless diffused daylight slightly underexposed at 2:1, Nordic cold grey-blue and moss-green low-saturation palette, an ordinary gesture at 1/2 speed turning uncanny, a surreal event treated as completely normal, 85mm shallow focus, 16mm grain, 1.85:1`

**⚠️ 不要与之叠加**：高饱和、暖金色、快切、密集运镜、戏剧性硬光。

---

# 五、一行式速查（未展开的导演）

> 用法：这些只给"一句话锚点"，直接贴进提示词风格句尾即可。需要完整 10 维参数时，参考上文最接近的完整条目再微调。

| 导演 | 领域 | 一行锚点（可直接贴进提示词） |
|---|---|---|
| 索菲亚·科波拉 Sofia Coppola | 电影 | 柔和过曝窗光、粉彩少女色、静止凝视的孤独背影、慵懒 shoegaze 配乐、ASL 5–8s |
| 格蕾塔·葛韦格 Greta Gerwig | 电影 | 暖调群戏中景、人物边走边说的跟拍、生活化自然光、饱和明快色卡（Barbie 的洋红/天蓝） |
| 卢卡·瓜达尼诺 Luca Guadagnino | 电影 | 意大利夏日 35mm 胶片、汗水与皮肤质感特写、跟随身体的手持、Sayombhu 式绿荫斑驳光 |
| 亚利桑德罗·伊纳里图 Iñárritu | 电影 | 超广角贴脸手持长镜、自然光/火光唯一光源、呼吸声入镜、镜头被血雾溅到 |
| 丹尼·博伊尔 Danny Boyle | 电影 | 荷兰角+超广角、高饱和原色（橙绿），跳切与定格字幕、电子乐驱动、ASL 1–2s |
| 盖·里奇 Guy Ritchie | 电影 | 快速抽帧加速+骤停、章节式人物定格介绍、伦敦冷灰配暖褐、圆桌环绕横摇 |
| 埃德加·赖特 Edgar Wright | 电影 | 音效驱动的极速甩摇与匹配剪辑、动作与音乐逐帧对齐、对称正面构图、snap zoom |
| 罗伯特·艾格斯 Robert Eggers | 电影 | 时代考据实景、只用烛光/自然光（1800K）、1.19:1 或 1.66:1 窄画幅、黑白高反差、缓慢推进 |
| 阿里·艾斯特 Ari Aster | 电影 | 明亮日光下的恐怖、极缓 180° 翻转与倒置构图、对称人偶屋式布景、民俗仪式群像 |
| 萨姆·门德斯 Sam Mendes | 电影 | 一镜到底战场调度（《1917》）、对称中心构图、Deakins 式硬逆光、冷蓝夜配照明弹橙 |
| 吕克·贝松 Luc Besson | 电影 | 高饱和霓虹未来感、广角贴脸、鱼眼与倾斜、蓝橙对撞、动作段 1.5s 快切 |
| 马修·沃恩 Matthew Vaughn | 电影 | 伪一镜动作长镜（教堂大屠杀式）、音乐点唱配暴力、鲜艳英式复古色、旋转跟随 |
| 扎克·施奈德 Zack Snyder | 电影 | 速度斜坡（实速→1/4→实速 在同一镜内）、去饱和高对比灰、逆光尘埃、极浅景深 f/0.95 |
| 约翰·卡朋特 John Carpenter | 电影 | 2.35:1 静止宽画幅、画面边缘潜伏的身影、蓝调夜景、合成器脉冲配乐、缓慢横摇 |
| 托尼·斯科特 Tony Scott | 电影 | 抽帧+拖影的躁动质感、高饱和青橙、烟雾百叶窗光、长焦快切、直升机低掠 |
| 韦斯·克雷文 Wes Craven | 电影 | 主观视角窥视、突然闯入画面的手、梦境与现实无缝切换、低机位仰拍、荧光绿红光 |
| 大卫·雷奇 David Leitch | 电影 | 枪斗术（gun-fu）全身连贯长镜、不切碎动作、霓虹紫蓝、宽景别看清招式、ASL 3–6s |
| 克洛伊·赵 Chloé Zhao | 电影 | 只拍 magic hour 自然光、超广角天空占 2/3、非职业演员纪实手持、荒原公路 |
| 努里·比格·锡兰 Nuri Bilge Ceylan | 电影 | 极长静止对话镜（30s+）、安纳托利亚雪原与土黄、单一窗光侧脸、大量环境空镜 |
| Nicolai Fuglsig | 广告 | 索尼《Balls》——真实大规模物理事件（25 万彩球滚下街道）、纪录式多机位、自然光 |
| Traktor | 广告 | 荒诞冷幽默、快节奏对比剪辑、鲜艳平面感、正面对称、ASL 0.8–1.5s |
| Bruno Aveillan | 广告 | 卡地亚《L'Odyssée》——奢华质感、金色流光、超现实旅程、微距材质特写、暖金 2800K |

---
# 六、欧美导演横向对照表（选风格时先看这张）

| 导演 | ASL | 运镜性格 | 色彩 | 光比 | 升格用法 |
|---|---|---|---|---|---|
| 库布里克 | 8–20s | 极慢推/拉，绝对稳 | 高饱和单色块 | 均匀 1.5:1 | 不用 |
| 诺兰 | 2–4s | 稳定跟拍，实拍 | 低饱和冷蓝灰 | 高 6:1（自然硬光） | 只给物理事件 1/4 |
| 韦斯·安德森 | 3–5s（等长） | 甩摇/平移/变焦 | 粉彩三色 | 极低 1.5:1（平光） | 只在结尾群像 1/2 |
| PTA | 6–12s | 穿行推轨长镜 | 70s 暖褐芥末黄 | 中 3:1（柔窗光） | 只在情绪崩溃 1/2 |
| 维伦纽瓦 | 6–12s | 极慢无声推进 | 雾霾橙/水泥灰单色 | 两极（雾极低 / 剪影极高） | 基本不用 |
| 马力克 | 2–4s | 贴地持续游走 | 黄昏金橙+草绿 | 低（自然逆光） | 3/4 给风与草 |
| 卡隆 | 15–60s | 超长横摇一镜 | 黑白 / 低饱和自然 | 中 3:1（自然窗光） | 不用 |
| 查泽雷 | 0.3–0.8s（高潮）/ 3–5s | 360° 环绕，对拍剪 | 单色追光高饱和 | 极高 10:1 | 腾空顶点 1/2 |
| 昆汀 | 对白 8–20s / 暴力 0.5–1.5s | 环绕+急速变焦 | 剥削片暖橙红 | 中高 4:1 | 慢走登场 1/2 |
| 科恩兄弟 | 4–8s | 贴地冲刺+锁死静止 | 雪白褐 / 沙黄 | 平淡（自然光） | 不用 |
| 乔治·米勒 | 0.8–2s | 车载并行高速 | 极饱和橙+电蓝 | 高 8:1（正午） | 20fps 抽帧加速 |
| 迈克尔·贝 | 1–2s | 360° 环绕+推入 | 极端青橙分离 | 高（强逆光光晕） | 英雄时刻 1/2（慎用） |
| 卡梅隆 | 2.5–4.5s | 后拉揭示+水下环绕 | 蓝绿冷调+橙点 | 中高 6:1（体积光束） | 水下冲击 1/2 |
| 乔丹·皮尔 | 5–9s | 极缓推脸+锁死 | 明亮日光草绿白墙 | 低 2:1（全亮） | 下沉时刻 1/2+后拉 |
| 蒂姆·波顿 | 3–5s | 螺旋上升+环绕 | 黑白+单点毒紫 | 高 8:1（硬侧光） | 3/4 给飘落物 |
| 德尔·托罗 | 4–7s | 缓慢横移展示美术 | 青绿+琥珀双色 | 中高（烛光对月光） | 3/4 给水中漂浮 |
| 大卫·林奇 | 8–15s | 极慢光学变焦 | 红与纯黑 | 极高 12:1（单实用光） | 倒放式诡异运动 |
| 斯科塞斯 | 长镜 20–60s / 蒙太奇 0.8–2s | 斯坦尼康穿行 | 饱和暖红+深棕 | 中高 5:1（实用光） | 定格代替慢镜 |
| 斯皮尔伯格 | 3–6s | 缓慢推入+dolly zoom | 暖金+天蓝 / 战争去饱和 | 中高 6:1（画外强光） | 基本不用 |
| 吉利根 | 静 3–5s / 爆 0.5s | 锁死静止 | 沙漠黄 | 高 8:1（正午硬光） | 只用延时 |
| 芬奇 | 3–5s | 无摩擦慢推 | 病态黄绿 | 极高 10:1（暗部压死） | 不用 |
| 萨波奇尼克 | 长镜 + 0.4–0.8s | 手持穿行 | 去饱和泥血灰 | 高（火光单源） | 致命一击 1/3 |
| 福永 | 单镜 60–360s | 斯坦尼康不间断 | 潮湿绿褐低饱和 | 变动（现场光） | 绝不使用 |
| 约翰·雷克 | 5–9s | 缓慢横移+极缓推 | 去饱和灰绿 | 低 3:1（阴天+荧光） | 不用 |
| 让-马克·瓦雷 | 3–5s + 0.2s 闪回 | 松散手持漂移 | 自然暖白 / 闷热青 | 低 2.5:1（自然窗光） | 不用（靠极短） |
| 雷德利·斯科特 | 2–4s | 缓慢横移揭示 | 青蓝 + 琥珀 | 高 8:1（烟雾逆光） | 冲击瞬间 1/2 |
| 斯派克·琼斯 | 8–15s（一镜） | 跟随身体 | 自然暖 | 低 2:1（柔光） | 镜内变速 |
| 道格尔·威尔逊 | 2.5–4s | 缓推/静止 | 暖金 + 冷蓝 | 低 2:1（柔光） | 心动瞬间 3/4 |
| 格雷泽 | 4–8s | 长焦凝视/固定机位 | 高对比黑白 | 极高 10:1（剪影） | 核心语言 1/4（200fps） |
| 塔西姆·辛 | 2–4s | 缓慢升降揭示图案 | 珠宝色高饱和 | 低 2:1（高调均匀） | 1/2 给布料颜料 |
| 罗曼·加夫拉斯 | 1.5–3s / 骚乱一镜 60s | 手持冲进人群 | 泥土褐+火光橙 | 高 6:1（照明弹） | 抛掷瞬间 1/2 |
| 马丁·德·图拉 | 4–8s | 极缓推进/静止 | 北欧冷灰蓝苔绿 | 低 2:1（阴天散射） | 日常动作 1/2 变诡异 |

---

# 七、⚠️ 本册内部禁忌组合（写进提示词前必查）

## ❌ 绝对冲突（模型会输出平庸平均值）

| 冲突组合 | 为什么冲突 |
|---|---|
| 库布里克 + 快切 | 他的压迫感完全建立在 8–20s 长镜头上，切碎就没了 |
| 韦斯·安德森 + 手持 | 对称平面构图与晃动是根本对立 |
| 芬奇 + 暖阳柔光 | 他的语言就是暗部压死与冷调，加暖柔光等于全部抵消 |
| 迈克尔·贝 + 极简留白 | 他靠信息过载与环绕运动，留白让他的语言无处施展 |
| 吉利根 + 连续运镜 | 他的张力来自机位锁死，一动就泄气 |
| 卡隆/福永 + 慢动作 | 他们的一镜到底卖的就是"实时性"，慢镜直接摧毁核心 |
| 维伦纽瓦 + 快切 | 巨物压迫需要时间累积，2s 切一刀等于没看见 |
| 马力克 + 棚拍布光 | 他只拍 magic hour 自然光，人工光一上风格归零 |
| 查泽雷 + 无配乐留白 | 他的剪辑点由鼓点定义，没音乐就没有剪辑逻辑 |
| 乔丹·皮尔 + 低照度暗调 | 他的恐怖恰恰建立在"全亮、无处可藏"上 |
| 格雷泽 + 多个隐喻并列 | 他一条片只讲一个隐喻，堆两个就变成普通广告 |
| 德·图拉 + 高饱和暖金 | 北欧冷灰是他的全部识别度 |
| 科恩兄弟 + 华丽运镜 | 荒诞感来自机位的木讷与"多停一拍" |
| 大卫·林奇 + 清晰因果叙事 | 诡异来自逻辑断裂，解释清楚就不诡异了 |
| 同时叠加 3 位以上导演 | 特征互相抵消，输出变成平庸平均值 |

## ⚠️ 半冲突（可用但只能各取一维）

| 组合 | 处理方式 |
|---|---|
| 诺兰 + 迈克尔·贝 | 都爱大场面但质感相反：取诺兰的实拍质感 + 贝的低机位仰角，**丢掉贝的光晕和青橙** |
| 斯皮尔伯格 + 芬奇 | 取芬奇的构图精度 + 斯皮尔伯格的脸部反应，**光比听芬奇的、推入速度听斯皮尔伯格的** |
| 塔西姆·辛 + 加夫拉斯 | 都拍大规模群像：取塔西姆的图案化站位 + 加夫拉斯的手持能量，**但色彩只能二选一** |
| 昆汀 + 斯科塞斯 | 语言高度重叠（点唱、暴力、旁白），叠加等于没叠加，**选一个即可** |

## ✅ 推荐的互补组合

- **诺兰（实拍质感）+ 萨波奇尼克（混战调度）** → 写实战争
- **雷德利·斯科特（烟雾光束）+ 塔西姆·辛（图案化群像）** → 史诗品牌广告
- **斯皮尔伯格（脸部反应）+ 维伦纽瓦（巨物剪影）** → 低成本科幻奇观（脸给情绪，剪影给规模，都不用真渲染）
- **道格尔·威尔逊（情感结构）+ 斯派克·琼斯（一镜）** → 温情品牌片
- **德·图拉（冷灰留白）+ 格雷泽（单一隐喻）** → 高端时尚情绪片
- **福永（不间断长镜）+ 加夫拉斯（群众能量）** → 骚乱/追逐一镜到底

---

# 八、转译三原则（与亚洲册通用）

1. **拆参数优先于报人名**：先写 `handheld 18mm at eye level, firelight only, desaturated grey`，再在句尾加 `in the style of Sapochnik's battle sequences`。
2. **一个维度只服从一位导演**：色彩听 A 的，运镜听 B 的，不要两个人抢同一个维度。
3. **最多取 3 个特征**：超过 3 个，模型开始平均化，风格反而消失。

---

## 与本技能其他文件的关系

- 亚洲导演（王家卫、张艺谋、杜琪峰、黑泽明等）：见 `director-anchors-asian.md`。
- 摄影指导维度（Deakins / Kamiński / Lubezki 等的布光与镜头选择）：见 `dp-cinematographer-anchors.md`。
- 动作/打斗场景的**镜长节奏与景别调度**：见 `references/genre/action-wuxia.md`（本文件负责"风格"，那份负责"剪辑数学"）。
- 建议流程：先用 `references/genre/action-wuxia.md` 定节奏曲线 → 再用本文件挑风格锚点填色彩/光影/质感 → 最后用 `dp-cinematographer-anchors.md` 微调布光细节。

