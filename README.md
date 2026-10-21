# Lab5：聊天应用持续集成

沿用本人 Lab2 的 Flask 聊天应用，支持多个会话及聊天记录的创建、查询、修改和删除。

## 文件与接口

- `app.py`：Flask 后端入口；`get_ai_reply()` 负责调用模型。
- `frontend/`：HTML、CSS 和 JavaScript 页面。
- `requirements.txt`：应用依赖。
- `.env.example`：配置示例，只有占位值。
- `data/conversations.json`：会话持久化文件，初始为空数组。

`GET /` 返回首页，`GET /api/hello` 返回 `{"message":"你好"}`。
`/api/conversations` 管理会话；`/api/conversations/<id>/messages` 及其消息 ID 子路径提供聊天记录 CRUD。修改消息仅更新问题文本，保留已有回答。

## 本地环境

在本仓库根目录用 PowerShell 执行：

```powershell
py -3.13 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe app.py
```

浏览器访问 http://localhost:5001/，按 Ctrl+C 停止服务。
首页和连通性接口不需要真实 API Key；真实聊天调用由 `DEEPSEEK_API_KEY` 配置。Lab5 自动测试将模拟模型调用，不需要真实 Key。
