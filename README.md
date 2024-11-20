<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Matematika</title>
    <link rel="stylesheet" href="style.css"> <!-- Hubungkan file CSS -->
</head>
<body>
    <div class="container">
        <h1>Game Matematika Sederhana</h1>
        <p id="question">Berapakah 2 + 3?</p>
        <input type="number" id="answer" placeholder="Masukkan jawaban Anda">
        <button onclick="checkAnswer()">Submit</button>
        <p id="feedback"></p>
        <p>Skor: <span id="score">0</span></p>
    </div>
    <script src="script.js"></script> <!-- Hubungkan file JavaScript -->
</body>
</html>body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #f0f8ff;
    margin: 0;
    padding: 0;
}

.container {
    margin-top: 50px;
}

h1 {
    color: #333;
}

button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #4caf50;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

input {
    padding: 10px;
    font-size: 16px;
    margin: 10px 0;
}

#feedback {
    margin-top: 20px;
    font-weight: bold;
}let score = 0;

// Membuat soal acak
function generateQuestion() {
    const num1 = Math.floor(Math.random() * 10) + 1;
    const num2 = Math.floor(Math.random() * 10) + 1;
    const questionElement = document.getElementById("question");
    questionElement.textContent = `Berapakah ${num1} + ${num2}?`;
    return num1 + num2;
}

let correctAnswer = generateQuestion(); // Soal pertama

// Memeriksa jawaban pemain
function checkAnswer() {
    const userAnswer = parseInt(document.getElementById("answer").value);
    const feedbackElement = document.getElementById("feedback");
    if (userAnswer === correctAnswer) {
        feedbackElement.textContent = "Benar!";
        feedbackElement.style.color = "green";
        score++;
    } else {
        feedbackElement.textContent = `Salah! Jawaban yang benar adalah ${correctAnswer}`;
        feedbackElement.style.color = "red";
    }
    document.getElementById("score").textContent = score;
    correctAnswer = generateQuestion(); // Soal baru
    document.getElementById("answer").value = ""; // Kosongkan input
}
