# Team-Genshin
#
# Teammates
Sushma Ganapuram, Rahul Kumar Jena, Satya sai ventata bharath Addagarla and Mounish Mani Kumar Mandalapu

# Sprint 1: Understanding the Problem

# Problem Statement:
To create a universal Proof of Reception (PoR) profile identification system, consolidating personal data under unique identities for secure and transparent control and monetization. PoR technology will ensure that data transactions are securely recorded and comply with privacy regulations. By integrating with MyTiki's hashed emails and payment profiles and using AI-based entity matches, the project aims to improve data integration and consistency. The ultimate goal is to establish a sustainable data framework that empowers users to reclaim their data rights and prevent unauthorized exploitation.

# Required Computer Systems
AWS Glue, AWS Athena and AWS Entity Resolution.

(Requirements are subject to change with change in Time.)

# Roadmap of the process
![Untitled](https://github.com/user-attachments/assets/fbb1aa41-173c-419c-84eb-3ea72ffd1512)


WorkFlow Doc: https://docs.google.com/document/d/1qJwszwjOjpykinJjil33mu1usrXiXjHrNz7AlTq5vAM/edit?usp=sharing

# Sprint 2: Understanding Datasets
Datasets provided for the time being would be:
1. User dataset         
Completeness– The data is complete with no Null values.
Consistency– all the columns are consistent within the dataset( has no duplicates)
Uniqueness– Dataset contains values that seem to be unique while, source column and loaded timestamp contain duplicates.
Conformity– Data conforms to expected types and formats.
Accuracy– Unable to verify without external reference data.

2. Demographic dataset              
Consistency–  It has multiple columns and most column seems to be formatted correctly, although there are categorical variables that are not formatted.
Uniqueness–   most of the attributes are not unique excluding user_id which is an identifier.
Conformity–  there are some conformity issues such as inconsistent lengths and data format issues.
Accuracy– Cannot be verified without external references.
Integrity– dataset is not completely consistent and complete, so it lacks integrity.
Completeness– It is incomplete as it has 8355 null values
- Columns like race_ethnicity and income_range have varied lengths, indicating that these might contain a mix of different formats or encodings.
- gender and user_state has varying lengths which suggest potential data quality issues

3. Transaction dataset    
Completeness- contains 4925756 missing values with merchant data (merchant_address, merchant_zip etc.) containing most missing values.         
Consistency–  it has a lot of missing values that needs to be dealt with, making it inconsistent.
Uniqueness–   some attributes are not unique excluding id,user_id and transaction_id that serve as identifiers.
Conformity–  there are some conformity issues such as inconsistent lengths, case sensitivity issues.
Accuracy– Cannot be verified without external references.
Integrity – dataset is not completely consistent and complete, so it lacks integrity.

4. Transaction dataset    
Completeness- contains 4925756 missing values with merchant data (merchant_address, merchant_zip etc.) containing most missing values.         
Consistency–  it has a lot of missing values that needs to be dealt with, making it inconsistent.
Uniqueness–   some attributes are not unique excluding id,user_id and transaction_id that serve as identifiers.
Conformity–  there are some conformity issues such as inconsistent lengths, case sensitivity issues.
Accuracy– Cannot be verified without external references.
Integrity – dataset is not completely consistent and complete, so it lacks integrity.

5. Receipts dataset  
Completeness- contains 312565 missing values with product_name and brand dominating the missing data.      
Consistency–   The Receipts dataset shows inconsistency in key columns like merchant_name, merchant_address, and various product categories, with high levels of missing data that affect reliability.
Uniqueness–   While receiptid is unique, user_id has a large number of duplicate values, indicating multiple receipts per user, which is expected but requires careful handling in analysis..
Conformity–  The presence of special characters in user_id suggests non-conformity in the identifier format, potentially complicating joins and data integrity checks.
Accuracy– High missing values in fields like channel, merchant_city, and size might compromise the accuracy of insights drawn from this dataset, especially when analyzing merchant-level data.
Integrity – The dataset maintains good row-level integrity with no completely duplicated rows, but logical consistency needs to be checked for related fields like amount and quantity values.


Algorithm Flow is shown below:
![image](https://github.com/user-attachments/assets/bca22dd5-2f2f-404a-a704-07f79d84bff5)


# Sprint 3: Algorithms used
Algorithms used:
1. Rule Based Matching in AWS Entity Matching Resolution
How it works: Datasets are to be uploaded to AWS Glue in the form of tables. Schema matching is then performed in AWS Entity Resolution using the 'User_ID' column. Following this, a workflow is created based on a rule-based algorithm, which is structured as a table to execute the matching process..
Inputs: Predefined/Continuous Datasets
Data Outputs: All columns which matches with User ID column from all datasets.
Hyperparameters: N/A
Model Tuning: N/A
Model Training Resources Required: AWS
Model Deployment: N/A

Snapshot of how it looks like:
![image](https://github.com/user-attachments/assets/9e4e0a28-9525-47ba-8bc4-01473a7b7f89)


3. ML Based Matching in AWS Entity Matching Resolution
How it works: Datasets are to be uploaded to AWS Glue in the form of tables. Schema matching is then performed in AWS Entity Resolution using the 'User_ID' column. Following this, a workflow is created based on a ML-based algorithm, which is structured as a table to execute the matching process..
Inputs: Predefined/Continuous Datasets
Data Outputs: All columns which matches with User ID column from all datasets.
Hyperparameters: N/A
Model Tuning: N/A
Model Training Resources Required: AWS
Model Deployment: N/A

4. Synthetic Data Generation:
   We have generated 50 unique rows for synthetic dataset. The goal is to use this data  to match the available datasets. Synthetic data replicates real-time data which has similar patterns to aggregate data.

   Snapshot of how it looks like after generated:
![image](https://github.com/user-attachments/assets/d32e475c-f755-41b9-a0b8-7f2106ef2148)

# Sprint 4: Visualizations / ML Model Training, Evaluation, & Verification

1. Matching User dataset and Synthetic Dataset
![Untitled-1](https://github.com/user-attachments/assets/fff64e28-31d2-44af-afa8-a8c13ae75428)


2. Challenges faced:
   Challenges and Potential Sources of Errors:

Data Quality Issues:
* Missing values in the dataset.
* Non-unique ID column or absence of any unique column.

Hashing Challenges:
* Selecting hashed data only if it uses hemsha246 algorithm.

Unexpected Errors:
* Errors encountered despite thorough preprocessing.

3. Result after matching User dataset with Synthetic data:
   Both the datasets successfully matched creating the "match_id" column which can be later used as a unique identifier to identify in the merged dataset.


Snapshot of merged user dataset and Synthetic dataset:

![Untitled-2](https://github.com/user-attachments/assets/396c2e76-8e6b-45c3-8614-b8cb9d58dea0)

4. Output  Generated by Entity Resolution after mapping User and Synthetic Data (Data converted to csv format)
   ![Untitled-3](https://github.com/user-attachments/assets/186f6935-e9a0-4c75-b957-e9239ba0b117)


Output modified to combine the matched rows and output as a single Row
#
![image](https://github.com/user-attachments/assets/50dad629-7fd7-453b-8fc0-8bb08efb1682)

5. We then proceed to combine User-Synthetic aggregate data with the Demographic dataset

Output from Entity Resolution after combining User-Synthetic aggregate data with the Demographic dataset
#

![image](https://github.com/user-attachments/assets/96b0b006-a932-43ed-b505-f06910ca0a41)

6. We then merged the remaining datasets and below is the snapshot showing that:
   ![image](https://github.com/user-attachments/assets/a1f4b0f7-250f-420a-b5e6-b736cabf651c)


Risks involved in this project:
![image](https://github.com/user-attachments/assets/3fd537e2-7aed-45d2-be03-6a7b972ddd27)

# Summary
This project focused on addressing the problem of fragmented personal data across multiple platforms and ensuring users can regain control over their data. To achieve this, we developed a system that consolidates data from various sources using AWS services. The architecture incorporated AWS S3 for data storage, AWS Glue for ETL (Extract, Transform, Load) operations, and AWS Entity Resolution for matching data between datasets. Athena was used to review and query the processed data. 

The project workflow involved retrieving and preparing data for matching, ensuring consistent formatting, and the presence of unique identifiers across datasets. Initial testing highlighted the importance of thorough pre-processing, particularly aligning column headers to avoid matching errors and ensuring that unique identifiers were included without being used as input fields for matching. Entity matching tests conducted through AWS Entity Resolution initially produced an unexpectedly high number of matches, which led to refining the matching logic to focus solely on cross-dataset matches and prevent self-matching. 

Key findings showed that while AWS Entity Resolution could effectively match data, ensuring data consistency and alignment was critical for successful implementation. The need for exact column header matches and the role of unique identifiers were reinforced as vital steps in the pre-processing stage. By implementing these improvements, the project could potentially establish a workflow capable of securely consolidating data and allowing for user-centric data management. 

Overall, this project provided a foundation for handling data fragmentation by linking disparate records into unified profiles, enhancing data transparency and user control.  

# Fucture Scope:
The system not only addresses the current challenge of data fragmentation but also lays the groundwork for future enhancements like advanced analytics, real-time data updates, and monetization opportunities.
