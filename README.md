<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>موقع الأسئلة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            direction: rtl;
        }
        .container {
            width: 80%;
            margin: 0 auto;
            padding: 20px;
        }
        .header {
            text-align: center;
            padding: 20px;
            background-color: #4CAF50;
            color: white;
        }
        .question-form textarea {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .submit-button, .admin-button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            margin-top: 10px;
            display: block;
        }
        .submit-button:hover, .admin-button:hover {
            background-color: #45a049;
        }
        .questions {
            margin-top: 30px;
        }
        .question {
            padding: 10px;
            background-color: #fff;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .admin-panel {
            display: none;
            margin-top: 20px;
            padding: 10px;
            background-color: #eee;
            border-radius: 8px;
        }
        .login-box {
            text-align: center;
            margin-top: 20px;
            cursor: pointer;
            color: blue;
            text-decoration: underline;
        }
        .login-form {
            display: none;
            text-align: center;
            padding: 20px;
            background-color: #f1f1f1;
            border-radius: 8px;
            margin-bottom: 30px;
        }
        .login-form input {
            padding: 10px;
            margin: 10px 0;
            width: 250px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .credit {
            text-align: center;
            margin-top: 30px;
            font-size: 14px;
            color: gray;
        }
        .links {
            text-align: center;
            margin-top: 20px;
        }
        .links a {
            color: #4CAF50;
            margin: 0 10px;
            text-decoration: none;
        }
        .links a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="header">
            <h1>موقع طرح الأسئلة</h1>
            <p>اطرح سؤالك هنا، وسيتم الإجابه عليه قريبًا!</p>
        </div>

        <div class="question-form">
            <textarea id="question" rows="4" placeholder="اكتب سؤالك هنا..."></textarea>
            <button class="submit-button" onclick="submitQuestion()">إرسال السؤال</button>
        </div>

        <div class="questions" id="questions-list">
            <!-- سيتم عرض الأسئلة هنا -->
        </div>

        <div class="links">
            <a href="https://www.instagram.com/ahamdy243?igsh=ajNjZW1tb3pmZnN2" target="_blank">انستاجرام</a>
            <a href="https://www.tiktok.com/@ahmedhamdy_06" target="_blank">تيكتوك</a>
            <a href="https://youtube.com/@ahmedhamdy1585?si=1hcfzCOXJQTi3kzF" target="_blank">يوتيوب</a>
        </div>

        <div class="login-box" onclick="showLogin()">تسجيل الدخول</div>

        <div id="login-section" class="login-form">
            <h2>تسجيل الدخول</h2>
            <input type="text" id="username" placeholder="اسم المستخدم">
            <input type="password" id="password" placeholder="كلمة المرور">
            <button onclick="login()">دخول</button>
            <p id="login-error" style="color: red; display: none;">اسم المستخدم أو كلمة المرور غير صحيحة</p>
        </div>

        <div id="admin-panel" class="admin-panel">
            <button class="admin-button" onclick="answerNextQuestion()">الإجابة عن الأسئلة غير المجاب عنها</button>
            <button class="admin-button" onclick="clearQuestions()">حذف كل الأسئلة</button>
        </div>

        <div class="credit">
            <p>تم التصميم بواسطة <a href="https://t.me/Omar_El3attar" target="_blank">عمر</a></p>
            <p style="font-size: 10px;">© جميع الحقوق محفوظة</p>
        </div>
    </div>

    <script>
        const adminUsername = "admin";
        const adminPassword = "12345";

        function showLogin() {
            var loginSection = document.getElementById('login-section');
            loginSection.style.display = loginSection.style.display === "block" ? "none" : "block";
        }

        function login() {
            var username = document.getElementById('username').value;
            var password = document.getElementById('password').value;

            if (username === adminUsername && password === adminPassword) {
                document.getElementById('login-section').style.display = 'none'; 
                document.getElementById('admin-panel').style.display = 'block';
            } else {
                document.getElementById('login-error').style.display = 'block';
            }
        }

        function submitQuestion() {
            var questionText = document.getElementById('question').value;
            if (questionText.trim() !== "") {
                var questionDiv = document.createElement('div');
                questionDiv.classList.add('question');
                questionDiv.innerHTML = `
                    <p><strong>سؤال:</strong> ${questionText}</p>
                    <p class="answer"><strong>الجواب:</strong> لم يتم الرد بعد.</p>
                `;
                document.getElementById('questions-list').appendChild(questionDiv);
                document.getElementById('question').value = "";
            } else {
                alert("يرجى كتابة سؤال أولاً!");
            }
        }

        function answerNextQuestion() {
            var unansweredQuestions = document.querySelectorAll('.question .answer');
            for (let i = 0; i < unansweredQuestions.length; i++) {
                if (unansweredQuestions[i].innerText.includes("لم يتم الرد بعد")) {
                    var answer = prompt("اكتب إجابتك لهذا السؤال:");
                    if (answer) {
                        unansweredQuestions[i].innerHTML = `<strong>الجواب:</strong> ${answer}`;
                    }
                    break;
                }
            }
        }

        function clearQuestions() {
            if (confirm("هل أنت متأكد من حذف جميع الأسئلة؟")) {
                document.getElementById('questions-list').innerHTML = "";
            }
        }
    </script>

</body>
</html>
