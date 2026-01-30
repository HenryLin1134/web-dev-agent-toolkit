# GitHub Copilot Agents 設置指南

## 前置要求

- GitHub Copilot 訂閱
- VS Code 1.80+
- GitHub Copilot 擴充已安裝
- Git 2.0+

## 安裝步驟

### 第1步: 驗證目錄結構

確認 `.github/copilot-agents/` 包含以下文件：

```
.github/copilot-agents/
├── agents.json
├── README.md
├── SETUP.md
├── USAGE.md
├── agents/
│   ├── *.json files (個別agent配置)
│   └── ...
└── prompts/
    ├── *.md files (agent prompt文檔)
    └── ...
```

### 第2步: 配置 VS Code

1. 打開 VS Code 設置 (`Ctrl+,` 或 `Cmd+,`)
2. 搜索 "copilot"
3. 找到 `GitHub Copilot: Agent Configuration`
4. 設置為：`.github/copilot-agents/agents.json`

或在 `settings.json` 中直接添加：

```json
{
  "github.copilot.agent.config": ".github/copilot-agents/agents.json"
}
```

### 第3步: 重啟 VS Code

重啟 VS Code 使設置生效。

### 第4步: 驗證安裝

1. 打開 Copilot 聊天面板 (`Ctrl+Shift+I`)
2. 輸入 `@` 查看可用的 agents
3. 確認所有 8 個 agents 都列出來：
   - @brain-orchestrator
   - @planning-agent
   - @implementation-agent
   - @testing-agent
   - @debug-agent
   - @fix-agent
   - @enhancement-agent
   - @release-agent

## 自訂配置

### 修改 Agent 提示

編輯 `prompts/` 中的 markdown 文件：

```markdown
# [Agent Name]

## 角色定義

... (編輯這裡)

## 職責

... (編輯這裡)
```

### 添加新的 Agent

1. 在 `agents.json` 的 `agents` 陣列中添加條目：

```json
{
  "id": "custom-agent",
  "name": "Custom Agent",
  "emoji": "🎯",
  "description": "Custom agent description",
  "role": "Custom Role",
  "capabilities": ["capability1", "capability2"],
  "prompt_file": "prompts/custom_agent.md",
  "outputs": ["output1"]
}
```

2. 在 `prompts/` 中創建對應的 markdown 文件：

```bash
touch .github/copilot-agents/prompts/custom_agent.md
```

3. 編寫 agent 提示內容

### 定義工作流程

在 `agents.json` 的 `workflows` 陣列中添加：

```json
{
  "id": "custom-workflow",
  "name": "Custom Workflow",
  "description": "Custom workflow description",
  "steps": ["planning-agent", "implementation-agent", "testing-agent"],
  "error_handling": "debug-agent"
}
```

## 環境變數配置

### 設置專案根目錄

在 VS Code 工作區設置中：

```json
{
  "github.copilot.projectRoot": "${workspaceFolder}/projects"
}
```

### 設置 Change Log 目錄

編輯 `agents.json`：

```json
{
  "configuration": {
    "changelog_directory": "projects/",
    "log_level": "info"
  }
}
```

## 集成 Git

### 配置 Git Hook (可選)

創建 `.git/hooks/pre-commit`：

```bash
#!/bin/bash
# 驗證 agents.json 語法
json_verify() {
  python -m json.tool .github/copilot-agents/agents.json > /dev/null
  if [ $? -ne 0 ]; then
    echo "Invalid agents.json"
    exit 1
  fi
}

json_verify
```

## 效能優化

### 減少Change Log大小

在 `agents.json` 中設置：

```json
{
  "configuration": {
    "max_changelog_entries": 100,
    "archive_older_than_days": 30
  }
}
```

### 啟用快取

```json
{
  "configuration": {
    "cache_enabled": true,
    "cache_ttl_hours": 24
  }
}
```

## 安全設置

### 權限配置

確保 `.github/copilot-agents/` 的適當權限：

```bash
chmod 644 .github/copilot-agents/agents.json
chmod 644 .github/copilot-agents/prompts/*.md
chmod 755 .github/copilot-agents/
```

### 敏感信息保護

不要在 prompts 中包含：

- API keys
- 密碼
- 個人信息
- 內部系統地址

## 故障排除

### Problem: Agents 不出現

**解決方案**:

1. 檢查 `agents.json` 語法: `json_verify`
2. 重新啟動 VS Code
3. 檢查 Copilot 擴充版本 >= 1.150.0

### Problem: Prompt 文件未找到

**解決方案**:

1. 驗證文件路徑是否正確
2. 檢查大小寫是否匹配
3. 確認文件編碼為 UTF-8

### Problem: Change Log 未生成

**解決方案**:

1. 檢查 changelog_directory 權限
2. 驗證 project_root 設置正確
3. 查看 Copilot 控制台日誌

### Problem: Agent 響應不符合預期

**解決方案**:

1. 檢查 prompt 文件內容
2. 驗證 agent 角色定義清晰
3. 查看 capabilities 列表是否完整

## 驗證檢查清單

- [ ] `agents.json` 存在且語法正確
- [ ] 所有 8 個 agent prompts 都存在
- [ ] VS Code 設置指向正確的 config 文件
- [ ] Copilot 擴充已啟用
- [ ] 所有 agent 都在 Copilot 聊天中出現
- [ ] 可以成功調用至少一個 agent
- [ ] Change Log 目錄存在且可寫入

## 後續步驟

1. 查看 [USAGE.md](USAGE.md) 了解如何使用 agents
2. 根據項目需求自訂 prompts
3. 定義適合你的工作流程
4. 監控 Change Logs 確保正常運作

## 支援資源

- [GitHub Copilot 文檔](https://docs.github.com/en/copilot)
- [VS Code Copilot 設置](https://code.visualstudio.com/docs/editor/artificial-intelligence)
- 查看 `README.md` 的常見問題

---

**設置完成後**，請進行 [使用指南](USAGE.md) 的第一步測試。
