# AI Learning Roadmap Generator

## Overview

AI Learning Roadmap Generator is a Python-based Data Science project that creates a personalized learning roadmap based on a user's current skills, target career role, and available study time.

The application identifies the user's existing skills, finds the skill gap for the selected role, provides an AI-based learning recommendation, estimates study duration, and generates a step-by-step learning roadmap.

The project also uses basic Natural Language Processing (NLP) to suggest a suitable career role when the user does not know their target role.

---

## Problem Statement

Beginners often face difficulty in understanding:

* Which skills are required for a specific career role
* Which skills they are currently missing
* What topics they should learn
* How much time they may need to study

This project helps users identify their skill gaps and generates a structured learning roadmap.

---

## Objectives

The main objectives of this project are:

1. Collect the user's current skills.
2. Allow users to select their target career role.
3. Suggest a career role using NLP when the target role is unknown.
4. Identify missing skills.
5. Generate an AI-based learning recommendation.
6. Estimate learning duration based on study hours.
7. Create a personalized learning roadmap.
8. Export the generated roadmap to a CSV file.

---

## Technologies Used

### Programming Language

* Python

### Python Libraries

* NumPy
* Pandas
* Scikit-learn

### NLP Techniques

* Text Cleaning
* Regular Expressions
* Tokenization
* Skill Extraction
* Skill Synonyms
* TF-IDF
* Cosine Similarity

### Machine Learning / Neural Network

* Multi-Layer Perceptron (MLP)
* ReLU Activation Function
* Basic Feature Engineering
* Classification
* Prediction Probability

---

## Supported Career Roles

The application supports the following roles:

1. Data Analyst
2. Data Scientist
3. ML Engineer
4. NLP Engineer

Each role has a predefined set of required skills.

---

## Skills Covered

The roadmap contains learning areas such as:

### Python

* Basics
* Variables
* Conditions
* Functions
* Lists and Dictionaries
* OOP Basics

### NumPy

* Arrays
* Indexing
* Array Operations
* Mathematical Functions

### Pandas

* DataFrames
* Data Cleaning
* Filtering
* GroupBy
* Merge

### SQL

* SELECT
* WHERE
* GROUP BY
* JOINS
* Subqueries

### Statistics

* Mean and Median
* Probability
* Standard Deviation
* Hypothesis Testing
* Correlation

### AI Basics

* What is AI?
* AI vs ML vs Deep Learning
* Types of AI
* AI Applications
* AI Ethics Basics

### Machine Learning

* Supervised Learning
* Unsupervised Learning
* Regression
* Classification
* Train-Test Split
* Model Evaluation

### Deep Learning Basics

* Neurons and Neural Networks
* Weights and Bias
* Activation Functions
* ReLU
* Forward Propagation
* Loss and Gradient Descent
* Overfitting

### NLP Basics

* Text Cleaning
* Tokenization
* Stopwords
* Stemming and Lemmatization
* Bag of Words
* TF-IDF
* Text Classification

## Note: The Deep Learning and NLP topics listed above are mainly used as learning-roadmap content. The actual implemented NLP functionality uses basic text processing, skill extraction, TF-IDF, and cosine similarity, while the implemented neural-network component uses an MLP classifier.

## How the Project Works

```text
User Input
    |
    v
Current Skills
    |
    v
Skill Extraction
    |
    +-----------------------------+
    |                             |
    v                             v
Target Role Known?          Target Role Unknown
    |                             |
    v                             v
Select Target Role           Enter Career Goal
                                    |
                                    v
                            TF-IDF + Cosine Similarity
                                    |
                                    v
                             Suggested Career Role
    |
    v
Skill Gap Analysis
    |
    v
MLP AI Recommendation
    |
    v
Duration Calculation
    |
    v
Personalized Roadmap
    |
    v
CSV Export
```

---

## NLP Component

The project uses basic NLP techniques to process user input.

### Text Cleaning

The system converts text to lowercase and removes unnecessary characters using regular expressions.

Example:

```text
"I want to become a Data Scientist!"
                    ↓
"i want to become a data scientist"
```

### Tokenization

The cleaned text is split into individual words.

### Skill Extraction

The system detects predefined skills from the user's input.

For example:

```text
python → Python
py → Python

sql → SQL
mysql → SQL
postgresql → SQL

ml → Machine Learning
machine learning → Machine Learning

dl → Deep Learning Basics
deep learning → Deep Learning Basics
```

