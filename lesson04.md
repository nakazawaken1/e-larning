# 第4回：表をきれいにデザインしよう

## 今日のゴール 🎯
見やすくデザインされた時間割表を作る！

## 学ぶこと 📚
- テーブルの枠線の付け方
- マスの大きさ調整
- 曜日ごとの色分け

## やってみよう！ 💻

### ステップ1：表に枠線をつけよう
`<style>` の中に以下を追加：

```css
table {
  border-collapse: collapse;
  margin: 20px auto;
}

th, td {
  border: 2px solid #333;
  padding: 15px 20px;
  text-align: center;
  width: 80px;
  height: 50px;
}

th {
  background-color: #4169e1;
  color: white;
}
```

### ステップ2：見出し行をカラフルにしよう
曜日ごとに色を変えるため、HTMLにクラスを追加：

```html
<tr>
  <th></th>
  <th class="mon">月</th>
  <th class="tue">火</th>
  <th class="wed">水</th>
  <th class="thu">木</th>
  <th class="fri">金</th>
</tr>
```

CSSに色を追加：

```css
.mon { background-color: #ff6b6b; }
.tue { background-color: #feca57; }
.wed { background-color: #48dbfb; }
.thu { background-color: #1dd1a1; }
.fri { background-color: #ff9ff3; }
```

### ステップ3：ホバー効果を追加しよう
マウスを乗せると色が変わる効果：

```css
td:hover {
  background-color: #fffacd;
  cursor: pointer;
}
```

## 今日のポイント 💡
- `border-collapse: collapse` → マスの境界線を1本にまとめる
- `padding` → マスの内側の余白
- `margin: 20px auto` → 上下20px、左右は自動で中央配置
- `:hover` → マウスを乗せた時のスタイル

## チャレンジ問題 🌟
1. 1時間目の横の見出しにも色をつけてみよう
2. 表に角丸をつけてみよう（ヒント：`border-radius`）

## 今日のアウトプット ✅
- [ ] 表に枠線がついた
- [ ] 見出しに色がついた
- [ ] マウスを乗せると色が変わる

## 理解度チェック ✅
1. 隣り合う枠線を1本にまとめるためのCSSプロパティはどれですか？
2. マスの内側の余白をとるためのCSSプロパティはどれですか？
3. 表を画面の中央に配置するために使うCSSプロパティはどれですか？
4. マウスを乗せた時のスタイルを指定するために使う記法はどれですか？
5. 特定の曜日の色だけを変えたい場合、HTMLタグに追加すべき属性はどれですか？
