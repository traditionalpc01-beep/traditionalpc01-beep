# Code Wiki: 个人开发者资料仓库

## 1. 仓库概览

这是一个个人开发者的 GitHub 个人资料仓库，主要用于展示开发者的技能、项目和活动。开发者是一位 Python 科研工具开发者，专注于 PDF 解析、LLM 信息提取和 CLI 工具链开发。

**主要功能/亮点：**
- 展示开发者的技术栈和项目经验
- 提供 GitHub 统计数据和活动图表
- 包含关键技术决策和架构选择的说明

**典型应用场景：**
- 个人技术展示和求职
- 项目案例参考
- 技术选型参考

## 2. 目录结构

本仓库是一个个人资料仓库，主要包含以下文件和目录：

```text
├── .github/             # GitHub 配置目录
│   └── workflows/       # GitHub Actions 工作流
│       └── metrics.yml  # GitHub 指标生成工作流
├── README.md            # 个人资料和项目展示
└── metrics.svg          # GitHub 指标图表
```

**文件说明：**
- **README.md**：主要的个人资料页面，包含开发者介绍、项目展示、技术栈和活动统计等信息
- **.github/workflows/metrics.yml**：GitHub Actions 工作流配置，用于生成 GitHub 指标图表
- **metrics.svg**：自动生成的 GitHub 指标图表

## 3. 系统架构与主流程

由于这是一个个人资料仓库，不涉及系统架构和主流程。以下是开发者在其项目中采用的架构决策：

| 决策 | 选择 | 原因 |
|:-----|:-----|:-----|
| 提取策略 | LLM API + Regex 本地兜底双模式 | API 不稳定或超限时自动降级，保证离线可用 |
| PDF 解析 | MinerU CLI + PaddleOCR 双通道 | MinerU 处理标准 PDF，OCR 兜底扫描件/图表 |
| 缓存机制 | PDF MD5 指纹去重 | 避免重复解析，支持增量处理上百篇论文 |
| 配置管理 | Click CLI + 交互式配置向导 | 科研用户非技术背景，需要零配置开箱即用 |
| 架构演进 | 单体 → Agent-First (LangGraph) | 将解析/提取/校验拆分为独立 Agent，提升可测试性和扩展性 |
| 打包分发 | PyPI + Electron 桌面壳 | CLI 满足批量场景，GUI 满足非技术用户 |
| 影响因子 | AI 自动补全 + 人工校验 | 从期刊名称自动匹配 JCR/IF 数据，降低人工查表成本 |

## 4. 核心功能模块

### 4.1 PaperInsight CLI

**功能说明**：PDF 论文智能分析工具，支持从 PDF 中提取结构化数据并转换为 Excel/JSON 格式。

**主要特点**：
- Click CLI 命令行接口
- 双模式提取（LLM API + Regex 本地兜底）
- 多 LLM 后端支持（OpenAI/DeepSeek/Longcat）
- 完整的数据处理流程：PDF → 文本清洗 → 数据提取 → Excel/JSON

**应用场景**：科研论文数据提取，特别是器件性能数据的自动化处理。

### 4.2 Agent-First 重构

**功能说明**：基于 LangGraph 的多 Agent 工作流引擎，用于论文分析工具的架构重构。

**主要特点**：
- LangGraph 工作流编排
- Agent 职责分离与状态管理
- 从 v3 单体架构到 v4 Agent 架构的演进

**应用场景**：复杂科研数据处理流程的自动化和可扩展性提升。

### 4.3 翼界科技官网

**功能说明**：企业级服务展示平台，用于展示无人机生态保护服务。

**主要特点**：
- React + TypeScript + Vite 技术栈
- 响应式企业级前端架构
- 无人机生态保护服务展示

**应用场景**：企业品牌展示和服务推广。

### 4.4 量子点材料数据挖掘工具

**功能说明**：量子点材料科学数据挖掘工具，支持自动提取和分析量子点性能数据。

**主要特点**：
- 自动提取量子点性能数据
- 数据分析和可视化
- 与论文分析工具集成

**应用场景**：材料科学研究，特别是量子点材料的性能分析。

### 4.5 实验室自动化管理系统

**功能说明**：实验室自动化管理系统，集成实验设备控制与数据采集。

**主要特点**：
- 实验设备控制
- 数据采集和管理
- 自动化实验流程

**应用场景**：科研实验室的自动化管理和数据处理。

