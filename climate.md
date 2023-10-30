---
layout: default
title: Climate Change
---
![Alt text](<images/CLIMATE CHANGE.png>)

# <span style="color: #228B22"> What is Climate Change? </span>

<!-- This is the page header with the title "What is Climate Change?" -->

<html>
<head>
  <style>
    button {
      color: #b46060;
      padding: 10px 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="climate-change-container">
    <p id="climate-info">Climate change is a global issue with serious consequences.</p>
    <button id="change-info">Next</button>
  </div>
  <script>
    const infoElement = document.getElementById("climate-info");
    const changeButton = document.getElementById("change-info");

    // JavaScript code for changing climate change information on button click
    changeButton.addEventListener("click", function () {
      if (infoElement.innerHTML === "Climate change is a global issue with serious consequences.") {
        infoElement.innerHTML = "It's not only killing our planet but also the species in it. Around 1 million species are on the brink of extinction due to climate change.";
      } else {
        infoElement.innerHTML = "Climate change is a global issue with serious consequences.";
      }
    });
  </script>
</body>
</html>

<!-- This section is an HTML block with JavaScript code for displaying and updating climate change information. -->

Climate change is one of the most pressing global issues of our time. It refers to significant and lasting changes in the Earth's climate patterns, primarily driven by human activities. This informational page aims to provide a comprehensive overview of climate change, including its causes, effects, consequences, and what we can do to address it.

<!-- Introduction to climate change -->

## <span style="color: #228B22"> Table of Contents
- [What is Climate Change?](#what-is-climate-change)
- [Causes of Climate Change](#causes-of-climate-change)
- [Effects of Climate Change](#effects-of-climate-change)
- [Consequences of Climate Change](#consequences-of-climate-change)
- [Mitigation and Adaptation](#mitigation-and-adaptation)
- [International Agreements](#international-agreements)
- [Taking Action](#taking-action)
- [Climate Change Resources](#climate-change-resources)

<!-- Table of contents with links to various sections -->

![Alt text](<images/download (1).jpeg>)

<!-- Image related to climate change -->

## <span style="color: #228B22"> Causes of Climate Change </span>
Human activities, particularly the burning of fossil fuels like coal, oil, and natural gas, as well as deforestation and industrial processes, have significantly increased the concentration of greenhouse gases in the atmosphere. These gases, including carbon dioxide (CO2), methane (CH4), and nitrous oxide (N2O), trap heat and lead to a warming effect.

<!-- Information about the causes of climate change -->

## <span style="color: #228B22"> Effects of Climate Change </span>
The effects of climate change are widespread and include rising global temperatures, more frequent and severe weather events (e.g., hurricanes, droughts, and wildfires), melting ice caps and glaciers, and disruptions in ecosystems and biodiversity.

<!-- Information about the effects of climate change -->

## <span style="color: #228B22"> Consequences of Climate Change </span>
Climate change has far-reaching consequences, affecting agriculture, water resources, health, and food security. It also poses challenges for vulnerable communities, as sea levels rise and weather patterns become less predictable.

<!-- Information about the consequences of climate change -->

## <span style="color: #228B22"> Mitigation and Adaptation </span>
Mitigation efforts focus on reducing greenhouse gas emissions by transitioning to clean energy sources, improving energy efficiency, and sustainable land use. Adaptation strategies involve preparing for the impacts of climate change by building resilient infrastructure and systems.

<!-- Information about mitigation and adaptation strategies -->

## <span style="color: #228B22"> International Agreements </span>
International agreements like the Paris Agreement aim to unite countries in a common effort to combat climate change. These agreements set targets for reducing greenhouse gas emissions and promote global cooperation.

<!-- Information about international agreements related to climate change -->

## <span style="color: #228B22"> Taking Action </span>
Individuals can take action by reducing energy consumption, adopting sustainable practices, supporting clean energy initiatives, and advocating for policies that address climate change. Community engagement and education are also crucial.

<!-- Information about individual and community actions to address climate change -->

## <span style="color: #228B22"> Climate Change Resources </span>
For further information and resources on climate change, consider exploring the following sources:

- [Intergovernmental Panel on Climate Change (IPCC)](https://www.ipcc.ch/)
- [National Aeronautics and Space Administration (NASA) - Climate](https://climate.nasa.gov/)
- [United Nations Framework Convention on Climate Change (UNFCCC)](https://unfccc.int/)
- [The Climate Reality Project](https://www.climaterealityproject.org/)

<!-- List of resources and links related to climate change -->

Climate change is a complex and urgent global challenge that requires collective action. Understanding its causes, effects, and the steps we can take to address it is crucial for the well-being of current and future generations. By working together, we can mitigate the impacts of climate change and create a more sustainable and resilient world.

<html>
<head>
    <title>How Climate Change friendly are you?</title>
    <style>
        body {
            text-align: center;
        }
        #game-container {
            margin: 0 auto;
            width: 400px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            margin: 5px;
        }
        #info-box {
            display: none;
        }
    </style>
</head>
<body>
    <h1>How Climate Change friendly are you?</h1>
    <div id="game-container">
        <h2>Choose Your Scenario</h2>
        <p>Select a scenario and take actions to combat climate change.</p>
        <button id="scenario-1-button" onclick="startScenario(1)">Scenario 1: Energy Efficiency</button>
        <button id="scenario-2-button" onclick="startScenario(2)">Scenario 2: Sustainable Transportation</button>
        <button id="scenario-3-button" onclick="startScenario(3)">Scenario 3: Renewable Energy</button>
        <button id="scenario-4-button" onclick="startScenario(4)">Scenario 4: Green Diet</button>
        <button id="scenario-5-button" onclick="startScenario(5)">Scenario 5: Reforestation</button>
    </div>
    <div id="info-box">
        <p id="info-text"></p>
        <button id="continue-button" onclick="resetGame()">Continue</button>
    </div>

<script>
        let environmentalScore = 50;
        let currentScenario = 0;

        const scenarios = [
            null,
            {
                name: "Energy Efficiency",
                actions: [
                    { name: "Upgrade home insulation", impact: 10 },
                    { name: "Switch to LED lights", impact: 5 },
                    { name: "Use programmable thermostat", impact: 5 }
                ]
            },
            {
                name: "Sustainable Transportation",
                actions: [
                    { name: "Ride a bicycle", impact: 10 },
                    { name: "Use public transport", impact: 5 },
                    { name: "Carpool with others", impact: 5 }
                ]
            },
            {
                name: "Renewable Energy",
                actions: [
                    { name: "Install solar panels", impact: 10 },
                    { name: "Support wind energy projects", impact: 5 },
                    { name: "Switch to a green energy provider", impact: 5 }
                ]
            },
            {
                name: "Green Diet",
                actions: [
                    { name: "Reduce meat consumption", impact: 10 },
                    { name: "Eat more plant-based foods", impact: 5 },
                    { name: "Reduce food waste", impact: 5 }
                ]
            },
            {
                name: "Reforestation",
                actions: [
                    { name: "Plant trees in your community", impact: 10 },
                    { name: "Support reforestation organizations", impact: 5 },
                    { name: "Participate in tree-planting events", impact: 5 }
                ]
            }
        ];

        function startScenario(scenarioNumber) {
            currentScenario = scenarioNumber;
            displayInfo(`You've chosen ${scenarios[scenarioNumber].name} scenario.`);
            document.getElementById("game-container").style.display = "none";
            showScenarioActions(scenarios[scenarioNumber].actions);
        }

        function showScenarioActions(actions) {
            const actionButtons = actions.map(action => {
                return `<button onclick="takeAction('${action.name}', ${action.impact})">${action.name}</button>`;
            });

            const actionButtonsHTML = actionButtons.join('<br>');
            document.getElementById("info-text").innerHTML = `Select an action to combat climate change:<br>${actionButtonsHTML}`;
        }

        function takeAction(action, impact) {
            environmentalScore += impact;
            displayInfo(`You took the action: "${action}" and your environmental score is now ${environmentalScore}.`);
        }

        function displayInfo(text) {
            document.getElementById("info-box").style.display = "block";
            document.getElementById("info-text").innerText = text;
        }

        function resetGame() {
            currentScenario = 0;
            environmentalScore = 50;
            document.getElementById("game-container").style.display = "block";
            document.getElementById("info-box").style.display = "none";
        }
    </script>
</body>
</html>