# Gap-Python-2025

* NOTE: At the end of class, I mentioned that <a href="https://github.com/davewadestein/Gap-Python-2025/blob/main/Demo/Demo_Titanic_Logistic_Regression.ipynb">Titanic Logistic Regression</a> was a different version of the Titanic Survivors notebook we looked at in class and mentioned it was supposed to include equivalent PySpark commands for a number of the Pandas cells. I have fixed that notebook, i.e., I have restored the missing PySpark commands.

## Course Evaluation
* https://www.surveymonkey.com/r/X3HRHD3
  
## Thursday 1-Question Polls
<img width="140" alt="Screenshot 2025-01-21 at 12 31 17 PM" src="https://github.com/user-attachments/assets/4de07868-6657-409a-8124-517ca160d644" />
<img width="240" alt="Screenshot 2025-01-21 at 12 32 27 PM" src="https://github.com/user-attachments/assets/6f14e782-e549-4a9d-98f0-faa43ad54229" />

## Wednesday 1-Question Polls
<img width="130" alt="Screenshot..." src="https://github.com/user-attachments/assets/548c1b6e-40cc-4e7f-9f04-b891d3721d5a" />
<img width="240" alt="Screenshot..." src="https://github.com/user-attachments/assets/3f71141f-dec0-4872-9bec-68b83955e0a1" />

## Tuesday 1-Question Polls
<img width="220" alt="Screenshot 2025-01-15 at 8 47 20 AM" src="https://github.com/user-attachments/assets/ee1b2acf-76f0-4438-8b04-e97777e0a43f" />
<img width="130" alt="Screenshot 2025-01-15 at 8 47 57 AM" src="https://github.com/user-attachments/assets/2b4dd525-9c20-43e7-91c0-2b91341019eb" />

## How to reach me during (or after) class
* dave@developintelligence.com

## What we'll use to do our work
* https://colab.research.google.com/
  
## Schedule (tentative)
* 8-9:30 Pacific: CLASS
* 9:30-10 Pacific: LUNCH BREAK 1 (for Central/Eastern time zones)
* 10-11:30 Pacific: CLASS
* 11:30-Noon Pacific: LUNCH BREAK 2 (for Pacific/Mountain time zones)
* Noon-1:45 Pacific: CLASS
* 1:50-2:05 Pacific: BREAK
* 2:05-4:00 Pacific: CLASS

## Goals
* develop a SOLID foundation in Python
   * ...so that you can write code / read code / understand code
* leverage AI
   * ...so that you can write code / read code / understand code
   * also to find bugs in code
   * (note that you will need that solid foundation to know...
      * what AI is telling you
      * when AI is wrong)
* understand best practices in Python
* understand error messages
* testing / debugging
* data manipulation / visualization
* Pandas / PySpark

## Challenges
* differing backgrounds
  * data science
  * engineering
  * product manager
* lots of material
* using a web-based tool

## Capstone Sketch (for Data Science folks)
* Data Loading & Exploration
  * Load data from tables and get familiar with it
  * Can start with basic SQL but shift to pyspark/functions
  * Some visualization (built in databricks notebooks is most typical but not python)
  * Some summary statistics

* Data Cleaning and Feature Extraction
  * Identify and perform cleaning on the data and extract relevant features
  * While development in a notebook is fine, the end goal of this step is to write modular functions that perform these cleaning steps
  * Think about modularizing by brand, market, channel, date ranges, and other relevant slices of the data
  * Any functions/classes should ultimately be defined in a python script and imported into a notebook/script for use
* Option 1: Data Analysis/Visualization
  * Perform some analysis and/or visualization of the data in a reusable/extendable format
  * Again, analysis and visualizations can be developed in notebook cells but should eventually be parametrized to be more reusable
  * For example an analysis method could take in a dataframe, a date range, a target variable to plot/analyze
* Option 2: Modeling
  * Train a model on the data (train test split), perform basic hyperparameter tuning or model comparison with MLFlow and register the model (Unity Catalog)
  * Create a Databricks workflow for (re)training the model and a workflow for inference (optionally add a schedule to the workflows)

## Capstone Ideas
* Here are some ideas for overall analysis/modeling 
goals. Some of the suggested parameterization can be added in at later steps when it becomes relevant (e.g. maybe start with a data extraction method that only takes brand, market, and a date range then later add in channel param, division as needed).

* Top-Selling Products (Analysis and Visualization)

  * Objective: Identify the top-selling products in a dataset.
  * Steps:
    1. Find datasets for sales.
    2. Explore the data, identify cleaning steps, and feature extraction.
    3. Write methods for data cleaning and feature extraction (param by brand, date range, channel(s)).
    4. Write method(s) to get the top N selling products in the data along with their sales (param by N, date range, channel(s), brand).
    5. Write a method to visualize the results. (Bonus: find the image data from the catalog and display product images as well)
    6. Parametrize a notebook (using dbutils.widgets) to perform the end-to-end analysis (load, clean, aggregate, and visualize) and create a workflow from this notebook.
    7. Run this notebook for multiple brands.
    8. What if we consider online purchases only? Retail only?
    9. Repeat this analysis for different time windows (top selling summer products, top selling holiday products, etc).
    10. What if we also include browsing data? What are the top viewed products? Top added to cart products? Are these different from top purchases?
    11. Bonus: What if we adjust for returns?
    12. Bonus: What if we wanted the top products for each division?

* Customer Segmentation (Clustering)
  * Objective: Group customers based on purchasing behavior.
  * Steps:
    1. Find datasets with customer purchase behavior (start with a single brand)
    2. Explore datasets, identify cleaning steps and feature extraction.
    3. Write modular methods to perform cleaning and data preparation in a python script (standardize the data!)
    4. Apply clustering (e.g K-means) to create 3–5 customer segments. (modularize by number of clusters!)
    5. Visualize clusters in 2D using PCA for dimensionality reduction (bonus: try 3D for fun).
    6. Analyze the clusters, what features are dominant? How would we describe the groups?
    7. Repeat the above steps split by retail and online purchases.
    8. Incorporate customer demographic data and repeat.
    9. What if we include data from multiple brands? Are there clusters for multi-brand customers? Clusters by brand?

* Customer Churn Prediction (Classification)
  * Objective: Predict if a customer is likely to stop shopping (in the upcoming week/month/quarter) based on historical data.
  * Steps:
     1. Identify tables needed to measure churn and other useful customer features.
     2. Split the data into training and test sets (by date)
     3. Explore datasets, identify cleaning steps, and feature extraction.
     4. Write modular methods to perform cleaning and data preparation (py script)
     5. Train a logistic regression or random forest classifier.
     6. Evaluate with accuracy, precision, and recall.
     7. Bonus: Perform hyperparameter tuning and compare models with MLFlow experiments.
     8. Examine feature importance.
     9. Register model with Databricks Unity Catalog
     10. Create a model inference notebook using the registered model.
