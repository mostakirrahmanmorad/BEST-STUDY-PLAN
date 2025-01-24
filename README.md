# BEST-STUDY-PLAN
This is my frist website code
<!DOCTYPE html>
<htmllang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Study AI</title>
    <style>
        /* Global Styles */
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(to bottom right, #6a11cb, #2575fc);
            color: #fff;
            overflow-x: hidden;
        }

        header {
            text-align: center;
            padding: 20px;
            background: #444;
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        /* Loader Animation */
        #loading-screen {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100vh;
            color: white;
        }

        .loader {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }

        .loader span {
            display: block;
            width: 15px;
            height: 15px;
            margin: 0 5px;
            background-color: white;
            border-radius: 50%;
            animation: bounce 1.5s infinite;
        }

        .loader span:nth-child(2) {
            animation-delay: 0.3s;
        }

        .loader span:nth-child(3) {
            animation-delay: 0.6s;
        }

        @keyframes bounce {
            0%, 80%, 100% {
                transform: scale(0);
            }
            40% {
                transform: scale(1);
            }
        }

        /* Login Form */
        #login-form {
            max-width: 400px;
            margin: 20px auto;
            background: #333;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        #login-form h2 {
            text-align: center;
            margin-bottom: 20px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
        }

        .form-group button {
            width: 100%;
            padding: 10px;
            background: #ffdd59;
            color: #000;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1.1rem;
        }

        .form-group button:hover {
            background: #f4c542;
        }

        /* Dashboard */
        #dashboard {
            display: none;
            padding: 20px;
            text-align: center;
        }

        #dashboard h2 {
            margin-top: 0;
        }

        .progress-bar {
            width: 100%;
            background: #ddd;
            border-radius: 20px;
            overflow: hidden;
            margin: 10px 0;
        }

        .progress-bar span {
            display: block;
            height: 20px;
            background: #4caf50;
            width: 50%;
        }

        /* AI Chat */
        #ai-chat {
            margin: 20px auto;
            padding: 10px;
            max-width: 600px;
            border: 1px solid #ddd;
            background: #222;
            border-radius: 10px;
        }

        #ai-chat input {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            border: none;
        }

        #ai-chat button {
            background: #4caf50;
            padding: 10px;
            border: none;
            color: #fff;
            border-radius: 5px;
            cursor: pointer;
        }

        #ai-chat .messages {
            margin: 20px 0;
            max-height: 300px;
            overflow-y: scroll;
            border: 1px solid #444;
            padding: 10px;
        }
    </style>
</head>
<body>
    <!-- Loader -->
    <div id="loading-screen">
        <h1>Study<span>AI</span></h1>
        <div class="loader">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </div>

    <!-- Login -->
    <div id="login-section" style="display: none;">
        <header>
            <h1>Welcome to Study AI</h1>
        </header>
        <div id="login-form">
            <h2>Login</h2>
            <form onsubmit="login(event)">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="Enter your username" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="Enter your password" required>
                </div>
                <div class="form-group">
                    <button type="submit">Login</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Dashboard -->
    <div id="dashboard" style="display: none;">
        <header>
            <h2>Dashboard</h2>
        </header>
        <div>
            <h3>Study Progress</h3>
            <div class="progress-bar">
                <span style="width: 60%;">60%</span>
            </div>
            <div class="progress-bar">
                <span style="width: 80%;">80%</span>
            </div>
        </div>
        <!-- AI Chat -->
        <div id="ai-chat">
            <h3>AI Chat</h3>
            <div class="messages" id="messages"></div>
            <input type="text" id="chat-input" placeholder="Ask your study-related question">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        // Loader simulation
        window.onload = function () {
            setTimeout(() => {
                document.getElementById('loading-screen').style.display = 'none';
                document.getElementById('login-section').style.display = 'block';
            }, 3000);
        };

        // Login function
        function login(event) {
            event.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username === "student" && password === "password") {
                alert("Login Successful!");
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('dashboard').style.display = 'block';
            } else {
                alert("Invalid Username or Password.");
            }
        }

        // AI Chat simulation
        function sendMessage() {
            const chatInput = document.getElementById('chat-input').value;
            const messages = document.getElementById('messages');
            if (chatInput.trim() !== "") {
                const userMessage = `<p><b>You:</b> ${chatInput}</p>`;
                messages.innerHTML += userMessage;
                setTimeout(() => {
                    const botReply = `<p><b>AI:</b> That's an interesting question!</p>`;
                    messages.innerHTML += botReply;
                }, 1000);
            }
        }
    </script>
</body>
</html>
