# 訪問看護経営の標準教科書

> 元救命ICU看護師が実証した、年商5億円・5拠点展開の「ユニットエコノミクス」と「組織行動学」

[![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0-blue.svg)](CHANGELOG.md)

## 📖 概要

2040年「多死社会」に向けた訪問看護ステーション経営の完全ガイドです。

### 対象読者

| 対象 | 説明 |
|------|------|
| 🏥 年商1億円未満の経営者 | 売上拡大・利益改善を目指す方 |
| 🏢 多店舗展開を目指す経営者 | 2店舗目以降の出店を検討中の方 |
| 📝 開業準備中の方 | これから訪問看護ステーションを開業する方 |

## 📁 ファイル構成

```
whitepaper/
├── index.html                    # エントリーポイント（リダイレクト）
├── whitepaper_part1.html         # ホワイトペーパー本体（全20ページ）
├── css/
│   └── style.css                 # 外部スタイルシート
├── docs/                         # ドキュメント
│   ├── DESIGN_SPECIFICATION.md   # デザイン仕様書
│   └── TEMPLATE_RECREATION_PROMPT.md  # テンプレート再現用プロンプト
├── README.md                     # このファイル
├── vercel.json                   # Vercel設定
└── .gitignore                    # Git除外設定
```

## 📑 目次

| 章 | タイトル | ページ |
|----|----------|--------|
| 序章 | 市場機会と参入根拠 | 03 |
| 第1章 | ユニットエコノミクスの完全解剖 | 04-05 |
| 第2章 | エリア・ドミナント戦略 | 06-07 |
| 第3章 | 組織文化と規律 | 08-09 |
| 第4章 | 財務ポートフォリオ戦略 | 10-11 |
| 第5章 | 0→1マーケティング | 12-13 |
| 第6章 | スケーリングと多角化の罠 | 14-15 |
| 第7章 | 品質管理とリスクヘッジ | 16-17 |
| 終章 | あなたへの提案 | 18 |

## 🚀 デプロイ方法

### GitHub + Vercel

1. **GitHubリポジトリを作成**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: 訪問看護経営ホワイトペーパー v1.0"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

2. **Vercelに接続**
   - [Vercel](https://vercel.com) にログイン
   - 「Import Project」からGitHubリポジトリを選択
   - デプロイ設定はデフォルトでOK
   - 「Deploy」をクリック

3. **完了！**
   - `https://your-project.vercel.app` でアクセス可能

### ローカルで確認

```bash
# Python 3がインストールされている場合
python -m http.server 8000

# Node.jsがインストールされている場合
npx serve
```

ブラウザで `http://localhost:8000` にアクセス

## 🎨 デザイン仕様

| 項目 | 値 |
|------|-----|
| ページサイズ | A4縦（210mm × 297mm） |
| フォント | Noto Sans JP |
| ブランドカラー | #1a365d（ネイビー） |
| 印刷対応 | ✅ PDF出力対応 |

詳細は `docs/DESIGN_SPECIFICATION.md` を参照

## 📝 新しいホワイトペーパーを作成する

1. `docs/TEMPLATE_RECREATION_PROMPT.md` のプロンプトをAIに渡す
2. トピックと章構成を指定
3. 自動的に同じデザインのホワイトペーパーが生成される

## ⚖️ 著作権

```
© 2025 一般社団法人全国訪問看護経営研究協会
著者: 渋谷 慶太

本資料の無断複製・転載・配布を禁じます。
```

## 📞 お問い合わせ

一般社団法人全国訪問看護経営研究協会

---

<p align="center">
  <strong>Japan Home Visit Nursing Management Research Association</strong>
</p>
