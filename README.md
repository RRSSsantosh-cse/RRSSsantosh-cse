<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Typing Animation</title>
  <style>
    body {
      font-family: 'Courier New', monospace;
      background: #111;
      color: #0f0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      font-size: 1.5rem;
    }

    .typing-container {
      white-space: nowrap;
      overflow: hidden;
      border-right: 2px solid #0f0;
      width: 0ch;
      animation: typing 3s steps(40) 1s forwards, blink 0.75s step-end infinite;
    }

    @keyframes typing {
      from { width: 0ch; }
      to { width: 40ch; }
    }

    @keyframes blink {
      50% { border-color: transparent; }
    }

    .hidden {
      display: none;
    }
  </style>
</head>
<body>

  <div id="typing" class="typing-container"></div>

  <script>
    const phrases = [
      "a passionate software developer",
      "an enthusiastic web developer",
      "eager to learn new technologies",
      "a hard worker"
    ];

    const typingDiv = document.getElementById("typing");
    let i = 0;

    function typePhrase(phrase, callback) {
      typingDiv.style.width = '0ch';
      typingDiv.innerHTML = "";
      let index = 0;

      const interval = setInterval(() => {
        typingDiv.innerHTML += phrase.charAt(index);
        index++;
        if (index === phrase.length) {
          clearInterval(interval);
          setTimeout(callback, 1500);
        }
      }, 100);
    }

    function startTypingLoop() {
      typePhrase(phrases[i], () => {
        i = (i + 1) % phrases.length;
        setTimeout(startTypingLoop, 500);
      });
    }

    startTypingLoop();
  </script>

</body>
</html>
