# 第8回：問題をランダムに出そう

## 今日のゴール 🎯
毎回違う問題が出てくるように、リストの中からランダムに選ぶ機能を作る！

## 学ぶこと 📚
- コンピュータにサイコロを振らせる（`Math.random`）
- 数を整数にする（`Math.floor`）
- リストから1つ選ぶ方法

## やってみよう！ 💻

### ステップ1：ランダムな数字を選ぼう
```javascript
function setQuestion() {
  // 0 から (リストの長さ - 1) までの数字をランダムに作る
  const randomIndex = Math.floor(Math.random() * wordList.length);
  const nextWord = wordList[randomIndex];
  
  // 画面の問題文を書き換える
  document.getElementById('question').innerText = nextWord.english + " はなに？";
}
```

## 理解度チェック ✅
1. 0から1の間のバラバラな数字を作る命令は何ですか？
2. 小数点以下を切り捨てて整数にする命令は何ですか？
3. リスト全体の長さを知るためのプロパティは何ですか？
4. リストの「一番最初」のデータを取り出すときの番号は何番ですか？
5. 画面上の文字を書き換えるために使うプロパティは何ですか？ (例: `document.getElementById('id').???`)
