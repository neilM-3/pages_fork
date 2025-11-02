---
layout: opencs
title: "Los Angeles"
description: "Submodule 2 of Backend Development Mini-Quest"
permalink: /west-coast/backend/submodule_2/
parent: "Backend Development"
team: "Zombies"
submodule: 2
categories: [CSP, Submodule, Backend]
tags: [backend, submodule, zombies]
author: "Zombies Team"
date: 2025-10-21
microblog: True
footer:
  previous: /west-coast/backend/submodule_1/
  home: /west-coast/sports/
  next: /west-coast/backend/submodule_3/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LA Sports API URL Builder</title>
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
            color: #000000;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #005A9C 0%, #EF3E42 100%);
            color: #000000;
            padding: 40px 20px;
            text-align: center;
        }

        .header h1 {
            font-size: 3em;
            margin-bottom: 10px;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.5);
        }

        .dodgers-logo {
            font-size: 5em;
            margin: 20px 0;
        }

        .header p {
            font-size: 1.3em;
            opacity: 0.9;
        }

        .lesson-section {
            background: white;
            color: #000000;
            padding: 40px;
            margin: 25px;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #EF3E42;
        }

        .lesson-section h2 {
            color: #005A9C;
            font-size: 2em;
            margin-bottom: 20px;
            border-bottom: 4px solid #EF3E42;
            padding-bottom: 10px;
        }

        .lesson-section h3 {
            color: #005A9C;
        }

        .lesson-section p {
            font-size: 1.1em;
            line-height: 1.8;
            margin-bottom: 20px;
            color: #000000;
        }

        .url-parts {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .url-part {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 20px;
            border-radius: 15px;
            border-left: 5px solid #005A9C;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 2px solid #dee2e6;
        }

        .url-part:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 90, 156, 0.3);
        }

        .url-part h3 {
            color: #EF3E42;
            margin-bottom: 10px;
        }

        .url-part p {
            color: #000000;
        }

        .code-box {
            background: #1e1e1e;
            color: #4af626;
            padding: 15px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            margin: 10px 0;
            overflow-x: auto;
            white-space: pre-wrap;
            word-break: break-all;
            user-select: all;
            cursor: text;
        }

        .teams-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }

        .team-card {
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            transition: all 0.3s;
            border: 2px solid #dee2e6;
        }

        .team-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.3);
        }

        .team-icon {
            font-size: 4em;
            text-align: center;
            margin-bottom: 15px;
        }

        .team-name {
            font-size: 1.8em;
            font-weight: bold;
            color: #005A9C;
            text-align: center;
            margin-bottom: 10px;
        }

        .stadium-name {
            text-align: center;
            color: #000000;
            font-size: 1.1em;
            margin-bottom: 20px;
        }

        .team-url {
            background: #2c3e50;
            color: #00ff00;
            padding: 15px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 0.9em;
            word-break: break-all;
            margin-top: 15px;
            user-select: all;
            cursor: text;
        }

        .copy-button {
            background: #EF3E42;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-size: 0.9em;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
            transition: all 0.3s;
        }

        .copy-button:hover {
            background: #d63538;
            transform: scale(1.05);
        }

        .challenge-section {
            background: white;
            padding: 40px;
            margin: 25px;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #EF3E42;
        }

        .challenge-section h2 {
            text-align: center;
            margin-bottom: 30px;
            font-size: 2.5em;
            color: #005A9C;
        }

        .challenge-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 2px solid #dee2e6;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .challenge-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        .challenge-card h3 {
            margin-bottom: 15px;
            font-size: 1.5em;
            color: #005A9C;
        }

        .challenge-card p {
            color: #000000;
        }

        .challenge-input {
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            border: 2px solid #dee2e6;
            font-size: 1em;
            font-family: 'Courier New', monospace;
            margin: 15px 0;
            transition: border-color 0.3s;
        }

        .challenge-input:focus {
            outline: none;
            border-color: #EF3E42;
        }

        .check-button {
            background: linear-gradient(135deg, #005A9C 0%, #EF3E42 100%);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .check-button:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0, 90, 156, 0.3);
        }

        .feedback {
            margin-top: 15px;
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            display: none;
        }

        .feedback.correct {
            background: #d5f4e6;
            color: #27ae60;
            display: block;
        }

        .feedback.incorrect {
            background: #fadbd8;
            color: #e74c3c;
            display: block;
        }

        .hint {
            background: rgba(0, 90, 156, 0.1);
            padding: 15px;
            border-radius: 10px;
            margin-top: 15px;
            font-style: italic;
            color: #005A9C;
            border-left: 4px solid #EF3E42;
        }

        .practice-section {
            background: white;
            padding: 40px;
            margin: 25px;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #005A9C;
        }

        .practice-section h2 {
            text-align: center;
            margin-bottom: 30px;
            font-size: 2.5em;
            color: #005A9C;
        }

        .build-area {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 2px solid #dee2e6;
        }

        .build-area > p {
            font-size: 1.2em;
            margin-bottom: 25px;
            color: #000000;
        }

        .build-step {
            margin-bottom: 25px;
        }

        .step-label {
            font-size: 1.2em;
            margin-bottom: 10px;
            font-weight: bold;
            color: #005A9C;
        }

        .step-input {
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            border: 2px solid #dee2e6;
            font-size: 1em;
            font-family: 'Courier New', monospace;
            transition: border-color 0.3s;
        }

        .step-input:focus {
            outline: none;
            border-color: #EF3E42;
        }

        .url-output {
            background: #2c3e50;
            color: #00ff00;
            padding: 20px;
            border-radius: 15px;
            font-family: 'Courier New', monospace;
            font-size: 1.1em;
            margin: 20px 0;
            word-break: break-all;
            min-height: 60px;
            user-select: all;
            cursor: text;
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2em;
            }

            .teams-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="dodgers-logo">⚾</div>
            <h1>LA Sports API URL Builder</h1>
            <p>Learn to Build API URLs Like a Pro!</p>
        </div>

        <div class="lesson-section">
            <h2>📚 Lesson: Understanding API URLs</h2>
            <p>Just like finding seats at Dodger Stadium, API URLs have specific parts that tell you exactly where to go. Let's break down how to build the perfect API URL to get LA sports team data!</p>

            <div class="url-parts">
                <div class="url-part">
                    <h3>🏠 Base URL</h3>
                    <p>The foundation - like the stadium address</p>
                    <div class="code-box">https://www.thesportsdb.com/api/v1/json/</div>
                </div>

                <div class="url-part">
                    <h3>🔑 API Key</h3>
                    <p>Your ticket to access the data</p>
                    <div class="code-box">3</div>
                </div>

                <div class="url-part">
                    <h3>📍 Endpoint</h3>
                    <p>What section you're looking for</p>
                    <div class="code-box">searchteams.php</div>
                </div>

                <div class="url-part">
                    <h3>🎯 Parameters</h3>
                    <p>Your specific seat number</p>
                    <div class="code-box">?t=Dodgers</div>
                </div>
            </div>

            <h3 style="color: #005A9C; font-size: 1.5em; margin: 30px 0 15px 0;">Complete URL Example:</h3>
            <div class="code-box" style="font-size: 1.1em;">https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Dodgers</div>
        </div>

        <div class="lesson-section">
            <h2>🏟️ LA Sports Teams & Their API URLs</h2>
            <p>Here are the API URLs for each LA team. Click "Copy URL" to copy the URL and test it in your browser!</p>
            
            <div class="teams-grid">
                <div class="team-card">
                    <div class="team-icon">🏀</div>
                    <div class="team-name">LA Clippers</div>
                    <div class="stadium-name">Intuit Dome</div>
                    <div class="team-url" id="clippers-url">https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Clippers</div>
                    <button class="copy-button" onclick="copyURL('clippers-url')">📋 Copy URL</button>
                </div>

                <div class="team-card">
                    <div class="team-icon">🏈</div>
                    <div class="team-name">LA Chargers</div>
                    <div class="stadium-name">SoFi Stadium</div>
                    <div class="team-url" id="chargers-url">https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Chargers</div>
                    <button class="copy-button" onclick="copyURL('chargers-url')">📋 Copy URL</button>
                </div>

                <div class="team-card">
                    <div class="team-icon">🏈</div>
                    <div class="team-name">USC Trojans</div>
                    <div class="stadium-name">LA Memorial Coliseum</div>
                    <div class="team-url" id="usc-url">https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=USC</div>
                    <button class="copy-button" onclick="copyURL('usc-url')">📋 Copy URL</button>
                </div>

                <div class="team-card">
                    <div class="team-icon">⚾</div>
                    <div class="team-name">LA Dodgers</div>
                    <div class="stadium-name">Dodger Stadium</div>
                    <div class="team-url" id="dodgers-url">https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Dodgers</div>
                    <button class="copy-button" onclick="copyURL('dodgers-url')">📋 Copy URL</button>
                </div>
            </div>
        </div>

        <div class="practice-section">
            <h2>✏️ Practice: Build Your Own URL</h2>
            
            <div class="build-area">
                <p>Now it's your turn! Fill in the blanks to create an API URL for the LA Lakers.</p>
                
                <div class="build-step">
                    <div class="step-label">Step 1: Base URL</div>
                    <input type="text" class="step-input" id="base-url" placeholder="Enter the base URL...">
                </div>

                <div class="build-step">
                    <div class="step-label">Step 2: API Key</div>
                    <input type="text" class="step-input" id="api-key" placeholder="Enter your API key...">
                </div>

                <div class="build-step">
                    <div class="step-label">Step 3: Endpoint</div>
                    <input type="text" class="step-input" id="endpoint" placeholder="Enter the endpoint...">
                </div>

                <div class="build-step">
                    <div class="step-label">Step 4: Team Parameter</div>
                    <input type="text" class="step-input" id="parameter" placeholder="Enter ?t=TeamName...">
                </div>

                <div class="build-step">
                    <div class="step-label">Your Complete URL:</div>
                    <div class="url-output" id="built-url">Fill in the fields above to build your URL...</div>
                </div>

                <button class="check-button" style="width: 100%; padding: 15px;" onclick="checkBuiltURL()">✅ Check My URL</button>
                <div class="feedback" id="build-feedback"></div>
            </div>
        </div>

        <div class="challenge-section">
            <h2>🎯 Challenge Time!</h2>
            
            <div class="challenge-card">
                <h3>Challenge 1: Build a URL for the LA Rams</h3>
                <p>Create the complete API URL to search for the LA Rams team.</p>
                <input type="text" class="challenge-input" id="challenge1" placeholder="Type your URL here...">
                <button class="check-button" onclick="checkChallenge(1)">Check Answer</button>
                <div class="feedback" id="feedback1"></div>
                <div class="hint">💡 Hint: Replace "Dodgers" with "Rams" in the example URL</div>
            </div>

            <div class="challenge-card">
                <h3>Challenge 2: Get ALL NBA Teams</h3>
                <p>Build a URL to get all teams in the NBA league (not just one team).</p>
                <input type="text" class="challenge-input" id="challenge2" placeholder="Type your URL here...">
                <button class="check-button" onclick="checkChallenge(2)">Check Answer</button>
                <div class="feedback" id="feedback2"></div>
                <div class="hint">💡 Hint: Use endpoint "search_all_teams.php" with parameter "?l=NBA"</div>
            </div>

            <div class="challenge-card">
                <h3>Challenge 3: Search for Angel Stadium</h3>
                <p>Build a URL to search for venues/stadiums named "Angel Stadium".</p>
                <input type="text" class="challenge-input" id="challenge3" placeholder="Type your URL here...">
                <button class="check-button" onclick="checkChallenge(3)">Check Answer</button>
                <div class="feedback" id="feedback3"></div>
                <div class="hint">💡 Hint: Use endpoint "searchvenues.php" with parameter "?t=Angel%20Stadium" (spaces become %20)</div>
            </div>
        </div>
    </div>

    <script>
        function copyURL(elementId) {
            const urlElement = document.getElementById(elementId);
            const url = urlElement.textContent;
            
            navigator.clipboard.writeText(url).then(() => {
                alert('✅ URL copied to clipboard!\n\nNow paste it in your browser address bar to test it!');
            }).catch(err => {
                alert('Please select and copy the URL manually: ' + url);
            });
        }

        // Update built URL as user types
        document.getElementById('base-url')?.addEventListener('input', updateBuiltURL);
        document.getElementById('api-key')?.addEventListener('input', updateBuiltURL);
        document.getElementById('endpoint')?.addEventListener('input', updateBuiltURL);
        document.getElementById('parameter')?.addEventListener('input', updateBuiltURL);

        function updateBuiltURL() {
            const base = document.getElementById('base-url').value;
            const key = document.getElementById('api-key').value;
            const endpoint = document.getElementById('endpoint').value;
            const param = document.getElementById('parameter').value;
            
            let url = '';
            if (base) url += base;
            if (key) url += key + '/';
            if (endpoint) url += endpoint;
            if (param) url += param;
            
            document.getElementById('built-url').textContent = url || 'Fill in the fields above to build your URL...';
        }

        function checkBuiltURL() {
            const builtURL = document.getElementById('built-url').textContent.trim();
            const correctURL = 'https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Lakers';
            const feedback = document.getElementById('build-feedback');
            
            if (builtURL.toLowerCase() === correctURL.toLowerCase()) {
                feedback.className = 'feedback correct';
                feedback.textContent = '🎉 Perfect! You built the Lakers API URL correctly! Try copying and testing it in your browser.';
            } else {
                feedback.className = 'feedback incorrect';
                feedback.textContent = `❌ Not quite right. The correct answer is: ${correctURL}`;
            }
        }

        function checkChallenge(challengeNum) {
            const input = document.getElementById(`challenge${challengeNum}`).value.trim();
            const feedback = document.getElementById(`feedback${challengeNum}`);
            
            let correct = false;
            let correctAnswer = '';

            switch(challengeNum) {
                case 1:
                    correctAnswer = 'https://www.thesportsdb.com/api/v1/json/3/searchteams.php?t=Rams';
                    correct = input.toLowerCase() === correctAnswer.toLowerCase();
                    break;
                case 2:
                    correctAnswer = 'https://www.thesportsdb.com/api/v1/json/3/search_all_teams.php?l=NBA';
                    correct = input.toLowerCase() === correctAnswer.toLowerCase();
                    break;
                case 3:
                    correctAnswer = 'https://www.thesportsdb.com/api/v1/json/3/searchvenues.php?t=Angel%20Stadium';
                    const alt = 'https://www.thesportsdb.com/api/v1/json/3/searchvenues.php?t=Angel+Stadium';
                    correct = input.toLowerCase() === correctAnswer.toLowerCase() || input.toLowerCase() === alt.toLowerCase();
                    break;
            }

            if (correct) {
                feedback.className = 'feedback correct';
                feedback.textContent = '🎉 Correct! Great job! Copy this URL and test it in your browser to see the data.';
            } else {
                feedback.className = 'feedback incorrect';
                feedback.textContent = `❌ Not quite right. The correct answer is: ${correctAnswer}`;
            }
        }
    </script>
</body>
</html>