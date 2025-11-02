---
layout: opencs
title: "San Diego"
description: "Stop 1: San Diego — “Connecting to the Data Field”"
permalink: /west-coast/backend/submodule_1/
parent: "Backend Development"
team: "Zombies"
submodule: 1
categories: [CSP, Submodule, Backend]
tags: [backend, submodule, zombies]
author: "Zombies Team"
date: 2025-10-21
microblog: True
footer:
  previous: /west-coast/sports/
  home: /west-coast/sports/
  next: /west-coast/backend/submodule_2/
---

# Submodule 1

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stop 1: San Diego — API Authentication & Access</title>
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
            background: transparent;
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

        .concept-box li {
            color: #000000 !important;
            line-height: 1.8;
        }

        .concept-box p strong {
            color: #000000 !important;
        }

        .concept-box code {
            background: #e9ecef;
            padding: 3px 8px;
            border-radius: 4px;
            color: #d63384;
            font-family: 'Courier New', monospace;
        }

        .tutorial-section {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #002D62;
        }

        .tutorial-section h2 {
            color: #002D62 !important;
            margin-bottom: 20px;
            font-size: 1.8em;
        }

        .tutorial-section h3 {
            color: #002D62 !important;
            margin-top: 25px;
            margin-bottom: 15px;
            font-size: 1.4em;
        }

        .tutorial-section p {
            color: #000000 !important;
            line-height: 1.8;
            margin-bottom: 15px;
        }

        .tutorial-section ol {
            margin-left: 25px;
            margin-bottom: 20px;
        }

        .tutorial-section li {
            color: #000000 !important;
            line-height: 2;
            margin-bottom: 10px;
        }

        .tutorial-section ul {
            margin-left: 25px;
        }

        .code-example {
            background: #2c3e50;
            color: #00ff00;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 0.9em;
            margin: 20px 0;
            overflow-x: auto;
        }

        .code-comment {
            color: #95a5a6;
        }

        .highlight-box {
            background: #fff3cd;
            border-left: 5px solid #ffc107;
            padding: 15px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .highlight-box p {
            color: #856404 !important;
            margin: 0;
        }

        .analogy-box {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #FFC425;
        }

        .analogy-box h2 {
            color: #002D62 !important;
            text-align: center;
            margin-bottom: 30px;
            font-size: 1.8em;
        }

        .analogy-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .analogy-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 2px solid #dee2e6;
        }

        .analogy-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        .analogy-icon {
            font-size: 1.2em;
            margin-bottom: 15px;
            font-weight: bold;
            color: #002D62;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .analogy-card h3 {
            color: #002D62 !important;
            margin-bottom: 12px;
            font-size: 1.2em;
        }

        .analogy-card p {
            color: #495057 !important;
            line-height: 1.6;
            font-size: 0.95em;
        }

        .step-indicator {
            margin-top: 15px;
            padding: 8px 12px;
            background: rgba(0, 45, 98, 0.1);
            border-radius: 6px;
            font-size: 0.85em;
            font-weight: bold;
            color: #002D62 !important;
            display: none;
        }

        .analogy-card.active .step-indicator {
            display: block;
            animation: pulse 0.5s ease-in-out;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .interactive-fetch {
            background: white;
            padding: 35px;
            margin: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            border: 3px solid #002D62;
        }

        .interactive-fetch h2 {
            color: #002D62 !important;
            text-align: center;
            margin-bottom: 15px;
            font-size: 1.8em;
        }

        .fetch-description {
            text-align: center;
            color: #495057 !important;
            margin-bottom: 25px;
            font-size: 1.05em;
        }

        .url-input {
            flex: 1;
            padding: 15px;
            border: 2px solid #dee2e6;
            border-radius: 10px;
            font-size: 1em;
            font-family: 'Courier New', monospace;
            transition: border-color 0.3s;
            width: 100%;
        }

        .url-input:focus {
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

        .example-urls {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .example-urls p {
            color: #002D62 !important;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .example-btn {
            background: white;
            color: #002D62;
            border: 2px solid #dee2e6;
            padding: 10px 15px;
            border-radius: 8px;
            margin: 5px;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }

        .example-btn:hover {
            border-color: #FFC425;
            background: #FFC425;
            color: white;
        }

        .loading-spinner {
            text-align: center;
            padding: 30px;
            display: none;
        }

        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #002D62;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .loading-spinner p {
            color: #002D62 !important;
            font-weight: bold;
        }

        .custom-response {
            background: #2c3e50;
            color: #00ff00;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 0.9em;
            white-space: pre-wrap;
            max-height: 400px;
            overflow-y: auto;
            margin-top: 20px;
        }

        .custom-response.active {
            animation: slideIn 0.3s ease-out;
        }

        .custom-response.error {
            background: #e74c3c;
            color: white;
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
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Stop 1: San Diego — "Requesting API Access"</h1>
            <p>Learn How to Authenticate Before Making API Calls</p>
        </div>

        <div class="concept-box">
            <h2>Coding Concept: Calling APIs (Part 1)</h2>
            <p><strong>Requesting Access - Authentication</strong></p>
            <ul style="margin-top: 10px; margin-left: 20px; line-height: 1.8;">
                <li>Before using an API, you often need to prove who you are</li>
                <li><strong>API Keys:</strong> Like a VIP pass that identifies your application</li>
                <li><strong>Tokens:</strong> Temporary credentials that expire after some time</li>
                <li><strong>OAuth:</strong> Like logging in with Google/Facebook - delegates authentication</li>
                <li>Public APIs = No authentication needed (rare)</li>
            </ul>
        </div>

        <div class="analogy-box">
            <h2>Understanding APIs: The Football Team Analogy</h2>
            <div class="analogy-grid">
                <div class="analogy-card" onmouseenter="highlightStep(1)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Playbook</div>
                    <h3>The Playbook (Database)</h3>
                    <p>Contains all available plays and data - like a database storing all information</p>
                    <div class="step-indicator" id="step-1">Step 1: Database holds all plays</div>
                </div>
                <div class="analogy-card" onmouseenter="highlightStep(2)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Play</div>
                    <h3>A Play (User Input)</h3>
                    <p>You select which play you want - like choosing what data to request from the API</p>
                    <div class="step-indicator" id="step-2">Step 2: Select your play</div>
                </div>
                <div class="analogy-card" onmouseenter="highlightStep(3)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Order</div>
                    <h3>Call the Play (API Request)</h3>
                    <p>You call out the order - like sending an API request with your selected endpoint</p>
                    <div class="step-indicator" id="step-3">Step 3: Input your order</div>
                </div>
                <div class="analogy-card" onmouseenter="highlightStep(4)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Coach</div>
                    <h3>The Coach (API)</h3>
                    <p>Reviews the request and decides what data to send - uses analytics to optimize response</p>
                    <div class="step-indicator" id="step-4">Step 4: API processes request</div>
                </div>
                <div class="analogy-card" onmouseenter="highlightStep(5)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Quarterback</div>
                    <h3>The Quarterback (Server)</h3>
                    <p>Executes the play and retrieves data from the playbook - like server fetching from database</p>
                    <div class="step-indicator" id="step-5">Step 5: Server retrieves data</div>
                </div>
                <div class="analogy-card" onmouseenter="highlightStep(6)" onmouseleave="resetHighlight()">
                    <div class="analogy-icon">Execution</div>
                    <h3>Play Result (Response)</h3>
                    <p>You receive the exact data you requested - API returns response to your application</p>
                    <div class="step-indicator" id="step-6">Step 6: Receive response</div>
                </div>
            </div>
        </div>

        <div class="tutorial-section">
            <h2>📚 How to Request API Access: Step-by-Step Guide</h2>
            
            <h3>Step 1: Find the API Documentation</h3>
            <p>Every API has documentation that tells you how to get access. Look for sections like "Getting Started", "Authentication", or "API Keys".</p>
            
            <div class="code-example">
<span class="code-comment">// Example: Common API Documentation URLs</span>
https://api.example.com/docs
https://developers.example.com/getting-started
https://example.com/api/authentication
            </div>

            <h3>Step 2: Sign Up / Register for an Account</h3>
            <p>Most APIs require you to create a developer account before you can get API keys.</p>
            
            <ol>
                <li>Go to the API provider's website (e.g., api.sandiegosports.com)</li>
                <li>Click "Sign Up" or "Create Developer Account"</li>
                <li>Fill in your information:
                    <ul style="margin-left: 20px; margin-top: 10px;">
                        <li>Name</li>
                        <li>Email address</li>
                        <li>Application name (what you're building)</li>
                        <li>Use case (why you need the API)</li>
                    </ul>
                </li>
                <li>Verify your email address</li>
            </ol>

            <h3>Step 3: Generate Your API Key</h3>
            <p>Once registered, you'll typically go to a dashboard or settings page to generate your API key.</p>
            
            <div class="code-example">
<span class="code-comment">// After registration, you'll receive a key like:</span>
API_KEY: sk_live_abc123xyz789def456ghi
<span class="code-comment">// This is YOUR unique identifier</span>
            </div>

            <div class="highlight-box">
                <p><strong>⚠️ IMPORTANT:</strong> Never share your API key publicly! Treat it like a password. Don't commit it to GitHub or expose it in client-side code.</p>
            </div>

            <h3>Step 4: Choose Your Access Level</h3>
            <p>Many APIs offer different tiers of access:</p>
            
            <ul style="margin-left: 25px; margin-bottom: 20px;">
                <li><strong>Free Tier:</strong> Limited requests (e.g., 100 requests/day)</li>
                <li><strong>Basic:</strong> More requests, basic features</li>
                <li><strong>Premium:</strong> High rate limits, advanced features</li>
                <li><strong>Enterprise:</strong> Unlimited access, premium support</li>
            </ul>

            <h3>Step 5: Include Your Key in API Requests</h3>
            <p>There are several ways to send your API key with requests:</p>
            
            <div class="code-example">
<span class="code-comment">// Method 1: In the Header (Most Common)</span>
fetch('https://api.example.com/data', {
    headers: {
        'Authorization': 'Bearer YOUR_API_KEY_HERE'
    }
})

<span class="code-comment">// Method 2: As a Query Parameter</span>
fetch('https://api.example.com/data?api_key=YOUR_API_KEY_HERE')

<span class="code-comment">// Method 3: In Request Body (for POST requests)</span>
fetch('https://api.example.com/data', {
    method: 'POST',
    body: JSON.stringify({
        api_key: 'YOUR_API_KEY_HERE',
        data: 'your data'
    })
})
            </div>

            <h3>Step 6: Test Your Authentication</h3>
            <p>Always test that your API key works before building your application:</p>
            
            <div class="code-example">
<span class="code-comment">// Simple test request</span>
const API_KEY = 'sk_live_abc123xyz789';

fetch('https://api.sandiegosports.com/test', {
    headers: {
        'Authorization': `Bearer ${API_KEY}`
    }
})
.then(response => response.json())
.then(data => {
    console.log('✅ Authentication successful!');
    console.log(data);
})
.catch(error => {
    console.log('❌ Authentication failed:', error);
});
            </div>

            <h3>Best Practices for API Keys</h3>
            <ul style="margin-left: 25px; margin-bottom: 20px;">
                <li>✅ Store keys in environment variables (.env files)</li>
                <li>✅ Use different keys for development and production</li>
                <li>✅ Rotate (change) your keys periodically</li>
                <li>✅ Keep keys on the server-side, not client-side</li>
                <li>❌ Never hardcode keys in your source code</li>
                <li>❌ Never commit keys to version control (GitHub)</li>
                <li>❌ Never share keys in public forums or Slack</li>
            </ul>

            <div class="code-example">
<span class="code-comment">// WRONG ❌ - Hardcoded key in code</span>
const apiKey = 'sk_live_abc123xyz789';

<span class="code-comment">// RIGHT ✅ - Using environment variable</span>
const apiKey = process.env.API_KEY;
            </div>
        </div>

        <div class="interactive-fetch">
            <h2>🎟️ Interactive: Request Your API Access Pass!</h2>
            <p class="fetch-description">Simulate the API registration process - Get your credentials to access venue data</p>
            
            <div style="background: #f8f9fa; padding: 25px; border-radius: 12px; margin-bottom: 25px;">
                <h3 style="color: #002D62; margin-bottom: 15px; text-align: center;">Step 1: Register for API Access</h3>
                
                <div style="margin-bottom: 15px;">
                    <label style="display: block; color: #002D62; font-weight: bold; margin-bottom: 8px;">Your Name:</label>
                    <input type="text" id="user-name" class="url-input" placeholder="Enter your name">
                </div>
                
                <div style="margin-bottom: 15px;">
                    <label style="display: block; color: #002D62; font-weight: bold; margin-bottom: 8px;">Your Email:</label>
                    <input type="email" id="user-email" class="url-input" placeholder="your.email@example.com">
                </div>
                
                <div style="margin-bottom: 20px;">
                    <label style="display: block; color: #002D62; font-weight: bold; margin-bottom: 8px;">Access Level:</label>
                    <select id="access-level" style="width: 100%; padding: 15px; border: 2px solid #dee2e6; border-radius: 10px; font-size: 1em;">
                        <option value="basic">Basic (Public data only) - 100 requests/hour</option>
                        <option value="premium">Premium (Full stadium stats) - 1000 requests/hour</option>
                        <option value="enterprise">Enterprise (Real-time data + Analytics) - 10000 requests/hour</option>
                    </select>
                </div>
                
                <button class="fetch-btn" onclick="generateAPIKey()" style="width: 100%; padding: 18px;">
                    🎫 Generate My API Key
                </button>
            </div>

            <div id="api-key-display" style="display: none; background: white; padding: 25px; border-radius: 12px; border: 3px solid #FFC425; margin-bottom: 25px;">
                <h3 style="color: #002D62; margin-bottom: 15px; text-align: center;">✅ Your API Credentials</h3>
                
                <div style="background: #2c3e50; color: #00ff00; padding: 20px; border-radius: 8px; margin-bottom: 15px; font-family: 'Courier New', monospace;">
                    <div style="margin-bottom: 10px;">
                        <strong style="color: #FFC425;">API Key:</strong><br>
                        <span id="generated-key" style="word-break: break-all;"></span>
                    </div>
                    <div style="margin-bottom: 10px;">
                        <strong style="color: #FFC425;">Access Level:</strong> <span id="display-access"></span>
                    </div>
                    <div>
                        <strong style="color: #FFC425;">Rate Limit:</strong> <span id="display-rate"></span> requests/hour
                    </div>
                </div>
                
                <p style="color: #495057; text-align: center; font-size: 0.95em;">
                    🔒 Keep your API key secret! Never share it publicly or commit it to GitHub.
                </p>
            </div>

            <div id="auth-demo-section" style="display: none;">
                <h3 style="color: #002D62; margin-bottom: 15px; text-align: center;">Step 2: Make an Authenticated Request</h3>
                
                <div class="example-urls">
                    <p><strong>Try these authenticated API calls:</strong></p>
                    <button class="example-btn" onclick="authenticatedFetch('petco')">🏟️ Petco Park Info</button>
                    <button class="example-btn" onclick="authenticatedFetch('snapdragon')">⚽ Snapdragon Stadium</button>
                    <button class="example-btn" onclick="authenticatedFetch('all')">📊 All Venues</button>
                    <button class="example-btn" onclick="authenticatedFetch('unauthorized')" style="background: #ffe6e6; border-color: #ff6b6b;">❌ Try Without Key</button>
                </div>

                <div id="auth-loading" class="loading-spinner">
                    <div class="spinner"></div>
                    <p>Authenticating and fetching data...</p>
                </div>

                <div id="auth-response" class="custom-response"></div>
            </div>
        </div>

        <div class="key-learning">
            <h3>🎯 Key Learning</h3>
            <p>API Keys are like VIP passes - they identify your application and control what data you can access. Always keep them secret and never share them publicly!</p>
        </div>
    </div>

    <script>
        let userAPIKey = null;
        let userAccessLevel = null;

        const stadiumData = {
            petco: {
                name: "Petco Park",
                sport: "Baseball",
                team: "San Diego Padres",
                league: "MLB",
                capacity: 40209,
                location: "Downtown San Diego",
                opened: 2004,
                surface: "Grass",
                nickname: "The Park at the Park"
            },
            snapdragon: {
                name: "Snapdragon Stadium",
                sport: "Soccer",
                team: "San Diego FC & San Diego Wave FC",
                league: "MLS / NWSL",
                capacity: 35000,
                location: "San Diego State University",
                opened: 2022,
                surface: "Grass",
                nickname: "The Dragon's Lair"
            },
            pechanga: {
                name: "Pechanga Arena",
                sport: "Hockey",
                team: "San Diego Gulls",
                league: "AHL",
                capacity: 12920,
                location: "Midway District",
                opened: 1966,
                surface: "Ice",
                nickname: "The Pond"
            }
        };

        function generateAPIKey() {
            const name = document.getElementById('user-name').value.trim();
            const email = document.getElementById('user-email').value.trim();
            const accessLevel = document.getElementById('access-level').value;

            if (!name || !email) {
                alert('Please fill in both name and email!');
                return;
            }

            const randomKey = 'sk_live_' + Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
            userAPIKey = randomKey;
            userAccessLevel = accessLevel;

            document.getElementById('generated-key').textContent = randomKey;
            document.getElementById('display-access').textContent = accessLevel.charAt(0).toUpperCase() + accessLevel.slice(1);
            
            const rateLimits = {
                basic: 100,
                premium: 1000,
                enterprise: 10000
            };
            document.getElementById('display-rate').textContent = rateLimits[accessLevel];

            document.getElementById('api-key-display').style.display = 'block';
            document.getElementById('auth-demo-section').style.display = 'block';

            setTimeout(() => {
                document.getElementById('api-key-display').scrollIntoView({ behavior: 'smooth', block: 'center' });
            }, 100);
        }

        function authenticatedFetch(endpoint) {
            const responseDiv = document.getElementById('auth-response');
            const loadingDiv = document.getElementById('auth-loading');

            if (endpoint === 'unauthorized') {
                loadingDiv.style.display = 'block';
                responseDiv.style.display = 'none';

                setTimeout(() => {
                    loadingDiv.style.display = 'none';
                    responseDiv.style.display = 'block';
                    responseDiv.classList.add('active', 'error');
                    
                    const errorResponse = {
                        status: 401,
                        error: "Unauthorized",
                        message: "API key is required. Please include 'Authorization: Bearer YOUR_API_KEY' in the request header.",
                        documentation: "https://api.sandiegosports.com/docs/authentication",
                        timestamp: new Date().toISOString()
                    };
                    
                    responseDiv.textContent = JSON.stringify(errorResponse, null, 2);
                    
                    setTimeout(() => {
                        responseDiv.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                    }, 100);
                }, 1000);
                return;
            }

            if (!userAPIKey) {
                alert('Please generate your API key first by filling out the form above!');
                return;
            }

            loadingDiv.style.display = 'block';
            responseDiv.style.display = 'none';

            setTimeout(() => {
                loadingDiv.style.display = 'none';
                responseDiv.style.display = 'block';
                responseDiv.classList.remove('error');
                responseDiv.classList.add('active');

                let data;
                if (endpoint === 'all') {
                    data = {
                        city: "San Diego",
                        total_venues: 3,
                        venues: Object.values(stadiumData)
                    };
                } else {
                    data = stadiumData