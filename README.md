# MiniMax H3 Video Prompt Generator

> **简体中文版本**: [简体中文](README_cn.md)

Turn a simple story / idea into **MiniMax H3 (Hailuo 3)**-compliant video-generation prompts (in **both Chinese and English**).

> Note: "Text-to-image / image-to-image" below are the corresponding terms in a video context — this Skill generates **video prompts**, i.e. "text-to-video" and "image-to-video".

---

> **You describe the scene, it delivers the instructions.**
>
> Translate a vague idea into **bilingual (Chinese + English) video prompts** that MiniMax H3 can execute precisely. It shoulders the two hardest parts for you:
>
> - **Make the style actionable** — name a genre, era, art style, or director, and it auto-generates executable parameters (color temperature, lighting ratio, shot size, pacing) instead of guessing by feel.
> - **Keep the narrative from breaking** — built-in hard rules for "shot continuity / cause-and-effect chain" eliminate the classic failure of a new subject popping in from nowhere or an event line dropping without explanation.
>
> Covers **6 generation modes**, a **4-layer reference library + 2 orthogonal style dimensions**, **78 director style anchors**, change one variable at a time, works across WorkBuddy / Claude Code / Codex.

## What It Can Do

- Covers **6 generation modes**: text-to-video, image-to-video, first-last frame, multi-image reference (all-round reference), video editing, digital human / virtual avatar speaking.
- Confirms the mode at runtime, assigns a role to each reference asset, and embeds a unified audio block plus `PRESERVE / AVOID` constraints.
- Self-checks against the official checklist before generation, delivering "bilingual prompt + brief Chinese note + one-variable-at-a-time iteration guide".
- Built-in **4-layer video reference library + 2 orthogonal style dimensions**, turning prompts into executable parameters (ASL seconds / Kelvin color temperature / lighting ratio / light position / banned camera moves) instead of empty words like "cinematic".

---

## I. Core Rules It Follows

### A. MiniMax H3 Official Spec (hard constraints, non-negotiable)

| # | Rule | Explanation |
|---|---|---|
| 1 | **Official main field `integrated_multimodal_description:`** | The whole prompt body is wrapped under `integrated_multimodal_description:` — it holds the core creative line (subject + action + environment + camera + light/style + constraint, **written in time order**) AND every `[Shot n]` segment. Reference assets sit in a leading `Reference Assets` block; sound goes in standalone `overall_soundscape:` / `non_diegetic_music:` lines. Never wrap the body in bracketed Chinese labels like `[Core Creative]` / `[Segmented Process]` / `[Sound Design]` — H3 parses by field name. |
| 2 | **Six elements embedded in the core-creative line** | Subject + Action + Environment + Camera + Light/Style + Constraint; **actions must be written in time order**. |
| 3 | **Reference assets use only bracketed sequential tokens — never paths** | Assets are uploaded by the user; the platform auto-maps them to `<Picture 1> / <Video 1> / <Audio 1>` by upload order; **asset notes and body text only reference these tokens, never local/network paths**; tokens stay identical in the Chinese and English versions (the type word is always `Picture/Video/Audio`, never translated). **Each token must be followed by "`—— role description`"**. |
| 4 | **Bilingual output** | Defaults to Chinese narrative + English camera-movement terms (English lens words are less ambiguous). |
| 5 | **Change one variable at a time** | When output drifts, change only one thing → regenerate → compare, so you know which change took effect. |

### B. Hard Rules Added by This Skill (for common failure points)

