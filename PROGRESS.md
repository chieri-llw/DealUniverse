# DealUniverse 進捗

## 最終更新: 2025/03/09

## 完了済み
- [x] GitHubリポジトリ作成
- [x] README.md 作成
- [x] PROGRESS.md 作成
- [x] フォルダ構造作成（docs/gas/sheets/dashboard/prompts）

## 進行中
- [ ] Phase 1: Sheets CRM 列定義

## 次にやること
- Sheets CRMの列定義（crm_schema.md）
- Sheets 費用ログの列定義（expense_schema.md）
- GAS: 01_calendar_trigger.gs を作成・テスト

## 設定済みの値
- SHEET_ID: （未記入）
- CARD_FOLDER_ID: （未記入）
- CHAT_WEBHOOK: （未記入）
- CLAUDE_API_KEY: （未記入）

## 決定済みの設計
- 名刺スキャン: Gemini写真3〜4枚 → Sheetsエクスポート
- 議事録: レコーダー → Google Docs → NotebookLM
- 請求書・発注書: Geminiに話しかけて生成
- 全体管理: Sheets CRM（案件名が共通キー）
