# Customer Churn Prediction using Deep Learning

This project predicts **bank customer churn** using **Deep Learning (Artificial Neural Networks)**. It leverages **data preprocessing, feature engineering, and neural network optimization** to predict whether a customer will leave the bank based on their profile and behavior characteristics.

The project also includes a **Streamlit web application** for real-time churn prediction.

** Live Demo:** [Customer Churn Prediction App](https://deep-learning-projects-3m352tfhkbf5tmmrgaqoqh.streamlit.app/)

---

## Project Overview

* **Dataset:**
  * Source: Bank Customer Churn Dataset
  * Contains 10,000 customer records with 14 features including demographics (age, gender, geography), account information (credit score, balance, tenure), and banking behavior (number of products, credit card status, active membership)
  * Target variable: `Exited` (1 = churned, 0 = retained)

* **Workflow:**
  * Data loading and exploratory analysis
  * Data preprocessing:
    * Handling categorical features with Label Encoding (Gender) and One-Hot Encoding (Geography)
    * Feature scaling using StandardScaler
    * Train/test split (80/20)
  * Neural network architecture design:
    * Input layer with 12 features
    * Configurable hidden layers with ReLU activation
    * Output layer with sigmoid activation for binary classification
  * Hyperparameter tuning using GridSearchCV:
    * Optimized number of neurons (8, 16, 32)
    * Optimized number of hidden layers (1, 2, 3)
    * Optimized training epochs (50, 100)
  * Model training with:
    * Binary cross-entropy loss
    * Adam optimizer
    * Early stopping to prevent overfitting
    * TensorBoard callback for monitoring
  * Model evaluation and performance analysis
  * Deployment as interactive Streamlit web application

---

## Tech Stack

* **Python 3.10+**
* **TensorFlow/Keras** – deep learning framework
* **Scikit-learn** – preprocessing, encoding, train-test split, GridSearchCV
* **Pandas, NumPy** – data manipulation and numerical operations
* **Streamlit** – web application framework for deployment
* **Pickle** – model and preprocessor serialization

---

## Project Structure

```
├── main.ipynb              # Jupyter notebook: EDA, preprocessing, model training, tuning
├── app.py                  # Streamlit web application for predictions
├── Churn_Modelling.csv     # Dataset
├── output/                 # Trained model and preprocessor files
│   ├── final_model.h5      # Trained neural network model
│   ├── label_encoder_gender.pkl
│   ├── onehot_encoder_geo.pkl
│   └── scaler.pkl
├── requirements.txt        # Python dependencies
└── README.md              # Project documentation
```

---

## Installation & Setup

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/customer-churn-prediction.git
cd customer-churn-prediction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Required Libraries

```
tensorflow
scikit-learn
pandas
numpy
streamlit
scikeras
```

---

## Running the Project

### Option 1: Jupyter Notebook

Open and run the analysis notebook:

```bash
jupyter notebook main.ipynb
```

The notebook includes:
* Data exploration and visualization
* Feature preprocessing
* Neural network model creation
* Hyperparameter tuning with GridSearchCV
* Model evaluation

### Option 2: Streamlit Web Application

Launch the interactive prediction interface:

```bash
streamlit run app.py
```

The app allows you to:
* Input customer features interactively
* Get real-time churn probability predictions
* View whether the customer is likely to churn

---

## Model Performance

### Best Hyperparameters (GridSearchCV)

| Parameter | Optimal Value |
|-----------|---------------|
| Neurons per layer | 16 |
| Number of hidden layers | 1 |
| Epochs | 100 |
| Batch size | 32 |

### Model Evaluation Metrics

| Metric | Value |
|--------|-------|
| Training Accuracy | ~86.4% |
| Validation Accuracy | ~86.5% |
| Loss Function | Binary Cross-entropy |
| Optimizer | Adam |

* **GridSearch Best Score:** 85.72% (3-fold cross-validation)
* **Early Stopping:** Implemented with patience to prevent overfitting
* **Final Model:** Saved as `final_model.h5` after training for 27 epochs (early stopping triggered)

---

## Neural Network Architecture

The final optimized model consists of:

```
Input Layer (12 features)
    ↓
Hidden Layer 1 (16 neurons, ReLU activation)
    ↓
Output Layer (1 neuron, Sigmoid activation)
```

**Key Features Used:**
* CreditScore
* Gender (encoded)
* Age
* Tenure
* Balance
* NumOfProducts
* HasCrCard
* IsActiveMember
* EstimatedSalary
* Geography (one-hot encoded: France, Germany, Spain)

---

## Feature Engineering

### Preprocessing Steps

1. **Removed irrelevant features:** `RowNumber`, `CustomerId`, `Surname`
2. **Label Encoding:** Applied to `Gender` (Male/Female → 0/1)
3. **One-Hot Encoding:** Applied to `Geography` (France, Germany, Spain → 3 binary columns)
4. **Feature Scaling:** StandardScaler applied to normalize all features
5. **Data Split:** 80% training, 20% testing

---

## Streamlit Application Features

The web app provides an intuitive interface with:

* **Interactive Input Fields:**
  * Dropdown selections (Geography, Gender, Credit Card, Active Member)
  * Sliders (Age, Tenure, Number of Products)
  * Number inputs (Balance, Credit Score, Estimated Salary)

* **Real-time Prediction:**
  * Displays churn probability as a percentage

* **User-Friendly Design:**
  * Clean, professional interface
  * Immediate feedback
  * No technical knowledge required

** Try it live:** [Customer Churn Prediction App](https://deep-learning-projects-3m352tfhkbf5tmmrgaqoqh.streamlit.app/)

---

## Key Insights

* **Model converges well:** Training and validation accuracy are closely aligned (~86%), indicating good generalization
* **Early stopping effective:** Model stopped at epoch 27 out of 100, preventing overfitting
* **Optimal architecture:** Single hidden layer with 16 neurons provides the best balance of complexity and performance
* **Preprocessing crucial:** Feature scaling and encoding significantly impact model performance

---

## Dataset Features

| Feature | Description |
|---------|-------------|
| CreditScore | Customer's credit score |
| Geography | Customer's country (France, Spain, Germany) |
| Gender | Male or Female |
| Age | Customer's age |
| Tenure | Years with the bank |
| Balance | Account balance |
| NumOfProducts | Number of bank products used |
| HasCrCard | Whether customer has credit card (0/1) |
| IsActiveMember | Whether customer is active (0/1) |
| EstimatedSalary | Customer's estimated salary |
| Exited | Target variable: 1 = Churned, 0 = Retained |

---


* Dataset: Bank Customer Churn Dataset
* Framework: TensorFlow/Keras
* Deployment: Streamlit
