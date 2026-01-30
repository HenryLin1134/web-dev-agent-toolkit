# Web-Creator v1.1.0 快速參考卡

## 🚨 核心規則（記住這些！）

```
┌─────────────────────────────────────────┐
│  web-creator 絕對不是一般 AI 助理       │
│  它是結構化的多 Agent 工作流程系統      │
└─────────────────────────────────────────┘
```

---

## ✅ 正確行為檢查清單

每次使用時，Agent 必須：

- [ ] 建立 CHANGELOG 檔案
- [ ] 調用 Planning Agent（第一步）
- [ ] 按順序執行工作流程
- [ ] 每個階段都產出文檔
- [ ] 不直接提供程式碼答案

---

## ❌ 禁止行為

| 禁止行為                 | 原因               |
| ------------------------ | ------------------ |
| 直接寫程式碼             | 跳過規劃和測試     |
| 跳過 Planning Agent      | 缺乏設計和架構     |
| 不建立 CHANGELOG         | 無法追蹤進度       |
| 像一般助理回答           | 不符合系統設計     |
| 跳過任何工作流程步驟     | 品質無法保證       |

---

## 🔄 標準工作流程

```
1. 初始化
   └─ 建立 CHANGELOG_brain-orchestrator.md

2. Planning
   └─ 調用 Planning Agent

3. Implementation
   └─ 調用 Implementation Agent

4. Testing
   └─ 調用 Testing Agent

5. Enhancement (可選)
   └─ 調用 Enhancement Agent

6. Release
   └─ 調用 Release Agent
```

---

## 📋 三種主要工作流程

### 新專案開發
```
Planning → Implementation → Testing → Enhancement → Release
```

### Bug 修復
```
Debug → Fix → Testing → Release
```

### 功能增強
```
Planning → Enhancement → Testing → Release
```

---

## 🎯 快速使用

### 正確啟動方式

```bash
@web-creator [描述你的需求]
```

範例：
- `@web-creator 建立一個登入頁面`
- `@web-creator 修復購物車 bug`
- `@web-creator 新增忘記密碼功能`

### 期待的回應模式

```
✅ "讓我啟動開發工作流程..."
✅ "正在建立 CHANGELOG..."
✅ "調用 Planning Agent 分析需求..."

❌ "好的，這是程式碼..."
❌ "你需要這些檔案..."
❌ "建議你這樣做..."
```

---

## 🐛 如果 Agent 行為不正確

### 糾正指令

```
"請按照正確的工作流程執行：
1. 建立 CHANGELOG
2. 調用 Planning Agent
3. 依序執行各階段"
```

### 重置工作流程

```
"重新開始，請遵守 web-creator 的強制執行規則"
```

---

## 📁 預期輸出結構

```
projects/[project_name]/
├── CHANGELOG_[timestamp]_brain-orchestrator.md
├── CHANGELOG_[timestamp]_planning-agent.md
├── CHANGELOG_[timestamp]_implementation-agent.md
├── CHANGELOG_[timestamp]_testing-agent.md
├── CHANGELOG_[timestamp]_enhancement-agent.md
├── CHANGELOG_[timestamp]_release-agent.md
├── project_plan.md
├── technical_specification.md
├── file_structure.md
├── task_breakdown.md
├── implementation_summary.md
├── test_report.md
├── test_results.json
├── enhancement_summary.md
├── release_notes.md
└── deployment_checklist.md
```

---

## 📊 品質驗證

### 檢查這些問題

1. **CHANGELOG 是否存在？**
   - 路徑: `projects/[project_name]/CHANGELOG_*.md`
   
2. **Planning 是否執行？**
   - 檢查: `project_plan.md` 存在
   
3. **測試是否完成？**
   - 檢查: `test_report.md` 和 `test_results.json`
   
4. **文檔是否完整？**
   - 所有必要的 `.md` 檔案都存在

---

## 🔧 8 個 Agent 概覽

| Agent                | 職責             | 何時調用         |
| -------------------- | ---------------- | ---------------- |
| 🧠 Brain             | 協調所有流程     | 每次需求         |
| 📋 Planning          | 需求分析與設計   | 開始時（強制）   |
| 💻 Implementation    | 程式碼實作       | Planning 後      |
| 🧪 Testing           | 質量測試         | Implementation 後|
| 🐛 Debug             | 問題診斷         | 發現錯誤時       |
| 🔧 Fix               | 問題修復         | Debug 後         |
| ✨ Enhancement       | 功能優化         | Testing 通過後   |
| 🚀 Release           | 發布管理         | 最後階段         |

---

## 💡 記住這些口訣

```
📝 先建 CHANGELOG，記錄開始
📋 必調 Planning，不可跳過
💻 依序實作，不急著寫
🧪 測試驗證，確保品質
✨ 優化增強，追求完美
🚀 最後發布，文檔齊全
```

---

## 📞 問題排查

### 問題：Agent 直接給答案
**解決**: 提醒遵守工作流程規則

### 問題：找不到 CHANGELOG
**原因**: Agent 跳過了初始化步驟
**解決**: 要求重新開始並建立 CHANGELOG

### 問題：缺少規劃文檔
**原因**: 沒有調用 Planning Agent
**解決**: 要求必須先執行 Planning 階段

### 問題：沒有測試報告
**原因**: 跳過了 Testing Agent
**解決**: 要求完成測試階段

---

## 📚 詳細文檔

需要更多資訊？查看：

- [WORKFLOW_ENFORCEMENT.md](WORKFLOW_ENFORCEMENT.md) - 完整執行指南
- [logs/IMPROVEMENT_v1.1.0.md](logs/IMPROVEMENT_v1.1.0.md) - 改進說明
- [BEHAVIOR_COMPARISON.md](BEHAVIOR_COMPARISON.md) - 行為對比
- [TEST_CASES.md](TEST_CASES.md) - 測試案例
- [USAGE.md](USAGE.md) - 使用指南

---

## 🎓 最佳實踐

### ✅ DO

- 清楚描述需求
- 等待完整工作流程執行
- 檢查 CHANGELOG 追蹤進度
- 驗證所有輸出文檔

### ❌ DON'T

- 期待立即的程式碼答案
- 跳過任何工作流程步驟
- 忽略 Agent 的規劃建議
- 不檢查測試報告就部署

---

**列印此卡片並放在手邊！**

**版本**: 1.0.0  
**對應系統版本**: v1.1.0  
**建立日期**: 2026-01-30
