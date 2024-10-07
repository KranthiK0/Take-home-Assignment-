# Take-home-Assignment-


Project Overview:
This project is designed to match clinical trials from clinicaltrials.gov with patient data based on age inclusion criteria and exclusion criteria related to their medical conditions and medications (interventions). The key objective is to filter out eligible patients for trials and save the result in both JSON and Excel formats.

The project consists of several stages:

Data Collection & Preprocessing: Collect clinical trial data (manually scraped) and patient data (from CSV files).

Data Integration: Merge patient information with their conditions and trials information.

Eligibility Criteria: Apply inclusion criteria based on age and exclusion criteria based on conditions and interventions.

Output Generation: Output eligible patients for trials in JSON format and Excel.

Testing: Unit and integration tests to verify correctness of the algorithms.


Files in the Project:

patients.csv: Contains patient demographic information.

Columns:
Id: Patient unique identifier.
BIRTHDATE: Patient birthdate to calculate age.
Other demographic columns (not relevant to matching).
conditions.csv: Contains medical conditions diagnosed for each patient.
Columns:
PATIENT: Patient ID to match with patients.csv.
DESCRIPTION: Medical condition (diagnosis) associated with the patient.


ctg-studies.csv: Manually scraped file containing clinical trials actively recruiting patients.

Columns:
NCT Number: Unique trial identifier.
Study Title: The title of the clinical trial.
Age: Age eligibility category (e.g., Adult, Child, Older Adult).
Conditions: Conditions associated with the trial.
Interventions: Medical interventions associated with the trial.

Python Scripts:

main.py: Contains the main logic for the matching algorithm, age and exclusion criteria, and data loading functions.
testing.py: Contains the unit tests and integration tests for validating age eligibility, exclusion criteria, and the final output structure.
generate_output.py: Contains logic to generate Excel and JSON files based on filtered eligible patients.

IPYNB file is attached 


Output Files:
eligible_patients_for_trials.xlsx: Excel file that contains patient IDs and the trials they are eligible for.
eligible_patients_trials.json: JSON file with eligible patients and the trials they qualify for.

Project Workflow:

Data Loading & Preprocessing:

Load patients.csv and conditions.csv, then merge them using Id and PATIENT columns.
Load ctg-studies.csv and preprocess trial conditions, interventions, and age eligibility.
Inclusion Criteria (Age):
Patients are first filtered based on age. The age is calculated from the birthdate in patients.csv and compared to the age eligibility of the trials.

Age categories:
Child: Age < 18.
Adult: 18 <= Age < 65.
Older Adult: Age >= 65.

Exclusion Criteria:

After filtering based on age, patients are further filtered based on exclusion criteria.
Exclusion occurs if:
A patient's condition matches any of the exclusion conditions in the trial.
A patient's condition matches any of the interventions associated with the trial.

Results Generation:
Eligible patients and their corresponding trials are saved to a JSON file.
Additionally, an Excel file is generated showing eligible patients and the trials for which they qualify.

Unit Testing:
Unit tests are written to test individual functions, such as age eligibility and exclusion checks.
Integration tests validate the entire workflow of loading data, processing eligibility, and generating outputs.

Modify Data for Testing:

If you want to test the script with your own data, replace the contents of the following CSV files:
patients.csv: Replace with new patient demographic data.
conditions.csv: Replace with new patient conditions.
ctg-studies.csv: Replace with new clinical trial data.

The JSON output is structured as follows:

json

[
  {
    "patientId": "string",
    "eligibleTrials": [
      {
        "trialId": "string",
        "trialName": "string",
        "eligibilityCriteriaMet": ["Age eligibility", "No exclusion condition"]
      }
    ]
  }
]
Each patient is grouped by patientId, and for each patient, a list of eligible trials is provided, with the eligibility criteria met (e.g., "Age eligibility", "No exclusion condition").


Customization:

Testing Different Data: To test the matching logic with your own dataset:
Replace the CSV files (patients.csv, conditions.csv, ctg-studies.csv) with your data.
Re-run the IPYNB script to generate new results based on the new data.

Adjusting Criteria:
The eligibility criteria logic can be modified in main.py:
Age criteria: Modify the check_age_eligibility function to adjust the age ranges.
Exclusion criteria: Modify the check_exclusion_criteria function to adjust how conditions and interventions are compared.


Conclusion:
This project provides a framework for matching patients to clinical trials based on their age and medical history, with the final output being both in Excel and JSON formats. It is designed for flexibility, allowing easy modifications to data and criteria for different use cases. Unit and integration tests help ensure the accuracy and robustness of the process.






