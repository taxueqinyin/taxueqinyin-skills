# taxueqinyin-skills

[English](./README.en.md)

这是一个个人开源 skills 集合仓库。

当前包含的 skill：

- [`english-learning-coach`](./english-learning-coach)：一个英语陪练 skill，用于沉浸式英语对话、纠错优先反馈、词汇追踪、CEFR 水平估算和轻量学习复盘。

## English Learning Coach

`english-learning-coach` 可以把 AI agent 变成一个英语练习搭子。它会先检查用户输入的英文，再决定如何回复：

- 如果英文正确、自然，就继续用简单、适合当前水平的英文聊天。
- 如果英文有错误或表达不自然，就只给出纠错内容，然后停止，不继续回答话题。

它的核心目标是保持沉浸感。普通对话中不会主动插入分数、等级说明、学习统计或进度总结，除非用户明确要求。

## 功能

- 纠错优先路由：覆盖语法、选词、搭配、介词、冠词、语气、清晰度和不自然表达。
- 可调严格度：支持 `natural`、`exam`、`lenient` 三种纠错风格。
- 自适应输出难度：默认从 `A2-B1` 左右开始。
- 主动词汇追踪：记录学习者真正用过的词。
- 滚动 CEFR 水平估算：基于练习历史和小测结果估计水平。
- 错题本：记录反复出现的问题。
- 内置命令：`/level`、`/summary`、`/stats`、`/review`、`/quiz`。
- 本地持久化：通过 `scripts/learning_store.py` 保存学习数据。

## 调整纠错严格度

默认严格度是：

```text
STRICTNESS_PROFILE: exam
```

可以在 `english-learning-coach/SKILL.md` 里修改这个值：

| 严格度 | 适合场景 |
| --- | --- |
| `natural` | 日常聊天。只纠正明显语法、选词、拼写、搭配或不自然表达问题。 |
| `exam` | 考试或精细练习。会纠正较小的语法、冠词、介词、语气和表达精确度问题。 |
| `lenient` | 轻松练习。只纠正影响理解、流畅度或非常不自然的问题。 |

如果你希望它更像考试老师，用 `exam`。如果你只想顺畅聊天、少被打断，用 `lenient` 或 `natural`。

## 安装

把整个 skill 文件夹复制到你的 agent skills 目录：

```text
english-learning-coach/
```

如果使用 Codex 风格的本地 skills，常见路径是：

```text
~/.codex/skills/english-learning-coach
```

然后用类似下面的提示开始对话：

```text
Use the English Learning Coach skill as my English conversation mode.
```

如果你的 agent 平台支持 skill 自动发现，可以直接使用 `SKILL.md` 和 `agents/openai.yaml` 里的元数据。

## 调用示例

如果你的 agent 平台支持 skill 自动触发，下面这些说法都适合作为触发方式：

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

如果平台没有自动触发 skills，可以直接使用更明确的启动提示：

```text
Use the English Learning Coach skill as my English conversation mode.
```

## 数据与隐私

运行时学习数据默认保存在本地：

```text
english-learning-coach/data/
```

这个目录可能包含练习历史、词汇记录、错题笔记、水平估算和小测结果。这些数据默认只保存在本地，不会随 skill 一起发布。

也可以通过环境变量自定义数据目录：

```text
ENGLISH_LEARNING_COACH_DATA_DIR
```

## 命令

```text
/level      查看或调整 agent 的输出难度
/summary    总结当前学习会话
/stats      查看学习统计
/review     复习常见错误
/quiz       进行一次简短小测
```

也支持直接反馈难度：

```text
too hard / simpler please / 太难了 / 简单点
harder / challenge me / 难一点 / 挑战我
```

## 仓库结构

```text
english-learning-coach/
  SKILL.md
  agents/
    openai.yaml
  scripts/
    learning_store.py
```
