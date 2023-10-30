---
layout: default
title: Your Impact
---

## How Climate Change Causes Lung Cancer

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

## Enter a state name and see how many cases they have! 

<head>
    <title>State Input</title>
</head>
<body>
    <h1>Enter a State Name</h1>
    <form id="stateForm">
        <input type="text" id="stateInput" placeholder="Enter a state name">
        <button type="submit">Submit</button>
    </form>

<div id="result">
    <!-- The result from the backend will be displayed here -->
    <p id="deathCancerData"></p>
    <p id="totalPopulationData"></p>
</div>

<script>
    // Listen for the form submission
    document.getElementById('stateForm').addEventListener('submit', function (e) {
        e.preventDefault(); // Prevent the default form submission
        // Get the state name from the input field
        const stateName = document.getElementById('stateInput').value;
        // Send the stateName to the backend using a fetch request
        fetch(`http://localhost:5000/api/data/state/${stateName}`, {
            method: 'GET',
            headers: {
                'Content-Type': 'application/json',
            }
        })
        .then(response => response.json())
        .then(data => {
            // Display the data in the corresponding elements
            document.getElementById('deathCancerData').textContent = `Total amount of death from lung cancer: ${data['Total amount of death from lung cancer']}`;
            document.getElementById('totalPopulationData').textContent = `Total Population: ${data['TotalPopulation']}`;
        })
        .catch(error => {
            console.error('Error:', error);
        });
    });
</script>
</body>






