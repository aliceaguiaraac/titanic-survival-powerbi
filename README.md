# Titanic Passenger Patterns & Outcomes

**From data preparation to executive insight. An end-to-end Power BI case study.**

This project explores passenger profiles, observed survival patterns, data quality and interactive segmentation using the Titanic dataset.

The goal was to build an executive Power BI experience that goes beyond static reporting by combining data preparation, semantic modelling, dynamic analysis and interactive decision support.



## Live Dashboard

Explore the interactive Power BI report:

<p data-sourcepos="9:1-9:189" dir="auto"><a href="https://app.powerbi.com/view?r=eyJrIjoiMmEyMzliZjktOWVmNi00MGQxLWIwNjUtZmQ5NzAzNGQxMjk5IiwidCI6IjM1ODAxOWMyLWZmMWQtNGRlOC04MDBlLTk2YTRkMzgwNzMwYyIsImMiOjl9" rel="nofollow">Click here to open the interactive Power BI report</a></p>


## Preview

![Titanic Power BI Executive Overview](images/titanicexecutiveview.png)



## Business Questions

The report was designed around four main analytical questions:

- What were the key survival patterns?
- Who were the passengers?
- What passenger characteristics were associated with survival?
- What data-quality limitations should be considered?



## Report Structure

### 1. Executive Overview

Provides a high-level view of the dataset and key survival patterns.

Main features:

- Total passengers
- Total survivors
- Overall survival rate
- Family travel profile
- Dynamic analysis using a Field Parameter
- Dynamic narrative insights
- Overall highest-survival passenger segment
- What-if parameter to control minimum segment size

The Field Parameter allows users to explore survival rates dynamically by:

- Passenger Class
- Sex
- Age Group
- Family Travel

The What-if parameter allows users to define the minimum number of passengers required for a segment to be considered when identifying the highest observed survival segment.



### 2. Passenger Profile

Explores the composition of the passenger population.

The page includes:

- Male and female passenger distribution
- Family travel profile
- Missing age information
- Age-group distribution
- Passenger-class distribution
- Gender distribution

This page focuses on understanding who was aboard before analysing survival outcomes.



### 3. Survival Analysis

Explores how survival varied across passenger characteristics.

The analysis includes:

- Survival rate by sex
- Survival rate by age group
- Survival rate by passenger class and sex
- Dynamic key findings

A custom **Deneb / Vega-Lite dumbbell chart** is used to compare female and male survival rates within each passenger class.

This visual was selected because the distance between the two points makes the survival gap easier to interpret than a traditional clustered bar chart.



### 4. Data Quality & Preparation

Assesses data completeness and documents the main preparation decisions.

Key data-quality findings:

- Age missing: **177 passengers**
- Cabin missing: **687 passengers**
- Embarked missing: **2 passengers**
- Fare missing: **0 passengers**

A completeness chart compares Known vs Missing values across key fields.

Preparation decisions include:

- Missing Age values were preserved and classified as **Unknown**
- Missing Cabin values were preserved and converted into a **Known / Missing availability indicator**
- Missing Embarked values were labelled **Unknown**
- Fare values were preserved without arbitrary imputation
- Derived analytical fields were created for:
  - Passenger Class
  - Age Group
  - Family Size
  - Family Travel
  - Data availability indicators

Missing values were not replaced without a defensible analytical or business rule.



## Analytical Approach

This report is primarily **descriptive and analytical**, rather than predictive.

The dashboard uses **observed survival rates** and does not present model-generated survival probabilities.

This distinction is intentional.

A predictive machine-learning layer would require additional steps such as:

- Feature engineering
- Train/test split
- Model selection
- Model validation
- Performance comparison
- Interpretation of predictive outputs

The current version focuses on the areas most aligned with Business Intelligence and Data Visualization:

- Data preparation
- Data quality
- Semantic modelling
- DAX
- Interactive analysis
- Executive storytelling

A natural next step would be a dedicated **Model Comparison** page evaluating predictive models such as Logistic Regression, Random Forest or other classifiers.



## Multidimensional Segment Analysis

The highest observed survival segment is calculated using the combination of:

- Sex
- Passenger Class
- Age Group
- Family Travel

Highly granular combinations can produce extreme survival rates based on a small number of observations.

For example, a segment containing only two passengers would show a 100% observed survival rate if both passengers survived.

To address this, the report includes a **What-if parameter** that allows the user to define the minimum segment size considered in the analysis.

This makes the result more transparent and allows users to explore how the highest-survival segment changes as the minimum sample size increases.


## Data Model

The report follows a simple analytical model built around the passenger dataset.

Key modelling principles include:

- Explicit measures instead of implicit aggregations
- Separation between descriptive columns and analytical measures
- Derived business-friendly attributes
- Explicit missing-value indicators
- Reusable DAX measures
- Dynamic calculations driven by filter context

Core measures include:

- Total Passengers
- Survivors
- Not Survivors
- Survival Rate
- Age Missing
- Cabin Missing
- Embarked Missing
- Fare Missing
- Passenger profile measures
- Dynamic highest / lowest survival groups
- Highest multidimensional survival segment



## Advanced Power BI Features

The report includes several Power BI capabilities beyond standard charting:

- **Field Parameters**
  - Dynamic analytical dimension switching

- **What-if / Numeric Range Parameter**
  - Minimum segment-size scenario analysis

- **Dynamic DAX Narratives**
  - Automatically generated analytical insights

- **Deneb / Vega-Lite**
  - Custom dumbbell visualization for passenger-class and sex comparison

- **Sentence-format Tooltips**
  - Context-aware explanatory tooltips

- **Native Donut Center Value**
  - Used to display total passenger context

- **Custom SVG Icons**
  - Used to maintain a consistent visual system



## Tools & Technologies

- Power BI
- Power Query
- DAX
- Deneb
- Vega-Lite



## Dataset

This project uses the public Titanic passenger dataset commonly associated with the Kaggle Titanic challenge.

The dataset contains **891 passenger records** and includes attributes such as:

- Passenger Class
- Name
- Sex
- Age
- Siblings / Spouses
- Parents / Children
- Ticket
- Fare
- Cabin
- Embarkation Port
- Survival status



## Key Analytical Principles

Throughout the project, several analytical principles were applied:

- Missing values were preserved rather than arbitrarily imputed
- Historical survival rates were described as **observed survival rates**
- Association was not presented as causation
- Small segment sizes were made visible through the What-if parameter
- Data-quality limitations were explicitly documented
- Analytical conclusions were derived dynamically wherever possible rather than hard-coded

