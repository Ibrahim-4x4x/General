<!--DOCTYPE html-->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade English - Unit 7 Lesson 2</title>
    <style>
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            line-height: 1.6; 
            max-width: 850px; 
            margin: auto; 
            padding: 20px; 
            background-color: #e9ecef; 
            -webkit-user-select: none; 
            user-select: none; 
        }
        
        #main-container { 
            background: white; 
            padding: 30px; 
            border-radius: 15px; 
            box-shadow: 0 4px 15px rgba(0,0,0,0.1); 
            position: relative; 
        }
        
        #exam-content { display: none; }

        #lock-screen {
            display: none; 
            position: fixed; 
            top: 0; left: 0; 
            width: 100%; height: 100%;
            background: white; 
            color: #d9534f; 
            text-align: center; 
            padding-top: 50px; 
            z-index: 9999;
        }

        .header { 
            text-align: center; 
            border-bottom: 3px solid #007bff; 
            margin-bottom: 25px; 
            padding-bottom: 10px;
        }

        .question-box { 
            margin-bottom: 30px; 
            padding: 20px; 
            border: 1px solid #dee2e6; 
            border-radius: 10px; 
            background-color: #fff;
        }

        .word-bank {
            background-color: #f8f9fa;
            padding: 15px;
            border: 2px dashed #007bff;
            border-radius: 8px;
            margin-bottom: 15px;
            text-align: center;
            font-weight: bold;
        }
        
        .answer-line {
            border: none; 
            border-bottom: 2px solid #007bff; 
            width: 150px; 
            outline: none; 
            background: transparent;
            font-size: 16px;
            text-align: center;
            color: #495057;
        }

        .btn { padding: 12px 25px; cursor: pointer; border: none; border-radius: 5px; font-size: 16px; margin: 10px; font-weight: bold; transition: 0.3s; }
        .btn-start { background-color: #007bff; color: white; width: 280px; }
        .btn-start:hover { background-color: #0056b3; }
        .btn-submit { background-color: #28a745; color: white; width: 100%; margin-top: 20px; }
        .btn-submit:hover { background-color: #218838; }

        .true-false-row { margin: 10px 0; padding: 10px; background: #f1f3f5; border-radius: 5px; }

        @media print { .no-print { display: none; } }
    </style>
</head>
<body>

<div id="lock-screen">
    <h1>⚠️ Activity Locked!</h1>
    <p style="font-size:20px; color:black;">School Activity Center</p>
    <p>You have already completed this activity or attempted to leave the page.</p>
    
    <div style="margin-top: 30px; border: 2px solid #ccc; display: inline-block; padding: 20px; border-radius: 10px;">
        <p style="color: blue;">Teacher Unlock Required:</p>
        <input type="password" id="teacher-password" placeholder="Enter PIN..." style="padding: 10px; font-size: 16px;">
        <button class="btn" onclick="unlockExam()" style="width: auto; background-color: #28a745; color:white;">Unlock</button>
        <p id="password-error" style="color: red; display: none;">Incorrect PIN!</p>
    </div>
</div>

<div id="main-container">
    <div id="start-area" style="text-align: center; padding: 50px;">
        <img src="https://img.icons8.com/color/96/000000/learning.png" alt="Learn"><br>
        <h2>English Workbook - Unit 7</h2>
        <h3>Lesson 2: WOW! Team Talk</h3>
        <p style="color: #6c757d;">Focus: Vocabulary, Reading, and Expressions</p>
        <button class="btn btn-start" onclick="startExam()">Start Practice Now</button>
    </div>

    <div id="exam-content">
        <div class="header">
            <h1>Unit 7: Lesson 2 Interactive</h1>
            <div style="display: flex; justify-content: space-between; padding: 10px;">
                <div><strong>Student:</strong> <input type="text" id="studentName" placeholder="Enter Name..." class="answer-line" style="width: 200px;"></div>
                <div><strong>Grade:</strong> 7th Grade</div>
            </div>
        </div>

        <div class="question-box">
            <h3>1. Complete the sentences with words from the bank:</h3>
            <div class="word-bank">
                angry | arguments | borrow | cool | easy | experiences | huge | maybe | month | podcasts | trying | vlogs
            </div>
            <p>1. I'm <input type="text" id="v1" class="answer-line"> to get on well with everyone for a <input type="text" id="v2" class="answer-line">.</p>
            <p>2. Well, it's been <input type="text" id="v3" class="answer-line"> with my friends. I haven't had any <input type="text" id="v4" class="answer-line"> with them.</p>
            <p>3. I was so <input type="text" id="v5" class="answer-line"> and we had a <input type="text" id="v6" class="answer-line"> argument!</p>
            <p>4. <input type="text" id="v7" class="answer-line"> you should record your <input type="text" id="v8" class="answer-line"> in some way.</p>
            <p>5. I think that <input type="text" id="v9" class="answer-line"> will be as popular as <input type="text" id="v10" class="answer-line"> one day.</p>
            <p>6. I think it's a <input type="text" id="v11" class="answer-line"> T-shirt! Just don't let my sister <input type="text" id="v12" class="answer-line"> it!</p>
        </div>

        <div class="question-box">
            <h3>2. Circle True (T) or False (F):</h3>
            <div class="true-false-row">
                1. Dana has been doing an experiment for a week. 
                <input type="radio" name="tf1" value="F"> T / <input type="radio" name="tf1" value="T"> F (Correct: False, she's doing it for a month)
            </div>
            <div class="true-false-row">
                2. Dana gets on worse with her sister than with her friends. 
                <input type="radio" name="tf2" value="T"> T / <input type="radio" name="tf2" value="F"> F
            </div>
            <div class="true-false-row">
                3. Dana ruined her sister's favourite T-shirt. 
                <input type="radio" name="tf3" value="F"> T / <input type="radio" name="tf3" value="F"> F
            </div>
        </div>

        <div class="question-box">
            <h3>3. Complete the Dialogue:</h3>
            <div class="word-bank">Never mind | What are you up to? | That's not on</div>
            <div style="font-style: italic; background: #f9f9f9; padding: 15px; border-radius: 5px;">
                <strong>A:</strong> Hi Abbas. <input type="text" id="ex1" class="answer-line">?<br>
                <strong>B:</strong> Not much. I'm waiting for Tareq, but he's late, as usual!<br>
                <strong>A:</strong> <input type="text" id="ex2" class="answer-line">. He should try harder to be on time.<br>
                <strong>B:</strong> I know. It makes me so angry.
            </div>
        </div>
        
        <button class="btn btn-submit no-print" onclick="submitExam()">Finish and Show Results</button>
        <div style="text-align: center; font-weight: bold; margin-top: 30px; color: #007bff;">Keep Learning!</div>
    </div>
</div>

<script>
    const TEACHER_SECRET = "0101"; 

    function startExam() {
        // Check if already locked before starting
        if (localStorage.getItem("unit7_status") === "locked") {
            showLockScreen();
            return;
        }
        document.getElementById('start-area').style.display = 'none';
        document.getElementById('exam-content').style.display = 'block';
    }

    function submitExam() {
        let score = 0;
        const totalPoints = 17;
        const name = document.getElementById('studentName').value;
        if (!name) { alert("Please enter your name!"); return; }

        // Vocab Check
        const vocabAnswers = ["trying", "month", "easy", "arguments", "angry", "huge", "maybe", "experiences", "podcasts", "vlogs", "cool", "borrow"];
        for(let i=1; i<=12; i++) {
            if(document.getElementById('v'+i).value.toLowerCase().trim() === vocabAnswers[i-1]) score++;
        }

        // T/F Check
        if (document.querySelector('input[name="tf1"]:checked')?.value === 'T') score++;
        if (document.querySelector('input[name="tf2"]:checked')?.value === 'T') score++;
        if (document.querySelector('input[name="tf3"]:checked')?.value === 'T') score++;

        // Expressions Check
        if (document.getElementById('ex1').value.toLowerCase().includes("up to")) score++;
        if (document.getElementById('ex2').value.toLowerCase().includes("not on")) score++;

        alert(`Great job, ${name}!\nYour Score: ${score} / ${totalPoints}`);
        lockActivity(); // Use a shared lock function
    }

    // Function to handle the locking state
    function lockActivity() {
        localStorage.setItem("unit7_status", "locked");
        showLockScreen();
    }

    function showLockScreen() {
        document.getElementById('exam-content').style.display = 'none';
        document.getElementById('start-area').style.display = 'none';
        document.getElementById('lock-screen').style.display = 'block';
    }

    function unlockExam() {
        if (document.getElementById('teacher-password').value === TEACHER_SECRET) {
            localStorage.removeItem("unit7_status");
            location.reload();
        } else {
            document.getElementById('password-error').style.display = 'block';
        }
    }

    // --- SECURITY MONITORING ---

    // 1. Detect if the user switches tabs or minimizes the window
    document.addEventListener("visibilitychange", function() {
        if (document.hidden && document.getElementById('exam-content').style.display === 'block') {
            lockActivity();
            alert("Activity Locked: You left the page during the exam.");
        }
    });

    // 2. Detect if the window loses focus (e.g., clicking on another app or a popup)
    window.addEventListener("blur", function() {
        if (document.getElementById('exam-content').style.display === 'block') {
            lockActivity();
            alert("Activity Locked: Window lost focus.");
        }
    });
</script>
</body>
</html>
