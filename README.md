# AI Learning Roadmap Generator

## Project Overview

The AI Learning Roadmap Generator is a Python-based Data Science project that creates a personalized learning roadmap based on a user's current skills, target career role, and available study time.

The application identifies the user's existing skills, analyzes the skill gap for the selected career role, provides an AI-based learning recommendation, estimates the learning duration, and generates a step-by-step roadmap.

When the user does not know their target role, the project uses basic Natural Language Processing (NLP) techniques such as TF-IDF and Cosine Similarity to suggest a suitable career role.

---

## Problem Statement

Beginners often have difficulty deciding:

* Which skills are required for a specific career role
* Which skills they are currently missing
* What topics they should learn
* How much time they should spend learning each skill

This project provides a simple personalized learning path based on the user's current skills and career goal.

---

## Objectives

The main objectives of this project are:

1. Collect the user's current skills.
2. Allow the user to select a target career role.
3. Suggest a career role when the target role is unknown.
4. Identify the skill gap.
5. Generate an AI-based learning recommendation.
6. Estimate learning duration based on study hours.
7. Generate a personalized learning roadmap.
8. Export the roadmap to a CSV file.

---

## Technologies Used

### Programming Language

* Python

### Libraries

* NumPy
* Pandas
* Scikit-learn

### NLP Techniques

* Text Cleaning
* Regular Expressions
* Tokenization
* Keyword-based Skill Extraction
* Skill Synonyms
* TF-IDF
* Cosine Similarity

### Machine Learning / Neural Network

* Multi-Layer Perceptron (MLP)
* Binary Feature Representation
* Classification
* Prediction Probability
* ReLU Activation Function

The project uses `MLPClassifier` with one hidden layer containing five neurons.

---

## Supported Career Roles

The application supports four career roles:

1. Data Analyst
2. Data Scientist
3. ML Engineer
4. NLP Engineer

Each role has a predefined set of required skills.

---

## Skills in the Learning Roadmap

The project contains the following learning areas.

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

The Deep Learning and NLP sections above are primarily learning-roadmap content. The actual implemented NLP component uses text cleaning, tokenization, skill extraction, TF-IDF, and Cosine Similarity. The actual neural-network component uses an MLP classifier.

---

## Project Workflow

```text
User Input
    |
    v
Current Skills
    |
    v
Skill Extraction
    |
    +------------------------------+
    |                              |
    v                              v
Target Role Known?           Target Role Unknown
    |                              |
    v                              v
Select Target Role             Career Goal
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
MLP Recommendation
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

## How the Project Works

### Step 1: User Input

The application asks the user for:

* Name
* Current skills
* Whether the target role is known
* Target career role or career goal
* Study hours per day

The application accepts `1/2` as well as `Yes/No` for the target-role question.

---

### Step 2: Skill Extraction

The system processes the user's current skills and maps different skill names or synonyms to standard skill names.

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

nlp → NLP Basics
```

This mapping is implemented using a predefined skill-synonym dictionary.

---

### Step 3: NLP Role Suggestion

When the user does not know their target role, the project analyzes the career goal.

The process is:

```text
Career Goal
     |
     v
Text Cleaning
     |
     v
TF-IDF
     |
     v
Cosine Similarity
     |
     v
Suggested Role
```

The project first checks for an exact role match. Otherwise, it compares the user's career goal with predefined role descriptions using TF-IDF and Cosine Similarity.

---

## Step 4: Skill Gap Analysis

The application compares the user's detected skills with the required skills for the selected target role.

For example:

```text
Current Skills:
Python, Pandas

Target Role:
Data Scientist
```

The application identifies missing skills such as:

```text
NumPy
SQL
Statistics
AI Basics
Machine Learning
Deep Learning Basics
```

The required skills for each role are predefined in the project.

---

## Step 5: AI Recommendation

The project uses a Multi-Layer Perceptron classifier to generate a learning recommendation.

The model uses five binary skill features:

```text
Python
SQL
Statistics
Machine Learning
Deep Learning
```

Each feature is represented as:

```text
1 = Skill Present
0 = Skill Missing
```

The model produces one of two recommendations:

