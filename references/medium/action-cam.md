# 介质语法手册 · 运动相机 / FPV Action Cam & FPV

> **一句话定性**：运动相机卖的不是画面，是**动能的第一人称传递**。观众要的不是"看见速度"，是**身体以为自己在动**。
> 所有决策都回到一个问题：**这个镜头会让人下意识收紧肩膀吗？**

**四条子路线（先选一条）**

| 路线 | 载体 | 核心快感 |
|---|---|---|
| **A · 头盔 / 胸挂 POV** | 人体 | 视线即镜头，肢体入画 |
| **B · FPV 穿越机** | 无人机 | 贴地贴物、俯冲穿孔 |
| **C · 车载 rig** | 车辆 | 低机位贴地速度感 |
| **D · 板载 / 杆载** | 滑雪板 / 冲浪板 / 自拍杆 | 第三人称跟随的"自我旁观" |

---

## 1. 介质签名 ×6（这一层的灵魂）

| 签名特征 | 物理成因 | 提示词写法 |
|---|---|---|
| **超广角全景深（第一签名）** | 等效 15–17mm、f/2.8、小传感器，超焦距覆盖 40cm→∞ | `ultra-wide 16mm equivalent, f/2.8, deep focus front to infinity, no bokeh` |
| **桶形畸变 / 地平线弯曲** | 超广角光学畸变，边缘直线外凸 | `barrel distortion, horizon bowing at the edges of frame` |
| **高帧率清晰运动** | 60–240fps 配短快门，几乎无运动模糊 | `120fps, short shutter, razor-crisp motion with almost no motion blur` |
| **近距离透视夸张** | 广角近摄，伸出的手/车头被拉大 | `extreme wide-angle proximity, the outstretched hand looming huge in frame` |
| **EIS 地平线锁定漂浮感** | 电子稳定 + horizon leveling，机身翻滚但画面不翻 | `electronic horizon lock, body rolling while the frame stays level, floating feel` |
| **镜头前的水滴 / 泥点** | 镜片直接暴露在介质中 | `water droplets and mud specks on the lens element, smearing highlights` |

**用法**：**第 1 条必写**。运动相机与电影镜头最快的区分就是"**没有虚化**"——一旦出现背景奶油化，介质感当场归零。

---

## 2. 画质参数

- **常用规格**：4K60 / 2.7K120 / 1080p240。写清楚：`shot at 2.7K 120fps`。
- **快门**：跟随高帧率，实际在 **1/240–1/1000**。**这不是电影的 180° 快门**，所以运动是"一格一格清晰"的，不是拖影的。这是运动相机最容易被忽略的签名。
- **动态范围**：约 **12 档**，但自动曝光偏保护中间调 → **天空常被削顶** `sky clipping to white`。
- **噪点与涂抹**：强降噪 + 强锐化 → 草地、雪面、水花的细节被抹成块 `smeared micro-detail in grass and spray, over-sharpened edges`。
- **压缩**：**80–120 Mbps H.265**，高细节高速运动时出现短暂 macroblocking。
- **色彩科学**：默认档过饱和、蓝青偏冷（天空与水被拉艳）；若走"素材感"用 flat log 再轻微还原 `punchy over-saturated cyan-blue sky` 或 `flat log profile, slightly lifted blacks`。
- **紫边**：强逆光边缘 `purple fringing on high-contrast backlit edges`。

---

## 3. 镜头与视角

- **等效焦段**：**15–17mm**（标准超广）；SuperView/拉伸模式约 **11–13mm**，画面两侧被横向拉长；Linear 模式约 **19–24mm**（畸变被算法拉平，但**边缘会有拉扯瑕疵**）。
- **光圈**：**固定 f/2.8**，无法改变。因此**没有景深控制这个变量**——不要在提示词里写 f/1.4 或浅景深。
- **常见机位高度**：
  - 头盔顶 **1.60–1.80m**（视线略高于真实眼位，这是 POV 的微妙不真实感）
  - 胸挂 **1.20–1.35m**（最有"身体感"，能看见手臂摆动）
  - 车头保险杠 / 底盘 **0.30–0.60m**（贴地速度感最强）
  - 自拍杆 / 板载 **0.60–1.00m**，杆长 0.5–1.2m
  - FPV **0.15m 贴地 → 60m 高**，全程连续变化
