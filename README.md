# DealUniverse 構築ロードマップ

## リポジトリ構造

```
DealUniverse/
│
├── README.md              ← プロジェクト概要
├── PROGRESS.md            ← 進捗管理（毎回ここから会話を始める）
│
├── docs/                  ← 設計ドキュメント
│   ├── sequence_crm.md        CRM軸フロー設計
│   ├── sequence_expense.md    費用・書類軸フロー設計
│   └── sequence_master.md     統合フロー設計
│
├── gas/                   ← GASスクリプト（コピペして使う）
│   ├── 01_calendar_trigger.gs     面談前ブリーフィング
│   ├── 02_card_scan_detect.gs     名刺スキャン検知
│   ├── 03_meeting_analysis.gs     面談後分析・CRM記録
│   ├── 04_followup_message.gs     フォローアップ文章生成
│   ├── 05_expense_log.gs          費用ログ自動記録
│   ├── 06_invoice_generate.gs     請求書・発注書生成
│   └── 07_alerts_reports.gs       アラート・月次レポート
│
├── sheets/                ← Sheetsテンプレート設計
│   ├── crm_schema.md          CRMシート列定義
│   └── expense_schema.md      費用ログシート列定義
│
├── dashboard/             ← GitHub Pages ダッシュボード
│   ├── index.html
│   ├── crm.js
│   └── expense.js
│
└── prompts/               ← Gemini・Claude用プロンプト集
    ├── card_scan.md           名刺スキャン用
    ├── receipt_scan.md        レシート読取用
    ├── invoice_generate.md    請求書生成用
    └── followup_message.md    フォローアップ文章用
```

---

## フェーズ別ビルド計画

### Phase 1【今週】基盤を作る
**目標：リポジトリを作ってSheetsと繋げる**

- [ ] GitHubリポジトリ作成（Public or Private）
- [ ] README.md と PROGRESS.md を作成
- [ ] Sheets CRM の列定義を確定（crm_schema.md）
- [ ] Sheets 費用ログの列定義を確定（expense_schema.md）
- [ ] GAS: 01_calendar_trigger.gs を設置・テスト

### Phase 2【2週間後】CRM軸を完成させる
**目標：面談前→録音→名刺→フォローアップが回る**

- [ ] GAS: 02_card_scan_detect.gs（Gemini連携）
- [ ] GAS: 03_meeting_analysis.gs（NotebookLM連携）
- [ ] GAS: 04_followup_message.gs（Claude API連携）
- [ ] prompts/ に各プロンプトを保存

### Phase 3【1ヶ月後】費用・書類軸を完成させる
**目標：発注書・レシート・請求書がSheetsに繋がる**

- [ ] GAS: 05_expense_log.gs（Gemini → Sheets）
- [ ] GAS: 06_invoice_generate.gs（請求書・発注書生成）
- [ ] GAS: 07_alerts_reports.gs（アラート・月次レポート）

### Phase 4【2ヶ月後】ダッシュボードを公開する
**目標：GitHub Pages で収支・人脈を可視化**

- [ ] dashboard/ の HTML/JS を構築
- [ ] GitHub Pages を有効化
- [ ] Sheets API と接続

---

## 毎回の会話の始め方（コンテキスト節約）

新しい会話を始める時はこのテンプレをコピペ：

```
DealUniverseの続きをお願いします。

【現在のフェーズ】Phase X - ○○

【PROGRESS.mdの内容】
（GitHubのPROGRESS.mdの内容をここにコピペ）

【今日やりたいこと】
○○のGASを作りたい / ○○のバグを直したい
```

---

## PROGRESS.md のテンプレート

```markdown
# DealUniverse 進捗

## 最終更新: 2025/03/09

## 完了済み
- [ ] （完了したものをここに）

## 進行中
- [ ] Phase 1: リポジトリ基盤構築

## 次にやること
- GitHubリポジトリ作成
- Sheets CRM の列定義

## 設定済みの値（コードに必要な情報）
- SHEET_ID: （後で記入）
- CARD_FOLDER_ID: （後で記入）
- CHAT_WEBHOOK: （後で記入）
- CLAUDE_API_KEY: スクリプトプロパティに保存済み

## 決定済みの設計
- 名刺スキャン: Gemini写真3〜4枚 → Sheetsエクスポート
- 議事録: レコーダー → Google Docs → NotebookLM
- 請求書・発注書: Geminiに話しかけて生成
- 全体管理: Sheets CRM（案件名が共通キー）
```
