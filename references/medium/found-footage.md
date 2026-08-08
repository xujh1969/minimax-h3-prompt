# 介质语法手册 · 伪纪实素材 Found Footage & Surveillance

> **一句话定性**：伪纪实的力量在于**信息不足**。恐惧与真实都来自"这台机器不关心你想看什么"——它不推近、不打光、不追焦，关键的东西永远在角落、在暗处、在丢帧的那一秒。
> 所有决策都回到一个问题：**这个画面是"被记录"的，还是"被拍摄"的？**

**六个子类（先选一个，参数完全不同）**

| 子类 | 心理效果 | 典型用途 |
|---|---|---|
| **CCTV 监控** | 冷漠的全知 | 恐怖、悬疑、事件还原 |
| **行车记录仪 Dashcam** | 突发与不可逆 | 事故、追逐、都市怪谈 |
| **DV 录像带** | 千禧年怀旧 + 廉价真实 | 家庭档案、伪调查录像 |
| **8mm 家庭胶片** | 已逝的温柔 | 回忆、创伤前的幸福 |
| **视频通话** | 隔着一层的无力 | 远距离恐惧、告别 |
| **直播推流** | 有观众在看的实时 | 事件正在发生、集体见证 |

---

## 1. 介质签名 ×6（跨子类通用，这一层的灵魂）

| 签名特征 | 物理成因 | 提示词写法 |
|---|---|---|
| **时间戳水印** | 设备自动烧录，无法关闭 | `burned-in timestamp overlay "2024-11-07 03:14:22"` |
| **曝光锁死** | 无人调整，窗外过曝、室内欠曝同框 | `locked exposure, blown-out window and crushed indoor shadows` |
| **无动机机位** | 机器不构图，主体常在边缘或被遮挡 | `unmotivated fixed framing, subject off-center and partly occluded` |
| **低帧率拖影** | 采样率不足，运动体拖成条 | `low frame rate 12fps, motion smearing into streaks` |
| **压缩块 / 磁带噪波** | 极低码率或磁介质缺陷 | `heavy macroblocking in low light` / `analog tape noise and dropouts` |
| **信号中断丢帧** | 传输/介质故障 | `intermittent frame drops, image freezing then jumping ahead` |

**用法**：这 6 条是"被记录"的物证。**至少写进 4 条**，否则模型会还你一条打了光的电影镜头。

---

## 2. 画质参数（按子类给数字）

| 子类 | 分辨率/画幅 | 帧率 | 色偏 | 噪点 / 缺陷 | 码率感 |
|---|---|---|---|---|---|
| **CCTV** | 720p–1080p，16:9 或 4:3 | **8–15fps** | 灰绿 / 青偏，饱和度极低 | 暗部大块 macroblocking | **1–2 Mbps** |
| **Dashcam** | 1080p，16:9 | 30fps | WDR 压平，天空发灰 | 高对比处紫边 | 8–15 Mbps |
| **DV 录像带** | **480i**，**4:3 (1.33:1)** | 50i / 60i 隔行 | 红色溢出、肤色偏橙 | 隔行梳状撕裂、磁带掉条 | 模拟，无码率概念 |
| **8mm 胶片** | 等效 <480p，**1.33:1** | **18fps**（Super 8）或 24fps | 暖黄褪色，青绿通道衰减 | 粗颗粒、划痕、门内毛发 | — |
| **视频通话** | 自适应 360p↔720p | 15–30fps 波动 | 白平衡错误偏蓝或偏黄 | 关键帧刷新时整帧糊 | 0.3–2 Mbps 抖动 |
| **直播推流** | 720p 竖屏 9:16 | 30fps 掉到 15fps | 手机色彩科学，过饱和 | 码率抖动导致周期性糊 | 2–4 Mbps |

**关键术语英文**：`interlacing combing artifacts`、`chroma bleed`、`tape dropout white streaks`、`tracking error jitter band at bottom of frame`、`gate weave`、`film halation`、`keyframe refresh smearing`。

---

## 3. 镜头与视角