- **主观性建立**：**肢体必须入画**。手、把手、滑雪板尖、车头引擎盖、马耳朵——`the rider's own hands on the handlebars in the lower frame`。没有肢体入画的 POV 只是"低机位广角",不是第一人称。

---

## 4. 运动特征

| 运动 | 具体描述 | 英文写法 |
|---|---|---|
| **FPV 俯冲 dive** | 从高处垂直下坠贴近地面再拉平，速度 40–120km/h | `FPV drone dive, plunging vertically down a cliff face then leveling out inches above the ground` |
| **FPV 穿孔 gap** | 穿过窗框/树缝/桥洞，间隙 0.5–2m | `threading a gap, flying through a broken window frame at speed` |
| **FPV 贴物飞行** | 距地面/墙面 **5–50cm** 的 proximity flying | `proximity flying, skimming 20cm above the water surface` |
| **FPV 翻滚** | power loop、split-S、roll，画面完整翻转 360° | `power loop, full 360° roll, horizon rotating completely` |
| **头盔转头** | 视线转动 **60–90°/s**，带轻微过冲 | `head turn whipping 70° with a slight overshoot` |
| **车载高频振动** | 路面激励 **15–40Hz**，过坎时整帧垂直冲击 | `constant high-frequency chassis vibration, hard vertical jolt over a bump` |
| **步态 / 板感** | 跑动 2.5–3Hz 起伏；转弯时机身随重心侧倾 | `body-mounted bounce with each stride, camera banking with the rider's lean` |

**绝对禁用**：`dolly`、`steadicam`、`crane`、`smooth cinematic tracking`、`slow graceful aerial drift`。
**理由**：FPV 与运动相机的价值就是**平滑的反面**。写进 steadicam，就变成了一条平庸的航拍。

---

## 5. 光线现实

- **只有自然光/现场光**，且**全自动曝光**，无人干预。
- **户外日光 5200–6500K**；阴天/雪地 **6500–7500K**；黄金时刻 **3200–4000K**。
- **曝光泵动**：穿过隧道、林荫、门洞时 AE 在 **0.3–0.5s** 内急剧调整 → `exposure pumping as the camera passes into the tunnel, image darkening then rebalancing`。
- **超广角必吃到天空** → 天空过曝是常态，不要试图"保住高光"。
- **强反射面**：雪地、水面、湿路面造成大面积高光溢出与镜头眩光 `sun flaring directly into the wide lens, veiling glare across frame`。
- **夜间基本不可用**：小传感器 + f/2.8 → 噪点爆炸。若必须夜拍，靠**头灯/车灯 3000–4000K 的近距离光锥**，画面其余部分全黑 `helmet light cone 3500K carving a tunnel of light, everything outside it pure black`。

---

## 6. 节奏与时长

- **ASL 1.5–4.0s**，但这是"剪辑版"的数据。
- **FPV 的正确答案是一镜到底**：10s **1 镜**。穿越机的价值在于**空间连续性**——一剪，动能就断了。
- **POV / 车载**：10s **≤ 4 镜**，且每镜至少 2s，让观众有时间"进入身体"。
- **结构建议（10s）**：
  ```
  0–2s   建立位置与肢体入画      1 镜，2.0s
  2–6s   核心动能（俯冲/穿孔/加速） 1 镜连续，4.0s
  6–8.5s 极限贴近点（离物 <50cm）  同镜或 1 镜，2.5s
  8.5–10s 拉开/冲出，视野突然开阔  1.5s
  ```
- **升格用法**：只给**腾空/水花/雪雾**这类瞬间，且 **1/4 (120fps) 足够**。整片升格会杀死速度感——**慢动作的运动相机不再传递动能**。

---

## 7. 声音特征

