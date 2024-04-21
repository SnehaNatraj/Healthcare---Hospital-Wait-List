# Healthcare - Dashboard

## Project Goals

- Track the current status of the patient waiting list
- Analyse the historical monthly trend of waiting list Inpatient & Outpatient categories
- Detailed specialty level & age profile analysis

## Metrics Required

- Average & Median Waiting list
- Current Total Waitlist

## Views Required

- Summary Page
- Detailed Page for Granular analysis

### Steps followed 

- Step 1: Load data into Power BI Desktop, the dataset is a CSV file.
- Step 2: Data Transformation - rename columns, add columns, and append both Inpatient and Outpatient tables.
- Step 3: Go to model view and manually create a connection between the two tables i.e, Mapping_Specialty (column 'Specialty') and New appended table (column 'Specialty_Name')
- Step 4: To create a toggle button, create a dummy table (Calculation) with columns Average & Median
- Step 5: Create dynamic fields using DAX:
    Latest Month Wait List = CALCULATE(SUM(All_Data[Total]),All_Data[Archive_Date] = MAX(All_Data[Archive_Date])) + 0

    PY Latest Month Wait List = CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = EDATE(MAX(All_Data[Archive_Date]),-12)) + 0

    Average Waiting List = AVERAGE(All_Data[Total])

    Median Waiting List = MEDIAN(All_Data[Total])

    Avg / Med Wait List = SWITCH(VALUES('Calculation Method'[Calc Method]), "Average", [Average Waiting List], "Median", [Median Waiting List])
- Step 6: Dashboard design and Layout
- Step 7: Add interactivity and navigation

## Report Snapshot (Power BI DESKTOP)

![summary dashboard](https://github.com/SnehaNatraj/Healthcare---Hospital-Wait-List/assets/163089747/c0518b0f-1ac9-44c3-b2b9-f2e04e34a7b7)

![detail view](https://github.com/SnehaNatraj/Healthcare---Hospital-Wait-List/assets/163089747/2f8d36d6-dd3c-4bba-8c4f-33dafc37e4f2)

## Inference

On average, through the years from 2018 to 2021, the percentage of patient wait lists concerning their category\
   Inpatient - 10.62%\
   Outpatient - 72.49%\
   Day Case - 16.89%\
Top 5 Specialty_Name concerning Average waiting list\
   Accident & Emergency\
   Paediatric Cardiology\
   Paediatric Orthopaedic\
   Pediatric Dermatology\
   Pediatric ENT
