<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dires Login</title>
    <style>
        body {
            background-color: #333;
            color: #fff;
            font-family: sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        .container {
            background-color: #222;
            padding: 30px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
            text-align: center;
        }

        h1 {
            margin-bottom: 20px;
        }

        input[type="text"],
        input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #555;
            border-radius: 3px;
            background-color: #444;
            color: #fff;
        }

        input[type="text"]:focus,
        input[type="password"]:focus {
            outline: none;
            border-color: #888;
        }

        .checkbox {
            display: inline-block;
            margin-bottom: 10px;
        }

        .checkbox input[type="checkbox"] {
            margin-right: 5px;
        }

        button {
            background-color: #007bff;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0069d9;
        }

        a {
            color: #007bff;
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }

        .footer {
            margin-top: 20px;
            font-size: 12px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Dires</h1>
        <img src="logo.svg" alt="Dires Logo">
        <p>Sign in to start your session</p>
        <form>
            <input type="text" placeholder="Email or Username" required>
            <input type="password" placeholder="Password" required>
            <div class="checkbox">
                <input type="checkbox" id="rememberMe">
                <label for="rememberMe">Remember Me</label>
            </div>
            <button type="submit">Sign In</button>
            <a href="#">Forgot Your Password?</a>
            <a href="#">Register a new membership</a>
        </form>
        <div class="footer">
            <a href="#">Imprint</a> | <a href="#">Terms of Service</a>
        </div>
    </div>
</body>
</html>