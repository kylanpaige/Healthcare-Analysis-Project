# Healthcare-Analysis-Project
Healthcare Analysis Project - Kylan Paige
Overview of the steps I'll be taking:

1. **Data Sourcing**: Identify and select relevant datasets that I can scrape or download.
2. **Data Collection**: Use Python to scrape or download the data.
3. **Data Cleaning & Transformation**: Process the data to make it suitable for analysis.
4. **Data Storage**: Store the processed data in a suitable format (e.g., SQL or Excel) that can be imported into Tableau.
5. **Data Visualization in Tableau**: Import the data into Tableau and create informative visualizations.
6. **Analysis & Presentation**: Interpret the visualizations and prepare a presentation.

### Step 1: Data Sourcing

Before I proceed, I need to decide on a theme or topic for my analysis. This will guide my search for datasets:

- **Economic Indicators**: Compare GDP, unemployment rates, and other economic indicators across countries or over time.
- **Healthcare**: Analyze data related to diseases, healthcare facilities, patient outcomes, etc.
- **Environment**: Look into data about climate change, pollution levels, deforestation rates, etc.
- **Sports**: Analyze performance metrics of teams or players, ticket sales, etc.
- **E-commerce**: Analyze sales data, customer reviews, product listings, etc.

Healthcare is a vast field with numerous datasets available. Based on my search, there are some interesting healthcare datasets available on GitHub:
1. [**sytora**](https://github.com/leanderme/sytora): A sophisticated smart symptom search engine.
2. [**awesome-healthcare-ai**](https://github.com/medtorch/awesome-healthcare-ai): A curated list of awesome open-source healthcare tools, algorithms, datasets, and research papers.
3. [**Heart-Failure-Condition-And-Survival-Analysis**](https://github.com/sauravmishra1710/Heart-Failure-Condition-And-Survival-Analysis): Perform a survival analysis based on the time-to-event (death event) for subjects. This dataset can be used to help hospitals assess the severity of patients with cardiovascular diseases and heart failure condition.
4. [**HAR**](https://github.com/mingzhu0527/HAR): Code for a paper on a Hierarchical Attention Retrieval Model for Healthcare Question Answering.
5. [**PowerPopHealth**](https://github.com/gregbeaumont/PowerPopHealth): A collection of content intended to simplify the process of ingesting and prepping Healthcare Open Data using Azure data tools and Power BI.

### Proposed Plan:

1. **Data Collection**: I'll use Python to download the "Heart-Failure-Condition-And-Survival-Analysis" dataset.
2. **Data Cleaning & Transformation**: Process the dataset to make it suitable for analysis.
3. **Data Storage**: Store the processed data in a suitable format (e.g., SQL or Excel) that can be imported into Tableau.
4. **Data Visualization in Tableau**: Import the data into Tableau and create informative visualizations.
5. **Analysis & Presentation**: Interpret the visualizations and prepare a presentation.

### Step 2: Data Collection

I start by downloading the "Heart-Failure-Condition-And-Survival-Analysis" dataset from GitHub. I write the Python code to do this in the notebook.

```python
import requests
import pandas as pd
from io import StringIO

# URL of the dataset on GitHub
data_url = 'https://raw.githubusercontent.com/sauravmishra1710/Heart-Failure-Condition-And-Survival-Analysis/main/heart_failure_clinical_records_dataset.csv'

# Download the dataset
response = requests.get(data_url)
data = StringIO(response.text)

# Load the dataset into a pandas DataFrame
heart_failure_df = pd.read_csv(data)
heart_failure_df.head()
```

### Step 3: Data Cleaning & Transformation

In this step:

- Load the dataset into a pandas DataFrame.
- Explore the dataset to understand its structure.
- Handle any missing values or outliers.
- Transform the data if necessary to make it suitable for analysis.

I start by loading the dataset and displaying the first few rows to understand its structure.

Here's a brief overview of the dataset:

- **Number of Rows**: 5 (This is just a sample; the dataset is larger.)
- **Number of Columns**: 13

**Columns**:

1. **age**: Age of the patient
2. **anaemia**: Decrease of red blood cells or hemoglobin (0: No, 1: Yes)
3. **creatinine_phosphokinase**: Level of the CPK enzyme in the blood (mcg/L)
4. **diabetes**: If the patient has diabetes (0: No, 1: Yes)
5. **ejection_fraction**: Percentage of blood leaving the heart at each contraction
6. **high_blood_pressure**: If the patient has hypertension (0: No, 1: Yes)
7. **platelets**: Platelets in the blood (kiloplatelets/mL)
8. **serum_creatinine**: Level of serum creatinine in the blood (mg/dL)
9. **serum_sodium**: Level of serum sodium in the blood (mEq/L)
10. **sex**: Gender of the patient (0: Female, 1: Male)
11. **smoking**: If the patient smokes (0: No, 1: Yes)
12. **time**: Follow-up period (days)
13. **DEATH_EVENT**: If the patient deceased during the follow-up period (0: No, 1: Yes)

### More in Depth definitions
1. **Age**: This is self-explanatory. It represents the age of the patient.
    
2. **Anaemia**: Anaemia is a condition in which you lack enough healthy red blood cells to carry adequate oxygen to your body's tissues. In the dataset, it's represented as a binary variable:
    
    - 0: No anaemia
    - 1: Presence of anaemia
3. **Creatinine Phosphokinase (CPK)**: This is an enzyme found mainly in the heart, brain, and skeletal muscle. It is tested in the blood to measure if there has been damage to these muscles. A high level of CPK is an indication of damage.
    
4. **Diabetes**: Diabetes is a disease that occurs when your blood glucose (blood sugar) is too high. In the dataset, it's represented as:
    
    - 0: No diabetes
    - 1: Presence of diabetes
5. **Ejection Fraction**: This is a measurement of the percentage of blood leaving your heart each time it contracts. The heart contracts and pushes blood out into the arteries. It's an indicator of how well your heart is pumping out blood and can be used to help diagnose and track heart failure.
    
6. **High Blood Pressure**: High blood pressure, or hypertension, is when the force of the blood against the walls of the arteries is too high. In the dataset, it's represented as:
    
    - 0: No high blood pressure
    - 1: Presence of high blood pressure
7. **Platelets**: Platelets are tiny blood cells that help your body form clots to stop bleeding. If one of your blood vessels gets damaged, it sends out signals to the platelets. The platelets then rush to the site of damage and form a plug, or clot, to repair the damage. The measurement in the dataset is in kiloplatelets/mL.
    
8. **Serum Creatinine**: Creatinine is a waste product that comes from the normal wear and tear on muscles of the body. The levels of creatinine in the bloodstream and urine can be used to calculate the creatinine clearance, which reflects the glomerular filtration rate (GFR). The GFR is a measure of how well the kidneys are filtering wastes from the blood.
    
9. **Serum Sodium**: Sodium is a substance that the body needs to work properly. It is an electrolyte that helps regulate the amount of water in and around cells. The serum sodium test measures the amount of sodium in the blood.
    
10. **Sex**:
    

- 0: Female
- 1: Male

11. **Smoking**: Indicates if the patient smokes or not:

- 0: Non-smoker
- 1: Smoker

12. **Time**: It's not explicitly mentioned in many datasets, but it often refers to the time (in days) at which the observation was made or the duration of the follow-up period for the patient.
    
13. **DEATH_EVENT**: Indicates if the patient deceased during the follow-up period:
    

- 0: No (Patient survived)
- 1: Yes (Patient passed away)

Next, I check for any missing values and handle them if necessary. 

The dataset does not have any missing values. This means I can proceed without needing to handle any gaps in the data.
### Step 4: Data Exploration & Visualization

Before diving into Tableau, I find it good practice to explore the dataset and visualize some key aspects using Python. This gives me insights into the data and helps me decide which aspects to focus on in Tableau.

I start by visualizing the distribution of some key variables:

1. Age distribution of patients.
2. Distribution of key categorical variables like diabetes, anemia, high blood pressure, and smoking.
3. Correlation between key numerical variables.

Here's the age distribution of patients:

![[Pasted image 20230911154638.png]]

From the histogram, I can observe that:

- The majority of patients are in the age range of 50 to 70 years.
- There's a peak around the age of 60, indicating a higher number of patients in that age group.

Next, I visualize the distribution of key categorical variables: diabetes, anemia, high blood pressure, and smoking. I use bar plots for this.

Here are the distributions of key categorical variables:

![[Pasted image 20230911154741.png]]

From the plots, I can observe:

1. **Diabetes**: A slightly higher number of patients do not have diabetes compared to those who do.
2. **Anemia**: A majority of patients do not have anemia.
3. **High Blood Pressure**: More patients do not have high blood pressure compared to those who do.
4. **Smoking**: A significant number of patients do not smoke.

Here's the correlation heatmap of the variables:

![[Pasted image 20230911154929.png]]

From the heatmap, I can observe the following:

- The variable `time` (Follow-up period) has a strong negative correlation with `DEATH_EVENT`. This suggests that patients with shorter follow-up periods are more likely to have a death event.
- `ejection_fraction` also has a negative correlation with `DEATH_EVENT`, indicating that higher ejection fractions (better heart function) are associated with lower death events.
- Other variables like `serum_creatinine` and `age` have positive correlations with `DEATH_EVENT`.

These insights can guide my analysis and visualization in Tableau.

### Step 5: Data Storage

Before moving to Tableau, I need to store the cleaned and processed data in a suitable format. Given the options, storing the data in an Excel file would be straightforward and easily importable into Tableau.

I save the dataset as an Excel file to be imported in the next step.

The dataset was  saved as an Excel file named [heart_failure_data.xlsx](https://app.noteable.io/p/9821ed0b-e3cc-4eaa-badd-a90c87abf5f3/Tableau-Case-1).

### Step 6: Data Visualization in Tableau

Now that I have my data ready, let's move to Tableau:

1. **Import Data**: Open Tableau and import the `heart_failure_data.xlsx` file.
2. **Explore Data**: I familiarize myself with the data in Tableau. Check the data types and ensure they are correctly identified.
3. **Create Visualizations**:
    - **Bar Charts**: For categorical variables like `diabetes`, `anaemia`, `high_blood_pressure`, and `smoking`.
    - **Histogram**: For the age distribution.
    - **Heatmap**: For the correlation between variables.
    - **Time Series**: To analyze the `time` variable against the `DEATH_EVENT`.
4. **Dashboard Creation**: Combine multiple visualizations into a single dashboard. This provides a comprehensive view of the data.
5. **Story Creation**: Create a story in Tableau to guide the viewer through my analysis. Highlight key findings and insights.

### Step 7: Analysis & Presentation

After creating the visualizations and dashboards, I need to interpret the results. Here are some points to consider:

- What age groups are most affected?
- How do factors like diabetes, anaemia, and high blood pressure influence the death event?
- What insights can be drawn from the correlation heatmap?

Prepare a presentation based on my findings.
