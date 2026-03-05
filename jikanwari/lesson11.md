# 第11回：見た目を仕上げよう

## 今日のゴール 🎯
スマホでも見やすい完成度の高いデザインにする！

## 学ぶこと 📚
- レスポンシブデザインの基礎
- アニメーション効果
- 全体のデザイン調整

## やってみよう！ 💻

### ステップ1：スマホでも見やすくしよう
`<head>` に以下を追加：

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### ステップ2：全体のスタイルを整えよう

```css
* {
  box-sizing: border-box;
  font-family: 'Hiragino Sans', 'Meiryo', sans-serif;
}

body {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 100vh;
  padding: 20px;
}

h1 {
  color: white;
  text-align: center;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
  margin-bottom: 20px;
}
```

### ステップ3：カードデザインを追加

```css
.container {
  max-width: 800px;
  margin: 0 auto;
  background: white;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0 10px 40px rgba(0,0,0,0.2);
}
```

HTMLを修正（tableとbuttonsを囲む）：
```html
<div class="container">
  <div class="buttons">...</div>
  <table>...</table>
</div>
```

### ステップ4：アニメーション効果を追加

```css
/* 表示時のアニメーション */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.container {
  animation: fadeIn 0.5s ease-out;
}

/* マスのホバー効果 */
td {
  transition: all 0.3s ease;
}

td:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}
```

### ステップ5：スマホ対応

```css
@media (max-width: 600px) {
  table {
    font-size: 12px;
  }
  
  th, td {
    padding: 8px 5px;
    width: auto;
  }
  
  body {
    padding: 10px;
  }
}
```

## 今日のポイント 💡
- `viewport` → スマホでの表示を最適化
- `linear-gradient` → グラデーション背景
- `@keyframes` → アニメーションを定義
- `transition` → 滑らかな変化
- `@media` → 画面サイズによるスタイル変更

## チャレンジ問題 🌟
1. 背景のグラデーションを自分の好きな色に変えてみよう
2. ボタンにもホバーアニメーションを追加してみよう
3. 表の見出しの色を変えてみよう

## 今日のアウトプット ✅
- [ ] きれいなグラデーション背景になった
- [ ] カードデザインが適用された
- [ ] アニメーションが動いている
- [ ] スマホサイズでも見やすい

## 理解度チェック ✅
1. スマホで正しく表示させるために必要なタグはどれですか？
2. 背景色をグラデーションにするCSS関数はどれですか？
3. アニメーションの動きを定義するためのCSSのルールはどれですか？
4. スタイルの変化を滑らかにするためのプロパティはどれですか？
5. 画面のサイズに合わせてスタイルを変えるためのCSSのルールはどれですか？