- **风噪压过一切**：相对风速 >2m/s 即产生持续宽频轰鸣与麦克风削顶 `overwhelming wind roar and mic clipping`。这是最强的速度证据，**不要清理掉**。
- **机身共振**：塑料外壳在振动下的低频嗡鸣 `housing resonance rumble`。
- **介质摩擦音**：雪板刮擦、轮胎滚动、水花拍击、链条与齿轮。
- **FPV 电机啸叫**：**高频 200–400Hz 随油门变化**的电机声（若为机载录音） `high-pitched motor whine rising and falling with throttle`。
- **人声**：几乎不可用，喊叫被风噪削顶成失真 `shouts distorted and clipped by wind`。
- **常见后期做法**：整轨换成音乐 + 保留少量风噪层。若要"原始素材感"，则**全程只留风噪**。

---

## 8. 界面与叠加元素

| 元素 | 英文写法 |
|---|---|
| 录制状态 | `"REC ● 4K60" and battery icon in the corner` |
| 遥测叠加 | `telemetry overlay: speed 87 km/h, altitude 1420m, G-force 2.3` |
| GPS 轨迹条 | `GPS track map widget in the lower-left corner` |
| FPV 模拟图传干扰 | `analog VTX static, horizontal tearing, snow rolling across frame when signal weakens` |
| FPV OSD | `OSD crosshair with "11.8V  0:42" and RSSI bars` |
| 数字图传故障 | `digital link macroblocking and a brief frozen frame` |
| 镜片污染 | `water droplets beading on the lens, wiped away by airflow` |

**注意**：POV / 车载**不要**用时间戳水印（那是监控语言）；FPV 的图传雪花只在**模拟图传**设定下成立，数字图传是"糊一下再恢复"。

---

## 9. 翻车点 ×4

1. **太稳、太平滑（头号翻车）** → AI 默认会把 FPV 拍成一条**平稳优雅的航拍**：匀速平飞、缓慢环绕、地平线永远水平。这是最致命的失败。**必须显式写**：俯冲、翻滚、贴物 20cm、穿孔、速度数字，并显式禁用 `no steadicam, no smooth cinematic drift`。
2. **出现浅景深虚化** → f/2.8 超广角物理上不可能虚化背景。写 `deep focus, everything in focus, no bokeh`。
3. **平飞代替贴物** → 离地 30m 匀速前进 = 普通无人机。FPV 的灵魂是**离物越近越贵**：贴水 20cm、擦墙 50cm、穿窗 1m。
4. **没有肢体入画** → 没有手、没有把手、没有板尖，第一人称就不成立，只剩一个低机位广角。

**附加**：不要写"刺激的/惊险的/动感十足"这类主观词；改写成物理量（速度 km/h、离地 cm、翻滚角度、帧率）。

---

## 10. 与题材的正交组合

| 题材 | 叠加运动相机后的效果 | 关键调整 |
|---|---|---|
| **恐怖** | 从"被追"变成"我在被追" | 头盔 POV + 60fps + 剧烈转头过冲 + 头灯光锥外全黑；风噪与自己的喘息；镜头被树枝刮到 |
| **美食** | 从"英雄镜"变成"厨房里的一双手" | 胸挂 POV：手在下画幅切菜下锅；全景深看得见整个灶台；**放弃浅景深与逆光蒸汽**，靠动作节奏 |
| **产品** | 从"演示"变成"使用中的真实场景" | 车载/板载 rig 贴地 0.4m 拍产品在运动中；遥测叠加给"性能"背书；桶形畸变让产品显得更强悍 |
| **温情** | 从"旁观感动"变成"我陪你一起" | 胸挂低速：牵手入画、孩子在前方回头；降到 30fps 减少机械感；黄金时刻 3600K 软化冷硬的超广角 |
| **纪实 / 探索** | 从"介绍地方"变成"我带你钻进去" | FPV 一镜到底：从高空俯冲穿过窗户进入室内再穿出；空间连续性即叙事 |
| **动作 / 竞速** | 从"看比赛"变成"我在赛道上" | 头盔 + 车头双机位；120fps；曝光泵动过隧道；风噪不清理 |

