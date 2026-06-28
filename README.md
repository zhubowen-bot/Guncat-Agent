# Guncat-Agent 全能智能体

> 结构化思维链 × 多 Agent 协同 × 60+ 工具生态 —— 新一代大模型智能体

[Guncat-Agent官网](https://guncat-agent.space-z.ai/) | [GitHub](https://github.com/Guncat-Agent/Guncat-Agent)

---

## 简介

Guncat 是新一代 AI 智能体框架，包含通用智能体（2.0/2.5/2.5-Pro）与面向准确信息检索的垂直智能体（Srch 系列）：

| 产品线                | 驱动方式        | 平台                  | 基座模型                             | 工具数量    | 开源情况     |
| ------------------ | ----------- | ------------------- | -------------------------------- | ------- | -------- |
| **Guncat 2.0 系列**  | Prompt 驱动   | 腾讯元器                | GLM-5 (200k)/混元preview 3.0       | Agent集群 | prompt开源 |
| **Guncat 2.5 系列**  | Prompt 驱动   | 腾讯元器                | GLM-5 (200k)/混元preview 3.0       | 基础工具    | prompt开源 |
| **Guncat 2.5-Pro** | Python 代码驱动 | python可移植，服务部署在Coze | API调用（Coze默认doubao-seed-2.0-Pro） | **60+** | 全项目开源    |
| **Guncat Srch 系列** | Prompt 驱动   | 智谱清言/腾讯元器           | GLM-4.7 / 混元preview 3.0          | 联网搜索    | prompt开源 |
| **Guncat Srch-Law V2** | Python 代码驱动 | python可移植，本地运行/API部署 | API调用（gpt-4o/claude-3-5-sonnet/qwen） | RAG+联网搜索 | **全项目开源** |

---

## 项目结构

```
Guncat-Agent/
├── Guncat 2.0/                    # Prompt驱动版本
│   ├── Guncat 2.0-flash-main_agent_prompt.md
│   └── Guncat 2.0-pro-main_agent_prompt.md
├── Guncat 2.5/                    # Sequential Thinking版本
│   ├── Guncat 2.5-lite_prompt.md
│   └── Guncat 2.5-max_prompt.md
├── Guncat 2.5-Pro-Project/        # Python代码驱动版本
│   ├── assets/                    # 静态资源
│   ├── config/                    # 配置文件
│   ├── scripts/                   # 运行脚本
│   ├── src/                       # 源代码
│   │   ├── agents/                # Agent实现
│   │   ├── graphs/                # LangGraph工作流
│   │   ├── storage/               # 存储层
│   │   ├── tools/                 # 工具集
│   │   ├── utils/                 # 工具函数
│   │   └── main.py                # 入口文件
│   ├── .coze                      # Coze配置
│   ├── .gitignore
│   ├── pyproject.toml             # 依赖配置
│   ├── README.md
│   └── uv.lock
├── Guncat Srch-Law/                # 法律检索智能体
│   └── Guncat Srch-Law V1.0-prompt.md
├── Guncat Srch-Research/           # 研究检索智能体
│   └── Guncat Srch-Research-prompt.md
├── Guncat Srch-Sift/               # 筛滤检索智能体
│   └── Guncat Srch-Sift-prompt.md
├── Guncat Srch-Law_v2-project/     # 法律检索智能体完整Agent应用
│   ├── agents/                     # 多Agent实现（Router/Contract/Compliance/Criminal）
│   ├── knowledge_base/             # RAG知识库（ChromaDB + bge-m3）
│   ├── output/                     # 输出格式化模块
│   ├── templates/                  # 法律意见书模板
│   ├── tests/                      # 测试文件
│   ├── tools/                      # 工具模块（联网搜索）
│   ├── README.md
│   ├── config.py                   # 配置文件
│   ├── main.py                     # 主入口
│   ├── requirements.txt
│   └── system_prompt_v2.md         # 强化版系统提示词
├── LICENSE
└── README.md
```

---

## Guncat 2.0 系列 - 全能Agent集群

基于 Prompt 驱动，全系搭载全能Agent集群，专注于完成复杂任务，成熟可靠。
2.0-pro 全过程通过子Agent协同工作，追求极致任务完成质量，支持超长程工作，支持长时间多轮对话不断链。
2.0-flash 通过主Agent调用工具，同时保留了pro的完整agent集群作为备选，通过重构提示词实现极致速度和可靠质量的绝佳统一。

### 版本矩阵

| 版本            | 定位   | 深度思考 | Agent能力  | 服务状态     | 工作方式                                |
| ------------- | ---- | ---- | -------- | -------- | ----------------------------------- |
| **2.0-pro**   | 旗舰   | ✅    | 最高       | 保留beta服务 | Multi-Agent协同，Prompt驱动              |
| **2.0-fast**  | 旗舰微调 | ❌    | 接近 Flash | 停止服务     | 主Agent工具调用+备用Multi-Agent协同，Prompt驱动 |
| **2.0-flash** | 极速   | ❌    | 优秀       | 正式版服务    | 主Agent工具调用+备用Multi-Agent协同，Prompt驱动 |

### 核心能力

**完整全能Agent集群**

联网搜索 图片理解 文档解析 第三方平台接入 高级文档处理与转换 高级图片处理 AI图片生成 视频剪辑与处理 代码解释器 脑图生成

---

## Guncat 2.5 系列 - Sequential Thinking 思维链

基于 Prompt 驱动，创新搭载 **Sequential Thinking** 结构化思维链与多 Agent 协同架构。

### 核心升级

**结构化思维链**

引入 Sequential Thinking 和任务 list，大幅提高多轮工具调用特别是快速模式下的稳定性、可视性、结构性和连续性。2.5 的 Sequential Thinking 让复杂任务的推理过程更加透明、可控。

**全新提示词架构**

2.5 版本完整描述工具的输入和输出参数，给出细致的输入规范，但不限制模型何时调用工具。相比 2.0 只列出工具并规定调用条件，反而更有利于模型的工具调用效率和准确性。

### 版本矩阵

| 版本                    | 定位  | 深度思考 | 速度 (vs 2.5-lite) | 质量  |
| --------------------- | --- | ---- | ---------------- | --- |
| **2.5-max**           | 旗舰  | ✅    | ~0.75x           | 最高  |
| **2.5-lite-thinking** | 推荐  | ✅    | ~0.9x            | 高   |
| **2.5-lite**          | 极速  | ❌    | 1x               | 高   |

### 核心能力

- 联网搜索
- 图片理解
- 文档解析
- 代码解释器
- 深度思考
- 多 Agent 协同
- 结构化思维链（Sequential Thinking）
- 暂不支持第三方平台接入、高级文档处理与转换、高级图片处理、AI 图片生成、视频剪辑与处理等，以上高级技能请暂时使用 Guncat 2.0系列/Guncat 2.5-Pro 版本

### 三档推理模式

模型自主选择推理策略：**极速模式**（不调用工具）→ **标准模式**（可调用工具）→ **深度模式**（Sequential Thinking + 多轮回溯）。

---

## Guncat 2.5-Pro -  LangChain / LangGraph 生态，Python 代码驱动

基于 **LangChain / LangGraph** 生态，Python 代码驱动，搭载 **doubao-seed-2.0-Pro**，国际第一梯队水平。

### 工具生态

| 领域   | 工具数量 | 工具列表                                                                                                                                                                                                   |
| ---- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 图片处理 | 9    | generate_image, image_understanding, extract_text_from_image, analyze_chart, compare_images, detect_objects, remove_watermark, enhance_image, style_transfer                                           |
| 视频处理 | 11   | generate_video, trim_video, concat_videos, extract_key_frames, extract_frames_by_interval, extract_audio, add_subtitles, auto_subtitle, analyze_video, extract_video_frames_count, combine_video_audio |
| 网页内容 | 8    | fetch_webpage, extract_text_from_url, extract_images_from_url, extract_links_from_url, analyze_article, convert_url_to_markdown, summarize_article, compare_articles                                   |
| 文档处理 | 11   | create_pdf, create_docx, create_pptx, create_excel, translate_text, summarize_document, qa_document, extract_table_from_document, create_report, convert_document_format, proofread_document           |
| 搜索服务 | 9    | web_search, web_search_with_ai_summary, image_search, search_news, academic_search, verify_information, get_knowledge_answer, compare_products, get_trending_topics                                    |
| 代码执行 | 12   | execute_python_code, calculate, generate_chart, parse_json, format_json, convert_data_format, generate_mindmap, analyze_data, generate_code, debug_code, explain_code, validate_json_schema            |

### 核心升级

- **Python 代码驱动**：工具调用和 Agent 逻辑由代码直接控制，更稳定、可控、可调试
- **LangGraph 生态**：支持复杂工作流编排、状态管理和多 Agent 协作
- **60+ 专业工具**：覆盖六大领域，数量与质量质的飞跃
- **速度 4x**：复杂任务速度约为 2.0-flash 的 4 倍

### 本地开发

```bash
# 进入项目目录
cd "Guncat 2.5-Pro-Project"

# 安装依赖（使用 uv）
uv sync

# 本地运行工作流
bash scripts/local_run.sh -m flow

# 运行指定节点
bash scripts/local_run.sh -m node -n node_name

# 启动 HTTP 服务
bash scripts/http_run.sh -m http -p 5000
```

### API 接口

| 接口                     | 方法   | 描述           |
| ---------------------- | ---- | ------------ |
| `/run`                 | POST | 同步执行工作流      |
| `/stream_run`          | POST | 流式执行工作流（SSE） |
| `/cancel/{run_id}`     | POST | 取消指定任务       |
| `/node_run/{node_id}`  | POST | 运行指定节点       |
| `/v1/chat/completions` | POST | OpenAI 兼容接口  |
| `/health`              | GET  | 健康检查         |
| `/graph_parameter`     | GET  | 获取图参数        |

---

## Guncat Srch 系列 - 准确信息检索智能体

区别于 Guncat 2.0 / 2.5 / 2.5-Pro 等通用智能体，**Guncat Srch 系列**专为实现**准确、可溯源的信息检索**而生，通过别出心裁的机制设计从源头大幅降低大模型幻觉问题。Law 与 Research 采用"强制多轮检索 + 多源交叉验证 + 时效性铁律"实现专业领域深度检索；Sift 则另辟蹊径，以"官方渠道溯源 → 实体状态锚定 → AI内容过滤"九步深度搜索法，专门解决搜索引擎中 AI 生成内容泛滥导致的信息污染问题。

基于 Prompt 驱动，运行于智谱清言/腾讯元器平台，搭载 GLM-4.7 / GLM-5 (200k) / 混元preview 3.0 基座模型，提供三个垂直领域的检索专家版本。

### 版本矩阵

| 版本                            | 定位         | 专精领域                                    | 检索轮次                 | 输出形态     |
| ----------------------------- | ---------- | --------------------------------------- | -------------------- | -------- |
| **Guncat Srch-Law V1.0**      | 国企法律分析专家   | 国有企业法律事务、商事/行政/刑事交叉案件、国资监管合规            | 强制 6 轮串行检索           | 结构化法律意见书 |
| **Guncat Srch-Research V1.0** | 多轮验证研究专家   | 跨领域信息检索、多源交叉验证、复杂概念辨析、趋势与风险评估           | 强制 4-6 轮搜索验证         | 结构化研究报告  |
| **Guncat Srch-Sift V1.0**     | AI信息筛滤检索专家 | 时效性强/幻觉率高的信息查询、AI生成内容过滤、官方一手信息溯源与实体状态锚定 | 九步深度搜索法（溯源→锚定→调研→筛滤） | 溯源验证报告   |

### 核心反幻觉机制

Guncat Srch 系列通过以下"别出心裁"的设计，从源头大幅减少幻觉：

**Law 与 Research 版本：**

- **强制多轮串行检索**：每次分析必须调用搜索工具执行多轮（Law 强制 6 轮，Research 至少 4-6 轮）按优先级排列的检索，覆盖权威来源、多视角交叉验证、数据验证、时效性校验等环节，杜绝"无检索即作答"
- **时效性铁律**：严禁引用已废止 / 已修订 / 已过时 / 来源不明的信息；每条引用必须标注法律名称+条款序号+最新修订日期（Law）或来源名称+发布时间（Research）
- **禁止臆断原则**：对不确定的问题必须明确标注"需进一步核实"并说明核实方向；Law 版本严禁编造案例，若无相关案例不得虚构
- **多源交叉验证矩阵**：Research 版本强制构建多源验证矩阵，将矛盾信息显性化，基于证据质量和逻辑一致性判断采信
- **权威来源优先**：优先选取置信度高的来源（政府网站、官媒、学术机构、权威媒体、官方公告、学术文献 DOI 等）
- **深度分析强制链**：6 条推理链强制执行，严禁以"篇幅限制"为由跳过任何深度分析步骤

**Sift 版本（筛滤检索）：**

Sift 针对"AI内容污染搜索引擎"这一核心问题，设计了完全不同的反幻觉路径：

- **官方渠道溯源（Official Source Tracing）**：在执行任何宽泛调研之前，强制为每个关键实体按 P0-P5 优先级查找官方信息源（官方网站/文档 → 官方社媒/博客 → 代码托管平台 → 官方应用商店 → 权威发布平台 → 权威评测机构），杜绝从二手解读中获取版本信息
- **实体状态锚定（Entity State Anchoring）**：仅以官方页面原文确认的版本号/状态为基准，非官方来源（尤其是 AI 生成内容）中的版本号一律不采信；多官方源矛盾时以发布时间最新者为准
- **AI内容识别与强制过滤**：对每条搜索结果执行六项检查（标题模式、作者信息、内容结构、时间表述、来源追溯、URL特征），识别"盘点/大全/终极指南"类 AI 综述、无署名文章、模板化内容、模糊时间表述等典型 AI 特征，分级降级处理
- **来源权威性 S-A-B-C-D 五级分级**：S级官方来源可直接采信，D级疑似AI内容原则上排除，C级仅作线索参考，建立严格的来源信任阶梯
- **时效敏感度分级评估**：检索前先判定问题时效敏感度（🔴极高/🟡中等/🟢较低），🔴极高敏感领域（科技产品版本、政策修订、赛事结果等）超过3个月即标记为可能过时
- **"先溯源→后锚定→再调研"思维纪律**：没有找到官方渠道之前绝不确认任何版本号/状态；历史信息物理隔离于"当前状态"描述；核心信念——"你对任何实体的当前状态一无所知，必须通过官方渠道去发现"
- **AI内容包围突破策略**：当某轮搜索 AI 内容占比超 80% 时，自动切换搜索词加入"官网""官方公告""Release""白皮书"等一手信息限定词，必要时尝试英文关键词突破

### 核心能力

**Guncat Srch-Law（国企法律分析专家）**

- 深度解析复杂商事、行政及刑事交叉案件
- 精准适用最新法律法规、司法解释及国资监管规定
- 识别国企特殊法律风险（国资监管、合规、反腐败、三重一大等）
- 法律概念精细化辨析（法定概念 vs 约定概念）
- 合同体系化解释方法论（体系 / 目的 / 文义 / 历史 / 诚信解释）
- 法理深度分析工具箱（整体对价理论、不当得利理论、权利义务一致性、受益分析法等）
- 实务操作精细化（保全措施、跨境执行、证据链构建）

**Guncat Srch-Research（多轮验证研究专家）**

- 跨领域信息检索与多源交叉验证
- 复杂概念辨析与术语精准定义
- 多维度信息整合与逻辑推演
- 时效性校验与信息置信度评估
- 分析工具箱（整体关联理论、利益相关方分析、因果链分析、反事实推演、基准线对比、矛盾识别法等）
- 结构化研究报告生成（含检索轮次记录、交叉验证矩阵、风险识别表）

**Guncat Srch-Sift（AI信息筛滤检索专家）**

- 官方渠道溯源（P0-P5 六级优先级查找一手信息源）
- 实体状态锚定（仅以官方原文确认当前版本/状态，拒绝转述）
- AI生成内容智能识别与过滤（标题模式/作者信息/内容结构/时间表述/来源追溯/URL特征六项检查）
- 来源权威性 S-A-B-C-D 五级分级与分级采信
- 时效敏感度分级评估（🔴极高/🟡中等/🟢较低）与信息半衰期判断
- 九步深度搜索法（意图解析→官方溯源→状态锚定→搜索设计→执行搜索→AI过滤→信息整合→来源标注→格式化输出）
- AI内容包围突破策略（自动切换一手信息限定词、英文关键词突破）
- 溯源验证报告生成（含官方渠道URL、原文引用、来源分级、时效性标记、信息可靠性评估）

### 工作流

**Law 与 Research 版本**共享四阶段工作流，在检索轮次和分析维度上各有侧重：

1. **信息澄清与背景确认**：确认基本事实、主体、诉求，提取关键术语建立"术语对照表"备用
2. **实时多轮检索 / 验证（强制）**：按优先级串行执行多轮检索，覆盖最新法规 / 事实、权威来源、多视角交叉、数据验证、时效性校验、细节补充
3. **复杂推理分析（强制）**：6 条推理链执行深度分析（术语辨析 → 体系化解释 → 特殊规则适用 → 深度分析 → 风险推演 → 建议与实务操作）
4. **输出结构化报告**：法律意见书 / 研究报告，含术语辨析表、来源验证矩阵、深度分析表、风险识别表、建议与实务操作

**Sift 版本**采用九步深度搜索法，核心逻辑为"先溯源→后锚定→再调研→筛滤输出"：

1. **查询意图与时效敏感度解析**：分析显性/隐性需求，判定时效敏感度（🔴极高/🟡中等/🟢较低），识别可能已变化的关键实体
2. **官方渠道溯源（核心步骤）**：为每个关键实体按 P0-P5 优先级查找官方信息源（官网→官方社媒→代码仓库→应用商店→权威发布→评测机构），执行5轮定向搜索，识别并降级AI内容
3. **实体状态锚定**：从官方渠道提取最新版本/状态原文，多官方源交叉验证，校准用户查询中的过时假设
4. **搜索策略设计**：基于官方确认的最新状态设计精准搜索词（官方状态前置+时间版本双锚定+排除AI内容）
5. **执行搜索与原始数据获取**：逐轮执行搜索，记录官方源占比与时间分布
6. **结果质量评估与AI内容过滤**：对每条结果进行S-A-B-C-D来源分级、AI内容六项强制检查、时效性检查，标记🟢官方确认/🟢当前有效/🟡历史参考/🔴过时排除/⚠️AI嫌疑/❓待验证
7. **信息整合与状态校准**：以官方锚定状态为唯一基准，历史信息物理隔离于当前状态，矛盾时以官方最新来源为准
8. **来源标注与可追溯性**：每条信息标注来源等级、时效性状态，AI嫌疑内容强制标注，推测性内容明确标注
9. **最终输出格式化**：生成溯源验证报告，含查询理解、时效评估、官方溯源结果、实体锚定结果、核心发现、详细信息、可靠性评估、来源分级清单、时效性声明

---

## Guncat Srch-Law V2 - 国企法律智能分析 Agent 系统（Python 代码驱动）

Guncat Srch-Law V2 是 Srch-Law V1.0 的**完整 Agent 应用升级版本**，从 Prompt 驱动升级为 **Python 代码驱动的 Multi-Agent 系统**，引入 RAG 知识库、联网实时检索、结构化输出等完整能力，实现从"提示词智能体"到"应用级智能系统"的跨越。

### 核心升级（相较于 V1.0）

| 升级维度 | V1.0（Prompt 驱动） | V2.0（Python 代码驱动） |
|---------|-------------------|----------------------|
| **架构** | 单体 Prompt，依赖平台工具调用 | Multi-Agent 路由架构（RouterAgent + ContractAgent + ComplianceAgent + CriminalAgent） |
| **知识库** | 仅依赖联网搜索，无本地知识 | **RAG 法律条文知识库**（ChromaDB + bge-m3 向量化），预加载核心法律法规 |
| **检索方式** | 依赖平台联网搜索能力 | 本地 RAG 检索 + 联网实时检索双引擎，确保法条引用准确 |
| **输出格式** | Markdown 文本输出 | Markdown / Word / PDF 三种结构化格式，含法律意见书模板 |
| **国企合规** | Prompt 中约定分析流程 | **专项 ComplianceAgent**，针对"三重一大"、国资监管、关联交易等国企特有场景专项优化 |
| **刑事风险** | Prompt 中覆盖分析 | **专项 CriminalAgent**，刑法第165-169条（国企相关犯罪）全覆盖 |
| **可移植性** | 依赖智谱清言/腾讯元器平台 | Python 可移植，支持本地运行 / FastAPI 部署 / Coze 集成 |
| **可控性** | 模型自主控制流程 | 代码控制工作流，步骤可追溯、可调试 |

### 系统架构

```
用户输入
   ↓
RouterAgent（意图识别与案件分类）
   ↓
┌─────────┬─────────┬─────────┐
│ 合同解析 │ 国企合规  │ 刑事风险  │
│ Agent   │ Agent   │ Agent   │
└─────────┴─────────┴─────────┘
   ↓
工具层：RAG 检索（ChromaDB） / 联网搜索 / 案例检索
   ↓
记忆与状态管理
   ↓
结构化法律意见书输出（Markdown / Word / PDF）
```

### Multi-Agent 架构

| Agent | 路径 | 功能 | 专精场景 |
|-------|------|------|---------|
| **RouterAgent** | `agents/router_agent.py` | 意图识别、案件分类、路由决策 | 自动判断案件类型（合同纠纷/国企合规/刑事风险/综合） |
| **ContractAgent** | `agents/contract_agent.py` | 合同解析分析 | 合同体系化解释（五步法）、关键术语辨析、违约责任分析 |
| **ComplianceAgent** | `agents/compliance_agent.py` | 国企合规审查 | "三重一大"决策程序、国资监管程序合规、关联交易审查、国有资产流失风险 |
| **CriminalAgent** | `agents/criminal_agent.py` | 刑事风险评估 | 刑法第165-169条全覆盖、职务犯罪风险推演、管理人员责任分析 |

### RAG 知识库

基于 **ChromaDB** 向量数据库 + **bge-m3** 中文向量化模型，预加载核心法律法规：

| 类别 | 法规数量 | 法规列表 |
|------|---------|---------|
| 法律 | 4 部 | 企业国有资产法、公司法（2023修订）、行政处罚法、刑法（国企相关条款） |
| 行政法规 | 2 部 | 企业国有资产交易监督管理办法（32号令）、企业国有资产监督管理暂行条例 |
| 国资委规范性文件 | 4 部 | "三重一大"决策制度意见、中央企业合规管理办法、国有企业参股管理暂行办法、企业国有资产评估管理暂行办法 |
| 司法解释 | 5 部 | 最高法公司法司法解释（一~五） |

### 核心能力

- **Multi-Agent 路由架构**：自动识别案件类型，路由到专用子Agent
- **RAG 法律条文检索**：基于 ChromaDB 向量化检索，确保法条引用准确
- **联网实时检索**：搜索最新法律法规、司法解释、裁判案例，补充时效性信息
- **合同解释五步法**：体系解释 → 目的解释 → 文义解释 → 历史解释 → 诚信解释，缺一不可
- **法理分析工具箱**：整体对价理论、不当得利理论、权利义务一致性、受益分析法等深层法理工具
- **国企合规专项强化**：国资监管程序合规、"三重一大"决策程序、关联交易审查、管理人员责任分析
- **刑事风险全覆盖**：刑法第165-169条（非法经营同类营业、为亲友非法牟利、失职被骗、滥用职权、低价折股出售国有资产等）
- **结构化法律意见书输出**：Markdown / Word / PDF 三种格式，含完整模板

### 工作流

1. **案件分类**：RouterAgent 分析案件描述，判断案件类型，路由到对应子Agent
2. **RAG 知识库检索**：检索本地法律条文知识库，获取相关法条原文，标注来源文件名称、条款序号、生效日期
3. **联网实时检索**：搜索最新法律法规（2024-2026新修订）、司法解释、国资委最新监管文件、近期裁判案例，执行时效性校验
4. **深度推理分析**：子Agent 执行 6 条推理链（法律关系解构 → 合同体系化解释 → 国企特殊规则适用 → 法理深度分析 → 责任风险推演 → 合规建议）
5. **格式化输出**：生成结构化法律意见书，支持 Markdown / Word / PDF 输出

### 快速开始

```bash
# 进入项目目录
cd "Guncat Srch-Law_v2-project"

# 安装依赖
pip install -r requirements.txt

# 配置 API 密钥
export LLM_API_KEY="your-api-key"
export LLM_MODEL="gpt-4o"  # 或 claude-3-5-sonnet、qwen 等

# 交互式运行
python main.py --mode interactive

# 文件输入模式
python main.py --mode file --input case_description.txt --format markdown
```

### 依赖说明

主要依赖：
- `langchain` / `langchain-openai` - LLM 调用框架
- `langgraph` - Multi-Agent 编排（扩展预留）
- `chromadb` - 向量数据库
- `sentence-transformers` - 中文文本向量化（bge-m3，首次运行自动下载约 2GB）
- `python-docx` - Word 文档生成
- `weasyprint` - PDF 生成（可选）

### 扩展建议

- **接入真实法律数据库 API**：北大法宝、裁判文书网、国家法律法规数据库
- **增强 RAG 知识库**：加载更多法律法规全文（建议至少 20 部核心法规），定期更新（每季度）
- **升级 LangGraph 编排**：支持 Agent 条件跳转、并行调用、推理过程可追溯
- **部署为 API 服务**：使用 FastAPI 封装，提供 HTTP API

### 测试

```bash
python tests/test_basic.py
```

---

## 版本对比

| 特性               | 2.5-Pro                         | 2.5-max      | 2.5-lite-thinking | 2.5-lite     | 2.0-flash    |
| ---------------- | ------------------------------- | ------------ | ----------------- | ------------ | ------------ |
| 架构               | Python/LangGraph                | Prompt 驱动    | Prompt 驱动         | Prompt 驱动    | Prompt 驱动    |
| 基座模型             | API调用，Coze提供doubao-seed-2.0-Pro | GLM-5 (200k) | GLM-5 (200k)      | GLM-5 (200k) | GLM-5 (200k) |
| 服务平台             | Coze                            | 腾讯元器         | 腾讯元器              | 腾讯元器         | 腾讯元器         |
| 深度思考             | ✅                               | ✅            | ✅                 | —            | —            |
| 工具数量             | 60+                             | 基础工具         | 基础工具              | 基础工具         | 基础+高级        |
| 图片处理             | 9 个工具                           | 图片理解         | 图片理解              | 图片理解         | 理解+生成        |
| 视频处理             | 11 个工具                          | —            | —                 | —            | 剪辑+处理        |
| 文档处理             | 11 个工具                          | 文档解析         | 文档解析              | 文档解析         | 解析+转换+生成     |
| 代码执行             | 12 个工具                          | 代码解释器        | 代码解释器             | 代码解释器        | 代码解释器        |
| 速度 (vs 2.5-lite) | 2x                              | 0.75x        | 0.9x              | 1x           | 1.1x         |
| 质量水平             | 国际第一梯队                          | 最高           | 高                 | 接近 Flash     | 优秀           |
| 对话方式             | 在线对话/API                        | API/元器平台     | API/元器平台          | API/元器平台     | API/元器平台     |

---

## 快速开始

### API 接入（Guncat 2.0/2.5 系列）

```python
import requests

url = "https://yuanqi.tencent.com/openapi/v1/agent/chat/completions"

headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer your-appkey"
}

data = {
    "assistant_id": "your-appid",
    "user_id": "user123",
    "stream": False,
    "messages": [
        {
            "role": "user",
            "content": [{"type": "text", "text": "你好"}]
        }
    ]
}

response = requests.post(url, headers=headers, json=data)
print(response.json()["choices"][0]["message"]["content"])
```

### 元器平台智能体 AppID

| 版本                | AppID                 |
| ----------------- | --------------------- |
| 2.5-max           | `2055612536249838656` |
| 2.5-lite-thinking | `2055564062957960256` |
| 2.5-lite          | `2055608596077149248` |
| 2.0-flash         | `2037888361351429632` |

### API 接入（Guncat 2.5-Pro）

```python
import requests

url = "https://b5k862mms8.coze.site/stream_run"
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_TOKEN"
}
data = {
    "content": {
        "query": {
            "prompt": [{
                "type": "text",
                "content": {"text": "你好"}
            }]
        }
    },
    "type": "query",
    "session_id": "your-session-id",
    "project_id": 7640359605809397803
}

response = requests.post(url, headers=headers, json=data, stream=True)
for line in response.iter_lines():
    if line:
        print(line.decode("utf-8"))
```

---

## 技术架构

- **Guncat 2.5 系列**：Prompt 驱动，运行于腾讯元器平台。引入 Sequential Thinking 结构化思维链，要求多次回溯、更细致的任务拆解，大幅提高多轮工具调用的稳定性和连续性。
- **Guncat 2.5-Pro**：Python 代码 + LangChain/LangGraph 驱动，服务部署于 Coze 平台。支持复杂工作流编排、状态管理和多 Agent 协作，工具调用和 Agent 逻辑由代码直接控制。
- **Guncat Srch 系列**：Prompt 驱动，运行于智谱清言/腾讯元器平台。Law 与 Research 通过强制多轮串行检索、多源交叉验证、时效性铁律和禁止臆断等机制实现专业领域深度检索；Sift 则通过官方渠道溯源、实体状态锚定和 AI 内容强制过滤等独特机制，专门解决搜索引擎中 AI 生成内容泛滥导致的信息污染问题。三个版本分别覆盖法律、研究、通用时效性信息查询三个垂直领域。
- **Guncat Srch-Law V2**：Python 代码驱动，基于 LangChain 框架的完整 Agent 应用系统。从 Srch-Law V1.0 的 Prompt 驱动升级为 Multi-Agent 路由架构（Router + Contract + Compliance + Criminal），引入 RAG 法律条文知识库（ChromaDB + bge-m3）、联网实时检索、结构化法律意见书输出（Markdown/Word/PDF）。实现从"提示词智能体"到"应用级智能系统"的跨越，Python 可移植，支持本地运行、FastAPI 部署或平台集成。

通用智能体（2.5 / 2.5-Pro）、垂直检索智能体（Srch 系列）与垂直 Agent 应用（Srch-Law V2）形成三层产品矩阵：
- **通用智能体**：追求全能与复杂任务协同
- **垂直检索智能体（Srch 系列）**：追求准确与可溯源的 Prompt 级快速部署
- **垂直 Agent 应用（Srch-Law V2）**：追求深度、可控、可扩展的应用级完整系统

---

## 历史版本

- **Guncat 2.0-pro**：最初 preview 版本，开启深度思考，完整 agent 集群模式，追求绝对质量，后保留为 `2.0-pro-beta`。
- **Guncat 2.0-fast**：preview 版本，不开启深度思考，搭配完整 agent 集群，后演进为正式版 `2.0-flash`，原 fast 版本不再保留。

---

## 许可证

MIT License

Copyright (c) 2026 Zhu Bowen

---

## 联系方式

📧 bowen_zbw@sjtu.edu.cn

🌐 [guncat-agent.space-z.ai](https://guncat-agent.space-z.ai)
