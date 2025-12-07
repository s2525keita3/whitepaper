# 訪問看護経営ホワイトペーパー デザイン仕様書

> **バージョン**: 1.0  
> **最終更新**: 2025年12月  
> **対象ファイル**: `whitepaper_part1.html`

---

## 1. 概要

### 1.1 目的
このテンプレートは、一般社団法人全国訪問看護経営研究協会のホワイトペーパー・専門レポートを統一されたデザインで作成するためのHTMLテンプレートです。

### 1.2 特徴
- **A4縦印刷対応**（210mm × 297mm）
- **ブラウザ表示・PDF出力両対応**
- **コンポーネントベース設計**（再利用可能なUIパーツ）
- **CSS変数によるカスタマイズ容易性**
- **プロフェッショナルなネイビー系カラースキーム**

### 1.3 対象読者
- 訪問看護の経営者（年商1億円未満）
- 多店舗展開を目指す経営者
- 開業準備中の方

---

## 2. デザイントークン（CSS変数）

### 2.1 ページサイズ
```css
--page-width: 210mm;   /* A4幅 */
--page-height: 297mm;  /* A4高さ */
```

### 2.2 フォント設定
```css
--font-body: "Noto Sans JP", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
--font-size-body: 13.5px;   /* 本文 */
--font-size-small: 11px;    /* 注釈・補足 */
```

**Google Fonts読み込み**:
```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&display=swap" rel="stylesheet" />
```

### 2.3 カラーパレット

#### ベースカラー
| 変数名 | 値 | 用途 |
|--------|-----|------|
| `--color-bg-canvas` | `#eeeeee` | 画面背景（ブラウザ表示時） |
| `--color-bg-page` | `#ffffff` | ページ背景 |
| `--color-text` | `#222222` | 本文テキスト |
| `--color-text-muted` | `#666666` | 補足テキスト、キャプション |
| `--color-heading` | `#111111` | 見出し |
| `--color-border` | `#E0E3EB` | ボーダー、区切り線 |
| `--color-soft` | `#F5F7FB` | 背景（薄いグレー） |

#### ブランドカラー（ネイビー系）
| 変数名 | 値 | 用途 |
|--------|-----|------|
| `--color-brand` | `#1a365d` | メインカラー（濃いネイビー） |
| `--color-brand-soft` | `#e8eef5` | メインカラー（薄い背景用） |
| `--color-brand-gradient` | `linear-gradient(135deg, #1a365d, #2c5282)` | グラデーション |

#### セマンティックカラー
| 種別 | メイン | 背景（soft） | 用途 |
|------|--------|--------------|------|
| Success（成功） | `#0F9D58` | `#E6F4EA` | 完了、良い状態、推奨、OK |
| Warning（警告） | `#F9AB00` | `#FEF7E0` | 注意、確認必要 |
| Alert（危険） | `#D93025` | `#FDECEA` | エラー、禁止、NG |
| Info（情報） | `#4285F4` | `#E8F0FE` | 補足情報、Tips、定義 |

---

## 3. ページレイアウト

### 3.1 印刷設定
```css
@page {
  size: A4;
  margin: 16mm 18mm;
}
```

### 3.2 ページ構造
```
┌─────────────────────────────────────┐
│  header-meta（上部12mm）            │
│  ┌─────────────────────────────┐   │
│  │  page-inner（本文エリア）     │   │
│  │  max-width: 130mm           │   │
│  │  margin: 22mm auto 20mm     │   │
│  └─────────────────────────────┘   │
│  footer-meta（下部10mm）            │
└─────────────────────────────────────┘
```

### 3.3 ページバリエーション

| クラス | max-width | margin-top | 用途 |
|--------|-----------|------------|------|
| `.page` | 130mm | 22mm | 通常ページ |
| `.page--cover` | 140mm | 30mm | 表紙・裏表紙 |
| `.page--toc` | 150mm | 22mm | 目次 |
| `.page--wide` | 170mm | 22mm | ワイドページ（大きなテーブル用） |

### 3.4 ページ区切り
```html
<section class="page page-break">
```
`page-break-after: always;` で印刷時に改ページ。

