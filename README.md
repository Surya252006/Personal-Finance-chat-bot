# Personal-Finance-chat-bot
Here i submit front-end code


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Finance Chatbot</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700&display=swap" rel="stylesheet">
    <style>
        body {
            background: linear-gradient(135deg, #74ebd5 0%, #ACB6E5 100%);
            font-family: 'Montserrat', sans-serif;
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .chat-container {
            background: #fff;
            border-radius: 25px;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.2);
            width: 400px;
            max-width: 90vw;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }
        .chat-header {
            background: linear-gradient(90deg, #11998e 0%, #38ef7d 100%);
            color: #fff;
            padding: 1.2rem 2rem;
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: 1px;
            text-align: center;
            border-bottom: 2px solid #c5f3e3;
        }
        .chat-body {
            height: 350px;
            overflow-y: auto;
            padding: 1.2rem 1rem;
            background: #f7fafc;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }
        .message {
            max-width: 80%;
            padding: 0.8rem 1.1rem;
            border-radius: 20px;
            font-size: 1rem;
            line-height: 1.4;
            display: flex;
            align-items: center;
            animation: fadeIn 0.2s;
        }
        .bot-message {
            background: linear-gradient(90deg, #acb6e5 0%, #74ebd5 100%);
            color: #222;
            align-self: flex-start;
            border-bottom-left-radius: 4px;
            box-shadow: 1px 2px 8px #e3e3e3;
        }
        .user-message {
            background: linear-gradient(90deg, #f7971e 0%, #ffd200 100%);
            color: #222;
            align-self: flex-end;
            border-bottom-right-radius: 4px;
            box-shadow: 1px 2px 8px #e3e3e3;
        }
        .chat-footer {
            display: flex;
            background: #f7fafc;
            padding: 1rem;
            border-top: 1px solid #e6eaf1;
        }
        .chat-footer input {
            flex: 1;
            padding: 0.8rem 1rem;
            border: none;
            border-radius: 20px;
            font-size: 1rem;
            outline: none;
            background: #e9f6fb;
            margin-right: 0.7rem;
            transition: background 0.2s;
        }
        .chat-footer input:focus {
            background: #d1f0e8;
        }
        .chat-footer button {
            background: linear-gradient(90deg, #11998e 0%, #38ef7d 100%);
            border: none;
            border-radius: 50%;
            width: 45px;
            height: 45px;
            color: #fff;
            font-size: 1.3rem;
            cursor: pointer;
            transition: background 0.2s;
            box-shadow: 0 4px 12px rgba(56, 239, 125, 0.2);
        }
        .chat-footer button:hover {
            background: linear-gradient(90deg, #38ef7d 0%, #11998e 100%);
        }
        @keyframes fadeIn {
            from {opacity: 0; transform: translateY(20px);}
            to {opacity: 1; transform: translateY(0);}
        }
        /* Responsive */
        @media (max-width: 450px) {
            .chat-container {
                width: 100vw;
                min-height: 100vh;
                border-radius: 0;
            }
            .chat-header {
                font-size: 1.2rem;
                padding: 1rem;
            }
            .chat-footer button {
                width: 40px;
                height: 40px;
            }
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            💸 Personal Finance Chatbot
        </div>
        <div class="chat-body" id="chat-body">
            <div class="message bot-message">
                👋 Hi! I'm your personal finance assistant.<br>
                Ask me anything about budgeting, saving, or expense tracking!
            </div>
        </div>
        <div class="chat-footer">
            <input id="user-input" type="text" placeholder="Type your message..." autocomplete="off" />
            <button id="send-btn" title="Send"><span>&#9658;</span></button>
        </div>
    </div>

    <script>
        const chatBody = document.getElementById('chat-body');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');

        function appendMessage(text, sender = 'user') {
            const msgDiv = document.createElement('div');
            msgDiv.className = `message ${sender}-message`;
            msgDiv.innerHTML = text;
            chatBody.appendChild(msgDiv);
            chatBody.scrollTop = chatBody.scrollHeight;
        }

        // Demo: Replace with your backend/chatbot API call
        function getBotResponse(userText) {
            // Placeholder: You should replace this with your actual backend API call.
            const responses = [
                "Here's a budgeting tip: Track every expense, even small ones!",
                "Saving 10% of your income is a great start. Need more ways to save?",
                "Want to analyze your spending trends? Connect your bank for insights.",
                "Set a financial goal – I'm here to help you plan for it!"
            ];
            return responses[Math.floor(Math.random() * responses.length)];
        }

        function handleSend() {
            const text = userInput.value.trim();
            if (!text) return;
            appendMessage(text, 'user');
            userInput.value = '';
            setTimeout(() => {
                const botReply = getBotResponse(text);
                appendMessage(`🤖 ${botReply}`, 'bot');
            }, 650);
        }

        sendBtn.addEventListener('click', handleSend);
        userInput.addEventListener('keyup', function(e) {
            if (e.key === 'Enter') handleSend();
        });
    </script>
</body>
</html>
