## ML/DL Model to accelerate the discovery and design of drugs of PLGA based Drug Delivery system
## Abstarct:
Drug Delivery Systems based on different biodegradable polymers have shown a very promising result. Designing such Drug Delivery Systems (DDS) is a very complex task as there are many physicochemical properties of the Polymers, Drugs, their compositions directly affect the release of the Drugs from the polymeric systems. Drug release from these systems is influenced by varied factors such as Time, Drug’s molecular weight, Polymer’s molecular weight, drug loading capacity etc. And it’s very costly and time consuming to design and develop such DDS if we go by traditional approach. Here, we introduce a computational approach to predict the Fractional Drug release from the PLGA- based DDS upon training Machine Learning models on historical data.
### Introduction:
The process of designing and developing a new drug is very time-consuming and expensive. Traditionally, the process involves a meticulous exploration of various factors that influence the release of drugs from the polymeric systems (DDS). These systems, which are frequently used in drug delivery systems, are designed to regulate the release of medicinal substances into the body over predetermined periods of time. Optimizing treatment efficacy requires an understanding of the various components' interactions within these systems and how they impact drug release kinetics. However, it requires extensive experimentation and iteration to identify the ideal composition and configuration of factors, especially for achieving optimal release within a short timeframe for specific diseases. This prolonged process contributes to the lengthy development timelines for drugs targeting various diseases, whether cancerous or non-cancerous. We must meticulously adjust these factors and observe the fractional drug release to find the ideal combination within a limited time frame.
To expedite new drug development utilizing PLGA-based Drug Delivery systems, we train different machine learning models and Neural Networks on historical data. By training various machine learning models, we can identify the combination of factors that yield optimal drug release for specific diseases. Subsequently, we validate these findings through experimental testing to determine the actual drug release rates. This approach accelerates the pace of new drug development, enabling quicker advancements in pharmaceutical research and potentially faster access to treatments for patients in need.

### Objective: 
The primary objective of this project is to leverage machine learning (ML) and deep learning (DL) techniques to expedite the discovery and design of drugs within poly(lactic-co-glycolic acid) (PLGA)-based drug delivery systems (DDS). ML/DL algorithms will be employed to predict experimental drug release from these advanced drug delivery systems. Subsequently, these trained models can be utilized to inform and guide the design of new PLGA-based drugs. The implementation of this data-driven approach has the potential to significantly reduce the time and cost associated with drug formulation development.

### Discussion:
It is widely known that drug-polymer compatibility significantly influences the performance of a formulation, including aspects such as drug loading capacity, drug release, and stability. The current study embarked on the investigation and refinement of machine learning (ML) models to accurately predict fractional drug release from PLGA based Drugs. To achieve this, a series of ML algorithms were trained and evaluated, including multiple linear regression (MLR), MLR with least absolute shrinkage and selection operator regularization (lasso), partial least squares (PLS), decision tree (DT), random forest (RF), extreme gradient boosting (XGB),AdaBoost,support vector regressor (SVR), k-nearest neighbors(k-NN), and NN. The RF/XGB models emerged as the top performer, demonstrating exceptional accuracy in predicting fractional drug release.

Here, the study aimed to predict the drug release of proteins and peptides from PLGA-based microparticles (MPs) utilizing a dataset comprising 68 PLGA formulations.In total, the dataset included 181 drug release profiles, encompassing 3783 individual fractional release measurements for 43 unique drug-polymer combinations.

17 molecular and physicochemical descriptors were initially chosen based on domain knowledge as input features to characterize the DDS formulations for various machine learning models. These input features encompassed the physicochemical properties of the drug, polymer, and DDS system, as well as factors accounting for the experimental conditions under which the in vitro release studies were conducted.It has also been shown that, for each drug release profile pertaining to a specific DDS, only the timepoint for drug release measurements (Time) varied, while all other input features remained constant.

These descriptors included the drug's molecular weight (Drug_MW), topical polar surface area (Drug_TSPA), number of heteroatoms (Drug_NHA), melting temperature (Drug_Tm), acid dissociation constant (Drug_pKa), and calculated partition coefficient (Drug_LogP). Additionally, descriptors related to the polymer were incorporated, such as polymer molecular weight (Polymer_MW), molar cross-linking ratio (CL_Ratio), and lactide-to-glycolide ratio (LA/GA). Other descriptors included the drug loading capacity of the LAI expressed as a fraction (DLC), the initial drug-to-polymer ratio used to prepare the LAIs (Initial D/M ratio), the surface area-to-volume ratio of the LAI (SA-V), the percentage of surfactant in the experimental release media (SE), as well as fractional drug release at 6h (T=0.25), 12h (T=0.5), and 24h (T=1.0).

![data_distribution](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/a7745e2c-a6bd-4834-992f-230560d2180e)


### Model Training:
These ML models underwent training and evaluation using a nested cross-validation strategy, comprising an inner loop for model training and hyperparameter tuning, and an outer loop for model evaluation. In the inner loop, 20% of drug-polymer groups were randomly allocated as a test set, while the remaining 80% were used for model development. Each model underwent hyperparameter optimization using group k-fold (k=10) cross-validation, with hyperparameters tuned using a random grid search. The model's performance was then evaluated on the test set within the outer loop. This nested cross-validation strategy was repeated ten times for each ML model to determine average performance. Model performance was assessed using mean absolute error (MAE), representing the average absolute difference between predicted and experimental fractional drug release values.

## Predicted vs Actual 

![model_comparison_plot](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/291cc4cc-8b8a-4104-89b8-5ca3051057e2)



### Model Refinement:
Upon observing the absolute Spearman’s Rank correlation between the initial 17 input features, it became evident that many features were correlated. Therefore, during model training, only those features/descriptors with a correlation of less than 0.9 were considered. The selected features for model training include DP_Group, LA/GA, Polymer_MW, CL Ratio, Drug_Tm, Drug_Pka, Initial D/M ratio, SA-V, SE, Drug_Mw, Drug_LogP, Time, T=0.25, and Release, with Release being the output feature.

![feature_correlation](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/af1a7ad7-7115-4c89-8957-804c8dfd40de)


### Model Evaluation :
All models were evaluated, and their performance metrics were compared.After Hyperparameter tuning It was found that Random Forest (RF) and Extreme Gradient Boosting (XGB) outperformed other models, with mean absolute error (MAE) values of 0.099 and 0.090, respectively. Furthermore, the actual and predicted release values were compared over time (days) of a particual DDS index.

### Model prediction

XGBoost Model's Prediction:

## For 5-FU-PLGA DDS

![xgb_5fu](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/32e09887-a3a5-4485-b5ab-544914108d3a)

## For DEX-PLGA

![xgb_dex](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/001abd4f-d6cb-4803-b7fe-2f5b868bed1a)








 
