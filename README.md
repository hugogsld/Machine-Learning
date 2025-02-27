# Machine Learning Final Report

**Online Shoppers Purchasing Intention Dataset**

Hugo GESLAND – December 2024

## Summary:

1. [Introduction to Analyzing E-Commerce Conversion Dynamics](#i-introduction-to-analyzing-e-commerce-conversion-dynamics)
2. [Justification and Source of Dataset](#ii-justification-and-source-of-dataset)
3. [Dataset Overview: The Numeric and Categorical Variables](#iii-dataset-overview-the-numeric-and-categorical-variables)
4. [Answer to Question 1: What is the relationship between features related to timing (weekend, month, and special day) and revenue generation?](#iv-answer-to-question-1-what-is-the-relationship-between-features-related-to-timing-weekend-month-and-special-day-and-revenue-generation)
5. [Answer to Question 2: Does the type of visitor (new, returning, or other) impact the decision to purchase?](#v-answer-to-question-2-does-the-type-of-visitor-new-returning-or-other-impact-the-decision-to-purchase)
6. [Answer to Question 3: How do certain web metrics (Bounce Rates, Administrative Duration, Page Value, and Product-Related metrics) influence revenue generation?](#vi-answer-to-question-3-how-do-certain-web-metrics-bounce-rates-administrative-duration-page-value-and-product-related-metrics-influence-revenue-generation)
7. [First Model: Logistic Regression](#vii-first-model-logistic-regression)
8. [Second Model – Random Forest](#viii-second-model-random-forest)
9. [Comparison of the metrics of the two models to determine which model is the most performant](#ix-comparison-of-the-metrics-of-the-two-models-to-determine-which-model-is-the-most-performant)
10. [Conclusion: How do factors influence behavior and purchase decisions on a website?](#x-conclusion-how-do-factors-influence-behavior-and-purchase-decisions-on-a-website)

---

## I - Introduction to Analyzing E-Commerce Conversion Dynamics

The rise of the Internet has significantly transformed shopping behaviors, with a steady increase in online consumers. However, despite these promising opportunities, companies, especially startups, face a critical challenge: understanding what drives a website visitor to make a purchase or abstain from it. As the marketing department of an e-commerce startup, our main objective is to increase revenue by optimizing strategies for promotion, pricing, and personalization. This study focuses on analyzing the behavior of website visitors to understand the customer's decision to make a purchase or not. The goal is to uncover the factors and contexts influencing the conversion of visitors into buyers. We aim to answer a fundamental question: what factors influence whether a website visit results in a purchase or not?

To explore this, we consider three key research questions:

1. What is the relationship between features related to timing (weekend, month, and special day) and revenue generation?
2. Does the type of visitor (new, returning, or other) impact the decision to purchase?
3. How do certain web metrics (Bounce Rates, Administrative Duration, Page Value, and Product-Related metrics) influence revenue generation?

---

## II - Justification and Source of Dataset

To address these questions, we use the **Online Shoppers Purchasing Intention Dataset** from the UC Irvine Machine Learning Repository. This dataset was specifically designed to capture user behaviors during unique sessions on an e-commerce website over a one-year period, avoiding any bias related to specific campaigns, user profiles, or periods. It contains 18 variables (10 numeric and 8 categorical) and 12,330 observations, each representing a user session. The dataset includes variables such as time spent on different sections of the website, Google Analytics metrics (bounce rate, page value), the month and weekday of the session, as well as technical information like the browser and operating system used. The target variable is binary, indicating whether a purchase was made (True) or not (False). This dataset, well-balanced in terms of data quality, allows for a detailed exploration of purchasing behaviors and serves as an ideal foundation for developing predictive models using Machine Learning algorithms, with practical applications for optimizing marketing strategies.

---

## III - Dataset Overview: The Numeric and Categorical Variables

### Numeric Variables:

- **Administrative:** Number of pages visited by the visitor related to account management.
- **Administrative Duration:** Total amount of time (in seconds) spent by the visitor on account management-related pages.
- **Informational:** Number of pages visited by the visitor related to website communication and address information.
- **Informational Duration:** Total amount of time (in seconds) spent by the visitor on informational pages.
- **Product Related:** Number of pages visited by the visitor related to product-related pages.
- **Product-Related Duration:** Total amount of time (in seconds) spent by the visitor on product-related pages.
- **Bounce Rate:** Average bounce rate value of the pages visited by the visitor.
- **Exit Rate:** Average exit rate value of the pages visited by the visitor.
- **Page Value:** Average page value of the pages visited by the visitor.
- **Special Day:** Closeness of the site visit time to a special day.

### Categorical Variables:

- **Operating System:** Operating system of the visitor.
- **Browser:** Browser of the visitor.
- **Region:** Geographic region from which the session has been initiated by the visitor.
- **Traffic Type:** Traffic source by which the visitor arrived at the website (e.g., banner, SMS, direct).
- **Visitor Type:** Whether the visitor is a New Visitor, a Returning Visitor, or Other.
- **Weekend:** Whether the date of the visit is on a weekend.
- **Month:** Month of the visit.
- **Revenue:** Whether the visit has been finalized with a transaction.

---

## IV - Answer to Question 1: What is the relationship between features related to timing (weekend, month, and special day) and revenue generation?

We analyze the **"Weekend"** variable to examine the distribution of orders throughout the week and assess the impact of weekends, determining whether it can be a determining factor.

- With only **23.26%** of visitors making a purchase, there is an opportunity to target weekends, as this is when people are most likely to browse and consider making purchases online. Therefore, it would be valuable to implement special weekend promotions to encourage users to complete a purchase at the end of their visit.

- An analysis of the distribution of purchases across months shows that **November** has the best conversion rate. Therefore, understanding why this month has the highest conversion rate is key to implementing promotional offers or other strategies to increase traffic and maintain this rate on a larger scale.

- **Chi-square test** results show that temporal variables (Month, Weekend, Special Day) significantly influence customer revenue. The Month variable has the strongest impact (Chi2 = 384.935, p = 0.000), followed by Special Days (Chi2 = 96.077, p = 0.000) and Weekends (Chi2 = 10.391, p = 0.001).

---

## V - Answer to Question 2: Does the type of visitor (new, returning, or other) impact the decision to purchase?

We analyzed the impact of the type of visitor (new, returning, or other) on purchase decisions. The data analysis shows that the type of visitor significantly impacts revenue generation. Although new visitors generally generate higher revenue due to promotions tied to their first purchase, returning visitors account for the largest traffic on the site. However, despite their high number, their purchase-to-no-purchase conversion rate is low, indicating they are not being effectively converted into regular buyers.

- The Chi-squared test result (135.252 with a p-value less than 0.05) indicates a statistically significant relationship between the visitor type and revenue generation.

---

## VI - Answer to Question 3: How do certain web metrics (Bounce Rates, Administrative Duration, Page Value, and Product-Related metrics) influence revenue generation?

We created a **correlation matrix** to identify correlations between web metrics and revenue. Key findings:

- **Visitors who generate revenue** tend to have lower bounce rates, higher page values, and spend more time on product pages.
- Time spent on **administrative pages** does not significantly impact conversions.
- Reducing bounce rates and improving page value are crucial for optimizing conversion rates.

---

## VII - First Model: Logistic Regression

We used **Logistic Regression** to predict whether a visitor makes a purchase (True or False). The regression model showed uneven performance:

- **Accuracy:** 87%
- **Precision (False):** 0.88
- **Precision (True):** 0.73
- **Recall (False):** 0.97
- **Recall (True):** 0.34
- **AUC:** 0.89

The model struggles to predict purchases accurately, with a lower recall for buyers.

---

## VIII - Second Model – Random Forest

The **Random Forest** model showed better overall performance:

- **Accuracy:** 89%
- **Precision (False):** 0.92
- **Precision (True):** 0.71
- **Recall (False):** 0.95
- **Recall (True):** 0.56
- **AUC:** 0.91

The Random Forest model performs better in detecting non-buyers but struggles with buyers.

---

## IX - Comparison of the metrics of the two models to determine which model is the most performant:

| Metric                         | Logistic Regression | Random Forest   |
|---------------------------------|---------------------|-----------------|
| **Accuracy**                    | 87%                 | 89%             |
| **AUC**                         | 0.89                | 0.91            |
| **Precision (False)**           | 0.88                | 0.92            |
| **Precision (True)**            | 0.73                | 0.71            |
| **Recall (False)**              | 0.97                | 0.95            |
| **Recall (True)**               | 0.34                | 0.56            |

The Random Forest model provides better performance overall, but Logistic Regression is more suitable for understanding key influencing factors and providing actionable insights for marketing teams.

---

## X - Conclusion: How do factors influence behavior and purchase decisions on a website?

The analysis reveals that key factors like **timing** (weekend, month, special days), **visitor type** (new vs returning), and **web metrics** (bounce rates, page value) influence online purchasing behavior. To maximize revenue, focus on **reducing bounce rates**, improving **page value**, and targeting **new visitors** with **personalized offers**.

**Logistic regression** remains the preferred model for providing transparent insights to marketing teams, while **Random Forest** can be used for more precise predictions.

By optimizing the user experience and focusing on the most impactful factors, companies can significantly increase their website conversion rates and revenue.
