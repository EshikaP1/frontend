<!DOCTYPE html>
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
    <form id="stateForm">
        <input type="text" id="stateInput" placeholder="Enter a state name">
        <button type="submit">Submit</button>
    </form>
    <div id="stateResult">
        <!-- The result for state data from the backend will be displayed here -->
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
                        <p>Total Deaths from Lung Cancer: ${data["Total amount of death from lung cancer"]}</p>
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