---

## 4. ヘッダー・フッター

### 4.1 ヘッダー（header-meta）
```html
<div class="header-meta">
  <div class="header-meta__left">
    <span class="badge badge--outline" style="border-color: var(--color-alert); color: var(--color-alert);">機密</span>
    <span>ホワイトペーパー名</span>
  </div>
  <div class="header-meta__right">章名 or Ver 1.0</div>
</div>
```

**配置**: `position: absolute; top: 12mm;`

### 4.2 フッター（footer-meta）
```html
<div class="footer-meta">
  <div>セクション名</div>
  <div>ページ番号</div>
</div>
```

**配置**: `position: absolute; bottom: 10mm;`  
**スタイル**: 上部に1pxボーダー

---

## 5. タイポグラフィ

### 5.1 見出し階層

| 要素 | サイズ | スタイル |
|------|--------|----------|
| `h1` | 22px | margin-bottom: 8px |
| `h2` | 16px | 左ボーダー3px（brand色）、padding-left: 8px |
| `h3` | 14px | margin-top: 14px |
| `h4` | 13px | margin-top: 10px |

### 5.2 本文・テキスト

| クラス | サイズ | 行高 | 用途 |
|--------|--------|------|------|
| `p` | 13.5px | 1.8 | 通常の段落 |
| `.lead` | 14px | 1.9 | リード文（強調段落） |
| `.small` | 11px | - | 注釈、補足、英語サブタイトル |

### 5.3 リスト
```css
ul, ol {
  font-size: 13.5px;
  line-height: 1.8;
  margin: 0 0 8px 20px;
}
li { margin-bottom: 4px; }
```

---

## 6. コンポーネント一覧

### 6.1 バッジ（Badge）
```html
<span class="badge badge--outline">機密</span>
<!-- カスタム色 -->
<span class="badge badge--outline" style="border-color: var(--color-alert); color: var(--color-alert);">機密</span>
```

### 6.2 ラベル（Label）
```html
<span class="label">標準</span>
<span class="label label--info">INFO</span>
<span class="label label--success">OK</span>
<span class="label label--warning">注意</span>
<span class="label label--alert">危険</span>
```

**スタイル**: `border-radius: 999px; padding: 2px 8px; font-size: 11px;`

### 6.3 コールアウト（Callout）
```html
<!-- 標準（ブランド色） -->
<div class="callout">
  <div class="callout-title">💡 POINT</div>
  <p>本文</p>
</div>

<!-- 情報（青） -->
<div class="callout callout--info">
  <div class="callout-title">📐 定義</div>
  <p>本文</p>
</div>

<!-- 成功（緑） -->
<div class="callout callout--success">
  <div class="callout-title">✓ 推奨</div>
  <p>本文</p>
</div>

<!-- 警告（黄） -->
<div class="callout callout--warning">
  <div class="callout-title">⚠ 注意</div>
  <p>本文</p>
</div>

<!-- 危険（赤） -->
<div class="callout callout--alert">
  <div class="callout-title">⛔ NG</div>
  <p>本文</p>
</div>
```

### 6.4 チェックリスト（Checklist）
```html
<ul class="checklist">
  <li>チェック項目1</li>
  <li>チェック項目2</li>
</ul>
```
**アイコン**: `☐`（未チェック）  
**完了版**: `.checklist--done` → `✔`

### 6.5 ステップリスト（Steps）
```html
<ol class="steps">
  <li><strong>手順1</strong><br>説明文</li>
  <li><strong>手順2</strong><br>説明文</li>
</ol>
```
**スタイル**: 数字が丸いバッジ（brand色、白文字）

### 6.6 カード（Card）
```html
<div class="card">
  <div class="card__title">タイトル</div>
  <div class="card__content">内容</div>
</div>

<div class="card card--highlight">
  <!-- 強調カード（brand色背景） -->
</div>
```

### 6.7 メトリクスボックス（Metric Box）
```html
<div class="metric-box">
  <div class="metric-box__label">ラベル</div>
  <div class="metric-box__value">50%</div>
  <div class="metric-box__note">補足説明</div>
</div>

<!-- カスタム背景 -->
<div class="metric-box" style="background: var(--color-success-soft);">
  <div class="metric-box__value" style="color: var(--color-success);">値</div>
</div>
```

