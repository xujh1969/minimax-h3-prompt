# 画风层手册 · Visual Style

> **一句话定性**：画风与题材**正交**。同一个「母子在站台告别」，可以是真人温情片、吉卜力手绘、皮克斯 3D、水墨动画——**故事一字不改，四套参数完全不同**。
> 题材决定「拍什么」，画风决定「用什么物质拍」。两者不能混着写。

---

## 铁律：画风必须锁在提示词开头

**画风是生成基底，不是修饰词。** 模型在解析提示词时，前 15–20 个 token 决定了整个画面的渲染管线（真实光学 vs 手绘笔触 vs 多边形着色）。把画风写在句尾当点缀，模型会先按真人实拍建立画面，再在表面刷一层风格滤镜——结果是**"3D 感的假动画"或"贴了动画贴图的实拍"**，两头不靠。

```
✅ 正确：吉卜力风格手绘水彩动画，一位母亲在乡村站台送别儿子……
❌ 错误：一位母亲在乡村站台送别儿子，画面为吉卜力风格。
```

**英文同理**：`Studio Ghibli-style hand-painted watercolor animation, a mother …`
风格词 + 媒介词（animation / live-action / stop-motion / 3D render）必须成对出现在**第一句**。

**一条片子只锁一种画风。** 混合风（如 Spider-Verse）是**被明确定义过的单一风格**，不是让你把"吉卜力 + 皮克斯"叠着写——那只会得到糊掉的平均值。

---

## 1. 真人实拍 Live-Action（基准参照系）

> 其余 15 种画风，都是**相对这一节的偏移量**。写任何动画风格前，先想清楚"它和实拍差在哪一维"。

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 无轮廓线。物体边界由光学对比度和景深虚化定义 |
| 上色与质感 | 连续渐变，皮肤有毛孔/绒毛/油光，材质由 BRDF 物理决定 |
| 背景与景深 | 真实光学景深，f/1.4–f/2.8 时背景奶油化，焦外光斑呈镜头光圈形状 |
| 光效处理 | 平方反比衰减、真实阴影半影、间接反弹光 |
| 运动规律 | 24fps + 1/48s 快门，运动模糊真实，无中间帧概念 |
| 摄影机行为 | 受重量与物理约束，手持有生理抖动，轨道有惯性 |
| 色彩体系 | 由传感器 + LUT 决定，宽色域连续过渡 |
| **头号翻车点** | 写了"电影感"却不给具体焦段/光比/色温——模型会输出手机随手拍的观感 |

**锚点句**
> 实拍电影画面，35mm 镜头，f/2.0 浅景深，柔和侧光光比 3:1，色温 4200K，24fps 自然运动模糊。
> `Live-action cinematic footage, 35mm lens, f/2.0 shallow depth of field, soft key light at 3:1 ratio, 4200K, 24fps natural motion blur.`

---

## 2. 日式赛璐璐 TV 动画 Cel-shaded Anime

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **闭合黑色描边**，粗细均匀（1–2px 等效），发丝与眼睛处线条加重 |
| 上色与质感 | **硬边色阶分界 cel shading**，通常 2–3 阶（亮部 / 本色 / 影色），影色是本色降明度 + 偏紫，**绝不用渐变** |
| 背景与景深 | 背景美术单独绘制，比人物精细一档；景深靠**画上去的模糊层**，不是光学虚化 |
| 光效处理 | **逆光通透**：角色边缘一圈高饱和亮边；光斑用叠加发光图层，不做物理反弹 |
| 运动规律 | **有限动画 limited animation**，主流为 on threes（24fps 下 8 张/秒）；关键动作偶尔 on twos（12 张/秒） |
| 摄影机行为 | 大量**平移与推拉**（拍摄台运动），少 3D 环绕；冲击瞬间用速度线 + 快速甩镜 |
| 色彩体系 | 高饱和、有限调色板，天空青蓝、肤色偏暖粉，阴影统一偏紫 |
| **头号翻车点** | 加了"真实全局光/柔和渐变阴影"→ 色阶被抹平，立刻变成廉价 3D 卡通渲染 |

**锚点句**
> 日式赛璐璐 TV 动画，硬边两阶上色，闭合黑色描边，逆光下角色边缘高饱和亮边，有限动画每秒 8 张，摄影机横向平移。
> `Japanese cel-shaded TV anime, hard two-tone cel shading, clean closed black outlines, backlit rim light on characters, limited animation on threes (8 drawings per second), horizontal camera pan.`

---

