# Los-Angeles-Crime-Report

## Access the Full PowerBI Report
To view the complete PowerBI report, please click [here](Final-Report.pdf).

## Data Abstraction
This dataset reflects incidents of crime in the City of Los Angeles dating back to 2020. This data is transcribed from original crime reports that are typed on paper; therefore, there may be some inaccuracies. Some location fields with missing data are noted as (0°, 0°). Address fields are only provided to the nearest hundred blocks to maintain privacy. This data is as accurate as the data in the database. Please note questions or concerns in the comments.

## Data Profiling in ALTRYX
![](Screenshots/DataProfiling.png)

## Tools used in ALTRYX
In analyzing the Los Angeles Crime dataset in Alteryx, the following tools were instrumental in gaining insights into the data's structure, quality, and content:

![](Screenshots/Altryx_workflow.png)
- **Input Data Tool**:
I utilized the Input Data Tool to import the Los Angeles Crime dataset into my Alteryx workflow. This tool can be configured to read the dataset from various sources, such as a CSV file.
   
- **Browse Tool**:
Connecting a Browse Tool to the output of the Input Data Tool enabled interactive inspection of the dataset in the Alteryx Results window. This tool facilitated the review of data structure and quality, anomaly detection, and initial understanding of content.         
- **Unique Tool**:
To identify unique values in specific columns, I incorporated Unique Tools into the workflow. For instance, the Unique Tool was employed to visualize all unique crime types in the "Crm Cd Desc" column.
- **Basic Data Profile Tool**:
Adding a Basic Data Profile Tool and connecting it to the output of the Input Data Tool allowed for the generation of summary statistics, data type information, and visualizations to profile the dataset.
- **Filter Tool**:
The Filter Tool provided the capability to control which records pass through the pipeline based on specific criteria, enhancing data manipulation and analysis processes.

## Data types used for staging pipelines in Talend

![](Screenshots/Talend_Pipeline.png)

Alteryx offers powerful tools for data profiling, including the Summarize Tool and Browse Tool, which allow users to explore and analyze the data types present in their datasets. Leveraging these data types, we can establish appropriate data type mappings in Talend to prevent errors during source-to-target data loads.

| Name         | Type     | Size |
|--------------|----------|------|
| DR_NO        | String   | 9    |
| Date Rptd    | String   | 22   |
| DATE OCC     | String   | 22   |
| TIME OCC     | String   | 4    |
| AREA         | String   | 2    |
| AREA NAME    | String   | 11   |
| Rpt Dist No  | String   | 4    |
| Part 1-2     | Byte     | 1    |
| Crm Cd       | Int16    | 2    |
| Crm Cd Desc  | V_String | 56   |
| Mocodes      | V_String | 49   |
| Vict Age     | Int16    | 2    |
| Vict Sex     | String   | 1    |
| Vict Descent | String   | 1    |
| Premis Cd    | Int16    | 2    |
| Premis Desc  | V_String | 63   |
| Weapon Used Cd | Int16  | 2    |
| Weapon Desc  | V_String | 46   |
| Status       | String   | 2    |
| Status Desc  | String   | 12   |
| Crm Cd 1     | Int16    | 2    |
| Crm Cd 2     | Int16    | 2    |
| Crm Cd 3     | Int16    | 2    |
| Crm Cd 4     | Int16    | 2    |
| LOCATION     | String   | 40   |
| Cross Street | V_String | 34   |
| LAT          | Double   | 8    |
| LON          | Double   | 8    |

## Insights on the LA Crime Data

1. **Unique DR Numbers**: All DR numbers (Division of Records) within the dataset are unique, indicating that each crime incident is assigned a distinct identifier. This uniqueness ensures that no duplicate records exist for the same incident.

2. **Victim Age Analysis**:
   - **Outliers**: The dataset includes several outliers in the "vict_age" column, indicating extreme age values that may require further investigation or data validation.
   - **Zero Values**: Approximately 98,709 rows have zero values in the "vict_age" column, which could represent missing or unknown age information. Handling these zeros is essential for accurate analysis.
   - **Negative Values**: The presence of negative values in the "vict_age" column does not align with practical expectations, suggesting potential data entry errors.

3. **Victim Gender Distribution**:
   - **Male Dominance**: Approximately 42% of victims are recorded as male, making them the largest group among recorded victim genders.
   - **Female Victims**: Around 36% of victims are identified as female.
   - **Null Values**: There are 13% of null values in the "vict_sex" column, which may require imputation or handling.
   - **Unknown Gender**: The value "H" in the "vict_sex" column, representing an unknown gender, could be imputed to "X" to signify an unknown gender category.

4. **Common Crime Descriptions**: Analysis of crime descriptions reveals that the most prevalent type of crime in the dataset is "vehicle being stolen." This insight provides an understanding of the predominant criminal activity in the area.

5. **Crime Resolution Status**: 77% of crimes have been marked as "solved" or "Investigation completed." This suggests that a significant portion of recorded crimes have reached a resolution or undergone investigation.
       
## Data Cleaning Using Staging Pipelines

1. **tMap Component**: Utilize the tMap component to replace missing values in specific columns. Employ the NVL() function to substitute a default value for null or outliers, ensuring data integrity and consistency.

2. **tUniqRow Component**: Employ the tUniqRow component to eliminate duplicates from your dataset. Configure it to retain either the first or last instance of a duplicate based on certain columns, effectively cleaning your data and reducing redundancy.

3. **tReplace Component**: Use the tReplace Component to identify specific values or patterns in your data and replace them with desired values. This component is invaluable for addressing inconsistencies or typographical errors, enhancing the accuracy and reliability of your dataset.

## Databases
![](Screenshots/Azuredatabase.png)

**Figure 1: Azure Database Data Description**

![](Screenshots/MySql_workbench.png)

**Figure 2: MySQL Workbench**
