<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FareGo - Admin Login</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #1dd1a1 0%, #10ac84 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 2rem;
        }

        /* Background decorative elements */
        .bg-decoration {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
            z-index: 1;
        }

        .bg-shape {
            position: absolute;
            opacity: 0.1;
        }

        .shape-1 {
            top: 10%;
            left: 10%;
            width: 200px;
            height: 200px;
            background: #1dd1a1;
            border-radius: 50%;
        }

        .shape-2 {
            top: 60%;
            right: 15%;
            width: 150px;
            height: 150px;
            background: #fd79a8;
            border-radius: 30%;
            transform: rotate(45deg);
        }

        .shape-3 {
            bottom: 20%;
            left: 20%;
            width: 100px;
            height: 100px;
            background: #fdcb6e;
            border-radius: 20%;
        }

        .login-container {
            position: relative;
            z-index: 10;
            width: 100%;
            max-width: 450px;
        }

        .login-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
        }

        .login-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #1dd1a1, #55a3ff, #fd79a8);
        }

        .logo-section {
            text-align: center;
            margin-bottom: 2rem;
        }

        .logo {
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #1dd1a1, #10ac84);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }

        .subtitle {
            color: #636e72;
            font-size: 1rem;
            font-weight: 500;
        }

        .login-header {
            text-align: center;
            margin-bottom: 2.5rem;
        }

        .login-title {
            font-size: 2rem;
            color: #2d3436;
            font-weight: 700;
            margin-bottom: 0.5rem;
        }

        .login-description {
            color: #636e72;
            font-size: 1rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
            position: relative;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #2d3436;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .form-input {
            width: 100%;
            padding: 1rem 1.25rem;
            border: 2px solid #e9ecef;
            border-radius: 12px;
            font-size: 1rem;
            transition: all 0.3s ease;
            background: rgba(255, 255, 255, 0.8);
        }

        .form-input:focus {
            outline: none;
            border-color: #1dd1a1;
            background: white;
            box-shadow: 0 0 0 3px rgba(29, 209, 161, 0.1);
        }

        .form-input::placeholder {
            color: #999;
        }

        .password-toggle {
            position: absolute;
            right: 1rem;
            top: 50%;
            transform: translateY(-50%);
            background: none;
            border: none;
            color: #636e72;
            cursor: pointer;
            font-size: 1rem;
            padding: 0.25rem;
            border-radius: 4px;
            transition: color 0.3s ease;
        }

        .password-toggle:hover {
            color: #1dd1a1;
        }

        .login-button {
            width: 100%;
            padding: 1rem 2rem;
            background: linear-gradient(135deg, #1dd1a1, #10ac84);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 1.5rem;
        }

        .login-button:hover {
            background: linear-gradient(135deg, #10ac84, #0d9970);
        }

        .login-button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .form-options {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            font-size: 0.9rem;
        }

        .remember-me {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: #636e72;
        }

        .remember-me input[type="checkbox"] {
            transform: scale(1.2);
        }

        .forgot-password {
            color: #1dd1a1;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .forgot-password:hover {
            color: #10ac84;
            text-decoration: underline;
        }

        .divider {
            text-align: center;
            margin: 2rem 0;
            position: relative;
            color: #636e72;
            font-size: 0.9rem;
        }

        .divider::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 1px;
            background: #e9ecef;
            z-index: 1;
        }

        .divider span {
            background: rgba(255, 255, 255, 0.95);
            padding: 0 1rem;
            position: relative;
            z-index: 2;
        }

        .social-login {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .social-btn {
            flex: 1;
            padding: 0.75rem;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            background: white;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
            font-weight: 500;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .social-btn:hover {
            border-color: #1dd1a1;
        }

        .footer-links {
            text-align: center;
            color: #636e72;
            font-size: 0.9rem;
        }

        .footer-links a {
            color: #1dd1a1;
            text-decoration: none;
            font-weight: 500;
        }

        .footer-links a:hover {
            text-decoration: underline;
        }

        .error-message {
            background: #fadbd8;
            color: #e74c3c;
            padding: 0.75rem 1rem;
            border-radius: 8px;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            border-left: 4px solid #e74c3c;
            display: none;
        }

        .success-message {
            background: #d1f2eb;
            color: #10ac84;
            padding: 0.75rem 1rem;
            border-radius: 8px;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            border-left: 4px solid #10ac84;
            display: none;
        }

        .loading {
            display: none;
            width: 20px;
            height: 20px;
            border: 2px solid #ffffff40;
            border-top: 2px solid #ffffff;
            border-radius: 50%;
            margin-left: 0.5rem;
        }

        /* Responsive design */
        @media (max-width: 768px) {
            body {
                padding: 1rem;
            }

            .login-card {
                padding: 2rem;
                border-radius: 16px;
            }

            .logo {
                font-size: 2rem;
            }

            .login-title {
                font-size: 1.75rem;
            }

            .form-options {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }

            .social-login {
                flex-direction: column;
            }
        }

        @media (max-width: 480px) {
            .login-card {
                padding: 1.5rem;
            }

            .logo {
                font-size: 1.75rem;
            }

            .login-title {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="bg-decoration">
        <div class="bg-shape shape-1"></div>
        <div class="bg-shape shape-2"></div>
        <div class="bg-shape shape-3"></div>
    </div>

    <div class="login-container">
        <div class="login-card">
            <div class="logo-section">
                <div class="logo">FareGo</div>
                <div class="subtitle">Transportation Management System</div>
            </div>

            <div class="login-header">
                <h1 class="login-title">Welcome Back</h1>
                <p class="login-description">Sign in to access your admin dashboard</p>
            </div>

            <div class="error-message" id="errorMessage">
                Invalid username or password. Please try again.
            </div>

            <div class="success-message" id="successMessage">
                Login successful! Redirecting to dashboard...
            </div>

            <form id="loginForm">
                <div class="form-group">
                    <label class="form-label">Username</label>
                    <input 
                        type="text" 
                        class="form-input" 
                        id="username"
                        placeholder="Enter your username"
                        required
                    >
                </div>

                <div class="form-group">
                    <label class="form-label">Password</label>
                    <div style="position: relative;">
                        <input 
                            type="password" 
                            class="form-input" 
                            id="password"
                            placeholder="Enter your password"
                            required
                        >
                        <button type="button" class="password-toggle" onclick="togglePassword()">
                            <span id="toggleIcon">👁️</span>
                        </button>
                    </div>
                </div>

                <div class="form-options">
                    <label class="remember-me">
                        <input type="checkbox" id="rememberMe">
                        Remember me
                    </label>
                    <a href="#" class="forgot-password" onclick="showForgotPassword()">Forgot password?</a>
                </div>

                <button type="submit" class="login-button" id="loginBtn">
                    Sign In
                </button>
            </form>



            <div class="footer-links">
                Need help? <a href="#" onclick="showSupport()">Contact Support</a>
            </div>
        </div>
    </div>

    <script>
        // Form validation and submission
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const loginBtn = document.getElementById('loginBtn');
            const loading = document.getElementById('loading');
            const errorMessage = document.getElementById('errorMessage');
            const successMessage = document.getElementById('successMessage');

            // Hide previous messages
            errorMessage.style.display = 'none';
            successMessage.style.display = 'none';

            // Basic validation
            if (!username || !password) {
                showError('Please fill in all fields');
                return;
            }

            // Show loading state
            loginBtn.disabled = true;
            loginBtn.textContent = 'Signing In...';

            // Simulate login process
            setTimeout(() => {
                // Demo credentials - in real app, this would be an API call
                if (username === 'admin' && password === 'admin123') {
                    showSuccess('Login successful! Redirecting...');
                    setTimeout(() => {
                        // Redirect to dashboard
                        window.location.href = '#dashboard';
                        // In real app: window.location.href = '/dashboard';
                    }, 1000);
                } else {
                    showError('Invalid username or password');
                    resetLoginButton();
                }
            }, 1000);
        });

        function showError(message) {
            const errorMessage = document.getElementById('errorMessage');
            errorMessage.textContent = message;
            errorMessage.style.display = 'block';
            resetLoginButton();
        }

        function showSuccess(message) {
            const successMessage = document.getElementById('successMessage');
            successMessage.textContent = message;
            successMessage.style.display = 'block';
        }

        function resetLoginButton() {
            const loginBtn = document.getElementById('loginBtn');
            
            loginBtn.disabled = false;
            loginBtn.textContent = 'Sign In';
        }

        function togglePassword() {
            const passwordInput = document.getElementById('password');
            const toggleIcon = document.getElementById('toggleIcon');
            
            if (passwordInput.type === 'password') {
                passwordInput.type = 'text';
                toggleIcon.textContent = '🙈';
            } else {
                passwordInput.type = 'password';
                toggleIcon.textContent = '👁️';
            }
        }

        function showForgotPassword() {
            alert('Forgot password functionality would open a password recovery modal or redirect to a recovery page');
        }

        function showSupport() {
            alert('Support contact: admin@farego.com\nPhone: +1 (555) 123-4567');
        }

        // Demo credentials helper
        document.addEventListener('DOMContentLoaded', function() {
            // Add demo credentials hint
            const loginCard = document.querySelector('.login-card');
            const demoHint = document.createElement('div');
            demoHint.innerHTML = `
                <div style="background: #e3f2fd; padding: 1rem; border-radius: 8px; margin-bottom: 1rem; font-size: 0.85rem; color: #1565c0; text-align: center;">
                    <strong>Demo Credentials:</strong><br>
                    Username: admin | Password: admin123
                </div>
            `;
            loginCard.insertBefore(demoHint, document.getElementById('loginForm'));
        });

        // Handle Enter key
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                document.getElementById('loginForm').dispatchEvent(new Event('submit'));
            }
        });
    </script>
</body>
</html>
