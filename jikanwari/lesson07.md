# 第7回：教科を選ぼう！選択リストを作る

## 今日のゴール 🎯
クリックで教科一覧から選択できる時間割を作る！

## 学ぶこと 📚
- セレクトボックス（ドロップダウン）の作り方
- 教科リストの管理
- より使いやすい入力方法

## やってみよう！ 💻

### ステップ1：教科リストを作ろう
`<script>` の最初に教科リストを追加：

```javascript
// 教科リスト
const subjects = [
  '',
  '国語',
  '算数',
  '理科',
  '社会',
  '英語',
  '音楽',
  '図工',
  '体育',
  '道徳',
  '総合',
  '学活'
];
```

### ステップ2：選択リストを表示する関数を作ろう

```javascript
// 選択リストを作る関数
function createSelect(cell) {
  // セレクト要素を作成
  const select = document.createElement('select');
  
  // 選択肢を追加
  subjects.forEach(function(subject) {
    const option = document.createElement('option');
    option.value = subject;
    option.textContent = subject || '選択してください';
    
    // 現在の値を選択状態にする
    if (cell.textContent === subject) {
      option.selected = true;
    }
    
    select.appendChild(option);
  });
  
  // 選択が変わった時の処理
  select.onchange = function() {
    cell.textContent = select.value;
  };
  
  // フォーカスが外れたら元に戻す
  select.onblur = function() {
    cell.textContent = select.value;
  };
  
  return select;
}
```

### ステップ3：クリック時に選択リストを表示

```javascript
// すべての td 要素を取得
const cells = document.querySelectorAll('td');

cells.forEach(function(cell) {
  cell.onclick = function() {
    // 既存の内容を保存
    const currentText = cell.textContent;
    
    // セレクトを作成して表示
    cell.textContent = '';
    const select = createSelect(cell);
    cell.appendChild(select);
    select.focus();
  };
});
```

## 今日のポイント 💡
- `createElement` → 新しいHTML要素を作る
- `appendChild` → 子要素として追加する
- `onchange` → 値が変わった時のイベント
- `onblur` → フォーカスが外れた時のイベント
- `focus()` → その要素にフォーカスを当てる

## チャレンジ問題 🌟
1. 教科リストに自分の学校の教科を追加してみよう
2. 選択リストのデザインをCSSで変えてみよう

## 今日のアウトプット ✅
- [ ] マスをクリックすると選択リストが出る
- [ ] 教科を選ぶとマスに表示される
- [ ] 別の場所をクリックすると選択リストが消える

## 理解度チェック ✅
1. 新しいHTML要素を作るJavaScriptの命令はどれですか？
2. 作成した要素を、別の要素の中に追加する命令はどれですか？
3. セレクトボックスの値が変わった時に発生するイベントはどれですか？
4. 要素からフォーカスが外れた時に発生するイベントはどれですか？
5. セレクトボックスの選択肢の一つ一つを表すHTMLタグはどれですか？
