---
layout: default
title: Aerosol data
---


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
    </div>

<script>
    // Listen for the form submission
    document.getElementById('countyForm').addEventListener('submit', function (e) {
    e.preventDefault(); // Prevent the default form submission
    // Get the county name from the input field
    const countyName = document.getElementById('countyInput').value;
    // Send the countyName to the backend using a fetch request
    fetch(`http://localhost:5000/api/data/county/${countyName}`, {
        method: 'GET',
        headers: {
        'Content-Type': 'application/json',
            }
            })
            .then(response => {
                if (response.status === 404) {
                    // Handle the case when data is not found
                    return { error: "County data not found" };
                }
                return response.json();
            })
            .then(data => {
                if (data.error) {
                    // Display the error message
                    document.getElementById('result').textContent = `Error: ${data.error}`;
                } else {
                    // Display the county data
                    const resultHtml = `
                        <p>County: ${data.County}</p>
                        <p>Year: ${data.Year}</p>
                        <p>Days with AQI: ${data["Days with AQI"]}</p>
                        <!-- Add more fields as needed -->
                    `;
                    document.getElementById('result').innerHTML = resultHtml;
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>
</html>