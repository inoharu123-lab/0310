<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🐼パンダクイズ🐼</title>
<style>
  body {
    font-family: "Comic Sans MS", "Arial", sans-serif;
    background-color: #fff8f0;
    text-align: center;
    padding: 30px;
  }
  .quiz-box {
    background-color: #fff;
    border-radius: 20px;
    padding: 25px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    max-width: 500px;
    margin: 0 auto;
  }
  h1 {
    color: #444;
  }
  .question {
    font-size: 1.2em;
    margin: 20px 0;
  }
  .options button {
    display: block;
    width: 100%;
    margin: 8px 0;
    padding: 10px;
    border: none;
    border-radius: 12px;
    background-color: #ffd6e0;
    cursor: pointer;
    transition: background-color 0.3s;
    font-size: 1em;
  }
  .options button:hover {
    background-color: #ffc1d1;
  }
  #result {
    font-size: 1.3em;
    margin-top: 25px;
    font-weight: bold;
  }
  .restart {
    margin-top: 15px;
    padding: 10px 20px;
    background-color: #b4e0b4;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    font-size: 1em;
  }
  .restart:hover {
    background-color: #9cd69c;
  }
</style>
</head>
<body>

<div class="quiz-box">
  <h1>🐼 パンダクイズ 🐼</h1>
  <div id="quiz"></div>
  <div id="result"></div>
</div>

<script>
const quizData = [
  {
    question: "パンダの主な食べ物はどれ？",
    options: ["竹", "りんご", "魚", "草"],
    answer: 0
  },
  {
    question: "パンダの体の色は？",
    options: ["黒と白", "茶色", "灰色", "白だけ"],
    answer: 0
  },
  {
    question: "パンダの生息地はどこ？",
    options: ["中国", "日本", "インド", "ロシア"],
    answer: 0
  }
];

let current = 0;
let score = 0;

const quizEl = document.getElementById("quiz");
const resultEl = document.getElementById("result");

function showQuestion() {
  if (current < quizData.length) {
    const q = quizData[current];
    quizEl.innerHTML = `
      <div class="question">${q.question}</div>
      <div class="options">
        ${q.options.map((opt, i) => 
          `<button onclick="checkAnswer(${i})">${opt}</button>`
        ).join("")}
      </div>
    `;
    resultEl.textContent = "";
  } else {
    quizEl.innerHTML = "";
    resultEl.innerHTML = `🎉 結果：${quizData.length}問中 ${score}問正解！ 🎉<br>
      <button class="restart" onclick="restartQuiz()">もう一度やる</button>`;
  }
}

function checkAnswer(selected) {
  if (selected === quizData[current].answer) {
    score++;
  }
  current++;
  showQuestion();
}

function restartQuiz() {
  current = 0;
  score = 0;
  showQuestion();
}

showQuestion();
</script>

</body>
</html>
