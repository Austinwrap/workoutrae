<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raeanne's Barbell Shakedown</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #fff0f5, #f0f8ff);
            color: #444;
            overflow-x: hidden;
            line-height: 1.4;
        }
        .welcome-page {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff6f61, #ff99cc, #ffb6c1);
            text-align: center;
            padding: 15px;
            color: #fff;
            text-shadow: 1px 1px 2px rgba(255, 105, 97, 0.3);
            animation: pulse 1.5s infinite alternate;
        }
        @keyframes pulse {
            0% { box-shadow: 0 0 8px rgba(255, 111, 97, 0.6); }
            100% { box-shadow: 0 0 15px rgba(255, 153, 204, 0.6); }
        }
        .welcome-page h1 {
            font-size: 2.5em;
            margin: 10px 0;
            font-weight: bold;
            letter-spacing: 1px;
        }
        .welcome-page p {
            font-size: 1.4em;
            margin: 6px 0;
            font-style: italic;
        }
        .enter-btn {
            padding: 10px 25px;
            font-size: 1.1em;
            background: #fff;
            border: 2px solid #ff6f61;
            border-radius: 25px;
            color: #ff6f61;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 15px;
        }
        .enter-btn:hover {
            background: #ff6f61;
            color: #fff;
            transform: scale(1.05);
        }
        .main-content {
            display: none;
            padding: 10px;
            text-align: center;
            background: linear-gradient(to bottom, #f0f8ff, #fff0f5);
            min-height: 100vh;
            color: #444;
        }
        .day-buttons {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 8px;
            margin: 10px auto;
            max-width: 300px;
        }
        .day-btn, .grocery-btn {
            padding: 8px 15px;
            background: #ffd1dc;
            border: 1px solid #ff99cc;
            border-radius: 15px;
            color: #ff6f61;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }
        .day-btn:hover, .grocery-btn:hover {
            background: #ff99cc;
            color: #fff;
        }
        .all-btn {
            padding: 6px 12px;
            background: #ffccd5;
            border: 1px solid #ff6f61;
            border-radius: 20px;
            color: #ff6f61;
            cursor: pointer;
            font-size: 0.8em;
            margin: 5px 0;
            transition: all 0.3s;
        }
        .all-btn:hover {
            background: #ff6f61;
            color: #fff;
        }
        .workout-popup, .grocery-popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, #fff0f5, #f0f8ff);
            padding: 15px;
            border-radius: 20px;
            box-shadow: 0 0 12px rgba(255, 111, 97, 0.3);
            max-width: 85%;
            max-height: 75vh;
            overflow-y: auto;
            z-index: 10;
            border: 2px dashed #ff99cc;
        }
        .close-btn {
            position: absolute;
            top: 8px;
            right: 8px;
            font-size: 1.3em;
            cursor: pointer;
            color: #ff6f61;
            padding: 5px;
            border: none;
            background: none;
            transition: color 0.3s;
        }
        .nav-btn, .skip-btn {
            font-size: 1.5em;
            cursor: pointer;
            color: #ff6f61;
            padding: 10px 15px;
            border: none;
            background: none;
            transition: color 0.3s;
            min-width: 50px;
            text-align: center;
        }
        .nav-btn:hover, .close-btn:hover, .skip-btn:hover {
            color: #ffb6c1;
        }
        .motivate-btn {
            padding: 8px 15px;
            background: #ffd1dc;
            border: 1px solid #ff99cc;
            border-radius: 15px;
            color: #ff6f61;
            font-size: 0.9em;
            cursor: pointer;
            margin: 5px 0;
            transition: all 0.3s;
        }
        .motivate-btn:hover {
            background: #ff99cc;
            color: #fff;
        }
        h2 {
            color: #ff6f61;
            font-size: 1.5em;
            margin-bottom: 8px;
            font-weight: bold;
        }
        h3 {
            color: #ff99cc;
            font-size: 1.2em;
            margin: 8px 0;
        }
        ul {
            list-style-type: square;
            padding-left: 20px;
            text-align: left;
            font-size: 0.9em;
            color: #555;
        }
        li {
            margin-bottom: 5px;
        }
        p {
            font-size: 0.9em;
            margin: 8px 0;
            color: #666;
        }
        .nav-container {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }
        .reminder {
            font-style: italic;
            color: #ff99cc;
            font-size: 0.85em;
        }
        .comparison-table {
            width: 100%;
            border-collapse: collapse;
            margin: 10px 0;
        }
        .comparison-table th, .comparison-table td {
            border: 1px solid #ff99cc;
            padding: 8px;
            text-align: left;
            font-size: 0.9em;
        }
        .comparison-table th {
            background: #ffd1dc;
            color: #ff6f61;
        }
        @media (max-width: 600px) {
            .welcome-page h1 { font-size: 2em; }
            .welcome-page p { font-size: 1.2em; }
            .day-btn, .grocery-btn { font-size: 0.85em; }
            .workout-popup, .grocery-popup { padding: 12px; }
            .nav-btn, .skip-btn { padding: 8px 12px; }
        }
    </style>
</head>
<body>
    <div class="welcome-page" id="welcome">
        <h1>¡Raeanne, Barbell Queen!</h1>
        <p>Shake It, Lift It—Nicotine-Free!</p>
        <button class="enter-btn" onclick="enterSite()">¡Crush It!</button>
    </div>

    <div class="main-content" id="main">
        <h2>Raeanne’s Shakedown Schedule</h2>
        <p class="reminder">Tip: Mix it up & stay consistent, badass!</p>
        <div class="day-buttons">
            <button class="day-btn" onclick="showWorkout('Monday')">Monday</button>
            <button class="day-btn" onclick="showWorkout('Tuesday')">Tuesday</button>
            <button class="day-btn" onclick="showWorkout('Wednesday')">Wednesday</button>
            <button class="day-btn" onclick="showWorkout('Thursday')">Thursday</button>
            <button class="day-btn" onclick="showWorkout('Friday')">Friday</button>
            <button class="day-btn" onclick="showWorkout('Saturday')">Saturday</button>
            <button class="day-btn" onclick="showWorkout('Sunday')">Sunday</button>
        </div>
        <button class="motivate-btn" onclick="showMotivation()">¡Fire Me Up!</button>
        <button class="all-btn" onclick="showAllWorkouts(0)">All Workouts</button>
        <button class="grocery-btn" onclick="showGroceryList('aldi')">Aldi Grocery List</button>
        <button class="grocery-btn" onclick="showGroceryList('pricechopper')">Price Chopper Grocery List</button>
        <button class="all-btn" onclick="showPriceComparison()">Price Comparison</button>
    </div>

    <!-- Raeanne’s Core Workouts -->
    <div class="workout-popup" id="Monday">
        <span class="close-btn" onclick="closePopup('Monday')">X</span>
        <h2>Monday: Cycle + HIIT</h2>
        <h3>Cycle (5:30-6:15)</h3>
        <ul>
            <li>45 min Spin Class</li>
        </ul>
        <h3>HIIT Group (6:30-7:15)</h3>
        <ul>
            <li>KB Swings: 20 lbs, 3x12</li>
            <li>DB Thrusters: 15 lbs each, 3x10</li>
            <li>Jump Squats: Bodyweight, 3x12</li>
            <li>Plank Rows: 15 lbs each, 3x10</li>
            <li>DB Shoulder Press: 15 lbs each, 3x10</li>
            <li>Russian Twists: 10 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Sunday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Monday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Tuesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Tuesday">
        <span class="close-btn" onclick="closePopup('Tuesday')">X</span>
        <h2>Tuesday: Full Body Strength + StairMaster</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>Goblet Squats (KB): 25 lbs, 3x12</li>
            <li>DB Romanian Deadlifts: 20 lbs each, 3x10</li>
            <li>DB Shoulder Press: 15 lbs each, 3x10</li>
            <li>KB Swings: 20 lbs, 3x12</li>
            <li>DB Bent-Over Rows: 20 lbs each, 3x10</li>
            <li>Plank Rows: 15 lbs each, 3x10</li>
        </ul>
        <h3>Finisher</h3>
        <ul>
            <li>30 min StairMaster (mix speed & steps)</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Monday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Tuesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Wednesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Wednesday">
        <span class="close-btn" onclick="closePopup('Wednesday')">X</span>
        <h2>Wednesday: Cycle + HIIT</h2>
        <h3>Cycle (5:30-6:15)</h3>
        <ul>
            <li>45 min Spin Class</li>
        </ul>
        <h3>HIIT Group (6:30-7:15)</h3>
        <ul>
            <li>KB Snatch: 15 lbs, 3x10 (alternate arms)</li>
            <li>DB Chest Press: 20 lbs each, 3x10</li>
            <li>Jump Lunges: Bodyweight, 3x12</li>
            <li>KB Deadlifts: 25 lbs, 3x10</li>
            <li>DB Reverse Flys: 10 lbs each, 3x12</li>
            <li>Plank to Push-Ups: Bodyweight, 3x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Tuesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Wednesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Thursday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Thursday">
        <span class="close-btn" onclick="closePopup('Thursday')">X</span>
        <h2>Thursday: Full Body HIIT + StairMaster</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Deadlifts: 25 lbs, 3x10</li>
            <li>DB Thrusters: 15 lbs each, 3x10</li>
            <li>KB Snatch: 15 lbs, 3x10 (alternate arms)</li>
            <li>Jump Squats: 10 lbs, 3x12</li>
            <li>Russian Twists: 10 lbs, 3x12</li>
            <li>Plank to Push-Ups: Bodyweight, 3x10</li>
        </ul>
        <h3>Finisher</h3>
        <ul>
            <li>30 min StairMaster (mix speed & steps)</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Wednesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Thursday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Friday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Friday">
        <span class="close-btn" onclick="closePopup('Friday')">X</span>
        <h2>Friday: Lower Body Strength</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>Bulgarian Split Squats: 20 lbs each, 3x10</li>
            <li>KB Sumo Deadlifts: 30 lbs, 3x12</li>
            <li>DB Step-Ups: 15 lbs each, 3x10</li>
            <li>DB Hip Thrusts: 25 lbs, 3x12</li>
            <li>KB Goblet Cossack Squat: 20 lbs, 3x10</li>
            <li>Jump Lunges: Bodyweight, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Thursday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Friday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Saturday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Saturday">
        <span class="close-btn" onclick="closePopup('Saturday')">X</span>
        <h2>Saturday: Full Body Circuit + StairMaster</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jump Rope: 3x1 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Clean & Press: 20 lbs, 3x10</li>
            <li>DB Lateral Lunges: 15 lbs each, 3x12</li>
            <li>DB Chest Press: 20 lbs each, 3x10</li>
            <li>KB Turkish Get-Ups: 15 lbs, 3x8</li>
            <li>DB Hanging Knee Raises: 10 lbs, 3x12</li>
            <li>KB Plank Drags: 15 lbs, 3x10</li>
        </ul>
        <h3>Finisher</h3>
        <ul>
            <li>30 min StairMaster (3 min fast, 2 min slow)</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Friday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Saturday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Sunday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Sunday">
        <span class="close-btn" onclick="closePopup('Sunday')">X</span>
        <h2>Sunday: Active Recovery</h2>
        <h3>Cardio (30 min)</h3>
        <ul>
            <li>Treadmill Incline Walk: 30 min</li>
        </ul>
        <h3>Core Workout (15-20 min)</h3>
        <ul>
            <li>KB Russian Twists: 15 lbs, 3x12</li>
            <li>DB Side Plank Hip Dips: 10 lbs, 3x10</li>
            <li>KB Farmers Carry: 20 lbs each, 3x30s</li>
            <li>Hollow Body Hold: Bodyweight, 3x45s</li>
            <li>Bicycle Crunches: Bodyweight, 3x20</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Saturday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Sunday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Monday')">Next ►</button>
        </div>
    </div>

    <!-- Alternate Workouts -->
    <div class="workout-popup" id="Alt1">
        <span class="close-btn" onclick="closePopup('Alt1')">X</span>
        <h2>Full Body HIIT (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Circles: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Windmills: 15 lbs, 4x10</li>
            <li>DB Arnold Press: 15 lbs each, 4x10</li>
            <li>DB Floor Press: 20 lbs each, 4x12</li>
            <li>KB Single-Leg RDL: 20 lbs, 4x10</li>
            <li>Jump Rope: 4x60s</li>
            <li>DB Hammer Curls: 15 lbs each, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt1')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt1')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt1')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt2">
        <span class="close-btn" onclick="closePopup('Alt2')">X</span>
        <h2>Lower Body (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Leg Swings: 2x15</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Suitcase Deadlifts: 25 lbs each, 4x10</li>
            <li>KB Box Squats: 20 lbs, 4x12</li>
            <li>DB Curtsy Lunges: 15 lbs each, 4x10</li>
            <li>DB Reverse Flys: 10 lbs each, 4x12</li>
            <li>KB Swings: 20 lbs, 4x12</li>
            <li>DB Step-Back Lunges: 20 lbs each, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt2')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt2')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt2')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt3">
        <span class="close-btn" onclick="closePopup('Alt3')">X</span>
        <h2>Full Body Strength (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Z Press: 15 lbs each, 4x10</li>
            <li>KB Clean & Press: 20 lbs, 4x10</li>
            <li>DB Goblet Squats: 25 lbs, 4x12</li>
            <li>DB Bent-Over Rows: 20 lbs each, 4x10</li>
            <li>KB Plank Drags: 15 lbs, 4x10</li>
            <li>DB Hanging Knee Raises: 10 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt3')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt3')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt3')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt4">
        <span class="close-btn" onclick="closePopup('Alt4')">X</span>
        <h2>HIIT Circuit (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jump Rope: 3x1 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Incline Press: 20 lbs each, 4x12</li>
            <li>KB Snatch: 15 lbs, 4x10</li>
            <li>DB Thrusters: 15 lbs each, 4x10</li>
            <li>Jump Squats: 10 lbs, 4x12</li>
            <li>DB Floor Flys: 15 lbs each, 4x10</li>
            <li>Plank Rows: 15 lbs each, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt4')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt4')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt4')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt5">
        <span class="close-btn" onclick="closePopup('Alt5')">X</span>
        <h2>Lower Body (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Walking Lunges: 2x10</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Bulgarian Split Squats: 20 lbs each, 4x10</li>
            <li>KB Sumo Deadlifts: 30 lbs, 4x12</li>
            <li>DB Step-Ups: 15 lbs each, 4x10</li>
            <li>DB Hip Thrusts: 25 lbs, 4x12</li>
            <li>KB Goblet Cossack Squat: 20 lbs, 4x10</li>
            <li>Jump Lunges: Bodyweight, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt5')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt5')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt5')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt6">
        <span class="close-btn" onclick="closePopup('Alt6')">X</span>
        <h2>Full Body (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Dynamic Stretch: 2 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Turkish Get-Ups: 15 lbs, 4x8</li>
            <li>DB Lateral Lunges: 15 lbs each, 4x12</li>
            <li>DB Chest Press: 20 lbs each, 4x10</li>
            <li>KB Swings: 20 lbs, 4x12</li>
            <li>DB Hammer Curls: 15 lbs each, 4x12</li>
            <li>Plank to Push-Ups: Bodyweight, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt6')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt6')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt6')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt7">
        <span class="close-btn" onclick="closePopup('Alt7')">X</span>
        <h2>Core Recovery (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Plank Hold: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Russian Twists: 15 lbs, 4x12</li>
            <li>DB Side Plank Hip Dips: 10 lbs, 4x10</li>
            <li>KB Farmers Carry: 20 lbs each, 4x30s</li>
            <li>Hollow Body Hold: Bodyweight, 4x45s</li>
            <li>Bicycle Crunches: Bodyweight, 4x20</li>
            <li>DB Hanging Knee Raises: 10 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt7')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt7')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt7')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt8">
        <span class="close-btn" onclick="closePopup('Alt8')">X</span>
        <h2>Full Body HIIT (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Wide Press: 20 lbs each, 4x10</li>
            <li>KB Snatch: 15 lbs, 4x10</li>
            <li>DB Thrusters: 15 lbs each, 4x10</li>
            <li>Jump Squats: 10 lbs, 4x12</li>
            <li>DB Reverse Flys: 10 lbs each, 4x12</li>
            <li>KB Plank Drags: 15 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt8')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt8')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt8')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt9">
        <span class="close-btn" onclick="closePopup('Alt9')">X</span>
        <h2>Upper Body Strength (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Arnold Press: 15 lbs each, 4x10</li>
            <li>KB Clean & Press: 20 lbs, 4x10</li>
            <li>DB Floor Press: 20 lbs each, 4x12</li>
            <li>DB Bent-Over Rows: 20 lbs each, 4x10</li>
            <li>DB Hammer Curls: 15 lbs each, 4x12</li>
            <li>Plank Rows: 15 lbs each, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt9')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt9')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt9')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt10">
        <span class="close-btn" onclick="closePopup('Alt10')">X</span>
        <h2>Full Body Power (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>KB Swings: 20 lbs, 4x12</li>
            <li>DB Thrusters: 15 lbs each, 4x10</li>
            <li>DB Suitcase Deadlifts: 25 lbs each, 4x10</li>
            <li>KB Turkish Get-Ups: 15 lbs, 4x8</li>
            <li>DB Lateral Lunges: 15 lbs each, 4x12</li>
            <li>Jump Rope: 4x60s</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt10')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt10')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt10')">Next ►</button>
        </div>
    </div>

    <!-- All Workouts Popup -->
    <div class="workout-popup" id="all-workouts">
        <span class="close-btn" onclick="closePopup('all-workouts')">X</span>
        <h2>Your Barbell Mixes</h2>
        <div id="all-workout-content"></div>
        <div class="nav-container">
            <button class="nav-btn" onclick="showAllWorkouts(currentAllIndex - 1)">◄ Prev</button>
            <button class="nav-btn" onclick="showAllWorkouts(currentAllIndex + 1)">Next ►</button>
        </div>
    </div>

    <!-- Motivation Popup -->
    <div class="workout-popup" id="motivate">
        <span class="close-btn" onclick="closePopup('motivate')">X</span>
        <h2>¡Your Shakedown Boost!</h2>
        <p id="quote"></p>
    </div>

    <!-- Aldi Grocery List Popup -->
    <div class="grocery-popup" id="aldi-grocery">
        <span class="close-btn" onclick="closePopup('aldi-grocery')">X</span>
        <h2>Aldi Meat Haul</h2>
        <ul>
            <li>Chicken Breast - Kirkwood Fresh Boneless Skinless (3 lbs, ~$12.87 at $4.29/lb)</li>
            <li>Chicken Thighs - Kirkwood Fresh Boneless Skinless (1 lb, ~$3.99 at $3.99/lb)</li>
            <li>Sirloin Steak - Black Angus (1.5 lbs, ~$13.49 at $8.99/lb)</li>
            <li>Ribeye Steak - Black Angus (1 lb, ~$11.99 at $11.99/lb)</li>
            <li>NY Strip Steak - Black Angus (1 lb, ~$10.49 at $10.49/lb)</li>
            <li>Salmon - Fremont Fish Market Frozen (1 lb, ~$7.99 at $7.99/lb)</li>
            <li>Canned Tuna - Northern Catch Chunk Light (3 cans, 5oz each, ~$2.07 at $0.69/can)</li>
            <li>Ground Turkey - Fresh Family Pack 93/7 (2.5 lbs, ~$8.73 at $3.49/lb)</li>
            <li>Ground Beef - 80/20 Fresh (2 lbs, ~$8.98 at $4.49/lb)</li>
            <li>Pork Chops - Fresh Boneless (1.5 lbs, ~$5.69 at $3.79/lb)</li>
        </ul>
        <p>Total Estimate: ~$86.29</p>
    </div>

    <!-- Price Chopper Grocery List Popup -->
    <div class="grocery-popup" id="pricechopper-grocery">
        <span class="close-btn" onclick="closePopup('pricechopper-grocery')">X</span>
        <h2>Price Chopper Meat Haul</h2>
        <ul>
            <li>Chicken Breast - Fresh Boneless Skinless (3 lbs, ~$14.97 at $4.99/lb)</li>
            <li>Chicken Thighs - Fresh Boneless Skinless (1 lb, ~$4.99 at $4.99/lb)</li>
            <li>Sirloin Steak - Fresh (1.5 lbs, ~$16.49 at $10.99/lb)</li>
            <li>Ribeye Steak - Fresh (1 lb, ~$13.99 at $13.99/lb)</li>
            <li>NY Strip Steak - Fresh (1 lb, ~$12.99 at $12.99/lb)</li>
            <li>Salmon - Fresh Atlantic (1 lb, ~$11.99 at $11.99/lb)</li>
            <li>Canned Tuna - Chunk Light in Water (3 cans, 5oz each, ~$2.97 at $0.99/can)</li>
            <li>Ground Turkey - 93/7 (2.5 lbs, ~$11.23 at $4.49/lb)</li>
            <li>Ground Beef - 80/20 Fresh (2 lbs, ~$10.58 at $5.29/lb)</li>
            <li>Pork Chops - Fresh Boneless (1.5 lbs, ~$6.89 at $4.59/lb)</li>
        </ul>
        <p>Total Estimate: ~$106.09</p>
    </div>

    <!-- Price Comparison Popup -->
    <div class="grocery-popup" id="price-comparison">
        <span class="close-btn" onclick="closePopup('price-comparison')">X</span>
        <h2>Price Comparison: Aldi vs Price Chopper</h2>
        <table class="comparison-table">
            <tr>
                <th>Item</th>
                <th>Aldi Price</th>
                <th>Price Chopper Price</th>
            </tr>
            <tr>
                <td>Chicken Breast (per lb)</td>
                <td>$4.29</td>
                <td>$4.99</td>
            </tr>
            <tr>
                <td>Chicken Thighs (per lb)</td>
                <td>$3.99</td>
                <td>$4.99</td>
            </tr>
            <tr>
                <td>Sirloin Steak (per lb)</td>
                <td>$8.99</td>
                <td>$10.99</td>
            </tr>
            <tr>
                <td>Ribeye Steak (per lb)</td>
                <td>$11.99</td>
                <td>$13.99</td>
            </tr>
            <tr>
                <td>NY Strip Steak (per lb)</td>
                <td>$10.49</td>
                <td>$12.99</td>
            </tr>
            <tr>
                <td>Salmon (per lb)</td>
                <td>$7.99 (Frozen)</td>
                <td>$11.99 (Fresh)</td>
            </tr>
            <tr>
                <td>Canned Tuna (per 5oz can)</td>
                <td>$0.69</td>
                <td>$0.99</td>
            </tr>
            <tr>
                <td>Ground Turkey 93/7 (per lb)</td>
                <td>$3.49</td>
                <td>$4.49</td>
            </tr>
            <tr>
                <td>Ground Beef 80/20 (per lb)</td>
                <td>$4.49</td>
                <td>$5.29</td>
            </tr>
            <tr>
                <td>Pork Chops (per lb)</td>
                <td>$3.79</td>
                <td>$4.59</td>
            </tr>
        </table>
        <p>Note: Prices are estimates as of March 2025; actual costs may vary by location.</p>
    </div>

    <script>
        function enterSite() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('main').style.display = 'block';
        }

        function showWorkout(day) {
            closeAllPopups();
            document.getElementById(day).style.display = 'block';
        }

        function showGroceryList(store) {
            closeAllPopups();
            document.getElementById(store + '-grocery').style.display = 'block';
        }

        function showPriceComparison() {
            closeAllPopups();
            document.getElementById('price-comparison').style.display = 'block';
        }

        function closePopup(id) {
            document.getElementById(id).style.display = 'none';
        }

        function closeAllPopups() {
            document.querySelectorAll('.workout-popup, .grocery-popup').forEach(popup => {
                popup.style.display = 'none';
            });
        }

        const workoutProgression = {
            'Monday': ['Monday', 'Monday', 'Alt1', 'Alt8'],
            'Tuesday': ['Tuesday', 'Tuesday', 'Alt3', 'Alt4'],
            'Wednesday': ['Wednesday', 'Wednesday', 'Alt2', 'Alt9'],
            'Thursday': ['Thursday', 'Thursday', 'Alt6', 'Alt10'],
            'Friday': ['Friday', 'Friday', 'Alt5', 'Alt2'],
            'Saturday': ['Saturday', 'Saturday', 'Alt4', 'Alt8'],
            'Sunday': ['Sunday', 'Sunday', 'Alt7', 'Alt3']
        };

        let skipCount = {};

        function skipWorkout(day) {
            skipCount[day] = (skipCount[day] || 0) + 1;
            const progression = workoutProgression[day];
            const nextWorkout = progression[Math.min(skipCount[day], progression.length - 1)];
            closePopup(day);
            showWorkout(nextWorkout);
        }

        const allWorkouts = [
            { day: 'Monday', warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>KB Swings: 20 lbs, 3x12</li><li>DB Thrusters: 15 lbs each, 3x10</li><li>Jump Squats: Bodyweight, 3x12</li><li>Plank Rows: 15 lbs each, 3x10</li><li>DB Shoulder Press: 15 lbs each, 3x10</li><li>Russian Twists: 10 lbs, 3x12</li>' },
            { day: 'Tuesday', warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>Goblet Squats (KB): 25 lbs, 3x12</li><li>DB Romanian Deadlifts: 20 lbs each, 3x10</li><li>DB Shoulder Press: 15 lbs each, 3x10</li><li>KB Swings: 20 lbs, 3x12</li><li>DB Bent-Over Rows: 20 lbs each, 3x10</li><li>Plank Rows: 15 lbs each, 3x10</li>' },
            { day: 'Wednesday', warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>KB Snatch: 15 lbs, 3x10</li><li>DB Chest Press: 20 lbs each, 3x10</li><li>Jump Lunges: Bodyweight, 3x12</li><li>KB Deadlifts: 25 lbs, 3x10</li><li>DB Reverse Flys: 10 lbs each, 3x12</li><li>Plank to Push-Ups: Bodyweight, 3x10</li>' },
            { day: 'Thursday', warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>KB Deadlifts: 25 lbs, 3x10</li><li>DB Thrusters: 15 lbs each, 3x10</li><li>KB Snatch: 15 lbs, 3x10</li><li>Jump Squats: 10 lbs, 3x12</li><li>Russian Twists: 10 lbs, 3x12</li><li>Plank to Push-Ups: Bodyweight, 3x10</li>' },
            { day: 'Friday', warmup: '<li>High Knees: 3x30 sec</li>', workout: '<li>Bulgarian Split Squats: 20 lbs each, 3x10</li><li>KB Sumo Deadlifts: 30 lbs, 3x12</li><li>DB Step-Ups: 15 lbs each, 3x10</li><li>DB Hip Thrusts: 25 lbs, 3x12</li><li>KB Goblet Cossack Squat: 20 lbs, 3x10</li><li>Jump Lunges: Bodyweight, 3x12</li>' },
            { day: 'Saturday', warmup: '<li>Jump Rope: 3x1 min</li>', workout: '<li>KB Clean & Press: 20 lbs, 3x10</li><li>DB Lateral Lunges: 15 lbs each, 3x12</li><li>DB Chest Press: 20 lbs each, 3x10</li><li>KB Turkish Get-Ups: 15 lbs, 3x8</li><li>DB Hanging Knee Raises: 10 lbs, 3x12</li><li>KB Plank Drags: 15 lbs, 3x10</li>' },
            { day: 'Sunday', warmup: '<li>Plank Hold: 3x30 sec</li>', workout: '<li>KB Russian Twists: 15 lbs, 3x12</li><li>DB Side Plank Hip Dips: 10 lbs, 3x10</li><li>KB Farmers Carry: 20 lbs each, 3x30s</li><li>Hollow Body Hold: Bodyweight, 3x45s</li><li>Bicycle Crunches: Bodyweight, 3x20</li>' }
        ];

        let currentAllIndex = 0;

        function showAllWorkouts(index) {
            closeAllPopups();
            if (index < 0) index = allWorkouts.length - 1;
            if (index >= allWorkouts.length) index = 0;
            currentAllIndex = index;
            const workout = allWorkouts[index];
            document.getElementById('all-workout-content').innerHTML = `
                <h3>${workout.day}</h3>
                <h4>Warmup</h4>
                <ul>${workout.warmup}</ul>
                <h4>Workout</h4>
                <ul>${workout.workout}</ul>
            `;
            document.getElementById('all-workouts').style.display = 'block';
        }

        const quotes = [
            "¡You’re a barbell badass—keep shaking it!",
            "Sweat now, shine later—Raeanne’s way!",
            "No nicotine, just gains—crush it!",
            "Lift heavy, live light—you’ve got this!",
            "Every rep is a step to your throne, Queen!"
        ];

        function showMotivation() {
            closeAllPopups();
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
            document.getElementById('quote').innerText = randomQuote;
            document.getElementById('motivate').style.display = 'block';
        }

        // Initialize page
        document.getElementById('welcome').style.display = 'block';
        document.getElementById('main').style.display = 'none';
    </script>
</body>
</html>
