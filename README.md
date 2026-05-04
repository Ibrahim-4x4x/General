<!--DOCTYPE html-->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade Second Exam - Dayr Abi Saeed</title>
    <style>
        /* تنسيق الصفحة العام */
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; max-width: 850px; margin: auto; padding: 20px; background-color: #f4f4f4; }
        #main-container { background: white; padding: 30px; border-radius: 10px; shadow: 0 0 10px rgba(0,0,0,0.1); position: relative; }
        
        /* إخفاء الامتحان في البداية */
        #exam-content { display: none; }

        /* شاشة القفل */
        #lock-screen {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: white; color: red; text-align: center; padding-top: 100px; z-index: 9999;
        }

        .header { text-align: center; border-bottom: 2px solid #000; margin-bottom: 20px; }
        .question-box { margin-bottom: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 8px; }
        
        /* أسطر الكتابة */
        .answer-line {
            border: none; border-bottom: 1px solid #000; width: 100%; 
            margin-top: 10px; margin-bottom: 15px; outline: none; background: transparent;
        }

        /* زر البدء وزر الحفظ */
        .btn { padding: 10px 20px; cursor: pointer; border: none; border-radius: 5px; font-size: 16px; margin: 10px; }
        .btn-start { background-color: #007bff; color: white; }
        .btn-save { background-color: #28a745; color: white; }

        @media print { .no-print { display: none; } body { background: white; } }
        
        /* منع النسخ */
        body { -webkit-user-select: none; user-select: none; }
        input[type="text"] { -webkit-user-select: text; user-select: text; }
    </style>
</head>
<body>

    <div id="lock-screen">
        <h1>⚠️ تم قفل الامتحان!</h1>
        <p>لقد حاولت مغادرة الصفحة أكثر من مرتين. لا يمكن إكمال الامتحان.</p>
        <p>مدرسة دير أبي سعيد الأساسية</p>
    </div>

   <div class="exam-container">
    <h2>Dayr Abi Saeed Primary School</h2> <h1>Second Semester / Second Exam</h1> <p><strong>Grade:</strong> 7th Grade</p> <div>
        <strong>Student Name:</strong> 
        <input type="text" id="studentName" class="answer-line" style="width: 250px;">
    </div>

    <hr>

    <div class="question-box">
        <h3>Q1. Read the text then answer: (8 Marks)</h3> <p><em>(Dialogue between Ali and Sami regarding online shopping)</em></p>
        <ol>
            <li>Why does Sami prefer online shopping? <input type="text" id="q1_1" class="answer-line"></li> <li>What if clothes don't fit? <input type="text" id="q1_2" class="answer-line"></li> <li>Two negative things about real shops? <input type="text" id="q1_3" class="answer-line"></li> <li>What happens if everyone shops online? <input type="text" id="q1_4" class="answer-line"></li> </ol>
    </div>

    <div class="question-box">
        <h3>Q2. Definitions: (4 Marks)</h3> <p>(receipt / queue / customer / second-hand)</p> a) <input type="text" id="q2_a" placeholder="Answer here...">: a person who buys something. <br>
        b) <input type="text" id="q2_b" placeholder="Answer here...">: a piece of paper you get. <br>
        c) <input type="text" id="q2_c" placeholder="Answer here...">: a line of people waiting. <br>
        d) <input type="text" id="q2_d" placeholder="Answer here...">: something used or worn. </div>

    <div class="question-box">
        <h3>Q3. Correct Verb Form: (4 Marks)</h3> 1. If I (pass/passed) the exam: <br> <label class="mcq-option"><input type="radio" name="q3_1" value="pass"> pass</label>
        <label class="mcq-option"><input type="radio" name="q3_1" value="passed"> passed</label>
        
        2. Ghada (looks/would look): <br> <label class="mcq-option"><input type="radio" name="q3_2" value="looks"> looks</label>
        <label class="mcq-option"><input type="radio" name="q3_2" value="would look"> would look</label>
    </div>

    <div class="question-box">
        <h3>Q4. Vocabulary: (4 Marks)</h3> 1. Shops <input type="text" id="q4_1" style="width: 80px;"> things to customers. <br>
        2. You can <input type="text" id="q4_2" style="width: 80px;"> money for later. <br>
        3. The teacher told us to <input type="text" id="q4_3" style="width: 80px;"> the board. <br>
        4. I'm only <input type="text" id="q4_4" style="width: 80px;">! I read your blog. </div>

    <button class="submit-btn" onclick="submitExam()">Submit & Send to Teacher</button>
    
    <div id="result" class="result-box"></div>
</div>

    <script>
        let violationCount = 0;
        const maxAllowed = 2;

        // مطابقة ID: start-area و exam-content
        function startExam() {
            // طلب ملء الشاشة
            let elem = document.documentElement;
            if (elem.requestFullscreen) { elem.requestFullscreen(); }
            
            // تبديل العرض
            document.getElementById('start-area').style.display = 'none';
            document.getElementById('exam-content').style.display = 'block';
        }

        // مراقبة مغادرة الصفحة
        document.addEventListener("visibilitychange", function() {
            // نتأكد أن الامتحان بدأ فعلاً قبل تسجيل مخالفة
            if (document.hidden && document.getElementById('exam-content').style.display === 'block') {
                violationCount++;
                
                if (violationCount < maxAllowed) {
                    alert("Warning! | تحذير: لا تخرج من الصفحة. المحاولة: " + violationCount);
                } else {
                    // قفل الامتحان - مطابقة ID: lock-screen
                    document.getElementById('exam-content').style.display = 'none';
                    document.getElementById('lock-screen').style.display = 'block';
                    if (document.exitFullscreen) { document.exitFullscreen(); }
                }
            }
        });

        // منع النقر الأيمن
        document.addEventListener('contextmenu', event => event.preventDefault());
    </script>
</body>
</html>
