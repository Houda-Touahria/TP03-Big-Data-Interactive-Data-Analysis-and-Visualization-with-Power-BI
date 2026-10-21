...
TP03: Interactive Data Analysis and Visualization with Power BI📌 
Project OverviewThis project focuses on analyzing user behavior data from an e-commerce platform using Power BI Desktop and Python (Kaggle) for preprocessing. 
The workflow covers the end-to-end business intelligence pipeline: dataset exploration, data cleaning and transformation, measure creation using DAX formulas, interactive dashboard design, and business insight extraction.
🗂️ Dataset DetailsSource: eCommerce behavior data from multi-category store (Kaggle)Timeframe: October 2019 logs (2019-Oct.csv).Nature of Data: Clickstream event logs capturing user interactions (view, cart, purchase) across diverse product categories including electronics, appliances, auto accessories, and apparel.
🛠️ Tools & TechnologiesPython / Pandas (Kaggle Environment): Memory-efficient sampling (500,000 rows) and initial data cleansing.Power Query Editor: Schema validation, data type corrections, and handling missing values.DAX (Data Analysis Expressions): Calculation of dynamic business KPIs.Power BI Desktop: Dashboard design, visual formatting, and slicer interactions.
🚀 Lab Tasks & ImplementationTask 1: Data Exploration & PreprocessingDue to the massive file size of the original dataset, a representative sample of 500,000 records was extracted and inspected.Missing Value Handling: Columns category_code and brand contained null entries, which were imputed with "Unknown" to avoid losing valuable transactional records.Feature Extraction:Extracted primary categories (main_category) by parsing hierarchical strings (e.g., electronics.smartphone $\rightarrow$ electronics).Derived date values (event_date) from UTC timestamps to allow daily trend tracking.Integrity Check: Filtered out negative or zero price anomalies and verified no exact duplicate rows remained.
Task 2: Power Query TransformationImported the cleaned dataset into Power BI Desktop.Set explicit data types:event_time & event_date $\rightarrow$ Date/Time and Dateprice $\rightarrow$ Decimal Numberbrand, main_category, event_type $\rightarrow$ TextApplied changes using Close & Apply to construct the reporting data model.Task 3: DAX MeasuresCreated dynamic measures to evaluate sales performance:Total Revenue:Total Revenue = 
CALCULATE(
    SUM(ecommerce_cleaned_sample[price]), 
    ecommerce_cleaned_sample[event_type] = "purchase"
)
Total Purchases:Total Purchases = 
CALCULATE(
    COUNTROWS(ecommerce_cleaned_sample), 
    ecommerce_cleaned_sample[event_type] = "purchase"
)
Task 4 & 5: Visualizations & InteractivityConstructed an interactive dashboard consisting of:KPI Card: Immediate display of aggregate purchases/revenue.Horizontal Bar Chart: Top performing brands by purchase count (highlighting market leaders such as Samsung, Elenberg, and LG).Column Chart: Revenue and transaction distribution across main_category.Behavior Funnel / Bar Chart: Interaction volume comparison across view, cart, and purchase stages.Line Chart: Daily timeline of purchase volumes throughout October.Dynamic Slicers: Interactive filtering by main_category and event_date slider to analyze segment performance in real time.📊 Summary Findings & Insights (Final Report)The interactive dashboard reveals that user activity on the platform is heavily dominated by product browsing, with final purchases representing only a small fraction of overall interactions. Electronics and household appliances account for the highest proportion of transactions, led predominantly by major global manufacturers such as Samsung and LG. Products categorized under "auto" represent automotive accessories and electronics rather than complete vehicles, showing steady demand. Daily transaction curves demonstrate recurring weekend sales peaks, reflecting regular leisure-time purchasing patterns. The implementation of dynamic slicers confirms that surges in browsing volume do not automatically translate to equivalent conversion rates, indicating that marketing efforts should focus on retargeting shoppers who abandon products at the cart phase.📁 Repository Structure├── TP03_Analysis.pbix           # Power BI Report File
├── screenshots/
│   ├── data_exploration.png     # Screenshot of initial imported table
│   └── final_dashboard.png      # Screenshot of the completed interactive dashboard
└── README.md                    # Project documentation & summary report
