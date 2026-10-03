# messagerie-anonyme-classe
Application de messagerie anonyme entre amis de classe
messagerie-anonyme-classe/
│
├── index.html
├── style.css
├── script.js
└── README.md
index.html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>ClassSecret 🤫📚</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <div class="app">

        <header>
            <div>
                <h1>ClassSecret 🤫</h1>
                <p>Messagerie anonyme de la classe</p>
            </div>

            <button id="darkMode">🌙</button>
        </header>

        <section id="login">
            <h2>Bienvenue 👋</h2>

            <p>
                Choisis un pseudo anonyme pour entrer dans la classe.
            </p>

            <input
                type="text"
                id="username"
                placeholder="Ex : Élève_221"
                maxlength="20"
            >

            <input
                type="text"
                id="classCode"
                placeholder="Code de la classe"
                maxlength="20"
            >

            <button onclick="joinClass()">
                Entrer dans la classe 🚀
            </button>
        </section>

        <section id="chat" class="hidden">

            <div class="class-info">
                <div>
                    <strong id="className"></strong>
                    <span>🟢 En ligne</span>
                </div>

                <button onclick="leaveClass()">Quitter</button>
            </div>

            <div id="messages"></div>

            <form id="messageForm">

                <input
                    type="text"
                    id="messageInput"
                    placeholder="Écris un message..."
                    maxlength="300"
                    autocomplete="off"
                >

                <button type="submit">
                    ➤
                </button>

            </form>

        </section>

    </div>

    <script src="script.js"></script>

</body>
</html>