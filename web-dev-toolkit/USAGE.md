# GitHub Copilot Agents 使用指南

## 🎯 基本用法

### 在 Copilot 聊天中調用 Agent

1. 打開 Copilot 聊天面板 (`Ctrl+Shift+I`)
2. 輸入 `@` 查看可用的 agents
3. 選擇一個 agent
4. 輸入你的請求

範例：

```
@brain-orchestrator 我需要建立一個電商平台，請幫我制定開發計畫
```

## 📋 Agent 使用場景

### 1️⃣ 新專案設置

使用 **Brain Orchestrator** 開始：

```
@brain-orchestrator
command: initialize
project_name: my_new_project
requirements:
  - 用戶認證系統
  - 產品展示
  - 購物車功能
  - 支付集成
```

### 2️⃣ 項目規劃

使用 **Planning Agent**：

```
@planning-agent
Please analyze these requirements and create a comprehensive plan:
- Requirements: [描述]
- Target Users: [目標用戶]
- Constraints: [約束條件]
```

輸出：

- `project_plan.md` - 項目計畫
- `technical_specification.md` - 技術規格
- `file_structure.md` - 文件結構
- `task_breakdown.md` - 任務細分

### 3️⃣ 代碼實現

使用 **Implementation Agent**：

```
@implementation-agent
Please implement based on this plan:
- Technical Stack: React + Node.js
- Architecture: [複製計畫中的架構]
- Initial Setup Commands: [必要的初始化命令]
```

輸出：

- 源代碼文件
- 配置文件
- `implementation_summary.md`

### 4️⃣ 質量測試

使用 **Testing Agent**：

```
@testing-agent
Please test the implementation with focus on:
- Functional testing
- Unit tests
- Edge cases
- Performance
```

輸出：

- `test_report.md`
- `test_results.json`

### 5️⃣ 問題診斷

如果測試失敗，使用 **Debug Agent**：

```
@debug-agent
Test failures detected:
- Test Name: [失敗的測試]
- Error: [錯誤信息]
- Stack Trace: [堆棧追蹤]
```

輸出：

- `debug_report.md` - 詳細診斷
- `issue_analysis.md` - 問題分析

### 6️⃣ 代碼修復

使用 **Fix Agent**：

```
@fix-agent
Based on debug report, please fix:
- Issue #1: [問題描述]
- Issue #2: [問題描述]
Priority: High
```

輸出：

- `fix_summary.md` - 修復摘要
- 修復後的代碼

### 7️⃣ 功能增強

使用 **Enhancement Agent**：

```
@enhancement-agent
Please add these features:
- Feature 1: [描述]
- Feature 2: [描述]
Priority: Medium
```

輸出：

- `enhancement_report.md`
- 新增功能代碼

### 8️⃣ 發行準備

使用 **Release Agent**：

```
@release-agent
Prepare release:
- Version: 1.0.0
- Type: major
- Features: [主要功能]
```

輸出：

- `release_notes.md` - 發行說明
- `deployment_checklist.md` - 部署清單

## 🔄 典型工作流程

### 完整開發流程

```
1. @brain-orchestrator initialize
   ↓
2. @planning-agent analyze requirements
   ↓
3. @implementation-agent code implementation
   ↓
4. @testing-agent run tests
   ↓
   IF tests fail:
     5a. @debug-agent diagnose issues
     5b. @fix-agent apply fixes
     5c. @testing-agent retry
   ↓
6. @enhancement-agent add optional features
   ↓
7. @testing-agent verify enhancements
   ↓
8. @release-agent prepare release
```

### Bug 修復流程

```
1. @debug-agent diagnose the bug
   ↓
2. @fix-agent fix the issue
   ↓
3. @testing-agent verify the fix
   ↓
4. @release-agent prepare patch release
```

### 功能增強流程

```
1. @planning-agent plan enhancement
   ↓
2. @enhancement-agent implement feature
   ↓
3. @testing-agent test new feature
   ↓
4. @release-agent prepare minor release
```

## 💡 最佳實踐

### ✅ DO

1. **提供完整上下文**

   ```
   ✓ @planning-agent
   Project: E-commerce Platform
   Requirements: [詳細需求]
   Budget: $50,000
   Timeline: 3 months
   ```

2. **保存 Change Logs**
   - 每個 agent 執行都生成 Change Log
   - 定期檢查並存檔
   - 用於追蹤和文檔化

3. **逐步進行**
   - 完成一個階段再進入下一個
   - 在進行下一步前檢查結果
   - 及時處理問題

