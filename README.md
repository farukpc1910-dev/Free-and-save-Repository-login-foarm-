<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Login Boom Effect</title>

    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(120deg, #000428, #004e92);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            overflow: hidden;
        }

        .login-box {
            background: rgba(255, 255, 255, 0.1);
            padding: 40px;
            width: 320px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 0 20px rgba(0,0,0,0.6);
        }

        .login-box h2 {
            color: #fff;
            margin-bottom: 30px;
        }

        .login-box input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: none;
            outline: none;
            border-radius: 5px;
            font-size: 16px;
        }

        .login-box button {
            width: 100%;
            padding: 12px;
            background: #ff0055;
            border: none;
            color: white;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 15px;
        }

        .login-box button:hover {
            background: #ff3366;
        }

        /* SHAKE ANIMATION */
        .shake {
            animation: shake 0.5s;
        }

        @keyframes shake {
            0% { transform: translateX(0); }
            20% { transform: translateX(-10px); }
            40% { transform: translateX(10px); }
            60% { transform: translateX(-10px); }
            80% { transform: translateX(10px); }
            100% { transform: translateX(0); }
        }

        /* BOOM TEXT */
        #boom {
            position: absolute;
            font-size: 150px;
            font-weight: bold;
            color: yellow;
            text-shadow: 0 0 20px red, 0 0 40px orange;
            display: none;
            animation: boomEffect 1s ease-in-out;
        }

        @keyframes boomEffect {
            0% {
                transform: scale(0) rotate(0deg);
                opacity: 0;
            }
            50% {
                transform: scale(1.5) rotate(10deg);
                opacity: 1;
            }
            100% {
                transform: scale(1) rotate(-10deg);
                opacity: 1;
            }
        }
    </style>
</head>

<body>

    <div class="login-box" id="loginBox">
        <h2>Login</h2>
        <input type="text" placeholder="Username" id="username">
        <input type="password" placeholder="Password" id="password">
        <button onclick="boom()">Submit</button>
    </div>

    <div id="boom">BOOM</div>

    <script>
        function boom() {
            var box = document.getElementById("loginBox");
            var boomText = document.getElementById("boom");

            // Shake effect
            box.classList.remove("shake");
            void box.offsetWidth;
            box.classList.add("shake");

            // Show BOOM
            boomText.style.display = "block";
            boomText.style.animation = "none";
            void boomText.offsetWidth;
            boomText.style.animation = "boomEffect 1s ease-in-out";

            // Hide BOOM after 2 seconds
            setTimeout(function(){
                boomText.style.display = "none";
            }, 2000);
        }
    </script>

</body>
</html>
