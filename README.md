- 👋 Hi, I’m @Jhaque19
- 👀 I’m interested in ...<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Spin Wheel Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        .wheel-container {
            position: relative;
            width: 300px;
            height: 300px;
        }
        .wheel {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 10px solid #333;
            position: relative;
            overflow: hidden;
        }
        .wheel div {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
        }
        .wheel div:nth-child(1) { background-color: #ffcc00; transform: rotate(0deg) skewY(-60deg); }
        .wheel div:nth-child(2) { background-color: #ff9900; transform: rotate(36deg) skewY(-60deg); }
        .wheel div:nth-child(3) { background-color: #ff6600; transform: rotate(72deg) skewY(-60deg); }
        .wheel div:nth-child(4) { background-color: #ff3300; transform: rotate(108deg) skewY(-60deg); }
        .wheel div:nth-child(5) { background-color: #ff0000; transform: rotate(144deg) skewY(-60deg); }
        .wheel div:nth-child(6) { background-color: #cc0000; transform: rotate(180deg) skewY(-60deg); }
        .wheel div:nth-child(7) { background-color: #990000; transform: rotate(216deg) skewY(-60deg); }
        .wheel div:nth-child(8) { background-color: #660000; transform: rotate(252deg) skewY(-60deg); }
        .wheel div:nth-child(9) { background-color: #330000; transform: rotate(288deg) skewY(-60deg); }
        .wheel div:nth-child(10) { background-color: #000000; transform: rotate(324deg) skewY(-60deg); }
        
        .spin-button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .icon-box {
            margin-top: 20px;
            text-align: center;
        }

        .icon-box div {
            margin: 10px;
            display: inline-block;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
            background-color: #f1f1f1;
        }
    </style>
</head>
<body>
    <div class="wheel-container">
        <div class="wheel">
            <div>1. 0.50$</div>
            <div>2. 0.005$</div>
            <div>3. 0.1$</div>
            <div>4. 2$</div>
            <div>5. 0.5$</div>
            <div>6. 500 Apple Coins</div>
            <div>7. 10 Apple Star</div>
            <div>8. 0.100$</div>
            <div>9. 0.1$</div>
            <div>10. 1000 Apple Coins</div>
        </div>
        <button class="spin-button" onclick="spinWheel()">Spin Wheel</button>
    </div>

    <div class="icon-box">
        <div>1. Apple Coins: 500</div>
        <div>2. 0.1$</div>
        <div>3. 0.005$</div>
    </div>

    <script>
        function spinWheel() {
            let wheel = document.querySelector('.wheel');
            let randomDeg = Math.floor(Math.random() * 3600) + 360;
            wheel.style.transition = "all 5s ease-out";
            wheel.style.transform = "rotate(" + randomDeg + "deg)";
        }
    </script>
</body>
</html>
- 🌱 I’m currently learning ...<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hamster Kombat</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f7f7f7;
            text-align: center;
        }

        h1 {
            color: #333;
        }

        #profile {
            margin-bottom: 20px;
        }

        #gameCanvas {
            background-color: #a4d3ee;
            margin: 20px auto;
            display: block;
            border: 2px solid #333;
        }

        .buttons {
            margin: 20px;
        }

        button {
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            margin: 10px;
            background-color: #ffcc00;
            border: none;
            border-radius: 5px;
        }

        #profile, #referral {
            margin: 20px;
            font-size: 18px;
        }

        #coins {
            font-size: 24px;
            margin: 20px;
        }

        #profileInfo {
            font-size: 20px;
            color: #555;
        }

        #withdrawBtn {
            background-color: #ff6347;
        }
    </style>
</head>
<body>

<h1>Hamster Kombat</h1>

<!-- Profile Section -->
<div id="profile">
    <p id="profileInfo">Player: <strong>John Doe</strong></p>
    <p id="coins">Coins: 0</p>
    <button id="withdrawBtn">Withdraw Coins</button>
</div>

<!-- Game Canvas -->
<canvas id="gameCanvas" width="600" height="400"></canvas>

<!-- Action Buttons -->
<div class="buttons">
    <button id="attackBtn">Tap to Earn Coins</button>
</div>

<!-- Referral Link Section -->
<div id="referral">
    <p id="referralLink">Your Referral Link: <a href="#">Generate Link</a></p>
</div>

<script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    // Game variables
    let player = { x: 100, y: 300, width: 50, height: 50, image: new Image(), health: 100 };
    let enemy = { x: 400, y: 300, width: 50, height: 50, image: new Image(), health: 100 };
    player.image.src = 'https://example.com/player-hamster.png'; // Replace with your image URL
    enemy.image.src = 'https://example.com/enemy-hamster.png'; // Replace with your image URL

    let coins = 0;

    // Draw the hamster (player and enemy)
    function drawHamster(hamster) {
        ctx.drawImage(hamster.image, hamster.x, hamster.y, hamster.width, hamster.height);
    }

    // Draw game objects
    function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawHamster(player);
        drawHamster(enemy);
    }

    // Attack the enemy hamster and earn coins
    function attack() {
        enemy.health -= 10;
        if (enemy.health <= 0) {
            coins += 10;
            enemy.health = 100; // Reset enemy health
            updateCoins();
        }
        draw();
    }

    // Update coin display
    function updateCoins() {
        document.getElementById('coins').innerText = `Coins: ${coins}`;
    }

    // Withdraw function (simulated)
    function withdraw() {
        alert(`You have withdrawn ${coins} coins!`);
        coins = 0;
        updateCoins();
    }

    // Generate referral link (example)
    function generateReferralLink() {
        const referralCode = Math.random().toString(36).substring(2, 8);
        const link = `${window.location.href}?ref=${referralCode}`;
        document.getElementById('referralLink').innerHTML = `Your Referral Link: <a href="${link}">${link}</a>`;
    }

    // Check for referral in URL
    const urlParams = new URLSearchParams(window.location.search);
    const referrer = urlParams.get('ref');
    if (referrer) {
        alert(`You were referred by ${referrer}. You earn 5 bonus coins!`);
        coins += 5;
        updateCoins();
    }

    // Event listeners
    document.getElementById('attackBtn').addEventListener('click', attack);
    document.getElementById('withdrawBtn').addEventListener('click', withdraw);
    window.onload = generateReferralLink; // Generate referral link on load

    // Initial draw
    draw();
</script>

</body>
</html>
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Jhaque19/Jhaque19 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
