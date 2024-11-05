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
![flowchart drawio](https://github.com/user-attachments/assets/684cf709-61bb-4285-9f21-c7be83e1d697)


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

Snapshot of how it looks like:
![image](https://github.com/user-attachments/assets/4a2103fb-e19c-4b98-9f65-b164213eb335)

Risks involved in this project:
![image](https://github.com/user-attachments/assets/3fd537e2-7aed-45d2-be03-6a7b972ddd27)

# Summary
