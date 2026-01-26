# 第8回：データを保存しよう！ローカルストレージ基礎

## 今日のゴール 🎯
入力した教科がブラウザに保存される機能を作る！

## 学ぶこと 📚
- ローカルストレージとは？
- データの保存方法
- 時間割データの構造

## ローカルストレージとは？ 💾
- ブラウザにデータを保存できる仕組み
- ページを閉じてもデータが残る
- パソコンの中に保存される（インターネット不要）

## やってみよう！ 💻

### ステップ1：基本的な使い方を試そう
開発者ツール（F12）のConsoleで試してみよう：

```javascript
// 保存する
localStorage.setItem('name', '太郎');

// 読み込む
console.log(localStorage.getItem('name')); // 太郎

// 削除する
localStorage.removeItem('name');
```

### ステップ2：時間割データを保存する関数を作ろう

```javascript
// 時間割データを保存する関数
function saveSchedule() {
  // 時間割データを入れる配列
  const scheduleData = [];
  
  // すべてのマスを取得
  const cells = document.querySelectorAll('td');
  
  // 各マスの内容を配列に追加
  cells.forEach(function(cell) {
    scheduleData.push(cell.textContent);
  });
  
  // JSON形式で保存
  localStorage.setItem('schedule', JSON.stringify(scheduleData));
  
  console.log('保存しました！', scheduleData);
}
```

### ステップ3：選択時に自動保存するようにしよう
`select.onchange` の中で `saveSchedule()` を呼び出す：

```javascript
select.onchange = function() {
  cell.textContent = select.value;
  saveSchedule(); // ← これを追加！
};
```

### ステップ4：保存されたか確認しよう
1. 教科を選択
2. 開発者ツールのConsoleで確認
3. 「保存しました！」と表示されればOK

## 今日のポイント 💡
- `localStorage.setItem(キー, 値)` → データを保存
- `localStorage.getItem(キー)` → データを読み込み
- `JSON.stringify()` → 配列やオブジェクトを文字列に変換
- ローカルストレージには文字列しか保存できない

## JSONとは？ 📝
- JavaScriptのデータを文字列にする形式
- 配列 `['国語', '算数']` → 文字列 `'["国語","算数"]'`
- データのやり取りによく使われる

## チャレンジ問題 🌟
1. 開発者ツールの「Application」タブ → 「Local Storage」で保存されたデータを確認してみよう
2. 「保存しました！」の代わりに画面にメッセージを表示してみよう

## 今日のアウトプット ✅
- [ ] 教科を選ぶと自動で保存される
- [ ] Consoleに「保存しました！」と表示される
- [ ] Local Storageにデータが入っている

## 理解度チェック ✅
1. ローカルストレージにデータを保存するための命令はどれですか？
2. ローカルストレージからデータを読み込むための命令はどれですか？
3. ローカルストレージに保存したデータは、ブラウザを閉じると消えますか？
4. 配列やオブジェクトをJSON形式の文字列に変換する関数はどれですか？
5. ローカルストレージの中身を確認できる開発者ツールのタブ名はどれですか？
