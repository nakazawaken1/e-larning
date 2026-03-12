# 第4回：ボタンをかっこよくしよう

## 今日のゴール 🎯
CSSを使って、クイズの箱やボタンをプロっぽくデザインする！

## 学ぶこと 📚
- 枠線を引く（`border`）
- 角を丸くする（`border-radius`）
- 内側の余白（`padding`）と外側の余白（`margin`）
- マウスを乗せた時の変化（`:hover`）

## やってみよう！ 💻

### ステップ1：クイズの箱をデザインしよう
```css
#quiz-container {
  background-color: white;
  max-width: 400px;
  margin: 20px auto;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
```

### ステップ2：ボタンをおしゃれにしよう
```css
button {
  display: block;
  width: 100%;
  margin: 10px 0;
  padding: 15px;
  font-size: 18px;
  background-color: #f8fafc;
  border: 2px solid #e2e8f0;
  border-radius: 10px;
  cursor: pointer;
  transition: 0.3s; /* じわっと変わる */
}

button:hover {
  background-color: #0ea5e9;
  color: white;
  border-color: #0ea5e9;
}
```

## 今日のポイント 💡
- `padding` は箱の中のすきま、 `margin` は箱の外のすきま。
- `border-radius` を大きくすると丸っこくなるよ。
- `:hover` を使うと、マウスを乗せた時に反応するから楽しい！

## 理解度チェック ✅
1. 箱の「内側」の余白を作るプロパティは何ですか？
2. 箱の「外側」の余白を作るプロパティは何ですか？
3. 角を丸くするために使うプロパティは何ですか？
4. マウスが要素の上に乗った時だけスタイルを変える仕組み（疑似クラス）を何と言いますか？
5. 色や形をじわっとゆっくり変えるために使うプロパティは何ですか？
