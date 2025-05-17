# 📈 Sales Forecasting Using Polynomial Regression

This project applies polynomial regression to forecast sales trends based on historical production data. The objective is to provide accurate, data-driven insights that support strategic decisions such as inventory planning, infrastructure investment, and operational scaling.

## 🔍 Overview

In real-world production environments, sales growth often follows a non-linear trajectory. A linear model may fail to capture such dynamics, which is why polynomial regression was explored. This method allows for more flexibility in modeling complex trends over time.

Through experimentation with polynomial degrees ranging from 1 to 6, we identified a **third-degree polynomial** as the most effective model. It captures the accelerating sales momentum while maintaining a balance between complexity and performance.

## ⚙️ Methodology

### 1. Model Selection and Trend Analysis

- Fitted polynomial regression models of order 1 through 6.
- Visualized the results to analyze how each polynomial captured the underlying pattern.
  ![Polynomial Fit Order 1–6](machine-learning/conventional/scientific-computing-sales-trend/images/polynomial_orders.png)
- Found that a third-order polynomial best reflects the accelerating sales trend, especially over the latter periods of the dataset.
  ![Best Fit: Third-Order Polynomial](machine-learning/conventional/scientific-computing-sales-trend/images/third_order_best_fit.png)
- Higher-degree models showed minimal improvements and increased the risk of overfitting.



### 2. Model Evaluation

- Applied **cross-validation** to assess model robustness and generalization capability.
- Used **Mean Squared Error (MSE)** as the primary evaluation metric.
- Results:
  - Linear Model (Order 1): MSE ≈ 1,459,207.44 → poor fit.
  - Third-Degree Polynomial: Optimal balance of accuracy and interpretability.

The root of the selected polynomial (where y = 0) was approximately -15.378, which lies outside the data range. This confirms there is no predicted drop to zero production within the timeframe analyzed.

### 3. Forecasting Production Thresholds

- Leveraged the third-degree polynomial to estimate when production will exceed **25,000 units**.
- This threshold serves as a trigger for capacity expansion planning, particularly for warehouse space.
- Factored in a **13-month lead time** to ensure operational readiness.
- Supplementary validation using **Taylor Series approximation** was conducted for consistency in forecast estimation.

## 📊 Key Insight

The model highlights a clear, accelerating growth pattern in production. This trend implies:

- Strong and sustained demand
- Potential for **scaling operations**
- Justification for **strategic investments** in logistics and infrastructure

## 🛠️ Technologies Used

- **Python** (NumPy, Pandas, Matplotlib)
- **Scikit-learn** (PolynomialFeatures, LinearRegression, cross-validation)
- **Symbolic estimation** with Taylor Series for scenario analysis


## 📌 Business Impact

- **Improved Forecasting**: More accurate sales trend models enable better business planning.
- **Capacity Management**: Clear prediction of production thresholds supports warehouse and supply chain decisions.
- **Reduced Risk**: Validation techniques prevent overfitting and ensure scalable performance in production environments.

## 📬 Contact

For collaboration, technical discussions, or inquiries related to this project, please feel free to reach out.


