# AI Sheets 문서 스크린샷 준비 목록

문서에 이미 심어져 있는 `> 📷 **Image — \`파일명.png\`:**` placeholder를 전부 수집한 목록입니다.
캡처한 PNG를 각 파일명 그대로 준비하면 됩니다.

- **총 placeholder**: 21개 블록
- **고유 이미지**: 20개 (`merge-conflicts.png`는 2개 문서에서 공유)

---

## Getting Started / Setup

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 1 | `hero.png` | AI Sheets 창 + 채워진 테이블 (Database·Localization 탭 둘 다 보이고 AI 사이드 패널 표시) — 히어로 컷 | README.md |
| 2 | `quickstart-window.png` | Unity `Window` 메뉴 열려 `AI Sheets > Spreadsheet` 하이라이트 + 옆에 열린 Spreadsheet 창 | getting-started/quick-start.md |
| 3 | `provider-settings.png` | AI Sheets Preferences(Project Settings) 페이지 — provider + API key + model 필드 | setup/providers.md |

## Spreadsheet Editor

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 4 | `window-layout.png` | Spreadsheet 창 전체 + 콜아웃 라벨 (Menu/Toolbar, grid, side panel) | spreadsheet-editor/README.md |
| 5 | `new-table-dialog.png` | New Table 다이얼로그 — 카테고리 선택기(Database/Localization) 하이라이트 | spreadsheet-editor/editing-tables.md |
| 6 | `column-manager.png` | Column Manager — 컬럼 data-type 드롭다운 열린 상태 | spreadsheet-editor/editing-tables.md |
| 7 | `cell-edit.png` | 셀 인라인 편집 중 + 우클릭 컨텍스트 메뉴(Cut/Copy/Paste, notes) | spreadsheet-editor/editing-tables.md |
| 8 | `import-export-menu.png` | File 메뉴 펼침 — Import From…/Export As… 서브메뉴 + 포맷 목록(CSV/TSV/JSON/XLIFF/ScriptableObject) | spreadsheet-editor/import-export.md |
| 9 | `merge-conflicts.png` ♻️ | Merge Conflicts 창 — per-row 액션 드롭다운(Smart Merge/Skip/Overwrite) + 일괄 버튼 | import-export.md · reference/merge-rules.md |
| 10 | `google-sheets-setup.png` | Google Sheets 설정/가이드 패널 — spreadsheet ID / sheet name 필드 | spreadsheet-editor/google-sheets.md |
| 11 | `google-sheets-sync.png` | 테이블 ↔ 동기화된 Google Sheet 나란히 (컬럼/행 매칭) | spreadsheet-editor/google-sheets.md |

## Database

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 12 | `database-table-codegen.png` | Database 테이블(타입 컬럼) + DB Model 설정 탭(PureCSharp/ScriptableObject, namespace/class name) | database/README.md |
| 13 | `gamedb-setup-window.png` | Game Database Setup 창 — DB 클래스명, per-table include/accessor/online-loading 목록, Generate 버튼 | database/gamedb.md |

## Localization

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 14 | `localization-table.png` | Localization 테이블 — key 컬럼 + 여러 언어 컬럼, 비어있는(missing) 셀 하이라이트 | localization/README.md |
| 15 | `translation.png` | Localization 테이블 — missing 셀 선택 + 사이드 패널 translate 액션(backend 드롭다운) | localization/translation.md |
| 16 | `localization-components.png` | GameObject Inspector — `TextLocalization` 컴포넌트 + localization key 필드 설정됨 | localization/components.md |

## AI Features

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 17 | `content-generation.png` | 사이드 패널 generation 액션 — 프롬프트 입력 + grid에서 대상 셀 선택 | ai-features/content-generation.md |
| 18 | `text-revision.png` | 텍스트 셀 선택 + Revise 액션 + before/after 텍스트 표시 | ai-features/text-revision.md |
| 19 | `spreadsheet-agent.png` | Agent 패널 — 자연어 태스크 입력 + 테이블에 적용된 결과 변경 | ai-features/agent.md |

## Reference

| # | 파일명 | 담을 화면 | 문서 |
|---|--------|----------|------|
| 20 | `shortcuts-window.png` | Shortcuts 창 — 스프레드시트 단축키 전체 목록 | reference/keyboard-shortcuts.md |

---

### 메모
- ♻️ `merge-conflicts.png` 는 import-export.md 와 merge-rules.md 두 곳에서 같은 이미지를 참조합니다 (1장만 준비).
- placeholder 형식: `> 📷 **Image — \`파일명.png\`:** 설명` (blockquote). 이미지 파일을 붙일 위치를 이 줄로 대체하면 됩니다.
- Gitbook에 실제 삽입 시:
  ```markdown
  <figure><img src="../.gitbook/assets/파일명.png" alt=""><figcaption></figcaption></figure>
  ```
