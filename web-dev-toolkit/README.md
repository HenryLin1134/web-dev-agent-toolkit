# GitHub Copilot Custom Agents Configuration

這是一個完整的 GitHub Copilot 自定義 agent 套件，將 agent-toolkit 轉換為 Copilot 兼容的格式。

## 📋 文件結構

```
.github/copilot-agents/
├── agents.json                    # 主配置文件
├── README.md                      # 這個文件
├── SETUP.md                       # 設置指南
├── USAGE.md                       # 使用指南
├── agents/                        # Agent 配置文件
│   ├── brain-orchestrator.json
│   ├── planning-agent.json
│   ├── implementation-agent.json
│   ├── testing-agent.json
│   ├── debug-agent.json
│   ├── fix-agent.json
│   ├── enhancement-agent.json
│   └── release-agent.json
└── prompts/                       # Agent 提示文檔
    ├── brain_orchestrator.md
    ├── planning_agent.md
    ├── implementation_agent.md
    ├── testing_agent.md
    ├── debug_agent.md
    ├── fix_agent.md
    ├── enhancement_agent.md
    └── release_agent.md
```

## 🎯 8個核心Agent

### 🧠 Brain Orchestrator (大腦統整者)

- **角色**: 中央協調器
- **職責**: 統籌所有agent工作，管理工作流程
- **調用**: 其他所有agent

### 📋 Planning Agent (計畫Agent)

- **角色**: 項目規劃專家
- **職責**: 需求分析、技術設計、任務分解
- **產出**: 計畫文件和技術規格

### 💻 Implementation Agent (實作Agent)

- **角色**: 高級軟體工程師
- **職責**: 代碼生成、架構實現、集成開發
- **產出**: 源代碼和配置文件

### 🧪 Testing Agent (測試Agent)

- **角色**: QA專家
- **職責**: 功能測試、單元測試、性能測試
- **產出**: 測試報告和測試結果

### 🐛 Debug Agent (調試Agent)

- **角色**: 診斷專家
- **職責**: 問題診斷、根本原因分析
- **產出**: 調試報告和修復建議

### 🔧 Fix Agent (修復Agent)

- **角色**: 問題解決專家
- **職責**: 代碼修復、質量保證、回歸測試
- **產出**: 修復代碼和修復摘要

### ✨ Enhancement Agent (擴充Agent)

- **角色**: 產品增強專家
- **職責**: 功能設計、功能實現、集成測試
- **產出**: 新增功能和改進代碼

### 🚀 Release Agent (發行Agent)

- **角色**: 發行經理
- **職責**: 版本管理、構建打包、部署準備
- **產出**: 發行說明和部署清單

## 🔄 工作流程

### 標準開發流程

```
需求輸入
  ↓
計畫Agent ─→ 實作Agent ─→ 測試Agent ─→ 擴充Agent ─→ 發行Agent
                              ↓ (失敗)
                           Debug Agent ─→ 修復Agent ─→ 回到測試
```

### Bug修復流程

```
Debug Agent ─→ 修復Agent ─→ 測試Agent ─→ 發行Agent
```

### 功能增強流程

```
計畫Agent ─→ 擴充Agent ─→ 測試Agent ─→ 發行Agent
```

## 🚀 快速開始

1. **複製到你的專案**

   ```bash
   cp -r .github/copilot-agents your-project/.github/
   ```

2. **配置 GitHub Copilot**
   - 在 VS Code 中安裝 GitHub Copilot 擴充
   - 在 Copilot 設定中指向此配置文件

3. **使用 Agent**
   - 在 Copilot 聊天中提及 agent 名稱
   - 例如：「@brain-orchestrator 請幫我規劃一個新專案」

## 📝 配置說明

### agents.json 結構

```json
{
  "version": "1.0.0",
  "name": "Web Development Toolkit",
  "agents": [
    {
      "id": "agent-id",
      "name": "Agent Name",
      "emoji": "🎯",
      "description": "Agent description",
      "role": "Role type",
      "capabilities": ["capability1", "capability2"],
      "prompt_file": "prompts/file.md",
      "outputs": ["output1", "output2"],
      "can_invoke": ["other-agent-id"]
    }
  ],
  "workflows": [
    {
      "id": "workflow-id",
      "name": "Workflow Name",
      "steps": ["agent-id1", "agent-id2"],
      "error_handling": "agent-id"
    }
  ]
}
```

## 🔧 自訂設置

### 修改Agent能力

編輯 `agents.json` 中的 `capabilities` 欄位：

```json
"capabilities": [
  "custom-capability-1",
  "custom-capability-2"
]
```

### 添加新的工作流程

在 `workflows` 陣列中添加：

```json
{
  "id": "custom-workflow",
  "name": "Custom Workflow",
  "description": "Custom workflow description",
  "steps": ["agent-id1", "agent-id2"],
  "error_handling": "debug-agent"
}
```

### 修改Prompt

編輯 `prompts/` 目錄中的 markdown 文件，根據需要自訂 agent 行為。

## 📊 Change Log 系統

所有 agent 執行都會生成 Change Log：

```
CHANGELOG_[timestamp]_[agent_id].md
```

包含以下信息：

- 執行時間戳
- Agent 名稱和狀態
- 執行的操作
- 修改的文件
- 下一步步驟
- 發現的問題

## ✅ 最佳實踐

1. **始終使用 Brain Orchestrator**
   - 讓它協調工作流程
   - 監督質量和進度

2. **保持 Prompt 更新**
   - 定期檢查和更新 prompts/
   - 根據項目需求調整

3. **監控 Change Logs**
   - 檢查每個 agent 的執行結果
   - 確保符合預期

4. **管理依賴**
   - 記錄新增的依賴
   - 更新文檔

## 🆘 疑難排解

### Agent 無法找到

- 確認 agents.json 中有正確的 agent ID
- 檢查 prompt 文件路徑是否正確

### 工作流程中斷

- 檢查上一個 agent 的 Change Log
- 查看是否有錯誤報告
- 調用 Debug Agent 診斷

### 文件未被創建

- 檢查 project_root 路徑
- 確認寫入權限
- 查看 implementation 的詳細輸出

## 📚 進階用法

### 條件工作流程

在 Brain Orchestrator 中實現條件邏輯：

```
IF condition:
  CALL agent1
ELSE:
  CALL agent2
```

### 並行執行

某些 agent 可以並行執行：

```
PARALLEL:
  - implementation-agent (模塊A)
  - implementation-agent (模塊B)
THEN:
  - integration step
```

### 自動重試

在配置中設置重試邏輯：

```json
"auto_recovery": true,
"max_retry_attempts": 3
```

## 📞 支援

如有任何問題，請參考：

- [SETUP.md](SETUP.md) - 詳細設置指南
- [USAGE.md](USAGE.md) - 詳細使用指南
- 原始 agent-toolkit 文檔

## 📄 許可證

此配置保持原始 agent-toolkit 的許可證。

---

**最後更新**: 2025-01-30