## 3. 吉卜力手绘水彩 Ghibli Hand-painted

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 细而柔的手绘线，**深棕/深绿而非纯黑**，线条有轻微顿挫和粗细变化 |
| 上色与质感 | **水彩 + 广告颜料**，纸纹可见，色块边缘有水痕；人物简洁扁平，**背景繁复**——这个反差是吉卜力的核心特征 |
| 背景与景深 | 背景是完整的水彩画：草叶逐片绘制、云有体积、远山有空气透视。**景深极浅或几乎没有**，远近都清晰 |
| 光效处理 | 柔和漫射为主，午后斜光穿过树叶形成斑驳光点；无强对比、无镜头光斑 |
| 运动规律 | **24fps 全动画**（关键戏），日常段落 12fps；风、水、草叶必须持续微动 |
| 摄影机行为 | 大量**静止长镜与缓慢横摇**，留出"间 ma"——**画面里必须有 1–2 秒什么都不发生**的呼吸段落 |
| 色彩体系 | 自然高饱和绿（黄绿→墨绿多层）、天空青蓝、云白偏暖，泥土赭石 |
| **头号翻车点** | 背景画得和人物一样简单 → 变成廉价日常番。吉卜力的钱全花在背景上 |

**锚点句**
> 吉卜力式手绘水彩动画，人物线条简洁扁平，背景为繁复水彩风景（逐片绘制的草叶、有体积感的积云），午后斜光穿过树叶洒下斑驳光点，24fps 全动画，摄影机静止长镜，画面中留有两秒无事发生的呼吸段落。
> `Studio Ghibli-style hand-painted watercolor animation, simple flat character linework against a densely painted watercolor landscape, individually painted grass blades and volumetric cumulus clouds, dappled afternoon sunlight through leaves, 24fps full animation, locked-off long take with a two-second breathing pause.`

---

## 4. 新海诚超写实光晕 Makoto Shinkai

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 人物线条细而干净，接近赛璐璐；但**背景无线条**，纯绘画堆叠 |
| 上色与质感 | 背景达到**照片级密度**：每片瓦、每根电线、每块玻璃反射都单独画；人物仍是 2–3 阶 cel |
| 背景与景深 | 天空占画面 40%–60%，云层分 3–5 层；玻璃、水面、金属必反射环境 |
| 光效处理 | **镜头光斑 lens flare + 光晕 bloom + 光线丢失 light leak 三件套**，逆光几乎每镜都有；雨滴挂在玻璃上折射背景 |
| 运动规律 | 人物 on twos/threes，但**光与粒子层 24fps 连续变化**——这是"活"的来源 |
| 摄影机行为 | 大量仰拍天空、缓慢升降、视差多层滚动（parallax scrolling） |
| 色彩体系 | **高饱和青蓝 × 暖橙**的强对比，紫色过渡带；黄昏与雨后是主场 |
| **头号翻车点** | 只写"新海诚风格"不写光斑与天空 → 退化成普通日常番。天空和光晕才是签名 |

**锚点句**
> 新海诚式超写实动画，黄昏天空占据画面上半部，五层积云带暖橙边缘，强逆光产生镜头光斑与柔和光晕，雨滴挂在玻璃上折射城市灯光，青蓝与橙色高饱和对比，多层视差缓慢横移。
> `Makoto Shinkai-style hyper-detailed anime, dusk sky filling the upper half with five layers of cumulus rimmed in warm orange, strong backlight producing lens flare and soft bloom, raindrops on glass refracting city lights, saturated teal-and-orange contrast, slow multi-layer parallax pan.`

---

## 5. 京都动画式日常 Kyoto Animation

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 极细、极稳定的线，几乎无抖动；睫毛与发丝分股绘制 |
| 上色与质感 | cel 基底但**多加一阶**（3–4 阶），肤色带极淡的红晕过渡；布料有褶皱阴影 |
| 背景与景深 | **真实空间透视**（教室、走廊、车站都按实景取材建模），有**模拟浅景深**：前景课桌虚化、后景窗户虚化 |
| 光效处理 | 细腻自然光影：窗棂投影随时间移动、逆光下发梢通透、灰尘颗粒在光柱中漂浮 |
| 运动规律 | 12–24fps 混用，**微表情与小动作是重点**：手指绞衣角、视线偏移、呼吸起伏 |
| 摄影机行为 | 大量**低机位、模拟真实焦段**（50mm/85mm 观感），轻微手持感，浅焦追随 |
| 色彩体系 | 中低饱和、明亮通透，米白/浅木/天蓝为主，避免重色 |
| **头号翻车点** | 用了大动作大情绪 → 京阿尼的力量在"什么都没发生的一秒"，动作太大就变成普通热血番 |

**锚点句**
> 京都动画式日常动画，午后教室，窗棂投影落在课桌上，灰尘在光柱中漂浮，人物三阶柔和上色、发梢逆光通透，模拟 85mm 浅景深虚化前景课桌，镜头低机位缓慢推近，只有手指绞动衣角的微小动作。
> `Kyoto Animation-style slice-of-life anime, afternoon classroom, window-frame shadows across the desks, dust motes floating in the light shaft, three-tone soft cel shading with translucent backlit hair tips, simulated 85mm shallow focus blurring the foreground desk, low-angle slow push-in, the only motion being fingers twisting a shirt hem.`

