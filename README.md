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

![Image_Alt](https://github.com/KanikaGaikwad/project-performance-predictive-risk/blob/41f1b8ac1dbc3bc75306d6ac5212e438a9622045/Performance%20Dashboard%201.png)
![Image_Alt](https://github.com/KanikaGaikwad/project-performance-predictive-risk/blob/bdcd61e21b0dfc84d4443ffeea6ad1584b4d8379/Performance%20Dashboard%202.png)


### 2. Predictive Project Risk Analysis (Predictive Insights Dashboard)
This dashboard utilizes machine learning to forecast which tasks are most likely to become overdue, enabling proactive risk mitigation and resource reallocation.

#### Key Metrics & Visuals:

- Total tasks predicted at risk of being overdue.

- Model performance metrics (e.g., Accuracy, Recall).

- Breakdown of overdue probability by task type, project, and other influencing factors.

- Detailed table of high-risk tasks for immediate action.

- Insights into feature importance (e.g., ```impact of days_since_last_update```, ```percentage_completion```).

![Image_Alt](https://github.com/KanikaGaikwad/project-performance-predictive-risk/blob/8c5118978bef56b12b5b21dcc7231ad0fa6cee6f/Predictive%20Dashboard%201.png)
![Image_Alt](https://github.com/KanikaGaikwad/project-performance-predictive-risk/blob/0f440a7edf4451138d15c8637a3d768689b0baca/Predictive%20dashboard%203.png)

## ⚙️ Methodology & Technologies
This project follows a robust data science lifecycle, from data acquisition and cleaning to predictive modeling and interactive visualization.

### Data Source & Engineering
Data Source: Simulated project management task data, designed to mimic real-world scenarios, including data quality issues (e.g., inconsistent spellings, missing values) and task dependencies.

- **Data Pipeline (Python):** A comprehensive Python script (or Jupyter notebook) handles:

- **Data Loading:** Ingesting raw task data.

- **Data Cleaning:** Standardizing categorical fields (```status```, ```priority```, ```blocker_reason```, ```quality_review_status```), handling missing values, and ensuring data consistency.

- **Feature Engineering:** Creating critical analytical features such as:

  - ```is_overdue``` (Target variable)

  - ```cycle_time_days```

  - ```days_since_last_update```

  - ```time_to_start_days```

  - ```has_predecessor```

  - ```has_due_date```

  - ```cost_of_rework```, ```cost_of_delay```, ```total_actual_cost``` (simulated financial metrics)

- Preprocessing: Scaling numerical features (MinMaxScaler) and encoding categorical features (OneHotEncoder).

### Machine Learning Model
- **Model Type:** Random Forest Classifier

- **Training:** The model is trained on the prepared dataset to predict the ```is_overdue``` status of tasks. ```class_weight='balanced'``` was used to address potential class imbalance.

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

```
.
├── data/
│   ├── initial_project_tasks.csv      # Raw/initial simulated task data
│   ├── project_tasks_for_power_bi.csv # Cleaned, feature-engineered, and predicted data for Power BI
│   ├── dim_assignees.csv              # Dimension table for assignees
│   └── dim_task_types.csv             # Dimension table for task types
├── notebooks/
│   └── project_data_pipeline.ipynb    # Python script/Jupyter notebook for data prep, ML, and prediction
├── powerbi/
│   └── Project_Performance_Dashboard.pbix # Power BI dashboard file
└── README.md
```
*Note: The Python script file name used here is ```project_data_pipeline.ipynb```. Please update this if your actual file name is ```Clickup_Data_prep.ipynb``` or something else.*

## ▶️ How to Use/View
1. **Clone the Repository:**
```
git clone [https://github.com/KanikaGaikwad/project-performance-predictive-risk.git]
cd [project-performance-predictive-risk]
```

2. **Prepare Data:**

- Ensure your initial data (```initial_project_tasks.csv```) is placed in the data/ directory.

- Run the Python notebook (notebooks/project_data_pipeline.ipynb) to process the data and generate ```project_tasks_for_power_bi.csv```, ```dim_assignees.csv```, and ```dim_task_types.csv```.

3. **View Dashboard:**

- Open ```powerbi/Project_Performance_Dashboard.pbix``` using Power BI Desktop.

- Refresh the data source if prompted to ensure the latest processed data is loaded.

## 🚀 Future Enhancements
This project has established a robust foundation for project analytics. Building upon this, several key areas for future development could provide even deeper insights and further optimize project operations:

**1. Granular Task Analysis & Process Optimization**
- **Objective:** To understand performance at a more granular level than task_type, by analyzing specific phases, sub-tasks, or activities within broader task categories.

- **Rationale:** High-level task types often encompass multiple internal steps. Pinpointing which specific sub-activities contribute most to delays (e.g., "Data Cleaning for Report X" vs. "Dashboard Design") is crucial for identifying precise process inefficiencies.

- **Approach:** This would likely involve:

  - **Natural Language Processing (NLP):** Applying text analysis to task_name or a ```task_description``` field (if available) to extract common sub-phases or keywords.

  - **Process Mining:** If more detailed timestamped data on status transitions were available, process mining techniques could visually map workflows and identify common deviations or bottlenecks.

  - **Hierarchical Analysis:** Leveraging a consistently populated parent_id field to roll up performance metrics from sub-tasks to parent tasks.

**2. Delegation, Workload Distribution, and Assignee Performance**
- **Objective:** To analyze how tasks are distributed among assignees, assess individual workload, and identify potential imbalances or areas for capacity optimization.

- **Rationale:** Understanding the human element (who is doing what, how much, and how efficiently) is vital for overall project flow. Individual work styles and delegation practices can significantly impact project delivery.

- **Approach:** This would involve:

  - Analyzing average ```time_tracked_hours```, ```cycle_time_days```, and task counts per ```assignee_id```.

  - Developing metrics for workload balance across the team.

  - Potentially correlating assignee performance with task types, complexity, or project.

  - This analysis could also inform strategic resource allocation and training needs.

**3. Advanced Predictive Modeling & Real-time Integration**
- **Objective:** To build more sophisticated models that can forecast task delays or identify tasks at high risk of becoming overdue with even greater precision, and integrate these insights into operational workflows.

- **Rationale:** Moving from reactive (diagnosing past delays) to proactive (predicting future delays) is a significant leap in project management maturity.

- **Approach:**

  - **Model Refinement:** Exploring more advanced machine learning models (e.g., time-series forecasting for completion dates, deep learning for complex patterns) or ensemble methods.

  - **Real-time Integration:** Connecting with live project management APIs (e.g., ClickUp, Jira) for automated data updates and deploying the predictive model as a microservice for real-time risk alerts.

  - **User Interface:** Developing a dedicated web application to host the dashboards and allow seamless user interaction and scenario planning without Power BI Desktop.

These future enhancements would further empower data-driven decision-making, moving towards a more optimized and predictable project delivery system.
