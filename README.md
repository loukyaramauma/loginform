# loginform
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Registration Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .form-container {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 400px;
        }
        h2 {
            text-align: center;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
        }
        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .form-group input.error {
            border-color: red;
        }
        .form-group .error-message {
            color: red;
            font-size: 0.875em;
        }
        .form-group .success-message {
            color: green;
            font-size: 0.875em;
        }
        .form-group button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            border: none;
            color: #fff;
            border-radius: 4px;
            cursor: pointer;
        }
        .form-group button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Register</h2>
        <form id="registrationForm">
            <div class="form-group">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username">
                <div class="error-message" id="usernameError"></div>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email">
                <div class="error-message" id="emailError"></div>
            </div>
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password">
                <div class="error-message" id="passwordError"></div>
            </div>
            <div class="form-group">
                <button type="submit">Register</button>
                <div class="success-message" id="successMessage"></div>
            </div>
        </form>
    </div>

    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(event) {
            event.preventDefault();

            // Clear previous errors
            document.querySelectorAll('.error-message').forEach(el => el.textContent = '');
            document.querySelectorAll('input').forEach(el => el.classList.remove('error'));
            document.getElementById('successMessage').textContent = '';

            let isValid = true;

            const username = document.getElementById('username').value.trim();
            const email = document.getElementById('email').value.trim();
            const password = document.getElementById('password').value.trim();

            if (username === '') {
                document.getElementById('usernameError').textContent = 'Username is required.';
                document.getElementById('username').classList.add('error');
                isValid = false;
            }

            if (email === '') {
                document.getElementById('emailError').textContent = 'Email is required.';
                document.getElementById('email').classList.add('error');
                isValid = false;
            } else if (!/\S+@\S+\.\S+/.test(email)) {
                document.getElementById('emailError').textContent = 'Email is not valid.';
                document.getElementById('email').classList.add('error');
                isValid = false;
            }

            if (password === '') {
                document.getElementById('passwordError').textContent = 'Password is required.';
                document.getElementById('password').classList.add('error');
                isValid = false;
            }

            if (isValid) {
                document.getElementById('successMessage').textContent = 'Registration successful!';
            }
        });
    </script>
</body>
</html>
