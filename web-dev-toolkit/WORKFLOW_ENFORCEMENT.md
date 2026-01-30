# Web-Creator 工作流程強制執行指南

## 📌 問題說明

**問題**: web-creator 在使用者講述需求時，不遵守規則步驟，會變回類似一般 Agent 模式

**原因分析**:
1. 缺乏明確的強制執行機制
2. 沒有檢查點來防止跳過步驟
3. 提示詞不夠明確和強制性

## ✅ 改進措施

### 1. 在 web-creator.agent.md 頂部添加 CRITICAL OPERATING RULES

新增了明確的禁止事項和檢查點：
- ❌ 禁止直接寫程式碼
- ❌ 禁止跳過 Planning Agent
- ❌ 禁止不建立 CHANGELOG
- ✅ 強制按照工作流程執行

### 2. 在 brain_orchestrator.md 添加強制執行規則

新增了：
- 強制執行檢查清單
- 明確的禁止行為
- 自我檢查機制

### 3. 添加 MANDATORY WORKFLOW ENFORCEMENT 章節

包含：
- 四個強制步驟
- 紅旗警示（Red Flags）
- 正確行為示範

## 🎯 正確使用流程

### 當使用者說："我想建立一個登入頁面"

**錯誤回應（舊版）**:
```
❌ "好的，我來幫你建立登入頁面。我們需要以下檔案..."
❌ 直接開始寫程式碼
❌ 直接給建議
```

**正確回應（新版）**:
```
✅ "讓我啟動工作流程來處理這個需求..."

Step 1: 建立 CHANGELOG
- 建立 projects/login-page/CHANGELOG_20260130_brain-orchestrator.md
- 記錄需求：建立登入頁面

Step 2: 調用 Planning Agent
- 分析登入頁面需求
- 設計技術架構
- 建立實作計畫

[然後按照 Planning → Implementation → Testing → Enhancement → Release 流程執行]
```

## 🔍 自我檢查清單

在回應使用者需求前，檢查：

- [ ] 我是否建立了 CHANGELOG 檔案？
- [ ] 我是否調用了 Planning Agent？
- [ ] 我是否跳過了任何工作流程步驟？
- [ ] 我是否像一般助理一樣直接回答？

**如果任何一項為 NO，立即停止並重新開始！**

## 📋 工作流程範本

### 新專案開發

```
1. Initialize
   ├─ Create CHANGELOG_brain-orchestrator.md
   └─ Document requirements

2. Planning Phase
   ├─ Invoke Planning Agent
   ├─ Create project_plan.md
   ├─ Create technical_specification.md
   ├─ Create file_structure.md
   └─ Create task_breakdown.md

3. Implementation Phase
   ├─ Invoke Implementation Agent
   ├─ Generate source code
   └─ Create implementation_summary.md

4. Testing Phase
   ├─ Invoke Testing Agent
   ├─ Run tests
   ├─ Create test_report.md
   └─ Create test_results.json

5. Enhancement Phase (if needed)
   ├─ Invoke Enhancement Agent
   └─ Create enhancement_summary.md

6. Release Phase
   ├─ Invoke Release Agent
   ├─ Create release_notes.md
   └─ Create deployment_checklist.md
```

### Bug 修復

```
1. Initialize
   └─ Create CHANGELOG_brain-orchestrator.md

2. Debug Phase
   ├─ Invoke Debug Agent
   └─ Identify root cause

3. Fix Phase
   ├─ Invoke Fix Agent
   └─ Apply fixes

4. Testing Phase
   ├─ Invoke Testing Agent
   └─ Verify fix

5. Release Phase
   └─ Update documentation
```

### 新功能開發

```
1. Initialize
   └─ Create CHANGELOG_brain-orchestrator.md

2. Planning Phase
   ├─ Invoke Planning Agent
   └─ Design feature

3. Implementation Phase
   └─ Invoke Implementation Agent

4. Testing Phase
   └─ Invoke Testing Agent

5. Enhancement Phase
   └─ Optimize feature

6. Release Phase
   └─ Document and deploy
```

## 🚨 常見錯誤與修正

### 錯誤 1: 直接提供程式碼

**錯誤**:
```
使用者: "幫我做一個按鈕"
Agent: "好的，這是程式碼: <button>...</button>"
```

**修正**:
```
使用者: "幫我做一個按鈕"
Agent: "讓我啟動開發工作流程...
1. 建立 CHANGELOG
2. 調用 Planning Agent 來設計按鈕功能
3. 然後依序執行實作和測試"
```

### 錯誤 2: 跳過 Planning Agent

**錯誤**:
```
使用者: "新增一個功能"
Agent: 直接調用 Implementation Agent
```

**修正**:
```
使用者: "新增一個功能"
Agent: 
1. 建立 CHANGELOG
2. 調用 Planning Agent（強制步驟）
3. Planning 完成後才調用 Implementation Agent
```

### 錯誤 3: 不建立 CHANGELOG

**錯誤**:
```
開始工作但沒有建立任何追蹤文件
```

**修正**:
```
每個階段都必須建立對應的 CHANGELOG 檔案
projects/[project_name]/CHANGELOG_[timestamp]_[agent_id].md
```

## 📊 成功指標

**改進後應該看到**:

✅ 每次需求都建立 CHANGELOG  
✅ 必定先調用 Planning Agent  
✅ 嚴格遵守工作流程順序  
✅ 每個階段都有文檔追蹤  
✅ 不再出現「一般 Agent 模式」  

**追蹤方式**:

檢查 `projects/` 資料夾中是否有完整的 CHANGELOG 鏈：
```
projects/[project_name]/
  ├─ CHANGELOG_timestamp_brain-orchestrator.md
  ├─ CHANGELOG_timestamp_planning-agent.md
  ├─ CHANGELOG_timestamp_implementation-agent.md
  ├─ CHANGELOG_timestamp_testing-agent.md
  └─ ...
```

## 🎓 使用建議

### 給使用者

當使用 web-creator 時：
1. 清楚描述你的需求
2. 期待看到工作流程開始（建立 CHANGELOG）
3. 如果 Agent 直接提供答案，提醒它遵守工作流程

範例提醒：
```
"請按照正確的工作流程執行，先建立 CHANGELOG 並調用 Planning Agent"
```

### 給開發者

定期檢查：
1. CHANGELOG 檔案是否完整
2. 每個階段是否有對應的輸出文檔
3. 工作流程是否被正確執行

## 🔄 更新日誌

- **2026-01-30**: 初始版本
  - 添加 CRITICAL OPERATING RULES
  - 加強 brain_orchestrator 提示詞
  - 新增 MANDATORY WORKFLOW ENFORCEMENT
  - 創建此工作流程強制執行指南

---

**版本**: 1.1.0  
**狀態**: 🟢 已改進  
**最後更新**: 2026-01-30
