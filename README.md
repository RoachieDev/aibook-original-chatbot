# 我的 AI 助手

基于 Streamlit 的网页对话助手，通过 OpenAI 兼容接口调用大模型（默认 DeepSeek），支持多轮对话与流式输出。

## 环境要求

- Python 3.9 及以上
- 可用的 API Key（如 [DeepSeek](https://platform.deepseek.com/)）

## 运行步骤

### 1. 克隆项目

```bash
git clone <仓库地址>
cd aibook-original-chatbot
```

### 2. 创建并激活虚拟环境（推荐）

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

### 3. 安装依赖

```bash
pip install -r requirements.txt
```

### 4. 配置环境变量

复制示例文件并填入你的 API 信息：

```bash
cp .env.example .env
```

编辑 `.env`，至少配置以下项：

| 变量 | 说明 | 示例 |
|------|------|------|
| `API_KEY` | 大模型 API 密钥 | `sk-xxx` |
| `BASE_URL` | API 基础地址 | `https://api.deepseek.com` |
| `MODEL_PROVIDER` | 模型提供方名称（界面展示用） | `DeepSeek` |
| `MODEL_NAME` | 模型 ID | `deepseek-v4-flash` |

### 5. 启动应用

```bash
streamlit run chatbot.py
```

终端会输出本地访问地址，一般为：

```
http://localhost:8501
```

在浏览器中打开该地址即可开始对话。输入 `Ctrl+C` 可停止服务。

## 项目结构

```
aibook-original-chatbot/
├── chatbot.py        # Streamlit 主程序
├── requirements.txt  # Python 依赖
├── .env.example      # 环境变量示例
└── README.md
```

## 使用说明

- 在页面底部输入框中输入问题并回车发送。
- 对话历史会在当前会话中保留，刷新页面会清空历史。
- 如需更换模型或服务商，修改 `.env` 中的 `BASE_URL` 与 `MODEL_NAME` 后重启应用即可。

## 常见问题

**启动报错：找不到 API Key**  
请确认项目根目录存在 `.env` 文件，且 `API_KEY` 已正确填写。

**请求失败或返回错误**  
检查 `BASE_URL`、`MODEL_NAME` 是否与你的 API 服务商文档一致，并确认账户余额与密钥权限正常。

**端口被占用**  
可指定其他端口启动：

```bash
streamlit run chatbot.py --server.port 8502
```
