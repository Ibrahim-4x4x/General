<!--DOCTYPE html-->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>7th Grade Exam - Automated</title>
    <style>
        
body {
    -webkit-user-select: none; /* Chrome, Safari, Opera */
    -moz-user-select: none;    /* Firefox */
    -ms-user-select: none;     /* IE/Edge */
    user-select: none;         /* Standard */
}

.answer-line, input[type="text"] {
    -webkit-user-select: text;
    -moz-user-select: text;
    -ms-user-select: text;
    user-select: text;
}
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; max-width: 800px; margin: auto; padding: 20px; background-color: #f4f4f9; }
        .exam-container { background: white; padding: 30px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        h1, h2 { text-align: center; color: #333; }
        .question-box { margin-bottom: 25px; padding: 15px; border: 1px solid #eee; border-radius: 8px; }
        .answer-line { border: none; border-bottom: 1px dashed #000; width: 100%; outline: none; margin: 10px 0; }
        .mcq-option { display: block; margin: 5px 0; cursor: pointer; }
        .submit-btn { background-color: #25d366; color: white; padding: 15px 30px; border: none; border-radius: 5px; font-size: 18px; cursor: pointer; width: 100%; font-weight: bold; }
        .submit-btn:hover { background-color: #128c7e; }
        .result-box { margin-top: 20px; font-weight: bold; color: #d9534f; text-align: center; display: none; }
    </style>
</head>
<body>

<div class="exam-container">
    <h2>Dayr Abi Saeed Primary School</h2> <h1>Second Semester / Second Exam</h1> <p><strong>Grade:</strong> 7th Grade</p> <div>
        <strong>Student Name:</strong> 
        <input type="text" id="studentName" class="answer-line" style="width: 250px;">
    </div>

    <hr>

    <div class="question-box">
        <h3>Q1. Read the text then answer: (8 Marks)</h3> <p><em>(Dialogue between Alex and Sami regarding online shopping)</em></p>
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
function submitExam() {
    let score = 0;
    let name = document.getElementById('studentName').value;
    if(!name) { alert("Please enter your name!"); return; }

    // Q2 Logic [cite: 25, 26, 27, 28]
    if(document.getElementById('q2_a').value.toLowerCase().trim() === 'customer') score++;
    if(document.getElementById('q2_b').value.toLowerCase().trim() === 'receipt') score++;
    if(document.getElementById('q2_c').value.toLowerCase().trim() === 'queue') score++;
    if(document.getElementById('q2_d').value.toLowerCase().trim() === 'second-hand') score++;

    // Q3 Logic 
    let q3_1 = document.querySelector('input[name="q3_1"]:checked')?.value;
    let q3_2 = document.querySelector('input[name="q3_2"]:checked')?.value;
    if(q3_1 === 'pass') score++;
    if(q3_2 === 'looks') score++;

    // Q4 Logic [cite: 36, 37, 38, 42]
    if(document.getElementById('q4_1').value.toLowerCase().trim() === 'sell') score++;
    if(document.getElementById('q4_2').value.toLowerCase().trim() === 'save') score++;
    if(document.getElementById('q4_3').value.toLowerCase().trim() === 'look at') score++;
    if(document.getElementById('q4_4').value.toLowerCase().trim() === 'kidding') score++;

    let totalPossible = 10; // (Q2, Q3, Q4 partial for demo)
    let message = `Exam Result for: ${name}%0AScore: ${score}/${totalPossible}%0A(Note: Q1 needs manual grading)`;
    
    // إرسال عبر واتساب (استبدل الرقم بالرقم الفعلي للمعلم)
    let teacherPhone = "962776051524"; // اكتب الرقم هنا مع مقدمة الدولة
    window.open(`https://wa.me/${teacherPhone}?text=${message}`, '_blank');

    document.getElementById('result').style.display = 'block';
    document.getElementById('result').innerHTML = `Your score: ${score}/${totalPossible} (Sent to Teacher)`;
}
</script>
<script>
    document.addEventListener('contextmenu', event => event.preventDefault());

    document.onkeydown = function(e) {
        if (e.ctrlKey && 
            (e.keyCode === 67 || // Ctrl+C
             e.keyCode === 86 || // Ctrl+V
             e.keyCode === 85 || // Ctrl+U (View Source)
             e.keyCode === 73)) { // Ctrl+Shift+I (Inspect)
            alert("Copying or Inspecting is disabled during the exam!");
            return false;
        }
    };

    document.addEventListener("visibilitychange", function() {
        if (document.hidden) {
            alert("Warning: You left the exam page! This incident will be reported to the teacher.");
        }
    });

    function startExam() {
        let elem = document.documentElement;
        if (elem.requestFullscreen) {
            elem.requestFullscreen();
        }
        document.getElementById('exam-content').style.display = 'block';
        document.getElementById('start-btn').style.display = 'none';
    }
</script>
</body>
</html>
