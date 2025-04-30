# de
fdgdgfd
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ماشین حساب درصد | 50 دلار تا 200,000 دلار</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator {
            background: white;
            width: 350px;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        h2 {
            color: #333;
            margin-bottom: 20px;
        }
        .input-group {
            margin-bottom: 15px;
            text-align: right;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }
        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
            box-sizing: border-box;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
            transition: background 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        #result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f9f9f9;
            border-radius: 6px;
            font-size: 18px;
            font-weight: bold;
            color: #333;
        }
        .error {
            color: red;
            font-size: 14px;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <h2>محاسبه‌گر درصد (50 تا 200,000 دلار)</h2>
        
        <div class="input-group">
            <label for="amount">مبلغ (دلار):</label>
            <input type="number" id="amount" placeholder="مثلاً 50" min="50" max="200000">
            <div id="amountError" class="error"></div>
        </div>
        
        <div class="input-group">
            <label for="percent">درصد مورد نظر:</label>
            <input type="number" id="percent" placeholder="مثلاً 10" min="1" max="100">
            <div id="percentError" class="error"></div>
        </div>
        
        <button onclick="calculate()">محاسبه کن</button>
        
        <div id="result"></div>
    </div>

    <script>
        function calculate() {
            const amount = parseFloat(document.getElementById("amount").value);
            const percent = parseFloat(document.getElementById("percent").value);
            
            // اعتبارسنجی ورودی‌ها
            const amountError = document.getElementById("amountError");
            const percentError = document.getElementById("percentError");
            amountError.innerText = "";
            percentError.innerText = "";
            
            let isValid = true;
            
            if (isNaN(amount) || amount < 50 || amount > 200000) {
                amountError.innerText = "لطفاً عددی بین 50 تا 200,000 وارد کنید!";
                isValid = false;
            }
            
            if (isNaN(percent) || percent < 1 || percent > 100) {
                percentError.innerText = "لطفاً درصدی بین 1 تا 100 وارد کنید!";
                isValid = false;
            }
            
            if (!isValid) {
                document.getElementById("result").innerText = "";
                return;
            }
            
            // محاسبه نتیجه
            const result = (amount * percent) / 100;
            
            // نمایش نتیجه
            document.getElementById("result").innerHTML = `
                <p>${percent}% از ${amount.toLocaleString()} دلار = <span style="color: #4CAF50;">${result.toLocaleString()} دلار</span></p>
            `;
        }
    </script>
</body>
</html>
