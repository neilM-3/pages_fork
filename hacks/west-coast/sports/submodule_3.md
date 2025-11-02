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
    <title>San Francisco - Step 3: Send Request & Get Response</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            min-height: 100vh;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #002D62 0%, #A2AAAD 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.2em;
            margin-bottom: 10px;
        }

        .header p {
            opacity: 0.9;
            font-size: 1.1em;
        }

        .concept-box {
            background: #ffffff;
            padding: 25px;
            border-left: 5px solid #FFC425;
            margin: 25px;
            border-radius: 8px;
        }

        .concept-box h2 {
            color: #002D62 !important;
            margin-bottom: 10px;
            font-weight: 600;
        }

        .concept-box p {
            color: #000000 !important;
            line-height: 1.6;
            font-weight: 500;
        }

        .concept-box strong {
            color: #000000 !important;
        }

        .step-section {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #002D62;
        }

        .step-section h2 {
            color: #002D62 !important;
            margin-bottom: 25px;
            font-size: 1.8em;
            text-align: center;
        }

        .step-section > p {
            color: #000000 !important;
            line-height: 1.8;
            margin-bottom: 15px;
            text-align: center;
        }

        .two-parts {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .part-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 12px;
            border: 2px solid #dee2e6;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .part-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 45, 98, 0.15);
        }

        .part-card h3 {
            color: #002D62 !important;
            margin-bottom: 15px;
            font-size: 1.4em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .part-icon {
            font-size: 1.5em;
        }

        .part-card p {
            color: #495057 !important;
            line-height: 1.8;
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
            font-size: 0.95em;
        }

        .status-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .status-card {
            background: white;
            padding: 15px;
            border-radius: 8px;
            border: 2px solid #dee2e6;
            text-align: center;
            transition: all 0.3s;
        }

        .status-card:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .status-200 {
            border-color: #28a745;
            background: linear-gradient(135deg, #d4edda 0%, #c3e6cb 100%);
        }

        .status-404 {
            border-color: #ffc107;
            background: linear-gradient(135deg, #fff3cd 0%, #ffeaa7 100%);
        }

        .status-401 {
            border-color: #dc3545;
            background: linear-gradient(135deg, #f8d7da 0%, #f5c6cb 100%);
        }

        .status-card h4 {
            font-size: 1.8em;
            margin-bottom: 8px;
        }

        .status-200 h4 {
            color: #28a745;
        }

        .status-404 h4 {
            color: #856404;
        }

        .status-401 h4 {
            color: #721c24;
        }

        .status-card p {
            color: #495057 !important;
            font-size: 0.9em;
        }

        .interactive-demo {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #FFC425;
        }

        .interactive-demo h2 {
            color: #002D62 !important;
            text-align: center;
            margin-bottom: 15px;
            font-size: 1.8em;
        }

        .demo-description {
            text-align: center;
            color: #495057 !important;
            margin-bottom: 25px;
            font-size: 1.05em;
        }

        .stadium-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 25px 0;
        }

        .stadium-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 12px;
            border: 2px solid #dee2e6;
            text-align: center;
            transition: all 0.3s;
        }

        .stadium-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 45, 98, 0.15);
            border-color: #FFC425;
        }

        .stadium-card h3 {
            color: #002D62 !important;
            margin-bottom: 10px;
            font-size: 1.2em;
        }

        .stadium-card p {
            color: #495057 !important;
            font-size: 0.9em;
            margin-bottom: 15px;
        }

        .api-code {
            background: #2c3e50;
            color: #00ff00;
            padding: 10px;
            border-radius: 6px;
            font-family: 'Courier New', monospace;
            font-size: 0.85em;
            margin: 10px 0;
            word-break: break-all;
        }

        .code-input-section {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 10px;
            margin: 25px 0;
            border: 2px solid #FFC425;
        }

        .code-input-section h3 {
            color: #002D62 !important;
            margin-bottom: 15px;
            text-align: center;
        }

        .code-input-section > p {
            color: #495057 !important;
        }

        .input-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }

        .code-input {
            flex: 1;
            padding: 15px;
            border: 2px solid #dee2e6;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 1em;
            transition: border-color 0.3s;
        }

        .code-input:focus {
            outline: none;
            border-color: #FFC425;
        }

        .fetch-btn {
            background: linear-gradient(135deg, #002D62 0%, #FFC425 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            white-space: nowrap;
        }

        .fetch-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 45, 98, 0.3);
        }

        .response-output {
            background: #2c3e50;
            color: #00ff00;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            margin-top: 15px;
            min-height: 100px;
            max-height: 400px;
            overflow-y: auto;
            white-space: pre-wrap;
        }

        .response-output.error {
            background: #e74c3c;
            color: white;
        }

        .response-output.success {
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .quiz-section {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #FFC425;
        }

        .quiz-section h2 {
            color: #002D62 !important;
            text-align: center;
            margin-bottom: 30px;
            font-size: 1.8em;
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
            color: #333 !important;
            font-size: 1.2em;
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
            font-size: 1.05em;
            color: #333 !important;
        }

        .quiz-option:hover {
            border-color: #FFC425;
            background: #fff9e6;
        }

        .quiz-option.correct {
            border-color: #28a745;
            background: #d4edda;
            color: #155724 !important;
            font-weight: bold;
        }

        .quiz-option.incorrect {
            border-color: #dc3545;
            background: #f8d7da;
            color: #721c24 !important;
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
            color: #155724 !important;
            border: 2px solid #28a745;
        }

        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24 !important;
            border: 2px solid #dc3545;
        }

        .next-btn {
            background: #FFC425;
            color: #002D62;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 15px;
            display: none;
            transition: all 0.3s;
        }

        .next-btn.show {
            display: inline-block;
        }

        .next-btn:hover {
            background: #ffb700;
            transform: translateY(-2px);
        }

        .quiz-results {
            text-align: center;
            padding: 30px;
            display: none;
        }

        .quiz-results.show {
            display: block;
        }

        .quiz-results h3 {
            color: #002D62 !important;
        }

        .score {
            font-size: 3em;
            color: #002D62;
            font-weight: bold;
            margin: 20px 0;
        }

        .restart-btn {
            background: linear-gradient(135deg, #002D62 0%, #FFC425 100%);
            padding: 15px 40px;
            color: white;
            border: none;
            border-radius: 10px;
            font-weight: bold;
            cursor: pointer;
            font-size: 1.1em;
            margin-top: 20px;
            transition: all 0.3s;
        }

        .restart-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 45, 98, 0.3);
        }

        .key-learning {
            background: linear-gradient(135deg, #002D62 0%, #FFC425 100%);
            color: white;
            padding: 25px;
            margin: 25px;
            border-radius: 12px;
            text-align: center;
        }

        .key-learning h3 {
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        .key-learning p {
            font-size: 1.05em;
            line-height: 1.6;
        }

        .remember-box {
            background: rgba(255, 255, 255, 0.2);
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }

        .remember-box ul {
            list-style: none;
            padding: 0;
        }

        .remember-box li {
            padding: 8px 0;
            font-size: 1.05em;
        }

        .remember-box li::before {
            content: "✓ ";
            font-weight: bold;
            margin-right: 8px;
        }

        #scoreMessage {
            color: #495057 !important;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🚀 Step 3: Send Request & Get Response</h1>
            <p>Where the Magic Happens - Talking to the Server</p>
        </div>

        <div class="concept-box">
            <h2>What is Step 3?</h2>
            <p>This is where you <strong>actually communicate</strong> with the server. You send your URL with code, and the server sends back an answer. Think of it like handing your order to a waiter and getting your food back!</p>
        </div>

        <div class="step-section">
            <h2>The Two Parts of Step 3</h2>
            <div class="two-parts">
                <div class="part-card">
                    <h3><span class="part-icon">📤</span> Part A: Send the Request</h3>
                    <p>Use code to send your URL to the server over the internet.</p>
                    <p><strong>Python Example:</strong></p>
                    <div class="code-box">response = requests.get("https://api.example.com/stadium")</div>
                    <p><strong>JavaScript Example:</strong></p>
                    <div class="code-box">fetch("https://api.example.com/stadium")</div>
                    <p style="margin-top: 15px; font-style: italic; color: #666;">This is like handing your written order to the waiter!</p>
                </div>

                <div class="part-card">
                    <h3><span class="part-icon">📥</span> Part B: Receive the Response</h3>
                    <p>The server sends back TWO things:</p>
                    <p><strong>1. Status Code</strong> - Did it work?</p>
                    <p><strong>2. The Data</strong> - Your requested information in JSON format</p>
                    <p style="margin-top: 15px; font-style: italic; color: #666;">This is like the waiter bringing your food or saying "Sorry, we're out!"</p>
                </div>
            </div>
        </div>

        <div class="step-section">
            <h2>Understanding Status Codes</h2>
            <p>The server always tells you if your request worked with a status code:</p>
            <div class="status-grid">
                <div class="status-card status-200">
                    <h4>200</h4>
                    <p><strong>✅ OK</strong></p>
                    <p>Success! Here's your data</p>
                </div>
                <div class="status-card status-404">
                    <h4>404</h4>
                    <p><strong>🤷 Not Found</strong></p>
                    <p>That data doesn't exist</p>
                </div>
                <div class="status-card status-401">
                    <h4>401</h4>
                    <p><strong>🔒 Unauthorized</strong></p>
                    <p>Wrong API key</p>
                </div>
            </div>
            <p style="color: #002D62; font-weight: bold; margin-top: 20px;">Always check the status code first! 200 = Success!</p>
        </div>

        <div class="interactive-demo">
            <h2>🏟️ Try It Yourself: NorCal Stadium API</h2>
            <p class="demo-description">Practice making API calls to get information about 5 major NorCal stadiums!</p>
            
            <div class="stadium-grid">
                <div class="stadium-card">
                    <h3>🏟️ Levi's Stadium</h3>
                    <p>San Francisco 49ers (NFL)</p>
                    <div class="api-code">levis</div>
                </div>
                <div class="stadium-card">
                    <h3>⚾ Oracle Park</h3>
                    <p>SF Giants (MLB)</p>
                    <div class="api-code">oracle</div>
                </div>
                <div class="stadium-card">
                    <h3>🏀 Chase Center</h3>
                    <p>Golden State Warriors (NBA)</p>
                    <div class="api-code">chase</div>
                </div>
                <div class="stadium-card">
                    <h3>⚾ Oakland Coliseum</h3>
                    <p>Oakland Athletics (MLB)</p>
                    <div class="api-code">coliseum</div>
                </div>
                <div class="stadium-card">
                    <h3>⚽ PayPal Park</h3>
                    <p>San Jose Earthquakes (MLS)</p>
                    <div class="api-code">paypal</div>
                </div>
            </div>

            <div class="code-input-section">
                <h3>📝 Enter Your API Call</h3>
                <p style="text-align: center; margin-bottom: 15px;">
                    Type the code format: <code style="background: #e9ecef; padding: 3px 8px; border-radius: 4px;">requests.get("stadium_code")</code>
                </p>
                <div class="input-row">
                    <input type="text" 
                           id="apiInput" 
                           class="code-input" 
                           placeholder='requests.get("levis")'
                           onkeypress="if(event.key === 'Enter') fetchStadium()">
                    <button class="fetch-btn" onclick="fetchStadium()">🚀 Send Request</button>
                </div>
                <p style="text-align: center; color: #666; font-size: 0.9em; margin-top: 10px;">
                    Example: Type <strong>requests.get("chase")</strong> to get Chase Center info
                </p>
            </div>

            <div id="apiResponse" class="response-output">Waiting for your API request...

Try typing: requests.get("levis") or requests.get("oracle")</div>
        </div>

        <div class="quiz-section">
            <h2>🎯 Test Your Knowledge</h2>
            
            <div class="quiz-question active" id="q1">
                <div class="question-text">Question 1: What are the TWO things the server sends back in Step 3?</div>
                <div class="quiz-option" onclick="checkAnswer(1, 0, false)">
                    A) Username and Password
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 1, true)">
                    B) Status Code and Data
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 2, false)">
                    C) Website URL and Images
                </div>
                <div class="quiz-option" onclick="checkAnswer(1, 3, false)">
                    D) API Key and Token
                </div>
                <div class="feedback" id="feedback1"></div>
                <button class="next-btn" id="next1" onclick="nextQuestion(2)">Next Question →</button>
            </div>

            <div class="quiz-question" id="q2">
                <div class="question-text">Question 2: What does a status code of 200 mean?</div>
                <div class="quiz-option" onclick="checkAnswer(2, 0, false)">
                    A) Error - data not found
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 1, false)">
                    C) Permission denied
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 2, true)">
                    B) Success - here's your data!
                </div>
                <div class="quiz-option" onclick="checkAnswer(2, 3, false)">
                    D) Server is down
                </div>
                <div class="feedback" id="feedback2"></div>
                <button class="next-btn" id="next2" onclick="showResults()">See Results →</button>
            </div>

            <div class="quiz-results" id="results">
                <h3 style="font-size: 2em;">🎉 Quiz Complete!</h3>
                <div class="score" id="finalScore">0/2</div>
                <p id="scoreMessage" style="font-size: 1.2em;"></p>
                <button class="restart-btn" onclick="restartQuiz()">🔄 Try Again</button>
            </div>
        </div>

        <div class="key-learning">
            <h3>🎯 Key Learning</h3>
            <p>Step 3 is where you actually talk to the server using code. You send your request with requests.get(), and the server responds with a status code (200 = success!) and your data in JSON format.</p>
            
            <div class="remember-box">
                <strong style="font-size: 1.2em; display: block; margin-bottom: 10px;">Remember:</strong>
                <ul>
                    <li>Use code like requests.get() to send your request</li>
                    <li>Always check the status code first</li>
                    <li>200 means success - you got your data!</li>
                    <li>Handle errors - don't assume it will always work</li>
                </ul>
            </div>
        </div>
    </div>

    <script>
        const stadiumData = {
            levis: {
                name: "Levi's Stadium",
                sport: "Football",
                team: "San Francisco 49ers",
                league: "NFL",
                capacity: 68500,
                location: "Santa Clara, CA",
                opened: 2014,
                surface: "Grass",
                superbowls_hosted: 1
            },
            oracle: {
                name: "Oracle Park",
                sport: "Baseball",
                team: "San Francisco Giants",
                league: "MLB",
                capacity: 41915,
                location: "San Francisco, CA",
                opened: 2000,
                surface: "Grass",
                world_series: 3
            },
            chase: {
                name: "Chase Center",
                sport: "Basketball",
                team: "Golden State Warriors",
                league: "NBA",
                capacity: 18064,
                location: "San Francisco, CA",
                opened: 2019,
                surface: "Hardwood",
                championships: 7
            },
            coliseum: {
                name: "Oakland Coliseum",
                sport: "Baseball",
                team: "Oakland Athletics",
                league: "MLB",
                capacity: 46847,
                location: "Oakland, CA",
                opened: 1966,
                surface: "Grass",
                world_series: 4
            },
            paypal: {
                name: "PayPal Park",
                sport: "Soccer",
                team: "San Jose Earthquakes",
                league: "MLS",
                capacity: 18000,
                location: "San Jose, CA",
                opened: 2015,
                surface: "Grass",
                mls_cups: 2
            }
        };

        function fetchStadium() {
            const input = document.getElementById('apiInput').value.trim();
            const output = document.getElementById('apiResponse');

            const match = input.match(/requests\.get\s*\(\s*["']([^"']+)["']\s*\)/);
            
            if (!match) {
                output.className = 'response-output error';
                output.textContent = '❌ ERROR: Invalid syntax!\n\nExpected format: requests.get("stadium_code")\n\nExample: requests.get("levis")';
                return;
            }

            const stadiumCode = match[1].toLowerCase();

            if (!stadiumData[stadiumCode]) {
                output.className = 'response-output error';
                output.textContent = `❌ Status Code: 404 Not Found\n\nError: Stadium "${stadiumCode}" not found in database.\n\nAvailable stadiums: levis, oracle, chase, coliseum, paypal`;
                return;
            }

            const response = {
                status: 200,
                statusText: "OK",
                message: "Success",
                data: stadiumData[stadiumCode],
                timestamp: new Date().toISOString()
            };

            output.className = 'response-output success';
            output.textContent = JSON.stringify(response, null, 2);
        }

        let score = 0;
        let currentQuestion = 1;

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
                feedback.textContent = '❌ Not quite. Review the lesson above!';
                
                options.forEach((opt) => {
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
            document.getElementById('q2').classList.remove('active');
            document.getElementById('results').classList.add('show');
            document.getElementById('finalScore