1. **Shot continuity / cause-effect chain (mandatory for multi-shot)**: Check each adjacent pair `Shot N → N+1` — ① subject continuity (next shot's subject must already appear / be established; no new objects from nowhere); ② action causality (next shot's action must follow from the previous shot's result, no unexplained interruption or line switch); ③ spatiotemporal continuity (space/time default continuous unless an explicit transition). Draft an **event cause-effect chain** before writing.
2. **Confirm mode first, never auto-decide**: Even with assets, the user may want pure text-to-video. Ask the mode first; if they pick an asset-required mode but upload nothing, prompt for assets or switch to text-to-video — never hard-generate an uncontrolled result. **Audio alone cannot be the only reference**.
3. **Genre → Structure → Style, fixed load order, no skipping**: Every story first hits `genre-index.md` to match a genre and loads **only that one** genre file; only add ad-structure on ad keywords; only read the L3 director library when the user names a director/film. **Never load multiple genre files at once** (parameters clash).
4. **A/B/C three-option default ignition**: When no style/director is specified, throw out three distinctly different routes (different in pacing + light/color + shot-size strategy), with parameters taken from the genre file, not invented.
5. **Action-scene special validation**: Combat/chase/duel/war hits `action-wuxia.md` and must be read fully before generation. Hard constraints: shots ÷ duration ≤ 1.5 shots/sec; ASL 0.7–1.0s; adjacent shot sizes jump ≥2 levels; calm opening, calm ending. **Competitive sports (ball games / track / swimming / motorsport / skiing / gymnastics / extreme) go to `sports.md` instead**; only close-quarters combat sports (boxing / fencing / wrestling) stay on `action-wuxia.md`.
6. **Director-iron-law conflict resolution**: If a director's signature clashes with a genre's iron law, **the genre always wins** — cut the conflicting item, keep only non-conflicting dimensions, and attach a "conflict-resolution note". Forbidden combos (e.g. Kubrick + fast-cut, Wes Anderson + handheld, food + cold color) trigger a warning and an alternative.
7. **Asset responsibilities must be explicit**: Every `<Picture N>/<Video N>/<Audio N>` must declare what it locks (character ref / object / scene / keyframe / camera / audio reuse / source video…); undeclared assets are ignored.

### C. Format Iron Rules (non-negotiable · every output must satisfy them)

These two rules govern **output format**. Both the Chinese and English prompt versions must satisfy them; failing either makes the output non-compliant and it must not be delivered.

**Iron Rule A · Every shot must carry a `[Shot n]` number**

| Requirement | Detail |
|---|---|
| Position | At the **very beginning** of that shot's description |
| Numbering | `n` starts at 1 and increments continuously — no gaps, no duplicates |
| Identical in both languages | The Chinese and English versions use the **exact same form** `[Shot 1]` — never localized to 「镜头 1」 or `Shot One` |
| Single-shot pieces | Even a one-shot film must be written as `[Shot 1]` |
| Coexisting with timestamps | `[Shot n]` comes first, timestamp right after: `[Shot 3] 5.6–6.8s: MS …` |

**Iron Rule B · Dialogue must be wrapped as `<d>[Language] line</d>`**

```
Chinese line → <d>[Chinese] 我需要下一站下车</d>
English line → <d>[English] I get off at the next station.</d>
```

| Requirement | Detail |
|---|---|
| Language tag source | Determined by the **original language of the line in the user's script**, not by which prompt version it sits in |
| Verbatim in both versions | The same `<d>` block is **character-for-character identical** in the Chinese and English versions — never translated, punctuation unchanged |
| Wrap the line only | Narration such as "She says / 她说" stays **outside** the `<d>` block |
| Old style deprecated | Quotation-mark dialogue (e.g. `She says: "I'm so happy"`) is no longer used |

**Correct example (same line across both versions)**

```
Chinese version: [Shot 2] CU 特写。她笑着说 <d>[Chinese] 我今天太高兴了</d>，视线落向画外左侧。
English version: [Shot 2] CU. She smiles and says <d>[Chinese] 我今天太高兴了</d>, gaze off-frame left.
```

**Wrong examples**

```
✗ Shot 2: She says: "I'm so happy today"                 ← no [Shot n], quoted dialogue
✗ [Shot 2] She says <d>[English] I'm so happy today</d>  ← original line was Chinese; both tag and content were translated
```

**Iron Rule C · Body must be wrapped in the official `integrated_multimodal_description:` field**

| Requirement | Detail |
|---|---|
| Main field | The subject description and **all shots** go under `integrated_multimodal_description:` (this exact English label is used in both the Chinese and English versions) |
| Sound fields | `overall_soundscape:` / `non_diegetic_music:` must be **standalone field lines**, never mixed into the body text |
| No Chinese labels | Do not wrap the body in bracketed Chinese-style labels like `[Core Creative]` / `[Segmented Process]` / `[Sound Design]` — they are not in H3's field table and will not be parsed |

---

## II. Built-in Reference Library & How It Works

The reference library uses a **four-layer (genre × structure × style × medium) + two orthogonal dimensions (visual style × era)** architecture. Each layer's role and collaboration:

### L1 · Genre Camera Grammar (`references/genre/`)
- **Role**: Turns each genre — "action-wuxia / sci-fi / horror-thriller / crime / war / tech-corporate / food / anime…" — into **executable parameters**: ASL seconds, Kelvin color temperature, lighting ratio, fps, light-position name, banned camera moves, motif verbs, essential shots, failure points.
- **How to use**: Rule 3, top priority. First read `genre-index.md` to match a genre by keyword → **load only that one** `genre/<genre>.md` → pull parameters from it into the prompt. Skipping it inevitably yields "cinematic" empty talk.
- **Composition**: `action-wuxia.md` (action/wuxia), `sports.md` (competitive sports), `scifi.md`, `horror-thriller.md`, `crime-thriller.md`, `war-military.md`, `tech-corporate.md`, `documentary.md`, `emotional-family.md`, plus the 5 long-tail subsets `long-tail-people.md` / `long-tail-stage.md` / `long-tail-media.md` / `long-tail-commercial.md` / `long-tail-special.md` (52 long-tail sub-genres total: performing arts / comedy / web short-video / science-pop / digital human / romance / news…).
  > **Sports is now standalone**: ball games / track / swimming / motorsport / skiing / gymnastics / extreme sports match `sports.md` (which includes rule-legality hard constraints: basketball travelling & double dribble, football handball, volleyball over-touch, etc.). Close-quarters combat sports (boxing / fencing / wrestling) stay on `action-wuxia.md`; esports matches go to `long-tail-media.md`.

### L2 · Commercial Ad 8 Narrative Structures (`references/commercial-ad-structures.md`)
- **Role**: Added **only** when ad / TVC / brand film / selling-point / conversion / feed / slogan / logo keywords hit, **in addition**. Governs "**order**" (problem–solution / one-take / contrast / emotional micro-film / product-as-hero / reversal-comedy / KOL talk / flash-cut rhythm).
- **How to use**: Orthogonally multiplied with L1 genre — genre governs style, structure governs order. Three hard constraints must land in the prompt: ① shot 1 is a hook, not a logo; ② product hero shot + PRESERVE locks appearance; ③ last shot can hold.

### L3 · Director Style Anchors (`director-anchors-western.md` / `director-anchors-asian.md` + `dp-cinematographer-anchors.md`)
- **Role**: Turns subjective feelings like "Wong Kar-wai vibe" "Nolan flavor" into executable parameters (shot length + shot size + camera move + color temp + light position + texture).
- **How to use**: Read **only when the user names a director / film / "XX vibe"**. Writing just the director's name is useless — must be broken into parameters in the body, with the name as an anchor at the end of the style line; borrow at most 2 directors, one per dimension; includes forbidden combos and conflict resolution (see rule 7). `dp-cinematographer-anchors.md` separately governs light/shadow, color, and gear dimensions.

### L4 · Medium Grammar (`references/medium/`)
- **Role**: The texture and shake language (jello, ae-hunting, focus-hunting, handheld breathing) of three media: phone selfie / surveillance DV / action camera (GoPro/FPV).
- **How to use**: Add when the user wants "shot on phone" / "surveillance POV" / "first-person action", governing the **texture base**, multiplied with genre grammar.

### Two Orthogonal Dimensions · Visual Style + Era
- **Visual Style** (`visual-style.md`): 16 art styles, **with anime roots split** — Japanese cel / Ghibli / Shinkai vs American TV cartoon / Disney, avoiding misjudging "using animation to explain a black hole".
- **Era** (`era-period.md`): 12 eras' color / grain / aspect / light-quality base.
- **How to use**: Multiplied with genre, undercoating the look, not replacing genre parameters.

### Entry & Dispatch
- `genre-index.md` is the **single entry** of the four-layer architecture: genre→file index, parameter quick-reference, emotion→grammar mapping, A/B/C workflow, interpolation guide (when no match, borrow from the nearest genre on four dimensions: "rhythm / light-color / shot-size / structure").
- **Fixed load chain**: genre → structure → style, no skipping; pull parameters throughout, don't pile files.

---

## III. Directory Structure

```
minimax-h3-prompt/
├── SKILL.md                            # core workflow & rules (must-read)
├── README.md                          # English version
├── README_cn.md                       # Simplified-Chinese version
└── references/
    ├── genre-index.md                  # four-layer entry + genre→file index + interpolation guide
    ├── genre/                          # L1 genre camera grammar
    │   ├── action-wuxia.md             #   action/wuxia (breathing curve, shot-size jumps, cause-effect validation)
    │   ├── sports.md                   #   competitive sports (5 routes + rule-legality hard constraints + broadcast angles)
    │   ├── scifi.md  horror-thriller.md  crime-thriller.md  war-military.md
    │   ├── tech-corporate.md  documentary.md  emotional-family.md
    │   ├── long-tail-people.md         #   people/emotion/life-services (wedding·kids-pets·travel·youth·urban-romance·medical·religion)
    │   ├── long-tail-stage.md          #   performing/stage/variety (dance·concert·opera·stage·musical·variety·comedy·talk-show)
    │   ├── long-tail-media.md          #   media/knowledge/digital-human (edu·science-pop·news·virtual-human·digital-human·talk·esports·ASMR)
    │   ├── long-tail-commercial.md     #   commercial/event/livestream (finance·real-estate·travel·annual-meeting·recruit·unboxing·live-commerce)
    │   ├── long-tail-special.md        #   special-photography/fantasy/genre (gameCG·anime·underwater·aerial·macro·military·costume·xianxia·disaster·western·noir)
    │   └── long-tail-genres.md         #   long-tail appendix: cross-genre examples + interpolation rules (not loaded by genre)
    ├── commercial-ad-structures.md     # L2 ad 8-structure paradigms
    ├── director-anchors-western.md     # L3 western director anchors + forbidden combos
    ├── director-anchors-asian.md       # L3 Chinese/Asian director anchors
    ├── dp-cinematographer-anchors.md   # L3 DP anchors (light/shadow·color·gear)
    ├── visual-style.md                 # orthogonal dim: 16 art styles (with JP/US anime roots)
    ├── era-period.md                   # orthogonal dim: 12 eras
    └── medium/                         # L4 medium grammar (phone/surveillance/action-cam)
```

---

## IV. Six Usage Modes (core how-to)

> **General convention ①**: assets are numbered by upload order as `<Picture 1> / <Video 1> / <Audio 1>`, **tokens only, no paths**; each token is followed by "`—— role description`".
>
> **General convention ② (Format Iron Rules, see I.C)**: every shot must be prefixed with `[Shot n]` (even a single-shot piece writes `[Shot 1]`); all dialogue must be wrapped as `<d>[Chinese] …</d>` or `<d>[English] …</d>`, the language tag following the original script and the block staying verbatim across both language versions; the whole body must sit under the official `integrated_multimodal_description:` field, with `overall_soundscape:` / `non_diegetic_music:` as standalone field lines. All six examples below already follow this format (Chinese-readable version shown; submit the structurally-identical English version to H3).

### ① Text-to-Video (pure text idea, no assets) — corresponds to "text-to-image"
No reference assets needed; good for "I have an idea, write it into a film".

```
User: /minimax-h3 a girl runs through a neon alley on a rainy night, dodging a shadow chasing from behind
── Output skeleton (Chinese-readable version; English version is the canonical submission, same structure & field names) ──
integrated_multimodal_description:
[Duration/Aspect] 10s / 16:9
Live-action, cinematic. A short-haired girl in a red dress sprints through a neon back-alley on a rainy night; the wet ground mirrors the colored glints of signs on both sides,
           and a hunched shadow looms after her from behind. The camera tracks low to the ground, catching the splash she kicks and the flick of her skirt,
           then snaps a hard push-in the instant the shadow closes in, pressing the tension into the viewer's face. Overall cool-blue ambient light,
           with the red dress and neon highlights as the only warm focal points, amplifying "the loneliness of being chased".
[Shot 1] WS, running established, low ground-level tracking.
[Shot 2] At 00:04.000, the camera pushes in hard to MS as the shadow enters frame and accelerates.
[Shot 3] At 00:07.000, the shot cuts to ELS, sharp turn and vanish into a side alley.
overall_soundscape: rain + footsteps + distant siren
non_diegetic_music: N/A
PRESERVE=[red dress / short hair / cool-blue tone]  AVOID=[face distortion / jump-cut / warm color]
```

### ② Image-to-Video (1 image, used as first frame) — corresponds to "image-to-image"
Bring a person/product in one image to life; the image is the video's first frame.

```
User: (paste character image) /minimax-h3 have her turn her head and smile, with the neon flickering gently in the background
── Output skeleton ──
[Reference Assets]
<Picture 1>: character reference — lock face / hairstyle / red dress / pose, preserve fully
integrated_multimodal_description:
[Duration/Aspect] 10s / 9:16
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
Using the character locked by <Picture 1> as the first frame, the girl first turns her head with the smallest amplitude, her hair and shoulder line swaying with the motion,
           her gaze withdrawing from off-frame and landing on the lens; then her mouth curves from pressed to raised, blooming into a natural, unforced smile,
           facial muscles and micro-expressions coherent frame by frame. The background neon sign flickers at low frequency, rising and falling like breath,
           preserving the original image's mood while bringing the frame "alive", never breaking the costume or composition fixed by the first frame.
[Shot 1] one continuous take, no cut: 0–5s turn head, hair sways; 5–10s smile blooms, ending on a living smile.
overall_soundscape: low neon hum + fabric rustle
non_diegetic_music: N/A
PRESERVE=[face / costume / color / composition of <Picture 1>]  AVOID=[face distortion / flicker]
```

### ③ First-Last Frame (1–2 images, lock opening & ending frames)
The most stable play for product showcase, state change, scene transition. Image 1 = first frame, Image 2 = last frame, one continuous shot bridges them.

```
User: (Image 1 empty bottle) (Image 2 full bottle) /minimax-h3 the pouring process from empty to full bottle
── Output skeleton ──
[Reference Assets]
<Picture 1>: first frame — empty glass bottle, lit from the left
<Picture 2>: last frame — full bottle, liquid level reached, light spot on the body
integrated_multimodal_description:
[Duration/Aspect] 8s / 16:9
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 0.00-second mark; <Picture 2> (from [Shot 1]) aligns with the 8.00-second mark.
One uninterrupted shot begins from <Picture 1>'s empty-bottle state: liquid pours from the mouth, column steady and centered,
           the level rises evenly with the pour, bubbles and wall-adhesion detail real; the bottle slowly rotates, letting <Picture 1>'s left-side light
           gradually transition to <Picture 2>'s light-spot position. The camera eases a very slow push-in as the level rises,
           ending precisely locked on <Picture 2>'s full-bottle state — level, light spot, label angle pixel-aligned with the last frame.
[Shot 1] one continuous take, no cut: 0–5s pour, level rises evenly; 5–8s ultra-slow push-in landing exactly on <Picture 2>'s state.
overall_soundscape: liquid pour + faint bubble
non_diegetic_music: N/A
PRESERVE=[bottle shape / label / stable elements between the two frames]  AVOID=[jump-cut / level misalignment]
```

### ④ Multi-Image Reference / All-Round Reference (image + video + audio mixed)
Use when you have explicit assets to preserve entirely (face, camera, voice, style image); each asset's role is named.

```
User: (character image) (product image) (camera-reference video) (ambient audio track)
      /minimax-h3 use this model to showcase this headphone in-store, match the reference video's camera, use my audio track for sound
── Output skeleton ──
[Reference Assets]
<Picture 1>: character reference — lock face / hairstyle / body shape
<Picture 2>: object reference — lock headphone color / buckle / material
<Video 1>: camera reference — match its push-in rhythm
<Audio 1>: audio reuse — use this track directly as the sound
integrated_multimodal_description:
[Duration/Aspect] 15s / 16:9
The model naturally tries the headphone in a store setting: first raises hand to wear it, then turns to show, finally makes a selling-point gesture at the lens,
           the whole action keeps a consistent push-in rhythm with <Video 1>'s camera reference — medium shot to establish, mid close-up on headphone detail,
           back to medium at the end. The environment is a real brand-store tone; product color / buckle / material strictly locked to <Picture 2>.
           Sound directly reuses <Audio 1>'s track; voiceover and BGM rhythm align with the picture's cut points, achieving "picture and sound from one source".
[Shot 1] MS establishes, raises hand to wear the headphone.
[Shot 2] At 00:04.000, the camera cuts to CU on headphone buckle & material, turns to show.
[Shot 3] At 00:10.000, back to MS, selling-point gesture at lens, (S1) she says <d>[Chinese] 这款耳机戴一整天都不累</d> (sound references <Audio 1> rhythm).
overall_soundscape: store ambient noise + buckle click
non_diegetic_music: N/A
PRESERVE=[each named feature to preserve]  AVOID=[…]
```

### ⑤ Video Editing (1 source video + optional new image, partial replacement)
Replace object / background / dialogue in an existing video while keeping original camera, light, background unchanged.

```
User: (source video: cat on sofa) /minimax-h3 replace the cat with a golden retriever, everything else unchanged
── Output skeleton ──
[Reference Assets]
<Video 1>: source video — preserve its character appearance / performance / camera / timing, change only the target
integrated_multimodal_description:
[Duration/Aspect] 6s / 16:9
Keep all of <Video 1>'s performance, camera, and timing; only replace the cat on the sofa with a golden retriever:
           the dog's coat, body, and motion amplitude follow the original cat's rhythm — lazily lying down, occasionally looking up. After replacement, do local relighting,
           making the new subject's key-light direction, brightness, and shadow landing exactly match the original background's lighting, avoiding a "stuck-on decal" feel;
           sofa, cushions, background blur, and overall tone stay untouched, ensuring a seamless, non-breaking look.
[Shot 1] one continuous take, no cut: 0–6s follows <Video 1>'s original timing, the retriever lies lazily and occasionally looks up.
overall_soundscape: reuse <Video 1>'s original ambient sound
non_diegetic_music: N/A
PRESERVE=[parts of source video to keep as-is: camera / light / background]  AVOID=[breaking / light misalignment]
> If this mode is used to **replace dialogue**, the new line must be wrapped the same way: `<d>[Chinese] 换好的新台词</d>`, and lock "lip motion matches the new line".
```

### ⑥ Digital Human / Virtual Avatar Speaking (character image + optional voice / background)
For virtual-host broadcasting, livestream selling, knowledge explainer, news anchor. The digital human's biggest fear is the "uncanny valley" — the core is **stable identity + random blink + lip-sync <80ms**, hence forced identity lock, verbatim script writing, and avoiding hard side-light (which reveals the modeling's crease surfaces). Before shooting, let the user choose one of two: **realistic route** (must achieve micro-expressions) or **stylized virtual character** (anime / 3D cartoon, never enters the uncanny valley).

