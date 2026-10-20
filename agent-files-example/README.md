# Agent 文件使用說明

本資料夾以「案件排序功能」示範如何搭配需求規格、通用工作規則與任務 Skill，讓 Agent 依明確範圍進行修改及檢查。

專案啟動方式與操作說明請參閱 [專案總覽](../README.md)。

## 三份文件的分工

| 文件 | 用途 | 何時修改 |
| --- | --- | --- |
| [software-spec.md](software-spec.md) | 定義要完成的功能、範圍限制與驗收條件 | 功能需求或完成條件改變時 |
| [AGENTS.md](AGENTS.md) | 定義通用工作流程、開發原則與交付要求 | 專案工作方式或共同規則改變時 |
| [SKILL.md](skills/sorting-function-check/SKILL.md) | 定義排序功能的檢查步驟、注意事項與結果格式 | 該類任務的操作或檢查方法改變時 |

功能細節集中在規格書；AGENTS 保留通用規則；SKILL 說明特定任務如何執行與回報。需求變更時，應一併檢查 SKILL 是否仍與規格一致。

## 資料夾結構

```text
agent-files-example/
├── README.md
├── software-spec.md
├── AGENTS.md
└── skills/
    └── sorting-function-check/
        └── SKILL.md
```

這些檔案位於範例資料夾。用於修改上層專案程式時，請在任務中明確指定三份文件與專案範圍，避免只讀取範例資料夾內的檔案。SKILL 中提到的 `software-spec.md`，在本範例指的是本資料夾內的規格書。

## 使用流程

1. 先確認 `software-spec.md` 已寫清楚目標、需求、限制與完成條件。
2. 指定 Agent 讀取 `AGENTS.md`，遵循修改前、開發中與交付時的共同規則。
3. 涉及排序方式、緊急程度、排序保留、空清單或響應式版面時，指定使用排序檢查 SKILL。
4. 讓 Agent 檢查相關程式及資料流程，說明修改範圍與驗證方法，再執行任務。
5. 依規格的完成條件驗證，並使用 SKILL 的格式回報結果。

若文件矛盾或缺少必要資料，先檢查現有程式；仍無法判定時提出具體問題，不自行擴充需求。

## 任務指令範例

在專案根目錄開啟 Agent 後，可使用以下指令。

### 檢查現有功能

```text
請先讀取 agent-files-example/AGENTS.md、
agent-files-example/software-spec.md 與
agent-files-example/skills/sorting-function-check/SKILL.md。

以目前專案根目錄的程式為檢查範圍，依規格檢查案件排序功能。
本次先檢查與回報，不修改程式；請依 SKILL 的輸出格式整理結果。
```

### 修改並驗證功能

```text
請遵循 agent-files-example/AGENTS.md，依
agent-files-example/software-spec.md 修改目前專案的案件排序功能，
並使用 agent-files-example/skills/sorting-function-check/SKILL.md
進行檢查與回報。

先確認現有實作，只修改不符合規格的部分，保留既有修改。
```

## 檢查結果如何閱讀

SKILL 要求結果包含：

- 檢查結果：通過／需要修改／需要人工確認。
- 對應規格：本次檢查涉及的需求。
- 受影響範圍：相關畫面、程式或 API。
- 測試案例：操作、預期結果、實際結果與狀態。
- 需要人工確認：尚未釐清或無法完成驗證的事項。

應確認四種排序、同級案件順序、排序保留與重設、空清單及小螢幕版面均有對應結果。未執行的測試必須註明，不得標示為通過。

本文件是使用指南，不代表專案功能已完成實測。
