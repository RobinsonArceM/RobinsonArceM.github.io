---
layout: default
title: HERMES - Insect Meal Composition Prediction & Optimization
---

# HERMES: Predicting and Optimizing Insect Meal Composition

**(Optional: Insert a key visual here - e.g., a plot of predicted vs actual, or feature importance)**

## Summary

Developed HERMES, a machine learning system funded by ANID's Startup Ciencia program for Infood Protein. HERMES predicts the nutritional composition (protein %, fat %, efficiency index) of Black Soldier Fly larvae meal based on diet and environmental conditions using Gradient Boosting models (Python, Scikit-learn). Crucially, it also incorporates a reverse optimization engine to determine the optimal ingredient mix and conditions required to achieve specific target nutritional profiles, enabling data-driven production for sustainable animal feed.

## Problem & Goal

Infood Protein aims to produce high-quality, sustainable insect-based protein for animal feed. However, the final nutritional composition of the Black Soldier Fly larvae meal can vary significantly depending on the larvae's diet and rearing conditions. Predicting and controlling this composition is crucial for consistent product quality and efficient resource utilization.

The goal of the HERMES project, supported by Startup Ciencia, was twofold:
1.  Develop accurate machine learning models to **predict** the final meal composition (protein %, fat %, efficiency) based on known inputs.
2.  Create an optimization system to **determine the optimal diet composition and environmental parameters** needed to achieve desired target nutritional profiles.

## My Role

*(Suggested - adjust as needed)* As the lead Data Scientist on this project, I was responsible for the end-to-end development of the HERMES system, including data analysis, model training, validation, and the implementation of the prediction and optimization components within a functional application.

## Approach & Methodology

The HERMES system consists of several interconnected modules, trained on data from ~200 experimental diets:

**(Insert Schematic Image Here)**
* *Caption Suggestion:* System architecture of HERMES, showing the forward prediction, reverse optimization, and ingredient solver components.
    ```html
    <img src="./assets/image_f56822.png" alt="HERMES System Architecture" style="width:80%; height:auto; display: block; margin-left: auto; margin-right: auto;">
    <p style="text-align: center; font-style: italic;">System architecture of HERMES</p>
    ```

* **Data:** Utilized experimental data encompassing ~200 different diet formulations fed to Black Soldier Fly larvae.
    * **Input Features:** Included dietary nutritional components (protein, fat, ashes, other nutrients - *consider listing 1-2 key examples if possible*), and environmental variables (*e.g., temperature, humidity - specify if possible*).
    * **Target Variables:** Protein Percentage (%), Fat Percentage (%), and a calculated Efficiency Index.
* **Forward Model (Prediction):**
    * Implemented three parallel Gradient Boosting Regressor models (using Scikit-learn), one for each target variable (protein, fat, efficiency).
    * Standard preprocessing steps like feature scaling were applied.
* **Reverse Model (Composition Optimization):**
    * To find the optimal composition and environmental parameters for a *given target output*, the system runs the trained forward models ~5000 times with varying inputs.
    * The best results from these runs are then refined using optimization techniques (likely leveraging `scipy.optimize`) to pinpoint a valid set of input conditions.
* **Ingredients Model (Diet Solver):**
    * Takes the optimal composition identified by the Reverse Model.
    * Utilizes an optimization process (starting with ~1000 random ingredient combinations) to find the most cost-effective or practical ingredient mix that achieves the target composition.
* **HERMES 1.0 Application:**
    * The entire pipeline (forward models, reverse optimization, ingredient solver) was integrated into a functional application using Streamlit.
    * The application allows users to input desired target values (e.g., protein %) and efficiently returns the recommended optimal diet ingredients and environmental parameters within approximately one minute.

## Results & Impact

* **Predictive Accuracy:** The forward Gradient Boosting models achieved an **R-squared (R²) of 0.72** in predicting the target nutritional components.
    * *Context:* Predicting complex biological outcomes like larval metabolism is inherently challenging. This result is significant, especially considering research by other teams required substantially larger datasets (~3000 diets) to reach R² values around 0.80, indicating HERMES achieved strong predictive power relative to the data investment.
* **Optimization Success:** The reverse optimization and ingredient solver successfully identified viable diet compositions and environmental conditions to meet user-defined nutritional targets.
    * *(Optional: Add a brief textual example: "e.g., Targeting 55% protein resulted in recommendations for diet X and conditions Y...")*
* **Business Impact:** HERMES provided Infood Protein with a powerful tool for data-driven decision-making, enabling them to:
    * Target specific nutritional profiles for different product lines.
    * Optimize the use of feed ingredients, potentially reducing costs.
    * Improve the consistency and quality of their final insect meal product.

## Technologies Used

* **Core:** Python
* **Data Handling:** Pandas, Numpy
* **Machine Learning:** Scikit-learn (GradientBoostingRegressor)
* **Optimization:** SciPy (optimize)
* **Application:** Streamlit
* **(Optional: Add plotting libraries like Matplotlib, Seaborn if used for analysis/results)**

## Links & Availability

* **Company:** [Infood Protein](https://www.infoodprotein.com/) (Link to their website)
* **Application:** The HERMES Streamlit application is internal intellectual property and requires credentials for access.
* **Code:** The code repository is private due to proprietary data and algorithms.
