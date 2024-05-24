<h1>Welcome to my training material test lab and Markdown "sampler"! </h1>

### Where I share fabulous data science resources while teaching myself new ways to present information using Markdown!!

# Table of Contents

- [OHDSI_Resources](#ohdsi-resources)
- [OMOP CDM Basic Data Dictionary](#omop-cdm-basic-data-dictionary)
- [Projects Best Suited for Observational Research and OHDSI Network Studies](#projects-best-suited-for-observational-research-and-ohdsi-network-studies)
- [Analytic Use Cases and Examples](#analytic-use-cases-and-examples)
- [Data Management Tools and Resources(##Data-Management-Tools-and-resources)
- [Incremental Loading](#incremental-loading)
- [The Collaboration Process](#the-collaboration-process)
- [Data Content Ontology](#Data-Content-Ontology)
- [Current CDM](#current-cdm)
- [Commonly Used CDM Tables Overview](#commonly-used-cdm-tables-overview)
- [ETL Basics](#ETL-Basics)
- [OHDSI Analysis Tools](#ohdsi-analysis-tools)
- [Data Science Handbook](#data-science-handbook)
- [Jupyter Notebooks and programming](#jupyter-notebooks-and-programming)
- [Recommended Trainings](#recommended-trainings)
- [Python, SQL, and R Programming Resources](#python-sql-and-r-programming-resources)
- [Analysis with SQL](#analysis-with-sql)
- [Analysis with R](#analysis-with-r)
- [Diversity, Equity, and Inclusion Resources](#diversity-equity-and-inclusion-resources)
- [REDCAP training resources] (#redcap-training-resources)

# OMOP CDM Basic Data Dictionary 
For a sample interactive OMOP data dictionary, please click on the image below:
[![OMOP Data Dictionary Thumbnail](https://dbjhu.github.io/DDthumbnail.png)](https://dbjhu.github.io/OMOPDD.html)
<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# Projects Best Suited for Observational Research and OHDSI Network Studies
![Source:  https://www.ohdsi.org/wp-content/uploads/2023/01/SOS-challenge-intro-24jan2023.pdf](AnalyticUseCases.png) 

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# (This is the exact same table as in the image above only in Markdown)

## Analytic Use Cases and Examples

| Analytic use case                     | Type                        | Structure                                                                                                               | Example                                                                                                                   |
|---------------------------------------|-----------------------------|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **Clinical characterization**         | Disease Natural History     | Amongst patients who are diagnosed with `<insert your favorite disease>`, what are the patient’s characteristics from their medical history? | Amongst patients with rheumatoid arthritis, what are their demographics (age, gender), prior conditions, medications, and health service utilization behaviors? |
|                                       | Treatment utilization       | Amongst patients who have `<insert your favorite disease>`, which treatments were patients exposed to amongst `<list of treatments for disease>` and in which sequence? | Amongst patients with depression, which treatments were patients exposed to SSRI, SNRI, TCA, bupropion, esketamine and in which sequence? |
|                                       | Outcome incidence           | Amongst patients who are new users of `<insert your favorite drug>`, how many patients experienced `<insert your favorite known adverse event from the drug profile>` within `<time horizon following exposure start>`? | Amongst patients who are new users of methylphenidate, how many patients experienced psychosis within 1 year of initiating treatment? |
| **Population-level effect estimation** | Safety surveillance         | Does exposure to `<insert your favorite drug>` increase the risk of experiencing `<insert an adverse event>` within `<time horizon following exposure start>`? | Does exposure to ACE inhibitor increase the risk of experiencing Angioedema within 1 month after exposure start? |
|                                       | Comparative effectiveness   | Does exposure to `<insert your favorite drug>` have a different risk of experiencing `<insert any outcome (safety or benefit)>` within `<time horizon following exposure start>`, relative to `<insert your comparator treatment>`? | Does exposure to ACE inhibitor have a different risk of experiencing acute myocardial infarction while on treatment, relative to thiazide diuretic? |
| **Patient level prediction**          | Disease onset and progression | For a given patient who is diagnosed with `<insert your favorite disease>`, what is the probability that they will go on to have `<another disease or related complication>` within `<time horizon from diagnosis>`? | For a given patient who is newly diagnosed with atrial fibrillation, what is the probability that they will go onto to have ischemic stroke in next 3 years? |
|                                       | Treatment response           | For a given patient who is a new user of `<insert your favorite chronically-used drug>`, what is the probability that they will `<insert desired effect>` in `<time window>`? | For a given patient with T2DM who start on metformin, what is the probability that they will maintain HbA1C <6.5% after 3 years? |
|                                       | Treatment safety             | For a given patient who is a new user of `<insert your favorite drug>`, what is the probability that they will experience `<insert adverse event>` within `<time horizon following exposure>`? | For a given patient who is a new user of warfarin, what is the probability that they will have GI bleed in 1 year? |

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

## Important Paper About Implementation of the OMOP CDM!
[Erica A Voss, Clair Blacketer, Sebastiaan van Sandijk, Maxim Moinat, Michael Kallfelz, Michel van Speybroeck, Daniel Prieto-Alhambra, Martijn J Schuemie, Peter R Rijnbeek, European Health Data & Evidence Network—learnings from building out a standardized international health data network, Journal of the American Medical Informatics Association, 2023;, ocad214](https://doi.org/10.1093/jamia/ocad214)

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# Data Content Ontology
![Dr. Rachel Richesson presents "Learning to Use EHR Data in Learning Health Systems"](https://img.youtube.com/vi/4uXqNLsiVuc/maxresdefault.jpg)

## Overview of Major Clinical Terminologies and Coding Systems

This document provides a detailed overview of several essential clinical terminologies and coding systems used in healthcare. Each system has a specific role and is crucial for standardized communication in healthcare settings. The information includes development history, usage, and updates of these systems.

For more in-depth information, links to the respective official websites are provided.

### SNOMED Clinical Terms (SNOMED CT)
- **Development:** Originally by the College of American Pathologists, now under SNOMED International.
- **Adoption:** Used in over 50 countries.
- **Concepts:** Over 340,000 active concepts in 19 hierarchies.
- **Usage:** Encodes clinical information including diseases, findings, and procedures.
- **Updates:** Biannual, with more frequent updates planned.
- **More Information:** [SNOMED International](https://www.snomed.org/snomed-ct)

### Logical Observation Identifiers Names and Codes (LOINC)
- **Developer:** Regenstrief Institute.
- **Function:** Identifiers for laboratory and clinical observations.
- **Content:** Over 90,000 terms.
- **Collaboration:** With SNOMED CT for coded content development.
- **Updates:** Biannual.
- **More Information:** [LOINC](https://loinc.org)

### RxNorm
- **Developer:** National Library of Medicine (NLM).
- **Function:** Standard nomenclature for medications.
- **Integration:** Links to various drug vocabularies.
- **Access:** Requires UMLS user license for proprietary content.
- **More Information:** [RxNorm - NLM](https://www.nlm.nih.gov/research/umls/rxnorm)

### International Classification of Disease (ICD)
- **Endorsement:** World Health Organization (WHO).
- **Versions:** ICD-10 widely used with national extensions; ICD-11 adopted for future use.
- **Purpose:** Epidemiology, health management, clinical purposes.
- **Updates:** Annual, freely available.
- **More Information:** [WHO ICD](https://www.who.int/classifications/icd)

### Current Procedural Terminology (CPT)
- **Developer:** American Medical Association (AMA).
- **Use:** Encoding of medical services and procedures in the USA.
- **Categories:** Three categories of codes.
- **Requirement:** License from AMA for use.
- **More Information:** [CPT - AMA](https://www.ama-assn.org/practice-management/cpt)

### Human Phenotype Ontology (HPO)
- **Function:** Bioinformatic resources for human diseases and phenotypes analysis.
- **Components:** Phenotype vocabulary, disease-phenotype annotations, algorithms.
- **Applications:** Genomic interpretation, gene-disease discovery, precision medicine.
- **Content:** Over 13,000 terms in 5 hierarchies.
- **Availability:** Freely available, multiple releases per year.
- **More Information:** [Human Phenotype Ontology](https://hpo.jax.org)

### Unified Medical Language System (UMLS)
- **Initiation:** By the US National Library of Medicine in 1986.
- **Goal:** To aid in the retrieval and integration of electronic biomedical information.
- **Challenge Addressed:** Different vocabularies expressing the same information differently.
- **Availability:** Free, but requires a license due to additional licensing requirements of some contents.
- **More Information:** [UMLS - NLM](https://www.nlm.nih.gov/research/umls)

### Ontology Mapping in BioPortal Applications
- **Process:** Finding the closest match of a code from one ontology in another.
- **Matching:** Exact equivalence is rare; approximate matching is common.
- **Challenges:** Labor-intensive and requires understanding the maps' nature and limitations.
- **Alternative Approach:** Mapping multiple ontologies to a central core terminology, as used by the OHDSI consortium.
- **More Information:** [BioPortal](https://bioportal.bioontology.org)

    <div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

https://www.healthit.gov/isa/section-i-vocabularycode-setterminology-standards-and-implementation-specifications

## OMOP Domains by Source to Standard Vocabulary
```mermaid
graph LR
    ICD9("ICD9") -->|Transformation to OMOP CDM| SNOMED("STANDARD<br>Vocabulary Concept Code<br>SNOMED")
    ICD10("ICD10") -->|Transformation to OMOP CDM| SNOMED
```
<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>


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

  <div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>


## Incremental Loading

Incremental loading in the context of OHDSI refers to the process of adding new or updated data to an existing OHDSI database without the need to completely rebuild or refresh the entire dataset. This can be particularly useful for large datasets where full loads can be time-consuming and inefficient. The process involves extracting only the changes since the last load and then transforming and loading this delta of data into the existing OMOP Common Data Model (CDM) used by OHDSI tools.

For instance, in the development of an ETL (Extract, Transform, Load) process for the bulk and incremental load of German patient data into the OMOP CDM using FHIR as referenced by OHDSI, it suggests that the incremental loading is an essential part of keeping the database up-to-date in an efficient manner​. [OHDSI Symposium Showcase #44](https://ohdsi.org/2021-global-symposium-showcase-44/#:~:text=,Reinecke%2C%20Michele%20Zoch%2C%20Martin%20Sedlmayr)

This group alos described a [Near Real-Time Incremental OMOP-CDM ETL System](https://www.ohdsi.org/wp-content/uploads/2021/09/14-abstract-lee.pdf)

This is also described by Dr. DuWayne Willett, CMIO of UTSW, at around minute 30 of this video:

[![OHDSI Symposium Presentation](http://img.youtube.com/vi/DPatSxFkIpI/0.jpg)](https://www.youtube.com/watch?v=DPatSxFkIpI "OHDSI Symposium Presentation by Dr. DuWayne Willett")

...and in this OHDSI symposium presentation: ![OHDSI Symposium Presentation](https://www.ohdsi.org/wp-content/uploads/2023/10/10-Willett-Poster.png).

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>


## The Collaboration Process 
### This is just an example of the kinds of diagrams we can make in Mermaid for our workflows

```mermaid
flowchart TD
    A[Person A receives a research request]
    B[Person/group B sets up a meeting]
    C[Iterative biomedical query mediation process begins]
    D[Project outline is created and signed off by all parties]
    E[Voucher/payment/estimate is produced including resource and timeframe]
    F[Department head reviews/signs off]
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
<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>


## Current CDM
![CDM54 Image](https://github.com/DBJHU/DBJHU.github.io/blob/main/cdm54.png)

*Source: [OHDSI Common Data Model](https://ohdsi.github.io/CommonDataModel/index.html)*

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>


[Interactive (Select) OMOP Data Dictionary](https://github.com/DBJHU/DBJHU.github.io/blob/main/SelectOMOPDataDictionaryInteractivev2.html)

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# Commonly Used CDM Tables Overview
The OMOP common data model (CDM) is a relational database made up of different tables that relate to each other by foreign keys (XXXX_ID values; e.g., PERSON_ID or PROVIDER_ID). The OMOP tables in your data export are as follows:

| Table              | Description |
|--------------------|---------------------|
| Person             | Contains basic demographic information describing a participant, including biological sex, birth date, race, and ethnicity. |
| Visit_occurrence   | Captures encounters with healthcare providers or similar events. Contains the type of visit a person has (outpatient care, inpatient care, or long-term care), as well as the date and duration information. Rows in other tables can reference this table, for example, condition_occurrences related to a specific visit. |
| Condition_occurrence | Indicates the presence of a disease or medical condition stated as a diagnosis, a sign, or symptom, which is either observed by a provider or reported by the patient. |
| Drug_exposure      | Captures records about the utilization of a medication. Drug exposures include prescription and over-the-counter medicines, vaccines, and large-molecule biologic therapies. Radiological devices ingested or applied locally do not count as drugs. Drug exposure is inferred from clinical events associated with orders, prescriptions written, pharmacy dispensing, procedural administrations, and other patient-reported information. |
| Measurement        | Contains both orders and results of a systematic and standardized examination or testing of a participant or participant's sample, including laboratory tests, vital signs, quantitative findings from pathology reports, etc. |
| Procedure_occurrence | Contains records of activities or processes ordered by or carried out by a healthcare provider on the patient to have a diagnostic or therapeutic purpose. |
| Observation        | Captures clinical facts about a person obtained in the context of an examination, questioning, or a procedure. Any data that cannot be represented by another domain, such as social and lifestyle facts, medical history, and family history, are recorded here. |
| Device_exposure    | Captures information about a person's exposure to a foreign physical object or instrument which is used for diagnostic or therapeutic purposes. Devices include implantable objects, blood transfusions, medical equipment and supplies, other instruments used in medical procedures, and material used in clinical care. |
| Death              | Contains the clinical events surrounding how and when a participant dies. |

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# OMOP Data Quality
[The Book of OHDSI - Chapter 15: Data Quality](https://ohdsi.github.io/TheBookOfOhdsi/DataQuality.html)

[Kahn MG, Callahan TJ, Barnard J, Bauck AE, Brown J, Davidson BN, Estiri H, Goerg C, Holve E, Johnson SG, Liaw ST, Hamilton-Lopez M, Meeker D, Ong TC, Ryan P, Shang N, Weiskopf NG, Weng C, Zozus MN, Schilling L. A Harmonized Data Quality Assessment Terminology and Framework for the Secondary Use of Electronic Health Record Data. EGEMS (Wash DC). 2016 Sep 11;4(1):1244. doi: 10.13063/2327-9214.1244. PMID: 27713905; PMCID: PMC5051581.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5051581/)



# ETL Basics
https://www.ohdsi.org/wp-content/uploads/2019/09/OMOP-Common-Data-Model-Extract-Transform-Load.pdf
https://ohdsi.github.io/TheBookOfOhdsi/ExtractTransformLoad.html

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

## ETL STEPS 
1. **Dataset profiling and documentation**
    - Create data model documentation, sample data, data dictionaries, code lists, and other relevant information (23-Aug)
    - Execute database profiling scan (WhiteRabbit) on source database
    - Prepare mapping approach/documents based on scan reports from database profiling scan

2. **Generation of the ETL Design**
    - Mapping workshop with all relevant parties to:
        1. Understand the source
        2. Define the scope of source data to be transformed
        3. Define acceptance criteria for OMOP output
        - Output: draft mapping document
    - Finalize mapping document:
        - Integrate all notes/documentation from workshop
        - Work through mappings and verify, update, fill in gaps
        - Meetings/emails with data contact/technical contact (TC) as needed

3. **Source Data Integrations and Semantic Mapping**
    - Source Code mapping:
        - Identify which codes are already mapped to standard vocabulary
        - Identify code types for codes that need to be mapped
        - Translation of code description/phrases to English, if/as needed
        - Create proposed code mappings
    - Generate mappings for data coming out of flowsheets (together with consortium)
    - Review/approval of code mappings, often done by medical experts affiliated with Data Owner (DO). 
    - Identify medical imaging available and define mappings to Imaging Extension
    - Identify waveform data available and map using consortium-defined guidelines
    - Use OHNLP to extract OMOP data from unstructured sources

4. **Technical architecture design**
    - Continuous Integration, Continuous Deployment (CI/CD):
        - Decide on ETL dev/deployment flow
        - Put version control mechanisms in place
    - OHDSI Ecosystem:
        - Evaluate infrastructure needed
        - Create infrastructure design documentation

5. **Technical ETL Development**
    - Implement ETL (Preferred Language/Structure?)
    - Update ETL based on testing/QA/feedback (8, 9)

6. **Setting up of Infrastructure**
    - Deploy core servers and associated services based on infrastructure design in (4)

7. **Installation of the OHDSI tools**
    - Install and configure all software (database server, Achilles/DQD/Ares, Atlas/WebAPI, R Studio server, HADES, notebooks/tooling related to analytics, and any other software to suit a site’s specific needs).

8. **ETL Testing and Validation**
    - ETL Execution:
        - Test ETL using sample/development data (with limited external data access)
        - Test ETL using DO data (with full external data access)
        - Verify and document QA
        - Submit Achilles/DQD/AresIndexer results to central location regularly
    - ETL Development Planning and Management:
        - Review ETL testing and progress (TCs/meetings)

9. **Data Quality Assessment**
    - QA/Acceptance testing:
        - Evaluate accuracy and completeness of mapping
        - Review and approval by DO

10. **Documentation**
    - Mapping Documentation and Themis Checks
    - Transformation/Technical Documentation

11. **Project Management Througout**
    - Organization of tasks, milestones, and follow-up

# OHDSI Analysis Tools
R, SQL, Python, or any preferred data analysis software. Examples provided below are for R and SQL.
[The Book of OHDSI Chapter 9] (https://ohdsi.github.io/TheBookOfOhdsi/SqlAndR.html) provides an overview of analysis of OHDSI data in R and SQL; note that you will not be able to avail yourselves of OHDSI software tools when analyzing your exported data for the reason explained above.

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

## Data Science Handbook
[Open, rigorous and reproducible research: A practitioner’s handbook](https://datascience.stanford.edu/programs/stanford-data-science-scholars-program/data-science-handbook) 
From Standord Data Science

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

## Data Management Tools and resources
DMP Tool:  https://dmptool.org/ 
https://sharing.nih.gov/data-management-and-sharing-policy/planning-and-budgeting-for-data-management-and-sharing/writing-a-data-management-and-sharing-plan#after


## Programming Resources:  Jupyter Notebooks, Python, SQL, and R Programming Resources

- [Project Jupyter](https://jupyter.org/)
- [What is the Jupyter Notebook?](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html)
- [NIAID NIH Informatics resources](https://bioinformatics.niaid.nih.gov/resources)

Software Carpentry is a website that provides free online lessons to researchers wanting to enhance their programming skills for data analysis. This website offers free online lessons on a variety of useful topics including:

- [Programming with Python](http://swcarpentry.github.io/python-novice-inflammation/)
- [Programming with R](http://swcarpentry.github.io/r-novice-inflammation/)
- [Databases and SQL](http://swcarpentry.github.io/sql-novice-survey/)

Additional resources:

- [DataCamp](http://www.datacamp.com/)
- [Khan Academy](https://www.khanacademy.org/computing/computer-programming/sql/sql-basics/v/welcome-to-sql)
- [Codecademy - Learn Python 2](https://www.codecademy.com/learn/learn-python)
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
- [R for Data Science](https://r4ds.had.co.nz/)
- [Introduction to Programming (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.1)
- [Python Programming (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.2)
- [Data Analysis with Python and Pandas (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.3)
- [Data Visualization with Python (NIAID, NIH)](https://bioinformatics.niaid.nih.gov/resources - 70.3.4)
- [Source:NIH All of US Study](https://support.researchallofus.org/hc/en-us/articles/360039690191-Jupyter-Notebooks-and-programming)

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# OHDSI Resources
Hello! Please familiarize yourself with the following tools and resources which will help you throughout this course and your OHDSI journey.

Check out the [**OHDSI Forums**](https://forums.ohdsi.org/) *Introduce yourself on the "Welcome to OHDSI" thread.*

Bookmark [**The Book of OHDSI**](https://ohdsi.github.io/TheBookOfOhdsi/)

Check out [**OHOP CDM FAQ**](https://ohdsi.github.io/CommonDataModel/faq.html)

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

<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# Special Topic:  Cinical Registries Using OHDSI

[![OHDSI and Clinical Registries: Sanity for Health Systems (Aug. 22 Community Call)](http://img.youtube.com/vi/DPatSxFkIpI/0.jpg)](https://youtu.be/DPatSxFkIpI?si=VOqE4VTlzIcxuWdP)

[Clinical Registries in OHDSI - September 2022](https://www.ohdsi.org/wp-content/uploads/2022/09/OHDSI-Clinical_Registries.pdf)

# Special topic: SSSOM

https://www.ohdsi.org/wp-content/uploads/2023/10/Talapova-Polina_Mapping_of_Critical_Care_EHR_Flowsheet_data_to_the_OMOP_CDM_via_SSSOM_2023symposium-Polina-Talapova.pdf

Matentzoglu N, Balhoff JP, Bello SM, Bizon C, BrushM, Callahan TJ et al. A Simple Standard
for Sharing Ontological Mappings (SSSOM). Database. 2022. 2022:baac035, DOI:
10.1093/database/baac035.

Mapping Commons. SSSOM: Simple Standard for Sharing Ontological Mappings. Wiki [Internet].
Available from: https://mapping-commons.github.io/sssom/about.

Mapping Commons. SSSOM: Simple Standard for Sharing Ontological Mappings. GitHub
[Internet]. Available from: https://github.com/mapping-commons/sssom.

https://www.w3.org/2004/02/skos/

# Recommended Trainings
## OHDSI Community
  **Broadsea3.0**  
  By: Lee Evans  
 [![Broadsea 3.0](https://img.youtube.com/vi/CNlsZzY7VrM/0.jpg)](https://youtu.be/CNlsZzY7VrM)


<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

## Tufts Bridge2AI Standards Module
- **June 15, 2023:**  
  **Data Quality Dashboard**  
  By: Jared Houghtaling  
  [![Data Quality Dashboard](https://img.youtube.com/vi/O2L1x0Sv3lc/0.jpg)](https://youtu.be/O2L1x0Sv3lc)

- **July 6, 2023:**  
  **Data Quality Dashboard output demo**  
  By: Jared Houghtaling  
  [![Data Quality Dashboard output demo](https://img.youtube.com/vi/qYDq5-dg-io/0.jpg)](https://youtu.be/qYDq5-dg-io)

- **July 13, 2023:**  
  **Achilles output demo**  
  By: Jared Houghtaling  
  [![Achilles output demo](https://img.youtube.com/vi/bIRQVgcnAwI/0.jpg)](https://youtu.be/bIRQVgcnAwI)

- **July 27, 2023:**  
  **Flowsheet follow-up**  
  By: Polina Talapova & Jared Houghtaling  
  [![Flowsheet follow-up](https://img.youtube.com/vi/3cTT2XJZslI/0.jpg)](https://youtu.be/3cTT2XJZslI)

- **August 3, 2023:**  
  **OMOP Standardized Vocabularies - Part 1**  
  By: Jared Houghtaling and Polina Talapova  
  [![OMOP Standardized Vocabularies - Part 1](https://img.youtube.com/vi/4xnH7-oJxyo/0.jpg)](https://youtu.be/4xnH7-oJxyo)

- **August 17, 2023:**  
  **OMOP Standardized Vocabularies - Part 2**  
  By: Polina Talapova  
  [![OMOP Standardized Vocabularies - Part 2](https://img.youtube.com/vi/1J7ISUASx6k/0.jpg)](https://youtu.be/1J7ISUASx6k)

- **August 24, 2023:**  
  **How to download and set-up a DDL (Demo)**  
  By: Jared Houghtaling  
  [![How to download and set-up a DDL (Demo)](https://img.youtube.com/vi/x9W3sa1xGoQ/0.jpg)](https://youtu.be/x9W3sa1xGoQ)

- **August 31, 2023:**  
  **Demo of WhiteRabbit and RabbitInAHat**  
  By: Jared Houghtaling  
  [![Demo of WhiteRabbit and RabbitInAHat](https://img.youtube.com/vi/gu1fQVwkBo8/0.jpg)](https://youtu.be/gu1fQVwkBo8)

- **September 7, 2023:**  
  **ARES usefulness for ETL at Tufts**  
  By: Jared Houghtaling  
  [![ARES usefulness for ETL at Tufts](https://img.youtube.com/vi/Czox3WT1pDM/0.jpg)](https://youtu.be/Czox3WT1pDM)

- **September 14, 2023:**  
  **Google form introduction for site progress tracking**  
  By: Jared Houghtaling  
  [![Google form introduction for site progress tracking](https://img.youtube.com/vi/ntZwikqhIcM/0.jpg)](https://youtu.be/ntZwikqhIcM)

- **September 21, 2023:**  
  **Sample ETL Process**  
  By: Jared Houghtaling  
  [![Sample ETL Process](https://img.youtube.com/vi/uX289BrzXM4/0.jpg)](https://youtu.be/uX289BrzXM4)

**October 12, 2023:**  
  **Google Form for Site Progress Tracking**  
  With Jared Houghtaling and Andrew Williams  
  [![Google Form for Site Progress Tracking](https://img.youtube.com/vi/oTP6ISo8FWc/0.jpg)](https://youtu.be/oTP6ISo8FWc)

- **October 26, 2023:**  
  **Review and Prioritization of DQD Results, and Discussion of DQD Issue Severity**  
  With Jared Houghtaling  
  [![Review and Prioritization of DQD Results, and Discussion of DQD Issue Severity](https://img.youtube.com/vi/dJr5tkm-Ex4/0.jpg)](https://youtu.be/dJr5tkm-Ex4)

- **November 2, 2023:**  
  **Principles of Mapping and Vocab Gaps Identification**  
  With Polina Talapova  
  [![Principles of Mapping and Vocab Gaps Identification](https://img.youtube.com/vi/jOKzb3x6hmo/0.jpg)](https://youtu.be/jOKzb3x6hmo)

- **November 9, 2023:**  
  **Usagi & STCM Demo**  
  With Polina Talapova & Jared Houghtailing  
  [![Usagi & STCM Demo](https://img.youtube.com/vi/hNhph-elrp4/0.jpg)](https://youtu.be/hNhph-elrp4)


<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>

# Diversity, Equity, and Inclusion Resources

- [How racial biases in medical algorithms lead to inequities in care | PBS News Weekend](https://www.pbs.org/newshour/show/how-racial-biases-in-medical-algorithms-lead-to-inequities-in-care)
- [AI Reveals its Biases by Generating What it Thinks Professors Look Like | PetaPixel](https://petapixel.com/2023/05/04/ai-reveals-its-biases-by-generating-what-it-thinks-professors-look-like/)
- [Does “AI” stand for augmenting inequality in the era of covid-19 healthcare? | The BMJ](https://www.bmj.com/content/372/bmj.n304)
- [The AUC Data Science | Initiative (aucenter.edu)](https://datascience.aucenter.edu/)
- [ReCode-Report.pdf (data.org)](https://datascience.aucenter.edu/)
- [ADDI Researcher Roundtable: The Importance of Diversity in Dementia Research on Vimeo](https://vimeo.com/799212327?forcedownload=true&_=4007b451dfc8424fa5226c4615e147ea)
- [Advancing Antiracism, Diversity, Equity, and Inclusion in STEMM Organizations: Beyond Broadening Participation |The National Academies Press](https://nap.nationalacademies.org/catalog/26803/advancing-antiracism-diversity-equity-and-inclusion-in-stemm-organizations-beyond)
- [Data Literacy: The Composition Effect | Education | St. Louis Fed (stlouisfed.org)](https://www.stlouisfed.org/education/the-composition-effect)
- [A lecture by Pilar Ossorio at MLHC Professor of Law and Bioethics at the University of Wisconsin Law School](https://www.youtube.com/watch?v=DzGSlWu4Lj0&list=PLRqwW7v078fYdZFpf43d0NBh4hiGCRtfV&index=6)
- [This paper by Dunkelau and Leuschel that summarizes Fairness-aware Machine Learning](https://www.phil-fak.uni-duesseldorf.de/fileadmin/Redaktion/Institute/Sozialwissenschaften/Kommunikations-_und_Medienwissenschaft/KMW_I/Working_Paper/Dunkelau___Leuschel__2019__Fairness-Aware_Machine_Learning.pdf)
- [Paper by Gichoya et al about minimixing bias in AI](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10546443/)
- [A conversation with Cathy O’Neil, author of the critically acclaimed Weapons of Math Destruction - YouTube](https://www.youtube.com/watch?v=1QlIbed_Hwg)
- [Nicole G. Weiskopf (NYU) and Carolyn Thompson (UCSD) – Bias in EHR - YouTube](https://youtu.be/8V-yO7GNNlw?feature=shared)
- [This Obermeyer et al paper on dissecting racial bias in an algorithm used to manage the health of populations - Science, 2019](https://science.sciencemag.org/content/366/6464/447)
- [Fair ML Keynote talk + Microsoft talk + slides - Science, 2019](https://science.sciencemag.org/content/366/6464/447)
- [Maria Hightower, M.D., M.B.A., MPH Chief Digital Technology officer of the University of Chicago Medicine comments on the racial bias in AI and the algorithm described above - Science, 2019](https://science.sciencemag.org/content/366/6464/447)
- [How scientists are subtracting race from medical risk calculators - Science, 2021](https://science.sciencemag.org/content/366/6464/447)
- [Race After Technology, by Ruha Benjamin [Professor of African American studies at Princeton University], summarizes how technology [from data collection, data imputation, government policy, etc] can play a role in different outcomes in society - Science](https://science.sciencemag.org/content/366/6464/447)

# REdCAP Training Resouces
## This is the main REDCap training page: [REDCap Resources](https://projectredcap.org/resources/)
From University of Colorado, below are excellent REDCap resources: [University of Colorado REDCap Resources](https://cctsi.cuanschutz.edu/resources/informatics/redcap-resources)

## Best Practices

### Best Practices
- [Background Information](https://redcap.ucdenver.edu/surveys/?s=RJ7DP8K9DL): Learn more about the background of REDCap at UC Denver, general policies for use, and some REDCap best practices (video)
- [COMIRB Template](https://redcap.ucdenver.edu/surveys/?s=FMWPDEH7X3) (user guide)
- [Best Practices](https://redcap.ucdenver.edu/surveys/?s=4JHTMJ3Y4P) (user guide)
- [18 HIPAA Identifiers & PHI (University of Maryland)](https://redcap.ucdenver.edu/surveys/?s=F9YD7CE8RW) (user guide)

## Project Setup

### Project Setup
- [Login and Project Creation](https://redcap.ucdenver.edu/surveys/?s=LYLJ7X3CYD): Learn how to log in to your REDCap account and create a new project (video)
- [Project Setup Page](https://redcap.ucdenver.edu/surveys/?s=L4KD8LCP8W): Explore the project home, project setup, other functionality, and project revision pages. Learn how to customize the settings for your projects, set user rights, use data access groups, and move your project to Production (video)
- [Online Designer](https://redcap.ucdenver.edu/surveys/?s=7FM7YD8Y9E): Learn about the basic steps in designing your project. Learn how to set up forms; create a new field; validate fields; code multiple choice questions; use yes/no and true/false fields; create slider fields; and how to use file upload fields, descriptive fields, and section headers (video)
- [Online Designer - Advanced Features](https://redcap.ucdenver.edu/surveys/?s=9M3Y4F3NY7): Learn how to use advanced features in the Online Designer such as branching logic, calculated fields, matrices, piping, and the data dictionary. Review some best practices in form creation (video)
- [Longitudinal Database](https://redcap.ucdenver.edu/surveys/?s=8D3C9L7PDE): Learn about the longitudinal data collection set up and how it varies from a standard or classic data collection instrument. Learn how to define events and assign forms to specific events, use the scheduling module, and advanced calendar features available only in longitudinal studies (video)
- [Repeating Forms](https://redcap.ucdenver.edu/surveys/?s=6D3C7N4FEM): Learn how to use repeating forms and events (video)

## Advanced Form Design

### Advanced Project Design
- [Action Tags](https://redcap.ucdenver.edu/surveys/?s=3YM7C9D4DE): Learn how to use the most popular and powerful action tags (video)
- [Action Tags List](https://redcap.ucdenver.edu/surveys/?s=7D4C9M7NY3): List of all action tags with descriptions (user guide)
- [Alerts and Notifications](https://redcap.ucdenver.edu/surveys/?s=8D4N7Y3FM9): Learn about the alerts and notifications feature (video)
- [Calculations](https://redcap.ucdenver.edu/surveys/?s=6D3M7Y9F4C): Learn how to use simple calculations, if/then statements, nest calculations, and datediff calculations (video)
- [Field Embedding](https://redcap.ucdenver.edu/surveys/?s=7M9C4D8FNY): Explore how to use the field embedding feature to format data entry and survey forms (video)
- [Formatting REDCap Forms with HTML](https://redcap.ucdenver.edu/surveys/?s=6D3C8M9Y7F) (user guide)
- [Logic Guide](https://redcap.ucdenver.edu/surveys/?s=7F9M3C4D8Y): Learn how to format logic in REDCap (user guide)
- [Smart Variables](https://redcap.ucdenver.edu/surveys/?s=8D7F9M3C4Y): Learn how to use smart variables in REDCap (video)

## Data Management

### Data Management
- [Data Entry](https://redcap.ucdenver.edu/surveys/?s=7D9M3F4C8Y): Learn how to add new records, edit existing records, use advanced data entry features, and navigate between records (video)
- [Missing Data](https://redcap.ucdenver.edu/surveys/?s=3F7D9M4C8Y): Set specific missing data codes for your entire project (video)
- [Advanced Features](https://redcap.ucdenver.edu/surveys/?s=8D7M3F9C4Y): Learn how to use some advanced REDCap features, including the randomization feature, the logging feature, the field comment log, the data import tool, and the data quality tool (video)
- [Data Imports](https://redcap.ucdenver.edu/surveys/?s=9F7D3M4C8Y): A detailed look at use the import tool to import data from another source (video)
- [Randomization](https://redcap.ucdenver.edu/surveys/?s=7M9D3F4C8Y): Learn how to use the randomization feature (video)
- [Reports and Exports](https://redcap.ucdenver.edu/surveys/?s=8F9D3M4C7Y): Learn how to create a report, review basic statistics and charts, and export a report or full data set (video)
- [Public Reports](https://redcap.ucdenver.edu/surveys/?s=9D7F3M4C8Y): Learn how to make reports accessible with a public link (video)

## Surveys

### Surveys
- [Surveys](https://redcap.ucdenver.edu/surveys/?s=8F9M3D4C7Y): Learn how to enable surveys, the benefits of using surveys, setting up your survey, and the different ways you can distribute both initial and follow-up surveys (video)
- [Survey Login](https://redcap.ucdenver.edu/surveys/?s=3F8D7M4C9Y): Learn how to use the survey login feature (video)
- [Survey Queue](https://redcap.ucdenver.edu/surveys/?s=4F8D3M7C9Y): A deep dive into using the survey queue (video)
- [PDF Auto-Archiver and e-Consent](https://redcap.ucdenver.edu/surveys/?s=7F3D8M9C4Y): Use REDCap's e-Consent framework to consent participants and save PDFs of the consent (video)
- [Twilio](https://redcap.ucdenver.edu/surveys/?s=9F3D7M4C8Y): Learn how to use Twilio to send your survey invitations via text message or allow participants to take the survey via voice call (video)
- [Twilio Guide](https://redcap.ucdenver.edu/surveys/?s=8F7D9M3C4Y) (user guide)

## Optional Modules

### Optional Modules
- [Double Data Entry](https://redcap.ucdenver.edu/surveys/?s=4F7D3M9C8Y): Learn how to use REDCap's Double Data Entry module (video)
- [Mobile App Guide](https://redcap.ucdenver.edu/surveys/?s=3F8D7M4C9Y) (user guide)
- [Multi-Language Management Manual](https://redcap.ucdenver.edu/surveys/?s=8D3F7M4C9Y) (user guide)

## Updates and Additional Features

### Updates and Additional Features
We hold a REDCap user group meeting for our active users after every major upgrade twice a year to discuss the new features. You can watch the recordings of our previous group videos on Vimeo:
- [User Group Meeting 2/23/2023](https://vimeo.com/123456789): MyCap integration, automated invitations with repeating surveys, file repository improvements
- [User Group Meeting 7/19/2022](https://vimeo.com/123456789): Multi-language management updates, survey start time and survey duration, FAQ updates
- [User Group Meeting 3/9/2022](https://vimeo.com/123456789): Multi-language management, public reports, @IF form display logic
- [User Group Meeting 8/11/2021](https://vimeo.com/123456789): Project dashboards, smart variables, smart charts, and smart tables
- [User Group Meeting 3/31/2021](https://vimeo.com/123456789): @CALCDATE/@CALCTEXT and special functions
- [User Group Meeting 8/26/2020](https://vimeo.com/123456789): eConsent, field embedding

## Frequently Asked Questions

### Frequently Asked Questions
- **Can I add users to my project?**
  Anyone creating projects should attend a tutorial (see schedule on Tutorials page) which focuses on project creation and REDCap use policies. If you have attended a

 tutorial you can request limited accounts for others who will not be designing/managing projects but only doing data entry, data export, etc. To request an account email the REDCap administrator with the person's name and work email address. By doing this you are also taking responsibility for training them.
  
- **Why is the Participant ID the first field in the project?**
  When you set up a REDCap database your record identifier e.g. Participant ID must be the first field on the first form so that REDCap will link all following data on all forms for that record. There is no need to repeat the record identifier in each form.

- **How do I code categorical variables?**
  If your categorical variable has numeric response options be sure to assign a value that is the same number to avoid confusion in analysis. For example if the question is "How many times did you ...." and the options are 0,1,2,3,4,5 you should assign values of 0-5 (note: you cannot use the auto-assign feature of REDCap because it will start with 1).

- **When should I use the dropdown field type?**
  Use dropdown field types instead of radio buttons for categorical variables on your data entry forms. REDCap allows you to type the first character of a label to select that option in a dropdown which is much easier than having to individually select each radio button with your mouse.

- **How do I tell the difference between a radio and checkbox field?**
  There is a visual cue to tell you whether a field is a radio button (single option) or a checkbox (choose all that apply). Radio buttons are round, checkboxes are square.

- **How do I format branching logic or a calculation with checkbox fields?**
  Checkbox or "choose all that apply" fields are coded slightly differently from other categorical fields such as radio or dropdown. In those each option is set to equal a unique value e.g. 1=red, 2=blue, 3=green. Because any or all of the checkbox field options can be selected, each option is treated as a separate field that is either checked or unchecked (coded 1 or 0). In your exported dataset you will see that each option has become a separate variable with the number of the option as part of the variable name e.g. color(1), color(2), color(3). When using options from a checkbox field in a calculation or in branching logic instead of writing "color = 3" for example you need to write "color(3)=1" meaning that option 3 of the variable "color" has been selected.

- **How do I hide a section header field type using branching logic?**
  Section header fields follow the branching logic for *all* fields until the next section header so to hide a section header all fields until the next section header must also be hidden.

- **How do I format greater than/less than conditions in my branching logic?**
  When using a greater than/less than (><) condition in branching logic don't put quotation marks around the value as you normally would when using equal to.

- **How do I test branching logic and calculated fields in my form or survey?**
  To test branching logic or calculated fields enter a test record into your database or survey. These functions do not work on the Preview screen. You can remove all test records when you move to production.

- **How do I add an “other” option in a multiple field question that a participant can write in their answer?**
  To include an "Other" option in a multiple choice question that will allow respondents to write in an answer, add a text field that is only displayed when the Other option is selected. If you want it to appear right next to the “Other” option in the multiple choice question you’ll need to use field embedding. You’ll follow the step above, but then additionally you’ll need to tell REDCap to embed the field with the multiple choice answers—this is done by putting the variable name in { } curly brackets where you want it to appear.

- **Can I base a calculated field off another calculated field?**
  If you are using calculated fields, avoid creating second-level calculations, i.e. using the results of a calculation as part of another calculation. These fields will not reliably calculate - even though values may appear in the field onscreen, the field may be blank in your exported dataset. Keep in mind the general recommendation to do calculations as part of analysis and keep only raw data in your REDCap database.

- **Why isn’t my calculation saved?**
  If you add a calculated field after you have collected the data used in the calculation you will need to resave the form containing the calculation to trigger REDCap to perform the calculation and populate the field. To update them all at once, you can go to Data Quality under Applications on the sidebar and run Rule H. It will show all fields where the calculated values don’t match what is saved and give you the option to update them all.

- **Can I display an image in my form or survey?**
  To display an image on your data entry form or survey use the descriptive text field type which has a field upload feature. For more information please see [Formatting REDCap Forms with HTML](https://redcap.ucdenver.edu/surveys/?s=6D3C8M9Y7F).

- **Can I customize the appearance of my form or survey?**
  REDCap allows some customization of form appearance using HTML code. These include font size, font color, and spacing/indentation of field label text.

- **How do I set up the event grid in a longitudinal project?**
  When setting up a Longitudinal project event grid, if you are not using the Scheduling module, you don't need to set specific "days offset" but you still need to enter something to tell REDCap the order of your events. If you leave all zero's REDCap will put your events in alphabetical order. So you can just put 1, 2, 3, etc. You may also want to use increments of 5's in case you later need to insert a new event.

- **What happens if I accidently delete an event?**
  In a Longitudinal Model database if you accidentally delete an event your data will not be lost just hidden. When you restore the event with the assigned forms the data will also be restored.

- **Can I change the coding of my fields while in production?**
  Although you can make changes to your project fields after moving your project to Production, keep in mind that changes to coding for categorical fields will impact your existing data. For example if you have a field with Yes/No responses that are coded 10 and you change these to 21 then what was originally coded as Yes will now be No - since you have changed the meaning of the value 1.

- **How do I test my database before moving to production?**
  It's a good idea to test your database or survey before moving to Production by entering a few records of either real or fake data. When moving to Production you can choose to keep or delete these records.

- **How do I review the changes I have made before submitting?**
  Before submitting post-production changes for review, you can see whether they will cause any problems by selecting the "view a detailed summary of all drafted changes" link located next to the Submit Changes for Review button.

- **Will I lose data if submitting changes while in production?**
  Project changes made after moving to production must be reviewed prior to being implemented to reduce the risk of data corruption due to a change. However, if you make a change that cannot possibly impact existing data (e.g. create a new field), once you submit the change for approval it will be approved automatically - you won't have to wait for manual review and approval by the administrator. To view whether you changes create potential issues while you're in draft mode, go to the "view a detailed summary of all drafted changes" link.

- **What should I do if I need to make significant changes while in production?**
  If your project is in production and you need to make several changes, consider making a copy of the project (which will be in development), making the changes there, then using the data dictionary to implement the changes all at once in the production project. Alternatively, you can ask the REDCap administrator to move your project back to development.

- **How do I combine my instruments into a single survey?**
  If you have multiple instruments that you want to send out as a single survey, combine them onto a single REDCap form. You can insert page breaks between instruments using the Section Header field type.

- **How do I hide calculated fields in a survey?**
  If you are including survey responses in a calculation but don't want the respondent to see the calculations, create a separate data entry form and put the calculation fields there. The calculations will be triggered when the survey is submitted.

- **How do I schedule a survey to be sent at a specific date/time?**
  Using the "automated invitations" feature you can schedule survey to be sent at a specific date/time as well as based on a specific response to a previous form or survey. See detailed instructions on how to do this in the Help/FAQ page.

- **How can I set up surveys to go out automatically?**
  If you are using online surveys, you can schedule them to be sent automatically at certain dates or based on specified conditions being met. See Automated Invitations in the Online Designer for instructions.

- **How do I personalize an email invitation?**
  REDCap allows you to customize field labels or survey invitations using "piping". This means you can insert the response to one field e.g. first name into the label of another field or into a survey invitation text. To do this just put the variable name in square brackets where you want the customized text. For example if the

 respondent's first name is in a variable called "fname" you can add it to the label of another field like this: [fname] what is your favorite color? Similarly, when you write a survey invitation you can use: Dear [fname], please complete the attached survey. Whatever name has been entered in the field fname will appear in place of the variable name.

- **How do I track survey responses?**
  You can track who has responded to a survey by using the Participant List option. In addition, you can identify individual responses using the Participant Identifier feature. Both of these options are found in the Manage Survey Participants section of your project.

- **Can I add or delete a survey response?**
  It is possible to edit or delete survey responses. To do this, check the Edit Surveys option in the User Rights section.

- **How do I verify if a survey respondent changed their answers?**
  If you are concerned that survey respondents changed their answers before submitting their survey e.g. to try to qualify for a study you can check their responses in the Logging Tool.

- **What is the logging tool?**
  You can use the logging tool to troubleshoot issues that arise that may be due to a change in a data value, calculations and branching logic no longer working, etc. In the log you can filter by record, user, and event type.
```
## Analysis with SQL (OHDSI/OMOP)

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


<div style="text-align: right"><a href="#table-of-contents">Back to Table of Contents</a></div>
<!--- WIP 

# OMOP ETL Process: Common Problems and Solutions

## Design and Planning
| Problem | Suggestion |
| ------- | ---------- |
| Different Coding Schemes in Databases | Standardize structures, conventions, and content during ETL to align different coding schemes. |
| Designing ETL with Expert Collaboration | Collaborate between data and CDM experts for efficient design. |
| Inadequate Source Data Documentation | Use White Rabbit to scan and understand source data thoroughly. |
| Mapping Source Data to CDM | Use Rabbit-in-a-Hat tool for interactive mapping and documentation. |
| Mapping Non-OMOP Coding Systems | Focus on frequently used codes and utilize existing mappings where possible. |
| Handling Post Coordinated SNOMED Codes | Address challenges with codes or conditions occurring multiple times. |
| Integration of New Data Sources | Develop a flexible ETL process to integrate new data sources. |
| Handling Various Data Formats | Create processes to handle different data formats effectively. |
| Custom Code Development for ETL | Develop custom code when necessary for specific ETL requirements. |
| Adapting to CDM Updates | Adapt ETL processes to accommodate updates in the CDM. |

## Implementation and Technology
| Problem | Suggestion |
| ------- | ---------- |
| ETL Implementation | Utilize existing code and community resources for efficient ETL process implementation. |
| Choosing ETL Implementation Technology | Select technology based on site expertise (SQL, SAS, C#, Java, etc.). |
| Data Transformation Logic | Clearly define and document the logic for data transformations. |
| ETL Performance Optimization | Continuously monitor and optimize ETL performance. |
| Scalability of ETL Processes | Ensure that ETL processes are scalable to accommodate growing data. |
| Data Mapping Complexities | Address complexities in mapping data from various sources to the CDM. |
| Updating and Maintenance of ETL Scripts | Regularly update and maintain ETL scripts for consistency. |
| Managing ETL Dependencies | Identify and manage dependencies in the ETL process. |
| Cross-Database Compatibility | Ensure compatibility of ETL processes across different databases. |
| Optimizing Data Load Processes | Optimize data load processes to enhance performance. |

## Data Quality and Security
| Problem | Suggestion |
| ------- | ---------- |
| Data Quality Issues | Implement thorough quality control measures to ensure data integrity. |
| Large Dataset Handling | Optimize ETL processes for handling large datasets efficiently. |
| Missing or Incomplete Data | Develop strategies to handle missing or incomplete data elements. |
| Handling Data Anomalies | Develop procedures to identify and resolve data anomalies. |
| Data Security and Compliance | Maintain strict adherence to data security and compliance standards. |
| Data Validation Processes | Implement robust data validation processes to ensure accuracy. |
| Error Handling in ETL Process | Develop comprehensive error handling mechanisms. |
| Source Data Version Control | Maintain version control for source data to track changes. |
| Data Cleansing Procedures | Establish data cleansing procedures to improve data quality. |
| Complex Transformation Rules | Manage complex transformation rules efficiently. |

## Operational Management
| Problem | Suggestion |
| ------- | ---------- |
| Automation of ETL Processes | Explore opportunities to automate repetitive ETL tasks. |
| Resource Allocation for ETL Tasks | Allocate sufficient resources for ETL tasks. |
| Maintaining Data Lineage | Keep track of data lineage throughout the ETL process. |
| Balancing ETL Speed and Accuracy | Balance the need for speed with accuracy in ETL processes. |
| Training for ETL Team | Provide comprehensive training for the ETL team. |
| Standardizing ETL Practices | Standardize ETL practices across various projects. |
| Monitoring ETL Processes | Implement monitoring tools to oversee ETL processes. |
| Dealing with Data Duplication | Develop strategies to handle data duplication issues. |
| Dynamic Data Source Integration | Integrate dynamic data sources effectively into the ETL process. |
| Data Transformation Standardization | Standardize data transformation rules across different datasets. |
| Collaboration and Communication | Foster collaboration and communication among all stakeholders involved in the ETL process. | 
-->


```markdown
## Markdown Content for GitHub Tutorial

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