### 4.6 私有项目（脱敏后）

#### 4.6.1 AI 数据处理平台

**功能说明**：企业级数据处理与分析平台，支持大规模数据处理。

**主要特点**：
- 基于 FastAPI 的高性能后端
- MongoDB 数据存储
- 大规模数据处理能力

**应用场景**：企业级数据处理和分析，支持业务决策。

#### 4.6.2 智能文档管理系统

**功能说明**：基于 AI 的文档管理与检索系统。

**主要特点**：
- React 前端界面
- Node.js 后端
- PostgreSQL 数据库
- AI 驱动的文档检索

**应用场景**：企业内部文档管理和智能检索。

#### 4.6.3 自动化测试框架

**功能说明**：企业内部自动化测试工具，提高测试效率。

**主要特点**：
- 基于 pytest 的测试框架
- Selenium 自动化测试
- 自动化测试报告生成

**应用场景**：企业内部软件质量保证和测试自动化。

## 5. 核心 API/类/函数

由于这是一个个人资料仓库，不包含具体的代码实现。以下是开发者在其项目中使用的核心技术和库：

### 5.1 技术栈

**后端技术**：
- Python
- FastAPI
- PyTorch
- SQLite
- Pandas
- Click (CLI 框架)
- OpenAI API
- Docker

**前端技术**：
- TypeScript
- React
- Vite
- Tailwind CSS

### 5.2 工具和库

**PDF 处理**：
- MinerU CLI
- PaddleOCR

**LLM 集成**：
- OpenAI API
- DeepSeek API
- Longcat API

**工作流编排**：
- LangGraph

## 6. 技术栈与依赖

### 6.1 主要技术栈

| 类别 | 技术/工具 | 用途 |
|------|-----------|------|
| 后端 | Python | 核心开发语言 |
| 后端 | FastAPI | API 开发框架 |
| 后端 | PyTorch | 深度学习框架 |
| 后端 | Node.js | 后端开发语言 |
| 前端 | TypeScript | 前端开发语言 |
| 前端 | React | 前端框架 |
| 前端 | Vite | 构建工具 |
| 前端 | Tailwind CSS | CSS 框架 |
| 数据库 | SQLite | 轻量级数据库 |
| 数据库 | MongoDB | NoSQL 数据库 |
| 数据库 | PostgreSQL | 关系型数据库 |
| 数据处理 | Pandas | 数据处理库 |
| CLI 工具 | Click | 命令行接口框架 |
| AI 集成 | OpenAI API | 大语言模型接口 |
| 容器化 | Docker | 应用容器化 |
| 版本控制 | Git | 代码版本管理 |
| 操作系统 | Linux | 开发和部署环境 |

### 6.2 项目依赖

由于这是一个个人资料仓库，不包含具体的项目依赖文件。以下是开发者在其项目中可能使用的主要依赖：

- **paper-analysis-toolkit**：
  - PyPDF2 或 pdfminer.six（PDF 解析）
  - pandas（数据处理）
  - click（CLI 框架）
  - openai（LLM API 集成）
  - regex（正则表达式处理）

- **paper-analysis-toolkit-agentflow**：
  - langgraph（工作流编排）
  - langchain（LLM 工具链）
  - pydantic（数据验证）

- **company-base**：
  - react（前端框架）
  - typescript（类型系统）
  - vite（构建工具）
  - tailwindcss（样式框架）

- **quantum-dot-miner**：
  - pandas（数据处理）
  - matplotlib（数据可视化）
  - scikit-learn（数据分析）

- **lab-automation-system**：
  - fastapi（API 框架）
  - sqlalchemy（ORM）
  - pydantic（数据验证）

- **AI 数据处理平台**（私有）：
  - fastapi（API 框架）
  - motor（MongoDB 驱动）
  - pydantic（数据验证）

- **智能文档管理系统**（私有）：
  - react（前端框架）
  - node.js（后端）
  - express（Node.js 框架）
  - postgresql（数据库）

- **自动化测试框架**（私有）：
  - pytest（测试框架）
  - selenium（自动化测试）
  - allure-pytest（测试报告）

## 7. 关键模块与典型用例

### 7.1 PDF 论文智能分析

**功能说明**：从 PDF 论文中提取器件性能数据，转换为结构化 Excel/JSON 格式。

**配置与依赖**：
- 配置文件：CLI 配置和 LLM API 密钥
- 依赖：Python 3.8+，相关 Python 包

