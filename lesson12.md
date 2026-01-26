# 第12回：完成！自分だけの時間割アプリ

## 今日のゴール 🎯
オリジナルの機能やデザインを追加して完成させる！

## これまでのふりかえり 📖

| 回 | 学んだこと |
|---|---|
| 1 | HTMLの基本、ファイルの作り方 |
| 2 | CSSでデザイン、色の変え方 |
| 3 | テーブル（表）の作り方 |
| 4 | テーブルのスタイリング |
| 5 | JavaScript入門、ボタン処理 |
| 6 | クリックイベント、入力処理 |
| 7 | セレクトボックス |
| 8 | ローカルストレージ保存 |
| 9 | データ読み込み |
| 10 | リセット機能 |
| 11 | レスポンシブ＆アニメーション |

## カスタマイズアイデア 💡

### アイデア1：教科ごとの色分け

```javascript
// 教科の色
const subjectColors = {
  '国語': '#ffcdd2',
  '算数': '#c8e6c9',
  '理科': '#bbdefb',
  '社会': '#fff9c4',
  '英語': '#f8bbd0',
  // 他の教科も追加
};

// マスに色をつける
function updateCellColor(cell) {
  const subject = cell.textContent;
  cell.style.backgroundColor = subjectColors[subject] || '';
}
```

### アイデア2：今日の授業をハイライト

```javascript
// 今日の曜日を取得（0=日曜, 1=月曜...）
const today = new Date().getDay();

// 月〜金（1〜5）の場合、その列をハイライト
if (today >= 1 && today <= 5) {
  const rows = document.querySelectorAll('tr');
  rows.forEach(function(row) {
    const cell = row.children[today];
    if (cell) {
      cell.style.boxShadow = '0 0 10px #ffd700';
    }
  });
}
```

### アイデア3：印刷機能

```html
<button id="printButton">🖨️ 印刷</button>
```

```javascript
document.getElementById('printButton').onclick = function() {
  window.print();
};
```

### アイデア4：時間割のタイトル変更

```html
<input type="text" id="titleInput" placeholder="時間割の名前">
```

```javascript
const titleInput = document.getElementById('titleInput');
const title = document.querySelector('h1');

titleInput.onchange = function() {
  title.textContent = titleInput.value || '時間割';
  localStorage.setItem('title', titleInput.value);
};

// 読み込み時
const savedTitle = localStorage.getItem('title');
if (savedTitle) {
  title.textContent = savedTitle;
  titleInput.value = savedTitle;
}
```

## 自分だけのアイデアを追加しよう！ ✨

考えてみよう：
- 🎨 色やデザインを変えてみる
- ⏰ 時間の表示を追加する
- 🔔 特定の教科にマークをつける
- 📝 メモ欄を追加する
- 🌙 ダークモードを作る

## 完成おめでとう！ 🎉

これで自分だけの時間割アプリが完成しました！

### 次のステップ
- 友達や家族に見せてみよう
- もっといろんな機能を追加してみよう
- 他のWebアプリにも挑戦してみよう

## 最終チェックリスト ✅
- [ ] 時間割表が表示される
- [ ] 教科を選択できる
- [ ] データが保存される
- [ ] リセットができる
- [ ] デザインがかっこいい
- [ ] オリジナルの機能を追加した

## 学んだスキル 🏆
```
✓ HTML - Webページの構造を作る
✓ CSS - デザインを整える
✓ JavaScript - 動きをつける
✓ ローカルストレージ - データを保存する
```

**おつかれさま！これであなたもWebプログラマーの仲間入りだ！** 🚀

## 理解度チェック ✅
1. ブラウザの印刷機能を呼び出すためのJavaScriptの命令はどれですか？
2. `new Date().getDay()` で「0」が返ってきた場合、それは何曜日ですか？
3. このコースでデータをブラウザに保存するために使った機能は何ですか？
4. JavaScriptで要素の背景色を変更する場合、`style` のあとに続くプロパティ名は何ですか？
5. `window` オブジェクトの `print` メソッドを実行すると何が起きますか？
