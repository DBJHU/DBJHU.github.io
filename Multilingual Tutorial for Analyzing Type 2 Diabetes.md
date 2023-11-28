# Tutorial for Analyzing Type 2 Diabetes First Occurrence in OMOP CDM Data

This tutorial demonstrates how to create a flat file that consolidates information for each `person_id` based on the first occurrence of type 2 diabetes (standard concept ID 201826) using various data analysis tools: SQL, SAS, R, Stata, and SPSS.

Remember to adjust file paths and variable specifics according to your dataset.

## SQL

### Loading Data
Assuming the data are already loaded into a SQL database.

### SQL Query
```sql
SELECT
    p.*,
    vo.*,
    co.condition_occurrence_id,
    de.drug_exposure_id,
    m.measurement_id
FROM
    person p
JOIN
    condition_occurrence co ON p.person_id = co.person_id
JOIN
    visit_occurrence vo ON co.visit_occurrence_id = vo.visit_occurrence_id
LEFT JOIN
    drug_exposure de ON p.person_id = de.person_id AND vo.visit_occurrence_id = de.visit_occurrence_id
LEFT JOIN
    measurement m ON p.person_id = m.person_id AND vo.visit_occurrence_id = m.visit_occurrence_id
WHERE
    co.condition_concept_id = 201826
AND
    co.condition_start_date = (
        SELECT MIN(condition_start_date)
        FROM condition_occurrence
        WHERE person_id = co.person_id AND condition_concept_id = 201826
    )
GROUP BY
    p.person_id;
```

## SAS

### Loading Data
```sas
libname mydata '/path/to/csv/files';

proc import datafile="/path/to/csv/person.csv" 
    out=mydata.person 
    dbms=csv 
    replace;
run;

… [Repeat for other CSV files]
```

### SAS Code
```sas
proc sql;
    create table first_diabetes_visit as
    select
        p.*,
        vo.*,
        co.condition_occurrence_id,
        de.drug_exposure_id,
        m.measurement_id
    from
        mydata.person p
    inner join
        mydata.condition_occurrence co on p.person_id = co.person_id
    inner join
        mydata.visit_occurrence vo on co.visit_occurrence_id = vo.visit_occurrence_id
    left join
        mydata.drug_exposure de on p.person_id = de.person_id and vo.visit_occurrence_id = de.visit_occurrence_id
    left join
        mydata.measurement m on p.person_id = m.person_id and vo.visit_occurrence_id = m.visit_occurrence_id
    where
        co.condition_concept_id = 201826
    and
        co.condition_start_date = (
            select min(condition_start_date)
            from mydata.condition_occurrence
            where person_id = co.person_id and condition_concept_id = 201826
        )
    group by
        p.person_id;
quit;
```

## R

### Loading Data
```R
library(readr)

person <- read_csv("path/to/csv/person.csv")
visit_occurrence <- read_csv("path/to/csv/visit_occurrence.csv")
condition_occurrence <- read_csv("path/to/csv/condition_occurrence.csv")
drug_exposure <- read_csv("path/to/csv/drug_exposure.csv")
measurement <- read_csv("path/to/csv/measurement.csv")
```

### R Code
```R
library(dplyr)

first_diabetes_visit <- condition_occurrence %>%
  filter(condition_concept_id == 201826) %>%
  group_by(person_id) %>%
  summarize(first_diagnosis_date = min(condition_start_date)) %>%
  inner_join(visit_occurrence, by = "person_id") %>%
  inner_join(person, by = "person_id") %>%
  left_join(drug_exposure, by = c("person_id", "visit_occurrence_id")) %>%
  left_join(measurement, by = c("person_id", "visit_occurrence_id")) %>%
  filter(condition_start_date == first_diagnosis_date)

write.csv(first_diabetes_visit, "first_diabetes_visit.csv", row.names = FALSE)
```

## Stata

### Loading Data
```stata
import delimited "path/to/csv/person.csv", clear
save person, replace

… [Repeat for other CSV files]
```

### Stata Code
```stata
Assuming data are already loaded and named appropriately
merge 1:1 person_id using condition_occurrence
merge 1:1 person_id using visit_occurrence
merge 1:1 person_id using drug_exposure
merge 1:1 person_id using measurement

Filtering for first occurrence of type 2 diabetes
egen min_date = min(cond(condition_concept_id == 201826, condition_start_date, .)), by(person_id

)
keep if condition_start_date == min_date

Exporting the dataset
export delimited using "first_diabetes_visit.csv", replace
```

## SPSS

### Loading Data
```spss
GET DATA
  /TYPE=TXT
  /FILE='path/to/csv/person.csv'
  /DELCASE=LINE
  /DELIMITERS=","
  /ARRANGEMENT=DELIMITED
  /FIRSTCASE=2
  /VARIABLES=
  … [Variable names and types]
CACHE.
EXECUTE.

… [Repeat for other CSV files]
```

### SPSS Code
```spss
MATCH FILES
  /FILE=*
  /TABLE='condition_occurrence'
  /BY person_id.
MATCH FILES
  /FILE=*
  /TABLE='visit_occurrence'
  /BY person_id.
MATCH FILES
  /FILE=*
  /TABLE='drug_exposure'
  /BY person_id.
MATCH FILES
  /FILE=*
  /TABLE='measurement'
  /BY person_id.

Filtering for first occurrence of type 2 diabetes.
AGGREGATE OUTFILE=* MODE=ADDVARIABLES OVERWRITE=YES
/BREAK=person_id
/first_diagnosis_date=MIN(condition_start_date (condition_concept_id = 201826)).

SELECT IF condition_start_date = first_diagnosis_date.

Exporting the dataset.
SAVE OUTFILE='path/to/output/first_diabetes_visit.sav'.
```

## Python

### Loading Data
```python
import pandas as pd

person = pd.read_csv('path/to/csv/person.csv')
visit_occurrence = pd.read_csv('path/to/csv/visit_occurrence.csv')
condition_occurrence = pd.read_csv('path/to/csv/condition_occurrence.csv')
drug_exposure = pd.read_csv('path/to/csv/drug_exposure.csv')
measurement = pd.read_csv('path/to/csv/measurement.csv')
```

### Python Code
```python
Filtering for first occurrence of type 2 diabetes
first_diagnosis = condition_occurrence[condition_occurrence['condition_concept_id'] == 201826]
first_diagnosis = first_diagnosis.groupby('person_id')['condition_start_date'].min().reset_index()

Merging with other dataframes
merged_data = first_diagnosis.merge(visit_occurrence, on='person_id')
merged_data = merged_data.merge(person, on='person_id')
merged_data = merged_data.merge(drug_exposure, on=['person_id', 'visit_occurrence_id'], how='left')
merged_data = merged_data.merge(measurement, on=['person_id', 'visit_occurrence_id'], how='left')

Filtering to keep only records corresponding to the first diabetes diagnosis
merged_data = merged_data[merged_data['condition_start_date'] == merged_data['first_diagnosis_date']]

Exporting the dataset
merged_data.to_csv('first_diabetes_visit.csv', index=False)
```
```