**使用示例**：
```bash
# 基本使用
paperinsight extract --input ./papers --output ./results

# 使用 LLM 模式
paperinsight extract --input ./papers --output ./results --mode llm

# 使用 Regex 兜底模式
paperinsight extract --input ./papers --output ./results --mode regex
```

### 7.2 Agent 工作流引擎

**功能说明**：使用 LangGraph 编排多 Agent 工作流，处理论文分析的各个环节。

**配置与依赖**：
- 配置文件：Agent 配置和工作流定义
- 依赖：langgraph，langchain，相关 Python 包

**使用示例**：
```python
# 初始化工作流
workflow = PaperAnalysisWorkflow()

# 运行工作流
result = await workflow.run(paper_path="./paper.pdf")

# 获取结果
print(result.extracted_data)
```

## 8. 配置、部署与开发

### 8.1 本地开发环境

**环境要求**：
- Python 3.8+
- Node.js 16+（前端项目）
- 相关依赖包

**安装步骤**：
1. 克隆项目仓库
2. 安装依赖：`pip install -r requirements.txt`（后端）或 `npm install`（前端）
3. 配置环境变量和 API 密钥
4. 运行开发服务器或 CLI 工具

### 8.2 部署方式

**后端项目**：
- PyPI 发布：`pip install paperinsight`
- Docker 容器化部署

**前端项目**：
- 静态网站部署（Vercel、Netlify 等）
- 企业内部服务器部署

### 8.3 持续集成/持续部署

- GitHub Actions 用于自动化测试和部署
- 代码质量检查和测试覆盖率监控

## 9. 监控与维护

### 9.1 日志与监控

- 命令行工具日志输出
- API 调用监控和错误处理
- 性能指标收集

### 9.2 常见问题与解决方案

| 问题 | 原因 | 解决方案 |
|------|------|----------|
| PDF 解析失败 | PDF 格式异常或扫描件 | 启用 OCR 兜底模式 |
| LLM API 调用失败 | API 密钥无效或网络问题 | 切换到 Regex 本地兜底模式 |
| 数据提取不准确 | 论文格式差异 | 调整提取规则或使用更精确的 LLM 模型 |
| 性能问题 | 处理大量论文 | 启用缓存机制和增量处理 |
| 量子点数据提取错误 | 数据格式不一致 | 优化数据提取规则和验证机制 |
| 实验室设备连接失败 | 网络问题或设备故障 | 检查网络连接和设备状态，重启服务 |
| MongoDB 连接问题 | 网络问题或配置错误 | 检查连接字符串和网络状态 |
| PostgreSQL 性能问题 | 数据库查询优化不足 | 优化查询语句和索引结构 |

## 10. 总结与亮点回顾

### 10.1 核心价值

- **科研自动化**：通过 AI 和自动化工具，将科研论文中的器件性能数据从 PDF 转换为结构化 Excel，提高科研效率
- **技术创新**：采用 LLM API + Regex 双模式提取策略，确保在各种情况下都能可靠地提取数据
- **架构演进**：从单体架构到 Agent-First 架构，提升系统的可测试性和扩展性
- **用户友好**：针对科研用户的非技术背景，提供零配置开箱即用的 CLI 工具和交互式配置向导

### 10.2 技术亮点

- **多模态数据处理**：结合 PDF 解析和 OCR 技术，处理各种类型的论文文档
- **智能数据提取**：利用 LLM 的理解能力，从非结构化文本中提取结构化数据
- **工作流编排**：使用 LangGraph 实现多 Agent 协作，处理复杂的科研数据处理流程
- **缓存机制**：通过 PDF MD5 指纹去重，避免重复解析，支持增量处理上百篇论文
- **多端支持**：同时提供 CLI 和 GUI 界面，满足不同用户的需求

### 10.3 应用前景

- **科研工具链**：为材料科学、化学、物理学等领域的研究者提供高效的数据提取工具
- **学术分析**：支持大规模论文数据挖掘和分析，发现研究趋势和热点
- **期刊影响因子自动补全**：从期刊名称自动匹配 JCR/IF 数据，降低人工查表成本
- **智能文献综述**：基于提取的数据，自动生成文献综述和比较分析

通过这些技术和工具，开发者为科研领域的自动化和智能化做出了贡献，提高了科研效率和数据处理的准确性。