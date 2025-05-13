# 🍽️ Restaurant Recommendation System

This project builds a restaurant recommendation system using a dataset sourced from Zomato. It includes detailed restaurant attributes, customer reviews, and offerings. The system performs data preprocessing, exploratory data analysis (EDA), and prepares data for building a recommendation engine.

---

## 📁 Dataset Overview

**Filename**: `3B.tsv`
**Source**: Zomato (Bangalore region)

### Columns Description

| Column                        | Description                                           |
| ----------------------------- | ----------------------------------------------------- |
| `url`                         | The Zomato URL of the restaurant                      |
| `name`                        | Restaurant name                                       |
| `online_order`                | Accepts online orders (Yes/No)                        |
| `book_table`                  | Supports table booking (Yes/No)                       |
| `rate`                        | Overall Zomato rating (scale: 0–5)                    |
| `votes`                       | Number of ratings received                            |
| `location`                    | Restaurant location                                   |
| `rest_type`                   | Type of restaurant (e.g., Quick Bites, Casual Dining) |
| `cuisines`                    | Types of cuisines offered                             |
| `approx_cost(for two people)` | Estimated cost for two people (INR)                   |
| `listed_in(type)`             | Listing category (e.g., Delivery, Dine-out)           |
| `sell_beverages`              | Sells beverages (yes/no)                              |
| `sell_chinese_food`           | Offers Chinese cuisine (yes/no)                       |
| `sell_thai_food`              | Offers Thai cuisine (yes/no)                          |
| `sell_indian_food`            | Offers Indian cuisine (yes/no)                        |
| `sell_mediterranean_food`     | Offers Mediterranean cuisine (yes/no)                 |
| `sell_fast_food`              | Offers fast food (yes/no)                             |
| `sell_desserts`               | Offers desserts (yes/no)                              |

---

## 🔍 Exploratory Data Analysis (EDA)

Key findings from the EDA process:

* Missing values were present in several categorical and numerical columns and were appropriately handled.
* The dataset contains:

  * **6091** unique customers
  * **2109** unique cuisines
  * **85** restaurant types
  * **91** distinct locations
* Numerical feature distributions:

  * `rate`: Mean ≈ 3.7, normally distributed
  * `approx_cost(for two people)`: Mean ≈ ₹417
* Visualizations included:

  * Ratings distribution
  * Top 10 cuisines
  * Cost distribution
  * Top 10 restaurant types
  * Top 10 locations

---

## 🧹 Data Preprocessing

* Converted columns `rate` and `approx_cost(for two people)` to numeric.
* Missing values were imputed using mean (for numerical) or dropped (for categorical).
* Dropped unnecessary features: `online_order`, `book_table`, and `votes`.
* Separated categorical and numerical features.
* Cleaned dataset used for further modeling.

---

## 🧠 Recommendation System

The project is structured to build a restaurant recommendation system based on customer preferences. It sets up the framework for:

* **Content-based filtering** using cosine similarity on textual and categorical attributes.
* Potential future integration of collaborative filtering or hybrid models.

---

## 📊 Visualizations

The analysis includes the following visual plots:

* Histogram + KDE of restaurant ratings
* Bar charts for top cuisines and restaurant types
* Histogram of approximate cost for two
* Bar chart of most common restaurant locations

---

## 📦 Dependencies

Ensure the following libraries are installed:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## 📝 Usage

1. Load the dataset:

   ```python
   df = pd.read_csv('3B.tsv', delimiter='\t')
   ```
2. Preprocess and clean the data as shown in the notebook/script.
3. Perform EDA to understand data distribution.
4. Build a recommendation model using cosine similarity or vectorization techniques.

---

## 📈 Future Enhancements

* Implement collaborative filtering using user-item matrices.
* Deploy a web-based restaurant recommender interface.
* Integrate NLP techniques for analyzing reviews and ratings.
* Use clustering techniques for user segmentation.

---

## 📑 License

This project is for educational and research purposes.
