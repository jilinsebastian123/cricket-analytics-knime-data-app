# 🏏 Cricket Analytics Hub: 150-Year Multi-Format Data App

An end-to-end data engineering pipeline and interactive analytics dashboard built with **KNIME Analytics Platform**. This project processes, models, and visualizes 150 years of international cricket history (1876–Present) across Test, ODI, and T20 formats using a triple-stream ETL architecture.

---

## 📌 Pipeline Architecture

The workflow is structured into a **Triple-Stream Data Pipeline** encapsulated within an interactive KNIME WebPortal component:

Batting Stream (Top)       ──► String Manipulation ──► Type Conversion ──► Format Filter Widget ──► 3 Linked Charts
Bowling Stream (Middle)    ──► Missing Value       ──► Domain Calc     ──► Country Filter Widget  ──► 3 Linked Charts
Tournament Stream (Bottom) ──► GroupBy (Year)      ──► Domain Calc     ──► Winner Twinlist Widget ──► Timeline & Table

Stream & Node Specifications
Batting Stream: CSV Reader ➔ Constant Value Column Appender ➔ Concatenate ➔ String Manipulation ➔ Cell Splitter ➔ Column Renamer ➔ String to Number ➔ Math Formula ➔ Nominal Row Filter Widgets ➔ Top k Row Filter ➔ Stacked Area Chart, Bar Chart, Scatter Plot.  
Bowling Stream: CSV Reader ➔ Constant Value Column Appender ➔ Concatenate ➔ Cell Splitter ➔ Column Renamer ➔ String to Number ➔ Missing Value ➔ Domain Calculator ➔ Nominal Row Filter Widgets ➔ Top k Row Filter ➔ Bar Chart, Pie/Donut Chart, Box Plot.
Tournament Stream: CSV Reader ➔ Constant Value Column Appender ➔ Concatenate ➔ GroupBy (Year) ➔ Domain Calculator ➔ Nominal Row Filter Widget (Winner Twinlist) ➔ Bar Chart, Pie/Donut Chart, Line Plot, and interactive Table View.
📊 Key Analytical Insights
1. Batting Dynamics & Efficiency
   Peak Run Supremacy: All-time run leaders surpass the 18,000+ aggregate threshold, with the primary elite cohort tightly grouped between 12,000 and 15,000 runs.
   Milestone Outliers: Stacked area analysis shows generational consistency, led by an extreme outlier commanding 250+ career milestones (combined 50s and 100s).
   Anchor vs. Striker Clustering: Scatter analysis highlights distinct dual clusters: classical anchors averaging 40+ at moderate strike rates (50–80) versus modern boundary hitters accelerating to 120–150+ SR.
2. Bowling Mastery & Discipline
   All-Time Benchmark: Elite strike leaders surpass the historic 800-wicket career threshold
   Global Wicket Distribution: Wickets are evenly distributed among traditional cricket powerhouses (India, Australia, Pakistan, England, West Indies, Sri Lanka).
   Rigid Economy Band: While bowling averages fluctuate across formats and eras (20–32 runs/wicket), elite bowling economy rates remain confined within a tight band of 2.5–4.5 runs/over.
3. Tournament Trends & Global Expansion
   Series Dominance: Historically led by Australia, England, and India (~200–250+ series titles each), with drawn series representing a significant portion of historical outcomes.
   Post-1970 Exponential Surge: Series frequency averaged under 10 per year prior to 1970, surging to over 70+ series annually in the modern era driven by white-ball tournament formats.
📁 Repository Contents
Cricket_Analytics_DataApp.knwf: Exported, portable KNIME workflow package configured with workflow-relative paths.
data/: Raw CSV files containing statistics for batting, bowling, and tournament series across Test, ODI, and T20 formats (odt.csv, odb.csv, twb.csv, twt.csv, twbo.csv, tbo.csv, odbo.csv, tt.csv, tb.csv).
Cricket_Analytics_Presentation.pdf: Slide deck breaking down the ETL pipeline architecture, research questions, and visual dashboard views[cite: 2].

🚀 How to Run the Project
Install KNIME Analytics Platform[cite: 2].
Download or clone this repository:
git clone [https://github.com/your-username/cricket-analytics-knime-data-app.git](https://github.com/your-jilinsebastian123/cricket-analytics-knime-data-app.git)
Open KNIME and import the workflow via File > Import KNIME Workflow...[cite: 2].
Run the workflow, then right-click the wrapped composite component (Cricket_Anal) and choose Interactive View to launch the dashboard.  
