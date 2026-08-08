# 介质语法手册 · 手机实拍 / UGC / 素人种草 Mobile & UGC

> **一句话定性**：手机UGC 的**可信度来自瑕疵，不来自画质**。观众判断"这是真人拍的"靠的不是清晰度，是自动曝光在跳、对焦在拉、走路在颠。
> 所有决策都回到一个问题：**这条片子有没有"没人在控制摄影机"的感觉？**

**三条子路线（先选一条，再往下读）**

| 路线 | 特征 | 允许的"精致度" |
|---|---|---|
| **A · 真素人随手拍** | 一镜到底、构图歪、光线难看、有废话 | 0%。任何构图意识都是破绽 |
| **B · 伪装的品牌 UGC** | 看似随手，实则光位可用、主体居中、2–3 个跳切 | 30%。允许"运气好的现场光"，不允许打灯 |
| **C · 竖屏口播种草** | 人对镜说话 + 产品插入镜、有字幕条 | 50%。允许稳定手持与补光板，但仍需 AE 跳变 |

---

## 1. 介质签名 ×6（这一层的灵魂）

| 签名特征 | 物理成因 | 提示词写法 |
|---|---|---|
| **果冻效应 / 摇晃斜切** | CMOS 逐行读出，甩镜时上下行时间差 | `rolling shutter jello, vertical lines skewing during whip pan` |
| **自动曝光跳变** | 无锁定的 AE 持续测光，主体一移动就重新计算 | `auto-exposure hunting, brightness stepping up and down mid-shot` |
| **对焦拉风箱** | CDAF/PDAF 在低对比场景来回搜索 | `focus hunting, lens racking back and forth before locking` |
| **高光溢出无过渡** | 小传感器动态范围有限，高光直接削顶 | `blown-out highlights clipping to pure white, no highlight rolloff` |
| **超广角边缘拉伸** | 0.5x 镜头等效 13–16mm，边缘透视畸变 | `0.5x ultra-wide lens, stretched distorted edges of frame` |
| **人像模式抠图瑕疵** | 算法景深分割在发丝/眼镜腿处失效 | `portrait-mode fake bokeh, matting halo around hair and glasses` |

**用法**：至少写进 **3 条**。只写"手机拍摄 shot on iPhone"是无效指令，模型会给你一条干净的电影短片。

---

## 2. 画质参数（给数字，不给形容词）

- **分辨率感**：标称 1080p–4K，但**观感只有 720p 的信息量** —— 因为算法降噪抹掉了高频细节。写 `oversharpened but detail-smeared`。
- **动态范围**：约 **9–10 档**，且被 HDR tone mapping 强行压平 → 天空发灰、阴影被提亮到发灰。
- **噪点特性**：暗部不是胶片颗粒，是**被降噪抹成的水彩涂抹感** `luminance noise smeared into watercolor blotches`。
- **锐化痕迹**：边缘有 1–2px 白边光晕 `sharpening halos on high-contrast edges`。
- **压缩块**：低光渐变区出现 **macroblocking**，码率感 8–20 Mbps H.264/HEVC。
- **色彩科学**：肤色被算法提亮拉黄、天空被拉青蓝、整体饱和度偏高一档 `over-saturated sky, algorithmically brightened skin tones`。
- **帧率与快门**：默认 **30fps**，白天快门常在 **1/250–1/500**（不是电影的 180° / 1/60）→ 动作**发顿、发脆、没有运动模糊**。这是手机感最被忽略的一条。写 `30fps with short shutter, crisp stuttery motion, minimal motion blur`。
- **HDR 视频的"发灰"**：亮部与暗部同时被拉回中间调，全画面**对比度偏低、通透感差** `flat HDR tone-mapped contrast, hazy midtones`。
- **人脸算法痕迹**：即使不开美颜，肤色也会被局部提亮、毛孔被抹平 `algorithmically smoothed skin with lifted local exposure on the face`。

---

## 3. 镜头与视角

- **等效焦段**：主摄 **24–26mm**（默认 1x）；超广角 **13–16mm**（0.5x）；长焦 **48–77mm**（2x/3x，画质明显掉档，噪点变多）。
- **光圈**：f/1.6–f/2.4，但传感器小 → **实际是深景深**。半身距离下背景仍然可辨认，**不会奶油化**。
- **机位高度**：手持胸高 **1.30–1.45m**；自拍臂长 **40–60cm**；吃饭俯拍距桌面 **30–50cm**。
- **握持带来的角度倾向**：单手持机天然带 **3–8° 侧倾**与轻微仰角；自拍时手机略高于眼、俯角 **5–15°**（显脸小的本能）。
- **画幅**：**竖屏 9:16 是默认**。横屏 = 立刻不像 UGC。写 `handheld vertical 9:16`。
- **禁止**：任何等效 85mm 以上的人像压缩感、任何 T1.4 的虚化。

