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

    <!-- Raeanne’s Main Workouts -->
    <div class="workout-popup" id="Monday">
        <span class="close-btn" onclick="closePopup('Monday')">X</span>
        <h2>Monday: Chest & Triceps</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Incline Press: 20 lbs, 3x12</li>
            <li>DB Floor Flys: 15 lbs, 3x10</li>
            <li>Overhead DB Tricep Ext: 20 lbs, 3x10</li>
            <li>DB Close Grip Press: 25 lbs, 3x11</li>
            <li>DB Tricep Dips (on bench): 15 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Sunday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Monday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Tuesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Tuesday">
        <span class="close-btn" onclick="closePopup('Tuesday')">X</span>
        <h2>Tuesday: Back & Biceps</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Renegade Rows: 20 lbs, 3x10</li>
            <li>DB Reverse Flys: 12 lbs, 3x12</li>
            <li>DB Concentration Curls: 15 lbs, 3x10</li>
            <li>DB Single Arm Pulls: 25 lbs, 3x12</li>
            <li>DB Zottman Curls: 12 lbs, 3x8</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Monday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Tuesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Wednesday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Wednesday">
        <span class="close-btn" onclick="closePopup('Wednesday')">X</span>
        <h2>Wednesday: Legs Day 1</h2>
        <h3>Warmup (5-10 bolsillo min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Reverse Lunges: 20 lbs each, 3x10</li>
            <li>DB Sumo Deadlifts: 30 lbs, 3x12</li>
            <li>DB Side Step-Ups: 15 lbs each, 3x10</li>
            <li>DB Bulgarian Split Squats: 20 lbs each, 3x8</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Tuesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Wednesday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Thursday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Thursday">
        <span class="close-btn" onclick="closePopup('Thursday')">X</span>
        <h2>Thursday: Shoulders</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Shoulder Rolls: 2x15</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Military Press: 15 lbs, 3x10</li>
            <li>DB Rear Delt Raises: 10 lbs, 3x12</li>
            <li>DB Lateral Raises: 10 lbs, 3x10</li>
            <li>DB Face Pulls (w/ resistance band): 3x12</li>
            <li>DB Shrugs: 25 lbs, 3x15</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Wednesday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Thursday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Friday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Friday">
        <span class="close-btn" onclick="closePopup('Friday')">X</span>
        <h2>Friday: Legs Day 2</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Walking Lunges: 2x10</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Hip Thrusts: 30 lbs, 3x12</li>
            <li>DB Romanian Deadlifts: 25 lbs each, 3x10</li>
            <li>DB Goblet Squats: 25 lbs, 3x10</li>
            <li>DB Calf Raises: 20 lbs each, 3x15</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Thursday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Friday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Saturday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Saturday">
        <span class="close-btn" onclick="closePopup('Saturday')">X</span>
        <h2>Saturday: Full Body Mix</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jump Rope (or mimic): 3x1 min</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Thrusters: 20 lbs, 3x10</li>
            <li>DB Bent Over Rows: 25 lbs, 3x12</li>
            <li>DB Walking Lunges: 15 lbs each, 3x10</li>
            <li>DB Arnold Press: 12 lbs, 3x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Friday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Saturday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Sunday')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Sunday">
        <span class="close-btn" onclick="closePopup('Sunday')">X</span>
        <h2>Sunday: Core & Recovery</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Plank Hold: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Woodchoppers: 15 lbs, 3x12</li>
            <li>DB Side Bends: 20 lbs, 3x15</li>
            <li>DB Plank Rows: 15 lbs, 3x10</li>
            <li>DB Weighted Sit-Ups: 10 lbs, 3x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="showWorkout('Saturday')">◄ Back</button>
            <button class="skip-btn" onclick="skipWorkout('Sunday')">Skip</button>
            <button class="nav-btn" onclick="showWorkout('Monday')">Next ►</button>
        </div>
    </div>

    <!-- Alternate Workouts (More Variations) -->
    <div class="workout-popup" id="Alt1">
        <span class="close-btn" onclick="closePopup('Alt1')">X</span>
        <h2>Chest & Triceps (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Circles: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Decline Press: 20 lbs, 4x10</li>
            <li>DB Tricep Overhead: 15 lbs, 4x12</li>
            <li>DB Chest Flys: 15 lbs, 4x10</li>
            <li>DB Tricep Pushdowns (w/ band): 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt1')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt1')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt1')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt2">
        <span class="close-btn" onclick="closePopup('Alt2')">X</span>
        <h2>Back & Biceps (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Dead Hangs: 3x20 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Underhand Rows: 25 lbs, 4x10</li>
            <li>DB Hammer Curls: 15 lbs, 4x12</li>
            <li>DB Face Pulls: 10 lbs, 4x12</li>
            <li>DB Chin-Up Holds (w/ bar): 4x15 sec</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt2')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt2')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt2')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt3">
        <span class="close-btn" onclick="closePopup('Alt3')">X</span>
        <h2>Legs (Alt 1)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Leg Swings: 2x15</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Front Squats: 25 lbs, 4x10</li>
            <li>DB Single-Leg RDLs: 20 lbs each, 4x10</li>
            <li>DB Lateral Lunges: 15 lbs each, 4x12</li>
            <li>DB Wall Sits (w/ weight): 20 lbs, 4x30 sec</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt3')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt3')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt3')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt4">
        <span class="close-btn" onclick="closePopup('Alt4')">X</span>
        <h2>Shoulders (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Pike Push-Ups: 15 lbs, 4x10</li>
            <li>DB Front Raises: 10 lbs, 4x12</li>
            <li>DB Y-Raises: 8 lbs, 4x12</li>
            <li>DB Shoulder Circles: 10 lbs, 4x15</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt4')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt4')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt4')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt5">
        <span class="close-btn" onclick="closePopup('Alt5')">X</span>
        <h2>Legs (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Butt Kicks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Step-Back Lunges: 20 lbs each, 4x10</li>
            <li>DB Glute Bridges: 30 lbs, 4x12</li>
            <li>DB Curtsy Lunges: 15 lbs each, 4x10</li>
            <li>DB Donkey Kicks (w/ weight): 10 lbs, 4x12</li>
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
            <li>DB Clean & Press: 20 lbs, 4x10</li>
            <li>DB Deadlift to Row: 25 lbs, 4x10</li>
            <li>DB Squat to Overhead: 15 lbs, 4x12</li>
            <li>DB Burpee Press: 10 lbs, 4x8</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt6')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt6')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt6')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt7">
        <span class="close-btn" onclick="closePopup('Alt7')">X</span>
        <h2>Core (Alt)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Plank Hold: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Russian Twists: 15 lbs, 4x15</li>
            <li>DB Leg Raises: 10 lbs, 4x12</li>
            <li>DB Bicycle Crunches: 10 lbs, 4x20</li>
            <li>DB Side Plank Rotations: 12 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt7')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt7')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt7')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt8">
        <span class="close-btn" onclick="closePopup('Alt8')">X</span>
        <h2>Chest & Triceps (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Jumping Jacks: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Wide Press: 25 lbs, 4x10</li>
            <li>DB Tricep Kickbacks: 12 lbs, 4x12</li>
            <li>DB Pullover: 20 lbs, 4x10</li>
            <li>DB Bench Dips: 15 lbs, 4x12</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt8')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt8')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt8')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt9">
        <span class="close-btn" onclick="closePopup('Alt9')">X</span>
        <h2>Back & Biceps (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>Arm Swings: 2x20</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Pendlay Rows: 25 lbs, 4x10</li>
            <li>DB Preacher Curls: 15 lbs, 4x12</li>
            <li>DB Rear Delt Flys: 10 lbs, 4x12</li>
            <li>DB Drag Curls: 12 lbs, 4x10</li>
        </ul>
        <div class="nav-container">
            <button class="nav-btn" onclick="closePopup('Alt9')">◄ Back</button>
            <button class="skip-btn" onclick="closePopup('Alt9')">Skip</button>
            <button class="nav-btn" onclick="closePopup('Alt9')">Next ►</button>
        </div>
    </div>
    <div class="workout-popup" id="Alt10">
        <span class="close-btn" onclick="closePopup('Alt10')">X</span>
        <h2>Full Body (Alt 2)</h2>
        <h3>Warmup (5-10 min)</h3>
        <ul>
            <li>High Knees: 3x30 sec</li>
        </ul>
        <h3>Workout (45 min)</h3>
        <ul>
            <li>DB Snatch: 20 lbs, 4x10</li>
            <li>DB Single-Arm Press: 15 lbs, 4x12</li>
            <li>DB Squat Jumps: 10 lbs, 4x10</li>
            <li>DB Push-Up to Row: 15 lbs, 4x8</li>
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
            'Tuesday': ['Tuesday', 'Tuesday', 'Alt2', 'Alt9'],
            'Wednesday': ['Wednesday', 'Wednesday', 'Alt3', 'Alt5'],
            'Thursday': ['Thursday', 'Thursday', 'Alt4', 'Alt4'],
            'Friday': ['Friday', 'Friday', 'Alt5', 'Alt5'],
            'Saturday': ['Saturday', 'Saturday', 'Alt6', 'Alt10'],
            'Sunday': ['Sunday', 'Sunday', 'Alt7', 'Alt7']
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
            { warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>DB Incline Press: 20 lbs, 3x12</li><li>DB Floor Flys: 15 lbs, 3x10</li><li>Overhead DB Tricep Ext: 20 lbs, 3x10</li><li>DB Close Grip Press: 25 lbs, 3x11</li><li>DB Tricep Dips (on bench): 15 lbs, 3x12</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Renegade Rows: 20 lbs, 3x10</li><li>DB Reverse Flys: 12 lbs, 3x12</li><li>DB Concentration Curls: 15 lbs, 3x10</li><li>DB Single Arm Pulls: 25 lbs, 3x12</li><li>DB Zottman Curls: 12 lbs, 3x8</li>' },
            { warmup: '<li>High Knees: 3x30 sec</li>', workout: '<li>DB Reverse Lunges: 20 lbs each, 3x10</li><li>DB Sumo Deadlifts: 30 lbs, 3x12</li><li>DB Side Step-Ups: 15 lbs each, 3x10</li><li>DB Bulgarian Split Squats: 20 lbs each, 3x8</li>' },
            { warmup: '<li>Shoulder Rolls: 2x15</li>', workout: '<li>DB Military Press: 15 lbs, 3x10</li><li>DB Rear Delt Raises: 10 lbs, 3x12</li><li>DB Lateral Raises: 10 lbs, 3x10</li><li>DB Face Pulls (w/ band): 3x12</li><li>DB Shrugs: 25 lbs, 3x15</li>' },
            { warmup: '<li>Walking Lunges: 2x10</li>', workout: '<li>DB Hip Thrusts: 30 lbs, 3x12</li><li>DB Romanian Deadlifts: 25 lbs each, 3x10</li><li>DB Goblet Squats: 25 lbs, 3x10</li><li>DB Calf Raises: 20 lbs each, 3x15</li>' },
            { warmup: '<li>Jump Rope (or mimic): 3x1 min</li>', workout: '<li>DB Thrusters: 20 lbs, 3x10</li><li>DB Bent Over Rows: 25 lbs, 3x12</li><li>DB Walking Lunges: 15 lbs each, 3x10</li><li>DB Arnold Press: 12 lbs, 3x10</li>' },
            { warmup: '<li>Plank Hold: 3x30 sec</li>', workout: '<li>DB Woodchoppers: 15 lbs, 3x12</li><li>DB Side Bends: 20 lbs, 3x15</li><li>DB Plank Rows: 15 lbs, 3x10</li><li>DB Weighted Sit-Ups: 10 lbs, 3x12</li>' },
            { warmup: '<li>Arm Circles: 2x20</li>', workout: '<li>DB Decline Press: 20 lbs, 4x10</li><li>DB Tricep Overhead: 15 lbs, 4x12</li><li>DB Chest Flys: 15 lbs, 4x10</li><li>DB Tricep Pushdowns (w/ band): 4x12</li>' },
            { warmup: '<li>Dead Hangs: 3x20 sec</li>', workout: '<li>DB Underhand Rows: 25 lbs, 4x10</li><li>DB Hammer Curls: 15 lbs, 4x12</li><li>DB Face Pulls: 10 lbs, 4x12</li><li>DB Chin-Up Holds (w/ bar): 4x15 sec</li>' },
            { warmup: '<li>Leg Swings: 2x15</li>', workout: '<li>DB Front Squats: 25 lbs, 4x10</li><li>DB Single-Leg RDLs: 20 lbs each, 4x10</li><li>DB Lateral Lunges: 15 lbs each, 4x12</li><li>DB Wall Sits (w/ weight): 20 lbs, 4x30 sec</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Pike Push-Ups: 15 lbs, 4x10</li><li>DB Front Raises: 10 lbs, 4x12</li><li>DB Y-Raises: 8 lbs, 4x12</li><li>DB Shoulder Circles: 10 lbs, 4x15</li>' },
            { warmup: '<li>Butt Kicks: 3x30 sec</li>', workout: '<li>DB Step-Back Lunges: 20 lbs each, 4x10</li><li>DB Glute Bridges: 30 lbs, 4x12</li><li>DB Curtsy Lunges: 15 lbs each, 4x10</li><li>DB Donkey Kicks (w/ weight): 10 lbs, 4x12</li>' },
            { warmup: '<li>Dynamic Stretch: 2 min</li>', workout: '<li>DB Clean & Press: 20 lbs, 4x10</li><li>DB Deadlift to Row: 25 lbs, 4x10</li><li>DB Squat to Overhead: 15 lbs, 4x12</li><li>DB Burpee Press: 10 lbs, 4x8</li>' },
            { warmup: '<li>Plank Hold: 3x30 sec</li>', workout: '<li>DB Russian Twists: 15 lbs, 4x15</li><li>DB Leg Raises: 10 lbs, 4x12</li><li>DB Bicycle Crunches: 10 lbs, 4x20</li><li>DB Side Plank Rotations: 12 lbs, 4x10</li>' },
            { warmup: '<li>Jumping Jacks: 3x30 sec</li>', workout: '<li>DB Wide Press: 25 lbs, 4x10</li><li>DB Tricep Kickbacks: 12 lbs, 4x12</li><li>DB Pullover: 20 lbs, 4x10</li><li>DB Bench Dips: 15 lbs, 4x12</li>' },
            { warmup: '<li>Arm Swings: 2x20</li>', workout: '<li>DB Pendlay Rows: 25 lbs, 4x10</li><li>DB Preacher Curls: 15 lbs, 4x12</li><li>DB Rear Delt Flys: 10 lbs, 4x12</li><li>DB Drag Curls: 12 lbs, 4x10</li>' },
            { warmup: '<li>High Knees: 3x30 sec</li>', workout: '<li>DB Snatch: 20 lbs, 4x10</li><li>DB Single-Arm Press: 15 lbs, 4x12</li><li>DB Squat Jumps: 10 lbs, 4x10</li><li>DB Push-Up to Row: 15 lbs, 4x8</li>' }
        ];

        let currentAllIndex = 0;

        function showAllWorkouts(index) {
            closeAllPopups();
            if (index < 0) index = allWorkouts.length - 1;
            if (index >= allWorkouts.length) index = 0;
            currentAllIndex = index;
            const workout = allWorkouts[index];
            document.getElementById('all-workout-content').innerHTML = `
                <h3>Warmup (5-10 min)</h3><ul>${workout.warmup}</ul>
                <h3>Workout (45 min)</h3><ul>${workout.workout}</ul>
            `;
            document.getElementById('all-workouts').style.display = 'block';
        }

        const quotes = [
            "¡Raeanne, you’re shaking up the bar and the weights—nicotine-free badass!",
            "One year clean, less booze, all power—keep pouring strength, queen!",
            "From shaker to barbell, you’re a consistency legend—crush it!",
            "No vape, no shots, just gains—Raeanne, you’re unstoppable!",
            "Bartending boss dropping habits and lifting heavy—own it!",
            "Mix it, lift it, win it—Raeanne, you’re a sober strength titan!",
            "A year of freedom, a lifetime of power—keep the streak alive!",
            "Pour less, press more—Raeanne, you’re rewriting the recipe for strong!",
            "Nicotine’s out, muscle’s in—shake up your limits, bartender!",
            "¡Raeanne, you’re the cocktail of grit—one year down, forever to go!"
        ];

        function showMotivation() {
            closeAllPopups();
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
            document.getElementById('quote').innerText = randomQuote;
            document.getElementById('motivate').style.display = 'block';
        }
    </script>
</body>
</html>
