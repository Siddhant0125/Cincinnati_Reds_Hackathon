# Cincinnati Reds Hackathon: Player Playing Time Prediction

## Overview
This project was developed for the Cincinnati Reds Hackathon and focuses on predicting the playing time for baseball players using advanced data analysis and machine learning techniques. The workflow is implemented in a Jupyter notebook and leverages player-level and event-level data from the 2021-2023 MLB seasons.

## Problem Statement
The goal is to predict the total playing time for each player in the upcoming season (2024) based on historical performance, player roles (batter, pitcher, or two-way), and a variety of engineered features. The predictions are intended for submission to a Kaggle competition.

## Data Sources
- **savant_data_2021_2023.csv**: Raw event-level data for MLB games from 2021 to 2023, including batter and pitcher IDs, game dates, pitch details, and outcomes.
- **sample_submission.csv**: Template for Kaggle submission, listing player IDs for which predictions are required.

## Workflow
1. **Data Loading & Preprocessing**
   - Load and parse the raw CSV data.
   - Extract season information from game dates.
   - Handle missing values and engineer new features (e.g., strike zone location, velocity drop, run production impact).

2. **Feature Engineering**
   - Aggregate statistics for each player per season, including:
     - Plate appearances, games played, balls/pitches faced, strikeouts, etc.
     - Advanced metrics: wOBA, BABIP, ISO, run production, contact quality.
   - Identify two-way players (those who both pitch and bat).
   - Merge batting and pitching stats for a comprehensive player profile.
   - Compute rolling 3-year averages for key features.

3. **Modeling**
   - Train/test split on 2021-2023 data.
   - Train multiple regression models:
     - XGBoost
     - Random Forest
     - Linear Regression
   - Evaluate models using MAE and RMSE; select the best-performing model.
   - Feature importance analysis (for tree-based models).

4. **Prediction & Submission**
   - Predict 2024 playing time for all players in the submission file.
   - Save predictions in the required Kaggle format.

## Key Features Used
- Games played (batter/pitcher)
- Balls/pitches faced
- Strikeouts, plate appearances
- Advanced metrics: wOBA, BABIP, ISO, run production
- Contact quality (weak, solid, barrel, etc.)
- Rolling averages (3-year window)
- Two-way player indicator

## Results
- The best model (as per notebook output) was selected based on lowest RMSE.
- Example model performance:
  - XGBoost: MAE ~4.57, RMSE ~6.58
  - Random Forest: MAE ~15.92, RMSE ~26.02
  - Linear Regression: MAE ~2.23, RMSE ~4.64
- Predictions for 2024 were saved to `predictions_2024.csv`.

## How to Run
1. **Install Dependencies**
   - Python 3.8+
   - Jupyter Notebook
   - pandas, numpy, scikit-learn, xgboost, matplotlib
   - (Install with `pip install -r requirements.txt` if requirements file is provided)

2. **Run the Notebook**
   - Open `Hackathon_Notebook.ipynb` in Jupyter.
   - Execute all cells in order.
   - Ensure `savant_data_2021_2023.csv` and `sample_submission.csv` are in the same directory.

3. **Output**
   - The notebook will generate `predictions_2024.csv` for Kaggle submission.

## File Structure
- `Hackathon_Notebook.ipynb`: Main analysis and modeling workflow.
- `savant_data_2021_2023.csv`: Raw data file (not included here).
- `sample_submission.csv`: Kaggle submission template (not included here).
- `predictions_2024.csv`: Model output (generated by notebook).

## Acknowledgements
- Cincinnati Reds Hackathon organizers
- MLB Statcast/Savant for data
- Kaggle for competition platform

## Contact
For questions or collaboration, please contact the project author via Kaggle or GitHub. 