---

## 4. 运动特征

| 运动 | 具体描述 | 英文写法 |
|---|---|---|
| **手持呼吸** | 静止站立时 ±0.5–1.5° 的低频漂移，周期约 0.8s | `subtle handheld breathing drift` |
| **走路弹跳** | 步频 **1.8–2.2Hz** 的垂直起伏，电子防抖后仍残留 | `vertical bounce with each footstep, residual after EIS` |
| **EIS 锁定-松开** | 防抖裁切约 10%，突然"抓住"再"放开"的塑料感 | `electronic stabilization locking then releasing` |
| **过冲回拉** | 甩向主体时冲过头再拉回 | `whip pan overshooting the subject then correcting back` |
| **单手换握** | 中途画面顿一下、角度突变 | `momentary jolt as the hand re-grips the phone` |
| **递机 / 转向** | 把手机转向另一个人或物，画面横扫 180° | `swinging the phone around 180° to show something else` |
| **低头看屏** | 手机随视线下垂，画面短暂拍到地面 | `phone dipping down, briefly framing the floor` |

**绝对禁用**：`dolly`、`crane`、`gimbal orbit`、`tracking shot on rails`、`smooth steadicam`。写进去一个，UGC 感即刻归零。

---

## 5. 光线现实

- **只有现场光**。没有反光板、没有三点布光、没有边缘光。
- **室内混光是常态**：顶灯 **3000–4000K** ＋ 窗光 **5600–6500K** 同框 → **白平衡在两者之间来回漂移** `white balance drifting between warm indoor and cool window light`。
- **屏幕光**：手机/电脑屏 **6500K** 冷蓝面光打脸，无阴影层次。
- **便利店/超市**：荧光 **4000–5000K 带绿偏** `greenish fluorescent cast`。
- **顶光是常态且不必回避**：眼窝与鼻下的死阴影正是"真实"的证据（这与美食片规则相反）。
- **夜景模式**：3–5s 多帧合成 → 阴影被提亮到不自然、运动物体拖出**涂抹残影** `night mode over-brightened shadows with smeared motion ghosting`。

---

## 6. 节奏与时长

- **ASL 2.5–6.0s**，远慢于广告片。真素人常常**一镜到底 10s**。
- **10s 内镜头数上限**：A 路线 **1–2 镜**；B 路线 **≤ 3 镜**；C 路线口播 **≤ 4 镜**（人像镜 + 产品插入镜交替）。
- **剪辑点类型是跳切 jump cut**，不是匹配剪辑。跳切处画面位置**要有轻微错位**才真实。
- 开头不要"设计过的钩子"——真素人的开头往往是**镜头还没端稳的那半秒**。

---

## 7. 声音特征

- **单声道机顶麦**，150Hz 以下滚降，低频空。
- **风噪爆音**：户外只要有风就 `wind buffeting and mic clipping`。
- **室内混响重**：浴室/厨房/空房间的硬反射 `boxy room reverb`。
- **近讲喷麦**：说话距麦 20–40cm，p/b 音爆破 `plosives popping`。
- **背景不干净**：电视声、空调、马路车流、家人说话 —— **干净的环境音是破绽**。
- **禁止**：影院级立体声、专业配音、无底噪的纯净人声。

---

## 8. 界面与叠加元素

| 元素 | 英文写法 |
|---|---|
| 竖屏安全区与平台 UI | `vertical 9:16 social app UI, like/comment icons on right side` |
| 自动字幕条 | `auto-generated burned-in subtitles at lower third` |
| 录制状态 | `REC ● 00:07 indicator, battery and signal in status bar` |
| 手指入镜 | `a finger partially covering the corner of the lens` |
| 镜头指纹雾化 | `smudged lens causing veiling glare and hazy streak flare` |
| 前后摄切换 | `abrupt cut as the camera flips to the front-facing lens` |
| 变焦档位切换 | `visible jump in framing and image quality when switching from 1x to 2x` |
| 通知横幅闪过 | `a notification banner sliding in at the top of the screen mid-shot` |

**注意**：手机 UGC **不要**用时间码水印（`2024-11-07 03:14:22`）——那是监控/DV 的语言，混用会让介质精分。

---

## 9. 翻车点 ×4

1. **太稳、太干净（头号翻车）** → AI 默认会给你一条平滑、曝光完美、对焦一次到位的片子，观众 1 秒识破。**必须显式写**：`auto-exposure hunting, focus hunting, handheld bounce, no stabilizer`。
2. **电影级浅景深 + 轨道运动** → 小传感器物理上做不到，一出现就是"广告伪装素人"露馅。写 `deep depth of field, no cinematic bokeh, no dolly or crane`。
3. **专业布光** → 出现边缘光/发丝光/柔光箱质感即失真。只允许现场光与混色温漂移。
4. **横屏 + 完美构图 + 无 UI** → 三者叠加等于"这是广告片"。竖屏、构图偏一点、留 UI 痕迹。

