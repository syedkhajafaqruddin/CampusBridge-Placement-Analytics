# CampusBridge --- Campus Placement Analytics Dashboard

> **End-to-end data analytics project \| Excel · Power Query · Power BI
> · DAX**

An interactive placement analytics dashboard built to help college
placement teams understand recruitment activity, student participation,
employer demand, and advertised job opportunities.

## Project at a glance

  -----------------------------------------------------------------------
  Item                                Details
  ----------------------------------- -----------------------------------
  Project                             CampusBridge --- Placement
                                      Analytics

  Domain                              Campus recruitment / higher
                                      education

  Primary tools                       Microsoft Excel, Power Query,
                                      Microsoft Power BI

  Analysis focus                      Applications, colleges, students,
                                      companies, roles, openings,
                                      packages, and recruitment drives

  Output                              Interactive Power BI dashboard with
                                      KPI cards and analytical visuals
  -----------------------------------------------------------------------

## 1. Business problem

Placement information is often spread across separate datasets for
students, colleges, companies, job roles, and applications. When these
datasets are not cleaned, connected, and analyzed together, placement
teams can find it difficult to answer important operational questions:

-   Which colleges generate the highest application activity?
-   Which industries and job types are offering the most openings?
-   Which job roles have higher advertised packages?
-   How does application activity change over time?
-   How are applications distributed across recruitment drive types?
-   How many students applied, how many joined, and how many companies
    were reached?

Without a consolidated view, teams may struggle to compare recruitment
activity, identify hiring demand, and plan employer outreach or student
preparation effectively.

### Project objective

Build a reliable, easy-to-use Power BI report that combines the
available placement data and turns it into clear insights for
recruitment planning and decision-making.

## 2. Tools and technologies

  -----------------------------------------------------------------------
  Tool                                How it was used
  ----------------------------------- -----------------------------------
  **Microsoft Excel**                 Initial review, cleaning, and
                                      preparation of the raw data before
                                      analysis.

  **Power Query**                     Data transformation and preparation
                                      in the Power BI workflow, including
                                      checking column types and resolving
                                      data-quality issues.

  **Microsoft Power BI**              Data modeling, relationship
                                      management, KPI cards, report
                                      design, and interactive
                                      visualizations.

  **DAX**                             Measures and calculations used to
                                      produce key performance indicators
                                      and aggregated metrics.
  -----------------------------------------------------------------------

## 3. Project workflow

### Step 1 --- Data review and cleaning in Excel

I first reviewed the source data in Excel and prepared it for analysis.
The data-cleaning work focused on common quality issues such as:

-   Missing or blank values
-   Duplicate records
-   Inconsistent text formats
-   Incorrect or inconsistent data types
-   Date fields that needed to be suitable for time-based analysis

The purpose of this stage was to improve consistency and reduce issues
that could affect the analysis.

### Step 2 --- Data transformation with Power Query

I used Power Query as part of the preparation workflow to inspect and
transform the data before building the report. This stage helped prepare
columns and tables for a consistent Power BI model.

### Step 3 --- Splitting the data into related tables

Instead of analyzing one large flat dataset, I organized the information
into separate subject-based tables:

  -----------------------------------------------------------------------
  Table                   What it contains        Why it is useful
  ----------------------- ----------------------- -----------------------
  `application`           Application-level       Main table for
                          information, including  analyzing application
                          application date and    activity
                          IDs linking students,   
                          colleges, companies,    
                          and roles               

  `student`               Student attributes such Supports student and
                          as college, branch,     college analysis
                          degree, CGPA, and       
                          backlogs                

  `college`               College details such as Supports college-level
                          name, city, and type    comparisons

  `companies`             Company details such as Supports employer and
                          name, type, industry,   industry analysis
                          and headquarters city   

  `roles`                 Role names, job types,  Supports job-demand and
                          openings, and           package analysis
                          advertised package      
                          information             

  `CALENDER`              Date, month, and year   Supports time-based
                          fields                  analysis and year
                                                  filtering
  -----------------------------------------------------------------------

*The table and column names above reflect the project model. The exact
fields available in each source table determine which analyses can be
performed.*

### Step 4 --- Building the data model in Power BI

I created relationships between the related tables using their key
columns. The model connects application records to the relevant student,
college, company, role, and calendar information.

The intended modeling approach is a **star-schema-style relational
model**: descriptive tables provide context, while application records
provide the activity being analyzed.

Key modeling considerations:

-   Use unique IDs on the **one** side of one-to-many relationships.
-   Keep repeated foreign-key values on the **many** side.
-   Use a dedicated calendar table for date analysis.
-   Prefer single-direction filtering unless a specific requirement
    justifies another direction.
-   Check duplicate keys and unmatched IDs before creating
    relationships.
-   Avoid unnecessary many-to-many relationships.

This modeling stage was important because incorrect relationships can
cause duplicated, identical, or misleading values in report visuals.

## 4. KPI cards

The dashboard includes the following headline metrics:

  -----------------------------------------------------------------------
  KPI                                 What it communicates
  ----------------------------------- -----------------------------------
  **Total Applications**              Overall application records in the
                                      analyzed data

  **Students Applied**                Number of students represented as
                                      having applied

  **Joined Students**                 Number of students recorded as
                                      joined in the project data

  **Total Openings**                  Total job openings represented in
                                      the roles data

  **Companies Reached**               Number of companies represented as
                                      reached in the analysis
  -----------------------------------------------------------------------

The displayed dashboard snapshot showed approximately **1K total
applications, 403 students applied, 59 joined students, 585 openings,
and 22 companies reached**. These are snapshot values from the report
and may change when filters or the underlying data change.