4. **清晰的指示**
   ```
   ✓ 具體: 「實現用戶認證系統，使用 JWT token」
   ✓ 完整: 包含所有相關信息
   ✓ 可測試: 定義明確的成功標準
   ```

### ❌ DON'T

1. **不要提供不清楚的需求**

   ```
   ✗ @planning-agent
   Please plan a website
   ```

2. **不要跳過步驟**

   ```
   ✗ 直接使用 @release-agent 而不測試
   ```

3. **不要忽視錯誤信息**

   ```
   ✗ 看到 Change Log 中的錯誤就忽視
   ✓ 立即調用 @debug-agent 診斷
   ```

4. **不要混淆 Agent 用途**
   ```
   ✗ 使用 @testing-agent 寫代碼
   ✓ 使用 @implementation-agent 寫代碼
   ```

## 📊 Change Log 解讀

### Change Log 位置

```
projects/[project_name]/CHANGELOG_[timestamp]_[agent_id].md
```

例如：

```
projects/my_blog/CHANGELOG_20250130_145300_planning_agent.md
```

### Change Log 內容示例

```markdown
# Planning Agent Execution Log

## Execution Summary

- **Timestamp**: 2025-01-30 14:53:00
- **Project**: my_blog
- **Status**: completed ✓
- **Duration**: 2 min 15 sec

## Actions Taken

1. ✓ Analyzed requirements
2. ✓ Designed architecture
3. ✓ Created file structure
4. ✓ Generated task breakdown

## Files Generated

- project_plan.md
- technical_specification.md
- file_structure.md
- task_breakdown.md

## Key Decisions

- Tech Stack: React + Node.js + PostgreSQL
- Architecture: Microservices
- Deployment: Docker + Kubernetes

## Next Steps

Proceed to implementation with:
```

@implementation-agent
project_name: my_blog
plan_file: projects/my_blog/project_plan.md

```

```

## 🆘 常見問題

### Q: 如何重新開始流程？

```
@brain-orchestrator
command: initialize
project_name: [same or new project]
force_restart: true
```

### Q: 如何查看以前的工作？

所有 Change Logs 保存在：

```
projects/[project_name]/CHANGELOG_*.md
```

### Q: Agent 的響應不正確怎麼辦？

1. 檢查你的指示是否清晰
2. 提供更多上下文信息
3. 使用 Debug Agent 分析問題
4. 考慮修改 agent 的 prompt

### Q: 如何並行使用多個 Agents？

```
同時打開多個 Copilot 聊天視窗：
- 聊天 1: @implementation-agent (模塊A)
- 聊天 2: @implementation-agent (模塊B)
```

### Q: 生成的代碼質量如何？

- 所有代碼應通過 @testing-agent
- 可以要求改進或重寫
- 使用 @debug-agent 診斷問題
- 使用 @fix-agent 修復問題

## 🎓 學習資源

### 開始使用

1. 完成 [設置指南](SETUP.md)
2. 運行第一個簡單的 @planning-agent 請求
3. 查看生成的 Change Log
4. 逐步使用其他 agents

### 進階用法

1. 定義自己的工作流程
2. 自訂 agent prompts
3. 集成到 CI/CD 管道
4. 建立項目特定的 agents

### 故障排除

- 檢查 Copilot 擴充日誌
- 查看 Change Logs 中的錯誤
- 在 VS Code 命令面板中搜索「Copilot」
- 參考 [設置指南](SETUP.md) 的故障排除部分

## 📈 效能提示

### 加快執行速度

1. **提供詳細的上下文**
   - Agent 需要理解背景信息
   - 清晰的指示減少迭代

2. **使用模板**

   ```
   @agent-name
   [使用預定義模板而不是每次寫完整指示]
   ```

3. **批量處理**
   - 合併相關任務
   - 減少 agent 轉換次數

4. **緩存結果**
   - Change Logs 提供了完整歷史
   - 重用以前的決策

## 🔐 安全指南

### 敏感信息

不要在 Copilot 聊天中分享：

- ❌ API keys
- ❌ 密碼
- ❌ 個人身份信息
- ❌ 內部系統地址
- ❌ 財務數據

### 代碼安全

- ✓ 在發布前進行安全審查
- ✓ 使用 @testing-agent 進行安全測試
- ✓ 定期更新依賴
- ✓ 遵循安全最佳實踐

## 📞 支援和回饋

- 查看 [README.md](README.md) 了解系統概述
- 參考 [SETUP.md](SETUP.md) 了解配置細節
- 檢查 Change Logs 尋找模式和建議

---

**開始使用**: 打開 Copilot 聊天，輸入 `@brain-orchestrator` 並開始你的第一個項目！

**最後更新**: 2025-01-30
