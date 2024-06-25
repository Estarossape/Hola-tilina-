<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Estás bien?</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        .option {
            display: inline-block;
            margin: 10px;
            padding: 10px 20px;
            font-size: 20px;
            cursor: pointer;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .hidden {
            display: none;
        }
        .img-container {
            margin-top: 20px;
        }
        .img-container img {
            max-width: 100px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <h1>¿Estás bien?</h1>
    <p>¿Podemos hablar?</p>
    <div id="options">
        <div id="yes" class="option" onclick="handleYes()">Sí</div>
        <div id="no" class="option" onclick="handleNo()">No</div>
    </div>
    <div id="message" class="hidden">
        <p id="response-message"></p>
        <div class="img-container" id="images"></div>
    </div>

    <script>
        let noClickCount = 0;
        const yesButton = document.getElementById('yes');
        const noButton = document.getElementById('no');
        const messageDiv = document.getElementById('message');
        const responseMessage = document.getElementById('response-message');
        const imagesDiv = document.getElementById('images');

        function handleYes() {
            messageDiv.classList.remove('hidden');
            responseMessage.innerHTML = '¡Te he extrañado mucho! Volvamos a hablar.';
            imagesDiv.innerHTML = '<img src="https://media.giphy.com/media/26gsiCIKW7ANEmxKE/giphy.gif" alt="Gatito celebrando">';
        }

        function handleNo() {
            noClickCount++;
            noButton.style.fontSize = (20 - noClickCount * 2) + 'px';
            if (noClickCount === 1) {
                yesButton.style.fontSize = '22px';
            } else {
                yesButton.style.fontSize = (22 + noClickCount * 2) + 'px';
            }
            
            messageDiv.classList.remove('hidden');
            if (noClickCount === 1) {
                responseMessage.innerHTML = '¿De veras no quieres volver a hablar?';
            } else {
                responseMessage.innerHTML = '¿Seguro?';
            }

            const img = document.createElement('img');
            img.src = 'https://i.imgur.com/tE9XTbH.jpg'; // Imagen de gatito triste
            img.alt = 'Gatito triste';
            imagesDiv.appendChild(img);
        }
    </script>
</body>
</html>
