# Grade Level Design Guidelines

Cognitive development stages, gameplay preferences, and UI design considerations
for primary school mathematics game design, based on Chinese curriculum (人教版).

---

## Grade 1-2 (Ages 6-8): Concrete Operational Stage

### Cognitive Characteristics
- Thinking is tied to concrete objects and visual representations
- Short attention span (5-10 minutes per activity)
- Developing number sense and basic operations
- Learning to follow multi-step instructions
- Strong reliance on counting strategies
- Beginning to understand place value

### Suitable Game Mechanics
- ✅ Catch/Collect items with classification
- ✅ Simple pathfinding with basic arithmetic
- ✅ Sort & Organize with drag-and-drop
- ✅ Interactive story with counting and comparison
- ✅ Timed challenge with visual number representations
- ✅ Build & Craft with shape recognition

### Less Suitable
- ❌ Complex strategy games with many rules
- ❌ Text-heavy games requiring advanced reading
- ❌ Abstract puzzle chains without visual support

### UI Design Guidelines
- **Font size:** Large (≥24px for body text, ≥36px for numbers)
- **Color:** Bright, high-contrast; use distinct colors for different elements
- **Buttons:** Extra large (≥56×56px), clearly labeled with icons + text
- **Feedback:** Immediate visual + audio-style feedback (animations, celebrations)
- **Instructions:** Voice-over friendly; use picture instructions where possible
- **Layout:** Simple, uncluttered; one primary action area
- **Interaction:** Click and drag only; no typing required
- **Progress:** Visual progress bar with physical metaphor (e.g., filling a jar)

### Common Topics
- 数的认识 (0-20, 100以内)
- 加减法 (20以内, 100以内)
- 认识图形 (平面/立体)
- 认识钟表 (整时/半时)
- 认识人民币
- 长度单位 (厘米/米)
- 分类与整理

---

## Grade 3-4 (Ages 8-10): Transitional Stage

### Cognitive Characteristics
- Transitioning from concrete to more abstract thinking
- Attention span increasing (10-20 minutes)
- Developing multiplication/division fluency
- Understanding fractions as numbers
- Beginning geometric reasoning
- Can handle multi-step problem solving
- Starting to use estimation strategies

### Suitable Game Mechanics
- ✅ Tower defense with operation choice
- ✅ Mystery/detective with multi-step clues
- ✅ Puzzle chain/Escape room (5-step chains)
- ✅ Card battle with strategic operation selection
- ✅ Life simulation with money and measurement
- ✅ Sliding/Tile merge with factor relationships
- ✅ Trading/Economy (basic level)
- ✅ Pathfinding with optimization

### Less Suitable
- ❌ Purely abstract logic without concrete anchors
- ❌ Games requiring algebraic notation
- ❌ Overly simple "catch the right answer" (too easy/boring)

### UI Design Guidelines
- **Font size:** Medium-Large (≥20px body, ≥28px numbers)
- **Color:** Rich palette; use color coding for categories
- **Buttons:** ≥48×48px; can use text labels without icons
- **Feedback:** Progressive hints; show partial credit for near-misses
- **Instructions:** Short text instructions; optional tutorial level
- **Layout:** Two-panel (game area + info panel) works well
- **Interaction:** Click, drag, basic text input for numbers
- **Progress:** Level-based with stars or badges

### Common Topics
- 万以内数的认识
- 多位数乘除法
- 分数初步认识
- 小数初步认识
- 面积与周长
- 年月日/24时计时法
- 条形统计图
- 角的度量

---

## Grade 5-6 (Ages 10-12): Abstract Thinking Stage

### Cognitive Characteristics
- Capable of abstract and hypothetical thinking
- Attention span 15-30 minutes
- Can handle multi-step logical reasoning
- Understanding algebraic concepts
- Proportional reasoning developing
- Can evaluate strategies and optimize
- Beginning formal proof and argumentation
- Competitive instincts developing

### Suitable Game Mechanics
- ✅ All mechanics suitable, with advanced math content
- ✅ Strategy games with optimization and trade-offs
- ✅ Escape room with complex puzzle chains
- ✅ Trading/Economy with percentages and ratios
- ✅ Physics/Trajectory with coordinate geometry
- ✅ Drawing/Graphing with precision
- ✅ Logic Grid with multiple constraints
- ✅ Card Battle with algebraic thinking

### Especially Effective
- Games with **multiple valid strategies** (encourages discussion)
- Games with **hidden information** (requires inference)
- Games with **resource optimization** (real-world application)
- Games with **score-based competition** (motivates improvement)

### UI Design Guidelines
- **Font size:** Standard (≥16px body, ≥22px numbers)
- **Color:** Sophisticated palette; can use more subtle distinctions
- **Buttons:** ≥44×44px standard
- **Feedback:** Detailed feedback explaining errors; show alternative strategies
- **Instructions:** Written rules; strategy tips available
- **Layout:** Complex layouts OK; multi-panel, sidebar, dashboard styles
- **Interaction:** Full interaction including typing, sliders, multi-select
- **Progress:** Detailed statistics; accuracy/speed/improvement tracking

### Common Topics
- 小数乘除法
- 分数加减乘除
- 百分数
- 比和比例
- 简易方程
- 多边形面积
- 长方体/正方体体积
- 圆 (周长/面积)
- 折线统计图/扇形统计图
- 负数

---

## Universal Design Rules (All Grades)

### Color & Accessibility
- Ensure sufficient contrast (WCAG AA minimum: 4.5:1 for text)
- Don't rely solely on color to convey information
- Use warm, inviting color palettes (avoid harsh neon or dark themes)

### Typography
- Use system Chinese fonts: `"Microsoft YaHei", "PingFang SC", "Noto Sans SC", sans-serif`
- Numbers in game should use a monospace-ish feel for alignment
- Avoid all-caps for Chinese text (not applicable)

### Motivation & Engagement
- **Immediate rewards:** Stars, coins, badges for completing levels
- **Growth mindset:** Messages like "再试一次，你离正确答案很近了！" not "答错了"
- **Surprise & delight:** Occasional animations, easter eggs, fun facts
- **Agency:** Let students choose difficulty, character, or path

### Error Handling in Games
- Wrong answer → Show hint, not just "错误"
- Second wrong → More specific hint about the concept
- Third wrong → Show the solution method, not just the answer
- Never punish with negative point values
- Always allow retry

### Number Formatting for Chinese Math
- Chinese digit grouping (每4位一组) is NOT used in primary math
- Use standard international grouping (每3位一组): 1,234,567
- Decimals use point (.), not comma
- Fractions use standard notation: ½, ¾ or 1/2, 3/4
- Currency: ¥ symbol (e.g., ¥12.50)
