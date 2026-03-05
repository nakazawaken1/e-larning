# 第10回：データから図鑑のタイルを作ろう！

## 今日のゴール 🎯
JavaScriptのデータを使って、HTMLのタイルを自動で生成する！

## 学ぶこと 📚
- 配列のすべてのデータを処理する `forEach()`
- JavaScriptでHTMLを作る `innerHTML`

## やってみよう！ 💻

### ステップ1：HTMLの生き物カードを全部消そう
今まで `<body>` の中に直接書いていた生き物カード（`<div class="card">...</div>`）を全部消して、代わりに空の入れ物だけを残します。

```html
<body>
  <h1>わたしの図鑑</h1>
  
  <!-- この中はJavaScriptが自動で作ってくれる！ -->
  <div id="zukan-container" class="zukan-container">
  </div>

</body>
```

### ステップ2：JavaScriptでカードを自動生成しよう
`<script>` タグの中に、データを1件ずつ読み取って、HTMLを作る命令を書きます。

```javascript
<script>
  // 生き物のデータ（前回と同じ）
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
    }
  ];

  // 入れ物のタグを id を使って取得する
  let container = document.getElementById("zukan-container");

  // zukanData の全てのデータを1つずつ取り出して処理する
  zukanData.forEach(function(ikimono) {
    // カードのHTMLを作る
    let cardHTML = `
      <div class="card" onclick="alert('${ikimono.name}だよ！')">
        <h2>${ikimono.name}</h2>
        <img src="${ikimono.image}" alt="${ikimono.name}の写真" width="200">
        <p>${ikimono.description}</p>
        <ul>
          <li>📍 場所：${ikimono.place}</li>
          <li>📅 日付：${ikimono.date}</li>
        </ul>
      </div>
    `;
    // 入れ物の中に追加する
    container.innerHTML += cardHTML;
  });
</script>
```

### ステップ3：ブラウザで確認しよう
ブラウザを更新して、タイルが同じように表示されるか確認しよう！

## 今日のポイント 💡
- `document.getElementById("名前")` → `id="名前"` がついたHTML要素を取得します。
- `.forEach(function(item) { ... })` → 配列の中のデータを1つずつ取り出して、`{ }` の中の処理を繰り返します。
- バッククォート `` ` `` →「テンプレートリテラル」と言い、`${ }` を使って変数の内容を簡単に文字列の中に入れられます。

## チャレンジ問題 🌟
`zukanData` の配列に3つ目の生き物のオブジェクトを追加してみよう！
HTMLを変えなくても、タイルが自動で増えるはずだよ。

## 今日のアウトプット ✅
- [ ] HTMLのカードを消して、空の `<div>` だけにした
- [ ] JavaScriptで自動的にカードを生成できた

## 理解度チェック ✅
1. `id="zukan-container"` の要素をJavaScriptで取得するコードは何ですか？
2. 配列のデータを1件ずつ取り出して繰り返す命令は何ですか？
