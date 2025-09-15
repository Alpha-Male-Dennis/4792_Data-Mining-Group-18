# 1. Business Understanding

## Problem Statement

The Journal of Natural and Applied Sciences (JONAS) publishes multidisciplinary research articles across various disciplines, including environmental science, agriculture, mining, engineering, and water resources. Manually categorizing these articles into their respective disciplines based on titles and abstracts is time-consuming and subjective. An automated classification model is needed to accurately assign articles to their relevant disciplines using natural language processing (NLP) and machine learning techniques.

## Business Objectives

The primary business objectives are:

1. Efficient Article Classification – Automate the categorization of journal articles to streamline editorial workflows.
2. Improved Discoverability – Enhance search and retrieval of articles by discipline for researchers and readers.
3. Reduced Manual Effort – Minimize the need for manual tagging by editors, reducing human error and workload.

## Success Criteria
* The model should correctly classify articles into predefined disciplines with high accuracy.
* The solution should be scalable to handle new articles as the journal continues publishing.
* The classification system should be interpretable, allowing editors to verify and adjust categories if needed.

## Data Mining Goals

* Text Preprocessing – Clean and preprocess article titles and abstracts (tokenization, stopword removal, stemming/lemmatization).
* Feature Extraction – Convert text into numerical features using techniques like TF-IDF or word embeddings (Word2Vec, GloVe).
* Model Development – Implement a supervised classification model (e.g., Naïve Bayes, SVM, Random Forest, or Neural Networks) to predict article disciplines.
* Evaluation – Assess model performance using metrics such as accuracy, precision, recall, and F1-score.

## Initial Project Success Criteria

* Accuracy: The model should achieve at least 85% accuracy in classifying articles into the correct discipline.
* Interpretability: The model should provide explainable predictions (e.g., feature importance in decision-making).
* Scalability: The solution should handle new, unseen articles without significant performance degradation.

# 2. Data Understanding

## Initial Findings Summary

### Data Loading and Description:

The dataset, journal_articles_final.csv, was successfully loaded into a pandas DataFrame named df.
The dataset contains 47 articles and 7 columns: article_id, title, abstract, keywords, discipline, year, and volume.
The columns have the following data types: article_id, title, abstract, keywords, and discipline are objects (strings), while year and volume are integers.


### Data Initial Exploration:

The distribution of articles by discipline shows that "Engineering" has the highest number of articles, followed by "Environmental Science" and "Agriculture".
The top 20 most frequent words in the abstracts (excluding stopwords) include terms like "study", "data", "water", "mining", and "construction", which align with the prominent disciplines in the dataset.

### Data Quality Verification:
There are missing values in the abstract (2 missing) and keywords (5 missing) columns. There are no duplicate articles based on the combination of 'title' and 'abstract'
# 3. Data Preparation

This phase of the project focused on preparing the raw journal article data for machine learning model development. The key steps involved:

**Data Cleaning:**
  *   Addressed missing values, specifically in the 'keywords' column, by filling them with empty strings.
  *   Checked for and confirmed the absence of duplicate articles based on title and abstract.

**Feature Engineering:**

  *   Created a new feature, 'CombinedText', by concatenating the cleaned 'title', 'abstract', and 'keywords' columns. This provides a comprehensive text representation for each article.

**Data Transformation:**
    *   Converted the categorical 'discipline' labels into a numerical format using One-Hot Encoding, which is necessary for most machine learning algorithms.
    *   Transformed the 'CombinedText' into a numerical representation using the Bag-of-Words model. This vectorization process allows the text data to be used as input for classification models.
Each step was clearly documented within the notebook, explaining the rationale behind the data cleaning, feature engineering, and transformation decisions.

# 4. Modeling

This phase focused on experimenting with different machine learning algorithms to classify articles into disciplines based on their titles and abstracts.

## Algorithm Selection
Three models were chosen for comparison:
1. **Random Forest Classifier** – robust to overfitting, handles high-dimensional embeddings well.
2. **Support Vector Machine (SVM)** – effective in high-dimensional spaces, good for text embeddings.
3. **Logistic Regression** – a strong baseline, efficient, and interpretable.

## Data Preparation for Modeling
- Used **Sentence-BERT (all-MiniLM-L6-v2)** embeddings (384 dimensions) for text representation.  
- Combined article **title + abstract** to form the input feature text.  
- Encoded discipline labels using **LabelEncoder**.  
- Training/testing split: **34 training samples (75%)**, **12 test samples (25%)**.  

## Model Training
- Applied `class_weight='balanced'` to handle class imbalance.  
- Used **Leave-One-Out Cross-Validation (LOOCV)** for reliable evaluation on the small dataset.  
- Configurations:  
  - Random Forest: limited depth (`max_depth=5`) to avoid overfitting.  
  - SVM: linear kernel, probability enabled.  
  - Logistic Regression: `max_iter=1000` for convergence.  

## Initial Results (LOOCV Accuracy)
- Random Forest: **14.7%**  
- SVM: **26.5%**  
- Logistic Regression: **32.4%**  

Logistic Regression showed the best stability and performance during training.

---