---

## 11. 中英双语锚点句（可直接粘贴）

**中文 · FPV 穿越机**
> FPV 穿越机第一人称，等效 16mm 超广角 f/2.8，全景深，前后皆清晰、无任何虚化；2.7K 120fps 短快门，运动极其清晰几乎无拖影；桶形畸变，地平线在画面边缘外凸；从 40m 高处垂直俯冲而下，速度约 90km/h，在离地 30cm 处急拉平，贴着水面掠行并激起尾流；随即以侧滚穿过一扇破窗的 1.2m 缝隙，画面完整翻转，随后 power loop 拉起；日光 6000K，天空过曝削白，逆光边缘有紫边；镜片上有水珠被气流抹开；模拟图传在信号弱处出现横向撕裂与雪花，OSD 显示 "11.8V 0:42"；全程一镜到底，风噪轰鸣与电机高频啸叫随油门起伏。

**English · FPV drone**
> FPV drone first-person flight, 16mm equivalent ultra-wide at f/2.8, deep focus from foreground to infinity with absolutely no bokeh; 2.7K 120fps with a short shutter, razor-crisp motion and almost no motion blur; barrel distortion with the horizon bowing at the frame edges; a vertical dive from 40 meters at roughly 90 km/h, pulling level just 30cm above the water and skimming across it throwing up spray; then a rolling pass threading a 1.2m gap through a broken window, the horizon rotating a full 360°, followed by a power loop; 6000K daylight, sky clipping to white, purple fringing on backlit edges; water droplets beading on the lens and smearing in the airflow; analog VTX static and horizontal tearing as the signal weakens, OSD reading "11.8V 0:42"; one continuous unbroken take, overwhelming wind roar and high-pitched motor whine rising with throttle. No steadicam, no dolly, no smooth cinematic aerial drift.

**中文 · 头盔 POV**
> 头盔运动相机第一人称，机位高 1.7m，等效 16mm 超广角 f/2.8，全景深无虚化；骑手自己的双手与车把占据画面下三分之一，建立主观性；4K 60fps，短快门，前方碎石路面的每一颗石子都清晰；车体高频振动持续存在，过坎时整帧垂直冲击一次；快速左转时头部转动约 70°/s 并略微过冲；穿过隧道口时自动曝光在 0.4 秒内急剧泵动，画面先黑后回；户外日光 6200K，太阳直射入镜产生大面积眩光；镜片边缘有泥点；风噪持续轰鸣并在加速时削顶。

**English · Helmet POV**
> Helmet-mounted action cam POV, 1.7m camera height, 16mm equivalent ultra-wide at f/2.8, deep focus with no bokeh anywhere; the rider's own hands and handlebars occupy the lower third of frame to establish first-person subjectivity; 4K 60fps with a short shutter, every stone on the gravel track rendered crisp; constant high-frequency chassis vibration with one hard vertical jolt over a bump; a fast left turn with the head whipping about 70° per second and slightly overshooting; exposure pumping over 0.4 seconds as the camera enters a tunnel, going dark then rebalancing; 6200K daylight with the sun flaring directly into the wide lens, veiling glare across frame; mud specks on the lens element; relentless wind roar clipping the mic under acceleration.

---

## 12. 自检清单（生成前逐条过）

- [ ] 明确选了 A / B / C / D 其中一条子路线
- [ ] 显式写了 **全景深、无虚化**（`deep focus, no bokeh`）
- [ ] 写了等效焦段（15–17mm）与固定光圈 f/2.8
- [ ] 写了帧率与短快门（60/120/240fps，清晰无拖影）
- [ ] 有桶形畸变 / 地平线弯曲
- [ ] **肢体或载具入画**（手、把手、板尖、车头）
- [ ] FPV 写了具体的俯冲 / 穿孔 / 贴物距离（cm 级）与速度（km/h），**不是平飞**
- [ ] 显式禁用了 steadicam / dolly / crane / smooth cinematic drift，声音保留风噪
