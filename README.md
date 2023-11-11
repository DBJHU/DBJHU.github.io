<!DOCTYPE html>
<html>
<body>
<h1>Hello!</h1>
<p>Welcome to my training material test lab!  I'm hosted with GitHub Pages.</p>
</body>
</html>

# Introduction

# Projects Best Suited for Observational Research and OHDSI Network Studies
![Source:  https://www.ohdsi.org/wp-content/uploads/2023/01/SOS-challenge-intro-24jan2023.pdf](AnalyticUseCases.png) 

## The Collaboration Process 
### This is just an example of the kinds of diagrams we can make
```mermaid
flowchart TD
    A[PersonA receives a research request]
    B[Person/group B sets up a meeting]
    C[Iterative biomedical query mediation process begins]
    D[Project outline is created and signed off by all parties]
    E[Voucher/payment/estimate is produced including resource and timeframe]
    F[Department head reviews/signs off on the voucher request]
    G[Work begins]
    H[First draft is produced with a notebook outlining results]
    I[Meeting is scheduled to review results of the notebook]
    J[Necessary modifications are made and returned to the researcher]
    K[End of Process]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J -.->|If modifications needed| G
    J -->|If complete| K
```

## OHDSI
# Current CDM
![Source: https://ohdsi.github.io/CommonDataModel/index.html](CDM54.png)


```mermaid
graph LR
    ICD9("ICD9") -->|Transformation to OMOP CDM| SNOMED("STANDARD<br>Vocabulary Concept Code<br>SNOMED")
    ICD10("ICD10") -->|Transformation to OMOP CDM| SNOMED
```

| Domain                    | Source Vocabulary              | Standard Vocabulary       |
|---------------------------|--------------------------------|---------------------------|
| Conditions                | ICD9, ICD10                    | SNOMED                    |
| Measurements              | LOINC or institutional specific codes | LOINC               |
| Drugs                     | NDC                            | RxNORM                    |
| Procedures                | ICD9, ICD10, CPT               | SNOMED                    |   |

* ICD = International Classification of Diseases
* SNOMED = Systematized Nomenclature of Medicine
* LOINC = Logical Observation Identifiers Names and Codes
* NDC = National Drug Code
* CPT = Current Procedural Terminology

---
title: "Interactive Data Dictionary"
format: html
---

```{=html}
<!-- Include DataTables CSS -->
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.20/css/jquery.dataTables.css">
<!-- Include jQuery and DataTables JavaScript -->
<script type="text/javascript" charset="utf8" src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
<script type="text/javascript" charset="utf8" src="https://cdn.datatables.net/1.10.20/js/jquery.dataTables.js"></script>
<script>
$(document).ready( function () {
    $('#table_id').DataTable();
} );
</script>
```

```{=html}
<!-- HTML table -->
<table id="table_id" class="display">
    <thead>
        <tr>
            <th>Relevant OMOP Table</th>
            <th>Field Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>person</td>
            <td>person_id</td>
            <td>A unique identifier for each person. </td>
        </tr>
        <tr>
            <td>person</td>
            <td>gender_concept_id</td>
            <td>A foreign key that refers to an identifier in the CONCEPT table for self-reported gender or sex at birth for the participant.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>year_of_birth</td>
            <td>The year of birth of the person. For data sources with date of birth, the year is extracted. For data sources where the year of birth is not available, the approximate year of birth is derived based on any age group categorization available.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>month_of_birth</td>
            <td>The month of birth of the person. For data sources that provide the precise date of birth, the month is extracted and stored in this field.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>day_of_birth</td>
            <td>The day of the month of birth of the person. For data sources that provide the precise date of birth, the day is extracted and stored in this field.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>birth_datetime</td>
            <td>The date and time of birth of the person. </td>
        </tr>
        <tr>
            <td>person</td>
            <td>race_concept_id</td>
            <td>A foreign key that refers to an identifier in the CONCEPT table for the unique race of the person, belonging to the 'Race' vocabulary.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>ethnicity_concept_id</td>
            <td>A foreign key that refers to the standard concept identifier in the Standardized Vocabularies for the ethnicity of the person, belonging to the 'Ethnicity' vocabulary.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>location_id</td>
            <td>A foreign key to the place of residency for the person in the location table, where the detailed address information is stored.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>provider_id</td>
            <td>A foreign key to the primary care provider the person is seeing in the provider table.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>care_site_id</td>
            <td>A foreign key to the site of primary care in the care_site table, where the details of the care site are stored.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>person_source_value</td>
            <td>An (encrypted) key derived from the person identifier in the source data. This is necessary when a use case requires a link back to the person data at the source dataset.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>gender_source_value</td>
            <td>The source code for the self-reported gender or sex at birth for the participant as it appears in the source data. The person’s response is mapped to a standard oncept in the Standardized Vocabularies; the original value is stored here for reference.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>gender_source_concept_id</td>
            <td>A foreign key to the self-reported gender or sex at birth concept for the participant that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>race_source_value</td>
            <td>The source code for the race of the person as it appears in the source data. The person race is mapped to a standard race concept in the Standardized Vocabularies and the original value is stored here for reference.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>race_source_concept_id</td>
            <td>A foreign key to the race concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>ethnicity_source_value</td>
            <td>The source code for the ethnicity of the person as it appears in the source data. The person ethnicity is mapped to a standard ethnicity concept in the Standardized Vocabularies and the original code is, stored here for reference.</td>
        </tr>
        <tr>
            <td>person</td>
            <td>ethnicity_source_concept_id</td>
            <td>A foreign key to the ethnicity concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_occurrence_id</td>
            <td>A unique identifier for each Condition Occurrence event.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person for whom the condition is recorded. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_concept_id</td>
            <td>A foreign key that refers to a Standard Concept identifier in the Standardized Vocabularies belonging to the 'Condition' domain.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_start_date</td>
            <td>The date when the instance of the Condition is recorded. </td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_start_datetime</td>
            <td>The date and time when the instance of the Condition is recorded. </td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_end_date</td>
            <td>The date when the instance of the Condition is considered to have ended.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_end_datetime</td>
            <td>The date and time when the instance of the Condition is considered to have ended. </td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the source data from which the Condition was recorded, the level of standardization, and the type of occurrence. </td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>stop_reason</td>
            <td>The reason that the Condition was no longer present, as indicated in the source data.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>provider_id</td>
            <td>A foreign key to the Provider in the PROVIDER table who was responsible for capturing (diagnosing) the Condition.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the unique identifier for the visit in the VISIT_OCCURRENCE table during which the Condition was determined (diagnosed).</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_source_value</td>
            <td>The source code for the Condition as it appears in the source data. This code is mapped to a Standard Condition Concept in the Standardized Vocabularies and the original code is stored here for reference.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_source_concept_id</td>
            <td>A foreign key to a Condition Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_status_source_value</td>
            <td>The source code for the condition status as it appears in the source data. This code is mapped to a Standard Concept in the Standardized Vocabularies and the original code is stored here for reference.</td>
        </tr>
        <tr>
            <td>condition_occurrence</td>
            <td>condition_status_concept_id</td>
            <td>The source code for the condition status as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_occurrence_id</td>
            <td>A unique identifier for each Person's visit or encounter at a healthcare provider.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person for whom the visit is recorded. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_concept_id</td>
            <td>A foreign key that refers to a visit Concept identifier in the Standardized Vocabularies belonging to the 'Visit' Vocabulary.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_start_date</td>
            <td>The start date of the visit.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_start_datetime</td>
            <td>The date and time of the visit started.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_end_date</td>
            <td>The end date of the visit. If this is a one-day visit the end date should match the start date.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_end_datetime</td>
            <td> The date and time of the visit end.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the type of source data from which the visit record is derived.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the provider table who was associated with the visit.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>care_site_id</td>
            <td>A foreign key to the care site in the care site table that was visited</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_source_value</td>
            <td>The source code for the visit as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>visit_source_concept_id</td>
            <td>A foreign key to a Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>admitting_source_concept_id</td>
            <td>A foreign key to the predefined concept in the Place of Service Vocabulary reflecting the admitting source for a visit.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>admitting_source_value</td>
            <td>The source code for the admitting source as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>discharge_to_concept_id</td>
            <td>A foreign key to the predefined concept in the Place of Service Vocabulary reflecting the discharge disposition for a visit.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>discharge_to_source_value</td>
            <td>The source code for the discharge disposition as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_occurrence</td>
            <td>preceding_visit_occurrence_id</td>
            <td>A foreign key to the visit_occurrence table of the visit immediately preceding this visit.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_id</td>
            <td>A unique identifier for each Person's unique interaction with the health care system.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person for whom the visit is recorded. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_concept_id</td>
            <td>A foreign key that refers to a visit Concept identifier in the Standardized Vocabularies belonging to the 'Visit' Vocabulary.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_start_date</td>
            <td>The start date of the encounter.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_start_datetime</td>
            <td>The date and time of the encounter started.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_end_date</td>
            <td>The end date of the encounter.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_end_datetime</td>
            <td>The date and time of the encounter ended. </td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the type of source data from which the visit record is derived.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the provider table who was associated with the visit.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>care_site_id</td>
            <td>A foreign key to the care site in the care site table that was visited</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_source_value</td>
            <td>The source code for the visit as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_source_concept_id</td>
            <td>A foreign key to a Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>admitting_source_value</td>
            <td>The source code for the admitting source as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>admitting_source_concept_id</td>
            <td>A foreign key to the predefined concept in the Place of Service Vocabulary reflecting the admitting source for a visit.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>discharge_to_source_value</td>
            <td>The source code for the discharge disposition as it appears in the source data.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>discharge_to_concept_id</td>
            <td>A foreign key to the predefined concept in the Place of Service Vocabulary reflecting the discharge disposition for a visit.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>preceding_visit_detail_id</td>
            <td>A foreign key to the visit_occurrence table of the visit immediately preceding this visit.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_detail_parent_id</td>
            <td>Use this field to find the visit detail that subsumes the given visit detail record. This is used in the case that a visit detail record needs to be nested beyond the VISIT_OCCURRENCE/VISIT_DETAIL relationship.</td>
        </tr>
        <tr>
            <td>visit_detail</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the unique identifier for the visit in the VISIT_OCCURRENCE table during which the encounter occurred.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_exposure_id</td>
            <td>A system-generated unique identifier for each Drug utilization event.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person who is subjected to the Drug. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_concept_id</td>
            <td>A foreign key that refers to a Standard Concept identifier in the Standardized Vocabularies belonging to the 'Drug' domain.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_exposure_start_date</td>
            <td>The start date for the current instance of Drug utilization. Valid entries include a start date of a prescription, the date a prescription was filled, or the date on which a Drug administration procedure was recorded.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_exposure_start_datetime</td>
            <td>The start date and time for the current instance of Drug utilization. Valid entries include a start datetime of a prescription, the date and time a prescription was filled, or the date and time on which a Drug administration procedure was recorded.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_exposure_end_date</td>
            <td>The end date for the current instance of Drug utilization. Depending on different sources, it could be a known or an inferred date and denotes the last day at which the patient was still exposed to Drug.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_exposure_end_datetime</td>
            <td>The end date and time for the current instance of Drug utilization. Depending on different sources, it could be a known or an inferred date and time and denotes the last day at which the patient was still exposed to Drug.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>verbatim_end_date</td>
            <td>The known end date of a Drug Exposure as provided by the source.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the type of Drug Exposure recorded. It indicates how the Drug Exposure was represented in the source data.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>stop_reason</td>
            <td>The reason the Drug was stopped. </td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>refills</td>
            <td>The number of refills after the initial prescription. The initial prescription is not counted, values start with null.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>quantity</td>
            <td>The quantity of drug as recorded in the original prescription or dispensing record.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>days_supply</td>
            <td>The number of days of supply of the medication as prescribed. This reflects the intention of the provider for the length of exposure.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>sig</td>
            <td>The directions ('signetur') on the Drug prescription as recorded in the original prescription (and printed on the container) or dispensing record.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>route_concept_id</td>
            <td>A foreign key that refers to a Standard Concept identifier in the Standardized Vocabularies reflecting the route of administration and belonging to the 'Route' domain.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>lot_number</td>
            <td>An identifier assigned to a particular quantity or lot of Drug product from the manufacturer.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the PROVIDER table who initiated (prescribed or administered) the Drug Exposure.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the Visit in the VISIT_OCCURRENCE table during which the Drug Exposure was initiated.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>visit_detail_id</td>
            <td>A foreign key to the Visit Detail in the VISIT_DETAIL table during which the Drug Exposure was initiated.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_source_value</td>
            <td>The source code for the Drug as it appears in the source data. This code is mapped to a Standard Drug concept in the Standardized Vocabularies and the original code is, stored here for reference.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>drug_source_concept_id</td>
            <td>A foreign key to a Drug Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>route_source_value</td>
            <td>The information about the route of administration as detailed in the source.</td>
        </tr>
        <tr>
            <td>drug_exposure</td>
            <td>dose_unit_source_value</td>
            <td>The information about the dose unit as detailed in the source.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_id</td>
            <td>A unique identifier for each Measurement.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person about whom the measurement was recorded. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_concept_id</td>
            <td>A foreign key to the standard measurement concept identifier in the Standardized Vocabularies. These belong to the 'Measurement' domain, but could overlap with the 'Observation' domain.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_date</td>
            <td>The date of the Measurement.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_datetime</td>
            <td>The date and time of the Measurement. Some database systems don't have a datatype of time. To accommodate all temporal analyses, datatype datetime can be used (combining measurement_date and measurement_time forum discussion)</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_type_concept_id</td>
            <td>A foreign key to the predefined Concept in the Standardized Vocabularies reflecting the provenance from where the Measurement record was recorded. </td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>operator_concept_id</td>
            <td>A foreign key identifier to the predefined Concept in the Standardized Vocabularies reflecting the mathematical operator that is applied to the value_as_number. </td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>value_as_number</td>
            <td>A Measurement result where the result is expressed as a numeric value.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>value_as_concept_id</td>
            <td>A foreign key to a Measurement result represented as a Concept from the Standardized Vocabularies (e.g., positive/negative, present/absent, low/high, etc.). These belong to the 'Meas Value' domain. </td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>unit_concept_id</td>
            <td>A foreign key to a Standard Concept ID of Measurement Units in the Standardized Vocabularies that belong to the 'Unit' domain.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>range_low</td>
            <td>The lower limit of the normal range of the Measurement result. The lower range is assumed to be of the same unit of measure as the Measurement value.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>range_high</td>
            <td>The upper limit of the normal range of the Measurement. The upper range is assumed to be of the same unit of measure as the Measurement value.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the PROVIDER table who was responsible for initiating or obtaining the measurement.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the Visit in the VISIT_OCCURRENCE table during which the Measurement was recorded.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>visit_detail_id</td>
            <td>A foreign key to the Visit Detail in the VISIT_DETAIL table during which the Measurement was taken.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_source_value</td>
            <td>The Measurement name as it appears in the source data. This code is mapped to a Standard Concept in the Standardized Vocabularies and the original code is stored here for reference.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>measurement_source_concept_id</td>
            <td>A foreign key to a Concept in the Standard Vocabularies that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>unit_source_value</td>
            <td>The source code for the unit as it appears in the source data. This code is mapped to a standard unit concept in the Standardized Vocabularies and the original code is stored here for reference.</td>
        </tr>
        <tr>
            <td>measurement</td>
            <td>value_source_value</td>
            <td>The source value associated with the content of the value_as_number or value_as_concept_id as stored in the source data.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_occurrence_id</td>
            <td>A system-generated unique identifier for each Procedure Occurrence.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person who is subjected to the Procedure. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_concept_id</td>
            <td>A foreign key that refers to a standard procedure Concept identifier in the Standardized Vocabularies. These belong to the 'Procedure' domain.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_date</td>
            <td>The date on which the Procedure was performed.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_datetime</td>
            <td>The date and time on which the Procedure was performed.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the type of source data from which the procedure record is derived.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>modifier_concept_id</td>
            <td>A foreign key to a Standard Concept identifier for a modifier to the Procedure (e.g. bilateral). </td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>quantity</td>
            <td>The quantity of procedures ordered or administered.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the PROVIDER table who was responsible for carrying out the procedure.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the Visit in the VISIT_OCCURRENCE table during which the Procedure was carried out.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_source_value</td>
            <td>The source code for the Procedure as it appears in the source data. This code is mapped to a standard procedure Concept in the Standardized Vocabularies and the original code is, stored here for reference. </td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>procedure_source_concept_id</td>
            <td>A foreign key to a Procedure Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>procedure_occurrence</td>
            <td>qualifier_source_value</td>
            <td>The source value for the qualifier as it appears in the source data.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_id</td>
            <td>A unique identifier for each observation.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person about whom the observation was recorded. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_concept_id</td>
            <td>A foreign key to the standard observation concept identifier in the Standardized Vocabularies. In cases where the recorded observation is the answer to a PPI question, this field will contain the Standard Concept ID for the corresponding question (or, if the question is non-standard, its standard LOINC/SNOMED equivalent).</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_date</td>
            <td>The date of the observation.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_datetime</td>
            <td>The date and time of the observation.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_type_concept_id</td>
            <td>A foreign key to the predefined concept identifier in the Standardized Vocabularies reflecting the type of the observation belonging to the 'Observation' domain.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>value_as_number</td>
            <td>The observation result stored as a number. This is applicable to observations where the result is expressed as a numeric value.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>value_as_string</td>
            <td>The observation result stored as a string. This is applicable to observations where the result is expressed as verbatim text.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>value_as_concept_id</td>
            <td>A foreign key to an observation result stored as a Concept ID. This is applicable to observations where the result can be expressed as a Standard Concept from the Standardized Vocabularies (e.g., positive/negative, present/absent, low/high, etc.). These belong to the 'Meas Value' domain. In cases where the recorded observation is the answer to a PPI question, this field will contain the standard PPI answer Concept ID or its standard LOINC/SNOMED equivalent (if the answer is non-standard). For PPI, this field is derived from value_source_concept_id.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>value_source_value</td>
            <td>The source value associated with the content of the value_as_number or value_as_concept_id as stored in the source data.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>qualifier_concept_id</td>
            <td>A foreign key to a Standard Concept ID for a qualifier (e.g., severity of drug-drug interaction alert)</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>unit_concept_id</td>
            <td>A foreign key to a Standard Concept ID of measurement units in the Standardized Vocabularies belonging to the 'Unit' domain.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the PROVIDER table who was responsible for making the observation.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the visit in the VISIT_OCCURRENCE table during which the observation was recorded.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>visit_detail_id</td>
            <td>A foreign key to the Visit Detail in the VISIT_DETAIL table during which the Observation was recorded.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_source_value</td>
            <td>The observation code as it appears in the source data. This code is mapped to a Standard Concept in the Standardized Vocabularies and the original code is, stored here for reference. If the recorded observation is the answer to a PPI question, the code for the PPI question is stored here. </td>
        </tr>
        <tr>
            <td>observation</td>
            <td>observation_source_concept_id</td>
            <td>A foreign key to a Concept that refers to the code used in the source. If the recorded observation is the answer to a PPI question, the PPI concept for the question is stored here.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>value_source_concept_id</td>
            <td>A foreign key to an Observation result represented as a Concept from the Standardized Vocabularies (e.g., positive/negative, present/absent, low/high, etc.).  For EHR data, these will be from the "Meas Val" domain. 

If the recorded observation is the response to a PPI question, this field will contain the PPI concept for the answer.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>unit_source_value</td>
            <td>The source code for the unit as it appears in the source data. This code is mapped to a standard unit concept in the Standardized Vocabularies and the original code is, stored here for reference.</td>
        </tr>
        <tr>
            <td>observation</td>
            <td>qualifier_source_value</td>
            <td>The source value associated with a qualifier to characterize the observation</td>
        </tr>
        <tr>
            <td>observation_period</td>
            <td>observation_period_id</td>
            <td>A unique identifier for each observation period</td>
        </tr>
        <tr>
            <td>observation_period</td>
            <td>person_id</td>
            <td>A foreign key identifier to the person for whom the observation period is defined. The demographic details of that person are stored in the person table</td>
        </tr>
        <tr>
            <td>observation_period</td>
            <td>observation_period_start_date</td>
            <td>The start date of the observation period for which data are available from the data source</td>
        </tr>
        <tr>
            <td>observation_period</td>
            <td>observation_period_end_date</td>
            <td>The end date of the observation period for which data are available from the data source</td>
        </tr>
        <tr>
            <td>observation_period</td>
            <td>period_type_concept_id</td>
            <td>A foreign key identifier to the predefined concept in the Standardized Vocabularies reflecting the source of the observation period information, belonging to the 'Obs Period Type' vocabulary</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_exposure_id</td>
            <td>A system-generated unique identifier for each Device Exposure.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person who is subjected to the Device. The demographic details of that Person are stored in the PERSON table.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_concept_id</td>
            <td>A foreign key that refers to a Standard Concept identifier in the Standardized Vocabularies belonging to the 'Device' domain.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_exposure_start_date</td>
            <td>The date the Device or supply was applied or used.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_exposure_start_datetime</td>
            <td>The date and time the Device or supply was applied or used.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_exposure_end_date</td>
            <td>The date use of the Device or supply was ceased.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_exposure_end_datetime</td>
            <td>The date and time use of the Device or supply was ceased.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_type_concept_id</td>
            <td>A foreign key to the predefined Concept identifier in the Standardized Vocabularies reflecting the type of Device Exposure recorded. It indicates how the Device Exposure was represented in the source data and belongs to the 'Device Type' domain.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>unique_device_id</td>
            <td>A UDI or equivalent identifying the instance of the Device used in the Person.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>quantity</td>
            <td>The number of individual Devices used in the exposure.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>provider_id</td>
            <td>A foreign key to the provider in the PROVIDER table who initiated or administered the Device.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>visit_occurrence_id</td>
            <td>A foreign key to the visit in the VISIT_OCCURRENCE table during which the Device was used.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>visit_detail_id</td>
            <td>A foreign key to the Visit Detail in the VISIT_DETAIL table during which the Device Exposure was initiated.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_source_value</td>
            <td>The source code for the Device as it appears in the source data. This code is mapped to a Standard Device Concept in the Standardized Vocabularies and the original code is stored here for reference.</td>
        </tr>
        <tr>
            <td>device_exposure</td>
            <td>device_source_concept_id</td>
            <td>A foreign key to a Device Concept that refers to the code used in the source.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>person_id</td>
            <td>A foreign key identifier to the deceased person. The demographic details of that person are stored in the person table.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>death_date   </td>
            <td>The date the person was deceased. If the precise date including day or month is not known or not allowed, December is used as the default month, and the last day of the month the default day.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>death_datetime</td>
            <td>The date and time the person was deceased. If the precise date including day or month is not known or not allowed, December is used as the default month, and the last day of the month the default day.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>death_type_concept_id</td>
            <td>A foreign key referring to the predefined concept identifier in the Standardized Vocabularies reflecting how the death was represented in the source data.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>cause_concept_id</td>
            <td>A foreign key referring to a standard concept identifier in the Standardized Vocabularies for conditions.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>cause_source_value</td>
            <td>The source code for the cause of death as it appears in the source data. This code is mapped to a standard concept in the Standardized Vocabularies and the original code is, stored here for reference.</td>
        </tr>
        <tr>
            <td>death</td>
            <td>cause_source_concept_id</td>
            <td>A foreign key to the concept that refers to the code used in the source. Note, this variable name is abbreviated to ensure it will be allowable across database platforms.</td>
        </tr>
        <tr>
            <td>fact_relationship</td>
            <td>domain_concept_id_1</td>
            <td>The concept representing the domain of fact one, from which the corresponding table can be inferred.</td>
        </tr>
        <tr>
            <td>fact_relationship</td>
            <td>fact_id_1</td>
            <td>The unique identifier in the table corresponding to the domain of fact one.</td>
        </tr>
        <tr>
            <td>fact_relationship</td>
            <td>domain_concept_id_2</td>
            <td>The concept representing the domain of fact two, from which the corresponding table can be inferred.</td>
        </tr>
        <tr>
            <td>fact_relationship</td>
            <td>fact_id_2</td>
            <td>The unique identifier in the table corresponding to the domain of fact two.</td>
        </tr>
        <tr>
            <td>fact_relationship</td>
            <td>relationship_concept_id</td>
            <td>A foreign key to a Standard Concept ID of relationship in the Standardized Vocabularies belonging to the 'Relationship' domain.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_id</td>
            <td>A unique identifier for each specimen.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>person_id</td>
            <td>A foreign key identifier to the Person for whom the Specimen is recorded.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_concept_id</td>
            <td>A foreign key referring to a Standard Concept identifier in the Standardized Vocabularies for the Specimen belonging to the 'Specimen' domain.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_type_concept_id</td>
            <td>A foreign key referring to the Concept identifier in the Standardized Vocabularies reflecting the system of record from which the Specimen was represented in the source data.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_date</td>
            <td>The date the specimen was obtained from the Person.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_datetime</td>
            <td>The date and time on the date when the Specimen was obtained from the person.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>quantity</td>
            <td>The amount of specimen collection from the person during the sampling procedure.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>unit_concept_id</td>
            <td>A foreign key to a Standard Concept identifier for the Unit associated with the numeric quantity of the Specimen collection belonging to the 'Unit' domain/</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>anatomic_site_concept_id</td>
            <td>A foreign key to a Standard Concept identifier for the anatomic location of specimen collection.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>disease_status_concept_id</td>
            <td>A foreign key to a Standard Concept identifier for the Disease Status of specimen collection.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_source_id</td>
            <td>The Specimen identifier as it appears in the source data.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>specimen_source_value</td>
            <td>The Specimen value as it appears in the source data. This value is mapped to a Standard Concept in the Standardized Vocabularies and the original code is, stored here for reference.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>unit_source_value</td>
            <td>The information about the Unit as detailed in the source.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>anatomic_site_source_value</td>
            <td>The information about the anatomic site as detailed in the source.</td>
        </tr>
        <tr>
            <td>specimen</td>
            <td>disease_status_source_value</td>
            <td>The information about the disease status as detailed in the source.</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_source_name</td>
            <td>The full name of the source</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_source_abbreviation</td>
            <td>An abbreviation of the source name</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_holder</td>
            <td>The name of the organization responsible for the development of the CDM instance</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>source_description</td>
            <td>A description of the source data origin and purpose for collection. The description may contain a summary of the period of time that is expected to be covered by this dataset.</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>source_documentation_reference</td>
            <td>URL or other external reference to location of source documentation</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_etl_reference</td>
            <td>URL or other external reference to location of ETL specification documentation and ETL source code</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>source_release_date</td>
            <td>The date for which the source data are most current, such as the last day of data capture</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_release_date</td>
            <td>The date when the CDM was instantiated</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>cdm_version</td>
            <td>The version of CDM used</td>
        </tr>
        <tr>
            <td>cdm_source</td>
            <td>vocabulary_version</td>
            <td>The version of the vocabulary used</td>
        </tr>
        <tr>
            <td>attribute_definition</td>
            <td>attribute_definition_id</td>
            <td>A unique identifier for each Attribute.</td>
        </tr>
        <tr>
            <td>attribute_definition</td>
            <td>attribute_name</td>
            <td>A short description of the Attribute.</td>
        </tr>
        <tr>
            <td>attribute_definition</td>
            <td>attribute_description</td>
            <td>A complete description of the Attribute definition</td>
        </tr>
        <tr>
            <td>attribute_definition</td>
            <td>attribute_type_concept_id</td>
            <td>Type defining what kind of Attribute Definition the record represents and how the syntax may be executed</td>
        </tr>
        <tr>
            <td>attribute_definition</td>
            <td>attribute_syntax</td>
            <td>Syntax or code to operationalize the Attribute definition</td>
        </tr>
        <tr>
            <td>concept</td>
            <td>concept_id</td>
            <td>A unique identifier for each Concept across all domains.</td>
        </tr>
        <tr>
            <td>concept</td>
            <td>concept_name</td>
            <td>An unambiguous, meaningful and descriptive name for the Concept.</td>
        </tr>
        <tr>
            <td>concept</td>
            <td>domain_id</td>
            <td>A foreign key to the DOMAIN table the Concept belongs to.</td>
        </tr>
        <tr>
            <td>concept</td>
            <td>vocabulary_id</td>
            <td>A foreign key to the VOCABULARY table indicating from which source the Concept has been adapted.</td>
        </tr>
        <tr>
            <td>concept</td>
            <td>concept_class_id</td>
            <td>The attribute or concept class of the Concept. </td>
        </tr>
        <tr>
            <td>concept</td>
            <td>standard_concept</td>
            <td>This flag determines where a Concept is a Standard Concept, i.e. is used in the data, a Classification Concept, or a non-standard Source Concept. </td>
        </tr>
        <tr>
            <td>concept</td>
            <td>concept_code</td>
            <td>The concept code represents the identifier of the Concept in the source vocabulary, such as SNOMED-CT concept IDs, RxNorm RXCUIs etc. </td>
        </tr>
        <tr>
            <td>concept</td>
            <td>valid_start_date</td>
            <td>The date when the Concept was first recorded. </td>
        </tr>
        <tr>
            <td>concept</td>
            <td>valid_end_date</td>
            <td>The date when the Concept became invalid because it was deleted or superseded (updated) by a new concept. </td>
        </tr>
        <tr>
            <td>concept</td>
            <td>invalid_reason</td>
            <td>Reason the Concept was invalidated. </td>
        </tr>
        <tr>
            <td>concept_ancestor</td>
            <td>ancestor_concept_id</td>
            <td>A foreign key to the concept in the concept table for the higher-level concept that forms the ancestor in the relationship.</td>
        </tr>
        <tr>
            <td>concept_ancestor</td>
            <td>descendant_concept_id</td>
            <td>A foreign key to the concept in the concept table for the lower-level concept that forms the descendant in the relationship.</td>
        </tr>
        <tr>
            <td>concept_ancestor</td>
            <td>min_levels_of_separation</td>
            <td>The minimum separation in number of levels of hierarchy between ancestor and descendant concepts. This is an attribute that is used to simplify hierarchic analysis.</td>
        </tr>
        <tr>
            <td>concept_ancestor</td>
            <td>max_levels_of_separation</td>
            <td>The maximum separation in number of levels of hierarchy between ancestor and descendant concepts. This is an attribute that is used to simplify hierarchic analysis.</td>
        </tr>
        <tr>
            <td>concept_class</td>
            <td>concept_class_id</td>
            <td>A unique key for each class</td>
        </tr>
        <tr>
            <td>concept_class</td>
            <td>concept_class_name</td>
            <td>The name describing the Concept Class.</td>
        </tr>
        <tr>
            <td>concept_class</td>
            <td>concept_class_concept_id</td>
            <td>A foreign key that refers to an identifier in the CONCEPT table for the unique Concept Class the record belongs to.</td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>concept_id_1</td>
            <td>A foreign key to a Concept in the CONCEPT table associated with the relationship. Relationships are directional, and this field represents the source concept designation.</td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>concept_id_2</td>
            <td>A foreign key to a Concept in the CONCEPT table associated with the relationship. Relationships are directional, and this field represents the destination concept designation.</td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>relationship_id</td>
            <td>A unique identifier to the type or nature of the Relationship as defined in the RELATIONSHIP table.</td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>valid_start_date</td>
            <td>The date when the instance of the Concept Relationship is first recorded.</td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>valid_end_date</td>
            <td>The date when the Concept Relationship became invalid because it was deleted or superseded (updated) by a new relationship. </td>
        </tr>
        <tr>
            <td>concept_relationship</td>
            <td>invalid_reason</td>
            <td>Reason the relationship was invalidated. </td>
        </tr>
        <tr>
            <td>concept_synonym</td>
            <td>concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table.</td>
        </tr>
        <tr>
            <td>concept_synonym</td>
            <td>concept_synonym_name</td>
            <td>The alternative name for the Concept.</td>
        </tr>
        <tr>
            <td>concept_synonym</td>
            <td>language_concept_id</td>
            <td>A foreign key to a Concept representing the language.</td>
        </tr>
        <tr>
            <td>domain</td>
            <td>domain_id</td>
            <td>A unique key for each domain.</td>
        </tr>
        <tr>
            <td>domain</td>
            <td>domain_name</td>
            <td>The name describing the Domain.</td>
        </tr>
        <tr>
            <td>domain</td>
            <td>domain_concept_id</td>
            <td>A foreign key that refers to an identifier in the CONCEPT table for the unique Domain Concept the Domain record belongs to.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>drug_concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table representing the identifier for Branded Drug or Clinical Drug Concept.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>ingredient_concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table, representing the identifier for drug Ingredient Concept contained within the drug product.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>amount_value</td>
            <td>The numeric value associated with the amount of active ingredient contained within the product.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>amount_unit_concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table representing the identifier for the Unit for the absolute amount of active ingredient.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>numerator_value</td>
            <td>The numeric value associated with the concentration of the active ingredient contained in the product</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>numerator_unit_concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table representing the identifier for the numerator Unit for the concentration of active ingredient.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>denominator_value</td>
            <td>The amount of total liquid (or other divisible product, such as ointment, gel, spray, etc.).</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>denominator_unit_concept_id</td>
            <td>A foreign key to the Concept in the CONCEPT table representing the identifier for the denominator Unit for the concentration of active ingredient.</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>box_size</td>
            <td>The number of units of Clinical of Branded Drug, or Quantified Clinical or Branded Drug contained in a box as dispensed to the patient</td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>valid_start_date</td>
            <td>The date when the Concept was first recorded. </td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>valid_end_date</td>
            <td>The date when the concept became invalid because it was deleted or superseded (updated) by a new Concept. </td>
        </tr>
        <tr>
            <td>drug_strength</td>
            <td>invalid_reason</td>
            <td>Reason the concept was invalidated.</td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>relationship_id</td>
            <td>The type of relationship captured by the relationship record.</td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>relationship_name</td>
            <td>The text that describes the relationship type.</td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>is_hierarchical</td>
            <td>Defines whether a relationship defines concepts into classes or hierarchies. </td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>defines_ancestry</td>
            <td>Defines whether a hierarchical relationship contributes to the concept_ancestor table. These are subsets of the hierarchical relationships.</td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>reverse_relationship_id</td>
            <td>The identifier for the relationship used to define the reverse relationship between two concepts.</td>
        </tr>
        <tr>
            <td>relationship</td>
            <td>relationship_concept_id</td>
            <td>A foreign key that refers to an identifier in the CONCEPT table for the unique relationship concept.</td>
        </tr>
        <tr>
            <td>vocabulary</td>
            <td>vocabulary_id</td>
            <td>A unique identifier for each Vocabulary, such as ICD9CM, SNOMED, Visit.</td>
        </tr>
        <tr>
            <td>vocabulary</td>
            <td>vocabulary_name</td>
            <td>The name describing the vocabulary, for example "International Classification of Diseases, Ninth Revision, Clinical Modification, Volume 1 and 2 (NCHS)" etc.</td>
        </tr>
        <tr>
            <td>vocabulary</td>
            <td>vocabulary_reference</td>
            <td>External reference to documentation or available download of the about the vocabulary.</td>
        </tr>
        <tr>
            <td>vocabulary</td>
            <td>vocabulary_version</td>
            <td>Version of the Vocabulary as indicated in the source.</td>
        </tr>
        <tr>
            <td>vocabulary</td>
            <td>vocabulary_concept_id</td>
            <td>A foreign key that refers to a standard concept identifier in the CONCEPT table for the Vocabulary the VOCABULARY record belongs to.</td>
        </tr>
    </tbody>
</table>
```



# Analysis Tools
R, SQL, Python, or any preferred data analysis software. Examples provided below are for R and SQL.
[The Book of OHDSI Chapter 9] (https://ohdsi.github.io/TheBookOfOhdsi/SqlAndR.html) provides an overview of analysis of OHDSI data in R and SQL; note that you will not be able to avail yourselves of OHDSI software tools when analyzing your exported data for the reason explained above.
<
## Jupyter Notebooks and programming
[Source:NIH All of US Study] (https://support.researchallofus.org/hc/en-us/articles/360039690191-Jupyter-Notebooks-and-programming)

Below you will find links to  helpful resources on using Jupyter Notebooks. 
Below you will find links to some of the most helpful resources that we have created and/or found on using Jupyter Notebooks. While we can’t teach you how to program, we have identified some online resources that can help get you started.
### OHDSI Resources
Hello! Please familiarize yourself with the following tools and resources which will help you throughout this course and your OHDSI journey.

Check out the [**OHDSI Forums**](https://forums.ohdsi.org/) *Introduce yourself on the "Welcome to OHDSI" thread.*

Bookmark [**The Book of OHDSI**](https://ohdsi.github.io/TheBookOfOhdsi/)

Join the OHDSI [**Microsoft Teams**](https://forms.office.com/Pages/ResponsePage.aspx?id=lAAPoyCRq0q6TOVQkCOy1ZyG6Ud_r2tKuS0HcGnqiQZUQ05MOU9BSzEwOThZVjNQVVFGTDNZRENONiQlQCN0PWcu) environment.

Check out the [**MIMIC-IV demo data set**](https://physionet.org/content/mimic-iv-demo-omop/0.9/1_omop_data_csv/) in OMOP CDM format!

Register with [**EHDEN Academy**](https://academy.ehden.eu/)

Visit the [**Atlas Demo**](https://atlas-demo.ohdsi.org/) and [**Athena**](https://athena.ohdsi.org/search-terms/start).

Bookmark the [**OHDSI YouTube tutorials and workshops**](https://youtube.com/playlist?list=PLpzbqK7kvfeXRQktX0PV-cRpb3EFA2e7Z)

Visit the [**OHDSI Community Dashboard**](https://dash.ohdsi.org/)

Bookmark [**OMOP Common Data Model (ohdsi.github.io)**](https://ohdsi.github.io/CommonDataModel/index.html)

[**Learn about GitHub**](https://docs.github.com/en/get-started/quickstart/hello-world) if you don't already know.

Plan to attend an [**OHDSI Community call**](https://ohdsi.org/community-calls/)

Learn about OHDSI [**Workgroups**](https://ohdsi.org/upcoming-working-group-calls/)

Follow OHDSI on social media: [**Twitter**](https://twitter.com/OHDSI) [**LinkedIn**](https://www.linkedin.com/company/ohdsi)

[**Subscribe**](https://ohdsi.org/subscribe-to-our-newsletter/) to the OHDSI Newsletter

Learn about past and [**upcoming OHDSI events**](https://ohdsi.org/2023-ohdsi-events/)

Learn about OHDSI [**software**](https://ohdsi.org/software-tools/)

Look up individual concepts in [Athena](https://athena.ohdsi.org/)

Check out useful OHDSI-related documentation here: [NIH ALL of US OMOP Documentation](https://support.researchallofus.org/hc/en-us/articles/360039585391-How-the-Observational-Medical-Outcomes-Partnership-OMOP-vocabulary-are-structured)

## Python, SWL, and R Programming Resources

- [Project Jupyter](https://jupyter.org/)
- [What is the Jupyter Notebook?](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html)
- [Intro to Jupyter Notebooks and Anaconda (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.1.1)

Software Carpentry is a website that provides free online lessons to researchers wanting to enhance their programming skills for data analysis. This website offers free online lessons on a variety of useful topics including:

- [Programming with Python](http://swcarpentry.github.io/python-novice-inflammation/)
- [Programming with R](http://swcarpentry.github.io/r-novice-inflammation/)
- [Databases and SQL](http://swcarpentry.github.io/sql-novice-survey/)

We have included additional resources for help with programming below.

- [DataCamp](http://www.datacamp.com/)
- [Codecademy - Learn Python 2](https://www.codecademy.com/learn/learn-python)
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
- [R for Data Science](https://r4ds.had.co.nz/)
- [Introduction to Programming (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.1)
- [Python Programming (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.2)
- [Data Analysis with Python and Pandas (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.3)
- [Data Visualization with Python (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.4)


## Analysis with SQL

The [OMOP Query Library](https://data.ohdsi.org/QueryLibrary/) is a library of commonly-used SQL queries for the OMOP Common Data Model (CDM).


## Analysis with R
Below are some sample R queries that demonstrate how to read in OMOP tables from CSV files, join them based on the `person_id` and `visit_occurrence_id` fields, and search for specific criteria.

Note: Adjust the file paths and column names accordingly based on the actual structure and location of your CSV files. The queries below are a generic representation and may need adjustments based on the specifics of your data set.

### Reading CSV files into R data frames:

```R
# Read the CSV files into R data frames
person_df <- read.csv("path_to_person_table.csv", header=TRUE, stringsAsFactors=FALSE)
visit_occurrence_df <- read.csv("path_to_visit_occurrence_table.csv", header=TRUE, stringsAsFactors=FALSE)
condition_occurrence_df <- read.csv("path_to_condition_occurrence_table.csv", header=TRUE, stringsAsFactors=FALSE)
```
Join tables based on `person_id`:

When a person has multiple visits in the `visit_occurrence` table, joining the `person` table with the `visit_occurrence` table will result in multiple rows for that person, each corresponding to a different visit. This is a standard one-to-many join operation.

```R
## Join person with visit_occurrence on 'person_id'
person_visit_df <- merge(person_df, visit_occurrence_df, by="person_id")
```

### Joining the Person-Visit table with the Condition Occurrence table:

```R
# Join the person-visit result with condition_occurrence on both 'person_id' and 'visit_occurrence_id'
full_df <- merge(person_visit_df, condition_occurrence_df, by=c("person_id", "visit_occurrence_id"))
```

### Search by a list of `person_ids`:

```R
# Define a list of person_ids to search for
search_person_ids <- c(1, 2, 3, 4, 5)

# Filter the data frame to only include rows with person_ids in the list
filtered_by_person_df <- subset(full_df, person_id %in% search_person_ids)
```

### Search by a specific condition concept code:

```R
# Define a specific condition concept code to search for
search_condition_concept_id <- 1234567

# Filter the data frame to only include rows with the specified condition concept code
filtered_by_condition_df <- subset(full_df, condition_concept_id == search_condition_concept_id)
```

### Search by a date range:

```R
# Define a date range to search for
start_date <- as.Date("2020-01-01")
end_date <- as.Date("2020-12-31")

## Filter the data frame to only include rows within the date range
filtered_by_date_df <- subset(full_df, visit_start_date >= start_date & visit_start_date <= end_date)
```
<!--TBD
## Analysis with Python 

### Required Python Libraries:

To execute the Python queries, you'll need to install the pandas library. -->

