---
layout: default
title: Aerosol data
---

<h1>Enter a County Name</h1>
<form id="countyForm">
    <input type="text" id="countyInput" placeholder="Enter a county name">
    <button type="submit">Submit</button>
</form>

<div id="result">
    <p id="countyData"></p>
</div>

<script>
    document.getElementById('countyForm').addEventListener('submit', function (e) {
        e.preventDefault();
        const countyName = document.getElementById('countyInput').value;
        get(`http://localhost:5000/api/data/county/${countyName}`, {
            method: 'GET',
            headers: {
                'Content-Type': 'application/json',
            }
        })
        .then(response => response.json())
        .then(data => {
            document.getElementById('countyData').textContent = JSON.stringify(data);
        })
        .catch(error => {
            console.error('Error:', error);
        });
    });
</script>