### 6.8 ナンバーバッジ（Number Badge）
```html
<span class="number-badge">1</span>タイトル
```
**スタイル**: 24px丸、brand色背景、白文字

### 6.9 矢印リスト（Arrow List）
```html
<ul class="arrow-list">
  <li>項目1</li>
  <li>項目2</li>
</ul>
```
**アイコン**: `→`（brand色）

### 6.10 ハイライトボックス（Highlight Box）
```html
<div class="highlight-box">
  <p style="margin: 0; font-weight: 600;">【タイトル】</p>
  <p style="margin: 8px 0 0;">本文</p>
</div>
```
**スタイル**: brand色ボーダー、薄いbrand色背景

### 6.11 引用ボックス（Quote Box）
```html
<div class="quote-box">
  <p style="margin: 0;">引用文や重要なメッセージ</p>
</div>
```
**スタイル**: 左ボーダー4px、イタリック風

### 6.12 ターゲットバッジ（Target Badge）
```html
<span class="target-badge">対象読者</span>
```
**スタイル**: 警告色背景、角丸4px

### 6.13 テーブル（Table）
```html
<table>
  <thead>
    <tr><th>見出し1</th><th>見出し2</th></tr>
  </thead>
  <tbody>
    <tr><td>データ1</td><td>データ2</td></tr>
  </tbody>
</table>
```
**スタイル**: 幅100%、ヘッダー背景soft色、偶数行ストライプ

---

## 7. レイアウトヘルパー

### 7.1 カラムレイアウト
```html
<!-- 2カラム（均等） -->
<div class="two-column">
  <div>左</div>
  <div>右</div>
</div>

<!-- 2カラム（左広め） -->
<div class="two-column two-column--wide-left">
  <div>左（1.3fr）</div>
  <div>右（1fr）</div>
</div>

<!-- 3カラム -->
<div class="three-column">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

### 7.2 セクション区切り
```html
<hr class="section-separator">
```
**スタイル**: `border-top: 1px dashed;`

---

## 8. 表紙コンポーネント

### 8.1 タグライン
```html
<div class="cover-tagline">WHITE PAPER 2025</div>
```

### 8.2 タイトル
```html
<h1 class="cover-title">メインタイトル<br>サブタイトル</h1>
```

### 8.3 サブタイトル
```html
<p class="cover-subtitle">
  キャッチコピー<br>
  説明文
</p>
```

### 8.4 メタ情報
```html
<div class="cover-meta">
  <p>
    発行日：2025年12月<br>
    著作権：<strong>組織名</strong><br>
    著者：著者名
  </p>
</div>
```

### 8.5 フッターストリップ
```html
<div class="cover-strip">
  <div class="cover-strip__text">ORGANIZATION NAME - DOCUMENT TYPE</div>
</div>
```
**スタイル**: 高さ12mm、グラデーション背景

---

## 9. 章見出しコンポーネント

```html
<div class="chapter-heading">
  <div class="chapter-heading__eyebrow">CHAPTER 01</div>
  <div class="chapter-heading__title">章タイトル</div>
  <p class="chapter-heading__goal">この章の目的説明</p>
</div>
```

| 要素 | サイズ | スタイル |
|------|--------|----------|
| `__eyebrow` | 11px | 大文字、letter-spacing: 0.16em、brand色 |
| `__title` | 18px | 太字700 |
| `__goal` | 12.5px | muted色 |

---

## 10. 目次コンポーネント

```html
<div class="toc-block">
  <div class="toc-title">第1章</div>
  <div class="toc-item">
    <span class="toc-item__label">章タイトル</span>
    <span class="toc-item__page">03</span>
  </div>
  <div class="toc-item">
    <span class="toc-item__label">　├ サブセクション</span>
    <span class="toc-item__page">04</span>
  </div>