---

## 6. 押井守 / 攻壳式赛博动画 Oshii-style Cyber Anime

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 线条硬、写实，机械部件用工程图级密度的细线；人物线条冷峻无萌化 |
| 上色与质感 | **低饱和青灰**为基底，金属有脏污与氧化层，混凝土有水渍；cel 阶数少但影色极重 |
| 背景与景深 | 街景密度极高（招牌、管线、电缆、涂鸦层层堆叠），**写实单点/两点透视**，广角变形 |
| 光效处理 | 阴天漫射 + 霓虹点光源；**水面倒影是核心视觉**，湿地面把光源拉成竖条 |
| 运动规律 | **刻意的低运动量**：大量静止画面 + 局部微动（雨、水波、飘带、鸽子） |
| 摄影机行为 | **静止长镜 8–15 秒**，或极缓慢横摇；无快速剪辑，节奏近似纪录片 |
| 色彩体系 | 青灰 / 墨绿 / 铁锈褐，饱和度压到 40%–55%，仅霓虹点缀高饱和 |
| **头号翻车点** | 加了快速剪辑和热血打斗 → 押井守的气质来自"停下来看城市"，节奏一快风格立刻消失 |

**锚点句**
> 押井守式写实赛博动画，雨后亚洲街区，招牌与电缆层层堆叠，湿地面把霓虹拉成竖条倒影，低饱和青灰色调，摄影机完全静止长镜十秒，只有雨滴与水面涟漪在动。
> `Mamoru Oshii-style realist cyberpunk anime, rain-soaked Asian street, dense layers of signage and overhead cables, neon smeared into vertical reflections on wet asphalt, desaturated teal-grey palette, locked-off ten-second static take, only rain and ripples moving.`

---

## 7. 皮克斯 / 迪士尼 3D Pixar-Disney CG

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **无线条**，全靠体积与光影造型；轮廓走**圆润造型语言**（圆、蛋形、无锐角） |
| 上色与质感 | 皮肤有**次表面散射 SSS**（耳朵与鼻翼透红光），布料有绒毛，材质干净无脏污 |
| 背景与景深 | 全 3D 场景 + **全局光照 GI**，中等景深（f/2.8–f/5.6 等效），背景清晰可读 |
| 光效处理 | 三点布光 + 环境光遮蔽 AO + 柔和反弹光；**主角脸上永远有一块干净的柔光** |
| 运动规律 | 24fps 全动画，遵循**挤压拉伸 squash-and-stretch、预备动作 anticipation、跟随与重叠 follow-through** |
| 摄影机行为 | 虚拟摄影机模拟真实器材（含轻微手持与镜头呼吸），运镜克制、构图工整 |
| 色彩体系 | 明亮饱和、色彩脚本 color script 驱动，一场戏一个主色调 |
| **头号翻车点** | 角色比例写实化 → 立刻掉进恐怖谷。皮克斯脸必须是**大眼睛、小下巴、圆颅顶**的夸张比例 |

**锚点句**
> 皮克斯式 3D 动画电影画面，角色为大眼睛圆润造型比例，皮肤有次表面散射透光感，全局光照与柔和反弹光，材质干净，虚拟摄影机缓慢推入，明亮高饱和色彩脚本。
> `Pixar-style 3D animated feature frame, stylized character with large eyes and rounded proportions, subsurface scattering in the skin, global illumination with soft bounce light, clean materials, slow virtual camera push-in, bright saturated color script.`

---

## 8. 梦工厂式 3D DreamWorks CG

> 与皮克斯同为 3D，差别在**三个刻度**：角色变形更夸张、运镜更电影化、光更硬。

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 无线条，但造型允许**尖锐与不对称**（鹰钩鼻、方下巴、极端体型差） |
| 上色与质感 | SSS + 更强的材质细节（毛发根数、皮革磨损、金属划痕），比皮克斯"脏"一档 |
| 背景与景深 | 更浅的景深与更长焦的构图，**背景常压暗做戏剧性减法** |
| 光效处理 | **硬光 + 高对比**，光比可达 6:1–8:1；大量边缘光勾人物轮廓 |
| 运动规律 | 24fps，变形幅度更大（表情可拉到极端），动作节奏更快更"弹" |
| 摄影机行为 | **强烈的电影级运镜**：低角度冲刺跟拍、快速环绕、虚拟长焦压缩 |
| 色彩体系 | 对比更强，冷暖分区明确（冷环境 + 暖人物） |
| **头号翻车点** | 光打得太柔 → 立刻变回皮克斯。梦工厂的辨识度在硬光与高对比 |

**锚点句**
> 梦工厂式 3D 动画，角色造型夸张不对称，硬光高对比光比 6:1，边缘光勾出轮廓，虚拟长焦低角度快速跟拍冲刺，背景压暗两档。
> `DreamWorks-style 3D animation, exaggerated asymmetric character design, hard key light at 6:1 contrast ratio, strong rim light separating the silhouette, low-angle telephoto tracking sprint, background two stops down.`

