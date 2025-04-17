# 🎧 Podcast Listening Time Prediction

This project was created as part of the [Kaggle Playground Series - Season 5, Episode 4](https://www.kaggle.com/competitions/playground-series-s5e4) competition. The goal was to predict how long users would listen to individual podcast episodes based on various metadata like genre, sentiment, publication time, and number of ads.

> 🧠 **Core takeaway:** The duration of a podcast episode is by far the strongest predictor of listening time — but clever features like _time between ads_ also add meaningful lift.

---

## 📦 Project Structure

- `podcast-listening-prediction-clean.ipynb` — Main notebook with EDA, feature engineering, modeling, and evaluation.
- `requirements.txt` — List of Python libraries used.
- `README.md` — This file :)

> **Note**: Due to [Kaggle's Terms of Use](https://www.kaggle.com/terms), the dataset is **not included** in this repository.  
> You can download it directly from the competition page [here](https://www.kaggle.com/competitions/playground-series-s5e4/data).

---

## 🧪 Techniques Used

- 🧼 **Smart Imputation**: Episode length `NaN`s were filled using the mean length of that podcast.
- 🛠 **Feature Engineering**:
  - `Length_Per_Ad`: Average minutes between ads (strong predictor)
  - `Binary_Ads`: Indicator if the episode had any ads (turned out to be redundant)
  - `Length_Was_Imputed`: Flag for whether length was originally missing
- 🔄 **Log-Transform**: Applied to target variable (`Listening_Time_Minutes`) to handle skew.
- 🌲 **Modeling**: XGBoost with categorical support (`enable_categorical=True`)
- 🔍 **Permutation Importance**: Used to evaluate real contribution of each feature

---

## 📊 Key Results

| Feature              | Importance |
|----------------------|------------|
| `Episode_Length_Minutes` | ⭐ Dominant predictor |
| `Length_Per_Ad`           | 👍 Second-best feature |
| `Num_Ads`                | 💡 Still useful |
| `Binary_Ads`             | ❌ Minimal impact |

Final validation RMSE: **_your score here_**

---

## ✨ What I Learned

- Even simple features like episode length can dominate predictive power — but derived features like ad pacing can still improve the model.
- Not all intuitive features (like a binary ad flag) are useful when you already have more granular data.
- SHAP can be tricky with categorical XGBoost, but permutation importance is an awesome alternative.

---

## 📌 Setup

You can recreate the environment using:

```bash
pip install -r requirements.txt

