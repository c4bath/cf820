CIND820 D1H - Big Data Analytics Project - Module 3


File submitted for Module 3 at https://github.com/c4bath/cf820

Filename: cforbathMod3.ipynb


Dataset:

The csv file is in my google drive and shared with anyone with the link :

https://drive.google.com/file/d/1zAxKDi6sWfjmYPXJosD1KwftiRCvb4tG/view?usp=share_link

The file is also available at:
https://www.kaggle.com/datasets/sadiaanzum/patient-survival-prediction-dataset

Per Kaggle: source of the dataset: https://journals.lww.com/ccmjournal/Citation/2019/01001/33__THE_GLOBAL_OPEN_SOURCE_SEVERITY_OF_ILLNESS.36.aspx



Project Status:

The following have been completed:

Data preprocessing including:

* High level data description
* Dropping columns as per module 2 that do not provide any: 
1. information value (i.e. 'encounter_id', 'patient_id', 'hospital_id'*)  Change from module 2 – hospital_id is no longer included
2. the predicted probabilities from the APACHE IV model ('apache_4a_hospital_death_prob','apache_4a_icu_death_prob')
3.  OR are not of interest in our prediction and analysis (the physiological measures, i.e. 'bilirubin_apache','bun_apache','creatinine_apache', etc) – these account for the overwhelming majority of the dropped features

Dropped rows with 2 or more missing values
Dropped feature that had the same value (' gcs_unable_apache’:  0) for all observations
Imputed remaining missing values (mean for numerical, mode for categorical)

Exploratory Data Analysis:
* Univariate, Bivariate, Multivariate
* Class imbalance (high: minority class ‘did not die’ ~8% of total observations)
* Correlations (heatmap and sorted) for numerical features
* Dropped highly correlated features (2)
* Chi-square analysis of categorical features

Preparation for feature selection and modeling:
* One-hot encoded categorical features (including ordinal GCS features) 
* Split dataset into independent and dependent variable data frames
* Scaled numeric features 

Feature Selection:
* Recursive Feature Elimination with Cross Validation using Random Forest estimator
	Features reduced from 71 to 55

Model Selection:
* Evaluated the following classifiers on the imbalanced dataset
1. Logistic Regression
2. XGB Classifier 
3. Random Forest
4. Gaussian Naïve Bayes

* Gaussian NB performed the best overall

Modelling with balanced dataset:
* Ran Gaussian NB while applying Synthetic Minority Oversampling Technique (SMOTE) to address class imbalance and evaluated and compared performance