---

## 9. Spider-Verse 混合风 Comic-Book Hybrid

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **手绘感墨线叠在 3D 模型上**，线条有断续与粗细变化；阴影处加**交叉排线 hatching** |
| 上色与质感 | **半调网点 halftone dots** 作为阴影与渐变的替代；**印刷套色错位 chromatic offset**（红青边缘偏移 2–4px） |
| 背景与景深 | 景深不用光学模糊，而用**色差分离 + 网点放大**表现"虚"——这是签名做法 |
| 光效处理 | 光斑用漫画式放射线与实心色块表示；霓虹用纯色叠加而非物理发光 |
| 运动规律 | **变帧率是灵魂**：新手角色 on twos（12fps），成熟/高速时切到 on ones（24fps）；同一镜内可混用 |
| 摄影机行为 | 极端广角 + 荷兰角 + 突然的画幅内分格（split panel）；**漫画拟声词与速度线直接绘制进画面** |
| 色彩体系 | 高饱和撞色（洋红 × 青 × 荧光黄），大面积纯色块，不追求自然 |
| **头号翻车点** | 配上写实皮肤质感与真实 GI → 网点和错位失去依托，画面变成"打了滤镜的 3D"。**必须放弃写实肤质** |

**锚点句**
> Spider-Verse 式漫画混合动画，3D 模型上叠手绘墨线与交叉排线，阴影用半调网点表现，红青套色错位偏移，角色动作以每秒 12 张为主并在冲刺时切到 24 张，画面内出现速度线与拟声词，洋红与青的高饱和撞色。
> `Spider-Verse-style comic hybrid animation, hand-inked outlines and cross-hatching over 3D geometry, halftone dot shading, red-cyan chromatic offset misregistration, characters animated on twos switching to ones during the dash, in-frame speed lines and onomatopoeia, saturated magenta-and-cyan palette.`

---

## 10. 美式 TV 卡通 Cartoon Network Style

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **粗黑轮廓线**（3–5px 等效），粗细统一，造型高度简化为几何形 |
| 上色与质感 | **纯平涂色块，无阴影或仅一块硬阴影**；无质感、无纹理 |
| 背景与景深 | 极简背景：几个色块 + 一条地平线；**无景深**，全画面同焦 |
| 光效处理 | 基本不做光效；需要"发光"时直接画一圈同心亮色环 |
| 运动规律 | 有限动画，8–12fps，靠**极端变形与形变过渡**制造喜感，不追求物理正确 |
| 摄影机行为 | 摄影机几乎不动，构图正面化；转场用硬切或圈入圈出 |
| 色彩体系 | 有限调色板（8–16 色），高明度、糖果色，色块之间对比明确 |
| **头号翻车点** | 加了柔和阴影或渐变 → 立刻失去"卡通"的干脆感，变成廉价 flash 动画 |

**锚点句**
> 美式电视卡通风格，粗黑轮廓线，纯平涂色块无渐变，极简背景仅有色块与地平线，角色造型高度几何化并做极端夸张变形，有限调色板糖果色，摄影机固定正面构图。
> `American TV cartoon style, thick black outlines, flat solid color fills with no gradients, minimal background of color blocks and a horizon line, geometric character shapes with extreme squash-and-stretch, limited candy-colored palette, locked frontal camera.`

---

## 11. 迪士尼二维手绘黄金期 Disney Hand-drawn Golden Age

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **Xerox 转印线条**：铅笔感、略毛躁、粗细有变化，不是数码平滑线 |
| 上色与质感 | 赛璐璐片正面上色 + **水彩/水粉手绘背景**；人物色平、背景有笔触 |
| 背景与景深 | 多平面摄影机 multiplane 制造纵深，前中后景以不同速度移动 |
| 光效处理 | 手绘光影：投影为整块色形，高光是画上去的亮色块；烛光/火光靠色相偏移表现 |
| 运动规律 | **24fps 全动画**，大量参考 rotoscope 真人素材，运动弧线圆润、重心可信 |
| 摄影机行为 | 缓慢推拉 + 多平面横移；镜头运动服务于场面调度，不炫技 |
| 色彩体系 | 中高饱和、偏暖，背景比人物低一档饱和以突出角色 |
| **头号翻车点** | 用数码平滑线 → 丢掉手绘温度。必须显式写"铅笔质感线条、赛璐璐片、手绘水彩背景" |

**锚点句**
> 迪士尼黄金期二维手绘动画，铅笔质感的 Xerox 转印线条，赛璐璐平涂人物配手绘水彩背景，多平面摄影机制造纵深，24fps 全动画，运动弧线圆润且重心可信。
> `Golden-age Disney hand-drawn 2D animation, textured Xerox pencil linework, flat cel-painted characters over hand-painted watercolor backgrounds, multiplane camera depth, 24fps full animation with rounded arcs and believable weight.`

