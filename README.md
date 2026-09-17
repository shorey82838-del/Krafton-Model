# Krafton-Model
Personalized Feed Recommendation System using player telemetry data, Random Forest churn prediction, engagement scoring, feature importance analysis, and personalized discount tiers.
🎮 Personalized Feed Recommendation System
An end-to-end machine learning project that uses player telemetry data to predict player churn, estimate engagement potential, and generate personalized player-level recommendations.

The project uses a Random Forest Classifier to predict whether a player is likely to churn. The predicted probability of remaining active is then used as an engagement score for personalized feed ranking and discount-tier assignment.

📌 Project Overview
The goal of this project is to demonstrate how player behavioral and financial telemetry can be transformed into actionable personalization signals.

The pipeline includes:

Loading player telemetry data
Cleaning and preprocessing the dataset
Handling missing values and data-quality issues
Training a Random Forest classification model
Predicting player churn
Evaluating model performance
Analyzing feature importance
Generating player engagement scores
Assigning personalized discount tiers
📊 Dataset
The project uses a dataset containing 500 player records and 10 variables.

Features
Feature	Description
player_id	Unique player identifier
session_frequency_weekly	Number of player sessions per week
avg_survival_time_min	Average survival time per session
kd_ratio	Player kill/death ratio
win_loss_streak	Current win/loss streak
currency_balance_uc	In-game currency balance
lifetime_value_usd	Estimated player lifetime value
royale_pass_tier	Player's Royale Pass tier
days_since_last_session	Days since the player's most recent session
churned	Target variable indicating whether the player churned
🧹 Data Preprocessing
The notebook performs several data-cleaning operations before modeling.

Missing Values
Numerical missing values are replaced with the column median.
Categorical missing values are replaced with the most frequent value.
Data Quality
The preprocessing pipeline also:

Clips negative session_frequency_weekly values to zero.
Caps extreme kd_ratio values at the 99th percentile.
Converts currency_balance_uc from string-formatted values into numeric values.
Encodes player_id using LabelEncoder.
🤖 Machine Learning Model
A Random Forest Classifier is trained to predict the churned target.

Model Features
The model uses:

Session frequency
Average survival time
KD ratio
Win/loss streak
In-game currency balance
Lifetime value
Royale Pass tier
Days since last session
The dataset is split into:

80% training data
20% testing data
The model is implemented using:

RandomForestClassifier(
    n_estimators=100,
    random_state=42
)
📈 Model Evaluation
The model is evaluated using:

Accuracy
Classification report
Confusion matrix
The notebook also visualizes the confusion matrix to compare predicted and actual player churn classifications.

Note: Exact performance metrics depend on executing the notebook with the supplied dataset.

🔍 Feature Importance
Random Forest feature importance is used to identify which player characteristics contribute most strongly to the model's predictions.

This provides an interpretable view of the behavioral signals that can be used for personalization.

The notebook generates a feature-importance visualization for the selected player attributes.

🎯 Personalized Engagement Score
The model's predicted probability for the non-churned / active class is used as a proxy for player engagement.

The project provides a function:

rank_personalized_feed(
    player_id,
    model,
    dataframe,
    features
)
For an individual player, it returns an engagement score such as:

Player UID_10000 Engagement Score: 0.82
A higher score indicates a higher predicted likelihood of remaining active.

💰 Personalized Discount Strategy
The project also translates engagement scores into simple personalized discount tiers.

Engagement Score	Discount Tier	Strategy
< 0.40	50% Win-back	Target players at high churn risk
0.40 – <0.70	25% Neutral	Encourage continued engagement
≥ 0.70	10% Loyalty	Reward highly engaged players
This provides a basic example of how machine-learning predictions can support personalized player-retention strategies.

🏗️ Project Pipeline
Player Telemetry Data
        │
        ▼
Data Cleaning & Preprocessing
        │
        ▼
Feature Selection
        │
        ▼
Train/Test Split
        │
        ▼
Random Forest Classifier
        │
        ▼
Churn Prediction
        │
        ▼
Engagement Probability
        │
        ├───────────────┐
        ▼               ▼
Feature Importance   Personalized
Analysis             Engagement Score
                         │
                         ▼
                  Discount Tier
📁 Repository Structure
├── Personised_Model.ipynb
├── krafton_player_telemetry_raw_500.csv
└── README.md
🛠️ Technologies Used
Python
Pandas – data manipulation
NumPy – numerical processing
Matplotlib – visualization
Seaborn – statistical visualization
Scikit-learn – machine learning and evaluation
Jupyter Notebook – development and experimentation
🚀 How to Run
1. Clone the repository
git clone <your-repository-url>
cd <repository-name>
2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
3. Launch Jupyter Notebook
jupyter notebook
4. Open
Personised_Model.ipynb
5. Run the notebook
Make sure the CSV dataset is available at the path expected by the notebook, or update the file_path variable to your local dataset location.

💡 Business Applications
This approach can be extended to support:

Player churn prevention
Personalized content feeds
Player segmentation
Retention campaigns
Loyalty programs
Targeted discounts
Engagement monitoring
Player lifecycle management
🔮 Future Improvements
Potential improvements include:

Hyperparameter tuning using GridSearchCV or RandomizedSearchCV
Cross-validation for more reliable evaluation
ROC-AUC and precision-recall analysis
SHAP-based model explainability
More sophisticated recommendation/ranking algorithms
Time-series player behavior analysis
Personalized content recommendations rather than only engagement scoring
Separate treatment of new, active, and returning players
A production API for real-time engagement scoring
Dashboard development using Streamlit or Power BI
⚠️ Limitations
This project uses churn prediction as a proxy for engagement. Therefore, the engagement score should not be interpreted as a direct measurement of content-level engagement.

The current implementation also demonstrates a recommendation strategy rather than a production-ready recommendation engine.

The discount thresholds are manually defined and would ideally be optimized using historical campaign performance and business objectives.

👤 Project Purpose
This project demonstrates an applied machine-learning workflow for transforming raw player telemetry into predictive engagement signals and personalized retention strategies.

It is suitable as a portfolio project for demonstrating skills in:

Data preprocessing
Exploratory analysis
Machine learning
Classification
Model evaluation
Feature importance
Personalization
Business-oriented ML applications
📜 License
This project can be distributed under the MIT License unless a different license is required for the dataset or project.
