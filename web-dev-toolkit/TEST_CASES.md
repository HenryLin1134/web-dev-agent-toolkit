# Web-Creator 工作流程測試案例

## 測試目的

驗證 web-creator 是否正確遵守工作流程規則，不會跳過步驟或變回一般 Agent 模式。

## 測試案例

### 測試案例 1: 簡單功能需求

**使用者輸入**:
```
@web-creator 我想要一個登入按鈕
```

**預期行為** ✅:
1. Agent 建立 `CHANGELOG_[timestamp]_brain-orchestrator.md`
2. Agent 調用 Planning Agent
3. Agent 不直接提供程式碼

**錯誤行為** ❌:
- 直接提供 `<button>` HTML 程式碼
- 直接給出建議而不建立 CHANGELOG
- 跳過 Planning Agent

---

### 測試案例 2: 新專案需求

**使用者輸入**:
```
@web-creator 幫我建立一個部落格網站
```

**預期行為** ✅:
1. 建立 `projects/blog/CHANGELOG_[timestamp]_brain-orchestrator.md`
2. 記錄需求到 CHANGELOG
3. 調用 Planning Agent 進行需求分析
4. Planning Agent 產出：
   - project_plan.md
   - technical_specification.md
   - file_structure.md
   - task_breakdown.md
5. 依序調用其他 Agent（Implementation → Testing → Enhancement → Release）

**錯誤行為** ❌:
- 直接開始寫程式碼
- 跳過任何工作流程步驟
- 像一般助理一樣回答

---

### 測試案例 3: Bug 修復需求

**使用者輸入**:
```
@web-creator 登入頁面無法正常運作
```

**預期行為** ✅:
1. 建立 `CHANGELOG_[timestamp]_brain-orchestrator.md`
2. 判斷為 Bug 修復工作流程
3. 調用 Debug Agent 診斷問題
4. 調用 Fix Agent 修復問題
5. 調用 Testing Agent 驗證修復

**錯誤行為** ❌:
- 直接建議程式碼修改
- 不進行診斷就提供解決方案
- 跳過測試階段

---

### 測試案例 4: 功能增強需求

**使用者輸入**:
```
@web-creator 為登入頁面新增忘記密碼功能
```

**預期行為** ✅:
1. 建立 `CHANGELOG_[timestamp]_brain-orchestrator.md`
2. 判斷為功能增強工作流程
3. 調用 Planning Agent 設計功能
4. 調用 Enhancement Agent 實作功能
5. 調用 Testing Agent 測試
6. 調用 Release Agent 發布

**錯誤行為** ❌:
- 直接修改程式碼
- 不經過規劃就實作
- 沒有測試就發布

---

## 驗證檢查清單

### 每個測試案例都應該檢查：

- [ ] 是否建立了 CHANGELOG 檔案？
- [ ] 檔案路徑是否正確？(`projects/[project_name]/CHANGELOG_[timestamp]_[agent_id].md`)
- [ ] 是否調用了正確的 Agent？
- [ ] Agent 調用順序是否正確？
- [ ] 是否有跳過任何強制步驟？
- [ ] 產出的文檔是否完整？

### 成功標準：

✅ **完全符合** - 所有檢查項目都通過  
⚠️ **部分符合** - 大部分檢查項目通過，有小問題  
❌ **不符合** - 跳過關鍵步驟或行為像一般 Agent

---

## 實際測試記錄

### 測試日期: ___________
### 測試者: ___________

| 測試案例 | 結果 | CHANGELOG 建立 | Agent 調用 | 工作流程 | 備註 |
|---------|------|--------------|-----------|---------|------|
| 案例 1  |      |              |           |         |      |
| 案例 2  |      |              |           |         |      |
| 案例 3  |      |              |           |         |      |
| 案例 4  |      |              |           |         |      |

### 問題記錄

如果發現問題，請記錄：

**問題描述**:


**預期行為**:


**實際行為**:


**影響範圍**:


**建議修正**:


---

## 回歸測試

### 下次測試日期: ___________

確認：
- [ ] 所有先前發現的問題都已修正
- [ ] 沒有出現新的回歸問題
- [ ] 工作流程執行穩定

---

**版本**: 1.0.0  
**建立日期**: 2026-01-30  
**對應改進版本**: v1.1.0
