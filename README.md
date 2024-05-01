# NYC_alg_compliance
Data cleaning and analysis of NYC's Algorithmic tool compliance reporting. 

In 2022, the NYC City Council Passed Local Law 22, requiring city agencies that use AI to annually report select information on their algorithm usage and data. 

Algorithmic Tools Compliance Report: https://data.cityofnewyork.us/City-Government/Algorithmic-Tools-Compliance-Report/jaw4-yuem/about_data

## Describing the dataset
The dataset reports on 76 algorithms currently in use with NYC agencies. Each row represents one tool.

The dataset contains 18 columns, 17 columns are object dtypes and one (year) is an integer. 
<img width="1071" alt="Algorithmic_tool_compliance_columns" src="https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/b4eed1e0-b04a-4903-ab0e-afa46f5ac82a">

<img width="301" alt="Screenshot 2024-05-01 at 11 19 57 AM" src="https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/f117cbf6-d108-4e63-8890-64effd9a38ca">

Within the 17 object columns, 10 contain descriptive information. 
The column "vendor" describes the partnerships (public, private, and third sector) that designed the algorithm rather than a list of collaborators. 
The "population_type" column, which describes which types of data power the algorithm, has a list with 8 different values.

The dataset contains many Na values across every column. 


## Cleaning the dataset

1. NA values weren't dropped from the dataset. Removing them would result in no available data. Moreover, for regulatory compliance and government accountability, it's essential to know which agencies are not fully reporting their algorithmic useage.

2. Convert *date_use* column to to_period.

3. Replace Na columns in *identifying_info* and *updated* columns to "Not Reported".

4. For non-Na values, the column *analysis_type* and *population_type* contains a dictionary of types of algorithmic analysis and data types used for each tool.  Seven distinct analysis types were identified, and some tools employed multiple types. Thus, the column was split into seven columns with responses of "yes," "no," or "not reported." In cases where the analysis type was reported, each column indicates "yes" or "no." However, for tools that didn't report an analysis type, the columns are labeled "not reported."


## Analyzing the dataset

### Number of Reported Algorithms by Agency
![algorithms_by_agency](https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/e973f4e7-cb7b-4388-9e7a-fd23ec61b5b6)

The DOHMH by far uses the most algorithms of any NYC agency.

### Algorithms with undisclosed data types and algorithm types
![alg_without_dtype](https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/1a47b75b-186f-49de-b14f-f988b2c330b6)

![alg_type_transparency](https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/3ccb7605-1b7f-4928-af24-8693a28b11ce)

40% of the algorithms did not report their data usage or algorithm type.

### Algorithm Type by Agency
![alg_type_by_agency](https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/83fadd4d-e41d-4ae7-8898-d0c705639d12)

The most common type of algorithm used by the city is predictive modeling. 

### Dtypes that fuel the algorithms
![dtypes_public_algs](https://github.com/jshapi16/NYC_alg_compliance/assets/79419060/5c35e69e-58a4-42c5-9e09-9758890dc19b)

Most city algorithms are using individual data.


## Next steps
There is still a lot to unpack in this dataset. I've begun an NLP analysis using NLTK and genism to separate vendor names and gain more information from the descriptive columns, stay tuned.

