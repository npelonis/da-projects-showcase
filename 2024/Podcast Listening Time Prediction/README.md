# Podcast Listening Behavior & Engagement Analysis

This project analyzes podcast episode metadata to understand and predict user listening time, with a focus on identifying which content and ad-related factors most strongly influence listener engagement. The goal is to surface actionable insights into how structural decisions (episode length, ad pacing, timing) impact listening behavior.

The analysis was conducted using a dataset from the Kaggle Playground Series (Season 5, Episode 4), which simulates real-world podcast consumption data.

## Business Question

How do episode structure and ad placement relate to listener engagement, and which factors are most predictive of how long users listen to podcast episodes?

## Dataset Overview

The dataset includes episode-level metadata such as:
- Episode length
- Number of ads
- Genre and sentiment
- Publication timing
- Total listening time per episode (target)

## Project Structure

- `podcast-listening-prediction.ipynb` – Main notebook containing all analysis, modeling, and results.
- `requirements.txt` – List of packages used for this project.
- `README.md` – Project summary and documentation.

Note: The dataset is not included in this repository due to Kaggle's Terms of Service. It can be accessed from the [competition data page](https://www.kaggle.com/competitions/playground-series-s5e4/data).

## Analytical Approach

### Data Preparation and Imputation

- Missing values in `Episode_Length_Minutes` were imputed using the mean episode length for each podcast.
- A new flag (`Length_Was_Imputed`) was added to capture whether a value was missing.

### Feature Engineering

- `Length_Per_Ad`: Calculated as `Episode_Length_Minutes / Num_Ads` to capture pacing of ad breaks.
- `Binary_Ads`: Indicator for whether an episode had any ads. This feature was eventually dropped due to low importance.
- `No_Ads`: Alternate binary flag tested for interpretability.
- Log-transformation was applied to the target (`Listening_Time_Minutes`) to address skew.

### Modeling

- The final model used XGBoost with native categorical support enabled (`enable_categorical=True`).
- Hyperparameters were kept simple to focus on evaluating feature contributions.
- The model was trained and validated using a standard 80/20 split.

### Feature Importance

Permutation importance was used to evaluate which features had the most predictive value.

| Feature                   | Relative Importance |
|---------------------------|---------------------|
| Episode_Length_Minutes    | Highest             |
| Length_Per_Ad             | Moderate            |
| Num_Ads                   | Moderate            |
| Binary_Ads                | Very Low (removed)  |

## Key Insights

- Episode length was by far the most predictive feature of listening time.
- The pacing of ads (`Length_Per_Ad`) added meaningful value beyond just the number of ads.
- Binary flags like `Binary_Ads` were not helpful once more informative numeric features were present.
- SHAP was considered but not used due to compatibility issues with categorical handling in XGBoost. Permutation importance provided an effective alternative.

## Impact & Relevance

This analysis demonstrates how viewer engagement can be quantified and explained using readily available metadata. The findings have direct relevance to:
- Content strategy (episode length optimization)
- Ad experience design (pacing vs. volume)
- Engagement forecasting and experimentation
The project reflects how viewer insights teams can move beyond raw metrics to uncover behavioral patterns that inform product and content decisions.
