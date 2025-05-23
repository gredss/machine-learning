# Spotify Tracks Analysis

This repository contains an exploratory and predictive analysis on a dataset of Spotify tracks sourced from Kaggle. The project focuses on exploring audio features and building a classification target based on track popularity.

---
![poster](classification/spotify_hit_songs_binary/poster.png)
## 📂 Dataset Overview

**Source:** Spotify API and other curated datasets
**Total Rows:** 232,725
**Total Columns:** 18

The dataset comprises a wide variety of Spotify tracks enriched with metadata and audio features. It is suitable for research or projects related to music analytics, recommendation systems, or audio-based classification.

### 📌 Column Descriptions

| Column             | Description                                             |
| ------------------ | ------------------------------------------------------- |
| `genre`            | Genre of the track (e.g., Movie, Country, Alternative). |
| `artist_name`      | Name of the performing artist or band.                  |
| `track_name`       | Title of the track.                                     |
| `track_id`         | Unique Spotify identifier.                              |
| `popularity`       | Score (0–100) indicating popularity.                    |
| `acousticness`     | Likelihood of the track being acoustic (0.0–1.0).       |
| `danceability`     | Suitability for dancing (0.0–1.0).                      |
| `duration_ms`      | Track duration in milliseconds.                         |
| `energy`           | Intensity and activity level (0.0–1.0).                 |
| `instrumentalness` | Predicts if a track is instrumental (0.0–1.0).          |
| `key`              | Estimated musical key (e.g., C, D, E).                  |
| `liveness`         | Probability of the track being live-recorded.           |
| `loudness`         | Average loudness in decibels (usually negative).        |
| `mode`             | Modality: 1 = major, 0 = minor.                         |
| `speechiness`      | Presence of spoken words (0.0–1.0).                     |
| `tempo`            | Beats per minute (BPM).                                 |
| `time_signature`   | Estimated time signature (e.g., 4 = 4/4).               |
| `valence`          | Musical positiveness (0.0 = sad, 1.0 = happy).          |

A new binary feature `hit` is engineered based on whether the track's popularity is above 60.

---

## 🧰 Libraries Used

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.model_selection import (
    train_test_split, RandomizedSearchCV, cross_validate,
    GridSearchCV, cross_val_score, learning_curve
)
from sklearn.ensemble import (
    RandomForestClassifier, RandomForestRegressor,
    GradientBoostingRegressor, GradientBoostingClassifier
)
from sklearn.linear_model import LogisticRegression, LinearRegression
from sklearn.metrics import (
    classification_report, confusion_matrix,
    ConfusionMatrixDisplay, r2_score, mean_absolute_error,
    mean_squared_error
)
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import (
    StandardScaler, RobustScaler, LabelEncoder,
    OneHotEncoder, OrdinalEncoder
)
from sklearn.inspection import permutation_importance
```

---

## 🔍 Exploratory Data Analysis (EDA)

### Dataset Loading and Sampling

```python
data = pd.read_csv('SpotifyFeatures.csv')
data = data.sample(frac=0.04, random_state=42)  # Downsample for efficiency
```

### Basic Inspection

```python
data.info()
data.shape          # (9309, 18)
data.columns
data.isnull().sum() # No missing values
data.duplicated().sum() # No duplicates
```

---

## 🏷️ Target Feature Engineering

A binary classification label is created:

```python
data['hit'] = (data['popularity'] > 60).astype(int)
```

### Hit Distribution

```python
hit_distribution = data['hit'].value_counts(normalize=True)
```

| Label       | Proportion |
| ----------- | ---------- |
| 0 (Not Hit) | 85.35%     |
| 1 (Hit)     | 14.65%     |

---

## 📊 Sample Preview

| genre      | artist\_name      | track\_name           | popularity | acousticness | energy | speechiness | valence | hit |
| ---------- | ----------------- | --------------------- | ---------- | ------------ | ------ | ----------- | ------- | --- |
| Country    | A Thousand Horses | My Time's Comin'      | 45         | 0.00192      | 0.835  | 0.0609      | 0.3850  | 0   |
| Soundtrack | Mark Mothersbaugh | House Tour            | 25         | 0.93200      | 0.0798 | 0.0439      | 0.0487  | 0   |
| Reggae     | Unified Highway   | We Can't Fall (Remix) | 19         | 0.03310      | 0.737  | 0.2120      | 0.7870  | 0   |
| Electronic | Stooki Sound      | Endz - Original Mix   | 29         | 0.00428      | 0.772  | 0.0904      | 0.1700  | 0   |
| Comedy     | Bill Hicks        | I Love My Job (Live)  | 17         | 0.96500      | 0.804  | 0.8070      | 0.1850  | 0   |

---

## 🧠 Next Steps

* Feature selection and transformation
* Classification modeling using Random Forest and Gradient Boosting
* Model evaluation using accuracy, confusion matrix, and classification report
* Feature importance analysis via permutation importance

---

## 📁 File Structure

```
├── ML_Spotify.ipynb
├── README.md
```

---

## 📌 Notes

* The dataset was downsampled to 4% of the original for efficient processing.
* No missing or duplicated records were found in the sampled dataset.
* The `hit` feature is based on an arbitrary threshold and can be adjusted based on different business criteria.

---

## 📜 License

Please refer to the [Kaggle dataset license](https://www.kaggle.com/datasets/zaheenhamidani/ultimate-spotify-tracks-db) for usage permissions.


