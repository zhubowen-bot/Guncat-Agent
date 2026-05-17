# Guncat-Agent 全能智能体

> 结构化思维链 × 多 Agent 协同 × 60+ 工具生态 —— 新一代大模型智能体

[Guncat-Agent官网](https://guncat-agent.space-z.ai/) | [GitHub](https://github.com/Guncat-Agent/Guncat-Agent)

---

## 简介

Guncat 是新一代 AI 智能体框架，包含两条平行的产品线：

| 产品线                | 驱动方式        | 平台                  | 基座模型                             | 工具数量    | 开源情况     |
| ------------------ | ----------- | ------------------- | -------------------------------- | ------- | -------- |
| **Guncat 2.0 系列**  | Prompt 驱动   | 腾讯元器                | GLM-5 (200k)                     | Agent集群 | prompt开源 |
| **Guncat 2.5 系列**  | Prompt 驱动   | 腾讯元器                | GLM-5 (200k)                     | 基础工具    | prompt开源 |
| **Guncat 2.5-Pro** | Python 代码驱动 | python可移植，服务部署在Coze | API调用（Coze默认doubao-seed-2.0-Pro） | **60+** | 全项目开源    |

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

| 领域   | 工具数量 | 工具列表 |
| ---- | ---- | ---- |
| 图片处理 | 9    | generate_image, image_understanding, extract_text_from_image, analyze_chart, compare_images, detect_objects, remove_watermark, enhance_image, style_transfer |
| 视频处理 | 11   | generate_video, trim_video, concat_videos, extract_key_frames, extract_frames_by_interval, extract_audio, add_subtitles, auto_subtitle, analyze_video, extract_video_frames_count, combine_video_audio |
| 网页内容 | 8    | fetch_webpage, extract_text_from_url, extract_images_from_url, extract_links_from_url, analyze_article, convert_url_to_markdown, summarize_article, compare_articles |
| 文档处理 | 11   | create_pdf, create_docx, create_pptx, create_excel, translate_text, summarize_document, qa_document, extract_table_from_document, create_report, convert_document_format, proofread_document |
| 搜索服务 | 9    | web_search, web_search_with_ai_summary, image_search, search_news, academic_search, verify_information, get_knowledge_answer, compare_products, get_trending_topics |
| 代码执行 | 12   | execute_python_code, calculate, generate_chart, parse_json, format_json, convert_data_format, generate_mindmap, analyze_data, generate_code, debug_code, explain_code, validate_json_schema |

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

| 接口 | 方法 | 描述 |
| ---- | ---- | ---- |
| `/run` | POST | 同步执行工作流 |
| `/stream_run` | POST | 流式执行工作流（SSE） |
| `/cancel/{run_id}` | POST | 取消指定任务 |
| `/node_run/{node_id}` | POST | 运行指定节点 |
| `/v1/chat/completions` | POST | OpenAI 兼容接口 |
| `/health` | GET | 健康检查 |
| `/graph_parameter` | GET | 获取图参数 |

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

两条产品线在技术架构、底层模型和运行平台上**完全隔离**，互为补充。

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


