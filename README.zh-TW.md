# Web 開發代理工具包

🤖 **適用於 GitHub Copilot 的自動化多代理 Web 開發系統**

[English](README.md) | 繁體中文

---

> ## ⚠️ 實驗性質 - AI 生成
>
> **本專案完全由 AI 生成，屬於實驗性質。**
>
> - 🤖 **100% AI 生成**：所有程式碼、文件和配置均由 AI 創建
> - 🧪 **實驗狀態**：本工具包正在積極開發和測試中
> - ⚡ **風險自負**：不建議在未經充分測試的情況下用於生產環境
> - 📊 **研究目的**：用於探索 AI 驅動的開發工作流程
>
> **在任何關鍵專案中使用之前，請在開發環境中進行徹底測試。**

---

## 📖 概述

本工具包提供了一個智慧編排系統，包含 8 個專門的開發代理，用於完整的專案生命週期管理：

**規劃 → 實作 → 測試 → 增強 → 發布**

## 🎯 功能特色

- ✨ **8 個專業 AI 代理** - 每個專注於特定的開發階段
- 🧠 **智慧編排** - 大腦代理協調所有工作流程
- 🔄 **3 種預定義工作流程** - 標準開發、錯誤修復、功能增強
- 📋 **自動變更追蹤** - 完整的所有變更審計追蹤
- 🚀 **生產就緒** - 完全測試和文件化的系統

## 📦 包含內容

```
web-dev-agent-toolkit/
├── web creator.agent.md          # 主要代理配置
└── web-dev-toolkit/
    ├── agents.json                # 代理定義
    ├── README.md                  # 系統概述
    ├── SETUP.md                   # 安裝指南
    ├── USAGE.md                   # 使用說明
    ├── QUICK_START.md             # 快速開始指南
    └── prompts/                   # 個別代理提示詞
        ├── brain_orchestrator.md
        ├── planning_agent.md
        ├── implementation_agent.md
        ├── testing_agent.md
        ├── debug_agent.md
        ├── fix_agent.md
        ├── enhancement_agent.md
        └── release_agent.md
```

## 🚀 快速開始

### 1. 安裝

將文件複製到您專案的 `.github` 目錄：

```bash
# 克隆此 repository
git clone https://github.com/HenryLin1134/web-dev-agent-toolkit.git

# 複製到您的專案
cp -r web-dev-agent-toolkit/.github/agents .github/
cp -r web-dev-agent-toolkit/.github/web-dev-toolkit .github/
```

### 2. 配置 GitHub Copilot

代理將在 VS Code 中自動可用（需要 GitHub Copilot）。

### 3. 開始使用

```
@web-creator initialize my_project
requirements: "建立一個具有用戶認證和評論功能的部落格平台"
```

## 🎭 8 個代理

| 代理 | 角色 | 功能 |
|------|------|------|
| 🧠 大腦編排器 | 協調者 | 管理整個工作流程 |
| 📋 規劃代理 | 規劃師 | 需求與設計 |
| 💻 實作代理 | 開發者 | 程式碼生成 |
| 🧪 測試代理 | QA 工程師 | 品質保證 |
| 🐛 除錯代理 | 診斷專家 | 問題分析 |
| 🔧 修復代理 | 故障排除員 | 問題解決 |
| ✨ 增強代理 | 優化專家 | 功能優化 |
| 🚀 發布代理 | 發布管理員 | 部署管理 |

## 📚 文件

- [安裝指南](web-dev-toolkit/SETUP.md) - 詳細安裝說明
- [使用指南](web-dev-toolkit/USAGE.md) - 如何使用代理
- [快速參考](web-dev-toolkit/QUICK_START.md) - 快速命令參考

## 🔧 系統需求

- Visual Studio Code
- GitHub Copilot 擴充功能
- GitHub Copilot Chat 擴充功能

## ⚠️ 免責聲明

**本工具包完全由 AI 生成，屬於實驗性質。** 雖然它旨在協助 Web 開發工作流程，但使用者應該：

- ✅ 徹底測試所有生成的程式碼
- ✅ 在應用變更之前審查代理輸出
- ✅ 先在開發/測試環境中使用
- ✅ 了解 AI 生成程式碼的限制
- ❌ 在未經驗證的情況下，不要依賴它用於關鍵生產系統
- ❌ 不要假設所有生成的程式碼都是無錯誤或安全的

作者和貢獻者對使用本實驗性工具包所產生的任何問題不承擔責任。

## 📝 授權

MIT 授權 - 詳見 LICENSE 文件

## 🤝 貢獻

歡迎貢獻！請隨時提交 Pull Request。

## 📞 支援

如有問題和疑問，請在 GitHub 上開啟 issue。

---

**版本**: 1.0.0-experimental  
**狀態**: 🧪 實驗性質（AI 生成）  
**最後更新**: 2026-01-30
