---
layout: default
title: Quizzes
# course: compsci
---


# <span style="color: #228B22"> Lung Cancer Quiz </span>


<html>
<head>
    <title>Lung Cancer Quiz</title>
</head>
<body>
    <h1>Lung Cancer Quiz</h1>

<div id="questions">
    <!-- Question 1 -->
    <div class="question">
        <p>Which is the most common type of lung cancer?</p>
        <div class="options">
            <input type="radio" name="q1" id="q1-option1" data-correct="true">
            <label for="q1-option1">Non-Small Cell Lung Cancer (NSCLC)</label><br>
            <input type="radio" name="q1" id="q1-option2">
            <label for="q1-option2">Small Cell Lung Cancer (SCLC)</label><br>
        </div>
        <div class="result"></div>
    </div>

<!-- Question 2 -->
<div class="question">
        <p>What is the primary cause of lung cancer?</p>
        <div class="options">
            <input type="radio" name="q2" id="q2-option1" data-correct="true">
            <label for="q2-option1">Exposure to carcinogens</label><br>
            <input type="radio" name="q2" id="q2-option2">
            <label for="q2-option2">Genetic factors</label><br>
            <input type="radio" name="q2" id="q2-option3">
            <label for="q2-option3">Diet</label><br>
        </div>
        <div class="result"></div>
    </div>

<!-- Question 3 -->
<div class="question">
        <p>What are common symptoms of lung cancer?</p>
        <div class="options">
            <input type="radio" name="q3" id="q3-option1">
            <label for="q3-option1">Fever</label><br>
            <input type="radio" name="q3" id="q3-option2" data-correct="true">
            <label for="q3-option2">Coughing up blood</label><br>
            <input type="radio" name="q3" id="q3-option3">
            <label for="q3-option3">Unexplained weight loss</label><br>
            <input type="radio" name="q3" id="q3-option4">
            <label for="q3-option4">Shortness of breath</label><br>
        </div>
        <div class="result"></div>
    </div>
</div>

<script>
    const radioButtons = document.querySelectorAll('input[type="radio"]');
    radioButtons.forEach(radio => {
        radio.addEventListener('change', () => {
            checkAnswer(radio);
        });
    });

    function checkAnswer(radio) {
        const questionDiv = radio.closest('.question');
        const correctRadio = questionDiv.querySelector('input[data-correct="true"]');
        const resultElement = questionDiv.querySelector('.result');

        if (radio === correctRadio) {
            resultElement.textContent = "Correct answer: " + correctRadio.nextElementSibling.textContent;
        } else {
            resultElement.textContent = "Incorrect. Correct answer: " + correctRadio.nextElementSibling.textContent;
        }
    }
</script>
</body>
</html>

<html>
<head>
    <title>How Climate Change Friendly Are You?</title>
    <style>
        body {
            text-align: center;
        }
        #game-container {
            margin: 0 auto;
            width: 400px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            margin: 5px;
        }
        #info-box {
            display: none;
        }
    </style>
</head>
<body>
    <h1>How Climate Change friendly are you?</h1>
    <div id="game-container">
        <h2>Choose Your Scenario</h2>
        <p>Select a scenario and take actions to combat climate change.</p>
        <button id="scenario-1-button" onclick="startScenario(1)">Scenario 1: Energy Efficiency</button>
        <button id="scenario-2-button" onclick="startScenario(2)">Scenario 2: Sustainable Transportation</button>
        <button id="scenario-3-button" onclick="startScenario(3)">Scenario 3: Renewable Energy</button>
        <button id="scenario-4-button" onclick="startScenario(4)">Scenario 4: Green Diet</button>
        <button id="scenario-5-button" onclick="startScenario(5)">Scenario 5: Reforestation</button>
    </div>
    <div id="info-box">
        <p id="info-text"></p>
        <button id="continue-button" onclick="resetGame()">Continue</button>
    </div>