**附加**：不要写"随意的/生活化的/真实感"这类主观词，模型无法执行；改写成具体故障（AE 跳变、对焦拉风箱、走路弹跳）。

---

## 10. 与题材的正交组合

| 题材 | 叠加手机UGC 后的效果 | 关键调整 |
|---|---|---|
| **美食** | 从"广告垂涎"变成"这家店我真去过" | 放弃逆光蒸汽，改顶光实拍；保留油光但允许过曝；30–50cm 俯拍；ASMR 换成餐厅嘈杂环境音 |
| **温情 / 家庭** | 从"催泪广告"变成"家人偷拍的一分钟" | 一镜到底、构图歪、人物半出画；混光白平衡漂移；背景有电视声 |
| **恐怖** | 从"鬼片"变成"她最后一条动态" | 竖屏 + 夜景模式涂抹残影；对焦在暗处反复拉；手抖幅度加倍；结束在录制中断 |
| **产品** | 从"官方 TVC"变成"开箱真实反馈" | 手指必须入镜操作产品；深景深看得见杂乱桌面；一次拍错的重新对焦 |
| **纪实 / 街头** | 从"纪录片"变成"路人正好拍到" | 走路弹跳 + 甩镜过冲；风噪；主体经常跑出画面再被追回 |
| **旅行 / 风景** | 从"航拍大片"变成"我真的站在那儿" | 严禁无人机；超广角 0.5x 边缘拉伸；天空过曝削白；自拍臂长入镜 |
| **教程 / 开箱** | 从"专业演示"变成"我边做边说" | 桌面俯拍 40cm；双手频繁遮挡主体；对焦在手与物之间反复拉；说话有卡壳 |

---

## 11. 中英双语锚点句（可直接粘贴）

**中文 · A 路线（真素人随手拍）**
> 竖屏 9:16 手机实拍，单手手持胸高约 1.4m，画面轻微侧倾 5°；边走边拍，每一步都有垂直弹跳；自动曝光来回跳变，走进窗光时高光直接过曝削白；对焦拉风箱两次后才锁定；等效 26mm 主摄，深景深，背景清晰可辨；室内顶灯 3500K 与窗光 6000K 混光，白平衡缓慢漂移；30fps 短快门，动作发脆无运动模糊；单声道，有风噪与空调底噪；一镜到底 10 秒。

**English · A route**
> Shot on a smartphone, handheld vertical 9:16, chest height ~1.4m with a slight 5° tilt; walking while filming with visible vertical bounce on every footstep; auto-exposure hunting, highlights clipping to pure white near the window; focus hunting racks twice before locking; 26mm equivalent main camera, deep depth of field, background clearly readable, no cinematic bokeh; mixed lighting 3500K tungsten and 6000K window with white balance drifting; 30fps short shutter, crisp stuttery motion with minimal motion blur; mono audio with wind buffeting and AC hum; single continuous 10-second take, no stabilizer, no dolly.

**中文 · C 路线（竖屏口播种草）**
> 竖屏 9:16 自拍视角，手机略高于眼、俯角 10°，臂长 50cm；人物居中对镜说话，肩部以上；0.5x 超广角导致边缘轻微拉伸；桌面反射的窗光当主光，鼻下有明显阴影；说话时轻微手抖与自动曝光呼吸；中途跳切到产品特写，手指入镜转动产品；镜头有指纹造成的雾化眩光；底部烧录自动字幕条；近讲喷麦与房间混响。

**English · C route**
> Vertical 9:16 selfie framing, phone slightly above eye level at 10° downward angle, arm's length ~50cm; subject centered, talking to camera, chest-up; 0.5x ultra-wide with stretched frame edges; window light bounced off the desk as key, hard shadow under the nose; subtle hand tremor and auto-exposure breathing while speaking; jump cut to a product close-up with a finger entering frame to rotate it; smudged lens producing veiling glare; burned-in auto-caption bar at lower third; plosive-heavy close-mic mono audio with boxy room reverb.

---

## 12. 自检清单（生成前逐条过）

- [ ] 明确选了 A / B / C 其中一条子路线，没有混着写
- [ ] 竖屏 9:16，**没有**横屏
- [ ] 至少写进 3 条介质签名（AE 跳变 / 对焦拉风箱 / 果冻 / 高光溢出 / 超广角拉伸 / 抠图瑕疵）
- [ ] 显式写了 `deep depth of field, no cinematic bokeh`
- [ ] 显式禁用了 dolly / crane / gimbal / steadicam
- [ ] 光线只用现场光，写了混色温或白平衡漂移
- [ ] 10s 内镜头数 ≤ 3，剪辑点是跳切
- [ ] 声音是单声道且写了风噪 / 混响 / 环境杂音
