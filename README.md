# Diabetes Management Platform

## Motivation

Diabetes is a prevalent and serious health issue across the country. While there is no cure for type-2 diabetes, its impact can be managed through lifestyle changes. Existing diabetes management applications are limited in functionalities and often require the use of multiple applications.


## Top Existing Applications

Most existing applications require subscriptions and lack a wide range of functionalities.

## Goal

Our goal is to simplify diabetes management by providing a comprehensive platform that analyzes health data, offers advice, recommendations, and locates nearby healthcare facilities—all through a simple and user-friendly interface.

## Features

- **Diabetes Status Prediction:**
  - Predict whether a patient is diabetic or not.
  - Risk score calculator in case of missing data.
  
- **Real-time Analysis and Visualization:**
  - Analyze and visualize health factors.

- **AI-powered Chatbot:**
  - Interacts with users, considering inputs and relevant details.
  - Answers user queries.

- **Edamam API Integration:**
  - Provides recipe suggestions.

- **Healthcare Facilities Finder:**
  - Uses Google Maps API to locate nearby healthcare facilities.

- **Speech-to-Text:**
  - Improves accessibility.

## Diabetes Status Predictor

### Steps Involved

1. Fetch and clean raw data.
2. Exploratory Data Analysis (EDA).
3. Preprocessing.
4. Train/test/validation set split.
5. Train models on the training set.
6. Validate models using the validation set.
7. Fine-tune models on the validation set.
8. Use the test set for final testing.

### Machine Learning Model

#### Data

- Diabetes prediction dataset.
- 0 implies non-diabetic, 1 implies diabetic.
- Features: Gender, age, hypertension, heart_disease, smoking_history, bmi, HbA1c_level, blood_glucose_level.
- Target variable: "diabetes."
- 100,000 observations.

#### Significant Class Imbalance

- Resampling performed to address class imbalance.

#### Model Training

- Tried Logistic regressor, KNN classifier, Random forest classifier, and XGBoost classifier.
- XGBoost classifier showed the best performance.

#### XGBoost Classifier

- 5-fold grid search cross-validation using roc-auc as the scoring parameter.
- Parameters:
  - n_estimators: 200, 300, 400.
  - Learning rate: 0.01, 0.05, 0.1.
  - Max depth: 1, 2, 3.
- Best parameters: n_estimators: 400, Learning rate: 0.1, Max depth: 3.

## Risk Score Calculator

Users can calculate their risk scores with limited inputs, based on the Cambridge diabetes risk score equation.

## Chatbot

Users can ask questions and receive answers from reputable sources through ChatGPT. The chatbot can also generate custom visualizations from user data.

### Methodology

- Assistant API
- Custom prompting
- Knowledge Retrieval
- Code Interpreter

### Iterations

1. **Bot 1: Base ChatGPT - Chatbot**
2. **Bot 2: Diabetes Advisor**
   - Retrieves information from health documents from reputable sources (John Hopkins, National Institute of Health, .edu, or .gov domains).
3. **Bot 3: Health Visualization Chatbot**
   - Provides custom visualizations of user data.

### Prompting

- Bot 2 with attached health documents.
- Bot 3 for custom visualizations (GPT executes Python code on uploaded files).

## Get Recipes

- Suggests diabetic-friendly recipes based on user-provided keywords.
- Uses Edamam API.

## Healthcare Facilities Nearby

- Powered by Google Maps API.
- Finds nearby healthcare units based on the user-provided address.

## Future

- Web Browsing feature added to chatbot.
- Extract structured data from unstructured text data.
- Add moderation and constrain user input.
- Facilitate communication between patients and doctors.
- Develop a payment model.