<script>
        let environmentalScore = 50;
        let currentScenario = 0;


        const scenarios = [
            null,
            {
                name: "Energy Efficiency",
                actions: [
                    { name: "Upgrade home insulation", impact: 10 },
                    { name: "Switch to LED lights", impact: 5 },
                    { name: "Use programmable thermostat", impact: 5 }
                ]
            },
            {
                name: "Sustainable Transportation",
                actions: [
                    { name: "Ride a bicycle", impact: 10 },
                    { name: "Use public transport", impact: 5 },
                    { name: "Carpool with others", impact: 5 }
                ]
            },
            {
                name: "Renewable Energy",
                actions: [
                    { name: "Install solar panels", impact: 10 },
                    { name: "Support wind energy projects", impact: 5 },
                    { name: "Switch to a green energy provider", impact: 5 }
                ]
            },
            {
                name: "Green Diet",
                actions: [
                    { name: "Reduce meat consumption", impact: 10 },
                    { name: "Eat more plant-based foods", impact: 5 },
                    { name: "Reduce food waste", impact: 5 }
                ]
            },
            {
                name: "Reforestation",
                actions: [
                    { name: "Plant trees in your community", impact: 10 },
                    { name: "Support reforestation organizations", impact: 5 },
                    { name: "Participate in tree-planting events", impact: 5 }
                ]
            }
        ];


        function startScenario(scenarioNumber) {
            currentScenario = scenarioNumber;
            displayInfo(`You've chosen ${scenarios[scenarioNumber].name} scenario.`);
            document.getElementById("game-container").style.display = "none";
            showScenarioActions(scenarios[scenarioNumber].actions);
        }


        function showScenarioActions(actions) {
            const actionButtons = actions.map(action => {
                return `<button onclick="takeAction('${action.name}', ${action.impact})">${action.name}</button>`;
            });


            const actionButtonsHTML = actionButtons.join('<br>');
            document.getElementById("info-text").innerHTML = `Select an action to combat climate change:<br>${actionButtonsHTML}`;
        }


        function takeAction(action, impact) {
            environmentalScore += impact;
            displayInfo(`You took the action: "${action}" and your environmental score is now ${environmentalScore}.`);
        }


        function displayInfo(text) {
            document.getElementById("info-box").style.display = "block";
            document.getElementById("info-text").innerText = text;
        }


        function resetGame() {
            currentScenario = 0;
            environmentalScore = 50;
            document.getElementById("game-container").style.display = "block";
            document.getElementById("info-box").style.display = "none";
        }
    </script>

<html>
<head>
    <title>County and State Input</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.0/chart.min.js"></script>
</head>
<body>
    <h1>Enter a County Name!</h1>
    <form id="countyForm">
        <input type="text" id="countyInput" placeholder="Enter a county name">
        <button type="submit">Submit</button>
    </form>
    <div id="countyResult">
        <!-- The result for county data from the backend will be displayed here -->
    </div>
    <div id="countyPieChart">
        <!-- The pie chart for county data will be displayed here -->
    </div>