---

## 12. 定格动画 / 黏土 Stop-Motion & Claymation

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 无线条，实体模型的真实轮廓；边缘有毛边、纤维、指纹 |
| 上色与质感 | **材质瑕疵就是卖点**：黏土指纹、毛毡起球、纸板毛边、缝线痕迹；表面哑光不反光 |
| 背景与景深 | 微缩布景，**微距浅景深**（等效 f/2.8–f/4，微缩尺度下景深极浅），远景快速虚化 |
| 光效处理 | **实体灯具布光 → 硬阴影边缘清晰**，投影方向单一且不变；有真实灰尘与光斑 |
| 运动规律 | 逐帧拍摄，**on twos（12fps）为主**，带轻微不规则抖动 stop-motion judder；这种"不完美"是真实性证据 |
| 摄影机行为 | 摄影机受微缩布景限制：多为**缓慢直线滑轨或固定机位**；快速自由运镜会立刻穿帮 |
| 色彩体系 | 实拍色彩，饱和度中等；常做低对比复古调 |
| **头号翻车点** | 写了"丝滑流畅的运动/流畅运镜" → 抹掉 judder 和实体感，退化成普通 3D。**必须保留抖动** |

**锚点句**
> 定格黏土动画，可见黏土指纹与布料纤维的实体模型，微缩布景微距浅景深，实体灯具产生边缘清晰的硬阴影，逐帧拍摄每秒 12 张并带有轻微不规则抖动，摄影机沿直线滑轨缓慢移动。
> `Stop-motion claymation, practical puppets with visible clay fingerprints and fabric fibers, miniature set with macro shallow depth of field, hard-edged shadows from practical lights, shot on twos at 12fps with subtle stop-motion judder, slow straight dolly move.`

---

## 13. 中国水墨动画 Chinese Ink Wash

> **禁止写"国风韵味"**。它必须被翻译成：**大面积留白 + 单一自然光源 + 青绿与赭石 + 前景枝叶遮挡 + 墨色浓淡分层**。

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **无轮廓线**。形体由墨块的浓淡边界直接构成，边缘有宣纸**晕染 bleed** |
| 上色与质感 | 墨分五色（焦/浓/重/淡/清）——实操按**五阶灰度**控制；设色仅青绿、赭石、朱砂三色点缀 |
| 背景与景深 | **留白即背景**，画面 40%–60% 为空白宣纸；纵深靠墨色变淡表示，不靠虚化 |
| 光效处理 | **无光源概念、无投影、无高光**。明暗只等于墨的浓淡 |
| 运动规律 | 极简运动，12fps 或更低；主体动，背景几乎静止；水与云用墨迹缓慢晕开表示 |
| 摄影机行为 | 缓慢横摇（模拟手卷展开）或固定；**禁止推拉变焦与环绕** |
| 色彩体系 | 单色墨 + 极少设色，饱和度 ≤ 25% |
| **头号翻车点** | 叠加高饱和色彩或霓虹 → 墨的层次被彻底吃掉，画面直接糊成脏色块 |

**锚点句**
> 中国水墨动画，无轮廓线，形体由浓淡五阶墨色构成，边缘在宣纸上自然晕染，画面半数留白，仅以青绿与赭石极少设色，无投影无高光，前景一枝墨竹入画遮挡，摄影机如手卷般缓慢横向展开。
> `Chinese ink-wash animation, no outlines, forms defined by five tonal values of ink bleeding softly into rice paper, half the frame left as empty white space, minimal mineral green and ochre accents, no cast shadows and no highlights, a branch of ink bamboo overlapping the foreground, slow horizontal pan like a handscroll unrolling.`

---

## 14. 剪纸 / 皮影 Paper-cut & Shadow Puppetry

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **硬边剪影**，边缘为刀切的锐利折线；镂空处透光形成图案 |
| 上色与质感 | 纸张/皮革**纤维质感**可见，半透明材质在逆光下呈现色彩；无渐变 |
| 背景与景深 | **平面层叠**：前中后三到五层平行纸片，层间有细微投影分隔；无真实纵深 |
| 光效处理 | **逆光透射 backlit translucency** 是唯一光源逻辑：光从幕布后打来，材质厚处暗、薄处亮 |
| 运动规律 | 关节式转动（肩、肘、膝为铰接点），8–12fps，运动为**刚体旋转与平移**，无形变 |
| 摄影机行为 | **横向平移调度**为主，角色左进右出；摄影机与幕布始终平行，禁止斜角与环绕 |
| 色彩体系 | 高饱和透光色（朱红、明黄、靛蓝、翠绿）+ 纯黑剪影 |
| **头号翻车点** | 让角色做三维转身 → 剪纸只有正侧两面，一转身模型就编不下去，画面塌陷 |

