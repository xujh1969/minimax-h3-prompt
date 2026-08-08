# MiniMax H3 视频提示词生成 Skill

把一句简单的故事情节 / 创意，转换为符合 **MiniMax H3（海螺 3）** 规范的视频生成提示词（**中英双语**）。

## 它能做什么

- 覆盖 **5 种生成模式**：文生视频、单图生视频、首尾帧、多图参考（全能参考）、视频编辑。
- 运行时先确认模式，为每个参考素材分配角色，嵌入统一音频块与 `PRESERVE / AVOID` 约束。
- 生成前用官方检查清单自检，产出「中英双语提示词 + 简短中文说明 + 一次只改一个变量迭代指引」。
- 内置**四层影像参考库 + 两维正交叠加**，让提示词落到可执行参数（ASL 秒数 / 开尔文色温 / 光比 / 光位 / 禁用运镜），而非"电影感"空话：
  - **L1 题材镜头语法**：专类 + long-tail 52 子类（动作武侠 / 科幻 / 恐怖惊悚 / 犯罪 / 战争 / 科技企业 / 美食 / 动漫根 …），含母题动词、ASL、光位色温、光比、升降格、声音、翻车点。
  - **L2 商业广告 8 种叙事结构范式**（与题材正交叠乘）。
  - **L3 导演风格锚点库**：欧美 / 亚洲导演 + 摄影指导（已拆分三份）。
  - **L4 介质语法**：手机自拍 / 监控 DV / 运动相机。
  - **两维正交**：视觉风格（16 画风，含日式赛璐璐 / 吉卜力、美式 TV 卡通 / 迪士尼等动漫根）+ 年代（12 时代）。
- 内置**「镜头连贯性 / 因果链」硬规则**：杜绝相邻镜头故事线断点（如追车中凭空冒出的物体、未交代就中断的动作线）。

## 目录结构

```
minimax-h3-prompt/
├── SKILL.md                            # 核心工作流与规则（必读）
├── README.md
└── references/
    ├── genre-index.md                  # 四层架构入口 + 题材→文件索引
    ├── genre/                          # 题材镜头语法（动作武侠/科幻/恐怖/犯罪/战争/科技/美食…）
    ├── genre/long-tail-genres.md       # 52 个长尾子类
    ├── director-anchors-western.md     # 欧美电影/剧/广告导演锚点
    ├── director-anchors-asian.md       # 华语与亚洲导演锚点
    ├── dp-cinematographer-anchors.md   # 摄影指导锚点（光影/色调/器材）
    ├── commercial-ad-structures.md     # 广告结构范式
    ├── visual-style.md                 # 视觉风格（含动漫根）
    ├── era-period.md                   # 年代
    └── medium/                         # 介质语法（手机/监控/运动相机）
```

## 支持的主流工具

本 Skill 采用通用的 **`SKILL.md` 格式**（YAML frontmatter + Markdown 指令），可在以下三款主流工具中直接安装、共用同一份文件，无需改写。

> **Windows 用户注意**：下文中的 `~` 即 `C:\Users\你的用户名\`。

---

### 1. WorkBuddy（原生支持）

- 用户级目录：`~/.workbuddy/skills/minimax-h3-prompt/`
- 项目级目录：`<你的项目>/.workbuddy/skills/minimax-h3-prompt/`

```bash
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.workbuddy/skills/minimax-h3-prompt
```

- **调用**：对话中输入 `/minimax-h3`，或直接说"帮我生成 MiniMax H3 视频提示词""把这个故事写成海螺 H3 提示词"。
- 内联图片（人物 / 场景）会被主动读取并写进提示词主体，是本工具相比纯文本接口的最大优势。

---

### 2. Claude Code

- 用户级目录：`~/.claude/skills/minimax-h3-prompt/`
- 项目级目录：`<项目>/.claude/skills/minimax-h3-prompt/`（随仓库提交，团队共享）

```bash
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.claude/skills/minimax-h3-prompt
```

- **注意**：克隆后目录第一层必须**直接是 `SKILL.md`**（不要把 `minimax-h3-prompt` 仓库根再套一层，例如 `~/.claude/skills/minimax-h3-prompt-master/...` 会被识别不到，要先扁平化）。
- Claude Code 会自动发现技能，**无需重启**；可用 `claude doctor` 在 "Loaded Skills" 中验证是否加载成功。
- **调用**：直接描述任务（如"把'雨夜女孩奔跑'写成 MiniMax H3 视频提示词"），Claude Code 按 `description` 自动匹配加载。

---

### 3. Codex（OpenAI Codex CLI / Codex App）

- 用户级目录：`~/.codex/skills/minimax-h3-prompt/`（**部分版本**为 `~/.agents/skills/minimax-h3-prompt/`，详见下方说明）
- 项目级目录：`.codex/skills/minimax-h3-prompt/`（或 `.agents/skills/`）

```bash
# 方式 A：手动克隆（最通用，跨版本稳定）
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.codex/skills/minimax-h3-prompt
```

也可用官方安装器（任选其一）：

```bash
# 会话内内置安装器（交互式选择）
$skill-installer

# 或用 npx 从 GitHub 一键安装到全局（指定目标为 codex）
npx skills add xujh1969/minimax-h3-prompt -a codex -g -y
```

- **注意**：
  - 安装后**重启 Codex** 使元数据（触发关键词 / 前置条件）生效。
  - 不同 Codex 版本技能目录不同：若你的版本使用 `~/.agents/skills`，可建立软链接统一管理：
    ```bash
    ln -s ~/.codex/skills ~/.agents/skills
    ```
  - Codex **默认不读取** `.claude/skills`，跨工具共享建议用上面的软链接或都装到 `~/.codex/skills`。
- **调用**：任务描述匹配时自动激活，或会话内 `$minimax-h3-prompt` 显式调用。

---

## 跨工具说明

- `/minimax-h3` 斜杠指令是 **WorkBuddy 原生**触发方式；在 Claude Code / Codex 中，Skill 通过 `description` 与任务匹配自动加载，也可用各自显式调用语法引用。
- 三款工具**共用同一份 `SKILL.md` 与 `references/` 参考库**，安装到对应目录即可，无需任何改动。
- 若要在多工具间共享同一份技能文件，推荐在 `~` 下只保留一份真实目录，其余用软链接指向它。

## 使用示例

> **用户**：`/minimax-h3` 一个城市夜景里车辆追逐的激烈动作电影，汽车追近摩托开始撞击
> **输出**：中英双语提示词（含题材语法、因果链连贯的多镜分段、PRESERVE/AVOID 约束、一次只改一个变量迭代指引）

---

## License

技能内容供个人与团队学习、使用、二次开发。如需引用参考库中的数据，请注明来源。
