# Logistic Regression – Airline Customer Satisfaction Prediction

## Project Overview
In this project, I analyzed passenger survey data to build a Logistic Regression classification model. The goal was to predict whether a passenger would be "Satisfied" or "Dissatisfied" with their flight, and more importantly, to extract the underlying factors driving those emotions. This project translates raw classification metrics into actionable business strategies for improving customer retention.

## Dataset Description
The dataset contains survey responses and flight details from over 129,000 airline passengers. 
* **Target Variable:** `satisfaction` (Satisfied vs. Dissatisfied)
* **Features:** Includes demographics (`Age`, `Customer Type`), flight details (`Class`, `Flight Distance`), and 1-5 rating scores for services (`Inflight entertainment`, `Seat comfort`, `Leg room service`, etc.).

## Environment Setup
To run this project locally, you will need Python installed along with the following libraries:
`pip install pandas scikit-learn seaborn matplotlib`

## Step-by-Step Methodology
1. **Data Cleaning:** Identified and removed 393 rows containing missing values in the `Arrival Delay in Minutes` column.
2. **Feature Encoding:** * Transformed the target variable (`satisfaction`) into a binary format (1 = Satisfied, 0 = Dissatisfied) using targeted string replacement.
   * Converted categorical predictors (`Customer Type`, `Type of Travel`, `Class`) into numerical format using One-Hot Encoding (`pd.get_dummies`), utilizing `drop_first=True` to prevent multicollinearity (the dummy variable trap).
3. **Data Splitting & Scaling:** Split the dataset into an 80% training set and a 20% testing set to ensure unbiased evaluation. Applied `StandardScaler` to normalize the features so larger numerical values (like Flight Distance) wouldn't distort the Logistic Regression algorithm.
4. **Model Training:** Built and trained a binomial Logistic Regression model using `Scikit-Learn`.

## Final Model Evaluation
The model was evaluated on the unseen 20% testing data using a Confusion Matrix.
* **Precision (84%):** Out of all the passengers the model *predicted* would be satisfied, 84% actually were.
* **Recall (84%):** Out of all the *actually* satisfied passengers in the real world, the model successfully identified 84% of them.
* **Conclusion:** The model is highly balanced and reliable for predicting customer sentiment. 

## Key Business Insights & Recommendations
By extracting the coefficients from the Logistic Regression model, I identified the top drivers of passenger emotion:

**1. The Biggest Driver of Satisfaction: Inflight Entertainment (Coefficient: +0.96)**
* **Insight:** Passengers care more about their screens and entertainment than almost any other physical comfort metric. 
* **Recommendation:** The airline should prioritize capital expenditure on upgrading Wi-Fi speeds and expanding the library of free movies/shows on the seatback screens. 

**2. The Biggest Driver of Dissatisfaction: "Disloyal" Customers (Coefficient: -0.72)**
* **Insight:** Passengers labeled as "disloyal" (first-time flyers or infrequent travelers) are significantly more likely to leave a negative review than frequent flyers in the exact same seats.
* **Recommendation:** The airline needs to overhaul the "first flight" experience. Implement a system where flight attendants are notified of first-time flyers on their manifest so they can provide proactive, welcoming service to convert them into loyal customers.