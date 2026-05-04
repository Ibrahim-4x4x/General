<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade Second Exam - Dayr Abi Saeed</title>
    <style>
        /* تنسيق المظهر العام */
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            line-height: 1.6; 
            max-width: 850px; 
            margin: auto; 
            padding: 20px; 
            background-color: #f4f4f4; 
            /* منع تحديد النص للحماية */
            -webkit-user-select: none; 
            user-select: none; 
        }
        
        #main-container { 
            background: white; 
            padding: 30px; 
            border-radius: 10px; 
            box-shadow: 0 0 10px rgba(0,0,0,0.1); 
            position: relative; 
        }
        
        /* إخفاء الامتحان في البداية */
        #exam-content { display: none; }

        /* شاشة القفل عند الغش */
        #lock-screen {
            display: none; 
            position: fixed; 
            top: 0; 
            left: 0; 
            width: 100%; 
            height: 100%;
            background: white; 
            color: red; 
            text-align: center; 
            padding-top: 100px; 
            z-index: 9999;
        }

        .header { text-align: center; border-bottom: 2px solid #000; margin-bottom: 20px; }
        .question-box { margin-bottom: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 8px; }
        
        /* أسطر الكتابة */
        .answer-line {
            border: none; 
            border-bottom: 1px solid #000; 
            width: 100%; 
            margin-top: 10px; 
            margin-bottom: 15px; 
            outline: none; 
            background: transparent;
            font-size: 16px;
        }

        /* السماح بالكتابة في الخانات */
        input[type="text"] { -webkit-user-select: text; user-select: text; }

        .btn { padding: 10px 20px; cursor: pointer; border: none; border-radius: 5px; font-size: 16px; margin: 10px; font-weight: bold; }
        .btn-start { background-color: #007bff; color: white; width: 250px; }
        .btn-save { background-color: #28a745; color: white; }
        .btn-submit { background-color: #dc3545; color: white; width: 100%; margin-top: 20px; }

        .dialogue { background-color: #f9f9f9; padding: 15px; border-left: 5px solid #ccc; margin: 10px 0; font-style: italic; }

        @media print { 
            .no-print { display: none; } 
            body { background: white; padding: 0; }
            #main-container { box-shadow: none; border: none; }
        }
    </style>
</head>
<body>

    <div id="lock-screen">
        <h1>⚠️ تم قفل الامتحان!</h1>
        <p style="font-size: 20px; color: black;">لقد حاولت مغادرة الصفحة أكثر من مرتين. لا يمكن إكمال الامتحان.</p>
        <div style="font-weight:bold; margin-top:20px;">مدرسة دير أبي سعيد الأساسية</div>
    </div>

    <div id="main-container">
        <div id="start-area" style="text-align: center; padding: 50px;">
            <h2>Second Semester / Second Exam</h2>
            <h3>7th Grade</h3>
            <p style="color: red; font-weight: bold;">تحذير: مغادرة الصفحة أو تبديل التبويب سيؤدي لقفل الامتحان تلقائياً.</p>
            <button class="btn btn-start" onclick="startExam()">Start Exam Now | ابدأ الامتحان</button>
        </div>

        <div id="exam-content">
            <div class="no-print" style="text-align: right;">
                <button class="btn btn-save" onclick="window.print()">Save as PDF / Print</button>
            </div>

            <div class="header">
                <h1>Second Semester / Second Exam</h1>
                <h2>Dayr Abi Saeed Primary School</h2>
                <div style="display: flex; justify-content: space-between; margin-top: 10px; padding: 10px;">
                    <div><strong>Name:</strong> <input type="text" id="studentName" placeholder="Type your name..." style="border:none; border-bottom:1px solid #000; width:250px; outline:none;"></div>
                    <div><strong>Grade:</strong> 7th Grade</div>
                </div>
            </div>

            <div class="question-box">
                <h3>Q1. Read the following text then answer the questions below: (8 Marks)</h3>
                <div class="dialogue">
                    Alex: Hey, Sami! Do you want to come shopping with me?<br>
                    Sami: No chance! I don't like shopping... (etc.)
                </div>
                <p>1. Why does Sami prefer online shopping over going to real shops?</p>
                <input type="text" id="q1_1" class="answer-line">
                <p>2. What does Sami do if the clothes he buys online don't fit him?</p>
                <input type="text" id="q1_2" class="answer-line">
            </div>

            <div class="question-box">
                <h3>Q2. Fill the blank with the correct word: (4 Marks)</h3>
                <p style="text-align: center;">(receipt / queue / customer / second-hand)</p>
                a) <input type="text" id="q2_a" style="width: 150px; border:none; border-bottom:1px solid #000; outline:none;"> : a person who buys something in a shop.<br>
                b) <input type="text" id="q2_b" style="width: 150px; border:none; border-bottom:1px solid #000; outline:none;"> : a piece of paper you get when you buy something.<br>
                c) <input type="text" id="q2_c" style="width: 150px; border:none; border-bottom:1px solid #000; outline:none;"> : a line of people waiting for something.<br>
                d) <input type="text" id="q2_d" style="width: 150px; border:none; border-bottom:1px solid #000; outline:none;"> : something that has already been used.
            </div>

            <div class="question-box">
                <h3>Q3. Choose the correct verb form: (4 Marks)</h3>
                <p>1. If I ( <input type="radio" name="q3_1" value="pass"> pass / <input type="radio" name="q3_1" value="passed"> passed ) the exam, I'll celebrate.</p>
                <p>2. If Ghada needs to buy something, she always ( <input type="radio" name="q3_2" value="looks"> looks / <input type="radio" name="q3_2" value="would look"> would look ) for the best price.</p>
            </div>

            <div class="question-box">
                <h3>Q4. Complete the sentences: (4 Marks)</h3>
                1. Shops <input type="text" id="q4_1" style="width: 100px; border:none; border-bottom:1px solid #000; outline:none;"> things to customers.<br>
                2. You can <input type="text" id="q4_2" style="width: 100px; border:none; border-bottom:1px solid #000; outline:none;"> money for later.
            </div>

            <button class="btn btn-submit no-print" onclick="submitExam()">Submit Exam | تسليم الامتحان</button>
            <div id="result-display" style="text-align:center; font-weight:bold; margin-top:20px; color: green; display:none;"></div>
            
            <div style="text-align: center; font-weight: bold; margin-top: 30px;">Good Luck!</div>
        </div>
    </div>

    <script>
        let violationCount = 0;
        const maxAllowed = 2;

        // بدء الامتحان وتفعيل وضع ملء الشاشة
        function startExam() {
            let elem = document.documentElement;
            if (elem.requestFullscreen) { elem.requestFullscreen(); }
            else if (elem.webkitRequestFullscreen) { elem.webkitRequestFullscreen(); }

            document.getElementById('start-area').style.display = 'none';
            document.getElementById('exam-content').style.display = 'block';
        }

        // نظام الحماية من الغش ومغادرة الصفحة
        document.addEventListener("visibilitychange", function() {
            if (document.hidden && document.getElementById('exam-content').style.display === 'block') {
                violationCount++;
                if (violationCount < maxAllowed) {
                    alert("Warning! | تحذير: لا تخرج من الصفحة. المحاولة رقم: " + violationCount);
                } else {
                    lockExam();
                }
            }
        });

        function lockExam() {
            document.getElementById('exam-content').style.display = 'none';
            document.getElementById('lock-screen').style.display = 'block';
            if (document.exitFullscreen) { document.exitFullscreen(); }
        }

        // تسليم الامتحان وحساب العلامة
        function submitExam() {
            let score = 0;
            let name = document.getElementById('studentName').value;
            if (!name) { alert("Please enter your name!"); return; }

            // منطق التصحيح التلقائي (أمثلة)
            if(document.getElementById('q2_a').value.toLowerCase().trim() === 'customer') score++;
            if(document.getElementById('q2_b').value.toLowerCase().trim() === 'receipt') score++;
            
            let q3_1 = document.querySelector('input[name="q3_1"]:checked')?.value;
            if(q3_1 === 'pass') score++;

            alert("Exam submitted successfully! Score: " + score);
            document.getElementById('result-display').innerHTML = "Thank you " + name + ". Your auto-graded score is: " + score;
            document.getElementById('result-display').style.display = 'block';
        }

        // منع النقر الأيمن واختصارات الكيبورد
        document.addEventListener('contextmenu', event => event.preventDefault());
        document.onkeydown = function(e) {
            if (e.ctrlKey && (e.keyCode === 67 || e.keyCode === 86 || e.keyCode === 85 || e.keyCode === 73)) {
                return false;
            }
        };
    </script>
</body>
</html>
