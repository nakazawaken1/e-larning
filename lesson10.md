# 第10回：リセット機能を作ろう

## 今日のゴール 🎯
全データをリセットするボタンを作る！

## 学ぶこと 📚
- データの削除方法
- 確認ダイアログの使い方
- ボタンのデザイン

## やってみよう！ 💻

### ステップ1：リセットボタンを追加しよう
`<h1>` の下あたりに追加：

```html
<div class="buttons">
  <button id="resetButton">🗑️ リセット</button>
</div>
```

### ステップ2：ボタンのスタイルを追加

```css
.buttons {
  text-align: center;
  margin: 10px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  margin: 5px;
}

#resetButton {
  background-color: #ff6b6b;
  color: white;
}

#resetButton:hover {
  background-color: #ee5a5a;
}
```

### ステップ3：リセット処理を作ろう

```javascript
// リセットボタンの処理
const resetButton = document.getElementById('resetButton');

resetButton.onclick = function() {
  // 確認ダイアログ
  const ok = confirm('本当に全部消しますか？');
  
  if (ok) {
    // ローカルストレージから削除
    localStorage.removeItem('schedule');
    
    // 全てのマスを空にする
    const cells = document.querySelectorAll('td');
    cells.forEach(function(cell) {
      cell.textContent = '';
    });
    
    alert('リセットしました！');
  }
};
```

## 今日のポイント 💡
- `confirm()` → OK/キャンセルの確認ダイアログを表示
- OKなら `true`、キャンセルなら `false` が返る
- `removeItem()` → 指定したキーのデータを削除
- 間違って消さないように確認を入れる！

## 危険な操作には確認を！ ⚠️
データを消す操作は取り消しできないので、必ず確認を入れよう！

```javascript
if (confirm('本当にいいですか？')) {
  // OKが押された時の処理
}
```

## チャレンジ問題 🌟
1. 「保存」ボタンも追加してみよう（手動保存）
2. リセット後に「リセットしました」を画面に表示してみよう
3. ボタンにアニメーション効果を追加してみよう

```css
button:active {
  transform: scale(0.95);
}
```

## 今日のアウトプット ✅
- [ ] リセットボタンが表示されている
- [ ] ボタンを押すと確認ダイアログが出る
- [ ] OKを押すと全データが消える
- [ ] キャンセルを押すと何も起きない

## 理解度チェック ✅
1. ローカルストレージから特定のキーのデータを削除する命令はどれですか？
2. 「OK」と「キャンセル」のボタンがある確認ダイアログを表示する関数はどれですか？
3. `confirm()` で「OK」が押された時、返ってくる値は何ですか？
4. `confirm()` で「キャンセル」が押された時、返ってくる値は何ですか？
5. ボタンがクリックされている瞬間のスタイルを指定するCSSの書き方はどれですか？
