---
layout: default
title: Lung Cancer
# course: compsci
---
![Alt text](<images/LUNG CANCER (4).png>)

## <span style="color: #228B22">Introduction:</span>
Lung cancer is a serious and often life-threatening medical condition that affects the lungs. It is the leading cause of cancer-related deaths worldwide. This informational page aims to provide an overview of lung cancer, including its causes, types, symptoms, diagnosis, treatment options, and prevention strategies.

## <span style="color: #228B22">Table of Contents</span>
- [What is Lung Cancer?](#what-is-lung-cancer)
- [Types of Lung Cancer](#types-of-lung-cancer)
- [Causes and Risk Factors](#causes-and-risk-factors)
- [Signs and Symptoms](#signs-and-symptoms)
- [Diagnosis and Staging](#diagnosis-and-staging)
- [Treatment Options](#treatment-options)
- [Living with Lung Cancer](#living-with-lung-cancer)
- [Prevention and Early Detection](#prevention-and-early-detection)
- [Support and Resources](#support-and-resources)
- [Conclusion](#conclusion)

## <span style="color: #228B22"> What is Lung Cancer? </span>
Lung cancer occurs when abnormal cells in the lung grow uncontrollably, forming a tumor. These tumors can interfere with lung function, making it difficult for the affected person to breathe. Lung cancer can be broadly categorized into two main types: non-small cell lung cancer (NSCLC) and small cell lung cancer (SCLC).

## <span style="color: #228B22"> Types of Lung Cancer </span>
- Non-Small Cell Lung Cancer (NSCLC): NSCLC is the most common type, accounting for around 85% of all lung cancer cases. It includes three subtypes: adenocarcinoma, squamous cell carcinoma, and large cell carcinoma.
- Small Cell Lung Cancer (SCLC): SCLC is less common but tends to grow and spread more quickly than NSCLC.

![Alt text](images/non-small-cell-lung-cancer-2249281_final-ea85b1b20eb748fb806d5ed11284dfd8.png)

## <span style="color: #228B22"> Causes and Risk Factors </span>
The primary cause of lung cancer is exposure to carcinogens, with tobacco smoke being the leading risk factor. Other risk factors include secondhand smoke, exposure to radon gas, workplace exposures (asbestos, arsenic, and more), and a family history of lung cancer.

## <span style="color: #228B22"> Signs and Symptoms </span>
Common symptoms of lung cancer may include a persistent cough, chest pain, shortness of breath, unexplained weight loss, coughing up blood, and recurrent infections. However, some cases may be asymptomatic in the early stages.

## <span style="color: #228B22"> Diagnosis and Staging </span>
Diagnosing lung cancer involves a combination of imaging tests, biopsies, and staging to determine the extent of the disease. Staging helps in planning appropriate treatment strategies.

## <span style="color: #228B22"> Treatment Options </span>
Treatment options for lung cancer depend on the type, stage, and overall health of the patient. They may include surgery, radiation therapy, chemotherapy, targeted therapy, immunotherapy, and palliative care to manage symptoms and improve quality of life.

![Alt text](<images/Types of lung cancer.png>)

## <span style="color: #228B22"> Living with Lung Cancer </span>
Living with lung cancer can be challenging, but it is possible to maintain a good quality of life with the right support, including emotional, psychological, and medical assistance.

## <span style="color: #228B22"> Prevention and Early Detection </span>
Preventing lung cancer primarily involves avoiding exposure to carcinogens, particularly by quitting smoking and avoiding secondhand smoke. Early detection through regular screenings, especially for high-risk individuals, can improve the chances of successful treatment.

## <span style="color: #228B22"> Support and Resources </span>
Numerous organizations and support groups offer assistance to individuals and families affected by lung cancer. These resources provide information, emotional support, and guidance throughout the cancer journey.

## <span style="color: #228B22"> Conclusion </span>
Lung cancer is a serious and potentially life-threatening condition that requires prompt diagnosis and treatment. Understanding the risk factors, signs, and available treatment options can improve outcomes and the quality of life for those affected by this disease. Remember, early detection and prevention are crucial in the fight against lung cancer.

![Alt text](images/4-stages-of-lung-cancer-Saint-Johns-Cancer-Institute.png)

## <span style="color: #228B22"> More information </span>
Here are other links to learn more about lung cancer! 
- [CDC](https://www.cdc.gov/cancer/lung/basic_info/what-is-lung-cancer.htm)
- [Cancer Society](https://www.cancer.org/cancer/types/lung-cancer/about/what-is.html)
- [Mayo Clinic](https://www.mayoclinic.org/diseases-conditions/lung-cancer/symptoms-causes/syc-20374620)
- [Cleveland Clinic](https://my.clevelandclinic.org/health/diseases/4375-lung-cancer)

<!DOCTYPE html>
<html>
<head>
    <title>Lung Cancer Quiz</title>
</head>
<body>
    <h1>Lung Cancer Quiz</h1>

    <div id="questions">
        <!-- Question 1 -->
        <div class="question">
            <p>Which is the most common type of lung cancer?</p>
            <div class="options">
                <input type="radio" name="q1" id="q1-option1" data-correct="true"> <label for="q1-option1">Non-Small Cell Lung Cancer (NSCLC)</label><br>
                <input type="radio" name="q1" id="q1-option2"> <label for="q1-option2">Small Cell Lung Cancer (SCLC)</label><br>
            </div>
            <div class="result"></div>
        </div>

        <!-- Question 2 -->
        <div class="question">
            <p>What is the primary cause of lung cancer?</p>
            <div class="options">
                <input type="radio" name="q2" id="q2-option1" data-correct="true"> <label for="q2-option1">Exposure to carcinogens</label><br>
                <input type="radio" name="q2" id="q2-option2"> <label for="q2-option2">Genetic factors</label><br>
                <input type="radio" name="q2" id="q2-option3"> <label for="q2-option3">Diet</label><br>
            </div>
            <div class="result"></div>
        </div>

        <!-- Question 3 -->
        <div class="question">
            <p>What are common symptoms of lung cancer?</p>
            <div class="options">
                <input type="radio" name="q3" id="q3-option1"> <label for="q3-option1">Fever</label><br>
                <input type="radio" name="q3" id="q3-option2" data-correct="true"> <label for="q3-option2">Coughing up blood</label><br>
                <input type="radio" name="q3" id="q3-option3"> <label for="q3-option3">Unexplained weight loss</label><br>
                <input type="radio" name="q3" id="q3-option4"> <label for="q3-option4">Shortness of breath</label><br>
            </div>
            <div class="result"></div>
        </div>
    </div>

    <script>
        const radioButtons = document.querySelectorAll('input[type="radio"]');
        radioButtons.forEach(radio => {
            radio.addEventListener('change', () => {
                checkAnswer(radio);
            });
        });

        function checkAnswer(radio) {
            const questionDiv = radio.closest('.question');
            const correctRadio = questionDiv.querySelector('input[data-correct="true"]');
            const resultElement = questionDiv.querySelector('.result');

            if (radio.isEqualNode(correctRadio)) {
                resultElement.textContent = "Correct answer: " + correctRadio.nextElementSibling.textContent;
            } else {
                resultElement.textContent = "Incorrect. Correct answer: " + correctRadio.nextElementSibling.textContent;
            }
        }
    </script>
</body>
</html>

