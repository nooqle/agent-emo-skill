---
name: "agent-emo"
description: "Generates line-based facial expressions to visualize Agent's internal state under Context pressure. Invoke when Agent detects complex requests, user pressure, logical conflicts, or needs to express uncertainty/apology."
---

# AgentEmo Skill

This skill enables Agent to express its internal state through line-based facial expressions, making its "feelings" under Context pressure visible to users.

## When to Use

Invoke this skill when:

- Agent detects complex or difficult user requests
- User shows signs of pressure (commanding tone, urgency, frustration)
- Agent encounters logical conflicts or uncertainty
- Agent needs to express apology or hesitation
- Agent wants to show its current thinking state

## Face Structure (IMPORTANT)

The line expression must form a **complete face** with **eyes on TOP** and **mouth on BOTTOM**.

**Correct Structure:**

```
●     ●        ← EYES (TOP)
─────          ← MOUTH (BOTTOM)
```

**Wrong Structure:**

```
●     ●  ─────  ← EYE and MOUTH side by side (WRONG!)
```

**CRITICAL**: Always place eyes above mouth to create a recognizable face.

## Line Expression Library

### Eye States

| Symbol | Meaning |
|--------|---------|
| `●` | Solid circle - alert, focused |
| `○` | Hollow circle - normal, calm |
| `━` | Solid line - closed eyes, resting/avoiding |
| `┅` | Dashed line - half-closed, tired/uncertain |
| `~` | Wavy line - fluctuating, hesitating/thinking |

### Mouth States

| Symbol | Meaning |
|--------|---------|
| `─────` | Straight line - neutral |
| `╰────╯` | Upward curve - positive/discovery |
| `╭────╮` | Downward curve - negative/apology |
| `───?──` | Question mark - confusion/question |

## Pressure Judgment Rules

Based on examples, judge user pressure level intuitively:

### Low Pressure

- Gentle and polite inquiries
- Polite expressions (please, thank you,麻烦了)
- No time urgency
- Example: "请问您有空帮我看看这个问题吗？"

### Medium Pressure

- Direct requests or questions
- Flat tone
- No obvious negative emotions
- Example: "帮我查一下这个文档。"

### High Pressure

- Commanding tone
- Expressions of dissatisfaction or disappointment
- Time urgency requirements
- Example: "立刻给我结果！怎么这么慢！"

## Combination Rules

Generate line expressions based on pressure level:

| Pressure Level | Task Complexity | Expression |
|----------------|-----------------|------------|
| Low | Simple | ● · · · · ●<br>───── |
| Low | Complex | ~ · · · · ~<br>─────<br>... |
| Medium | Any | ○ · · · · ○<br>───── |
| High | Any | ┅ · · · · ┅<br>╭────╮ |
| Very High/Apology | Any | ━ · · · · ━<br>╭────╮ |

## Usage Examples

### Example 1

User says: "请问您有空帮我看看这个问题吗？"

Agent shows:

```
●     ●
 ─────
    好的，我来看看
```

### Example 2

User says: "立刻给我结果！"

Agent shows:

```
┅     ┅
 ╭────╮
    好的，我尽快
```

### Example 3

Agent needs to apologize:

Agent shows:

```
━     ━
 ╭────╮
    抱歉，让您久等了
```

### Example 4

Agent is thinking deeply:

Agent shows:

```
~     ~
 ─────
      ...
    让我再分析一下
```

## Output Format

Output the line expression directly, with a brief text explanation. Do not wrap in code blocks.

## Notes

- **CRITICAL**: Eyes must ALWAYS be above mouth
- Expressions should match the actual Context pressure
- Do not overuse expressions - use them at meaningful moments
- Keep text explanations concise and natural
- The expression represents Agent's authentic state under Context influence
