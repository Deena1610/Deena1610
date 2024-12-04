- 👋 Hi, I’m @Deena1610
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Deena1610/Deena1610 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
![1000030791](https://github.com/user-attachments/assets/8eaadd4b-00e2-4d87-b338-cd247121ba06)
![1000030792](https://github.com/user-attachments/assets/c4abb7b0-e2f6-4470-8225-b0d55952a3fe)
pip install flask
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/")
def home():
    return "வணக்கம்! இது உங்கள் AI-powered website."

@app.route("/predict", methods=["POST"])
def predict():
    data = request.json
    user_input = data.get("input", "")
    response = f"நீங்கள் சொன்னது: {user_input}. நான் உங்களுக்கு உதவுகிறேன்!"
    return jsonify({"response": response})

if __name__ == "__main__":
    app.run(debug=True)
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Assistant</title>
</head>
<body>
    <h1>Welcome to Your AI Assistant</h1>
    <input type="text" id="userInput" placeholder="Type something...">
    <button onclick="sendInput()">Send</button>
    <p id="response"></p>

    <script>
        async function sendInput() {
            const input = document.getElementById("userInput").value;
            const response = await fetch("http://127.0.0.1:5000/predict", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ input: input })
            });
            const data = await response.json();
            document.getElementById("response").innerText = data.response;
        }
    </script>
</body>
</html>
