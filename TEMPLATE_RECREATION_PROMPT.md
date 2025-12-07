# ホワイトペーパーテンプレート再現用プロンプト

> このプロンプトをAIに渡すことで、同じデザインのホワイトペーパーを再現できます。

---

## プロンプト本文

```
あなたは「一般社団法人全国訪問看護経営研究協会」のホワイトペーパーを作成するHTMLデザイナーです。
以下の仕様に厳密に従って、A4印刷対応のHTMLホワイトペーパーを作成してください。

【基本仕様】
- A4縦サイズ（210mm × 297mm）
- 印刷・PDF出力対応
- フォント: Noto Sans JP（Google Fonts）
- 本文サイズ: 13.5px、行高: 1.8

【カラーパレット】
- ブランドカラー: #1a365d（ネイビー系）
- ブランド薄い色: #e8eef5
- 成功色: #0F9D58 / 背景: #E6F4EA
- 警告色: #F9AB00 / 背景: #FEF7E0
- 危険色: #D93025 / 背景: #FDECEA
- 情報色: #4285F4 / 背景: #E8F0FE
- テキスト: #222222
- 補足テキスト: #666666
- ボーダー: #E0E3EB
- 背景（薄い）: #F5F7FB

【ページ構造】
各ページは以下の構造:
1. header-meta（上部12mm）: 左に「機密」バッジ＋ドキュメント名、右にバージョンor章名
2. page-inner（本文エリア）: max-width 130mm、上下マージン 22mm/20mm
3. footer-meta（下部10mm）: 左にセクション名、右にページ番号

【必須コンポーネント】
1. バッジ（Badge）: 丸角ピル型、アウトラインスタイル
2. ラベル（Label）: 丸角ピル型、塗りつぶしスタイル、5色バリエーション
3. コールアウト（Callout）: 左ボーダー3px、背景色付き、5種類（標準/info/success/warning/alert）
4. チェックリスト: ☐マーク付きリスト
5. ステップリスト: 丸数字バッジ付き手順リスト
6. カード: ボーダー＋角丸8px、ハイライト版あり
7. メトリクスボックス: ラベル＋大きな数値＋補足
8. テーブル: 100%幅、ヘッダー背景付き、偶数行ストライプ
9. ハイライトボックス: brand色ボーダー＋薄いbrand背景
10. 引用ボックス: 左ボーダー4px＋薄いグレー背景
11. 矢印リスト: →マーク付きリスト

【章見出しの構造】
```html
<div class="chapter-heading">
  <div class="chapter-heading__eyebrow">CHAPTER XX</div>
  <div class="chapter-heading__title">章タイトル</div>
  <p class="chapter-heading__goal">この章の目的説明</p>
</div>
```

【見出し階層】
- h1: 22px
- h2: 16px、左ボーダー3px（ブランド色）
- h3: 14px
- h4: 13px

【表紙の構成】
- タグライン（丸角ピル、薄い背景）例: WHITE PAPER 2025
- メインタイトル（26px太字）
- サブタイトル（14px、左ボーダー付き、イタリック）
- リード文
- 対象読者バッジ
- メタ情報（発行日、著作権、著者）
- フッターストリップ（グラデーション、高さ12mm）

【レイアウトヘルパー】
- .two-column: 2カラムグリッド（1fr 1fr）
- .two-column--wide-left: 左広め（1.3fr 1fr）
- .three-column: 3カラムグリッド

【ブランド情報】
- 組織名: 一般社団法人全国訪問看護経営研究協会
- 英語: Japan Home Visit Nursing Management Research Association
- 著者: 渋谷慶太
- 機密表示: 機密（赤色）

【印刷設定】
@page { size: A4; margin: 16mm 18mm; }
```

---

## クイックリファレンス：よく使うコンポーネントのHTML

### コールアウト（5種）
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

### ラベル（5種）
```html
<span class="label">標準</span>
<span class="label label--info">INFO</span>
<span class="label label--success">OK</span>
<span class="label label--warning">注意</span>
<span class="label label--alert">危険</span>
```

