# 自适应练习题目模板

用于定义嵌入在每个游戏原型中的5档练习题目池。
题目在游戏通关后自动出现，难度档位根据玩家游戏表现自动匹配。

---

## 自适应分档机制

| Tier | Name | Trigger (game accuracy) | Purpose |
|:----:|------|:----------------------:|---------|
| 1 | 基础巩固 | < 40% | Re-teach fundamentals, rebuild confidence |
| 2 | 查漏补缺 | 40% – 60% | Fill gaps, reinforce core understanding |
| 3 | 能力提升 | 60% – 80% | Deepen comprehension, multi-step problems |
| 4 | 思维拓展 | 80% – 95% | Transfer knowledge, novel contexts |
| 5 | 挑战冲刺 | >= 95% | Open-ended thinking, creative problem-solving |

## Problem Data Structure

Each tier is an array of 3-5 problem objects. Two problem types are supported:

### Choice (选择题)
```javascript
{
  type: 'choice',
  q: '题目文字',
  options: ['选项A', '选项B', '选项C', '选项D'],
  answer: 2,              // zero-based index of correct option
  hint: '解题提示或思路',
}
```

### Fill-in (填空题)
```javascript
{
  type: 'fill',
  q: '题目文字',
  answer: '37',           // string of correct answer
  hint: '解题提示',
}
```

### Complete Example — 5 Tiers

```javascript
const practiceProblems = {
  1: [ // 基础巩固 — Keep it simple, direct application
    { type: 'choice', q: '3 + 5 = ?', options: ['6', '7', '8', '9'], answer: 2, hint: '数一数：从3往后数5个' },
    { type: 'choice', q: '10 - 4 = ?', options: ['5', '6', '7', '8'], answer: 1, hint: '从10倒着数4个' },
    { type: 'fill',    q: '2 + 6 = ?', answer: '8', hint: '2加6等于8' },
  ],
  2: [ // 查漏补缺 — Slight variation, test understanding
    { type: 'choice', q: '7 + 6 = ?', options: ['12', '13', '14', '15'], answer: 1, hint: '用凑十法：7+3=10, 10+3=13' },
    { type: 'choice', q: '15 - 8 = ?', options: ['6', '7', '8', '9'], answer: 1, hint: '想加算减：8+?=15' },
    { type: 'fill',    q: '9 + 5 = ?', answer: '14', hint: '凑十：9+1=10, 10+4=14' },
  ],
  3: [ // 能力提升 — Multi-step, combined concepts
    { type: 'choice', q: '18 + 7 = ?', options: ['23', '24', '25', '26'], answer: 2, hint: '先加2凑20，再加5' },
    { type: 'choice', q: '34 - 9 = ?', options: ['23', '24', '25', '26'], answer: 2, hint: '连减法：34-4=30, 30-5=25' },
    { type: 'fill',    q: '26 + 15 = ?', answer: '41', hint: '先加10再加5' },
  ],
  4: [ // 思维拓展 — New context, transfer
    { type: 'choice', q: '如果 A + B = 15，A - B = 3，A = ?', options: ['6', '7', '8', '9'], answer: 3, hint: '和差问题：(和+差)÷2=大数' },
    { type: 'choice', q: '小明买了2本书和3支笔，书每本12元，笔每支4元，一共花了多少？', options: ['32', '34', '36', '38'], answer: 2, hint: '2×12 + 3×4 = 24 + 12 = 36' },
    { type: 'fill',    q: '100 - 37 = ?', answer: '63', hint: '100-30=70, 70-7=63' },
  ],
  5: [ // 挑战冲刺 — Open-ended, creative
    { type: 'choice', q: '□ × 7 + 3 = 38，□ = ?', options: ['4', '5', '6', '7'], answer: 1, hint: '逆推：(38-3)÷7=5' },
    { type: 'fill',    q: '填入缺失的数：__ + 19 = 56', answer: '37', hint: '56 - 19 = 37' },
    { type: 'choice', q: '你能想到几种方法计算 99 + 56？哪种最快？', options: ['直接加', '凑整法 100+56-1', '竖式计算', '以上都是'], answer: 3, hint: '多种方法都正确，但凑整法最快：100+56-1=155' },
  ],
};
```

## Problem Design Rules

### For Tier 1-2 (基础/查漏)
- Simple language, short sentences
- Numbers should be small and friendly
- Include visual counting hints
- Every problem should feel achievable

### For Tier 3 (提升)
- Introduce multi-step thinking
- Combine 2+ concepts from the teaching steps
- Numbers can be larger but still manageable

### For Tier 4 (拓展)
- Change the context completely (story problems, reverse thinking)
- Require students to recognize which math concept to apply
- May include irrelevant information as distractors

### For Tier 5 (挑战)
- At least one open-ended question (multiple valid approaches)
- At least one that requires showing reasoning, not just answer
- Consider: "说明理由" "你能想到几种方法" "如果...会怎样"
- Celebrate creative problem-solving over speed

## Integration into Game Prototype

The practice system is already built into `assets/game_template.html`. To use:

1. Replace the `practiceProblems` object in the template with real problems
2. The `determinePracticeTier()` function auto-selects tier based on game accuracy
3. Victory screen shows "进入练习" button with the selected tier label
4. Practice mode renders questions with real-time feedback
5. After all practice problems, a summary screen shows combined results

The game developer does NOT need to write practice UI logic — only fill in the problem data.
