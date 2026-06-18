---
name: math-game-designer
description: "小学数学教学游戏设计师。根据用户输入的知识点详细教学步骤，设计5个有创意的游戏方案，生成游戏设计文档(GDD)，并构建可交互的HTML游戏原型。This skill should be used when the user provides detailed teaching steps for a primary school math knowledge point and wants creative game designs with playable HTML prototypes. Trigger: 设计游戏、游戏原型、教学游戏、根据教学步骤生成游戏、设计几个数学游戏、帮我把这个知识点做成游戏、game design for math teaching."
agent_created: true
---

# 小学数学教学游戏设计师

## Overview

This skill transforms detailed math teaching steps into creative, playable HTML game prototypes.
For each knowledge point, design 5 independent game concepts — each with a different game mechanic,
targeting different thinking modes — then build fully functional HTML prototypes that students
can interact with directly in a browser.

The output consists of 5 Game Design Documents (GDD) + 5 playable HTML prototypes. Each prototype
includes an embedded adaptive practice system — after game completion, students automatically receive
difficulty-matched practice problems based on their in-game performance.

## Workflow

### Step 1: Analyze the Teaching Steps

When the user provides teaching steps, first analyze them systematically:

1. **Identify the knowledge point** — What math concept is being taught? (e.g., "两位数加法进位", "分数的基本性质")
2. **Determine the grade level** — Infer from the teaching steps' complexity and language. Refer to `references/grade_level_guidelines.md` for grade-level cognitive characteristics.
3. **Extract key learning objectives** — What should students be able to do after learning?
4. **Identify common misconceptions** — Where do students typically struggle?
5. **Note prerequisite knowledge** — What must students already know?

Output this analysis in a concise summary block before proceeding to game design.

### Step 2: Generate 5 Game Design Documents

Design 5 games that are:
- **Creative and distinct** — Each uses a fundamentally different game mechanic. Never repeat the same mechanic type.
- **Thought-provoking** — Games should require reasoning, not just rote practice. Include open-ended challenges where possible.
- **Age-appropriate** — Match cognitive level per `references/grade_level_guidelines.md`.
- **Pedagogically sound** — Each game must clearly connect to specific teaching steps from the input.

To select game mechanics, consult `references/game_mechanics_catalog.md` (12 categories, 82 mechanics with a knowledge-point matching matrix).

**Mechanic selection workflow:**
1. First, consult the "知识点 × 玩法速查矩阵" at the bottom of the catalog — identify mechanics marked ✅ (高度适配) or ○ (可以适配) for the target knowledge point.
2. From those candidates, pick 5 mechanics spanning **5 different categories** (族系). No two games from the same category.
3. Prioritize mechanics where the grade level range covers the target grade.
4. **Cross-reference with `references/international_game_library.md`**: Look up the target knowledge point's category in the library to see how existing web games handle similar math concepts. Study their interaction patterns, feedback systems, and difficulty progression for HTML prototype inspiration.

**Category coverage requirement:**
The 5 games MUST come from 5 distinct categories. Acceptable combinations span any of the 12 categories:

| 编号 | 族系 | 关键词 | 适合转化HTML的程度 |
|:----:|------|--------|:-----------------:|
| A | 竞速族 | 快、先、抢、限时 | ★★★★★ 天然适配 |
| B | 卡牌族 | 抽、翻、配、组 | ★★★★★ 天然适配 |
| C | 棋盘族 | 掷骰、走格、路径 | ★★★★ 棋盘需模拟 |
| D | 操作族 | 拼、摆、量、画、折 | ★★★ 需模拟操作界面 |
| E | 推理族 | 猜、排、破、推 | ★★★★★ 天然适配 |
| F | 角色族 | 扮、模拟、交易 | ★★★★ 情景模拟 |
| G | 对抗族 | 攻、防、比、赌 | ★★★★ 需要AI对手 |
| H | 合作族 | 协作、共建、教 | ★★★ 单人多角色模拟 |
| I | 运气族 | 随机、抽奖、悬念 | ★★★★★ 天然适配 |
| J | 韵律族 | 歌谣、拍手、节奏 | ★★ 身体参与难转化 |
| K | 笔纸族 | 连线、填空、涂色 | ★★★★★ 天然适配 |
| L | 运动族 | 跑、跳、投、蹲 | ★ 身体运动难转化 |

