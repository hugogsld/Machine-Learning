# Machine Learning Final Report

**Online Shoppers Purchasing Intention Dataset**  
Hugo GESLAND – December 2024

## Introduction

This report analyzes the behavior of website visitors and their decision-making process regarding online purchases. The primary aim is to understand the factors influencing whether a visitor makes a purchase or not. By applying machine learning algorithms to the **Online Shoppers Purchasing Intention Dataset**, we seek to answer key questions about how timing, visitor type, and web metrics affect revenue generation. This study will utilize techniques such as Logistic Regression and Random Forest to build predictive models, compare their performance, and provide insights for improving e-commerce strategies.

## Table of Contents:

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

The rapid growth of online shopping has shifted the way consumers interact with e-commerce websites. However, despite the abundance of traffic on these sites, many visitors do not convert into buyers. For e-commerce businesses, understanding the factors that influence a visitor's decision to purchase is crucial for improving conversion rates and increasing revenue. This project focuses on identifying these critical factors by analyzing user behavior data and applying machine learning models to predict purchasing intent. By understanding how various features (such as visitor type, timing, and web engagement) affect conversion, we aim to provide actionable insights that can enhance marketing strategies.

---

## II - Justification and Source of Dataset

This analysis is based on the **Online Shoppers Purchasing Intention Dataset**, sourced from the UC Irvine Machine Learning Repository. The dataset contains information about online shopper behavior collected over a one-year period. It includes 18 variables (10 numeric and 8 categorical) and 12,330 observations, representing different user sessions on the website. These variables capture key user metrics such as time spent on pages, traffic source, and demographic details. The target variable indicates whether a visitor made a purchase (True) or not (False). The dataset is well-suited for building predictive models to analyze purchasing behavior and optimize strategies for increasing conversions.

---

## III - Dataset Overview: The Numeric and Categorical Variables

### Numeric Variables:
- **Administrative**: Number of pages visited related to account management.
- **Administrative Duration**: Time (in seconds) spent on account management pages.
- **Informational**: Number of pages visited related to website communication and information.
- **Informational Duration**: Time (in seconds) spent on informational pages.
- **Product Related**: Number of pages visited related to product-related content.
- **Product-Related Duration**: Time (in seconds) spent on product-related pages.
- **Bounce Rate**: Average bounce rate of the pages visited.
- **Exit Rate**: Average exit rate of the pages visited.
- **Page Value**: Average value of the pages visited.
- **Special Day**: Closeness of the visit time to a special day.

### Categorical Variables:
- **Operating System**: The visitor's operating system.
- **Browser**: The visitor's browser.
- **Region**: The geographic region from which the session originated.
- **Traffic Type**: The traffic source (e.g., banner, SMS, direct).
- **Visitor Type**: Whether the visitor is new, returning, or other.
- **Weekend**: Whether the visit occurred on a weekend.
- **Month**: The month of the visit.
- **Revenue**: Whether the visit resulted in a purchase.

---

## IV - Answer to Question 1: What is the relationship between features related to timing (weekend, month, and special day) and revenue generation?

The analysis of timing-related variables reveals that certain temporal factors significantly influence revenue generation:

- **Weekend**: The conversion rate on weekends is lower, with only 23.26% of visitors making a purchase. Implementing weekend promotions could boost conversions.
- **Month**: November stands out with the highest conversion rate, suggesting that targeted marketing campaigns during this month could help maintain and scale this performance.
- **Special Day**: Temporal variables (Month, Weekend, Special Day) significantly influence revenue, with a strong relationship between the month of visit and purchase likelihood (Chi2 = 384.935, p = 0.000).

---

## V - Answer to Question 2: Does the type of visitor (new, returning, or other) impact the decision to purchase?

The type of visitor (new, returning, or other) plays a crucial role in determining conversion rates:

- New visitors are often attracted by promotional offers, leading to higher revenue generation. However, returning visitors, although they generate high traffic, have a lower conversion rate.
- The **Chi-squared test** (135.252, p < 0.05) indicates a statistically significant relationship between visitor type and revenue generation, suggesting that marketing efforts should be focused on both attracting new visitors and re-engaging returning ones effectively.

---

## VI - Answer to Question 3: How do certain web metrics (Bounce Rates, Administrative Duration, Page Value, and Product-Related metrics) influence revenue generation?

Key web metrics play an important role in influencing revenue generation:

- **Bounce Rate**: Lower bounce rates are correlated with higher revenue generation, indicating that visitors who engage more with the site are more likely to make a purchase.
- **Page Value**: Visitors with higher page values tend to have higher conversion rates.
- **Product-Related Duration**: Time spent on product-related pages is positively correlated with purchases.
- **Administrative Duration**: Time spent on administrative pages does not appear to significantly affect conversions.

---

## VII - First Model: Logistic Regression

**Logistic Regression** was applied to predict whether a visitor makes a purchase. The results are as follows:
- **Accuracy**: 87%
- **Precision (False)**: 0.88
- **Precision (True)**: 0.73
- **Recall (False)**: 0.97
- **Recall (True)**: 0.34
- **AUC**: 0.89

This model showed high accuracy but struggled with predicting buyers (low recall for True).

---

## VIII - Second Model – Random Forest

The **Random Forest** model performed better in terms of overall accuracy and recall:
- **Accuracy**: 89%
- **Precision (False)**: 0.92
- **Precision (True)**: 0.71
- **Recall (False)**: 0.95
- **Recall (True)**: 0.56
- **AUC**: 0.91

This model performed better at identifying non-buyers but also had a higher recall for buyers.

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

The Random Forest model outperforms Logistic Regression in terms of overall performance, especially for non-buyers, but Logistic Regression is more interpretable for understanding key factors influencing purchases.

---

## X - Conclusion: How do factors influence behavior and purchase decisions on a website?

This study reveals that key factors like **timing**, **visitor type**, and **web metrics** significantly influence online purchasing decisions. To improve conversion rates, e-commerce businesses should focus on:
- Reducing **bounce rates** and improving **page value**.
- Targeting **new visitors** with personalized offers.
- Optimizing the user journey, particularly around high-conversion periods like weekends and specific months.

**Logistic Regression** provides transparency for marketing teams, while **Random Forest** is more suitable for precise predictions. Optimizing these factors can significantly improve revenue generation for e-commerce sites.

---

This markdown can be directly used in a GitHub repository as a detailed and clear project report.
