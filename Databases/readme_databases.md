# DATABASES INFO

1 - WORKFLOW
------------

	ICH_database_complete.xlsx ---->
	 ----> ICH_database_complete_pseudoanonymized.xlsx / ICH_database_complete_pseudoanonymized.csv ---->
	 ----> ICH_database_pseudoanonymized_nonredudant.csv ---->
	 ----> ICH_database_anonymized.csv ---->
	 ----> ICH_database.csv / ICH_database.rds/ICH_database.hdf5.

	

	ICH_database_anonymized_metadata.xls / ICH_database_anonymized_metadata.csv ---->
	 ----> ICH_database_metadata.csv



2 - DATABASES
--------------

* **<code>ICH_database_complete.xlsx</code>**: complete database.

* **<code>ICH_database_complete_pseudoanonymized.xlsx</code>**: database without patients identifiers (NHC, ID, Hospital...) in <code>.xlsx.</code>

* **<code>ICH_database_complete_pseudoanonymized.csv</code>**: database without patients identifiers (NHC, ID, Hospital...) in <code>.csv.</code>

* **<code>ICH_database_nonredudant_pseudoanonymized.csv</code>**: <code>ICH_database_complete_pseudoanonymized.csv</code> without some redundant or non-useful atributes.

* **<code>ICH_database_anonymized.csv</code>**: <code>ICH_database_nonredudant_pseudoanonymized.csv</code> fully anonymized by the:
	* Anonymization of: <code>Fecha de ingreso</code>, <code>Fecha de alta</code>, <code>Fecha de TC</code>, <code>Fecha análisis de sangre</code>, <code>Fecha nacimiento</code>, <code>Fecha mortalidad.</code>
	* Addition of: <code>Time between blood analysis and head CT scan</code>, <code>Age at the hospital admission date</code>, <code>Survival days after admission</code>.

* **<code>ICH_database.csv</code>**: <code>ICH_database_anonymized.csv</code> cleaned (assignation of variable datatypes, correction of incorrect data values, rename variables with the variable labels, and removal of variables that only had a different value or with redundant information and dates which only contain the value "anonymized").

* **<code>ICH_database.rds</code>**: <code>ICH_database.csv</code> saved as R object in <code>.rds</code> to preserve variable datatypes.

* **<code>ICH_database.hdf5</code>**: <code>ICH_database.csv</code> saved as hdf5 file to preserve variable datatypes.

* **<code>ICH_database_anonymized_metadata.csv</code>**: file with information about the variables of <code>ICH_database_nonredudant_pseudoanonymized.csv</code> and <code>ICH_database_anonymized.csv</code>. This file contains the following variables:
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

* **<code>ICH_database_anonymized_metadata.xls</code>**: same as <code>ICH_database_anonymized_metadata.csv</code> but in <code>.xls.</code>

* **<code>ICH_database_metadata.csv</code>**: file with information about the variables of <code>ICH_database.csv</code>. This file contains the following variables:
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


2 - MAIN DATABASE CONTENT (<code>ICH_database</code>)
-------------------------------------------------------

The cleanest version of the ***ICH database*** is <code>ICH_database</code>, which is available in three formats (<code>.csv</code>, <code>.rds</code>, <code>.hdf5</code>). This database is accompanied by another file (<code>ICH_database_metadata</code>) containing all relevant metadata, including the definitions of all variables. These variables, grouped by category, are as follows.



	IDENTIFIERS
		· patient

	DEMOGRAPHICS
		· sex
		· age
		· hospital

	OUTCOMES
		· follow_up
		· final_outcome
		· survival_discharge
		· survival_3d
		· survival_6d
		· survival_9d
		· survival_12d
		· survival_15d
		· survival_1m
		· survival_3m
		· survival_1y
		· survival_5y
		· survive
		· survival_days

		· neurosurg (detailed also below in treatment of the ICH)
		· interprocedures (detailed also below in treatment of the ICH)

	OUTCOMES/PREDICTORS
		· hospitalizations_1y
		· hospitalizations_3y
		· hospitalizations_5y
		· hospitalization_icu_days
		· hospitalization_days


	PAST MEDICAL HISTORY

		FAMILY DISEASES
		· nfamily_medhist

		DRUG USE
		· tobacco
		· n_tobacco
		· drugs
		· alcohol
		· g_alcohol

		PAST MEDICAL HISTORY
		· ht
		· dmellitus
		· dyslipidemia
		· previous_ich
		· cv_diseases
		· carrhythmias
		· structural_heart_disease
		· vascular_diseases
		· neurological_diseases
		· dementia
		· depression
		· psychiatric_diseases
		· cancerous_autoimmune_diseases
		· cancerous_diseases
		· autoimmune_diseases
		· hyper_hypo_thyroidism
		· haematological_disorders
		· other_diseases
		
		REGULAR MEDICATIONS
		· antihypertensives
		· antidiabetics
		· hypolipidemics
		· anticoagulants
		· antiplatelets
		· chemotherapeutics
		· digoxin
		· n_other_medications
		· aceis
		· arbs
		· ccbs
		· bblockers
		· ablockers
		· ablockers1
		· ablockers2
		· diuretics
		· other_antihypertensives
		· biguanides
		· sulfonylureas
		· glinides
		· glp1a
		· dpp4i
		· agi
		· insulin
		· statins
		· aspirin
		· p2y12b
		· gIIbIIIai
		· cumarinics
		· noac
		· dabigatran
		· rivaroxaban
		· other_medications


	SYMPTOMS / ANAMNESIS AT THE EMERGENCY DEPARTMENT
		· onset_h
		· headache
		· emesis
		· visual_disturbances
		· seizures
		· mh_trauma
		· mh_le_trauma
		· mh_he_trauma
		· other_symptoms


	PHYSICAL EXAMINATION AT THE EMERGENCY DEPARTMENT
		· sbp
		· dbp
		· spo2
		· temperature
		· bpm
		· rr
		· neurol_signs
		· diplopia
		· anisocoria
		· aphasia
		· dysarthria
		· altered_consciousness
		· nuchal_rigidity
		· rfacial_palsy
		· lfacial_palsy
		· ruplimb_mimpairment
		· luplimb_mimpairment
		· rlwlimb_mimpairment
		· llwlimb_mimpairment
		· balance_impairment
		· tgcs


	ICH CAUSES
		· primary_ich
		· vascular_ich
		· traumatic_ich
		· ht_ich
		· amyloidangiopathy_ich
		· aneurysmal_ich
		· avm_ich
		· hti_ich
		· other_ich


	TREATMENT OF THE ICH
		· neurosurg
		· interprocedures


	BLOOD ANALYSIS
		BLOOD ANALYSIS AT THE EMERGENCY DEPARTMENT
		· glucose
		· urea
		· creatinine
		· sodium
		· potasium
		· egfr
		· prothrombin_activity
		· leukocytes
		· erythrocytes
		· hemoglobin
		· hematocrit
		· platelets
		· mcv
		· rdw
		· mchc
		· mpv
		· mch
		· inr
		· fibrinogen
		
		OTHER BLOOD ANALYSIS VARIABLES
		· maxfibrinogen
		· time_between_CT_bloodanalysis



------------------------------------------------------------------
