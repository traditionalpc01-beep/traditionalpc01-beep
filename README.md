<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=C792EA&center=true&vCenter=true&random=false&width=460&lines=%E7%8B%AC%E7%AB%8B%E5%BC%80%E5%8F%91%E8%80%85+%C2%B7+Python+%2B+AI+%2B+Automation;QLED+%E5%99%A8%E4%BB%B6%E6%80%A7%E8%83%BD%E6%95%B0%E6%8D%AE%E6%8F%90%E5%8F%96+%C2%B7+%E6%97%A0%E4%BA%BA%E6%9C%BA%E7%94%9F%E6%80%81%E4%BF%9D%E6%8A%A4&sep=false" alt="Typing SVG" />
</p>

<p align="center">
  <b>Python 科研工具开发者</b> &nbsp;|&nbsp; PDF 解析 &middot; LLM 信息提取 &middot; CLI 工具链
</p>
<p align="center">
  <i>把科研论文中的器件性能数据，从 PDF 变成结构化 Excel —— 自动化、可溯源、带校验</i>
</p>

<p>
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=traditionalpc01-beep&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&custom_title=GitHub+Stats" />
  <img height="165" src="https://github-readme-streak-stats.demolab.com/?user=traditionalpc01-beep&theme=tokyonight&locale=zh_Hans&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" />
</p>

---

### /now