</div>
```

---

## 11. ブランド情報

### 11.1 組織名
- **正式名称**: 一般社団法人全国訪問看護経営研究協会
- **英語表記**: Japan Home Visit Nursing Management Research Association

### 11.2 著者
- **著者名**: 渋谷 慶太
- **英語表記**: Keita Shibuya

### 11.3 機密レベル
- **表記**: 機密（赤色バッジ）

---

## 12. ページ構成（現在のホワイトペーパー）

| ページ | 内容 |
|--------|------|
| 1 | 表紙 |
| 2 | 目次 |
| 3 | 序章：市場機会と参入根拠 |
| 4-5 | 第1章：ユニットエコノミクスの完全解剖 |
| 6-7 | 第2章：エリア・ドミナント戦略 |
| 8-9 | 第3章：組織文化と規律 |
| 10-11 | 第4章：財務ポートフォリオ戦略 |
| 12-13 | 第5章：0→1マーケティング |
| 14-15 | 第6章：スケーリングと多角化の罠 |
| 16-17 | 第7章：品質管理とリスクヘッジ |
| 18 | 終章：あなたへの提案 |
| 19 | 重要事項：法的免責と著作権 |
| 20 | 裏表紙 |

---

## 13. 新規ホワイトペーパー作成手順

### 13.1 基本手順

1. `whitepaper_part1.html` をコピー
2. ファイル名を変更（例: `new_whitepaper.html`）
3. 以下を書き換え:
   - `<title>` タグ
   - 表紙のタイトル・サブタイトル・著者情報
   - 目次
   - 各章の内容
   - フッターのセクション名
   - ページ番号
   - 裏表紙の情報

### 13.2 カラー変更時

`:root` 内の以下を変更:
```css
--color-brand: #新しい色;
--color-brand-soft: #新しい薄い色;
--color-brand-gradient: linear-gradient(135deg, #色1, #色2);
```

### 13.3 新しい章を追加

```html
<section class="page page-break">
  <div class="header-meta">
    <div class="header-meta__left">
      <span class="badge badge--outline" style="border-color: var(--color-alert); color: var(--color-alert);">機密</span>
      <span>ホワイトペーパー名</span>
    </div>
    <div class="header-meta__right">章名</div>
  </div>

  <div class="page-inner">
    <div class="chapter-heading">
      <div class="chapter-heading__eyebrow">CHAPTER XX</div>
      <div class="chapter-heading__title">章タイトル</div>
      <p class="chapter-heading__goal">この章の目的</p>
    </div>

    <!-- 本文コンテンツ -->

  </div>

  <div class="footer-meta">
    <div>章名</div>
    <div>ページ番号</div>
  </div>
</section>
```

---

## 14. 復元用チェックリスト

このテンプレートを完全に復元するために必要な要素:

### デザイン基盤
- [ ] Google Fonts: Noto Sans JP (300, 400, 500, 700)
- [ ] CSS変数: 全カラーパレット定義（ネイビー系ブランドカラー）
- [ ] A4ページサイズ設定
- [ ] 印刷用@pageルール

### コンポーネント
- [ ] Badge（バッジ）
- [ ] Label（ラベル）5種
- [ ] Callout（コールアウト）5種
- [ ] Checklist（チェックリスト）
- [ ] Steps（ステップリスト）
- [ ] Card（カード）
- [ ] Metric Box（メトリクス）
- [ ] Number Badge（番号バッジ）
- [ ] Arrow List（矢印リスト）
- [ ] Highlight Box（ハイライトボックス）
- [ ] Quote Box（引用ボックス）
- [ ] Target Badge（ターゲットバッジ）
- [ ] Table（テーブル）

### レイアウト
- [ ] 2カラム / 3カラム グリッド
- [ ] ヘッダー / フッター
- [ ] 章見出しコンポーネント
- [ ] 目次コンポーネント
- [ ] 表紙コンポーネント一式

### ブランド
- [ ] 組織名: 一般社団法人全国訪問看護経営研究協会
- [ ] 著者: 渋谷慶太
- [ ] 機密表示: 機密（赤）

---

## 更新履歴

| 日付 | 版数 | 内容 |
|------|------|------|
| 2025/12/06 | 1.0 | 初版作成 |



