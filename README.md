<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aanmelden bij uw account</title>
    <!-- Favicon voor het tabblad -->
    <link rel="icon" href="https://www.freepnglogos.com/uploads/image-microsoft-logo--5.png" type="image/png">
    <style>
       /* Reset default styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-image: url('https://aadcdn.msauth.net/shared/1.0/content/images/backgrounds/2_11d9e3bcdfede9ce5ce5ace2d129f1c4.svg');
    background-size: cover;
    background-position: center;
    color: #333;
}

/* Container for the login form */
.login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
}

.login-box {
    width: 440px;
    height: 338px;
    padding: 30px;
    background: #ffffff;
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
    text-align: left;
    border-radius: 0;
    display: flex;
    flex-direction: column;
}

.logo img {
    width: 110px;
    margin-bottom: 1rem;
}

.login-box h2 {
    font-size: 1.4rem;
    color: #000;
    margin-bottom: 1rem;
    font-weight: 600;
}

.input-group {
    margin-bottom: 1.25rem;
}

.input-group input {
    width: 100%;
    padding: 0.75rem;
    border: none;
    border-bottom: 1px solid #000;
    font-size: 1rem;
    color: #333;
    background: #fff;
    transition: border-color 0.3s ease;
}

.input-group input:focus {
    border-bottom: 1px solid #0078d4;
    outline: none;
}

.input-group input::placeholder {
    color: #999;
}

.button-group {
    display: flex;
    gap: 0.5rem;
    justify-content: flex-end;
    margin-top: 1rem;
}

.back-button, .next-button {
    width: 108px;
    height: 32px;
    font-size: 0.9rem;
    border: none;
    cursor: pointer;
    font-weight: normal;
}

.back-button {
    background: #f0f0f0;
    color: #333;
    transition: background-color 0.3s ease;
}

.next-button {
    background: #0078d4;
    color: #ffffff;
    transition: background-color 0.3s ease;
}

.back-button:hover {
    background: #e1e1e1;
}

.next-button:hover {
    background: #005a9e;
}

/* Account options styling */
.account-options {
    font-size: 0.9rem;
    margin-top: 1rem;
    color: #000;
}

.account-options span {
    color: #000;
}

.create-account {
    color: #0078d4;
    text-decoration: none;
}

.forgot-password {
    display: block;
    font-size: 0.9rem;
    color: #0078d4;
    text-decoration: none;
    margin-top: 0.5rem;
}

.error-message {
    color: #d9534f;
    font-size: 0.9rem;
    margin-top: 1rem;
    display: none;
}

/* Options box styling */
.options-box {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 440px;
    height: 48px;
    background: #ffffff;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    border-radius: 0;
    cursor: pointer;
}

.options-box:hover {
    background: #f0f0f0;
}

.options-icon {
    width: 20px;
    height: 20px;
    margin-right: 8px;
}

.options-box span {
    font-size: 0.9rem;
    color: #000;
}

@media (max-width: 480px) {
    .login-box, .options-box {
        width: 90%;
        padding: 1.5rem;
    }
}

    </style>
</head>
<body>
    <div class="login-container">
        <div class="login-box">
            <div class="logo">
                <img src="https://aadcdn.msauth.net/shared/1.0/content/images/microsoft_logo_564db913a7fa0ca42727161c6d031bef.svg" alt="Microsoft Logo">
            </div>
            <h2>Aanmelden</h2>
            <form id="loginForm" onsubmit="handleSubmit(event)">
                <div class="input-group" id="emailGroup">
                    <input type="email" id="email" name="email" placeholder="E-mailadres, telefoonnummer of skype-naam" required>
                </div>
                <div class="input-group" id="passwordGroup" style="display: none;">
                    <input type="password" id="password" name="password" placeholder="Wachtwoord" required>
                </div>
                
                <p class="account-options">
                    <span>Geen account?</span>
                    <a href="https://signup.live.com/signup" class="create-account">Maak nu een account</a>
                </p>
                <a href="#" class="forgot-password">Hebt u geen toegang tot het account?</a>
                
                <div class="button-group">
                    <button type="button" class="back-button" onclick="window.location.href='https://account.microsoft.com/account/Account'">Vorige</button>
                    <button type="button" class="next-button" onclick="showPasswordField()">Volgende</button>
                </div>
            </form>
            <p class="error-message" id="errorMessage"></p>
        </div>
        
        <div class="options-box" onclick="window.location.href='https://login.microsoft.com/common/fido/get?uiflavor=Host'">
            <img src="https://aadcdn.msauth.net/shared/1.0/content/images/signin-options_3e3f6b73c3f310c31d2c4d131a8ab8c6.svg" alt="Aanmeldingsopties Icon" class="options-icon">
            <span class="options-text">Aanmeldingsopties</span>
        </div>
    </div>
    
    <script>
        // JavaScript code
        function showPasswordField() {
            const emailGroup = document.getElementById('emailGroup');
            const passwordGroup = document.getElementById('passwordGroup');
            const nextButton = document.querySelector('.next-button');
            
            if (emailGroup.style.display !== 'none' && document.getElementById('email').value !== '') {
                emailGroup.style.display = 'none';
                passwordGroup.style.display = 'block';
                nextButton.textContent = 'Aanmelden';
            } else if (document.getElementById('password').value !== '') {
                // Na invullen van het wachtwoord, naar volgende pagina navigeren
                window.location.href = 'https://myaccount.microsoft.com/?ref=amc';
            }
        }
        
        function handleSubmit(event) {
            event.preventDefault();
            showPasswordField();
        }
    </script>
</body>
</html>
