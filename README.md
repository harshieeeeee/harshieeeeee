!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dinosaur Game</title>
<style>
    body {
        margin: 0;
        padding: 0;
        overflow: hidden;
    }
    #game-container {
        width: 100%;
        height: 100vh;
        background-color: #f7f7f7;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    #dinosaur {
        width: 60px;
        height: 60px;
        background-color: #666;
        position: absolute;
        bottom: 0;
    }
    #cactus {
        width: 20px;
        height: 40px;
        background-color: #666;
        position: absolute;
        bottom: 0;
        animation: cactusMove 2s linear infinite;
    }
    @keyframes cactusMove {
        0% {
            left: 100%;
        }
        100% {
            left: -20px;
        }
    }
</style>
</head>
<body>
<div id="game-container">
    <div id="dinosaur"></div>
</div>
<script>
    const dinosaur = document.getElementById('dinosaur');
    let isJumping = false;

    document.addEventListener('keydown', (event) => {
        if (event.code === 'Space' && !isJumping) {
            isJumping = true;
            jump();
        }
    });

    function jump() {
        let position = 0;
        const jumpInterval = setInterval(() => {
            if (position === 150) {
                clearInterval(jumpInterval);
                const fallInterval = setInterval(() => {
                    if (position === 0) {
                        clearInterval(fallInterval);
                        isJumping = false;
                    }
                    position -= 5;
                    dinosaur.style.bottom = position + 'px';
                }, 20);
            }
            position += 5;
            dinosaur.style.bottom = position + 'px';
        }, 20);
    }
</script>
</body>
</html>
