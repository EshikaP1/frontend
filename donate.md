---
layout: default
title: How you can help
---
![Alt text](images/DONATE.png)

<!-- Introduction and title of the page -->
You can make a positive impact by supporting organizations working to address critical issues related to lung cancer and climate change. Your donations can help fund research, provide support to affected individuals, and drive initiatives to combat these challenges. Below, you'll find links to reputable organizations where you can make contributions:

<!-- Explanation of how readers can contribute to the causes of lung cancer and climate change -->

## <span style="color: #228B22"> Lung Cancer </span>

<!-- Section title related to Lung Cancer -->

### [Lung Cancer Foundation of America](https://lcfamerica.org/donate/)
<!-- Organization 1: Lung Cancer Foundation of America -->
The Lung Cancer Foundation of America (LCFA) is dedicated to funding innovative and promising research in the fight against lung cancer. Your donations support groundbreaking advancements in prevention, early detection, treatment, and ultimately, finding a cure.

### [American Lung Association](https://www.lung.org/get-involved/ways-to-give)
<!-- Organization 2: American Lung Association -->
The American Lung Association works tirelessly to improve lung health and prevent lung disease through education, advocacy, and research. Your donations can contribute to their efforts in reducing the impact of lung cancer and respiratory conditions.

### [Cancer Research Institute](https://www.cancerresearch.org/join-the-cause/donate)
<!-- Organization 3: Cancer Research Institute -->
The Cancer Research Institute (CRI) funds cancer immunotherapy research, including research into lung cancer treatments. Your support helps advance innovative approaches to fighting cancer.

## <span style="color: #228B22"> Climate Change </span>

<!-- Section title related to Climate Change -->

### [Environmental Defense Fund](https://www.edf.org/give)
<!-- Organization 4: Environmental Defense Fund -->
The Environmental Defense Fund (EDF) focuses on finding solutions to combat climate change and protect the environment. Your donations support their work in advocating for policies, clean energy solutions, and sustainable practices.

### [The Nature Conservancy](https://www.nature.org/en-us/what-we-do/our-insights/perspectives/support-our-mission/)
<!-- Organization 5: The Nature Conservancy -->
The Nature Conservancy is dedicated to conserving lands and waters while addressing climate change challenges. Your contributions help protect ecosystems and promote sustainable environmental practices.

### [350.org](https://350.org/donate/)
<!-- Organization 6: 350.org -->
350.org is a grassroots organization that mobilizes for climate action and divestment from fossil fuels. Your donations support their efforts in building a sustainable future.

## <span style="color: #228B22"> Conclusion </span>

<!-- Conclusion section -->
Your contributions can make a real difference in the fight against lung cancer and climate change. These organizations are actively engaged in research, advocacy, and education, and your support can help drive positive change. Thank you for considering a donation to these important causes.

<html>
<head>
    <title>Indoor Air Quality Quiz</title>
</head>
<body>
    <h1>Indoor Air Quality Quiz</h1>

<div>
        <label for="userName">Name:</label>
        <input type="text" id="userName">
    </div>

<form id="quizForm">
        <div>
            <label for="smokeIndoors">1) Do you smoke inside your house?</label>
            <select id="smokeIndoors">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>

 <div>
            <label for="gasStove">2) Do you have a gas stove?</label>
            <select id="gasStove">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>

 <div>
            <label for="useAirFresheners">3) Do you use scented candles or air fresheners?</label>
            <select id="useAirFresheners">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>

  <div>
            <label for="indoorPets">4) Do you have pets that live indoors?</label>
            <select id="indoorPets">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>

 <div>
            <label for="moldMildew">5) Have you noticed any visible mold or mildew growth in your home?</label>
            <select id="moldMildew">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>

<button id="submitBtn" type="button">Submit</button>
    </form>

<script>
        document.getElementById("submitBtn").addEventListener("click", () => {
            const userName = document.getElementById("userName").value;
            const score = 5 - getScore();
            alert(`Hello, ${userName}! Your score is ${score}/5.`);
        });

        function getScore() {
            let score = 0;
            const answers = ["smokeIndoors", "gasStove", "useAirFresheners", "indoorPets", "moldMildew"];
            answers.forEach(answerId => {
                const answer = document.getElementById(answerId).value;
                if (answer === "no") {
                    score += 1;
                }
            });
            return score;
        }
    </script>
</body>
</html>

