# Jjig
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Important Life Test</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #6a5cff, #8e7bff);
      font-family: Arial, sans-serif;
    }

    .quiz-box {
      background: #fff;
      width: 380px;
      padding: 25px;
      border-radius: 14px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      text-align: center;
    }

    .score {
      background: #f1f1f1;
      padding: 10px;
      border-radius: 20px;
      margin-bottom: 20px;
      font-weight: bold;
    }

    h2 {
      font-size: 18px;
      margin-bottom: 20px;
    }

    .option {
      border: 1px solid #ddd;
      padding: 12px;
      margin: 10px 0;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.2s;
    }

    .option:hover {
      background: #f3f3ff;
    }

    .option.correct {
      background: #4f7cff;
      color: white;
    }

    .option.wrong {
      background: #ff6b6b;
      color: white;
    }

    .next-btn {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background: #6a5cff;
      color: white;
      cursor: pointer;
      display: none;
    }
  </style>
</head>
<body>

  <div class="quiz-box">
    <div class="score" id="score">Score: 0/4</div>
    <h2 id="question"></h2>
    <div id="options"></div>
    <button class="next-btn" onclick="nextQuestion()">Next</button>
  </div>

<script>
  const quiz = [
    {
      question: "When did u first fell for me?",
      options: ["Oct 29", "Nov 26", "Sep 29", "I don't remember 😅"],
      answer: 2
    },
    {
      question: "What you like the most in me?",
      options: ["Eyes", "smile", "hands","Waist"],
      answer: 0
    },
    {
      question: "Who said 'I love you' first?",
      options: ["Me", "YouH", "Both", "No one"],
      answer: 1
    },
    {
      question: "Will you always stay with me?",
      options: ["Yes ❤️", "Forever 💍", "Obviously 😌", "Try me"],
      answer: 1
    }
{
      question: "Will you be my VALENTINE?",
      options: ["Yes ❤️", "a big yes", "obviously"],
      answer: 1
    }
  ];

  let current = 0;
  let score = 0;
  let answered = false;

  const questionEl = document.getElementById("question");
  const optionsEl = document.getElementById("options");
  const scoreEl = document.getElementById("score");
  const nextBtn = document.querySelector(".next-btn");

  function loadQuestion() {
    answered = false;
    nextBtn.style.display = "none";
    optionsEl.innerHTML = "";
    questionEl.innerText = quiz[current].question;

    quiz[current].options.forEach((opt, index) => {
      const div = document.createElement("div");
      div.className = "option";
      div.innerText = opt;
      div.onclick = () => selectOption(div, index);
      optionsEl.appendChild(div);
    });
  }

  function selectOption(element, index) {
    if (answered) return;
    answered = true;

    const correct = quiz[current].answer;
    const options = document.querySelectorAll(".option");

    if (index === correct) {
      element.classList.add("correct");
      score++;
    } else {
      element.classList.add("wrong");
      options[correct].classList.add("correct");
    }

    scoreEl.innerText = `Score: ${score}/${quiz.length}`;
    nextBtn.style.display = "block";
  }

  function nextQuestion() {
    current++;
    if (current < quiz.length) {
      loadQuestion();
    } else {
      questionEl.innerText = "Test Completed 💖";
      optionsEl.innerHTML = `<h3>Your Score: ${score}/${quiz.length}</h3>`;
      nextBtn.style.display = "none";
    }
  }

  loadQuestion();
</script>

</body>
</html>
