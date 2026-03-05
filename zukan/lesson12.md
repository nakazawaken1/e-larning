# 第12回：オリジナル図鑑の完成！🎉

## 今日のゴール 🎯
これまで学んだすべてを使って、自分だけのオリジナル図鑑を完成させる！

## 学ぶこと 📚
- これまで学んだHTML・CSS・JavaScriptの総復習
- 自分らしくカスタマイズする方法

## 今回の完成形コード
これが、図鑑Webサービスのすべての機能が入った完成版のコードです！
全部コピーして、自分だけのカスタマイズを加えてみよう！

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>わたしのオリジナル図鑑</title>
  <style>
    body {
      background-color: #f0f8ff;
      font-family: sans-serif;
      margin: 0;
    }

    /* --- ヘッダー --- */
    header {
      background-color: #2e8b57;
      color: white;
      text-align: center;
      padding: 20px;
    }
    header h1 {
      margin: 0;
      font-size: 2em;
    }

    /* --- 追加フォーム --- */
    .add-form {
      background-color: white;
      max-width: 500px;
      margin: 20px auto;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      text-align: center;
    }
    .add-form h2 { color: #2e8b57; }
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
    .add-form button:hover { background-color: #236b43; }

    /* --- 図鑑タイル --- */
    .zukan-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
      padding: 24px;
    }
    .card {
      background-color: white;
      width: 250px;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      text-align: center;
      cursor: pointer;
      transition: all 0.2s ease;
    }
    .card:hover {
      transform: translateY(-4px);
      box-shadow: 0 8px 16px rgba(0,0,0,0.15);
    }
    .card h2 { color: #ff6347; margin-top: 5px; }
    img { border-radius: 8px; }
    ul { list-style: none; padding: 0; color: #666; font-size: 14px; text-align: left; }
    li { margin-bottom: 5px; }
  </style>
</head>
<body>
  
  <!-- ヘッダー -->
  <header>
    <h1>🌿 わたしのオリジナル図鑑 🐛</h1>
    <p>見つけた草花や虫を記録しよう！</p>
  </header>

  <!-- 追加フォーム -->
  <div class="add-form">
    <h2>🐾 生き物を追加する</h2>
    <input id="input-name"  type="text" placeholder="名前（例：タンポポ）">
    <input id="input-place" type="text" placeholder="場所（例：公園）">
    <input id="input-date"  type="text" placeholder="日付（例：3月5日）">
    <input id="input-memo"  type="text" placeholder="メモ（例：黄色くてかわいい花）">
    <button onclick="addIkimono()">追加する！</button>
  </div>

  <!-- 図鑑タイル表示エリア -->
  <div id="zukan-container" class="zukan-container"></div>

  <script>
    // 最初から表示するデータ
    let zukanData = [
      {
        name: "アサガオ",
        image: "https://placehold.jp/240x180.png?text=アサガオ",
        description: "夏にきれいに咲く花です。",
        place: "学校の花壇",
        date: "7月20日"
      },
      {
        name: "カブトムシ",
        image: "https://placehold.jp/240x180.png?text=カブトムシ",
        description: "かっこいいツノがある夏の虫です。",
        place: "近くの森",
        date: "8月5日"
      },
      {
        name: "タンポポ",
        image: "https://placehold.jp/240x180.png?text=タンポポ",
        description: "春に黄色いかわいい花を咲かせます。",
        place: "公園",
        date: "4月10日"
      }
    ];

    let container = document.getElementById("zukan-container");

    // カードを1つ画面に追加する関数
    function renderCard(ikimono) {
      let cardHTML = `
        <div class="card" onclick="showDetail('${ikimono.name}', '${ikimono.description}', '${ikimono.place}', '${ikimono.date}')">
          <h2>${ikimono.name}</h2>
          <img src="${ikimono.image}" alt="${ikimono.name}の写真" width="200">
          <p>${ikimono.description}</p>
          <ul>
            <li>📍 場所：${ikimono.place}</li>
            <li>📅 日付：${ikimono.date}</li>
          </ul>
        </div>
      `;
      container.innerHTML += cardHTML;
    }

    // カードをクリックしたらくわしい情報を見せる
    function showDetail(name, desc, place, date) {
      alert(`【${name}】\n\n📝 ${desc}\n📍 場所：${place}\n📅 日付：${date}`);
    }

    // 最初のリストを全部表示する
    zukanData.forEach(renderCard);

    // フォームから新しい生き物を追加する関数
    function addIkimono() {
      let name  = document.getElementById("input-name").value;
      let place = document.getElementById("input-place").value;
      let date  = document.getElementById("input-date").value;
      let memo  = document.getElementById("input-memo").value;
      
      if (name === "") {
        alert("名前を入力してください！");
        return;
      }

      let newIkimono = {
        name: name,
        image: "https://placehold.jp/240x180.png?text=" + encodeURIComponent(name),
        description: memo || "（メモなし）",
        place: place || "（場所なし）",
        date: date || "（日付なし）"
      };

      zukanData.push(newIkimono);
      renderCard(newIkimono);

      // フォームをリセット
      document.getElementById("input-name").value  = "";
      document.getElementById("input-place").value = "";
      document.getElementById("input-date").value  = "";
      document.getElementById("input-memo").value  = "";

      alert(`「${name}」を図鑑に追加したよ！🎉`);
    }
  </script>

</body>
</html>
```

## まとめ：全12回で学んだこと 💡

| 回 | テーマ | 学んだこと |
|---|---|---|
| 第1回 | HTMLの基本 | `<html>`, `<head>`, `<body>`, `<h1>` |
| 第2回 | テキスト表現 | `<p>`, `<ul>`, `<li>`, `<h2>` |
| 第3回 | CSSで色付け | `color`, `background-color`, `<style>` |
| 第4回 | 画像の表示 | `<img>`, `src`, `alt`, `width` |
| 第5回 | タイルレイアウト | `<div>`, `class`, `display: flex` |
| 第6回 | デザインの仕上げ | `border-radius`, `box-shadow`, `text-align` |
| 第7回 | JSの基本 | `<script>`, `console.log`, `let` |
| 第8回 | クリックイベント | `onclick`, `alert()`, `cursor: pointer` |
| 第9回 | データ管理 | オブジェクト `{}`, 配列 `[]` |
| 第10回 | DOM操作 | `getElementById`, `forEach`, `innerHTML` |
| 第11回 | フォーム入力 | `<input>`, `<button>`, `function`, `.value` |
| 第12回 | 総仕上げ | 全機能の統合とカスタマイズ |

## カスタマイズのアイデア 🌟
- タイトルや配色を自分の好みに変えてみよう！
- テキストの代わりに自分で撮影した草花や虫の写真を入れてみよう！（`img` の `src` を写真のパスに変えれば OK！）
- 図鑑のジャンルを変えてみよう！（おかし図鑑、雲図鑑、電車図鑑…なんでも OK！）

## よくできました！ 🎊
あなたは全12回で立派な図鑑Webサービスを作りました。
HTML・CSS・JavaScriptを使って、データを入力・表示できる本格的なWebアプリです。
おめでとう！！

## 理解度チェック ✅
1. 配列の末尾に新しいデータを追加するメソッドは何ですか？（ヒント：`zukanData.???`）
2. HTML・CSS・JavaScriptはそれぞれ「何を担当するか」を説明できますか？