<!-- Add a separator or some other text here if you want to separate the results -->
 <h1>Enter a State Name</h1>
    <form id="stateForm">
        <input type="text" id="stateInput" placeholder="Enter a state name">
        <button type="submit">Submit</button>
    </form>
    <div id="stateResult">
        <!-- The result for state data from the backend will be displayed here -->
    </div>
    <div id="statePieChart">
        <!-- The pie chart for state data will be displayed here -->
    </div>


 <script>
        // County Form Submission
        document.getElementById('countyForm').addEventListener('submit', function (e) {
            e.preventDefault();
            const countyName = document.getElementById('countyInput').value;
            fetch(`http://localhost:5000/api/data/county/county/${countyName}`, {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json',
                }
            })
            .then(response => {
                if (response.status === 404) {
                    return { error: "County data not found" };
                }
                return response.json();
            })
            .then(data => {
                if (data.error) {
                    document.getElementById('countyResult').textContent = `Error: ${data.error}`;
                } else {
                    // Create the pie chart for county data
                    const pieChartHtml = `
                        <h2>Air Pollution in ${data.County}</h2>
                        <canvas id="countyAirPollutionChart"></canvas>
                    `;
                    document.getElementById('countyPieChart').innerHTML = pieChartHtml;


                    new Chart(document.getElementById('countyAirPollutionChart'), {
                        type: 'pie',
                        data: {
                            labels: ['Good Days', 'Moderate Days', 'Unhealthy Days', 'Very Unhealthy Days', 'Hazardous Days'],
                            datasets: [{
                                data: [data['Good Days'], data['Moderate Days'], data['Unhealthy Days'], data['Very Unhealthy Days'], data['Hazardous Days']],
                                backgroundColor: ['green', 'yellow', 'orange', 'red', 'purple'],
                            }],
                        },
                        options: {
                            plugins: {
                                tooltip: {
                                    callbacks: {
                                        label: function (context) {
                                            const label = context.label || '';
                                            const value = context.parsed || 0;
                                            const total = context.dataset.data.reduce((acc, val) => acc + val, 0);
                                            const percentage = ((value / total) * 100).toFixed(2);
                                            return `${label}: ${percentage}%`;
                                        },
                                    },
                                },
                            },
                            title: {
                                display: true,
                                text: `Air Pollution in ${data.County}`,
                            },
                        },
                    });
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });


        // State Form Submission
        document.getElementById('stateForm').addEventListener('submit', function (e) {
            e.preventDefault();
            const stateName = document.getElementById('stateInput').value;
            fetch(`http://localhost:5000/api/data/cancer/cancer/state/${stateName}`, {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json',
                }
            })
            .then(response => {
                if (response.status === 404) {
                    return { error: "State data not found" };
                }
                return response.json();
            })
            .then(data => {
                if (data.error) {
                    document.getElementById('stateResult').textContent = `Error: ${data.error}`;
                } else {
                    const resultHtml = `
                        <p>Total Population: ${data.TotalPopulation}</p>
                        <p>Total Death rate from Lung Cancer: ${data["Total amount of death from lung cancer"]}</p>
                    `;
                    document.getElementById('stateResult').innerHTML = resultHtml;
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>
</html>

<html>
<head>
    <title>Air Pollution Quiz!!</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* Add your CSS styles here */
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        .quiz-question {
            margin: 20px 0;
        }
        .quiz-options input {
            margin-right: 10px;
        }
        .quiz-result {
            font-weight: bold;
        }
        #chart-container {
            margin-top: 30px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Air Pollution Quiz!!</h1>
<p>Quiz time! Answer the questions below to the best of your ability. If you get it wrong, you can press other options to see the right.</p>

<!-- Quiz form section -->
 <div class "quiz-question">
            <p>1. What is the main source of indoor air pollution in many households?</p>
            <div class="quiz-options">
                <input type="radio" name="q1" value="a"> Smoking<br>
                <input type="radio" name="q1" value="b"> Outdoor air pollution<br>
                <input type="radio" name="q1" value="c"> Houseplants<br>
            </div>
            <div class="quiz-result" id="q1-result"></div>
        </div>

<!-- Quiz question 2 -->
 <div class="quiz-question">
            <p>2. Which air pollutant is associated with the formation of acid rain?</p>
            <div class="quiz-options">
                <input type="radio" name="q2" value="a"> Carbon monoxide<br>
                <input type="radio" name="q2" value="b"> Sulfur dioxide<br>
                <input type="radio" name="q2" value="c"> Nitrogen oxide<br>
            </div>
            <div class="quiz-result" id="q2-result"></div>
        </div>

<!-- Button to submit the quiz -->
 <button onclick="submitQuiz()">Submit Quiz</button>

<!-- Chart for air quality -->
 <div id="chart-container">
            <h2>Real-time Air Quality</h2>
            <canvas id="airQualityChart" width="400" height="200"></canvas>
        </div>
    </div>

<!-- JavaScript code section -->
<script>
        // JavaScript function for submitting the quiz
        function submitQuiz() {
            // Get the selected answers
            const q1Answer = document.querySelector('input[name="q1"]:checked');
            const q2Answer = document.querySelector('input[name="q2"]:checked');

            // Check answers and display results
            if (q1Answer && q2Answer) {
                if (q1Answer.value === "a") {
                    document.getElementById("q1-result").textContent = "Correct";
                } else {
                    document.getElementById("q1-result").textContent = "Incorrect";
                }

                if (q2Answer.value === "b") {
                    document.getElementById("q2-result").textContent = "Correct";
                } else {
                    document.getElementById("q2-result").textContent = "Incorrect";
                }
            }
        }

        // Create a simple air quality chart
        const ctx = document.getElementById('airQualityChart').getContext('2d');
        const airQualityChart = new Chart(ctx, {
            type: 'bar',
            data: {
                labels: ['PM2.5', 'PM10', 'NO2', 'SO2', 'CO'],
                datasets: [{
                    label: 'Air Quality Index',
                    data: [25, 40, 20, 15, 10],
                    backgroundColor: 'rgba(75, 192, 192, 0.7)',
                    borderColor: 'rgba(75, 192, 192, 1)',
                    borderWidth: 1,
                }]
            },
            options: {
                scales: {
                    y: {
                       