- **CCTV**：等效 **2.8–4mm**（水平 FOV **90–110°**），**安装高度 2.8–4.0m**，**俯角 20–35°**。永远是**高位俯视广角**，人脸永远看不清。可用四宫格 `quad-split multi-camera view`。
- **Dashcam**：**140–170° 鱼眼**，强桶形畸变，直线在边缘弯曲；机位在后视镜后方**高约 1.3m**；画面下缘常有**仪表盘与挡风玻璃反光** `dashboard reflection ghosting on the windshield`。
- **DV 录像带**：等效 **40–500mm 变焦**（业余用户爱乱推拉），常用广角端；手持胸高或齐腰**盲拍 1.0–1.2m**，角度乱。
- **8mm 胶片**：定焦等效 **12–25mm**；手持齐胸，常有"拍摄者也在走动"的漫游感。
- **视频通话**：笔电/手机前摄，等效 **~28mm，FOV 70°**；桌面高度 **0.7–0.8m** 的**仰角 5–15°**（显下巴），或手持晃动。
- **直播推流**：手机主摄 26mm，竖屏，主播举机移动。

---

## 4. 运动特征

| 子类 | 运动方式 | 英文写法 |
|---|---|---|
| **CCTV** | **完全静止**；若为球机则是**步进式转动**（匀速、无加减速、到位即停） | `locked-off static` / `PTZ camera panning at constant speed, mechanical stop` |
| **Dashcam** | 车体高频微振 **10–20Hz**；过坎时整帧垂直跳动；转向时鱼眼边缘扭曲 | `constant engine vibration micro-shake, sharp jolt over bumps` |
| **DV** | 业余手持：晃、找不到主体、突然变焦推拉 | `amateur handheld, sudden clumsy zoom in and out, losing the subject` |
| **8mm** | **抖动门 gate weave**：整帧 ±1–2% 的缓慢漂移，与手持抖动叠加 | `gate weave, whole frame drifting slightly frame to frame` |
| **视频通话** | 静置不动 + 偶尔被碰一下；或手持走动导致自适应降码率 | `phone propped up, occasional bump; bitrate collapsing when moving` |
| **直播** | 竖屏手持行走，走路弹跳 | `handheld vertical walking bounce` |

**通用铁律**：**没有一台 found footage 设备会做推轨、升降、环绕**。写进 `dolly` / `orbit` / `crane` 即出戏。

---

## 5. 光线现实

- **只有现场光，且通常很难看**。走廊顶灯 **3500–4000K**、荧光 **4000–5000K 带绿**、钠灯路灯 **2000–2200K 橙**、屏幕光 **6500K**。
- **CCTV 红外夜视**：**850nm 单色黑白**，光源与镜头同轴 → **完全平光、无阴影**；近处过曝、3m 外迅速衰减到全黑；**人眼与动物眼呈反光白瞳** `infrared night vision, monochrome, retroreflective white pupils, flat axial light, falloff into pure black`。
- **Dashcam 夜间**：对向车灯 **4300–6000K** 造成大面积耀斑与光晕；雨滴在挡风上散射成光斑 `oncoming headlight flare, rain droplets scattering light on the windshield`。
- **DV 内建灯**：机顶 LED/卤素 **3200K 硬直打**，正面惨白、背景 2m 外衰减全黑 `harsh on-camera light, subject blown out, background falling to black`。
- **8mm 胶片**：日光片基 **5500K**，室内钨丝灯下不校色 → **整体橙红**；高光处有 **halation 光晕**。
- **视频通话**：屏幕光打脸 + 顶灯下巴阴影，背光坐窗前时**脸全黑** `backlit by window, face rendered as a silhouette`。

---

## 6. 节奏与时长

