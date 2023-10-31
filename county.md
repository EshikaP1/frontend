---
layout: default
title: Aerosol data
---

<!DOCTYPE html>
<html>
<head>
    <title>County Input</title>
</head>
<body>
    <h1>Enter a County Name</h1>
    <form id="countyForm">
        <input type="text" id="countyInput" placeholder="Enter a county name">
        <button type="submit">Submit</button>
    </form>

    <div id="result">
        <!-- The result from the backend will be displayed here -->
        <p><strong>State:</strong> <span id="stateData"></span></p>
        <p><strong>County:</strong> <span id="countyData"></span></p>
        <p><strong>Year:</strong> <span id="yearData"></span></p>
        <p><strong>Days with AQI:</strong> <span id="daysWithAQIData"></span></p>
        <!-- Add more fields as needed -->
    </div>

    <script>
        document.getElementById('countyForm').addEventListener('submit', function (e) {
            e.preventDefault();
            const countyName = document.getElementById('countyInput').value;
            fetch(`http://localhost:5000/api/data/county/${countyName}`, {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json',
                }
            })
            .then(response => response.json())
            .then(data => {
                document.getElementById('stateData').textContent = data['State'];
                document.getElementById('countyData').textContent = data['County'];
                document.getElementById('yearData').textContent = data['Year'];
                document.getElementById('daysWithAQIData').textContent = data['Days with AQI'];
                // Add more lines for other fields
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>
</html>
