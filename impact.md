---
layout: default
title: Your Impact
---
![Alt text](images/IMPACT.png)

<!-- Introduction and title of the page -->
Climate change does not directly cause lung cancer. Instead, lung cancer primarily results from exposure to carcinogens, with tobacco smoke being the leading risk factor. However, climate change can indirectly influence lung cancer risk through several mechanisms:

# <span style="color: #228B22"> Table of Contents </span>

<!-- Section title -->
1. [Air Quality and Pollution](#air-quality-and-pollution)
2. [Wildfires](#wildfires)
3. [Vector-Borne Diseases](#vector-borne-diseases)
4. [Heat Stress](#heat-stress)
5. [Altered Allergen Distribution](#altered-allergen-distribution)

<!-- Subsections related to climate change's impact on lung cancer -->

## <span style="color: #228B22"> Air Quality and Pollution </span>

<!-- Subsection title -->
Climate change can exacerbate air pollution, which may contain fine particulate matter (PM2.5), ozone, and other pollutants harmful to respiratory health. Prolonged exposure to polluted air can increase the risk of lung cancer.

## <span style="color: #228B22"> Wildfires </span>

<!-- Subsection title -->
Rising global temperatures and altered precipitation patterns can contribute to an increase in the frequency and intensity of wildfires. Wildfires release a range of harmful air pollutants, including particulate matter and volatile organic compounds. Prolonged exposure to wildfire smoke can harm lung health and potentially increase lung cancer risk.

## <span style="color: #228B22"> Vector-Borne Diseases </span>

<!-- Subsection title -->
Climate change can expand the geographical range of certain disease vectors like mosquitoes. This can lead to an increased risk of vector-borne diseases such as malaria or Zika, which can impact lung health when these diseases affect the respiratory system.

## <span style="color: #228B22"> Heat Stress </span>

<!-- Subsection title -->
Extreme heat events associated with climate change can lead to heat-related illnesses, potentially increasing the risk of respiratory infections that may, in some cases, contribute to lung cancer risk.

## <span style="color: #228B22"> Altered Allergen Distribution </span>

<!-- Subsection title -->
Climate change can affect the distribution and prevalence of allergenic pollen-producing plants. For individuals with allergies or asthma, exposure to increased pollen can exacerbate respiratory issues. While allergies themselves are not a direct cause of lung cancer, ongoing respiratory inflammation from allergens can increase the risk of lung damage.

<!-- A call to action and conclusion section -->
Addressing climate change is important for protecting public health and reducing the risk of various respiratory ailments.

<!-- HTML code section begins -->

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
<div class="quiz-question">
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
<button id="submitQuizButton">Submit Quiz</button>

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

    // Add an event listener to the submit button
    const submitButton = document.getElementById("submitQuizButton");
    submitButton.addEventListener("click", submitQuiz);

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
                y: {} // Add appropriate configuration here
            }
        }
    });
</script>

<html>
<head>
    <title>Real-time Air Quality and Lung Cancer Rates</title>
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
        #chart-container {
            margin-top: 30px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Real-time Air Quality and Lung Cancer Rates</h1>

   <!-- Chart for real-time air quality data -->
  <div id="airQualityChartContainer">
            <h2>Real-time Air Quality Data</h2>
            <canvas id="airQualityChart" width="400" height="200"></canvas>
        </div>

 <!-- Chart for comparing lung cancer rates of 5 countries -->
 <div id="lungCancerChartContainer">
            <h2>Lung Cancer Rates in 5 Countries</h2>
            <canvas id="lungCancerChart" width="400" height="200"></canvas>
        </div>
    </div>

<script>
        // Real-time air quality data
        const airQualityData = {
            labels: ['PM2.5', 'PM10', 'NO2', 'SO2', 'CO'],
            datasets: [{
                label: 'Air Quality Index',
                data: [25, 40, 20, 15, 10],
                backgroundColor: 'rgba(75, 192, 192, 0.7)',
                borderColor: 'rgba(75, 192, 192, 1)',
                borderWidth: 1,
            }],
        };

        // Air pollution in 5 countries
        const lungCancerData = {
            labels: ['India', 'China', 'Bangladesh', 'Pakistan', 'Nepal'],
            datasets: [{
                label: '5 Countries with the Worst Air Pollution Rates',
                data: [500, 200, 200, 200, 150],
                backgroundColor: 'rgba(255, 99, 132, 0.7)',
                borderColor: 'rgba(255, 99, 132, 1)',
                borderWidth: 1,
            }],
        };

        // Create real-time air quality chart
        const airQualityCtx = document.getElementById('airQualityChart').getContext('2d');
        new Chart(airQualityCtx, {
            type: 'bar',
            data: airQualityData,
            options: {
                scales: {
                    y: {
                        beginAtZero: true,
                    },
                },
            },
        });

        // Create lung cancer rates chart
        const lungCancerCtx = document.getElementById('lungCancerChart').getContext('2d');
        new Chart(lungCancerCtx, {
            type: 'bar',
            data: lungCancerData,
            options: {
                scales: {
                    y: {
                        beginAtZero: true,
                    },
                },
            },
        });
    </script>
</body>
</html>
