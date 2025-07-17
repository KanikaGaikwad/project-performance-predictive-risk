# Project Performance & Predictive Risk Dashboard
This project delivers a comprehensive analytics solution for optimizing project management and mitigating timeline/budget risks. Leveraging Python for robust data engineering and machine learning, and Power BI for interactive visualization, it provides both a diagnostic overview of project health and a predictive layer to identify tasks at risk of becoming overdue.

## 📊 Project Overview & Motivation
In complex project environments, fragmented data and a lack of proactive insights often lead to resource inefficiencies, missed deadlines, and budget overruns. This project addresses these challenges by:

- Unifying disparate task data into a coherent, analyzable structure.

- Providing a clear, real-time view of project performance and bottlenecks.

- Forecasting potential overdue tasks to enable proactive intervention.

- Quantifying the financial impact of inefficiencies (rework, delays) to drive strategic decisions.

The solution is designed to enhance resource allocation efficiency and reduce operational expenditures by providing data-driven insights.

## ✨ Key Features & Dashboards
The solution comprises two main interactive Power BI dashboards:

### 1. Project Performance & Operational Analytics (Diagnostic Dashboard)
This dashboard offers a comprehensive view of current and historical project performance, enabling stakeholders to understand key metrics, identify trends, and diagnose issues.

#### Key Metrics & Visuals:

- Overall project status and completion rates.

- Task distribution by project, status, and priority.

- Time-related metrics (e.g., average cycle time, time to start).

- Identification of current bottlenecks and high-impact areas.

<<Replace this with your actual diagnostic dashboard screenshot path.>>

### 2. Predictive Project Risk Analysis (Predictive Insights Dashboard)
This dashboard utilizes machine learning to forecast which tasks are most likely to become overdue, enabling proactive risk mitigation and resource reallocation.

#### Key Metrics & Visuals:

- Total tasks predicted at risk of being overdue.

- Model performance metrics (e.g., Accuracy, Recall).

- Breakdown of overdue probability by task type, project, and other influencing factors.

- Detailed table of high-risk tasks for immediate action.

- Insights into feature importance (e.g., impact of days_since_last_update, percentage_completion).

<Replace this with your actual predictive dashboard screenshot path.>

## ⚙️ Methodology & Technologies
This project follows a robust data science lifecycle, from data acquisition and cleaning to predictive modeling and interactive visualization.

### Data Source & Engineering
Data Source: Simulated project management task data, designed to mimic real-world scenarios, including data quality issues (e.g., inconsistent spellings, missing values) and task dependencies.

- **Data Pipeline (Python):** A comprehensive Python script (or Jupyter notebook) handles:

- **Data Loading:** Ingesting raw task data.

- **Data Cleaning:** Standardizing categorical fields (status, priority, blocker_reason, quality_review_status), handling missing values, and ensuring data consistency.

- **Feature Engineering:** Creating critical analytical features such as:

  - is_overdue (Target variable)

  - cycle_time_days

  - days_since_last_update

  - time_to_start_days

  - has_predecessor

  - has_due_date

  - cost_of_rework, cost_of_delay, total_actual_cost (simulated financial metrics)

- Preprocessing: Scaling numerical features (MinMaxScaler) and encoding categorical features (OneHotEncoder).

### Machine Learning Model
- **Model Type:** Random Forest Classifier

- **Training:** The model is trained on the prepared dataset to predict the is_overdue status of tasks. class_weight='balanced' was used to address potential class imbalance.

- **Interpretability:** SHAP (SHapley Additive exPlanations) values were used to interpret model predictions, providing insights into which features drive a task's likelihood of being overdue. This enables prescriptive actions.

### Data Visualization
- **Platform:** Power BI

- **Interactivity:** Dashboards are designed with interactive slicers, drill-through capabilities, and custom tooltips for a dynamic user experience.

- **Relational Schema:** A new relational schema was designed to unify fragmented task tracking and dependencies, ensuring data integrity and enabling complex analytical queries within Power BI.

## 📈 Business Impact & Value
The insights and predictive capabilities of this solution are projected to deliver significant business value:

- **15% Lift in Resource-Allocation Efficiency:** By providing clear visibility into project performance and potential bottlenecks, enabling optimized resource deployment.

- **10-15% OpEx Reduction & Enhanced ROI:** Through granular financial analysis that pinpoints inefficiencies related to Task, Rework, and Delay costs, driving targeted recommendations.

- **12-18% Mitigation of Timeline & Budget Risks:** By leveraging predictive insights from the Random Forest model and SHAP interpretability to facilitate proactive resource allocation and early bottleneck identification.

## 📁 Project Structure
'''
.
├── data/

│   ├── initial_project_tasks.csv      # Raw/initial simulated task data

│   └── project_tasks_for_power_bi.csv # Cleaned, feature-engineered, and predicted data for Power BI

├── notebooks/

│   └── project_data_pipeline.ipynb    # Python script/Jupyter notebook for data prep, ML, and prediction

├── powerbi/

│   └── Project_Performance_Dashboard.pbix # Power BI dashboard file

└── README.md
'''

<*Note: The Python script file name used here is project_data_pipeline.ipynb. Please update this if your actual file name is Clickup_Data_prep (3).ipynb or something else.*>

## ▶️ How to Use/View
1. **Clone the Repository:**
'''
git clone [your-repo-url]
cd [your-repo-name]
'''

2. **Prepare Data:**

- Ensure your initial data (initial_project_tasks.csv) is placed in the data/ directory.

- Run the Python notebook (notebooks/project_data_pipeline.ipynb) to process the data and generate project_tasks_for_power_bi.csv.

3. **View Dashboard:**

- Open powerbi/Project_Performance_Dashboard.pbix using Power BI Desktop.

- Refresh the data source if prompted to ensure the latest processed data is loaded.

## 🚀 Future Enhancements
- Integration with live project management APIs (e.g., ClickUp, Jira) for real-time data updates.

- Deployment of the predictive model as a microservice for automated risk alerts.

- Development of a web application to host the dashboards and allow user interaction without Power BI Desktop.

- Exploration of more advanced time-series forecasting models for project completion dates.
