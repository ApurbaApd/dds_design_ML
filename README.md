## ML/DL Model to accelerate the discovery and design of drugs of PLGA based Drug Delivery system
### Introduction:
A drug delivery system (DDS) is defined as a formulation or technology designed to carry medicines or therapeutic substances into the body in a careful and precise manner, enabling a therapeutic substance to selectively reach its site of action without affecting non-target cells, organs, or tissues. These systems may also include protective packaging, such as tiny shields called micelles or nanoparticles, which safeguard the medicine and facilitate its targeted delivery within the body. The primary goal of drug delivery systems is to enhance the efficacy, safety, and usability of medicines.

Now, a biopolymeric drug delivery system is a type of drug delivery system that utilizes biopolymers as the primary raw material to design and develop drug carriers or matrices for controlling the release of pharmaceutical agents or medication within the body. For instance, PLGA-based DDS, being biodegradable and biocompatible, is suitable for various medical and pharmaceutical applications. However, the complex interplay between multiple parameters, including the physicochemical properties of the drug and polymer, makes it very challenging to intuitively predict the performance of these systems.The application of ML in the pharmaceutical sciences is generally limited by a lack of available open-source datasets to train models.

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

![prediction_vs_real_fig](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/aaa41598-eb68-4981-a162-e3677f78d07e)


### Model Refinement:
Upon observing the absolute Spearman’s Rank correlation between the initial 17 input features, it became evident that many features were correlated. Therefore, during model training, only those features/descriptors with a correlation of less than 0.9 were considered. The selected features for model training include DP_Group, LA/GA, Polymer_MW, CL Ratio, Drug_Tm, Drug_Pka, Initial D/M ratio, SA-V, SE, Drug_Mw, Drug_LogP, Time, T=0.25, and Release, with Release being the output feature.

![feature_correlation](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/af1a7ad7-7115-4c89-8957-804c8dfd40de)


### Model Evaluation :
All models were evaluated, and their performance metrics were compared. It was found that Random Forest (RF) and Extreme Gradient Boosting (XGB) outperformed other models, with mean absolute error (MAE) values of 0.046 and 0.003, respectively. Furthermore, the actual and predicted release values were compared over time (days) of a particual DDS index.

![model_evaluation](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/bc322f3f-7efd-457c-bccb-f13976e21159)

![5FU_RF](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/8b8e31d2-0b11-466e-a377-98881b433543)

![xgb_FU83](https://github.com/ApurbaApd/dds_design_ML/assets/119648597/cc1ee6bf-8eb1-46d6-b0b9-085ef54fcad0)






 
