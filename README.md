"# DM2024-Lab2-homework" 

d12126002

PEIRONGKANG

NTU

**DM2024-Lab2-Homework Report**

### 1. Data Preprocessing

**Objective**: To clean the data to ensure that the model can effectively extract relevant emotion features.

**Steps**:

1. Extract raw tweet text from the JSON file and remove irrelevant information, including URLs, usernames (e.g., @username), punctuation, and other unnecessary elements.
2. Standardize the text to lowercase and remove common stop words (e.g., “the,” “is,” etc.) to reduce noise.
3. Apply lemmatization to reduce words to their base forms, improving feature generalization.

### 2. Feature Engineering

**Objective**: Convert text into numerical features that can be interpreted by the model.

**Methods**:

1. Use the Term Frequency-Inverse Document Frequency (TF-IDF) vectorization method to convert cleaned text into word vector representations. TF-IDF assigns higher weights to significant words, helping the model to recognize emotion-relevant vocabulary.
2. Set the maximum number of features to 5,000 to retain meaningful features while reducing model complexity.

### 3. Model Selection and Training

**Model Selection**: Logistic Regression

**Rationale**:

- Logistic Regression performs well in text classification tasks and is computationally efficient. Its linear nature effectively handles high-dimensional, sparse data transformed by TF-IDF.
- Additionally, Random Forest was explored to assess feature importance and gain a more interpretable understanding of feature impact.

### 4. Model Evaluation and Analysis

**Objective**: To evaluate model performance, optimize settings, and analyze cases of misclassification.

**Validation Set Analysis**:

- The training set was split into training and validation subsets to observe the model's performance on unseen data.

- A confusion matrix was used to visualize classification across different emotion categories, identifying emotion pairs that the model tends to confuse.

- **Feature Importance Analysis**:

  - Random Forest was used to derive feature importance, revealing that certain emotion-related keywords (e.g., "happy," "sad") possess higher feature weights.
  - For Logistic Regression, regression coefficients were analyzed to evaluate the impact of each feature on classification.

  **Experimental Findings**:

  - The model performs well in identifying distinct emotions (e.g., “joy,” “anger”) but encounters confusion between closely related emotions (e.g., “trust” and “joy”).
  - The high-dimensional features derived from TF-IDF contribute effectively to emotion classification, with stop-word removal and lemmatization further enhancing model stability.

  ### 5. Insights and Future Optimization Directions

  **Insights**:

  - Logistic Regression is suitable for this emotion classification task, maintaining strong performance even in high-dimensional feature spaces.
  - Balancing the dataset may improve the detection of rare emotion classes.

  **Future Directions**:

  - Consider implementing deep learning models (e.g., LSTM or BERT) to further optimize emotion classification, especially for capturing complex contextual information.

  - For commonly confused emotion pairs, data augmentation or additional feature engineering could further enhance model accuracy.

    

**DM2024-Lab2-Master Experiment Report**

### 1. Data Loading

**Datasets**:

- `tweets_DM.json`: Contains tweets scraped from Twitter.
- `data_identification.csv`: Identifies whether each tweet belongs to the training or test set.
- `emotion.csv`: Contains emotion labels for each tweet in the training set.

**Data Loading and Merging**: The data was read using the `pandas` and `json` libraries, then merged based on `tweet_id` to create the final dataset.

### 2. Data Preprocessing

**Objective**: To clean text and remove noise, allowing the model to identify text features more accurately.

**Preprocessing Steps**:

- Remove URLs, usernames (e.g., `@username`), punctuation, etc.
- Use the `nltk` library for stop word removal and lemmatization to further simplify the text.

### 3. Feature Engineering

**Objective**: To transform text into numerical features for model learning.

**Method**: Use TF-IDF vectorization to convert the `clean_text` column into a term frequency feature matrix.

### 4. Model Training

**Model Selection**: Logistic Regression

**Rationale**:

- Logistic Regression is suitable for text classification tasks, offering efficient training and stability when handling sparse matrices. `max_iter=200` is set to ensure convergence.

### 5. Generating Submission File

**Objective**: To make predictions on test set data and format results as a CSV file for submission.

