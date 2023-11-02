<!DOCTYPE html>
<html>
<head>
    <title>County and State Input</title>
</head>
<body>
    <form id="countyForm">
        <!-- County Form Submission -->
        <label for="countyInput">Enter County Name:</label>
        <input type="text" id="countyInput" name="countyInput">
        <button type="submit">Submit</button>
    </form>

<div id="countyResult"></div>
    <canvas id="countyPieChart" width="600" height="400" style="display: none;"></canvas>
    <canvas id="countyBarChart" width="800" height="400" style="display: none;"></canvas>

<script>
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
                    document.getElementById('countyPieChart').style.display = 'none';
                    document.getElementById('countyBarChart').style.display = 'none';
                } else if (data) {
                    document.getElementById('countyResult').textContent = '';
                    document.getElementById('countyPieChart').style.display = 'block';
                    document.getElementById('countyBarChart').style.display = 'block';

                    // Create the pie chart for county data
                    createPieChart(data);

                    // Create the bar chart for additional data
                    createBarChart(data);
                }
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });

        function createPieChart(data) {
            const pieCanvas = document.getElementById('countyPieChart');
            const ctx = pieCanvas.getContext('2d');
            const labels = ['Good Days', 'Moderate Days', 'Unhealthy Days', 'Very Unhealthy Days', 'Hazardous Days'];
            const colors = ['#3E4F6B', '#F1C40F', '#E74C3C', '#3498DB', '#9B59B6'];
            const values = [
                data['Good Days'],
                data['Moderate Days'],
                data['Unhealthy Days'],
                data['Very Unhealthy Days'],
                data['Hazardous Days']
            ];

            let total = 0;
            values.forEach(value => total += value);

            let startAngle = 0;
            let endAngle = 0;

            const centerX = pieCanvas.width / 2;
            const centerY = pieCanvas.height / 2;
            const radius = Math.min(centerX, centerY) - 50;

            for (let i = 0; i < values.length; i++) {
                endAngle = startAngle + (Math.PI * 2 * (values[i] / total));
                ctx.fillStyle = colors[i];
                ctx.beginPath();
                ctx.moveTo(centerX, centerY);
                ctx.arc(centerX, centerY, radius, startAngle, endAngle);
                ctx.closePath();
                ctx.fill();
                startAngle = endAngle;

                // Display numbers
                const text = `${labels[i]}: ${values[i]}`;
                const textX = centerX + Math.cos(startAngle - Math.PI / 2 + (endAngle - startAngle) / 2) * radius;
                const textY = centerY + Math.sin(startAngle - Math.PI / 2 + (endAngle - startAngle) / 2) * radius;
                ctx.fillStyle = 'black';
                ctx.font = '14px Arial';
                ctx.fillText(text, textX - 40, textY);
            }

            // Add labels in the center
            ctx.fillStyle = 'black';
            ctx.font = '24px Arial';
            ctx.fillText('Air Pollution', centerX - 100, centerY);
            ctx.font = '18px Arial';
            ctx.fillText(`in ${data.County}`, centerX - 80, centerY + 30);

            // Add legend
            for (let i = 0; i < labels.length; i++) {
                ctx.fillStyle = colors[i];
                ctx.fillRect(centerX + 180, 50 + 30 * i, 20, 15);
                ctx.fillStyle = 'black';
                ctx.font = '16px Arial';
                ctx.fillText(labels[i], centerX + 210, 65 + 30 * i);
            }
        }

        function createBarChart(data) {
            const barCanvas = document.getElementById('countyBarChart');
            const ctx = barCanvas.getContext('2d');
            const labels = [
                'Days with AQI',
                'Unhealthy for Sensitive Groups Days',
                'Max AQI',
                '90th Percentile AQI',
                'Median AQI',
                'Days CO',
                'Days NO2',
                'Days Ozone',
                'Days PM2.5',
                'Days PM10'
            ];

            const values = [
                data['Days with AQI'],
                data['Unhealthy for Sensitive Groups Days'],
                data['Max AQI'],
                data['90th Percentile AQI'],
                data['Median AQI'],
                data['Days CO'],
                data['Days NO2'],
                data['Days Ozone'],
                data['Days PM2.5'],
                data['Days PM10']
            ];

            const maxValue = Math.max(...values);

            const barWidth = 40;
            const spacing = 80;
            const startX = 50;
            const startY = barCanvas.height - 100;
            const centerX = barCanvas.width / 2;

            for (let i = 0; i < labels.length; i++) {
                const x = startX + (i * spacing);
                const barHeight = (values[i] / maxValue) * (barCanvas.height - 150);
                ctx.fillStyle = getRandomColor();
                ctx.fillRect(x, startY - barHeight, barWidth, barHeight);
                ctx.fillStyle = 'black';
                ctx.fillText(values[i], x, startY - barHeight - 20);
                ctx.fillText(labels[i], x, startY + 20);
            }
        }

        function getRandomColor() {
            const letters = '0123456789ABCDEF';
            let color = '#';
            for (let i = 0; i < 6; i++) {
                color += letters[Math.floor(Math.random() * 16)];
            }
            return color;
        }
    </script>
</body>
</html>
