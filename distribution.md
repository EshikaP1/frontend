---
layout: default
title: Distrubution 
---
IMAGE HERE 

# Lung Cancer by State 
Here is an interactive where you type in a state name and you get the number of lung cancer cases it has! 


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
    </div>

 <script>
        // Listen for the form submission
        document.getElementById('stateForm').addEventListener('submit', function (e) {
            e.preventDefault(); // Prevent the default form submission

            // Get the state name from the input field
            const stateName = document.getElementById('stateInput').value;

            // Send the stateName to the backend using a fetch request
            fetch('https://cancer0.stu.nighthawkcodingsociety.com/', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ state_name: stateName }),
            })
            .then(response => response.json())
            .then(data => {
                // Display the result from the backend in the result div
                document.getElementById('result').textContent = `Result from backend: ${data.result}`;
            })
            .catch(error => {
                console.error('Error:', error);
            });
        });
    </script>
</body>

The distribution of lung cancer cases can be grouped my space. Some areas are more disporportionally affected by lung cancer cases than others. Some areas specially, such as low income or areas next to factories, have a sharp increase in lung cancer cases. 

## Distribution Maps 

## San Diego County Lung Cancer Cases 
![Alt text](<images/download (2).jpeg>)

## California Lung Cancer Cases 
![Alt text](<images/Screenshot 2020-07-20 08.57.36.png>)

## United States Lung Cancer Cases
![Alt text](images/mm6936a8-F.gif)

## World Lung Cancer Cases 
![Alt text](images/Ch11_Lung_Rates_M-mobile.png)
