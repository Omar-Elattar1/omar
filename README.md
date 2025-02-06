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
        .question-form {
            margin-bottom: 30px;
        }
        .question-form textarea {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .submit-button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
            margin-top: 10px;
        }
        .submit-button:hover {
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
        .credit {
            text-align: center;
            margin-top: 30px;
        }
        .credit p {
            font-size: 14px;
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
        /* قسم تسجيل الدخول */
        .login-form {
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
        .login-form button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }
        .login-form button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- نموذج تسجيل الدخول للأدمن -->
        <div id="login-section" class="login-form">
            <h2>تسجيل الدخول</h2>
            <input type="text" id="username" placeholder="اسم المستخدم">
            <input type="password" id="password" placeholder="كلمة المرور">
            <button onclick="login()">دخول</button>
            <p id="login-error" style="color: red; display: none;">اسم المستخدم أو كلمة المرور غير صحيحة</p>
        </div>

        <!-- لو تم تسجيل الدخول بنجاح يتم عرض المحتوى -->
        <div id="content-section" style="display: none;">
            <div class="header">
                <h1>موقع طرح الأسئلة</h1>
                <p>اطرح سؤالك هنا، وسيتم الإجابه عليه قريبًا!</p>
            </div>

            <div class="question-form">
                <label for="question">سؤالك:</label>
                <textarea id="question" rows="4" placeholder="اكتب سؤالك هنا..."></textarea>
                <button class="submit-button" onclick="submitQuestion()">إرسال السؤال</button>
            </div>

            <div class="questions" id="questions-list">
                <!-- الأسئلة ستظهر هنا -->
            </div>

            <div class="links">
                <a href="https://www.instagram.com/ahamdy243?igsh=ajNjZW1tb3pmZnN2" target="_blank">انستاجرام</a>
                <a href="https://www.tiktok.com/@ahmedhamdy_06" target="_blank">تيكتوك</a>
                <a href="https://youtube.com/@ahmedhamdy1585?si=1hcfzCOXJQTi3kzF" target="_blank">يوتيوب</a>
            </div>

            <div class="credit">
                <p>تم التصميم بواسطة <a href="https://t.me/Omar_El3attar" target="_blank">عمر</a></p>
                <p>© جميع الحقوق محفوظة</p>
            </div>
        </div>
    </div>

    <script>
        // بيانات تسجيل الدخول الخاصة بالأدمن (يمكن تعديلها حسب الحاجة)
        const adminUsername = "admin";
        const adminPassword = "12345";

        // دالة لتسجيل الدخول
        function login() {
            var username = document.getElementById('username').value;
            var password = document.getElementById('password').value;
            
            if (username === adminUsername && password === adminPassword) {
                document.getElementById('login-section').style.display = 'none'; // إخفاء قسم تسجيل الدخول
                document.getElementById('content-section').style.display = 'block'; // إظهار المحتوى
            } else {
                document.getElementById('login-error').style.display = 'block'; // إظهار رسالة خطأ إذا كانت البيانات غير صحيحة
            }
        }

        // دالة لإرسال السؤال
        function submitQuestion() {
            var question = document.getElementById('question').value;
            if (question.trim() !== "") {
                var questionsList = document.getElementById('questions-list');
                var newQuestionDiv = document.createElement('div');
                newQuestionDiv.classList.add('question');
                newQuestionDiv.innerHTML = `<p><strong>سؤال:</strong> ${question}</p><p><strong>الجواب:</strong> لم يتم الرد بعد.</p>`;
                questionsList.appendChild(newQuestionDiv);

                // مسح النص بعد الإرسال
                document.getElementById('question').value = "";
            } else {
                alert("يرجى كتابة سؤال أولاً!");
            }
        }
    </script>
</body>
</html>
