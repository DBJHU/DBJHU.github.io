```python
pip install pytrials
```


```python
import pandas as pd
from pytrials.client import ClinicalTrials



```


```python
ct = ClinicalTrials()




```


```python
# Get 50 full studies related to CP in json format.
#ct.get_full_studies(search_expr="readmission", max_studies=50)

```


```python
# Get several fields from 1000 studies related to readmission, in csv format.
readmission_fields = ct.get_study_fields(
    search_expr="readmission",
    fields=[
        "NCTId", "BriefTitle", "OverallStatus", "StartDate", "CompletionDate",
        "LastUpdatePostDate", "LeadSponsorName", "BriefSummary",
        "DetailedDescription", "StudyType", "EnrollmentType",
        "InterventionType", "InterventionName", "PrimaryOutcomeMeasure",
        "SecondaryOutcomeMeasure", "OtherOutcomeMeasure",
        "EligibilityCriteria", "Gender", "MinimumAge", "MaximumAge"
    ],
    max_studies=1000,
    fmt="csv",
)

```


```python
# Get the count of studies related to readmission*.
ct.get_study_count(search_expr="readmission")


```


```python
# Create DataFrame from the fetched data
df = pd.DataFrame.from_records(readmission_fields[1:], columns=readmission_fields[0])


```


```python
# Convert 'StartDate' to datetime and sort by this column in descending order
df['StartDate'] = pd.to_datetime(df['StartDate'], errors='coerce')
df = df.sort_values(by='StartDate', ascending=False)

```


```python
# Select the top 1000 most recent studies
df = df.head(1000)
```


```python
# Add a new column for the cardiac flag, initialize to 0
df['cardiac'] = 0

```


```python
# Add a new column for the learning health system flag, initialize to 0
df['LHS'] = 0

```


```python
# Iterate over the rows and check for the phrase "learning health system"
for index, row in df.iterrows():
    if "learning health system" in str(row['DetailedDescription']).lower():
        df.at[index, 'LHS'] = 1
```


```python
# Iterate over the rows and check for the phrase "cardiac"
for index, row in df.iterrows():
    if "cardiac" in str(row['DetailedDescription']).lower():
        df.at[index, 'cardiac'] = 1
```


```python
# Sort the DataFrame by StartDate in descending order
df['StartDate'] = pd.to_datetime(df['StartDate'], errors='coerce')  # Convert StartDate to datetime
df = df.sort_values(by='StartDate', ascending=False)

```


```python

# Now, export this updated DataFrame to a CSV file
df.to_csv('cardiac_readmission_fields_sorted.csv', index=False)  # 'index=False' to not include row indices in the CSV
```