These mappings are defined using a skill-synonym dictionary.

### TF-IDF

TF-IDF converts the career goal and role descriptions into numerical vectors.

### Cosine Similarity

Cosine similarity compares the user's career goal with predefined role descriptions and selects the most similar role.

---

## Skill Gap Analysis

The application compares the user's detected skills with the skills required for the selected target role.

Example:

```text
Current Skills:
Python, Pandas

Target Role:
Data Scientist
```

The system identifies the missing skills:

```text
NumPy
SQL
Statistics
AI Basics
Machine Learning
Deep Learning Basics
```

The required skills for each role are predefined in the application.

---

## AI Recommendation Component

The project uses an MLPClassifier to provide a learning recommendation.

The model uses binary features representing whether the user has:

* Python
* SQL
* Statistics
* Machine Learning
* Deep Learning

The model produces recommendations such as:

```text
Focus on Core Fundamentals
```

or

```text
Continue with Advanced Learning
```

The model uses a small manually created sample dataset for demonstration purposes.

The neural network configuration includes:

* One hidden layer
* 5 hidden neurons
* ReLU activation
* LBFGS solver

The displayed recommendation probability is obtained using `predict_proba()`.

> Note: This probability is not the overall model accuracy. The MLP component is a small demonstration model and is not intended to represent a production-ready prediction system.

---

## Personalized Roadmap

After identifying the skill gap, the application generates a personalized roadmap.

For every missing skill, the system displays:

* Step number
* Skill
* Estimated study duration
* Topics to learn

Example:

```text
Step 1: NumPy

Estimated Study Duration: 0.5 week(s)

Topics:
- Arrays
- Indexing
- Array Operations
- Mathematical Functions
```

---

## Duration Calculation

The estimated duration depends on:

* Required skills
* Base duration assigned to each skill
* Number of study hours per day

The project uses a heuristic formula to estimate the overall learning duration.

The duration is an estimate and may vary from person to person.

---

## CSV Export

After generating the roadmap, the application saves the result as:

```text
my_ai_learning_roadmap.csv
```

The CSV contains:

* Step
* Skill
* Topic
* Duration_Weeks

---

## Example

### Input

```text
Enter your name: Durga

Enter your current skills:
Python, Pandas

Do you know your target role?
1. Yes
2. No

Select an option:
1

Select your target role:
2

How many hours can you study per day?
4
```

### Output

```text
Target Role: Data Scientist

Detected Skills:
Python, Pandas

Skill Gap:
NumPy
SQL
Statistics
AI Basics
Machine Learning
Deep Learning Basics

Recommendation:
Focus on Core Fundamentals

Estimated Duration:
6 week(s)
```

---

## Project Structure

```text
AI-Learning-Roadmap-Generator/
│
├── app.py
├── requirements.txt
├── README.md
└── my_ai_learning_roadmap.csv
```

`my_ai_learning_roadmap.csv` is generated automatically when the application runs successfully.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/AI-Learning-Roadmap-Generator.git
```

### 2. Open the Project Folder

```bash
cd AI-Learning-Roadmap-Generator
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Application

```bash
python app.py
```

---

## Main Functions

The project contains the following important functions:

```text
clean_text()
tokenize()
extract_skills()
suggest_role()
find_skill_gap()
calculate_duration()
get_recommendation()
generate_roadmap()
```

---

## Limitations

* Role descriptions are predefined.
* Skill extraction uses predefined keywords and synonyms.
* The MLP model uses a small manually created sample dataset.
* Learning duration is an estimated heuristic.
* The NLP implementation is basic.
* The project does not use LLMs, Generative AI, RAG, Transformers, or external APIs.

---

## Future Enhancements

Future versions can include:

* More career roles
* More skills and learning topics
* Larger real-world training datasets
* Course and resource recommendations
* Streamlit web interface
* Advanced NLP models
* Integration with online learning platforms
* Improved recommendation models

---

## Conclusion

The AI Learning Roadmap Generator demonstrates how Python, data processing, basic NLP, machine learning, and a basic neural-network model can be combined to create a personalized learning recommendation system.

The application helps users understand their current skill level, identify missing skills for a target role, and follow a structured learning roadmap.

---

## Author

**Yarramsetti Lakshmi Prasanna**

B.Sc. Computer Science | Data Science Fresher

GitHub: https://github.com/prasannayarramsetti816
