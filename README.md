<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7th Grade - Unit 7 Lesson 2 Interactive Activity</title>
    <style>
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            line-height: 1.6; 
            max-width: 850px; 
            margin: auto; 
            padding: 20px; 
            background-color: #eef2f3; 
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
            top: 0; 
            left: 0; 
            width: 100%; 
            height: 100%;
            background: white; 
            color: #d9534f; 
            text-align: center; 
            padding-top: 50px; 
            z-index: 9999;
        }

        .header { text-align: center; border-bottom: 3px solid #007bff; margin-bottom: 20px; padding-bottom: 10px; }
        .question-box { margin-bottom: 30px; padding: 20px; border: 1px solid #e0e0e0; border-radius: 12px; background: #fff; }
        .word-bank { background: #f0f7ff; padding: 15px; border-radius: 8px; border: 1px dashed #007bff; margin-bottom: 15px; text-align: center; font-weight: bold; }
        
        .answer-line {
            border: none; 
            border-bottom: 2px solid #007bff; 
            width: 150px; 
            outline: none; 
            background: transparent;
            font-size: 16px;
            color: #333;
            text-align: center;
        }

        .btn { padding: 12px 25px; cursor: pointer; border: none; border-radius: 8px; font-size: 16px; margin: 10px; font-weight: bold; transition: 0.3s; }
        .btn-start { background-color: #007bff; color: white; width: 250px; }
        .btn-start:hover { background-color: #0056b3; }
        .btn-submit { background-color: #28a745; color: white; width: 100%; margin-top: 20px; }

        .dialogue-box { background-color: #fcfcfc; padding: 15px; border-left: 5px solid #007bff; margin: 10px 0; }
    </style>
</head>
<body>

<div id="lock-screen">
    <h1>⚠️ Activity Locked!</h1>
    <p style="font-size:20px; color:black;">Security Violation Detected</p>
    <div style="margin-top: 30px; border: 2px solid #ccc; display: inline-block; padding: 20px; border-radius: 10px;">
        <p style="color: blue;">Enter Teacher Code to Unlock:</p>
        <input type="password" id="teacher-password" style="padding: 10px;">
        <button class="btn" onclick="unlockExam()" style="background-color: #28a745; color:white;">Unlock</button>
    </div>
</div>

<div id="main-container">
    <div id="start-area" style="text-align: center; padding: 50px;">
        <h2>Action Pack 7 - Unit 7</h2>
        <h3>Lesson 2: Getting on with Everyone</h3>
        <p style="color: #666;">Complete the vocabulary and dialogue exercises.</p>
        <button class="btn btn-start" onclick="startExam()">Start Activity</button>
    </div>

    <div id="exam-content">
        <div class="header">
            <h1>Unit 7 Vocabulary & Dialogue</h1>
            <div style="display: flex; justify-content: space-between; padding: 10px;">
                <div><strong>Name:</strong> <input type="text" id="studentName" class="answer-line" style="width: 200px;"></div>
                <div><strong>Grade:</strong> 7th Grade</div>
            </div>
        </div>

        <div class="question-box">
            <h3>Q1. Complete the sentences from the dialogue:</h3>
            <div class="word-bank">
                angry | arguments | borrow | cool | easy | experiences | huge | maybe | month | podcasts | trying | vlogs
            </div>
            <ol>
                <li>I'm <input type="text" id="ex1_1" class="answer-line"> to get on well with everyone for a <input type="text" id="ex1_2" class="answer-line">.</li>
                <li>Well, it's been <input type="text" id="ex1_3" class="answer-line"> with my friends. I haven't had any <input type="text" id="ex1_4" class="answer-line"> with them.</li>
                <li>I was so <input type="text" id="ex1_5" class="answer-line"> and we had a <input type="text" id="ex1_6" class="answer-line"> argument!</li>
                <li><input type="text" id="ex1_7" class="answer-line"> you should record your <input type="text" id="ex1_8" class="answer-line"> in some way.</li>
                <li>I think that <input type="text" id="ex1_9" class="answer-line"> will be as popular as <input type="text" id="ex1_10" class="answer-line"> one day.</li>
                <li>I think it's a <input type="text" id="ex1_11" class="answer-line"> T-shirt! Just don't let my sister <input type="text" id="ex1_12" class="answer-line"> it!</li>
            </ol>
        </div>

        <div class="question-box">
            <h3>Q2. True (T) or False (F)?</h3>
            <p>1. Dana has been doing an experiment for a week. 
               <select id="ex2_1"><option>?</option><option>T</option><option>F</option></select></p>
            <p>2. Dana gets on worse with her sister than with her friends. 
               <select id="ex2_2"><option>?</option><option>T</option><option>F</option></select></p>
            <p>3. Dana ruined her sister's favorite T-shirt. 
               <select id="ex2_3"><option>?</option><option>T</option><option>F</option></select></p>
        </div>

        <div class="question-box">
            <h3>Q3. Social Expressions</h3>
            <div class="word-bank">What are you up to? | Never mind | That's not on</div>
            <div class="dialogue-box">
                <strong>A:</strong> Hi Abbas. 1. <input type="text" id="ex3_1" class="answer-line" style="width: 200px;"><br>
                <strong>B:</strong> Not much. I'm waiting for Tareq.<br><br>
                <strong>A:</strong> Are you using my tablet without asking? 2. <input type="text" id="ex3_2" class="answer-line" style="width: 200px;"><br>
                <strong>B:</strong> I'm really sorry. I thought it was mine!<br>
                <strong>A:</strong> 3. <input type="text" id="ex3_3" class="answer-line" style="width: 200px;">. We all make mistakes.
            </div>
        </div>
        
        <button class="btn btn-submit" onclick="submitExam()">Submit Results</button>
    </div>
</div>

<script>
    const TEACHER_SECRET = "0101"; 

    function startExam() {
        document.getElementById('start-area').style.display = 'none';
        document.getElementById('exam-content').style.display = 'block';
    }

    function submitExam() {
        const name = document.getElementById('studentName').value;
        if (!name) { alert("Please enter your name!"); return; }
        
        // Basic Logic: Check a few answers to show it works
        let score = 0;
        if(document.getElementById('ex1_1').value.toLowerCase().trim() === 'trying') score++;
        if(document.getElementById('ex2_1').value === 'F') score++;
        
        alert("Well done, " + name + "! You've submitted your activity.");
        location.reload(); 
    }

    function showLockScreen() {
        document.getElementById('exam-content').style.display = 'none';
        document.getElementById('lock-screen').style.display = 'block';
    }

    function unlockExam() {
        if (document.getElementById('teacher-password').value === TEACHER_SECRET) {
            document.getElementById('lock-screen').style.display = 'none';
            document.getElementById('start-area').style.display = 'block';
        } else {
            alert("Wrong Code!");
        }
    }

    document.addEventListener("visibilitychange", function() {
        if (document.hidden && document.getElementById('exam-content').style.display === 'block') {
            showLockScreen();
        }
    });
</script>

</body>
</html>
