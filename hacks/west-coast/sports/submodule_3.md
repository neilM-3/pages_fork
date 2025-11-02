---
layout: opencs
title: "San Francisco"
description: "Submodule 3 of Backend Development Mini-Quest"
permalink: /west-coast/backend/submodule_3/
parent: "Backend Development"
team: "Zombies"
submodule: 3
categories: [CSP, Submodule, Backend]
tags: [backend, submodule, zombies]
author: "Zombies Team"
date: 2025-10-21
microblog: True
footer:
  previous: /west-coast/backend/submodule_2/
  home: /west-coast/sports/
  next: /west-coast/backend/submodule_4/
---
 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>San Francisco - Making API Calls</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f5f5f5;
            color: #333;
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
        }

        .header {
            background: linear-gradient(135deg, #AA0000 0%, #B3995D 100%);
            color: white;
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(170, 0, 0, 0.2);
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .section {
            background: white;
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .section h2 {
            color: #AA0000;
            margin-bottom: 20px;
            font-size: 1.8em;
            border-bottom: 3px solid #B3995D;
            padding-bottom: 10px;
        }

        .explanation {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            border-left: 5px solid #B3995D;
            margin: 20px 0;
            font-size: 1.1em;
            line-height: 1.8;
        }

        .step-box {
            background: white;
            border: 3px solid #B3995D;
            padding: 25px;
            border-radius: 10px;
            margin: 20px 0;
        }

        .step-number {
            background: #AA0000;
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5em;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .code-box {
            background: #2c3e50;
            color: #00ff00;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            margin: 15px 0;
            overflow-x: auto;
            font-size: 1em;
        }

        .highlight-box {
            background: #fff3cd;
            border: 2px solid #ffc107;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }

        .highlight-box strong {
            color: #AA0000;
            font-size: 1.1em;
        }

        .btn {
            background: linear-gradient(135deg, #AA0000 0%, #B3995D 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1.1em;
            transition: all 0.3s;
            display: inline-block;
            margin: 10px 5px;
        }

        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(170, 0, 0, 0.3);
        }

        .quiz-section {
            background: white;
            padding: 30px;
            border-radius: 15px;
            margin-top: 30px;
            border: 3px solid #B3995D;
        }

        .quiz-section h2 {
            color: #AA0000;
            text-align: center;
            margin-bottom: 30px;
            font-size: 2em;
        }

        .quiz-question {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 25px;
            display: none;
        }

        .quiz-question.active {
            display: block;
        }

        .question-text {
            color: #333;
            font-size: 1.3em;
            margin-bottom: 20px;
            font-weight: bold;
        }

        .quiz-option {
            background: white;
            padding: 15px 20px;
            border-radius: 8px;
            border: 2px solid #dee2e6;
            cursor: pointer;
            margin: 10px 0;
            transition: all 0.3s;
            font-size: 1.1em;
        }

        .quiz-option:hover {
            border-color: #B3995D;
            background: #fff9e6;
        }

        .quiz-option.correct {
            border-color: #28a745;
            background: #d4edda;
            color: #155724;
            font-weight: bold;
        }

        .quiz-option.incorrect {
            border-color: #dc3545;
            background: #f8d7da;
            color: #721c24;
        }

        .quiz-option.disabled {
            pointer-events: none;
            opacity: 0.7;
        }

        .feedback {
            margin-top: 15px;
            padding: 15px;
            border-radius: 8px;
            font-weight: bold;
            display: none;
        }

        .feedback.show {
            display: block;
        }

        .feedback.correct {
            background: #d4edda;
            color: #155724;
            border: 2px solid #28a745;
        }

        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 2px solid #dc3545;
        }

        .next-btn {
            background: #B3995D;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 15px;
            display: none;
        }

        .next-btn.show {
            display: inline-block;
        }

        .next-btn:hover {
            background: #9d864f;
        }

        .quiz-results {
            text-align: center;
            padding: 30px;
            display: none;
        }

        .quiz-results.show {
            display: block;
        }

        .score {
            font-size: 3em;
            color: #AA0000;
            font-weight: bold;
            margin: 20px 0;
        }

        .restart-btn {
            background: #B3995D;
            padding: 15px 40px;
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1.1em;
            margin-top: 20px;
        }

        .restart-btn:hover {
            background: #9d864f;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏟️ San Francisco: API Calls</h1>
            <p>Learn the 3 Simple Steps to Get Data from the Internet</p>
        </div>

        <div class="section">
            <h2>What is an API?</h2>
            <div class="explanation">
                <strong>API = Application Programming Interface</strong><br><br>
                Think of it like ordering food at a restaurant:
                <ul style="margin-top: 10px; margin-left: 20px;">
                    <li>🍽️ <strong>You</strong> = Your app/website</li>
                    <li>👨‍🍳 <strong>Kitchen</strong> = The server with data</li>
                    <li>🧑‍💼 <strong>Waiter</strong> = The API (takes your order to the kitchen and brings back food)</li>
                </ul>
            </div>

            <div class="highlight-box">
                <strong>Real Example:</strong> When you check sports scores on your phone, the app uses an API to ask a server "What's the score of the Warriors game?" and the server sends back the answer!
            </div>
        </div>

        <div class="section">
            <h2>The 3 Steps to Make an API Call</h2>
            
            <div class="step-box">
                <div class="step-number">1</div>
                <h3 style="color: #AA0000; margin-bottom: 15px;">Get Permission (API Key)</h3>
                <p style="margin-bottom: 15px;">Just like you need a ticket to enter a stadium, you need an API key to access data.</p>
                <div class="code-box">API Key: sf_abc123xyz789</div>
                <p style="margin-top: 10px; color: #666; font-style: italic;">This proves you're allowed to get the data</p>
            </div>

            <div class="step-box">
                <div class="step-number">2</div>
                <h3 style="color: #AA0000; margin-bottom: 15px;">Build Your Request (URL)</h3>
                <p style="margin-bottom: 15px;">Tell the computer exactly what data you want by building a special web address (URL).</p>
                <div class="code-box">https://api.example.com/stadium?name=chase_center&key=abc123</div>
                <p style="margin-top: 10px; color: #666;">
                    <strong>This URL has 3 parts:</strong><br>
                    • <strong>Base URL:</strong> Where to look<br>
                    • <strong>Endpoint:</strong> What you want (stadium info)<br>
                    • <strong>Parameters:</strong> Details (which stadium + your key)
                </p>
            </div>

            <div class="step-box">
                <div class="step-number">3</div>
                <h3 style="color: #AA0000; margin-bottom: 15px;">Get the Response (JSON Data)</h3>
                <p style="margin-bottom: 15px;">The server sends back data in JSON format - a way computers share information.</p>
                <div class="code-box">{
  "name": "Chase Center",
  "team": "Golden State Warriors",
  "capacity": 18064,
  "opened": 2019
}</div>
                <p style="margin-top: 10px; color: #666; font-style: italic;">Your app can now display this data to users!</p>
            </div>
        </div>

        <div class="section">
            <h2>🎮 Try It Yourself!</h2>
            <div class="explanation">
                Click the button below to see a simulated API call in action. Watch how the three steps work together!
            </div>
            
            <button class="btn" onclick="runDemo()">🚀 Make an API Call</button>
            
            <div id="demoOutput" style="margin-top: 20px;"></div>
        </div>

        <div class="section" style="background: linear-gradient(135deg, #AA0000 0%, #B3995D 100%); color: white;">
            <h2 style="color: white; border-bottom: 3px solid white;">🎯 Remember This!</h2>
            <div style="font-size: 1.2em; line-height: 1.8;">
                Every time an app shows you live data (weather, sports scores, social media posts), it's making API calls using these same 3 steps:
                <br><br>
                <strong>1. Permission (API Key)</strong> → <strong>2. Request (URL)</strong> → <strong>3. Response (JSON)</strong>
            </div>
        </div>

        <div class="quiz-section">
            <h2>🎯 Test Your Knowledge</h2>
            
            <div class="quiz-question active" id="q1">
                <div class="question-text">Question 1: What is an API key used for?</div>
                <div class="quiz-option" onclick="checkAnswer(1, 0, false)">
                    A) To make your computer faster
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 1, true)">
                    B) To prove you have permission to access data
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 2, false)">
                    C) To store passwords
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 3, false)">
                    D) To create websites
                </div>
                <div class="feedback" id="feedback1"></div>
                <button class="next-btn" id="next1" onclick="nextQuestion(2)">Next Question →</button>
            </div>

            <div class="quiz-question" id="q2">
                <div class="question-text">Question 2: What are the 3 steps of making an API call in order?</div>
                <div class="quiz-option" onclick="checkAnswer(2, 0, false)">
                    A) Response → Request → Key
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 1, true)">
                    B) Key → Request → Response
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 2, false)">
                    C) Request → Key → Response
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 3, false)">
                    D) Key → Response → Request
                </div>
                <div class="feedback" id="feedback2"></div>
                <button class="next-btn" id="next2" onclick="nextQuestion(3)">Next Question →</button>
            </div>

            <div class="quiz-question" id="q3">
                <div class="question-text">Question 3: What format does an API usually send data back in?</div>
                <div class="quiz-option" onclick="checkAnswer(3, 0, false)">
                    A) PDF
                </div>
                <div class="quiz-option" onclick="checkAnswer(3, 1, true)">
                    B) JSON
                </div>
                <div class="quiz-option" onclick="checkAnswer(3, 2, false)">
                    C) MP3
                </div>
                <div class="quiz-option" onclick="checkAnswer(3, 3, false)">
                    D) JPG
                </div>
                <div class="feedback" id="feedback3"></div>
                <button class="next-btn" id="next3" onclick="showResults()">See Results →</button>
            </div>

            <div class="quiz-results" id="results">
                <h3 style="color: #AA0000; font-size: 2em;">🎉 Quiz Complete!</h3>
                <div class="score" id="finalScore">0/3</div>
                <p id="scoreMessage" style="font-size: 1.2em; color: #666;"></p>
                <button class="restart-btn" onclick="restartQuiz()">🔄 Try Again</button>
            </div>
        </div>
    </div>

    <script>
        let score = 0;
        let currentQuestion = 1;

        function runDemo() {
            const output = document.getElementById('demoOutput');
            output.innerHTML = '<div style="background: #f8f9fa; padding: 20px; border-radius: 10px; border-left: 5px solid #B3995D;">';
            
            setTimeout(() => {
                output.innerHTML += '<p style="color: #AA0000; font-weight: bold; margin: 10px 0;">✓ Step 1: Got API Key: sf_demo123</p>';
            }, 500);
            
            setTimeout(() => {
                output.innerHTML += '<p style="color: #AA0000; font-weight: bold; margin: 10px 0;">✓ Step 2: Built URL: https://api.example.com/stadium?name=chase_center&key=sf_demo123</p>';
            }, 1500);
            
            setTimeout(() => {
                output.innerHTML += '<p style="color: #AA0000; font-weight: bold; margin: 10px 0;">✓ Step 3: Received Response:</p>';
                output.innerHTML += '<div class="code-box" style="margin-top: 10px;">{\n  "name": "Chase Center",\n  "team": "Warriors",\n  "capacity": 18064\n}</div>';
                output.innerHTML += '<p style="color: #28a745; font-weight: bold; margin-top: 15px; font-size: 1.2em;">✅ Success! Data retrieved!</p></div>';
            }, 2500);
        }

        function checkAnswer(questionNum, optionIndex, isCorrect) {
            const question = document.getElementById(`q${questionNum}`);
            const options = question.querySelectorAll('.quiz-option');
            const feedback = document.getElementById(`feedback${questionNum}`);
            const nextBtn = document.getElementById(`next${questionNum}`);
            
            options.forEach(opt => opt.classList.add('disabled'));
            
            if (isCorrect) {
                options[optionIndex].classList.add('correct');
                feedback.className = 'feedback correct show';
                feedback.textContent = '✅ Correct! Great job!';
                score++;
            } else {
                options[optionIndex].classList.add('incorrect');
                feedback.className = 'feedback incorrect show';
                feedback.textContent = '❌ Not quite. Try reviewing the lesson above!';
                
                options.forEach((opt, idx) => {
                    if (opt.textContent.includes('B)')) {
                        opt.classList.add('correct');
                    }
                });
            }
            
            nextBtn.classList.add('show');
        }

        function nextQuestion(nextNum) {
            document.getElementById(`q${currentQuestion}`).classList.remove('active');
            document.getElementById(`q${nextNum}`).classList.add('active');
            currentQuestion = nextNum;
        }

        function showResults() {
            document.getElementById('q3').classList.remove('active');
            document.getElementById('results').classList.add('show');
            document.getElementById('finalScore').textContent = `${score}/3`;
            
            const message = document.getElementById('scoreMessage');
            if (score === 3) {
                message.textContent = '🌟 Perfect! You understand APIs!';
                message.style.color = '#28a745';
            } else if (score === 2) {
                message.textContent = '👍 Good job! Review the lesson to master it.';
                message.style.color = '#ffc107';
            } else {
                message.textContent = '📚 Keep learning! Try reading through the lesson again.';
                message.style.color = '#dc3545';
            }
        }

        function restartQuiz() {
            score = 0;
            currentQuestion = 1;
            
            document.querySelectorAll('.quiz-question').forEach(q => {
                q.classList.remove('active');
                const options = q.querySelectorAll('.quiz-option');
                options.forEach(opt => {
                    opt.classList.remove('correct', 'incorrect', 'disabled');
                });
                q.querySelector('.feedback').classList.remove('show');
                q.querySelector('.next-btn').classList.remove('show');
            });
            
            document.getElementById('q1').classList.add('active');
            document.getElementById('results').classList.remove('show');
        }
    </script>
</body>
</html>