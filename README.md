# README - Project Overview and Code Explanation

## RANDOM DATA WAS GENERATED TO PUBLISH THIS PROJECTS, IN ORDER TO PRESERVE CLIENT'S CONFIDENCIALITY

## Project Description
This repository contains a series of Python scripts used to process, analyze, and generate insights from Jira and Asist ticketing system data. The goal is to evaluate the efficiency of software development projects, particularly focusing on time management and issue tracking. The project includes data wrangling, exploration, machine learning, and report generation tasks.

## Data Sources
### The data comes from three main sources:
- **Asist**: A ticket management system, with data about both open and closed tickets.
- **Jira**: A software used for project management and issue tracking.
- **Worklogs**: Logs showing the amount of time spent on various tasks by team members.

## Key Steps in the Analysis

### 1. Data Preparation
Before analysis, several preprocessing steps are necessary, including:
- **Merging Datasets**: The Asist Origin and Asist Open datasets are merged to combine data from closed and open tickets.
- **Time Conversion**: All time values (in seconds) are converted into days.
- **Project Number Extraction**: A project number is extracted from Jira ticket summaries to link Jira data with Asist data.
- **Categorization**: A categorization of team members as either Developer or Tester is applied, along with their project associations.
- **Date Format Conversion**: All date columns are converted to the desired format ('%d/%m/%Y').
- **Column Selection**: Unnecessary columns are discarded to focus on the most relevant data.

### 2. Data Cleaning and Exploration
The following tasks were performed during data exploration:
- **Missing Values**: Replaced missing values in critical columns with default or calculated values.
- **Data Type Conversion**: Ensured correct data types for various columns (e.g., converting time spent into numeric values).
- **Ticket Number Extraction**: A helper function extracts Asist ticket numbers from Jira summaries to facilitate data merging.
- **Worklog Analysis**: Worklogs are examined, categorized by task types, and linked to the corresponding projects.

### 3. Merging Data
Once data is cleaned and structured, the following merges are performed:
- **Jira Data**: Merge Jira project data with Asist tickets to create a unified database containing project estimates and time spent.
- **Worklogs**: Merge worklogs with ticket information to track individual contributions to tickets, categorize them into TMA or Project, and assign roles (Developer/Tester).

### 4. Reporting and Insights
Several reports and tables are generated to provide insights into the data:
- **Pivot Tables**: To evaluate time spent on different types of projects (TMA vs. non-TMA).
- **Time Spent by Developer/Tester**: A table showing how much time each developer or tester spent per week.
- **Project Analysis**: Detailed reports for each project, including:
  - Time spent on development (excluding bug fixes).
  - Time spent solving bugs vs. time spent on tests.
  - Number of bugs opened by different roles (HN vs. Staci).
  - Average solution time for each project.

### 5. Machine Learning Models
- **Time Prediction**: A model is applied to predict the amount of time it would take to resolve new tickets based on historical data.
- **Classification**: A classification model predicts the priority or urgency of a ticket.

## Steps and Functions Overview

### Mount Google Drive
The code begins by mounting Google Drive and authenticating the user to access Google Sheets data.

### Importing Required Libraries
Several libraries are imported, such as pandas for data manipulation, numpy for mathematical operations, sklearn for machine learning, and gspread for interacting with Google Sheets.

### Merging Asist Data
Closed and open ticket data from Asist are combined into a single dataset, and missing values are addressed. The dataset is also enriched with additional columns such as "Status" and "Priority".

### Data Wrangling for Worklogs
Worklogs data are explored and cleaned. Time values are converted, and relevant information (e.g., author, start date, project) is retained.

### Ticket Time Analysis
Time spent on development, bug fixes, and testing are analyzed to provide a detailed breakdown of the project work.

### Pivot Table Generation
A pivot table aggregates time spent per project type (TMA or not) and domain.

### Time Spent on Non-Facturable Tasks
A separate analysis is conducted to examine time spent on non-billable tasks such as internal issues.

### Weekly Time Tracking for Developers/Testers
Time tracking is done on a weekly basis for each team member to ensure that time logs align with project timelines.

### Machine Learning Models
ML models are used to predict how long it will take to resolve new tickets and classify tickets by their urgency.

### Final Reports
Various insights are extracted through aggregation and statistical analysis to provide meaningful reports on project efficiency.

## Machine Learning Model Explanation

### Random Forest Regressor
The Random Forest Regressor is used to predict the time required to resolve new tickets based on historical data. This model considers features such as original estimates and time spent in the past to make predictions.

### Classification for Ticket Priority
A classification model is trained to predict the priority of tickets, helping to identify urgent issues based on historical trends.

## Concluding Remarks
This repository is a comprehensive tool for project time tracking, analysis, and prediction in a software development environment. The use of machine learning enhances the ability to predict ticket resolution times and classify issues based on urgency, which can significantly improve project management and resource allocation.