**锚点句**
> 皮影戏风格动画，硬边剪影角色由铰接关节驱动，光线从幕布后方逆向透射，半透明皮革呈现朱红与靛蓝，可见纤维纹理，三层平面纸片层叠制造纵深，角色沿水平方向平移进出画面，摄影机与幕布严格平行。
> `Shadow-puppet style animation, hard-edged silhouettes with articulated joints, strong backlight transmitting through translucent leather in vermilion and indigo, visible fiber texture, three stacked flat paper layers for depth, characters sliding horizontally in and out of frame, camera locked parallel to the screen.`

### 14b. Vox 剪纸拼贴（知识/科普/数据视频首选）

不同于皮影的「逆光透射剪影」，Vox 是**正面受光的哑光拼贴**：扁平实色纸贴（flat solid-color paper cutout sticker）、锐利切边与投影、明显纸层堆叠、高反差、干净矢量细节，带「流体延时 + 定格纸感」动画。适合做知识讲解、数据对比、信息图、新闻时间线——**结构与数据表达见 `references/vox-knowledge.md`**，该文件专补「知识性视频」的表达方式路由、叙事弧、数据视觉层、固定运镜序列与自检清单。

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **硬边切边**（die-cut outline），纸贴有可见厚度与投影；非剪影 |
| 上色与质感 | **哑光实色纸面**（matte），无渐变、无光滑 3D；可带轻微纸纤维 |
| 背景与景深 | **平面层叠 + 语义功能**：前中后纸层，背景必须承载场景/数据底板/路径，禁止无意义的满屏色碎 |
| 光效处理 | 正面柔向光（soft directional lighting），非逆光；保持定格纸感、稳定不闪烁 |
| 运动规律 | 流体延时动画 + 定格纸纹触感；避免照片写实/3D 纵深 |
| 摄影机行为 | 连续贯穿运镜（push_in / pan / layer_dissection / parallax），服务于主体与信息揭示 |
| 色彩体系 | 珊瑚红 `#E8625C` / 哑光青蓝 `#2B697A` / 芥末琥珀 `#E5A93C` / 奶油纸白 `#FAF9F5` / 深炭灰 `#2D2D2D`（Hex 仅作不可见生成控制） |
| **头号翻车点** | 把 Hex 色值/色号渲染成画面可见文字；背景铺满无关彩色碎纸；无声视频却写旁白台词 |

**锚点句**
> Vox 风格剪纸拼贴动画，哑光实色纸贴角色与物体，硬边切边与锐利投影，明显纸层堆叠，高反差干净矢量细节，流体延时动画带定格纸感，正面柔向光，稳定不闪烁。
> `Vox style paper-cut collage art, stylized minimal flat solid-color paper cutout stickers with sharp die-cut outlines and crisp drop shadows, obvious paper layer stacking, high contrast clean vector details, fluid time-lapse animation with stop-motion paper texture feel, soft directional lighting, stable non-flickering.`

---

## 15. 像素艺术 / Low-poly Pixel Art & Low-poly

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | **像素级硬边阶梯**，轮廓由单像素深色描边构成；low-poly 则为可见的三角面边界 |
| 上色与质感 | **有限调色板**（16–32 色为典型），用**抖动 dithering** 棋盘点阵模拟渐变，绝无平滑过渡 |
| 背景与景深 | **分辨率网格锁定**（如 320×180 或 480×270 后放大），背景同样网格化；纵深靠明度分层 |
| 光效处理 | 光是"另一块颜色"，不是渐变；发光用同心色环 + 抖动边缘 |
| 运动规律 | **位移必须整像素对齐**，6–12fps 帧动画；角色行走为 4–8 帧循环 |
| 摄影机行为 | 整像素步进的横向卷轴或固定机位；**任何亚像素平滑移动都会产生抖动糊边** |
| 色彩体系 | 有限调色板、高对比、色相跳跃明显 |
| **头号翻车点** | 加了浅景深虚化或运动模糊 → 像素网格被插值抹平，直接变成"糊掉的低清视频" |

**锚点句**
> 像素艺术动画，320×180 分辨率网格锁定后整数倍放大，16 色有限调色板，棋盘抖动模拟渐变，单像素深色描边，硬边阶梯无抗锯齿，角色为 8 帧行走循环，摄影机整像素步进横向卷轴，无景深虚化无运动模糊。
> `Pixel-art animation, locked 320×180 pixel grid upscaled with nearest-neighbor, 16-color limited palette, checkerboard dithering instead of gradients, single-pixel dark outlines, aliased hard edges, 8-frame walk cycle, camera scrolling in whole-pixel steps, no depth-of-field blur and no motion blur.`

---

## 16. CGI 写实渲染 + 转描/油画动画 Photoreal CGI & Rotoscope-Painterly

> 两种"极端相反的完美度"合并成一节：一个**过分干净**，一个**过分抖动**。

