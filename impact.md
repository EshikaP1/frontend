---
layout: default
title: Your Impact
---

![Alt text](<images/Lung Cancer (3).png>)

Climate change does not directly cause lung cancer. Instead, lung cancer primarily results from exposure to carcinogens, with tobacco smoke being the leading risk factor. However, climate change can indirectly influence lung cancer risk through several mechanisms:

# Table of Contents

1. [Air Quality and Pollution](#air-quality-and-pollution)
2. [Wildfires](#wildfires)
3. [Vector-Borne Diseases](#vector-borne-diseases)
4. [Heat Stress](#heat-stress)
5. [Altered Allergen Distribution](#altered-allergen-distribution)



## Air Quality and Pollution

Climate change can exacerbate air pollution, which may contain fine particulate matter (PM2.5), ozone, and other pollutants harmful to respiratory health. Prolonged exposure to polluted air can increase the risk of lung cancer.

## Wildfires

Rising global temperatures and altered precipitation patterns can contribute to an increase in the frequency and intensity of wildfires. Wildfires release a range of harmful air pollutants, including particulate matter and volatile organic compounds. Prolonged exposure to wildfire smoke can harm lung health and potentially increase lung cancer risk.

## Vector-Borne Diseases

Climate change can expand the geographical range of certain disease vectors like mosquitoes. This can lead to an increased risk of vector-borne diseases such as malaria or Zika, which can impact lung health when these diseases affect the respiratory system.

## Heat Stress

Extreme heat events associated with climate change can lead to heat-related illnesses, potentially increasing the risk of respiratory infections that may, in some cases, contribute to lung cancer risk.

## Altered Allergen Distribution

Climate change can affect the distribution and prevalence of allergenic pollen-producing plants. For individuals with allergies or asthma, exposure to increased pollen can exacerbate respiratory issues. While allergies themselves are not a direct cause of lung cancer, ongoing respiratory inflammation from allergens can increase the risk of lung damage.

Addressing climate change is important for protecting public health and reducing the risk of various respiratory ailments.


<html>
<head>
    <title>Air Pollution Interactive</title>
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
        <h1>About Air Pollution</h1>
<p>Welcome to our interactive page about air pollution. Take our quiz and explore real-time air quality data below.</p>

 <div class="quiz-question">
            <p>1. What is the main source of indoor air pollution in many households?</p>
            <div class="quiz-options">
                <input type="radio" name="q1" value="a"> Smoking<br>
                <input type="radio" name="q1" value="b"> Outdoor air pollution<br>
                <input type="radio" name="q1" value="c"> Houseplants<br>
            </div>
            <div class="quiz-result" id="q1-result"></div>
        </div>

 <div class="quiz-question">
            <p>2. Which air pollutant is associated with the formation of acid rain?</p>
            <div class="quiz-options">
                <input type="radio" name="q2" value="a"> Carbon monoxide<br>
                <input type="radio" name="q2" value="b"> Sulfur dioxide<br>
                <input type="radio" name="q2" value="c"> Nitrogen oxide<br>
            </div>
            <div class="quiz-result" id="q2-result"></div>
        </div>

 <button onclick="submitQuiz()">Submit Quiz</button>

 <div id="chart-container">
            <h2>Real-time Air Quality</h2>
            <canvas id="airQualityChart" width="400" height="200"></canvas>
        </div>
    </div>

<script>
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
                        beginAtZero: true,
                        max: 100
                    }
                }
            }
        });
    </script>
</body>
</html>