**Building** [paper-analysis-toolkit](https://github.com/traditionalpc01-beep/paper-analysis-toolkit) v4 — PDF 论文智能分析 CLI，支持 regex 本地兜底 + LLM API 双模式
**Refactoring** [paper-analysis-toolkit-agentflow](https://github.com/traditionalpc01-beep/paper-analysis-toolkit-agentflow) — Agent-First 架构重构，LangGraph 多 Agent 工作流引擎
**Exploring** 量子点材料科学领域的自动化数据挖掘 pipeline 与期刊影响因子自动补全

---

### What I Build

从零独立开发科研领域工具，覆盖从 PDF 解析到数据提取到报告生成的完整链路。

<table>
  <tr>
    <td align="center" valign="top" width="33%">
      <b>PaperInsight CLI</b><br/><sub>PDF 论文智能分析</sub><br/><br/>
      <a href="https://github.com/traditionalpc01-beep/paper-analysis-toolkit">
        <img width="280" src="https://github-readme-stats.vercel.app/api/pin/?username=traditionalpc01-beep&repo=paper-analysis-toolkit&theme=tokyonight&hide_border=true&show_owner=true&description_lines_count=2" />
      </a>
      <br/><br/>
      <sup>
        Click CLI &middot; 双模式提取<br/>
        PDF → 文本清洗 → 数据提取 → Excel/JSON<br/>
        多 LLM 后端 (OpenAI/DeepSeek/Longcat)
      </sup>
    </td>
    <td align="center" valign="top" width="33%">
      <b>Agent-First Refactor</b><br/><sub>多 Agent 工作流引擎</sub><br/><br/>
      <a href="https://github.com/traditionalpc01-beep/paper-analysis-toolkit-agentflow">
        <img width="280" src="https://github-readme-stats.vercel.app/api/pin/?username=traditionalpc01-beep&repo=paper-analysis-toolkit-agentflow&theme=tokyonight&hide_border=true&show_owner=true&description_lines_count=2" />
      </a>
      <br/><br/>
      <sup>
        LangGraph 工作流编排<br/>
        Agent 职责分离与状态管理<br/>
        从 v3 单体到 v4 Agent 架构
      </sup>
    </td>
    <td align="center" valign="top" width="33%">
      <b>翼界科技官网</b><br/><sub>企业级服务展示平台</sub><br/><br/>
      <a href="https://github.com/traditionalpc01-beep/company-base">
        <img width="280" src="https://github-readme-stats.vercel.app/api/pin/?username=traditionalpc01-beep&repo=company-base&theme=tokyonight&hide_border=true&show_owner=true&description_lines_count=2" />
      </a>
      <br/><br/>
      <sup>
        React + TypeScript + Vite<br/>
        无人机生态保护服务展示<br/>
        响应式企业级前端架构
      </sup>
    </td>
  </tr>
</table>

---

### Private Projects (脱敏后)

| 项目名称 | 类型 | 技术栈 | 描述 |
|---------|------|--------|------|
| **AI 数据处理平台** | 后端服务 | Python, FastAPI, MongoDB | 企业级数据处理与分析平台，支持大规模数据处理 |
| **智能文档管理系统** | 全栈应用 | React, Node.js, PostgreSQL | 基于 AI 的文档管理与检索系统 |
| **自动化测试框架** | 工具链 | Python, pytest, Selenium | 企业内部自动化测试工具，提高测试效率 |

---

### Latest Updates

**Updated** [paper-analysis-toolkit](https://github.com/traditionalpc01-beep/paper-analysis-toolkit) v4.1 — 新增支持 Longcat API，优化 OCR 处理流程

**Released** [quantum-dot-miner](https://github.com/traditionalpc01-beep/quantum-dot-miner) v1.0 — 量子点材料科学数据挖掘工具，支持自动提取和分析量子点性能数据

**Developing** [lab-automation-system](https://github.com/traditionalpc01-beep/lab-automation-system) — 实验室自动化管理系统，集成实验设备控制与数据采集

---

### Architecture Decisions

在项目中做过的关键选型和设计决策，这些是我思考技术问题的方式：

| 决策 | 选择 | 原因 |
|:-----|:-----|:-----|
| 提取策略 | LLM API + Regex 本地兜底双模式 | API 不稳定或超限时自动降级，保证离线可用 |
| PDF 解析 | MinerU CLI + PaddleOCR 双通道 | MinerU 处理标准 PDF，OCR 兜底扫描件/图表 |
| 缓存机制 | PDF MD5 指纹去重 | 避免重复解析，支持增量处理上百篇论文 |
| 配置管理 | Click CLI + 交互式配置向导 | 科研用户非技术背景，需要零配置开箱即用 |
| 架构演进 | 单体 → Agent-First (LangGraph) | 将解析/提取/校验拆分为独立 Agent，提升可测试性和扩展性 |
| 打包分发 | PyPI + Electron 桌面壳 | CLI 满足批量场景，GUI 满足非技术用户 |
| 影响因子 | AI 自动补全 + 人工校验 | 从期刊名称自动匹配 JCR/IF 数据，降低人工查表成本 |

---

### Tech Stack

<p>
  <img src="https://skillicons.dev/icons?i=python,fastapi,pytorch,typescript,react,vite,tailwind&perline=7&theme=dark" />
</p>
<p>
  <img src="https://skillicons.dev/icons?i=sqlite,pandas,click,openai,docker,git,linux&perline=7&theme=dark" />
</p>

---

### Trophies & Activity

<p>
  <img width="490" src="https://github-profile-trophy.vercel.app/?username=traditionalpc01-beep&theme=onestar&no-bg=true&no-frame=true&column=7&margin-w=5" />
</p>

<p>
  <img width="830" src="https://github-readme-activity-graph.vercel.app/graph?username=traditionalpc01-beep&bg_color=1a1b27&color=c792ea&line=c792ea&point=c792ea&area=true&area_color=c792ea10&hide_border=true&theme=react-dark&days=31&height=150" />
</p>

---

### Open to Opportunities

- **方向**: Python 后端 / AI 应用开发 / 科研工具链 / 数据工程
- **偏好**: 有产品感的团队，认可独立开发经历，技术驱动
- **时间**: 全职 / 远程优先

### Reach Me

[![](https://img.shields.io/badge/Email-office@ejdrone.com-6C63FF?style=flat&logo=protonmail&logoColor=white)](mailto:office@ejdrone.com)
[![](https://img.shields.io/badge/GitHub-traditionalpc01--beep-181717?style=flat&logo=github&logoColor=white)](https://github.com/traditionalpc01-beep)

<img src="https://komarev.com/ghpvc/?username=traditionalpc01-beep&style=flat-square&color=c792ea" alt="Profile Views" />
