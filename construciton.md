<!DOCTYPE html>
<html>
<head>
    <title>Pie Chart</title>
</head>
<body>
    <div style="width: 400px; height: 400px;">
        <canvas id="pieChart"></canvas>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        fetch('/api/pie-chart-data')
            .then(response => response.json())
            .then(data => {
                const ctx = document.getElementById('pieChart').getContext('2d');
                const pieChart = new Chart(ctx, {
                    type: 'pie',
                    data: {
                        labels: data.labels,
                        datasets: [{
                            data: data.data,
                            backgroundColor: [
                                'red',
                                'green',
                                'blue',
                            ],
                        }],
                    },
                });
            });
    </script>
</body>
</html>