For HTML prototypes, prioritize categories rated ★★★★ or higher. Categories J/L may be adapted conceptually but need significant reimagining for screen-based interaction.

For each game, produce a Game Design Document following the template in `references/game_design_doc_template.md`. The GDD must include:

1. **Game Name** — Catchy, Chinese, age-appropriate
2. **Game Mechanic Type** — From the mechanics catalog, include the catalog code (e.g., "A01 抢答赛", "E02 密室逃脱")
3. **Core Concept** — One-paragraph elevator pitch
4. **Learning Objectives Mapping** — Which teaching steps does this game address?
5. **Core Gameplay Loop** — Step-by-step description of what the player does
6. **Thinking Mode** — What kind of thinking does this stimulate? (逻辑推理/空间想象/策略规划/创造性思维/归纳总结/...)  
7. **Visual Style** — Brief art direction notes
8. **Difficulty Progression** — How does the game scale?
9. **Feedback System** — How does the game tell the student they're right/wrong?
10. **HTML Prototype Scope** — What features will the prototype include?

### Step 3: Build HTML Prototypes with Embedded Adaptive Practice

For each game, build a standalone, playable HTML file. Every prototype must include two integrated
systems: the **core game** and the **adaptive practice module**.

**Technical Requirements:**
- Single `.html` file — no external dependencies (inline all CSS/JS)
- Works offline — no CDN, no network requests
- Responsive — works on desktop browsers and tablets (min-width: 320px)
- Touch-friendly — buttons/clickable areas at least 44×44px
- Chinese language UI
- Clean, child-friendly visual design

**Gameplay Requirements:**
- Clear win/lose conditions
- Immediate feedback on every action
- Score or progress tracking
- A "重新开始" (restart) button
- At least 3 levels/rounds of content
- Progressive difficulty within the game

**Adaptive Practice Requirements (embedded in game):**
- After game completion, the victory screen shows a "进入练习" button
- Practice difficulty is **auto-selected** based on game accuracy:
  - < 40% accuracy → Tier 1 (基础巩固)
  - 40-60% accuracy → Tier 2 (查漏补缺)
  - 60-80% accuracy → Tier 3 (能力提升)
  - 80-95% accuracy → Tier 4 (思维拓展)
  - >= 95% accuracy → Tier 5 (挑战冲刺)
- Each tier contains 3-5 problems sourced from the 5-tier pool defined per `references/practice_problems_template.md`
- Practice mode shows immediate correct/wrong feedback with solution hints
- After practice completes, show a summary screen with combined game + practice results
- A "直接重玩" skip option always available to bypass practice

**Code Quality:**
- Well-commented JavaScript
- Clear separation of game logic, practice logic, and rendering
- Track `correctCount` and `totalAttempts` during gameplay for tier calculation
- Handle edge cases (rapid clicking, browser resize, empty input, etc.)
- Include a `<title>` tag with the game name

Use `assets/game_template.html` as a starting scaffold. The template already includes:
- Full practice mode UI (hidden by default)
- `determinePracticeTier()` adaptive selection logic
- `enterPracticeMode()` / `renderPracticeQuestion()` / `showPracticeSummary()` flow
- Choice and fill-in question types with feedback

**How to customize per game:**
1. Replace the game logic section with your game's mechanics
2. Replace the `practiceProblems` object with 5 tiers of real problems
3. Customize `difficultyLabels` tier names if needed
4. Ensure game logic tracks `state.correctCount` and `state.totalAttempts`

### Step 4: Generate the Practice Problem Pool

For the current knowledge point, design the 5-tier practice problem pool that will be
embedded into every game prototype. Follow `references/practice_problems_template.md`.

**Key design rules:**
1. Each of the 5 tiers has 3-5 problems of appropriate difficulty
2. Tier 1-2: Direct application, build confidence. Tier 3: Multi-step, deepen understanding.
   Tier 4: New contexts, transfer learning. Tier 5: Open-ended, creative thinking.
3. Mix problem types: at least one fill-in and one open-ended/reasoning question across the pool
4. Every problem must include a `hint` — a brief solution approach that teaches, not just answers
5. The same problem pool is reused across all 5 game prototypes (each game varies the gameplay,
   not the practice content)