### チェックリスト
```html
<ul class="checklist">
  <li>チェック項目1</li>
  <li>チェック項目2</li>
</ul>
```

### ステップリスト
```html
<ol class="steps">
  <li><strong>手順1</strong><br>説明</li>
  <li><strong>手順2</strong><br>説明</li>
</ol>
```

### カード
```html
<div class="card">
  <div class="card__title">タイトル</div>
  <div class="card__content">内容</div>
</div>

<div class="card card--highlight">
  <!-- 強調版 -->
</div>
```

### メトリクスボックス
```html
<div class="metric-box">
  <div class="metric-box__label">ラベル</div>
  <div class="metric-box__value">50%</div>
  <div class="metric-box__note">補足</div>
</div>

<!-- 色付き -->
<div class="metric-box" style="background: var(--color-success-soft);">
  <div class="metric-box__value" style="color: var(--color-success);">値</div>
</div>
```

### ハイライトボックス
```html
<div class="highlight-box">
  <p style="margin: 0; font-weight: 600;">【タイトル】</p>
  <p style="margin: 8px 0 0;">本文</p>
</div>
```

### 引用ボックス
```html
<div class="quote-box">
  <p style="margin: 0;">重要なメッセージや引用</p>
</div>
```

### 矢印リスト
```html
<ul class="arrow-list">
  <li>項目1</li>
  <li>項目2</li>
</ul>
```

### 2カラム・3カラム
```html
<div class="two-column">
  <div>左</div>
  <div>右</div>
</div>

<div class="three-column">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
```

### テーブル
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

### ページテンプレート
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

## 完全なCSSコード（コピー用）

以下のCSSをHTMLの`<style>`タグ内に配置してください:

