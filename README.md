<!--
这个页面不挂任何第三方统计服务。
没有 vercel 公共实例的 stats 卡，没有 trophy，没有访客计数，没有定时生成的 svg。
唯一的外部依赖是 shields.io 的静态徽章。
-->

<div align="center">

**traditionalpc01-beep**

科研工具开发者 · Python 为主，写一点 Go 和 TypeScript

把 QLED / 量子点方向的论文数据，从 PDF 变成能直接进 Excel 的结构化表格

<br/>

![Python](https://img.shields.io/badge/python-3776AB?style=flat-square&logo=python&logoColor=white&labelColor=555555&alt=Python)
![Go](https://img.shields.io/badge/go-00ADD8?style=flat-square&logo=go&logoColor=white&labelColor=555555&alt=Go)
![TypeScript](https://img.shields.io/badge/typescript-3178C6?style=flat-square&logo=typescript&logoColor=white&labelColor=555555&alt=TypeScript)
![React](https://img.shields.io/badge/react-61DAFB?style=flat-square&logo=react&logoColor=black&labelColor=555555&alt=React)
![Electron](https://img.shields.io/badge/electron-2C2E3B?style=flat-square&logo=electron&logoColor=white&labelColor=555555&alt=Electron)

</div>

---

同一篇器件性能数据，在十篇论文里可能有十种写法，单位、量程、是否含滤光片都不统一。我做的事情就是让机器把这批数字读出来，并且**读出来的数敢直接进 Excel** —— 带来源页码，带原始上下文，能对回去核对。

下面这些工具都是一个人从零写的，从解析、抽取到落表和打包。

## 现在

- **paperinsight 4.2.1** — 改动已经合进 `main`，release tag 还停在 v4.1。刚修掉两个 P0：PDF 指纹缓存往返后失效，以及 LongCat 接口静默返回 `None` 时不报警。
- **physics-writing-studio v3.3.0** — 从通用的 Nature 改写工具收窄到 QLED / 量子点专域，知识库按物理论文重新蒸馏。
- **multi-model-consensus-pipeline** — 在补分级降级路径的测试。

## 项目

#### [paper-analysis-toolkit](https://github.com/traditionalpc01-beep/paper-analysis-toolkit)

`typer` CLI · 1.1 MB Python · 有 Electron 桌面壳

PDF → Markdown → 器件指标 → Excel/JSON。解析走 MinerU API，扫描件和图表用 PaddleOCR 兜底（`paperinsight/parser/mineru.py`、`paperinsight/ocr/paddlex_api.py`）；抽取层同时接 OpenAI 兼容协议、DeepSeek 和 LongCat 三个后端（`paperinsight/llm/`），API 挂了会自动退回本地 regex 规则，不会因为某个模型限流就整批中断。按 PDF 的 MD5 做增量缓存，几百篇重跑只解析新增的那几篇。桌面壳是 `electron` 28 + `electron-builder`，给非代码背景的研究者用。

#### [physics-writing-studio](https://github.com/traditionalpc01-beep/physics-writing-studio)

189 篇 Nature 系开放获取物理论文语料 · 14 个 TSV 知识库约 10,700 行

上游是 [mumdark/nature-writing-studio](https://github.com/mumdark/nature-writing-studio) 的 v2.x，我把它转成了纯物理领域版本：语料换成 QLED / 量子点方向，句式库和术语表重新蒸馏。中文草稿进，符合期刊行文习惯的英文出，跑在 Codex / ZCode 这类 AI 助手里。这是我最近在改的一个。

#### [multi-model-consensus-pipeline](https://github.com/traditionalpc01-beep/multi-model-consensus-pipeline)

`Python 3.11+` · 270 KB · 单测覆盖共识判定、schema 校验与状态机

让多个模型互相审代码，但**不让它们做开放式推理**：编排逻辑硬编码进 MCP Server，模型只在 `route_id` / `task_class` / `next_action` 这类封闭选项里选，输入输出全部绑 JSON Schema，不合格直接熔断。已接入 Codex CLI 和 LongCat-Flash-Thinking，按 L2（完整编排）/ L1（只选路）/ L0（禁用模型编排）三级降级 —— 基础模型是可热插拔的弱依赖节点，任何一个挂了流程还能走完。

#### [paper-analysis-toolkit-agentflow](https://github.com/traditionalpc01-beep/paper-analysis-toolkit-agentflow)

Agent-First 拆分版 · 5 步固定流程

把单体 pipeline 拆成职责隔离的阶段：MinerU 转 Markdown → 用 IDE agent 或网页工具匹配期刊与最新影响因子 → LongCat 逐篇抽指标（一篇一线程）→ 合并身份数据与指标数据 → 回填报告路径。增量 finalize 会把 `03_paper_data.json` 和 `04_metrics_result.json` 单独合，中间某篇失败不影响其余落表。

#### [company-base](https://github.com/traditionalpc01-beep/company-base)

`React 18` + `TypeScript 5.8` + `Vite 6` + `Tailwind` · `React Router 7`

翼界科技的官网，无人机与生态保护服务的展示站。我一个人做的前端，包含响应式布局和构建流水线。

## 一些做法

| 问题 | 我的选择 | 为什么 |
|:---|:---|:---|
| 抽取全靠 LLM，限流就瘫 | LLM 与本地 regex 双模式，失败自动降级 | 批量任务不能因为一个接口断流整批重跑 |
| 扫描件和图表 PDF | MinerU 主路 + PaddleOCR 兜底 | MinerU 处理标准文本层，OCR 只补它啃不动的 |
| 重复解析上百篇论文 | PDF 的 MD5 指纹做去重与增量 | 解析是最贵的一步，能省就省 |
| 影响因子每年变 | 从期刊名自动匹配，匹配不到才人工查 | 查表成本比写匹配逻辑高 |
| 使用者不会命令行 | 交互式配置向导 + Electron 壳 | 科研使用者不装 Python 环境 |
| 多模型代码协作不可控 | 封闭选项 + JSON Schema 契约 + 三级降级 | 开放式推理没法复现，也就没法审 |

已经废弃的：[paper-analysis-toolsV2](https://github.com/traditionalpc01-beep/paper-analysis-toolsV2) 是早期版本，仓库留着做对照，实际用 `paper-analysis-toolkit`。

## 联系

在找 Python 后端 / AI 应用开发 / 科研工具链方向的机会，全职或远程优先。

[![Email](https://img.shields.io/badge/office%40ejdrone.com-6C63FF?style=flat-square&logo=protonmail&logoColor=white&alt=Email)](mailto:office@ejdrone.com)
[![GitHub](https://img.shields.io/badge/traditionalpc01--beep-181717?style=flat-square&logo=github&logoColor=white&alt=GitHub)](https://github.com/traditionalpc01-beep)
