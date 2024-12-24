# Automating Persona Generation: Leveraging Large Language Models in Educational Digital Services
**Authors:**  Thanatat Wongabut / Unhawa Ninrutsirikun / Chonlameth Arpnikanondt

School of Information Technology, King Mongkut's University of Technology Thonburi

## Abstract
This study provides a preliminary exploration on automating user persona generation via Large Language Models (LLMs) with a case study on educational digital services. Data were collected from 40 undergraduate students at one of Thailand’s science and technology higher education institutes through questionnaires and semi-structured interviews, with participants grouped via K-means clustering for diverse representation. The study relied on LLMs to analyze the data to generate empathy maps and jobs-to-be-done to assist in guiding the persona generation. Validation ensued by checking whether persona contents were aligned with leading features determined by SHAP (SHapley Additive exPlanations). The results demonstrated that each persona was reliably tied to the feature importances as identified by SHAP—effectively, highlighting how each generated persona successfully captured the unique traits of the cluster it represented. Such promising results have paved way for further optimization for better precision and accuracy, with the opportunity to generalize the approach undertaken in this study into an LLM-based framework for automating persona generation.

## Requirements
1. Questionnaires attributes (.txt)
2. Questionnaire responses for each cluster (.csv)
3. Interview scripts for each cluster (.csv)
4. Image captioning (.csv)

## Persona Generation in ChatGPT-4

**Step 1:** Let ChatGPT-4 understand the question attributes in <questionnaire_attributes.txt>, with the following prompt. 

```
I want you to act as a UX researcher. I will provide the spreadsheet file about the questionnaire responses. Each row contains user information which has attributes in the given text file.

Just keep the following in mind for now, there is more data to follow. Say only 'Continue'.
```