- **CCTV**：**一镜到底，不剪**。10s 就是 10s 一镜。若要"剪"，唯一合法的剪辑点是**摄像机编号切换**（CAM 03 → CAM 07）。
- **Dashcam**：一镜到底；事件发生在**第 6–8 秒**最有效（前面必须无聊）。
- **DV / 8mm**：剪辑点是**机内启停**——即录制中断造成的**跳帧闪白/雪花** `in-camera stop-start with flash frames`。ASL **3–8s**。
- **视频通话 / 直播**：一镜，靠**冻帧与卡顿**制造节拍。
- **10s 内镜头数上限**：CCTV / Dashcam **1 镜**；DV / 8mm **≤ 3 镜**；通话 / 直播 **1 镜（可含 1 次画中画切换）**。
- **反直觉铁律**：**前 60% 必须无事发生**。伪纪实的恐怖来自"等待"，剪成快节奏就变回类型片了。

---

## 7. 声音特征

- **CCTV**：**多数无声**。若有声，是低保真单声道 + **50/60Hz 电流嗡鸣** `mains hum` + 空旷混响，语音几乎听不清。
- **Dashcam**：车厢闷响、发动机低频、转向灯"嗒嗒"、雨刮器节拍、突发碰撞时**麦克风削顶爆音** `mic clipping on impact`。
- **DV 录像带**：机顶麦单声道、**磁带嘶声 tape hiss**、变焦马达声被录进去 `zoom motor whine picked up by the onboard mic`。
- **8mm 胶片**：**默认无声**（这是它最强的情绪武器）；若配声，用后期磁条的失真杂音或纯放映机咔哒声 `projector clatter`。
- **视频通话**：**编解码压缩感**、AGC 抽吸、回声与啸叫、断续机械音 `codec artifacts, echo, robotic dropouts`。
- **直播**：手机单声道 + 风噪 + 提示音效。

---

## 8. 界面与叠加元素

| 元素 | 英文写法 |
|---|---|
| CCTV 时间戳与机位号 | `"CAM 03  2024-11-07  03:14:22" burned into top-left corner` |
| CCTV 多宫格 | `quad-split surveillance grid, four camera feeds` |
| Dashcam 遥测 | `"2024/11/07 18:42:11  35km/h  N31.2 E121.4" overlay at bottom` |
| DV 日期字符 | `yellow dot-matrix date stamp "NOV 07 1998  9:02 PM"` |
| DV 录制标记 | `"REC ●" and battery icon in the corner, tracking error band at bottom` |
| 8mm 胶片缺陷 | `film scratches, hair in the gate, flash frames at the reel change` |
| 通话 UI | `video call interface, participant name bar, mute icon, "Reconnecting…" toast` |
| 直播 UI | `live badge, floating heart animations, scrolling comments overlay` |
| 通用故障 | `analog static, scan lines, horizontal tearing, image freezing for 1.5 seconds` |

---

## 9. 翻车点 ×4

1. **太干净、太稳、太亮（头号翻车）** → AI 会给你一条曝光正确、构图漂亮、平滑运动的"电影感监控镜头"，介质感全无。**必须显式写**：低帧率、压缩块、曝光锁死、水印、静止机位。
2. **子类参数串味** → 给 CCTV 加上磁带噪波、给 8mm 加上时间戳数字、给通话加上胶片颗粒。**一条片子只服从一个介质的物理规律**。
3. **主体被完美记录** → 脸拍得清清楚楚、动作正好在画面中央 = 假。让主体**偏出画面、被柱子遮住、走出监控盲区**。
4. **剪成类型片节奏** → 快切 + 配乐 + 特写反打，立刻从"素材"变回"电影"。守住一镜到底与无配乐。

**附加**：不要写"复古的/怀旧的/诡异的"这类主观词；改写成具体缺陷（隔行梳齿、掉帧白条、gate weave、红外白瞳）。

---

## 10. 与题材的正交组合

