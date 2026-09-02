[index.html.html](https://github.com/user-attachments/files/31736800/index.html.html)

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ابحث بالبريد الإلكتروني</title>
<style>
  * { box-sizing: border-box; }
  body {
    font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
    padding: 20px;
  }
  .card {
    background: #fff;
    border-radius: 16px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.25);
    padding: 40px;
    width: 100%;
    max-width: 420px;
    text-align: center;
  }
  h1 {
    font-size: 22px;
    color: #333;
    margin-bottom: 24px;
  }
  input[type="email"] {
    width: 100%;
    padding: 14px 16px;
    font-size: 16px;
    border: 2px solid #e0e0e0;
    border-radius: 10px;
    outline: none;
    transition: border-color 0.2s;
    text-align: center;
    direction: ltr;
  }
  input[type="email"]:focus {
    border-color: #764ba2;
  }
  button {
    margin-top: 16px;
    width: 100%;
    padding: 14px;
    font-size: 16px;
    font-weight: bold;
    color: #fff;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s;
  }
  button:hover { opacity: 0.9; }
  #result {
    margin-top: 24px;
    font-size: 20px;
    font-weight: bold;
    min-height: 30px;
    padding: 14px;
    border-radius: 10px;
    display: none;
  }
  #result.found {
    display: block;
    background: #e8f5e9;
    color: #2e7d32;
    border: 2px solid #a5d6a7;
  }
  #result.not-found {
    display: block;
    background: #ffebee;
    color: #c62828;
    border: 2px solid #ef9a9a;
  }
</style>
</head>
<body>

<div class="card">
  <h1>يرجى إدخال بريدك الإلكتروني</h1>
  <input type="email" id="emailInput" placeholder="example@email.com" required>
  <button onclick="showWord()">عرض</button>
  <div id="result"></div>
</div>

<script>
  // ==============================================
  // عدّل هنا: ضع كل بريد إلكتروني والكلمة المقابلة له
  // ==============================================
  const emailWordMap = {
    "ahmed@example.com": "مبروك!",
    "sara@example.com": "أهلاً بيكِ",
    "test@example.com": "كلمة تجريبية"
  };
  // ==============================================

  function showWord() {
    const emailInput = document.getElementById('emailInput');
    const email = emailInput.value.trim().toLowerCase();
    const resultDiv = document.getElementById('result');

    // نبحث بدون حساسية لحالة الأحرف
    const match = Object.keys(emailWordMap).find(
      key => key.toLowerCase() === email
    );

    if (match) {
      resultDiv.textContent = emailWordMap[match];
      resultDiv.className = 'found';
    } else {
      resultDiv.textContent = 'لا توجد بيانات مرتبطة بهذا البريد الإلكتروني';
      resultDiv.className = 'not-found';
    }
  }

  // السماح بالضغط على Enter
  document.getElementById('emailInput').addEventListener('keypress', function(e) {
    if (e.key === 'Enter') showWord();
  });
</script>

</body>
</html>
