<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Meme Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background-color: #f0f0f0;
            background-size: cover;
            background-position: center;
            transition: filter 0.5s ease;
        }
        img {
            max-width: 100%;
            height: auto;
            margin-top: 20px;
            position: relative;
            z-index: 1;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            margin-top: 20px;
            position: relative;
            z-index: 1;
        }
        .blur-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            filter: blur(5px);
            background-size: cover;
            background-position: center;
        }
    </style>
</head>
<body>

    <h1>Random Meme Generator</h1>
    <div class="blur-background" id="blurBackground"></div>
    <img id="memeImage" src="" alt="Random Meme">
    <br>
    <button onclick="getRandomMeme()">Get Random Meme</button>

    <script>
        async function getRandomMeme() {
            const response = await fetch('https://meme-api.com/gimme');
            const data = await response.json();
            document.getElementById('memeImage').src = data.url;
            document.getElementById('blurBackground').style.backgroundImage = `url(${data.url})`;
        }

        // Load a meme when the page is first opened
        window.onload = getRandomMeme;
    </script>

</body>
</html>