```text
Focus on Core Fundamentals
```

or

```text
Continue with Advanced Learning
```

The model is trained using a small manually created sample dataset.

### Important Note

The displayed `Recommendation Probability` comes from the model's `predict_proba()` output.

It should not be interpreted as the overall model accuracy or as production-level confidence because the model is trained on a small demonstration dataset.

---

## Step 6: Personalized Learning Roadmap

After identifying the skill gap, the application generates a personalized roadmap.

For every missing skill, it displays:

* Step number
* Skill name
* Estimated study duration
* Important topics

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

## Step 7: Duration Estimation

The project estimates the learning duration using:

* Base duration assigned to each skill
* User's study hours per day

The project uses a heuristic formula for estimation.

```text
Estimated Duration =
(Base Skill Duration × 2) / Study Hours Per Day
```

The result is rounded up for the overall roadmap duration and used as an approximate learning plan.

The estimated duration is only a planning approximation and may vary from person to person.

---

## Step 8: CSV Export

After generating the roadmap, the application saves it as:

```text
my_ai_learning_roadmap.csv
```

The generated CSV contains:

* Step
* Skill
* Topic
* Duration_Weeks

---

## Example

### Sample Input

```text
Enter your name: Durga

Enter your current skills:
Python, Pandas

Do you know your target role?
1. Yes
2. No

Select an option:
1

Available Roles:
1. Data Analyst
2. Data Scientist
3. ML Engineer
4. NLP Engineer

Select your target role:
2

How many hours can you study per day?
4
```

### Sample Output

```text
Target Role: Data Scientist

Detected Skills:
Python, Pandas

SKILL GAP:
NumPy
SQL
Statistics
AI Basics
Machine Learning
Deep Learning Basics

AI RECOMMENDATION:
Focus on Core Fundamentals

Estimated Duration:
6 week(s)
```

The application then displays the complete roadmap for each missing skill.

---

## Main Functions

The notebook contains the following important functions:

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

These functions handle text processing, skill extraction, role suggestion, skill-gap analysis, AI recommendation, duration estimation, and roadmap generation.

---

## Project Structure

```text
AI-Learning-Roadmap-Generator/
│
├── AI_Learning_Roadmap_Generator_Prj.ipynb
├── README.md
└── requirements.txt
```

The file `my_ai_learning_roadmap.csv` is generated automatically when the notebook is executed.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/prasannayarramsetti816/AI-Learning-Roadmap-Generator.git
```

### 2. Open the Project Folder

```bash
cd AI-Learning-Roadmap-Generator
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Open the Jupyter Notebook

Open:

```text
AI_Learning_Roadmap_Generator_Prj.ipynb
```

Run the notebook cells in order.

---

## Requirements

The project requires:

```text
numpy
pandas
scikit-learn
```

---

## Limitations

* The role descriptions are predefined.
* Skill extraction uses predefined keywords and synonyms.
* The MLP recommendation model uses a small manually created dataset.
* Recommendation probability is not overall model accuracy.
* Learning duration is a heuristic estimate.
* The NLP implementation is basic.
* The project does not use LLMs, Generative AI, RAG, LangChain, Transformers, BERT, GPT, or external APIs.

---

## Future Enhancements

Future versions of the project can include:

* More career roles
* More technical skills
* Larger real-world training datasets
* Course and learning-resource recommendations
* Streamlit web application
* Improved recommendation models
* Advanced NLP techniques
* Integration with online learning platforms

---

## Conclusion

The AI Learning Roadmap Generator demonstrates how Python, NumPy, Pandas, basic NLP, machine learning, and a basic neural-network model can be combined to create a personalized learning recommendation system.

The project helps users:

* Understand their current skills
* Identify missing skills
* Choose a suitable career role
* Receive an AI-based learning recommendation
* Generate a structured learning roadmap
* Estimate their learning duration

This project is designed as a beginner-friendly Data Science project and demonstrates practical application of Python, NLP, machine learning, and data processing concepts.

---

## Author

**Yarramsetti Lakshmi Prasanna**

B.Sc. Computer Science | Data Science Fresher

GitHub:
https://github.com/prasannayarramsetti816
