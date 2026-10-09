# start-vibe-coding

<p align="center">
  <img src="assets/svp.png" alt="start-vibe-coding logo" width="720">
</p>

把 `INIT.md` 丢进一个新仓库，告诉智能体你要做什么，它就能从第一轮开始带着真实项目上下文自己 vibe coding 起来。

[English](README.md) | 简体中文

---

## 这是什么

`start-vibe-coding` 是一份轻量的仓库初始化协议。它把新项目里反复出现的那套动作收成一个文件：README、项目地图、编码规则，以及环境说明。

智能体按 `INIT.md` 会建好面向人的文档、写在 `AGENTS.md` 里的长期规则、写在 `SPEC.md` 里的项目地图、写在 `PROJECT_LOG.md` 里的共享记录、用来放汇报的 `presentation/` 目录、默认仓库文件，以及仓库根目录的 `.venv`。

---

## 如何使用

1. 把 `INIT.md` 复制到新仓库根目录。
2. 用自然语言说明你要做什么。
3. 让智能体按这份协议初始化项目。

```text
I want to build a personal expense tracker web app.
Initialize this project following INIT.md.
```

---

## 会创建什么

- `README.md` — 项目概览和使用说明
- `PROJECT_LOG.md` — 追加式开发记录；多个智能体也在这里拆分任务、汇总结果
- `SPEC.md` — 项目地图，包括汇报目录和日志怎么用
- `AGENTS.md` — 长期有效的编码与协作规则
- `presentation/` — Jupyter notebook 或 HTML，供智能体向人汇报结果
- `.gitignore`、`requirements.txt`、`LICENSE`，以及仓库根目录的 `.venv`

需要时可以加翻译版 README，例如 `README.zh.md`。

---

## License

[MIT License](LICENSE)
