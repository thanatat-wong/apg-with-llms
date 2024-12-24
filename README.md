# Automating Persona Generation: Leveraging Large Language Models in Educational Digital Services
**Authors:**  Thanatat Wongabut / Unhawa Ninrutsirikun / Chonlameth Arpnikanondt

School of Information Technology, King Mongkut's University of Technology Thonburi

## Table of Contents
There are six sections:
1. [Abstract](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#abstract)
2. [Automatic Persona Generation Development Process](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#file-requirements)
3. [Automatic Persona Generation Experiments](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#file-requirements)
4. [File Requirements](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#file-requirements)
5. [Persona Generation Prompts for ChatGPT-4](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#file-requirements)
6. [Persona Generation Output](https://github.com/thanatat-wong/apg-with-llms/blob/main/README.md#file-requirements)

## Abstract
This study provides a preliminary exploration on automating user persona generation via Large Language Models (LLMs) with a case study on educational digital services. Data were collected from 40 undergraduate students at one of Thailand’s science and technology higher education institutes through questionnaires and semi-structured interviews, with participants grouped via K-means clustering for diverse representation. The study relied on LLMs to analyze the data to generate empathy maps and jobs-to-be-done to assist in guiding the persona generation. Validation ensued by checking whether persona contents were aligned with leading features determined by SHAP (SHapley Additive exPlanations). The results demonstrated that each persona was reliably tied to the feature importances as identified by SHAP—effectively, highlighting how each generated persona successfully captured the unique traits of the cluster it represented. Such promising results have paved way for further optimization for better precision and accuracy, with the opportunity to generalize the approach undertaken in this study into an LLM-based framework for automating persona generation.

## Automatic Persona Generation Development Process

![Alt text](https://github.com/thanatat-wong/apg-with-llms/blob/main/apg-development-process.jpg?raw=true)

## Automatic Persona Generation Experiments

![Alt text](https://github.com/thanatat-wong/apg-with-llms/blob/main/apg-experiment.png?raw=true)

## File Requirements
1. Questionnaires attributes (.txt)
2. Questionnaire responses for each cluster (.csv)
3. Interview scripts for each cluster (.csv)
4. Image captioning (.csv) from https://www.kaggle.com/datasets/ahmadahmadzada/images2000/data

## Persona Generation Prompts for ChatGPT-4

**Step 1:** Let ChatGPT-4 understand the question attributes in <questionnaire_attributes.txt>, with the following prompt. 

```
I want you to act as a UX researcher. I will provide the spreadsheet file about the questionnaire responses. Each row contains user information which has attributes in the given text file.

Just keep the following in mind for now, there is more data to follow. Say only 'Continue'.
```

**Step 2:** Let chatGPT-4 analyze responses from questionnaire in <questionnaire_responses.csv>.
```
From the given file is the questionnaire response. Next, I will provide the CSV file about the interview script the experience of digital service for education which is from the one of respondent who answered the given questionnaire. 

Just keep the following in mind for now, there is more data to follow. Say only 'Continue'.
```

**Step 3:** Attach <interview_scripts.csv> file, and create an empathy map.
```
You also have knowledge about empathy map. Based on the interview script and questionnaire responses, your job will be coming up with building up one empathy map for the representative of this cluster. The areas that you need to provide are:
- age 
- faculty 
- hearing: refers to what are they hearing others say, what are they hearing from friends, what are they hearing from colleagues or what are they hearing second-hand. 
- thinking and feeling: refers to what other thoughts and feelings might motivate their behavior. 
- seeing: refers to what do they see others saying and doing or what do they see in their immediate environment. 
- speaking and doing: refers to what have we heard them say, what can we imagine them saying, what do they do, what behavior have we observed or what can we imagine them doing. 
- frustration: refers to what are their fears, pains, and anxieties.
- desire: refers to what are their wants, needs, hopes and dreams.

Please answer in .txt file.
```

**Step 4:** Create Jobs-To-Be-Done (JTBD) statements from the generated empathy map.
```
Previously, you got the empathy map from the prior result. The next step is construct jobs-to-be-done statement(s). You have to start with the following template below:

Step 1: I want to [desire/motivation]
Step 2: when [situation/context]
Step 3: so that I can [expected outcome/result]
Step 4: without [pain point/constraint]

Note that for step 4, if there is no any pain point or constraint, no need to add in this step.

Please answer in .txt file.
```
**Step 5:** Give the command to ChatGPT-4 to understand the image captions file in the next step.
```
Next, I will provide the spreadsheet file about the image caption. Your job will be coming up with keeping the following file for creating the persona in the next step.

Just keep the following in mind for now, there is more task to follow. Say only 'Continue'.
```

**Step 6:** Attach <image_captioning.csv> file, and let ChatGPT-4 choose appropriate image from the attached file. Then, generate the persona by composing Identity, General Profile, Goals, Scenarios, Knowledge and Experience, Relationships, Psychological Profile and Needs, Attitude and Motivation, Expectations, and Special Needs.
```
From the given file is the image caption. Next, your job will be coming up with utilizing the empathy map, jobs-to-be-done statements and culture profile to create the persona based on the following persona components below:
- Identity
	- First Name / Last Name = generate the name for this persona
	- Picture = select the best representative picture from the image caption spreadsheet and give me the id and caption
	- Short statement describing the overall life goal and should be less than 50 words
	- Personal Profile (Paragraph - Overall Story) and should be between 150-300 words
- General Profile
	- Age
	- Faculty
	- Major
	- Gender
- Goals
	- One statement for describing "Personal Goals" and should be less than 50 words
	- One statement for describing "Application Goals" and should be less than 50 words
	- One statement for describing "Professional Goals" and should be less than 50 words
- Scenarios = refers to three to five use case statements related the individual user (i.e., the persona), the task or situation, the user's desired outcome, goal for that task, procedure and task flow information, a time interval, envisioned features, functionality the user will need or use by depending on the most or the least interactions in digital service for education, excluding the types which respondent has no experience to, and each statement must tell clearly who, what, where, when, why and how.
- Knowledge and Experience
	- Digital Tools = refers to technologies or tools that the respondent use to access digital services for education (e.g., computer, smartphone, etc.).
	- Relevant Skills [Digital Skill] = refers to any digital skills that the respondent possess.
- Relationships
	- Social Circles = refers to who the respondent primarily interact with when using the digital service for education.
	- Influence = refers to respondent opinions of your friends, professors or colleagues influence your use of digital services for education.
- Psychological Profile and Needs
	- Learning Styles = refers to what methods the respondent prefers to learn new information or skills.
	- Decision Making = refers to things that influence to respondent's decision on using digital services for education. 
- Attitude and Motivation
	- Technology Attitude = refers to what the respondent's general attitude towards new technologies. 
	- Motivation to Use = refers to what motivities the respondent uses the digital service for education.
- Expectations
	- What the respondent is favorite feature of digital service for education.
- Special Needs
	- Accessibility Requirements = refers to what needs or requirements from respondent's perspective to digital services for education.

Please create and answer in .txt file.
```
## Persona Generation Output
According to the results from the ChatGPT-4, the following image is the final persona output by rearranging the layout automatically in Python:
![Alt text](https://github.com/thanatat-wong/apg-with-llms/blob/main/generated-persona.png?raw=true)