**Write to each game prototype:**
Copy the `practiceProblems` object into the `<script>` section of each HTML file, replacing
the template's example data. The practice UI and adaptive logic are already built into the template.

### Step 5: Deliver Results

Create all files in the workspace under `数学游戏/<知识点名称>/` with Chinese naming throughout:

```
数学游戏/<知识点名称>/
├── 总览.md                            # 5款游戏总览 + 自适应练习系统说明
├── 游戏设计文档/
│   ├── 游戏01_<名称>.md              # 游戏1设计文档
│   ├── 游戏02_<名称>.md              # 游戏2设计文档
│   ├── 游戏03_<名称>.md              # 游戏3设计文档
│   ├── 游戏04_<名称>.md              # 游戏4设计文档
│   └── 游戏05_<名称>.md              # 游戏5设计文档
└── 游戏原型/
    ├── 游戏01_<名称>.html            # 可玩原型1（含游戏+嵌入练习）
    ├── 游戏02_<名称>.html            # 可玩原型2（含游戏+嵌入练习）
    ├── 游戏03_<名称>.html            # 可玩原型3（含游戏+嵌入练习）
    ├── 游戏04_<名称>.html            # 可玩原型4（含游戏+嵌入练习）
    └── 游戏05_<名称>.html            # 可玩原型5（含游戏+嵌入练习）
```

**Naming rules:**
- 根目录用知识点中文全称，如 `两位数加法进位`、`分数的基本性质`
- 游戏文件命名格式：`游戏01_数字特工.html`，其中 `01` 是编号，`数字特工` 是游戏名称
- 所有目录和文件名一律使用中文，见名知意

After all files are created, use `preview_url` to show the first game prototype, and use `deliver_attachments` to deliver all HTML files. Summarize the 5 game designs in a comparison table, and present the adaptive practice tier system (5 tiers × performance thresholds) in a summary table.

## Game Design Principles

Follow these principles for every game design:

### 1. Think First, Click Second
Games should require mental effort. Avoid designs where students can succeed by randomly clicking. Every interaction should be a decision.

### 2. Failure is Learning
Wrong answers should be informative, not punishing. Show WHY an answer is wrong. Allow retry. Never use negative language or shame.

### 3. Show the Math
Make mathematical thinking visible. Use number lines, area models, manipulatives, and visual representations. Don't hide the math behind flashy effects.

### 4. Progressive Challenge
Start with straightforward applications to build confidence, then introduce variations that require deeper understanding. The last level should make students transfer knowledge to a new context.

### 5. Celebrate Thinking, Not Just Answers
Reward strategy, improvement, and creative approaches — not just correct answers. Include "thinking bonuses" or acknowledgment of clever solutions.

### 6. Adaptive Practice Closes the Loop
Gameplay is the hook — practice is the learning. The embedded adaptive practice system ensures every student gets problems at their level: struggling students rebuild fundamentals, strong students stretch further. This prevents the "one-size-fits-all" trap of static worksheets.

### 7. Chinese Math Education Context
- Align with 人教版 (PEP) curriculum standards
- Use Chinese number formatting and conventions
- Follow Chinese stock market color convention (红涨绿跌) if applicable
- Support Chinese character display for all number forms

## Resources

### references/
- `game_design_doc_template.md` — Structured template for GDDs. Load when writing game design documents.
- `game_mechanics_catalog.md` — 12族系82种玩法机制总表，含知识点×玩法速查矩阵。At Step 2, first use the matrix to find ✅/○ candidates, then pick 5 from different categories.
- `grade_level_guidelines.md` — Cognitive development stages, UI design guidelines, and mechanic suitability by grade level. Load at Step 1 for analysis.
- `practice_problems_template.md` — Adaptive 5-tier problem pool template with performance→tier mapping, choice and fill-in data structures, and design rules. Load at Step 4 for problem pool design.
- `international_game_library.md` — 225款 MathPlayground 在线数学游戏库，按22个知识分类+年级推荐索引。Load at Step 2 for HTML prototype design inspiration — see how existing web games handle interaction, feedback, and difficulty progression for similar math topics.

### assets/
- `game_template.html` — Reusable HTML/CSS/JS scaffold for game prototypes. Copy and adapt for each game. Includes common UI patterns (score display, feedback modals, restart button, responsive grid).
