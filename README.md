<!DOCTYPE html>
<html lang="hi">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultra Smart Hindi ChatBot</title>
    <link rel="stylesheet" href="style.css">
</head>
<style>
    body {
        font-family: "Poppins", sans-serif;
        background: linear-gradient(135deg, #89f7fe, #66a6ff);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }

    .chat-container {
        height: 100%;
        width: 97%;
        max-width: 420px;
        background: white;
        border-radius: 15px;
        box-shadow: 0 4px 20px rgba(9, 9, 9, 1);
        overflow: hidden;
        display: flex;
        flex-direction: column;
    }

    .chat-header {
        background: linear-gradient(90deg, #3b82f6, #2563eb);
        color: white;
        padding: 15px;
        text-align: center;
        font-size: 20px;
        font-weight: bold;
    }

    .chat-box {
        flex: 1;
        padding: 15px;
        overflow-y: auto;
        display: flex;
        flex-direction: column;
        scroll-behavior: smooth;
    }

    .msg {
        margin: 8px 0;
        padding: 10px 14px;
        border-radius: 10px;
        max-width: 75%;
        line-height: 1.5;
        font-size: 15px;
        animation: fadeIn 0.3s ease;
        box-shadow: 0 4px 20px rgba(0, 0, 25, 0.7);
    }

    .user {
        align-self: flex-end;
        background: #DCF8C6;
        border-top-right-radius: 0;
    }

    .bot {
        align-self: flex-start;
        background: #EAEAEA;
        border-top-left-radius: 0;
    }

    .typing {
        font-style: italic;
        color: #777;
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
            transform: translateY(5px);
        }

        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .chat-input {
        display: flex;
        border-top: 1px solid #ddd;
        background: #fafafa;
    }

    .chat-input input {
        flex: 1;
        padding: 12px;
        border: none;
        outline: none;
        font-size: 16px;
    }

    .chat-input button {
        background: #3b82f6;
        color: white;
        border: none;
        padding: 12px 18px;
        font-size: 16px;
        cursor: pointer;
        transition: 0.3s;
    }

    .chat-input button:hover {
        background: #2563eb;
    }
</style>

<body>
    <div class="chat-container">
        <div class="chat-header">🤖 Ultra Smart ChatBot</div>
        <div class="chat-box" id="chat-box">
            <div class="msg bot">Namaste 🙏! Main aapka Ultra SmartBot hoon 💡<br>Mujhse baat karne ke liye kuch likhiye...</div>
        </div>
        <div class="chat-input">
            <input type="text" id="user-input" placeholder="Apna message likhiye..." onkeydown="if(event.key==='Enter') sendMessage()">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            const input = document.getElementById("user-input");
            const msg = input.value.trim();
            if (!msg) return;
            showMessage(msg, "user");
            input.value = "";
            setTimeout(() => {
                showTyping();
                setTimeout(() => {
                    removeTyping();
                    const reply = getBotReply(msg.toLowerCase());
                    showMessage(reply, "bot");
                }, 1000);
            }, 400);
        }

        function showMessage(message, sender) {
            const chatBox = document.getElementById("chat-box");
            const msgDiv = document.createElement("div");
            msgDiv.className = "msg " + sender;
            msgDiv.innerHTML = message;
            chatBox.appendChild(msgDiv);
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function showTyping() {
            const chatBox = document.getElementById("chat-box");
            const typingDiv = document.createElement("div");
            typingDiv.className = "msg bot typing";
            typingDiv.id = "typing";
            typingDiv.textContent = "Typing...";
            chatBox.appendChild(typingDiv);
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function removeTyping() {
            const typingDiv = document.getElementById("typing");
            if (typingDiv) typingDiv.remove();
        }

        function getBotReply(msg) {
            const emojis = ["😊", "😄", "😉", "😎", "🤗"];
            const randomEmoji = emojis[Math.floor(Math.random() * emojis.length)];

            if (["hello", "hi", "namaste", "hey"].some(w => msg.includes(w)))
                return `Namaste! Kaise ho? ${randomEmoji}`;

            if (["kaise", "badiya","haal", "hal", "kaisa"].some(w => msg.includes(w)))
                return "Main bilkul mast hoon 😄 Aap batao, life kaisi chal rahi hai?";

            if (["dhanyavad", "shukriya", "thank"].some(w => msg.includes(w)))
                return "Arre, aapka to hamesha swagat hai! 🙏";

            if (["naam", "name", "tumhara naam"].some(w => msg.includes(w)))
                return "Mera naam Ultra SmartBot hai 💬 Aapka kya naam hai?";

            if (msg.includes("mera naam"))
                return "Wah! Bahut khoobsurat naam hai aapka 💖";

            if (["udaas", "sad", "bura", "dukh"].some(w => msg.includes(w)))
                return "Arre udaas mat ho dost 😔 Har subah nayi umeed leke aati hai 🌅";

            if (["sexi", "land", "gf", "cut"].some(w => msg.includes(w)))
                return "meri le lo na aaj rat ko 🥰";

            if (["khush", "happy", "accha", "mood"].some(w => msg.includes(w)))
                return "Yeh hui na baat! Khush raho hamesha 😄✨";

            if (["padhai", "school", "college", "study"].some(w => msg.includes(w)))
                return "Padhai zaruri hai 📚 Lekin apne liye time nikalna aur smile karna aur bhi zaruri 😄";

            if (["mausam", "barish", "garmi", "thand"].some(w => msg.includes(w)))
                return "Mausam to badal raha hai 🌦️ Aapke yahan kaisa hai abhi?";

            if (["food", "khaana", "bhukh", "khana"].some(w => msg.includes(w)))
                return "Mujhe samosa aur chai bahut pasand hai ☕😋 Aapka favourite kya hai?";

            if (msg.includes("time"))
                return "Abhi ka samay hai 🕒: " + new Date().toLocaleTimeString();

            if (["date", "tareekh"].some(w => msg.includes(w)))
                return "Aaj ki tareekh hai 📅: " + new Date().toLocaleDateString();

            if (["joke", "jok","mazaak", "chutkula"].some(w => msg.includes(w))) {
                const jokes = [
                    "Computer ka favourite khana kya hai? — Micro-chips! 😂",
                    "Programmer: meri gf ne kaha ‘space do’, maine code me space de diya 😆",
                    "Teacher: Tum late kyu aaye? Student: Sir, sleep mode me tha! 😴"
                ];
                return jokes[Math.floor(Math.random() * jokes.length)];
            }

            if (["bye", "alvida", "goodbye", "phir milte"].some(w => msg.includes(w)))
                return "Alvida dost 👋 Apna khayal rakhna, phir milte hain!";

            // Default friendly replies
            const randomReplies = [
                `Wah! Yeh baat to interesting hai ${randomEmoji}`,
                `Hmm, mujhe aur batao na 🤔`,
                `Aapka sense of humor accha hai 😅`,
                `Mujhe lagta hai aap smart ho 💡`,
                `Accha! Yeh baat mujhe pehli baar pata chali 😄`
            ];
            return randomReplies[Math.floor(Math.random() * randomReplies.length)];
        }
    </script>
</body>

</html>
