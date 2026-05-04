<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade Second Exam - Dayr Abi Saeed</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; max-width: 850px; margin: auto; padding: 20px; background-color: #f4f4f4; -webkit-user-select: none; user-select: none; }
        #main-container { background: white; padding: 30px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); position: relative; }
        #exam-content { display: none; }
        #lock-screen { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: white; color: red; text-align: center; padding-top: 50px; z-index: 9999; }
        .header { text-align: center; border-bottom: 2px solid #000; margin-bottom: 20px; }
        .question-box { margin-bottom: 30px; padding: 15px; border: 1px solid #ddd; border-radius: 8px; }
        .answer-line { border: none; border-bottom: 1px solid #000; width: 100%; margin-top: 10px; margin-bottom: 15px; outline: none; background: transparent; font-size: 16px; }
        input[type="text"] { -webkit-user-select: text; user-select: text; }
        .btn { padding: 10px 20px; cursor: pointer; border: none; border-radius: 5px; font-size: 16px; margin: 10px; font-weight: bold; }
        .btn-start { background-color: #007bff; color: white; width: 250px; }
        .btn-submit { background-color: #28a745; color: white; width: 100%; margin-top: 20px; }
        .dialogue { background-color: #f9f9f9; padding: 15px; border-left: 5px solid #ccc; margin: 10px 0; font-style: italic; }
    </style>
</head>
<body>

<div id="lock-screen">
    <h1>⚠️ تم قفل الامتحان!</h1>
    <p style="font-size:20px; color:black;">مدرسة دير أبي سعيد الأساسية [cite: 2]</p>
    <p>لقد تجاوزت المحاولات المسموحة أو تم تسليم الامتحان سابقاً.</p>
    <div style="margin-top: 30px; border: 2px solid #ccc; display: inline-block; padding: 20px; border-radius: 10px;">
        <p style="color: blue;">فتح الامتحان يحتاج رمز المعلم:</p>
        <input type="password" id="teacher-password" placeholder="الرمز..." style="padding: 10px;">
        <button class="btn btn-start" onclick="unlockExam()" style="width: auto;">فتح القفل</button>
    </div>
</div>

<div id="main-container">
    <div id="start-area" style="text-align: center; padding: 50px;">
        <h2>Second Semester / Second Exam</h2>
        <h3>7th Grade [cite: 4]</h3>
        <button class="btn btn-start" onclick="startExam()">Start Exam Now | ابدأ الامتحان</button>
    </div>

    <div id="exam-content">
        <div class="header">
            <h1>Second Semester / Second Exam [cite: 1]</h1>
            <h2>Dayr Abi Saeed Primary School [cite: 2]</h2>
            <div><strong>Name:</strong> <input type="text" id="studentName" class="answer-line" style="width:250px;"></div>
        </div>

        <div class="question-box">
            <h3>Q2. Definitions: (4 Marks)</h3>
            a) <input type="text" id="q2_a" style="width: 120px;"> : a person who buys something[cite: 25].<br>
            b) <input type="text" id="q2_b" style="width: 120px;"> : a piece of paper you get[cite: 26].<br>
            c) <input type="text" id="q2_c" style="width: 120px;"> : a line of people waiting[cite: 27].<br>
            d) <input type="text" id="q2_d" style="width: 120px;"> : something used or worn[cite: 28].
        </div>

        <div class="question-box">
            <h3>Q3. Correct Verb Form: (2 Marks)</h3>
            1. If I ( <input type="radio" name="q3_1" value="pass"> pass / <input type="radio" name="q3_1" value="passed"> passed ) the exam[cite: 30].<br>
            2. Ghada always ( <input type="radio" name="q3_2" value="looks"> looks / <input type="radio" name="q3_2" value="would look"> would look )[cite: 31].
        </div>

        <button class="btn btn-submit" onclick="submitAndEmail()">Submit & Send Email | تسليم وإرسال إيميل</button>
    </div>
</div>

<script>
    const TEACHER_EMAIL = "teacher@example.com"; // *** ضع إيميل المعلم هنا ***
    const TEACHER_SECRET = "0101"; 
    let violationCount = 0;

    window.onload = function() {
        if (localStorage.getItem("exam_status") === "locked") showLockScreen();
    };

    function startExam() {
        if (localStorage.getItem("exam_status") === "locked") return showLockScreen();
        document.documentElement.requestFullscreen?.();
        document.getElementById('start-area').style.display = 'none';
        document.getElementById('exam-content').style.display = 'block';
    }

    function submitAndEmail() {
        let score = 0;
        let name = document.getElementById('studentName').value;
        if (!name) return alert("Please enter your name!");

        // تصحيح السؤال الثاني [cite: 25, 26, 27, 28]
        if(document.getElementById('q2_a').value.toLowerCase().trim() === 'customer') score++;
        if(document.getElementById('q2_b').value.toLowerCase().trim() === 'receipt') score++;
        if(document.getElementById('q2_c').value.toLowerCase().trim() === 'queue') score++;
        if(document.getElementById('q2_d').value.toLowerCase().trim() === 'second-hand') score++;

        // تصحيح السؤال الثالث [cite: 30, 31]
        if(document.querySelector('input[name="q3_1"]:checked')?.value === 'pass') score++;
        if(document.querySelector('input[name="q3_2"]:checked')?.value === 'looks') score++;

        let total = 6; // مجموع علامات الأسئلة المؤتمتة
        let subject = encodeURIComponent(`Exam Result: ${name} - 7th Grade`);
        let body = encodeURIComponent(`Student Name: ${name}\nFinal Score: ${score}/${total}\n\nAnswers:\nQ2: ${document.getElementById('q2_a').value}, ${document.getElementById('q2_b').value}, ${document.getElementById('q2_c').value}, ${document.getElementById('q2_d').value}`);

        // فتح البريد الإلكتروني
        window.location.href = `mailto:${TEACHER_EMAIL}?subject=${subject}&body=${body}`;

        // قفل الامتحان بعد التسليم
        localStorage.setItem("exam_status", "locked");
        alert("Exam Submitted! Please send the email that just opened.");
        location.reload();
    }

    function showLockScreen() {
        document.getElementById('exam-content').style.display = 'none';
        document.getElementById('start-area').style.display = 'none';
        document.getElementById('lock-screen').style.display = 'block';
    }

    function unlockExam() {
        if (document.getElementById('teacher-password').value === TEACHER_SECRET) {
            localStorage.removeItem("exam_status");
            location.reload();
        } else {
            alert("Wrong Password!");
        }
    }

    document.addEventListener("visibilitychange", function() {
        if (document.hidden && document.getElementById('exam-content').style.display === 'block') {
            violationCount++;
            if (violationCount >= 2) {
                localStorage.setItem("exam_status", "locked");
                showLockScreen();
            } else {
                alert("Warning: Don't leave the page!");
            }
        }
    });
</script>
</body>
</html>
