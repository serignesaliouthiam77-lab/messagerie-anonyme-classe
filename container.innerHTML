let currentUser = "";
let currentClass = "";

const usernameInput = document.getElementById("username");
const classCodeInput = document.getElementById("classCode");

function joinClass() {

    const username = usernameInput.value.trim();
    const classCode = classCodeInput.value.trim();

    if (!username || !classCode) {
        alert("Entre ton pseudo et le code de la classe.");
        return;
    }

    currentUser = username;
    currentClass = classCode;

    localStorage.setItem("classUser", currentUser);
    localStorage.setItem("classCode", currentClass);

    document.getElementById("login").classList.add("hidden");
    document.getElementById("chat").classList.remove("hidden");

    document.getElementById("className").textContent =
        "Classe : " + currentClass;

    loadMessages();
}

function leaveClass() {

    localStorage.removeItem("classUser");
    localStorage.removeItem("classCode");

    location.reload();
}

function getStorageKey() {

    return "messages_" + currentClass;
}

function loadMessages() {

    const messages =
        JSON.parse(localStorage.getItem(getStorageKey())) || [];

    const container =
        document.getElementById("messages");

    container.innerHTML = "";

    messages.forEach(message => {
        displayMessage(message);
    });

    container.scrollTop = container.scrollHeight;
}

function displayMessage(message) {

    const container =
        document.getElementById("messages");

    const div =
        document.createElement("div");

    div.classList.add("message");

    if (message.author === currentUser) {
        div.classList.add("me");
    }

    div.innerHTML = `
        <div class="message-author">
            ${escapeHTML(message.author)}
        </div>

        <div class="message-text">
            ${escapeHTML(message.text)}
        </div>

        <div class="message-time">
            ${message.time}
        </div>
    `;

    container.appendChild(div);
}

document
    .getElementById("messageForm")
    .addEventListener("submit", function(event) {

        event.preventDefault();

        const input =
            document.getElementById("messageInput");

        const text = input.value.trim();

        if (!text) {
            return;
        }

        const messages =
            JSON.parse(localStorage.getItem(getStorageKey())) || [];

        const message = {

            author: currentUser,

            text: text,

            time: new Date().toLocaleTimeString(
                "fr-FR",
                {
                    hour: "2-digit",
                    minute: "2-digit"
                }
            )
        };

        messages.push(message);

        localStorage.setItem(
            getStorageKey(),
            JSON.stringify(messages)
        );

        input.value = "";

        loadMessages();
    });

function escapeHTML(text) {

    const div =
        document.createElement("div");

    div.textContent = text;

    return div.innerHTML;
}

document
    .getElementById("darkMode")
    .addEventListener("click", function() {

        document.body.classList.toggle("dark");

    });

window.addEventListener("load", function() {

    const savedUser =
        localStorage.getItem("classUser");

    const savedClass =
        localStorage.getItem("classCode");

    if (savedUser && savedClass) {

        currentUser = savedUser;
        currentClass = savedClass;

        document.getElementById("login")
            .classList.add("hidden");

        document.getElementById("chat")
            .classList.remove("hidden");

        document.getElementById("className")
            .textContent = "Classe : " + currentClass;

        loadMessages();
    }

});