> **Metric definition matters:** "Joined Students" and "Students
> Applied" should be interpreted according to the source data's
> definitions. A joined-to-applicant comparison is meaningful only when
> both measures use compatible populations and counting rules. It should
> not automatically be described as an official placement rate.

## 5. Dashboard visualizations

The report uses a focused set of visuals, each designed to answer a
business question.

  -----------------------------------------------------------------------
  Visualization           Fields / analysis       Business question
  ----------------------- ----------------------- -----------------------
  **Applications by       College name on the     Which colleges have the
  College** ---           category axis;          highest application
  horizontal bar chart    application count as    activity?
                          the value               

  **Job Openings by       Industry on the         Which industries are
  Industry** ---          category axis; sum of   contributing the most
  horizontal bar chart    openings as the value   advertised openings?

  **Average Advertised    Role name on the        Which roles have higher
  Package by Job Role**   category axis; average  average advertised
  --- horizontal bar      package (LPA) as the    packages?
  chart                   value                   

  **Monthly Application   Calendar month/date on  How does application
  Trend** --- line chart  the X-axis; application activity change over
                          count on the Y-axis     time?

  **Job Openings by Job   Job type on the         Are more openings
  Type** --- bar chart    category axis; sum of   full-time or internship
                          openings as the value   opportunities?

  **Application Share by  Drive type as the       How are applications
  Drive Type** --- pie    legend; application     distributed across
  chart                   count as the value      recruitment drive
                                                  types?
  -----------------------------------------------------------------------

### Why these visuals?

-   Bar charts make comparisons between colleges, industries, roles, and
    job types easy.
-   The line chart reveals changes and patterns over time.
-   The pie chart provides a simple view of the share of applications
    across drive types.
-   KPI cards give users a quick summary before they explore the
    detailed visuals.

## 6. Business questions and how the dashboard helps answer them

### Q1. Which colleges have the highest application activity?

**Dashboard response:** The Applications by College chart ranks colleges
by application count. Placement teams can use it to compare
participation and identify where outreach or engagement may need
attention.

### Q2. Which industries are offering the most openings?

**Dashboard response:** The Job Openings by Industry chart compares the
total openings associated with each industry. This helps highlight areas
of employer demand and can inform employer-engagement priorities.

### Q3. Which job roles have higher advertised packages?

**Dashboard response:** The Average Advertised Package by Job Role chart
compares average package values across roles. Students and placement
teams can use it to explore how advertised compensation differs by role.

### Q4. How does application activity change month by month?

**Dashboard response:** The Monthly Application Trend shows application
volume over time. This can help teams identify busy periods and plan
placement activities, provided the date data and calendar relationship
are accurate.

### Q5. What types of jobs are available?

**Dashboard response:** The Job Openings by Job Type chart compares
full-time and internship openings, helping users understand the mix of
opportunities in the dataset.

### Q6. Which recruitment drive types account for the applications?

**Dashboard response:** The Application Share by Drive Type pie chart
shows the distribution of application records across drive types, such
as virtual, on-campus, and pool campus drives.

## 7. Business value

The dashboard brings several related datasets into one analytical view.
It helps placement stakeholders:

-   Compare application activity across colleges.
-   Understand the distribution of openings across industries and job
    types.
-   Explore advertised packages across job roles.
-   Review application trends over time.
-   Understand participation across recruitment drive types.
-   Use a consistent set of KPIs as a starting point for placement
    discussions.

The dashboard supports better-informed planning; it does not by itself
establish why a college or industry performs a certain way. Further
investigation and validated source data are needed before making
operational decisions.

## 8. Key learning outcomes

Through this project, I gained practical experience in:

-   Cleaning and preparing data in Excel.
-   Transforming data with Power Query.
-   Separating a flat dataset into related tables.
-   Understanding primary keys, foreign keys, and one-to-many
    relationships.
-   Designing a star-schema-style data model.
-   Creating DAX measures and KPI cards.
-   Choosing visuals based on business questions.
-   Checking data quality and validating report results.
-   Presenting analysis in a structured Power BI dashboard.

## 9. Repository structure

A suggested GitHub repository structure is:

``` text
CampusBridge-Placement-Analytics/
│
├── README.md
├── data/
│   ├── source-data/          # Add data files here if you are permitted to share them
│   └── cleaned-data/         # Add prepared data files here if appropriate
│
├── dashboard/
│   └── CampusBridge.pbix     # Power BI report file
│
└── screenshots/
    └── dashboard-overview.png
```

Update the file names and folders to match the actual files you upload.
Do not publish personal, confidential, or restricted student/company
information. If the dataset is not yours to distribute, include a small
anonymized sample or describe the data without uploading the source
records.

## 10. How to explore the project

1.  Open the `.pbix` file in Microsoft Power BI Desktop.
2.  Review the KPI cards for the overall placement activity snapshot.
3.  Use the year slicer and any available report filters to explore
    different periods.
4.  Select chart categories to cross-filter other visuals.
5.  Compare colleges, industries, job types, roles, and drive types to
    explore the business questions.

## 11. Conclusion

CampusBridge demonstrates an end-to-end analytics workflow: preparing
raw data, organizing it into related tables, building a structured data
model, creating DAX-based KPIs, and developing visualizations around
practical business questions.

The central learning from this project is that an effective dashboard is
not just a collection of charts. It starts with reliable data, a sound
model, and a clear understanding of the decisions the analysis is
intended to support.

------------------------------------------------------------------------

**Tools:** Microsoft Excel · Power Query · Microsoft Power BI · DAX

**Project:** CampusBridge --- Campus Placement Analytics Dashboard