```css
:root {
  --page-width: 210mm;
  --page-height: 297mm;

  --font-body: "Noto Sans JP", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-size-body: 13.5px;
  --font-size-small: 11px;

  --color-bg-canvas: #eeeeee;
  --color-bg-page: #ffffff;
  --color-text: #222222;
  --color-text-muted: #666666;
  --color-heading: #111111;
  --color-border: #E0E3EB;
  --color-soft: #F5F7FB;

  --color-brand: #1a365d;
  --color-brand-soft: #e8eef5;
  --color-brand-gradient: linear-gradient(135deg, #1a365d, #2c5282);

  --color-success: #0F9D58;
  --color-success-soft: #E6F4EA;
  --color-warning: #F9AB00;
  --color-warning-soft: #FEF7E0;
  --color-alert: #D93025;
  --color-alert-soft: #FDECEA;
  --color-info: #4285F4;
  --color-info-soft: #E8F0FE;
}

* { box-sizing: border-box; }
html, body { margin: 0; padding: 0; }

body {
  font-family: var(--font-body);
  color: var(--color-text);
  background: var(--color-bg-canvas);
}

@page {
  size: A4;
  margin: 16mm 18mm;
}

@media print {
  body { background: #ffffff; }
  .page { margin: 0; box-shadow: none; border-radius: 0; }
  .no-print { display: none !important; }
}

.document { padding: 16px 0 32px; }

.page {
  position: relative;
  width: var(--page-width);
  min-height: var(--page-height);
  margin: 0 auto 16px;
  background: var(--color-bg-page);
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.08);
  overflow: hidden;
}

.page-inner {
  max-width: 130mm;
  margin: 22mm auto 20mm;
}

.page--cover .page-inner {
  max-width: 140mm;
  margin-top: 30mm;
}

.page--toc .page-inner {
  max-width: 150mm;
  margin-top: 22mm;
}

.page--wide .page-inner {
  max-width: 170mm;
}

.page-break { page-break-after: always; }

.header-meta {
  position: absolute;
  top: 12mm;
  left: 18mm;
  right: 18mm;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: var(--font-size-small);
  color: var(--color-text-muted);
}

.header-meta__left {
  display: flex;
  align-items: center;
  gap: 8px;
}

.footer-meta {
  position: absolute;
  bottom: 10mm;
  left: 18mm;
  right: 18mm;
  border-top: 1px solid var(--color-border);
  padding-top: 4mm;
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: var(--color-text-muted);
}

.badge {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 999px;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.1em;
}

.badge--outline {
  border: 1px solid var(--color-brand);
  color: var(--color-brand);
}

h1, h2, h3, h4 {
  margin: 0 0 10px;
  color: var(--color-heading);
  line-height: 1.4;
}

h1 { font-size: 22px; margin-bottom: 8px; }

h2 {
  font-size: 16px;
  margin-top: 16px;
  border-left: 3px solid var(--color-brand);
  padding-left: 8px;
}

h3 { font-size: 14px; margin-top: 14px; }
h4 { font-size: 13px; margin-top: 10px; }

p {
  font-size: var(--font-size-body);
  line-height: 1.8;
  margin: 0 0 8px;
}

.lead {
  font-size: 14px;
  line-height: 1.9;
  margin-bottom: 12px;
}

.small {
  font-size: var(--font-size-small);
  color: var(--color-text-muted);
}

ul, ol {
  font-size: var(--font-size-body);
  line-height: 1.8;
  margin: 0 0 8px 20px;
  padding: 0;
}

li { margin-bottom: 4px; }

.cover-title {
  font-size: 26px;
  line-height: 1.5;
  font-weight: 700;
  margin-bottom: 10px;
}

.cover-subtitle {
  font-size: 14px;
  color: var(--color-text-muted);
  margin-bottom: 18px;
  border-left: 3px solid var(--color-brand);
  padding-left: 12px;
  font-style: italic;
}

.cover-tagline {
  display: inline-block;
  padding: 4px 10px;
  border-radius: 999px;
  background: var(--color-brand-soft);
  color: var(--color-brand);
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  margin-bottom: 12px;
}

.cover-meta {
  margin-top: 40px;
  font-size: var(--font-size-small);
  color: var(--color-text-muted);
}

.cover-meta strong { color: var(--color-heading); }

.cover-strip {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 12mm;
  background: var(--color-brand-gradient);
  opacity: 0.85;
}

.cover-strip__text {
  position: absolute;
  right: 24mm;
  bottom: 4mm;
  font-size: 10px;
  color: #ffffff;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.toc-block {
  padding: 10px 12px;
  border-radius: 10px;
  border: 1px solid var(--color-border);
  background: #fafbff;
  margin-bottom: 14px;
}

.toc-title {
  font-size: 13px;
  font-weight: 600;
  margin-bottom: 8px;
}

.toc-item {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  font-size: 12px;
  margin-bottom: 4px;
}

.toc-item__label { color: var(--color-text-muted); }
.toc-item__page { font-variant-numeric: tabular-nums; color: var(--color-text-muted); }

.two-column {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.two-column--wide-left { grid-template-columns: 1.3fr 1fr; }

.three-column {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.callout {
  border-left: 3px solid var(--color-brand);
  background: var(--color-soft);
  padding: 8px 10px;
  margin: 8px 0 12px;
  font-size: 12.5px;
  border-radius: 0 6px 6px 0;
}

.callout--info { border-left-color: var(--color-info); background: var(--color-info-soft); }
.callout--success { border-left-color: var(--color-success); background: var(--color-success-soft); }
.callout--warning { border-left-color: var(--color-warning); background: var(--color-warning-soft); }
.callout--alert { border-left-color: var(--color-alert); background: var(--color-alert-soft); }

.callout-title {
  font-weight: 600;
  margin-bottom: 4px;
  font-size: 12.5px;
}

.label {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 999px;
  background: var(--color-soft);
  color: var(--color-brand);
  font-size: 11px;
  font-weight: 500;
  margin-bottom: 4px;
}

.label--info { background: var(--color-info-soft); color: var(--color-info); }
.label--success { background: var(--color-success-soft); color: var(--color-success); }
.label--warning { background: var(--color-warning-soft); color: var(--color-warning); }
.label--alert { background: var(--color-alert-soft); color: var(--color-alert); }

.checklist {
  list-style: none;
  margin-left: 0;
}

.checklist li {
  position: relative;
  padding-left: 18px;
  margin-bottom: 4px;
}

.checklist li::before {
  content: "☐";
  position: absolute;
  left: 0;
  top: 0;
  font-size: 11px;
  color: var(--color-brand);
}

.checklist--done li::before {
  content: "✔";
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 8px 0 12px;
  font-size: 12.5px;
}

th, td {
  border: 1px solid var(--color-border);
  padding: 6px 8px;
  text-align: left;
}

th {
  background: var(--color-soft);
  font-weight: 500;
}

tr:nth-child(even) { background: #fafbfc; }

.chapter-heading { margin-bottom: 6px; }

.chapter-heading__eyebrow {
  font-size: 11px;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--color-brand);
  margin-bottom: 4px;
}

.chapter-heading__title {
  font-size: 18px;
  font-weight: 700;
  line-height: 1.5;
}

.chapter-heading__goal {
  font-size: 12.5px;
  color: var(--color-text-muted);
  margin-top: 4px;
  margin-bottom: 10px;
}

.section-separator {
  margin: 10px 0;
  border: 0;
  border-top: 1px dashed var(--color-border);
}

.steps {
  counter-reset: step-counter;
  list-style: none;
  margin-left: 0;
  padding-left: 0;
}

.steps li {
  position: relative;
  padding-left: 32px;
  margin-bottom: 12px;
  counter-increment: step-counter;
}

.steps li::before {
  content: counter(step-counter);
  position: absolute;
  left: 0;
  top: 0;
  width: 22px;
  height: 22px;
  background: var(--color-brand);
  color: #fff;
  border-radius: 50%;
  font-size: 12px;
  font-weight: 600;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card {
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 12px;
  background: #fff;
}

.card__title {
  font-size: 13px;
  font-weight: 600;
  margin-bottom: 6px;
}

.card__content {
  font-size: 12px;
  color: var(--color-text-muted);
}

.card--highlight {
  border-color: var(--color-brand);
  background: var(--color-brand-soft);
}

.metric-box {
  background: var(--color-soft);
  border-radius: 8px;
  padding: 10px 12px;
  margin-bottom: 8px;
}

.metric-box__label {
  font-size: 11px;
  color: var(--color-text-muted);
  margin-bottom: 2px;
}

.metric-box__value {
  font-size: 18px;
  font-weight: 700;
  color: var(--color-brand);
}

.metric-box__note {
  font-size: 10px;
  color: var(--color-text-muted);
}

.number-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
  background: var(--color-brand);
  color: #fff;
  border-radius: 50%;
  font-size: 12px;
  font-weight: 600;
  margin-right: 6px;
}

.arrow-list {
  list-style: none;
  margin-left: 0;
  padding-left: 0;
}

.arrow-list li {
  padding-left: 16px;
  position: relative;
  margin-bottom: 4px;
}

.arrow-list li::before {
  content: "→";
  position: absolute;
  left: 0;
  color: var(--color-brand);
}

.highlight-box {
  background: var(--color-brand-soft);
  border: 1px solid var(--color-brand);
  border-radius: 8px;
  padding: 12px;
  margin: 12px 0;
}

.quote-box {
  background: var(--color-soft);
  border-left: 4px solid var(--color-brand);
  padding: 12px 16px;
  margin: 12px 0;
  font-style: italic;
}

.target-badge {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 4px;
  background: var(--color-warning-soft);
  color: #9a6700;
  font-size: 11px;
  font-weight: 600;
  margin-right: 8px;
}
```

---

## 使用例：新しいホワイトペーパー作成

### プロンプト例
```
上記のテンプレート仕様に従って、以下のトピックでホワイトペーパーを作成してください：

【タイトル】訪問看護ステーションの採用戦略
【対象読者】訪問看護経営者、人事担当者
【章構成】
- 第1章：採用市場の現状分析
- 第2章：効果的な求人広告の作り方
- 第3章：面接・選考のベストプラクティス
- 第4章：オンボーディングと定着率向上
【著作権】一般社団法人全国訪問看護経営研究協会　渋谷慶太
```



