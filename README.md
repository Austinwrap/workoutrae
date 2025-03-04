<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raeanne's Fitness Journey</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9ebfc;
            color: #333;
            overflow-x: hidden;
        }
        .welcome-page {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff9cee, #d4a5ff);
            text-align: center;
            padding: 20px;
        }
        .welcome-page h1 {
            font-size: 2.2em;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        .welcome-page p {
            font-size: 1.3em;
            color: white;
            margin: 10px 0;
        }
        .enter-btn {
            padding: 15px 30px;
            font-size: 1.2em;
            background-color: #ff66cc;
            border: none;
            border-radius: 25px;
            color: white;
            cursor: pointer;
            transition: transform 0.3s;
        }
        .enter-btn:hover {
            transform: scale(1.1);
        }
        .main-content {
            display: none;
            padding: 20px;
            text-align: center;
        }
        .day-buttons {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        .day-btn {
            padding: 12px 25px;
            background-color: #d4a5ff;
            border: none;
            border-radius: 20px;
            color: white;
            cursor: pointer;
            font-size: 1.1em;
            transition: background-color 0.3s;
        }
        .day-btn:hover {
            background-color: #ff66cc;
        }
        .workout-popup, .motivate-popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
            max-width: 90%;
            max-height: 85vh;
            overflow-y: auto;
            z-index: 10;
        }
        .close-btn {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 1.8em;
            cursor: pointer;
            color: #ff66cc;
        }
        .motivate-btn {
            padding: 12px 25px;
            background-color: #ff9cee;
            border: none;
            border-radius: 20px;
            color: white;
            font-size: 1.1em;
            cursor: pointer;
            margin-top: 25px;
        }
        .motivate-btn:hover {
            background-color: #ff66cc;
        }
        h2 {
            color: #ff66cc;
            font-size: 1.8em;
            margin-bottom: 15px;
        }
        h3 {
            color: #d4a5ff;
            font-size: 1.4em;
            margin: 15px 0 10px;
        }
        ul {
            list-style-type: disc;
            padding-left: 25px;
            text-align: left;
            line-height: 1.6;
        }
        li {
            margin-bottom: 10px;
        }
        p {
            font-size: 1.1em;
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <div class="welcome-page" id="welcome">
        <h1>Welcome, Raeanne!</h1>
        <p>You’re a total rockstar!</p>
        <p>Let’s crush those goals together!</p>
        <button class="enter-btn" onclick="enterSite()">Enter</button>
    </div>

    <div class="main-content" id="main">
        <h2>Raeanne's Weekly Workouts</h2>
        <div class="day-buttons">
            <button class="day-btn" onclick="showWorkout('Monday')">Monday</button>
            <button class="day-btn" onclick="showWorkout('Tuesday')">Tuesday</button>
            <button class="day-btn" onclick="showWorkout('Wednesday')">Wednesday</button>
            <button class="day-btn" onclick="showWorkout('Thursday')">Thursday</button>
            <button class="day-btn" onclick="showWorkout('Friday')">Friday</button>
        </div>
        <button class="motivate-btn" onclick="showMotivation()">Motivate Me</button>
    </div>

    <!-- Workout Popups -->
    <div class="workout-popup" id="Monday">
        <span class="close-btn" onclick="closePopup('Monday')">X</span>
        <h2>Monday: Cycle + HIIT</h2>
        <h3>Warmup</h3>
        <ul>
            <li>StairMaster: 1,500 steps (~10 min)</li>
        </ul>
        <h3>Workout</h3>
        <ul>
            <li>Cycle Class: 45 min (group session)</li>
            <li>HIIT Workout: Post-cycle (group session)</li>
        </ul>
    </div>
    <div class="workout-popup" id="Tuesday">
        <span class="close-btn" onclick="closePopup('Tuesday')">X</span>
        <h2>Tuesday: Strength Set 2</h2>
        <h3>Warmup</h3>
        <ul>
            <li>Treadmill: 1 mile (~10–12 min, brisk walk)</li>
        </ul>
        <h3>Workout</h3>
        <ul>
            <li>KB Squat + Overhead Press: 10 reps, 3 rounds</li>
            <li>Medicine Ball Slams: 12 reps, 2 rounds</li>
            <li>DB Deadlift: 12 reps, 3 rounds</li>
        </ul>
    </div>
    <div class="workout-popup" id="Wednesday">
        <span class="close-btn" onclick="closePopup('Wednesday')">X</span>
        <h2>Wednesday: Cycle + HIIT</h2>
        <h3>Warmup</h3>
        <ul>
            <li>StairMaster: 1,500 steps (~10 min)</li>
        </ul>
        <h3>Workout</h3>
        <ul>
            <li>Cycle Class: 45 min (group session)</li>
            <li>HIIT Workout: Post-cycle (group session)</li>
        </ul>
    </div>
    <div class="workout-popup" id="Thursday">
        <span class="close-btn" onclick="closePopup('Thursday')">X</span>
        <h2>Thursday: Strength Set 1</h2>
        <h3>Warmup</h3>
        <ul>
            <li>Treadmill: 1 mile (~10–12 min, brisk walk)</li>
        </ul>
        <h3>Workout</h3>
        <ul>
            <li>KB Goblet Squat: 12 reps, 3 rounds</li>
            <li>DB Russian Twists: 20 twists (10/side), 3 rounds</li>
            <li>Plank with Shoulder Taps: 20 taps (10/side), 3 rounds</li>
        </ul>
    </div>
    <div class="workout-popup" id="Friday">
        <span class="close-btn" onclick="closePopup('Friday')">X</span>
        <h2>Friday: Strength Set 2</h2>
        <h3>Warmup</h3>
        <ul>
            <li>StairMaster: 2,000 steps (~15 min)</li>
        </ul>
        <h3>Workout</h3>
        <ul>
            <li>KB Squat + Overhead Press: 10 reps, 3 rounds</li>
            <li>Medicine Ball Slams: 12 reps, 2 rounds</li>
            <li>DB Deadlift: 12 reps, 3 rounds</li>
        </ul>
    </div>

    <!-- Motivation Popup -->
    <div class="motivate-popup" id="motivate">
        <span class="close-btn" onclick="closePopup('motivate')">X</span>
        <h2>Your Motivation Boost!</h2>
        <p id="quote"></p>
    </div>

    <script>
        function enterSite() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('main').style.display = 'block';
        }

        function showWorkout(day) {
            document.getElementById(day).style.display = 'block';
        }

        function closePopup(id) {
            document.getElementById(id).style.display = 'none';
        }

        const quotes = [
            "You’re stronger than you think, babe!",
            "Sweat today, shine tomorrow!",
            "Every rep is a step to your best self!",
            "You’ve got this—keep pushing!",
            "Strong women lift each other up—starting with you!",
            "Your only limit is the one you set!",
            "Slay the gym, queen!",
            "Muscles are made of grit and grace!",
            "You’re a warrior, not a worrier!",
            "One more rep, one more win!",
            "Fit is not a destination, it’s a vibe!",
            "You’re building a masterpiece—keep going!",
            "Strong legs, strong heart, strong YOU!",
            "The gym is your playground—own it!",
            "You don’t sweat, you sparkle!",
            "Tough times don’t last, tough women do!",
            "Lift like a lady, beast like a boss!",
            "You’re not here to shrink—you’re here to grow!",
            "Every drop of sweat is a victory!",
            "Your strength is your superpower!",
            "Queens don’t quit!",
            "You’re unstoppable—believe it!",
            "Progress, not perfection, babe!",
            "The grind is your glow-up!",
            "Strong is the new sexy!",
            "You’re a force of nature—keep moving!",
            "Pain today, power tomorrow!",
            "You’re rewriting your story with every lift!",
            "Hustle for that muscle!",
            "You’re a badass in the making!",
            "Keep showing up—you’re worth it!",
            "The weights don’t lift themselves!",
            "You’re tougher than the toughest days!",
            "Sweat is your crown—wear it proud!",
            "You’re building a legacy of strength!",
            "No excuses, just results!",
            "You’re a diamond—pressure makes you shine!",
            "Strong women don’t wait—they lift!",
            "Every squat is a step to slay!",
            "You’re the hero of your own story!",
            "Push past the doubt—you’ve got this!",
            "Your body is art—sculpt it!",
            "Fear less, lift more!",
            "You’re not just strong—you’re fierce!",
            "The gym is where queens rise!",
            "You’re a warrior princess—keep fighting!",
            "Strength looks good on you!",
            "You’re breaking barriers, babe!",
            "One rep at a time, you’re unstoppable!",
            "You’re not done—you’re just getting started!"
        ];

        function showMotivation() {
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
            document.getElementById('quote').innerText = randomQuote;
            document.getElementById('motivate').style.display = 'block';
        }
    </script>
</body>
</html>
​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​