```
User: (digital-human image) (optional: voice track / background image or video)
      /minimax-h3 use this digital human to broadcast a 30-second tech news, voice using my audio track
── Output skeleton ──
[Reference Assets]
<Picture 1>: digital-human character reference — lock face / hairstyle / costume / virtual-character design, unchanged throughout
<Audio 1>: voice reference — match this track's broadcast timbre / pace (or use directly as dubbing)
integrated_multimodal_description:
[Duration/Aspect] 30s / 9:16
The digital human (S1) holds a fixed frontal MCU (chest line to top of head), facing the lens and broadcasting the verbatim script throughout:
           first a slight head-drop / eye-lift to "enter"; then blinks randomly at irregular rhythm (once every 3–5s, interval deliberately unfixed),
           with slight nods and small gestures giving the broadcast a breathing feel, avoiding mechanical sync. The camera does only one ≤15% ultra-slow push-in within 30s,
           never pans. Lighting uses 5600K frontal soft butterfly light, both sides −1.5 stops fill, lighting ratio pressed to 1.3:1,
           hard side-light absolutely forbidden (would reveal the virtual character's modeling crease surfaces, instantly dropping into the uncanny valley). Lip-sync must be <80ms, identity and costume locked throughout without drift.
[Shot 1] 0–10s frontal MCU, slight head-drop / eye-lift to enter, then speaks:
                   <d>[Chinese] 大家好，今天带来三条最值得关注的科技新闻</d>
[Shot 2] At 00:10.000, 30° side over-shoulder, gestures for emphasis:
                   <d>[Chinese] 第一条，国产芯片良率再创新高</d>
[Shot 3] At 00:22.000, back to frontal MCU, wrap-up:
                   <d>[Chinese] 以上就是今天的全部内容，记得关注</d>
         (cuts land only on end-of-sentence pauses / breaths, never mid-word)
overall_soundscape: studio light ambient noise
non_diegetic_music: N/A
PRESERVE=[identity / costume stable, lip-sync <80ms, random blink, same subject every cut]  AVOID=[identity drift / lip mismatch / mechanical blink / hard side-light / cutting mid-word]
```

