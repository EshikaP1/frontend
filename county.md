---
layout: default
title: Aerosol data
---
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

<!-- Add a separator or some text here if you want to separate the results -->

<h1>Enter a State Name</h1>
    <form id= "stateForm">
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
                            tooltips: {
                                callbacks: {
                                    label: function (tooltipItem, data) {
                                        const dataset = data.datasets[tooltipItem.datasetIndex];
                                        const total = dataset.data.reduce((prev, current) => prev + current);
                                        const currentValue = dataset.data[tooltipItem.index];
                                        const percentage = ((currentValue / total) * 100).toFixed(2);
                                        return `${data.labels[tooltipItem.index]}: ${percentage}%`;
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
                    // Create the pie chart for state data
                    const pieChartHtml = `
                        <h2>Lung Cancer Data in ${data.State}</h2>
                        <canvas id="stateLungCancerChart"></canvas>
                    `;
                    document.getElementById('statePieChart').innerHTML = pieChartHtml;

                    new Chart(document.getElementById('stateLungCancerChart'), {
                        type: 'pie',
                        data: {
                            labels: ['Total Deaths', 'Survivors'],
                            datasets: [{
                                data: [data['Total amount of death from lung cancer'], data['Total Population'] - data['Total amount of death from lung cancer']],
                                backgroundColor: ['red', 'green'],
                            }],
                        },
                        options: {
                            tooltips: {
                                callbacks: {
                                    label: function (tooltipItem, data) {
                                        return `${data.labels[tooltipItem.index]}: ${data.datasets[0].data[tooltipItem.index]}`;
                                    },
                                },
                            },
                            title: {
                                display: true,
                                text: `Lung Cancer Data in ${data.State}`,
                            },
                        },
                    });
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>
</html>