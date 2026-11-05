<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mon premier site</title>

    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #ff416c, #8e44ad);
            color: white;
            text-align: center;
        }

        .container {
            padding: 100px 20px;
        }

        h1 {
            font-size: 45px;
        }

        p {
            font-size: 20px;
        }

        button {
            padding: 15px 30px;
            background: white;
            color: #8e44ad;
            border: none;
            border-radius: 30px;
            cursor: pointer;
        }
    </style>
</head>

<body>
    <div class="container">
        <h1>Bienvenue sur mon site !</h1>
        <p>Mon premier site créé avec GitHub.</p>

        <button onclick="alert('Bienvenue !')">
            Clique ici
        </button>
    </div>
</body>
</html>
