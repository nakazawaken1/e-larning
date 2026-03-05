# 第9回：ページを開いたらデータを読み込もう

## 今日のゴール 🎯
保存したデータが次回アクセス時に自動で表示される！

## 学ぶこと 📚
- ページ読み込み時の処理
- 保存したデータの復元
- JSONから配列への変換

## やってみよう！ 💻

### ステップ1：データを読み込む関数を作ろう

```javascript
// 時間割データを読み込む関数
function loadSchedule() {
  // 保存されたデータを取得
  const savedData = localStorage.getItem('schedule');
  
  // データがなければ終了
  if (!savedData) {
    console.log('保存データがありません');
    return;
  }
  
  // JSON文字列を配列に戻す
  const scheduleData = JSON.parse(savedData);
  
  // すべてのマスを取得
  const cells = document.querySelectorAll('td');
  
  // 各マスにデータを設定
  cells.forEach(function(cell, index) {
    if (scheduleData[index]) {
      cell.textContent = scheduleData[index];
    }
  });
  
  console.log('読み込みました！', scheduleData);
}
```

### ステップ2：ページ読み込み時に実行しよう

```javascript
// ページが読み込まれたら実行
document.addEventListener('DOMContentLoaded', function() {
  loadSchedule();
});
```

### ステップ3：動作確認！
1. いくつかの教科を選択
2. ブラウザを閉じる
3. もう一度ファイルを開く
4. 前回の内容が表示されていれば成功！

## 今日のポイント 💡
- `DOMContentLoaded` → HTMLの読み込みが完了したイベント
- `addEventListener` → イベントに処理を追加
- `JSON.parse()` → JSON文字列をJavaScriptのデータに戻す
- `forEach` の第2引数 `index` → 何番目の要素かがわかる

## コードの実行順序 📋
1. HTMLが読み込まれる
2. `DOMContentLoaded` イベントが発生
3. `loadSchedule()` が実行される
4. 保存データが表示される

## チャレンジ問題 🌟
1. データがない時に「まだ時間割が登録されていません」と表示してみよう
2. 読み込み完了時にメッセージを一瞬だけ表示してみよう

## 今日のアウトプット ✅
- [ ] ページを開くと前回のデータが表示される
- [ ] Consoleに「読み込みました！」と表示される
- [ ] ブラウザを閉じて開いても内容が残っている

## 理解度チェック ✅
1. JSON形式の文字列を、JavaScriptの配列やオブジェクトに戻す関数はどれですか？
2. HTMLの読み込みが完了した時に発生するイベントの名前は何ですか？
3. イベントが発生した時の処理を追加するための命令はどれですか？
4. ローカルストレージにデータが保存されていない場合、`getItem` は何を返しますか？
5. `forEach` の2番目の引数（`index`）には何が入っていますか？