### 16A · CGI 写实渲染 Photoreal CGI（产品级）

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 无线条，边缘由光线追踪的反射与折射定义 |
| 上色与质感 | PBR 材质：金属**各向异性 anisotropic** 拉丝高光、玻璃色散、液体折射率 1.33、涂层清漆层 |
| 背景与景深 | 纯色/渐变无限背景，或 HDRI 环境；景深等效 f/4–f/8，主体全清晰 |
| 光效处理 | **HDRI 环境光 + 柔光箱反射条**，光线追踪反射与焦散 caustics |
| 运动规律 | 24–60fps 绝对平滑，无抖动、无重量误差 |
| 摄影机行为 | 完美的机械轨道：匀速环绕、垂直升降、零抖动 |
| 色彩体系 | 中性精准，品牌色严格还原 |
| **头号翻车点** | "太完美"既是卖点也是破绽——拍**产品**时是加分项，拍**人物**时直接掉进恐怖谷。人物慎用 |

**锚点句**
> 产品级 CGI 写实渲染，光线追踪反射与焦散，HDRI 环境照明配柔光箱条形反射，金属表面各向异性拉丝高光，无限渐变背景，摄影机匀速零抖动环绕，画面绝对干净无颗粒。
> `Product-grade photorealistic CGI render, ray-traced reflections and caustics, HDRI environment lighting with softbox strip reflections, anisotropic brushed-metal specular, infinite gradient backdrop, perfectly smooth constant-speed orbit, absolutely clean and grain-free.`

### 16B · 转描 / 油画动画 Rotoscope & Painterly

| 维度 | 参数 |
|---|---|
| 线条与轮廓 | 手绘线覆盖真人运动轨迹，轮廓**逐帧微动**；油画版本无线条，靠笔触边界成形 |
| 上色与质感 | 厚涂笔触可见（油画刀痕/油彩堆叠），每帧笔触位置重画 |
| 背景与景深 | 背景与人物同为绘画，笔触密度一致；无光学景深 |
| 光效处理 | 光影是"色块的冷暖差"，非物理计算；高光是一笔亮色 |
| 运动规律 | **沸腾 boil 是签名**：每帧重绘导致轮廓与笔触持续抖动，12fps 时最明显 |
| 摄影机行为 | 沿用被转描素材的原始运镜（因此可以有真实手持感） |
| 色彩体系 | 高饱和主观用色，冷暖对比强烈，允许非自然色 |
| **头号翻车点** | 写"稳定平滑的线条" → 杀掉 boil，风格立即消失。**必须显式要求逐帧抖动** |

**锚点句**
> 转描油画动画，真人运动被逐帧手绘覆盖，可见厚涂油彩笔触，每帧重绘导致轮廓持续沸腾抖动，12fps，光影以冷暖色块表现而非物理明暗，高饱和主观用色。
> `Rotoscoped painterly animation, live-action motion hand-painted frame by frame, visible thick oil-paint brushstrokes, constant boiling of contours from per-frame repainting, 12fps, light rendered as warm-cool color blocks rather than physical shading, saturated subjective palette.`

---

## 画风 × 题材 组合矩阵

| 题材 | 首选画风 | 为什么成立 | 关键参数一句话 |
|---|---|---|---|
| 温情 / 亲情 | **吉卜力手绘** | 繁复自然背景 + 留白呼吸，让情绪有地方沉淀 | 24fps 全动画、静止长镜、斜光穿树叶 |
| 科幻 / 反乌托邦 | **押井守赛博** | 低饱和 + 静止长镜 = 冷峻的世界观压迫感 | 青灰 45% 饱和、静止 10s、湿地面倒影 |
| 产品 / 电商 | **CGI 写实渲染** | 需要材质可信与品牌色精准，"太完美"是加分项 | 光追反射、HDRI、匀速环绕、零颗粒 |
| 恐怖 / 悬疑 | **定格动画** | 实体材质 + judder 抖动 = 天然的不适感与恐怖谷 | 12fps 抖动、硬阴影、微距浅景深 |
| 动作 / 超英 | **Spider-Verse** | 变帧率与速度线把打击感直接可视化 | 12↔24fps 切换、半调网点、红青错位 |
| 喜剧 / 搞笑 | **美式 TV 卡通** | 极端形变 + 平涂色块，节奏可以快到不讲物理 | 粗黑线、8fps、极端 squash-stretch |
| 青春 / 校园 | **京都动画式** | 微表情与自然光影承载"没说出口的话" | 三阶柔和上色、85mm 浅焦、窗棂投影 |
| 灾难 / 天象奇观 | **新海诚式** | 天空是主角，光晕与云层撑起震撼 | 五层云、lens flare、青蓝×暖橙 |
| 传统文化 / 诗意 | **中国水墨** | 留白与墨阶取代布景与打光，成本最低、气质最独 | 五阶墨、50% 留白、无投影、缓慢横摇 |
| 儿童 / 家庭 | **皮克斯 3D** | 圆润造型 + SSS 皮肤，天生的亲和度 | 大眼圆颅、GI 柔和反弹、明亮色彩脚本 |
| 民间故事 / 寓言 | **剪纸皮影** | 铰接式平面调度，天然带"讲古"的距离感 | 逆光透射、三层纸片、水平进出画 |
| 复古游戏 / 亚文化 | **像素艺术** | 网格与有限调色板本身就是年代符号 | 320×180 网格、16 色、抖动、整像素移动 |
| 热血 / 战斗番 | **日式赛璐璐** | 有限动画把资源集中在冲击帧上，性价比最高 | 8fps 保持、硬色阶、逆光亮边、速度线 |
| 冒险 / 奇幻长片 | **梦工厂 3D** | 硬光高对比 + 电影级运镜撑住史诗尺度 | 光比 6:1、边缘光、长焦低角度跟拍 |

