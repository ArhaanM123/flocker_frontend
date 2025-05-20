---
layout: post
title: Flocker Social Media Site 
search_exclude: true
description: Login and explore our social media hub for everything DNHS 
hide: true
menu: nav/home.html
---


<html>
<head>
    <title>Flask WebSocket Chat</title>
    <script src="https://cdn.socket.io/4.5.4/socket.io.min.js"></script>
</head>
<body>
    <h1>WebSocket Chat</h1>
    <input id="msgInput" placeholder="Type a message...">
    <button onclick="sendMessage()">Send</button>
    <ul id="messages"></ul>
    <script>
        const socket = io("http://localhost:4887");
        socket.on("connect", () => {
            console.log("Connected to server");
        });
        socket.on("message", (msg) => {
            const li = document.createElement("li");
            li.textContent = msg;
            document.getElementById("messages").appendChild(li);
        });
        function sendMessage() {
            const input = document.getElementById("msgInput");
            const msg = input.value;
            socket.send(msg);
            input.value = "";
        }
    </script>
</body>
</html>
