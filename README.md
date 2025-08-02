# flashcardQuizApp
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Flashcard Quiz App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      text-align: center;
      padding: 20px;
    }

    h2 {
      color: #333;
    }

    .card {
      background: white;
      padding: 20px;
      margin: 20px auto;
      border-radius: 10px;
      width: 300px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    .card p {
      font-size: 18px;
      color: #555;
    }

    button {
      margin: 10px 5px;
      padding: 10px 15px;
      border-radius: 5px;
      border: none;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    input {
      margin: 5px;
      padding: 10px;
      width: 250px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .controls {
      margin-bottom: 20px;
    }
  </style>
</head>
<body>
  <h2>Flashcard Quiz App</h2>

  <div class="card">
    <p id="flashcardText">Loading...</p>
    <button onclick="toggleAnswer()">Show Answer</button>
  </div>

  <div class="controls">
    <button onclick="prevCard()">Previous</button>
    <button onclick="nextCard()">Next</button>
  </div>

  <h3>Add New Flashcard</h3>
  <input type="text" id="newQuestion" placeholder="Enter question">
  <input type="text" id="newAnswer" placeholder="Enter answer">
  <button onclick="addCard()">Add Flashcard</button>

  <script>
    let flashcards = [
      { question: "Capital of India?", answer: "New Delhi" },
      { question: "2 + 2 = ?", answer: "4" },
      { question: "HTML stands for?", answer: "HyperText Markup Language" }
    ];

    let current = 0;
    let showAnswer = false;

    function displayCard() {
      const cardText = showAnswer
        ? flashcards[current].answer
        : flashcards[current].question;
      document.getElementById("flashcardText").textContent = cardText;
    }

    function toggleAnswer() {
      showAnswer = !showAnswer;
      displayCard();
    }

    function nextCard() {
      current = (current + 1) % flashcards.length;
      showAnswer = false;
      displayCard();
    }

    function prevCard() {
      current = (current - 1 + flashcards.length) % flashcards.length;
      showAnswer = false;
      displayCard();
    }

    function addCard() {
      const question = document.getElementById("newQuestion").value.trim();
      const answer = document.getElementById("newAnswer").value.trim();

      if (question && answer) {
        flashcards.push({ question, answer });
        alert("Flashcard added!");
        document.getElementById("newQuestion").value = "";
        document.getElementById("newAnswer").value = "";
      } else {
        alert("Please enter both question and answer.");
      }
    }

    window.onload = displayCard;
  </script>
</body>
</html>
