# 第11回：図鑑に新しい生き物を追加しよう！

## 今日のゴール 🎯
フォームを使って、図鑑に新しい生き物のデータを入力して追加できるようにする！

## 学ぶこと 📚
- 情報を入力するフォーム（`<input>` タグ）
- ボタンをクリックした時に関数を呼び出す方法
- 関数（ファンクション）の作り方

## やってみよう！ 💻

### ステップ1：入力フォームをHTMLに追加しよう
`<div id="zukan-container">` の前に、生き物を登録するフォームを追加します。

```html
<body>
  <h1>わたしの図鑑</h1>

  <!-- 追加フォームを入れる箱 -->
  <div class="add-form">
    <h2>🐾 生き物を追加する</h2>
    <input id="input-name"  type="text" placeholder="名前（例：タンポポ）">
    <input id="input-place" type="text" placeholder="場所（例：公園）">
    <input id="input-date"  type="text" placeholder="日付（例：3月5日）">
    <input id="input-memo"  type="text" placeholder="メモ（例：黄色い花）">
    <button onclick="addIkimono()">追加する！</button>
  </div>

  <div id="zukan-container" class="zukan-container"></div>
</body>
```

### ステップ2：追加フォームのCSSを書こう
`<style>` の中に、フォームのデザインを追加します。

```html
<style>
  /* ...既存のCSS... */

  .add-form {
    background-color: white;
    max-width: 500px;
    margin: 20px auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    text-align: center;
  }

  .add-form input {
    display: block;
    width: 80%;
    margin: 8px auto;
    padding: 8px 12px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 14px;
  }

  .add-form button {
    margin-top: 12px;
    padding: 10px 24px;
    background-color: #2e8b57;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
  }
  
  .add-form button:hover {
    background-color: #236b43;
  }
</style>
```

### ステップ3： JavaScriptで「追加する関数」を書こう
`<script>` の中に、フォームの入力値を読み取ってカードを追加する関数を書きます。

```javascript
  <script>
    // ★ 前回のzukanDataと自動生成のコードはそのまま残す ★
    // ...

    // 生き物を追加する関数
    function addIkimono() {
      // フォームから入力された値を取得する
      let name  = document.getElementById("input-name").value;
      let place = document.getElementById("input-place").value;
      let date  = document.getElementById("input-date").value;
      let memo  = document.getElementById("input-memo").value;
      
      // 名前が空っぽだったら警告して終わる
      if (name === "") {
        alert("名前を入力してください！");
        return;
      }

      // 新しい生き物のカードHTMLを作って追加する
      let container = document.getElementById("zukan-container");
      let cardHTML = `
        <div class="card" onclick="alert('${name}だよ！')">
          <h2>${name}</h2>
          <img src="https://placehold.jp/240x180.png?text=${name}" alt="${name}の写真" width="200">
          <p>${memo}</p>
          <ul>
            <li>📍 場所：${place}</li>
            <li>📅 日付：${date}</li>
          </ul>
        </div>
      `;
      container.innerHTML += cardHTML;

      // フォームを空っぽにリセットする
      document.getElementById("input-name").value  = "";
      document.getElementById("input-place").value = "";
      document.getElementById("input-date").value  = "";
      document.getElementById("input-memo").value  = "";
    }
  </script>
```

### ステップ4：ブラウザで確認しよう
1. ブラウザを更新します。
2. フォームに生き物の情報を入力して、「追加する！」ボタンを押してみよう！
3. 図鑑にタイルが追加されたら成功！

## 今日のポイント 💡
- `<input>` → ユーザーが文字を入力できるテキストボックスです。
- `<button onclick="関数名()">` → クリックしたときに指定した関数を実行します。
- **関数（ファンクション）** は `function 名前() { ... }` という形で作ります。呼び出された時に `{ }` の中の処理を実行します。
- `.value` → 入力フォームの中に書かれた文字を取得します。

## チャレンジ問題 🌟
「追加する！」ボタンを押したとき、追加後にメッセージ `alert('追加したよ！')` を出してみよう！

## 今日のアウトプット ✅
- [ ] フォームとボタンを追加できた
- [ ] ボタンを押して新しいカードを追加できた

## 理解度チェック ✅
1. ユーザーが文字を入力できる欄（テキストボックス）を作るタグは何ですか？
2. JavaScript で関数を作るときに使うキーワードは何ですか？
