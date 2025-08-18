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