| 题材 | 叠加伪纪实后的效果 | 关键调整 |
|---|---|---|
| **恐怖** | 从"鬼片"变成"警方公开的证物" | 选 CCTV：8fps + 红外白瞳 + 时间戳；恐怖点放在**画面边缘或即将走出画外**；前 6s 空镜 |
| **温情 / 家庭** | 从"广告催泪"变成"翻出的旧带子" | 选 8mm：18fps + gate weave + 暖黄褪色 + **无声**；过曝的阳光；换卷闪白作为结束 |
| **美食** | 从"食欲"变成"这家店的日常真的这样" | 选 CCTV 或 DV：顶光荧光偏绿、色彩难看，靠**动作真实**而非油光；不要特写 |
| **产品 / 事故** | 从"演示"变成"用户实录/事故证据" | 选 Dashcam：鱼眼 + 遥测水印 + 前 7s 平淡 + 一次不可逆的瞬间；碰撞时麦克风爆音 |
| **纪实 / 调查** | 从"纪录片"变成"未公开的原始素材" | 选 DV：4:3 + 隔行梳齿 + 业余变焦推拉 + 机顶灯直打 + 录制启停跳帧 |
| **告别 / 情感** | 从"对话戏"变成"最后一次通话" | 选视频通话：360p 压缩块 + 冻帧 1.5s + 回声 + "Reconnecting…" |

---

## 11. 中英双语锚点句（可直接粘贴）

**中文 · CCTV 恐怖**
> 固定机位监控画面，摄像头安装于 3.5m 高、俯角 30°，等效 3mm 超广角，水平视野约 100°；帧率 12fps，运动体拖出条状残影；曝光锁死，走廊尽头的门缝过曝，近处阴影死黑；灰绿偏色、饱和度极低，暗部大块压缩马赛克；红外夜视单色黑白，同轴平光无阴影，人眼呈反光白瞳，3 米外迅速衰减为全黑；左上角烧录时间戳 "CAM 03 2024-11-07 03:14:22"；全程无剪辑，画面在第 7 秒短暂丢帧冻结 0.8 秒；无配乐，仅 50Hz 电流嗡鸣与空旷混响。

**English · CCTV horror**
> Fixed surveillance camera, mounted 3.5m high at a 30° downward angle, 3mm equivalent ultra-wide, ~100° horizontal field of view; 12fps low frame rate with motion smearing into streaks; locked exposure, blown-out door gap at the end of the corridor and crushed black shadows in the foreground; desaturated grey-green cast, heavy macroblocking in the dark areas; infrared night vision, monochrome, flat axial illumination with no shadows, retroreflective white pupils, falloff to pure black beyond 3 meters; burned-in timestamp "CAM 03 2024-11-07 03:14:22" in the top-left; single continuous locked-off take with no cuts, image freezing for 0.8 seconds at the 7-second mark; no music, only 50Hz mains hum and hollow room reverb.

**中文 · 8mm 家庭胶片 · 温情**
> 8mm 家庭胶片影像，1.33:1 画幅，18fps 略显轻快的动作节奏；抖动门造成整帧缓慢漂移，画面上有划痕与门内毛发；日光下暖黄褪色，青绿通道衰减，高光处有胶片光晕；粗颗粒，等效低于 480p 的柔软细节；手持齐胸拍摄，拍摄者边走边拍，偶尔失去主体；孩子在草地上跑，回头对镜头笑；结尾换卷造成两帧过曝闪白；**全片无声**。

**English · Super 8 home movie, tender**
> Super 8 home movie footage, 1.33:1 academy frame, 18fps giving motion a slightly brisk cadence; gate weave drifting the whole frame between exposures, visible scratches and a hair in the gate; sun-faded warm yellow palette with degraded cyan channel, film halation blooming around highlights; coarse grain, soft sub-480p detail; handheld at chest height, the operator walking while filming and briefly losing the subject; a child running across the grass, turning back to smile at the lens; two overexposed flash frames at the reel change to end; completely silent, no music, no dialogue.

---

## 12. 自检清单（生成前逐条过）

- [ ] 明确锁定了**一个**子类，参数没有串味
- [ ] 写了对应子类的分辨率 / 帧率 / 画幅（如 12fps、480i、1.33:1）
- [ ] 有时间戳 / UI / 胶片缺陷之一作为"被记录"的物证
- [ ] 曝光是锁死的，画面里同时存在过曝区与死黑区
- [ ] 机位无动机：主体偏心、被遮挡或走出画外
- [ ] **没有** dolly / crane / orbit / steadicam
- [ ] 10s 内镜头数符合上限，前 60% 无事发生
- [ ] 声音是无声 / 低保真 / 压缩失真之一，**没有**配乐
