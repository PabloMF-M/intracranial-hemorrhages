# Intracranial hemorrhages


**Author 1:** Pablo Menéndez Fernández-Miranda MD, PhD, MSc  [✉️](mailto:pablomenendezfernandezmiranda@gmail.com)

**Author 2:** Marta Álvarez de Linera Alperi MD, PhD.

-------------------


PROJECT INFORMATION
-------------------

***WARNING*** - GitHub does not render all HTML content. To properly view all content, please copy and paste the notebook links [here](https://nbviewer.org).


	THIS PROJECT IS STILL ONGOING!!!!


1 - ABSTRACT
-------------

The aim of this project is to find new prognostic factors of ICH and develop a risk stratification tool, with the premise of being easy-to-implement and use. For that purpose data from more than 160 variables belonging to 300 patients were collected. The results showed that glucose levels, prothrombin activity, hours from the clinical onset, Glasgow Coma Scale, and the comorbidity associated, were prognosis factors for survival. The models with highest performance (c-index) were those based on Cox regression, with up to 0.84 95% CI (0.75,0.90). There, a Cox model based on five clinical variables is proposed as a potential tool to aid in decision making for patients with ICH, although further clinical validation studies is required.


2 - PROJECT WORKFLOW SUMMARY
---------------------------

2.1. (Anonymization, Cleaning and Curation)
-------------------------------------------

Below are the successive databases that have been generated during the anonymization and cleaning process, up to the final database used for the project. In parentheses are the notebooks that were used to carry out the transformations.



	ICH_database_complete.xlsx (not available in this repository due to privacy issues) -->
 	
	--(...)--> ICH_database_pseudoanonymized_nonredudant.csv (not available) ------------->

	--(1. Anonymization 2 (R))--------------> ICH_database_anonymized.csv ---------------->

	--(2. Cleaning & Curation (R))----------> ICH_database.csv / ICH_database.rds & 
	                                          ICH_database_metadata.csv ------------------->

	--(3. Save the dataset in Python-HDF5)--> ICH_database.hdf5 --------------------------->

	--> ...


	2.2 (Data Loading, Statistical Analysis and Machine Learning Modeling)
	----------------------------------------------------------------------
	
	Data Loading

	--(A. Loading the dataset in python)-----------------------> Options to load the dataset in R.
	--(B. Loading the dataset in R)----------------------------> Options to load the dataset in python.

	
	Statistical Analysis

	--(4.1 EDA & Descriptive Statistics of Outcomes)-----------> EDA & Descriptive Statistics of outcomes.
	--(4.2 EDA & Descriptive Statistics of Predictors)---------> EDA & Descriptive Statistics of predictors.
	--(4.3 EDA & Descriptive Statistics of Dates (R))----------> EDA & Descriptive Statistics of dates.
	--(5.1 Inferential Statistics - Hypothesis Contrasts (R))--> Hypothesis contrasts.
	--(5.2 Inferential Statistics - Survival Analysis)---------> Survival analysis.

	
	Machine Learning Modeling

	--(6. Dimensionality reduction - PCAs & FA)----------------> PCAs & FA.
	--(7. Kernel Methods - SVM & SSVM)-------------------------> SVM & SSVM.
	--(8. RSF, GB model and AFT models)------------------------> Random Survival Forest, Gradient Boosted & Accelerated Failure Time models.



3 - MATERIALS AND METHODS
------------------------

3.1. Available Databases
-------------------------

*Unavailable databases are not described here, they are described in Databases/readme_databases.txt*

3.1.1. Datasets
----------------

* **<code>ICH_database_anonymized.csv</code>**: data collected from **300 patients** with Intracranial Hemorrhages (ICH) was fully anonymized by removing patient identifiers and relevant dates (e.g., birth or death dates).

* **<code>ICH_database.csv</code>**: <code>ICH_database_anonymized.csv</code> cleaned after the following steps:
	* Assignation of variable datatypes.
	* Correction of incorrect data values.
	* Rename variables with variable labels.
	* Removal of variables that only had a different value.
	* Removal of variables with redundant information.
	* Removal of dates which only contain the value "anonymized".

* **<code>ICH_database.rds</code>**: <code>ICH_database.csv</code> saved as R object in <code>.rds</code> (RDS) to preserve variable datatypes.

* **<code>ICH_database.hdf5</code>**: <code>ICH_database.csv</code> saved as <code>.hdf5</code> file (HDF5) to preserve variable datatypes.
		

3.1.2. Metadata
----------------
* **<code>ICH_database_anonymized_metadata.csv</code>**: file with information about the variables in <code>ICH_database_anonymized.csv</code>:
	* <code>Variable_Name:</code> name of the variable (spanish).
	* <code>Variable_R_Name:</code> name of the variable given by R.
	* <code>Variable_Label:</code> recommended name of the variable for further database analysis.
	* <code>Variable_Definition:</code> definition of the variable.
	* <code>R_Datatype:</code> recommended R datatype for the variable.
	* <code>Python_Datatype:</code> recommended Python datatype for the variable.
	* <code>Pandas_Datatype:</code> recommended Pandas datatype for the variable.
	* <code>Values:</code> values that the variable can have.
	* <code>Maximum_Number_of_Different_Values_in_the_Dataset:</code> maximum number of possible different values in the dataset.
	* <code>Comment:</code> comments about the variable.
	* <code>Type_of_Variable:</code> if variable is *a priori* an **outcome** (***dependent***) or a **predictor** (***independent***), or if the variable just contains additional information about the dataset (***auxiliary***).

* **<code>ICH_database_anonymized_metadata.xls</code>**: same as <code>ICH_database_anonymized_metadata.csv</code> but in <code>.xls</code>.

* **<code>ICH_database_metadata.csv</code>**: file with information about the variables in <code>ICH_database.csv</code>:
	* <code>Variable_Name</code>: name of the variable (spanish).
	* <code>Variable_Label</code>: name of the variable in the database.
	* <code>Variable_Definition</code>: definition of the variable.
	* <code>R_Datatype</code>: R datatype.
	* <code>Python_Datatype</code>: Python datatype.
	* <code>Pandas_Datatype</code>: Pandas datatype.
	* <code>Values</code>: values that the variable can have.
	* <code>Maximum_Number_of_Different_Values_in_the_Dataset</code>: maximum number of possible different values in the dataset.
	* <code>Comment</code>: comments about the variable.
	* <code>Type_of_Variable</code>: if variable is *a priori* an **outcome** (***dependent***) or a **predictor** (***independent***), or if the variable just contains additional information about the dataset (***auxiliary***).


3.2. Notebooks
---------------

* **A. Loading the dataset in python**: describes the best options to load the dataset in python.

* **B. Loading the dataset in R**: describes the best options to load the dataset in R.

* **1. Anonymization 2 (R):** loads <code>ICH_database_nonredudant_pseudoanonymized.csv</code> and generates <code>ICH_database_anonymized.csv</code>. In a first step, all patient identifiers (IDs,...) were removed. This notebook now performs a second anonymization step, which consists of anonymizing dates. This type of data may contain information that could help identify patients, so it is safer to anonymize all variables containing dates. However, to avoid the loss of information, three new variables will be generated and added to the database: <code>Time between head CT scan and blood analysis (days)</code>, <code>Age at hospital admission (years)</code>, and <code>Survival days after admission (days)</code>. This notebook will carry out this second anonymization step, including the following sub-steps.
		1. Load data.
		2. Change the dates into <code>Date types.</code>
		3. Generate the new variables.
		4. Anonymize the dates and save the anonymized database.

* **2. Cleaning & Curation (R):** load <code>ICH_database_anonymized.csv</code> & <code>ICH_database_anonymized_metadata.csv</code> and generate <code>ICH_database.csv</code> & <code>ICH_database_metadata.csv</code> after the following steps.
		
		1. Load the database.
		2. Check variables: datatypes and values.
		3. Change datatypes when appropriate.
		4. Change values when appropriate.
		5. Delete non-useful variables.
		6. Change column names and re-adapt metadata_database.
		8. Save the cured database and the metadata database.


* **3. Save the dataset in Python-HDF5:** save the dataset in a HDF5 file to easier further usage in Python. This notebook includes the following steps:

		1. Load dataset metadata and extract an array with categorical columns index.
		2. Load the dataset: all variables with <code>NaN</code> will be <code>float64</code> and all variables without <code>NaN</code> <code>int64.</code>
		3. Change to categories when appropriate.
		4. Check datatypes and save in a hdf5 file.


* **4.1 EDA & Descriptive Statistics of Outcomes:** exploring data analysis and descriptive statistics of the * a priori* outcome variables contained in <code>ICH_cured.csv</code>. This notebook contains the following steps.

		1. Define some useful functions for further analysis.
		2. Load data and metadata.
		3. Check the pandas datatype and the *a priori* variable type of the dataset variables.
		4. Exploring and making a statistical description of the *a priori* outcome variables.


* **4.2 EDA & Descriptive Statistics of Predictors:** exploring data analysis and descriptive statistics of the *a priori* predictor variables contained in <code>ICH_cured.csv</code>. This notebook contains the following steps.

		1. Load data and metadata.
		2. Check the pandas datatype and the a priori variable type of the dataset variables.
		3. Exploring and making a statistical description of the *a priori* predictor variables.


* **4.3 EDA & Descriptive Statistics of Dates (R):** this notebook analyzes the relevant dates, which have been removed in the databases shared in this repository for anonymization purposes.

		1. Load data.
		2. Change dates into <code>Date types.</code>
		3. Descriptive statistics.


* **5.1 Inferential Statistics - Hypothesis Contrasts (R):** this notebook is designed to do an statistical analysis following the standards of biostatistics for multiple variables (***False Discovery Rate- FDR** *correction of p-values* was included):

		1. Load dataset and metadata.
		2. Assumption of normality.
		3. Correlation analysis.
		4. Statistical tests: hypothesis contrasts.


* **5.2 Inferential Statistics - Survival Analysis:** this notebook performs a survival analysis of patients who have suffered an intracranial hemorrhage. Survival is defined as survival to hospitalization discharge. Different biostatiscal techniques are used for that purpose, including the well-known ***Kaplain-Meier estimator***, ***Mantel-Cox (log-rank) test***, and the **state-of-the-art** method for survival prediction until the last *adaptations of Machine Learning algorithms for survival analysis*, ***Cox Proportional Hazards regression***.

		1. Load dataset.
		2. Define survival variables.
		3. Survival functions.
		4. Cox Proportional Hazards regression.


* **6. Dimensionality reduction - PCAs & FA:** this notebook explores some dimensionality reduction techniques, including ***Principal Component Analysis (PCA)*** and ***Factorial Analysis (FA)***. PCA is more appropriate for quantitative data, nevertheless, FA allows to analyze a dataset with numerical and categorical variables at the same time.

		1. Load dataset.
		2. Principal Component Analysis (PCAs).
		3. Factorial Analysis (FA).


* **7. Kernel Methods - SVM & SSVM:** kernel methods are a type of Machine Learning algorithms used to map input data into a different multidimensional space in which data classes can be easily sepparated. Therefore, these methods are widely used to solve classifcation and regression problems. A very well-knowned algorithm of this group is ***Support Vector Machine (SVM)***, which has been adapted for solving survival prediction in the named ***Survival Support Vector Machine (SSVM)***.

		1. Load dataset.
		2. Support Vector Machine (SVM).
		3. Survival Support Vector Machine (SSVM).


* **8. RSF, GB model and AFT models:** This notebook explores models based on ***Random Survival Forest*** and ***Gradient Boosted techniques***, including a parametric approach for survival function estimation, the well-known ***Accelerated Failure Time*** approach.

		1. Load dataset.
		2. Random Survival Forests.
		3. Gradient Boosted Model.
		4. Accelerated Failure Time Model.

-------------------------------------------------------------------------------------------------------------------