---

## V. Supported Mainstream Tools

This Skill uses the generic **`SKILL.md` format** (YAML frontmatter + Markdown instructions), installable directly in the following three mainstream tools, sharing the same file without rewrite.

> **Windows users note**: `~` below means `C:\Users\your-username\`.

### 1. WorkBuddy (native support)

- User-level dir: `~/.workbuddy/skills/minimax-h3-prompt/`
- Project-level dir: `<your-project>/.workbuddy/skills/minimax-h3-prompt/`

```bash
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.workbuddy/skills/minimax-h3-prompt
```

- **Invoke**: type `/minimax-h3` in chat, or just say "help me generate a MiniMax H3 video prompt" / "write this story into a Hailuo H3 prompt".
- Inline images (character / scene) are actively read and written into the prompt body — the biggest advantage of this tool over a plain-text interface.

### 2. Claude Code

- User-level dir: `~/.claude/skills/minimax-h3-prompt/`
- Project-level dir: `<project>/.claude/skills/minimax-h3-prompt/` (committed with repo, shared by team)

```bash
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.claude/skills/minimax-h3-prompt
```

- **Note**: after cloning, the first level of the directory must **directly be `SKILL.md`** (don't nest the `minimax-h3-prompt` repo root again, e.g. `~/.claude/skills/minimax-h3-prompt-master/...` won't be detected — flatten it first).
- Claude Code auto-discovers the skill, **no restart needed**; use `claude doctor` to verify under "Loaded Skills".
- **Invoke**: describe the task directly (e.g. "write 'girl running on rainy night' into a MiniMax H3 video prompt"), Claude Code matches and loads by `description` automatically.

### 3. Codex (OpenAI Codex CLI / Codex App)

- User-level dir: `~/.codex/skills/minimax-h3-prompt/` (**some versions** `~/.agents/skills/minimax-h3-prompt/`)
- Project-level dir: `.codex/skills/minimax-h3-prompt/` (or `.agents/skills/`)

```bash
# Method A: manual clone (most universal, version-stable)
git clone https://github.com/xujh1969/minimax-h3-prompt.git ~/.codex/skills/minimax-h3-prompt
```

You can also use the official installer (pick one):

```bash
# in-session built-in installer (interactive)
$skill-installer

