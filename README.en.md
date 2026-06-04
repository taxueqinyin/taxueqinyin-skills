# taxueqinyin-skills

[简体中文](./README.md)

This is a personal open-source skills collection.

This repository currently contains one skill:

- [`english-learning-coach`](./english-learning-coach): an English conversation coach skill for immersive practice, correction-only feedback, vocabulary tracking, CEFR estimation, and lightweight progress review.

## English Learning Coach

`english-learning-coach` turns an AI agent into an English practice partner. It checks the user's English before replying, then chooses one of two paths:

- If the English is correct and natural, continue the conversation in simple, level-aware English.
- If the English has mistakes or unnatural phrasing, reply with correction only and stop there.

The main design goal is immersion. The agent does not interrupt normal conversation with scores, level notes, or progress reports unless the user asks for them.

## Features

- Correction-only routing for grammar, word choice, collocation, prepositions, articles, register, clarity, and unnatural expressions.
- Adjustable strictness profiles: `natural`, `exam`, and `lenient`.
- Adaptive output level control, starting around `A2-B1` by default.
- Active vocabulary tracking based on words the learner actually uses.
- Rolling CEFR estimate from practice history and quiz results.
- Error book for recurring mistakes.
- Built-in commands: `/level`, `/summary`, `/stats`, `/review`, and `/quiz`.
- Local persistence through `scripts/learning_store.py`.

## Installation

Copy the skill folder into your agent's skills directory:

```text
english-learning-coach/
```

For Codex-style local skills, this is commonly:

```text
~/.codex/skills/english-learning-coach
```

Then start a conversation with a prompt like:

```text
Use the English Learning Coach skill as my English conversation mode.
```

If your agent platform supports skill auto-discovery, the metadata in `SKILL.md` and `agents/openai.yaml` can be used directly.

## Trigger Examples

If your agent platform supports automatic skill triggering, these phrases are good ways to invoke the skill:

```text
英语练习
开始英语练习
练英语
帮我进入英语陪练模式
我想练英语，你帮我纠错
和我用英语聊天，错了先纠正
英语对话练习
English practice
Let's practice English.
Chat with me in English and correct me when needed.
Use the English Learning Coach skill.
```

If your platform does not auto-trigger skills, use a more explicit starter prompt:

```text
Use the English Learning Coach skill as my English conversation mode.
```

## Data And Privacy

Runtime learning data is stored locally by default under:

```text
english-learning-coach/data/
```

The data directory may contain practice history, vocabulary records, error notes, profile estimates, and quiz checkpoints. By default, this data stays local and is not published with the skill.

You can override the data location with:

```text
ENGLISH_LEARNING_COACH_DATA_DIR
```

## Commands

```text
/level      Show or change the agent's output level
/summary    Summarize the current learning session
/stats      Show learning statistics
/review     Review recurring mistakes
/quiz       Run a short checkpoint quiz
```

Difficulty feedback is also supported:

```text
too hard / simpler please / 太难了 / 简单点
harder / challenge me / 难一点 / 挑战我
```

## Repository Layout

```text
english-learning-coach/
  SKILL.md
  agents/
    openai.yaml
  scripts/
    learning_store.py
```