---

## ⚠️ 画风禁忌（叠一起模型必糊）

| 禁忌组合 | 冲突根源 | 会得到什么 | 正确做法 |
|---|---|---|---|
| 水墨 + 高饱和霓虹 | 墨的信息量全在**浓淡五阶**上，高饱和色直接吃掉灰阶 | 脏色块、笔触消失 | 水墨只配青绿/赭石/朱砂点缀，饱和度 ≤ 25% |
| 像素 + 浅景深虚化 | 虚化需要**亚像素插值**，与网格锁定互斥 | 糊掉的低清视频，像素感全无 | 像素风一律全画面同焦，纵深靠明度分层 |
| 定格 + 丝滑运镜 | 定格的真实性来自**逐帧不完美**，丝滑等于抹掉证据 | 廉价 3D 观感 | 保留 12fps judder，运镜限直线滑轨 |
| 赛璐璐 + 真实全局光 | cel 的硬色阶分界与 GI 的连续渐变**在着色上互相抵消** | 塑料感 3D 卡通 | 光效只用叠加发光图层 + 逆光亮边 |
| Spider-Verse + 写实肤质 | 半调网点与套色错位需要**平面色块**作依托 | 打了滤镜的普通 3D | 放弃 SSS 与毛孔，肤色改为 2–3 块平涂 |
| 吉卜力 + 强烈镜头光斑 | 光斑是**光学产物**，手绘水彩世界里没有镜头 | 风格分裂、像后期特效 | 要光晕就改用新海诚风；吉卜力只用斑驳树影 |
| 皮影 + 三维环绕运镜 | 剪纸只有正侧两面，**没有第三个面可转** | 角色一转身就塌陷/变形 | 摄影机与幕布严格平行，只做水平平移 |
| 美式卡通 + 柔和渐变阴影 | 平涂的干脆感依赖**零渐变** | 廉价 flash 动画 | 阴影最多一块硬边色，或干脆不要 |
| 两种画风并列写 | 模型取平均值，两边特征都被削弱 | 谁都不像的糊面 | 一条片子只锁一种；要混合就写已定义的混合风 |

---

## 日式 vs 美式动画的六个根本差异

> 这六条是**同一个动作在两套体系里的不同拍法**。写提示词时逐条二选一，不要混。

| # | 维度 | 日式 | 美式 |
|---|---|---|---|
| 1 | **帧率策略** | 有限动画，8fps 保持 + 冲击帧发力 | 全动画，24fps 连续，每帧都在动 |
| 2 | **明暗方式** | 硬色阶分界 cel shading，2–3 阶 | 连续渐变 + 全局光照，无分界线 |
| 3 | **背景繁复度** | 背景精细度**高于**人物，钱花在美术上 | 背景与人物同级或更简，钱花在动作上 |
| 4 | **角色变形幅度** | 造型稳定，靠表情符号与光效表达情绪 | 挤压拉伸幅度大，身体本身就是表情 |
| 5 | **摄影机自由度** | 以平移/推拉为主的二维调度 | 3D 空间自由环绕、俯冲、长焦压缩 |
| 6 | **光效逻辑** | 逆光亮边 + 叠加发光图层（画上去的光） | 物理光照 + 反弹光 + AO（算出来的光） |

**逐条中英对照写法**

1. 日 `limited animation held on threes, 8 drawings per second` ／ 美 `full animation on ones, 24fps continuous motion`
2. 日 `hard-edged two-tone cel shading` ／ 美 `smooth gradient shading with global illumination`
3. 日 `simple flat characters against a densely detailed painted background` ／ 美 `characters and environment at matched detail level`
4. 日 `stable character proportions, emotion carried by expression and lighting` ／ 美 `extreme squash-and-stretch, the whole body deforms`
5. 日 `2D staging with horizontal pans and push-ins` ／ 美 `free 3D virtual camera orbiting and diving through space`
6. 日 `painted rim light and additive glow layers` ／ 美 `physically-based lighting with bounce light and ambient occlusion`

**选择口诀**：要**气氛与克制**选日式，要**动作与体积**选美式。中间地带不存在——模型会把它渲成"3D 感的日漫"，这是最难看的失败态。