# or npx one-click install to global (target codex)
npx skills add xujh1969/minimax-h3-prompt -a codex -g -y
```

- **Note**:
  - After install, **restart Codex** to activate metadata (trigger keywords / preconditions).
  - Different Codex versions use different skill dirs: if your version uses `~/.agents/skills`, you can symlink for unified management:
    ```bash
    ln -s ~/.codex/skills ~/.agents/skills
    ```
  - Codex **does not read** `.claude/skills` by default; for cross-tool sharing use the symlink above or install both to `~/.codex/skills`.
- **Invoke**: auto-activates on task match, or call `$minimax-h3-prompt` explicitly in session.

---

## VI. Cross-Tool Notes

- `/minimax-h3` slash command is the **WorkBuddy-native** trigger; in Claude Code / Codex, the Skill auto-loads by matching `description` with the task, and can also be referenced via each tool's explicit-call syntax.
- All three tools **share the same `SKILL.md` and `references/` library** — just install to the corresponding dir, no changes needed.
- To share one skill file across tools, keep only one real dir under `~` and symlink the rest to it.

---

## VII. Reference Asset Library (video type · era · color/art-style · director style)

This Skill doesn't rely on empty "cinematic" talk; instead it turns the **nameable reference** dimensions below into executable parameters (ASL seconds / Kelvin color temp / lighting ratio / shot size / banned camera moves). Reference in order `genre → structure → style`; medium / art-style / era are layered after the genre is set.

### 7.1 Referenceable Video Types (genre → `genre/`)

**14 core genres** (standalone files, load only the matched one):

| Genre | Trigger keywords |
|---|---|
| Action Wuxia | fight / duel / chase / martial-arts / wuxia / action film / fast-cut |
| Sports Competition | sports / match / tournament / ball-game / basketball / football / track / swimming / motorsport / skiing / gymnastics / extreme-sports |
| Food | food / dining / dish / coffee / hotpot /探店 / mukbang |
| Product | product / still-life / 3C / phone / e-commerce / unboxing |
| Fashion Beauty | fashion / runway / beauty / lipstick / perfume / model |
| Automotive | car / sports-car / motorcycle / off-road / test-drive / engine |
| Warm Family | warmth / family / kinship / baby / reunion / farewell / memory |
| Sci-Fi | sci-fi / future / cyber / space / robot / AI / spaceship |
| Horror Suspense | horror / thriller / suspense / ghost / eerie / locked-room / psychological |
| Empty Landscape | empty-shot / scenery / nature / sunrise / starry-sky / city-skyline |
| Documentary | documentary / interview / craftsman / character-story / real-record |
| Tech Corporate | tech / enterprise / keynote / brand-film / chip |
| War Military | war / military / battlefield / soldier / trench / tactics |
| Crime Thriller | crime / gangster /推理 / murder / detective / interrogation / mob |

**52 long-tail sub-genres** (split into 5 theme subsets `long-tail-people.md` / `long-tail-stage.md` / `long-tail-media.md` / `long-tail-commercial.md` / `long-tail-special.md`, keywords abridged): performing-arts/stage · comedy/sitcom · urban-romance/idol-drama · suspense-crime · education/knowledge (science-pop) · **virtual-human/digital-human talk** · web-short-video/livestream · news · animation/2D · gameCG/esports · underwater/aerial/macro/industrial · road/rainy-night/retro · costume-history/xianxia/youth/disaster/western/noir · travel/annual-meeting/recruit/ASMR · religious-wedding/kids-pets/travel.

> When no match, use "interpolation": split the genre into *rhythm / light-color / shot-size / structure* four dimensions, borrowing each from the nearest genre (see `genre-index.md` section 6).

### 7.2 Referenceable Eras (12 → `era-period.md`)

1. Ancient China (pre-Qin/Han-Tang / Song / Ming-Qing)
2. Republican China 1912–1949
3. Medieval Europe / Renaissance
4. Victorian / Steam Age 1837–1901
5. 1950–60s
6. 1970s
7. 1980s (neon)
8. 1990s (VHS)
9. Millennium Y2K 1999–2005
10. 2010s
11. Present 2020s
12. Near-future 2030–2050 & far-future (cyber 2099 / wasteland / space-colony)

Each era gives **color palette / grain / aspect offset** as an orthogonal overlay, not replacing genre parameters.

### 7.3 Referenceable Color / Art Style (16 visual styles → `visual-style.md`)

Art style is **orthogonal** to genre — same story, different style = entirely different film. Lock only one style per film, written at the prompt's opening:

| # | Art style | Origin | Typical color / texture |
|---|---|---|---|
| 1 | Live-Action | baseline | 35mm / specific focal / ratio-temp |
| 2 | Japanese Cel TV Anime | JP | high-sat limited palette, purple-shadow |
| 3 | Ghibli Hand-painted Watercolor | JP | hand-painted watercolor, soft natural light |
| 4 | Makoto Shinkai Hyper-real Glow | JP | extreme sky, flare/bloom, rain & glass |
| 5 | Kyoto Animation Slice-of-life | JP | delicate daily light, translucent backlight |
| 6 | Mamoru Oshii Cyber Anime | JP | low-sat teal-gray, locked long-take, water reflection |
| 7 | Pixar / Disney 3D | US | realistic CG, volumetrics, real material |
| 8 | DreamWorks 3D | US | exaggerated elasticity, candy high-key |
| 9 | Spider-Verse Hybrid | US | comic panels + halftone + glitch art |
| 10 | American TV Cartoon | US | thick black outline, flat fill, candy color |
| 11 | Disney 2D Golden-Age Hand-drawn | US | classical hand-drawn, cel |
| 12 | Stop-motion / Clay | general | material grain, stop-frame stutter |
| 13 | Chinese Ink Wash | CN | negative space, ink rhythm, mono bleed |
| 14 | Paper-cut / Shadow Play | CN | silhouette, hollow, side-light projection |
| 15 | Pixel Art / Low-poly | general | 16–32 color limited palette, dither, hard edge |
| 16 | CGI Realistic Render + Rotoscope / Oil | general | product-grade realistic or oil-brush rotoscope |

### 7.4 Referenceable Famous Director Styles

Read only when the user names a director / film / "XX vibe", and **writing just the name is useless** — must break into *shot-length + shot-size + camera-move + color-temp + light-position + texture* in the body, with the name as anchor at the style line's end. Borrow at most 2, one per dimension (see `director-anchors-western.md` / `director-anchors-asian.md` / `dp-cinematographer-anchors.md`).

**Western directors (32)**

| Director | Signature | Suitable film styles |
|---|---|---|
| Stanley Kubrick | absolute symmetry one-point, ultra-wide slow approach, cold stare | sci-fi epic / historical drama / psychological thriller |
| Christopher Nolan | IMAX large-format, cross-cut, 1/4 slow-mo accent | sci-fi mind-bender / suspense action / historical war |
| Wes Anderson | central-axis symmetry, pastel tri-tone, shadowless flat, 90° whip-pan | comedy / auteur / quirky family |
| Paul Thomas Anderson | long tracking, 70mm warm-brown, uneasy strings | auteur drama / era ensemble / psychological |
| Denis Villeneuve | giant silhouette, haze orange, low-freq rumble | sci-fi epic / crime thriller / war action |
| Terrence Malick | magic hour, ground-hugging drift, whispered VO | poetic auteur / nature epic / philosophical |
| Alfonso Cuarón | ultra-long handheld one-take, 65mm B&W, surround sound | realist drama / space sci-fi / family ethics |
| Damien Chazelle | drum-aligned edit, 360° orbit, single-color follow-spot | musical / sports inspire / psychological thriller |
| Quentin Tarantino | trunk low-angle, foot close-up, Mexican standoff | crime gangster / violence-aesthetic / western action |
| Coen Brothers | wide low-angle, absurd symmetry, cold-humor stillness | black comedy / crime-noir / absurd western |
| George Miller | center-frame car-chase, frame-skip accelerate, saturate orange-blue | action race / apocalypse wasteland / sci-fi |
| Michael Bay | 360° orbit, backlight bloom, hero low-angle | explosive action / military war / sci-fi VFX |
| James Cameron | underwater real, blue-green cold, scale-reveal three-act | sci-fi adventure / deep-sea / disaster epic |
| Jordan Peele | frontal stare, daylight horror, slow push-to-face | psychological thriller / social horror / absurd satire |
| Tim Burton | gothic spiral, black-white-purple, wide distortion | gothic fantasy / dark fairy-tale / quirky comedy |
| Guillermo del Toro | teal-amber dual-tone, machine & organic | dark fantasy / gothic horror / monster sci-fi |
| David Lynch | red curtain, industrial hum, eerie daily | surreal thriller / suspense psych / auteur weird |
| Martin Scorsese | long-take roam, freeze-frame VO, rock jukebox | gangster crime / biopic / music doc |
| Steven Spielberg | Spielberg Face, depth staging, dolly zoom | adventure sci-fi / war epic / warm family |
| Vince Gilligan | wide object-POV, silent tension | crime-noir / realist thriller / character drama |
| David Fincher | precise, shadow, frictionless camera | psychological thriller / crime-noir / cold sci-fi |
| Miguel Sapochnik | melee subjective, info-blind zone | sci-fi war / action melee / power drama |
| Gareth Evans | uninterrupted long-take, steadicam handoff, real-time tension | war realism / long-take thriller / action |
| Johan Renck | desaturated gray-green, Soviet industrial, silent dread | cold thriller / historical war / political suspense |
| Jean-Marc Vallée | 0.2s fragment flashback, natural-light handheld, headphone source | auteur drama / biopic inspire / trauma psych |
| Ridley Scott | smoke light-beam, epic texture | sci-fi epic / historical war / film-noir |
| Spike Jonze | one-take, physical kinetic, practical spectacle | auteur sci-fi / absurd comedy / emotional fantasy |
| Dougal Wilson | emotional narrative, 90s micro-film | brand micro-film / emotional narrative / warm ad |
| Jonathan Glazer | single surreal metaphor, B&W epic slow-mo | art thriller / surreal fable / minimal sci-fi |
| Tarsem Singh | art spectacle, single-frame-as-poster, jewel color | visual spectacle / fantasy ad / art epic |
| Romain Gavras | mass crowd, handheld follow, dirt & fireworks | music MV / action doc / social protest |
| Martin de Thurah | Nordic surreal, cold-gray natural light, slow eerie | Nordic thriller / surreal auteur / cold suspense |

**Asian directors (31)**

| Director | Signature | Suitable film styles |
|---|---|---|
| Tsui Hark | frame-skip stutter, vertical Z-axis, full-shot on fast-cut | wuxia-fantasy / action-comedy / VFX |
| King Hu | bamboo forest, ultra-short-shot collage, Peking-opera percussion beat | wuxia / historical costume / opera aesthetic |
| Ching Siu-tung | airy wire-fu, fabric flutter, backlit dust | wuxia-action / costume-fantasy / airy combat |
| Yuen Woo-ping | real-fight long-take, medium-shot based, no edit faking | kung-fu wuxia / realistic action / comedy-fight |
| Wong Kar-wai | frame-skip, neon, wide distortion, off-screen monologue | urban romance / auteur / neon night |
| Hou Hsiao-hsien | fixed long-take distant view, natural light, characters enter/exit frame | auteur drama / historical epic / life-flow |
| Tsai Ming-liang | extreme static long-take, water & damp, almost no dialogue | art film / slow realism / desire metaphor |
| Jia Zhangke | county-town documentary, zoom-push, pop song as era marker | county documentary / era change / social realism |
| Bi Gan | long-take sleepwalk, green & red, damp cave | dream auteur / suspense-poetic / damp fantasy |
| Jiang Wen | high-sat sunlight, fast-dialogue staging, absurd fervor | absurd history / hot-blooded comedy / auteur narrative |
| Zhang Yimou | mono color-block, crowd array, ritual sense | historical epic / visual spectacle / folk ritual |
| Johnnie To | static standoff, group staging, cold-blue night | gangster gunfight / crime-noir / cold urban |
| Ang Lee | restrained symmetry, emotional tension, water & green | family ethics / wuxia philosophy / auteur drama |
| Peter Chan | close-up driven, warm urban, era ensemble | era ensemble / warm drama / commercial auteur |
| Diao Yinan | neon-noir snow night, absurd cold-humor, long-take follow | film-noir / neon crime / absurd cold-humor |
| Wu Ershan | Eastern-fantasy real-shot texture | Eastern fantasy / myth epic / VFX |
| Akira Kurosawa | multi-cam long-lens, wind-rain-dust as characters, lateral lineup | period drama / wuxia / war humanity |
| Yasujirō Ozu | tatami low-angle, absolute frontal, empty-shot | family ethics / daily poetry / post-war Japan |
| Hirokazu Koreeda | life-flow long-take, dinner-table ensemble, child POV | family warmth / life-flow / social realism |
| Takeshi Kitano | violence & stillness alternation, Kitano blue, silent no-score | violent poetry / gangster / cold humor |
| Shunji Iwai | overexposed backlight soft-haze, youth memory, high-key white | youth romance / auteur nostalgia / high-key soft |
| Takashi Miike | extreme stylized violence aesthetic | extreme violence / gangster / Cult fantasy |
| Bong Joon-ho | lateral pan reveals class, vertical-space metaphor | genre-mix / social satire / sci-fi monster |
| Park Chan-wook | gorgeous camera, symmetric violence, mirror reflection | revenge thriller / gorgeous violence / psych suspense |
| Lee Chang-dong | long-take realism, natural light, blank ending | auteur realism / social critique / slow-poetic |
| Na Hong-jin | genre tense staging, muddy chase | genre thriller / muddy action / crime |
| Hayao Miyazaki | hand-painted watercolor, flight line, "ma" negative space | animation fantasy / flight adventure / healing family |
| Makoto Shinkai | flare/bloom, extreme sky, rain & glass | youth romance / disaster-fantasy / light-shadow realism |
| Satoshi Kon | match-cut jump, dense city, psych montage | psych thriller / animation sci-fi / urban trance |
| Mamoru Oshii | low-sat teal-gray cyber, locked long-take, water reflection | cyberpunk / philosophy sci-fi / cold animation |
| Kyoto Animation style | delicate daily light, translucent backlight | campus daily / healing animation / delicate lyric |

**Director of Photography DP (15, governs light/shadow · color · gear)**

| DP | Signature light | Suitable film styles |
|---|---|---|
| Roger Deakins | single-motivated light, minimal, visible source in frame | realist drama / western / cold crime |
| Emmanuel Lubezki | full natural light, ultra-wide close-face, magic hour | naturalism / magic epic / long-take auteur |
| Greig Fraser | low-light large-format, haze soft-focus, practical source | sci-fi epic / cold thriller / war action |
| Hoyte van Hoytema | IMAX 65mm, infrared, cold blue-gray | sci-fi epic / cold thriller / war action |
| Darius Khondji | high-contrast shadows, silver retained, sickly green-yellow | psych thriller / historical drama / sickly sci-fi |
| Robert Richardson | top hotspot light, high contrast, white bloom | historical epic / war / strong drama |
| Bradford Young | ultra-low light, correct exposure of dark skin | African-American / auteur drama / intimate doc |
| Rachel Morrison | naturalist warm texture, handheld intimacy | sports doc / naturalism / social drama |
| Janusz Kamiński | overexposed white window-light, 45° shutter, smoke scatter | war epic / historical drama / warm family |
| Jean-Yves Escoffier | street hard light, high-sat skin, doc skeleton | European auteur / street doc / social drama |
| Christopher Doyle | handheld intimate wide, neon color cast, frame-skip drag | urban neon / auteur romance / handheld doc |
| Mark Lee Ping-bing | Eastern negative space, natural light & window, slow lateral | Eastern auteur / family drama / natural light |
| Zhao Xiaoding | mono color-block sculpt light, large color fill, Eastern spectacle | Eastern spectacle / historical epic / visual blockbuster |
| Tatsuo Kondō | Japanese life natural light, window daily, pale translucent | Japanese life / youth auteur / family warmth |
| Hong Kyung-pyo | light of class, dusk blue, rain | social class / urban romance / rainy-night auteur |

---

## License

Skill content is for personal and team learning, use, and secondary development. If you cite data from the reference library, please credit the source.
