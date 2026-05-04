<!DOCTYPE html>
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

    <div id="main-container">
        <div id="start-area" style="text-align: center; padding: 50px;">
            <h2>Second Exam - 7th Grade</h2>
            <p>يرجى العلم أن مغادرة الصفحة ستؤدي لقفل الامتحان.</p>
            <button class="btn btn-start" onclick="startExam()">Start Exam Now | ابدأ الامتحان</button>
        </div>

        <div id="exam-content">
            <button class="btn btn-save no-print" onclick="window.print()">Save as PDF / Print</button>
            
            <div class="header">
                <h1>Second Semester / Second Exam</h1>
                <h2>Dayr Abi Saeed Primary School</h2>
                <div style="display: flex; justify-content: space-between; margin-top: 10px;">
                    <div><strong>Name:</strong> <input type="text" placeholder="Write name..." style="border:none; border-bottom:1px solid #000; width:200px; outline:none;"></div>
                    <div><strong>Grade:</strong> 7th Grade</div>
                </div>
            </div>

            <div class="question-box">
                <h3>Q1. Answer the questions based on the dialogue:</h3>
                <p>1. Why does Sami prefer online shopping?</p>
                <input type="text" class="answer-line">
                <p>2. What does Sami do if clothes don't fit?</p>
                <input type="text" class="answer-line">
            </div>

            <div class="question-box">
                <h3>Q3. Choose the correct verb:</h3>
                <p>1. If I ( <input type="radio" name="q1"> pass / <input type="radio" name="q1"> passed ) the exam, I'll celebrate.</p>
                <p>2. If I ( <input type="radio" name="q2"> could / <input type="radio" name="q2"> can ) travel back in time, I'd go to Ancient Jordan.</p>
            </div>

            <div style="text-align: center; font-weight: bold;">Good Luck!</div>
        </div>
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
