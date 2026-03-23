<div style="background-color:black; color:white; padding:20px; border-radius:10px;">

<!-- Animated GIF -->
<p align="center">
  <img src="https://camo.githubusercontent.com/48d30aafc86131bcb77c8085cea9ea944c74ae4f6026127eb5be2d7bae8f285b/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f76322f726573697a653a6669743a3637392f312a7a566e574a7479474f585f6b5549446d3663634366512e676966" width="500"/>
</p>

<h1 align="center" style="color:white;">Hi 👋, I'm Tushar Kaushik</h1>
<p align="center" style="color:white;">
🎓 MS, Applied Data Science — <b>University of Southern California (USC)</b><br/>
📍 Los Angeles, CA<br/>
🔗 <a href="https://www.linkedin.com/in/tushar-kaushik-493a8115a/" style="color:#58a6ff;">LinkedIn</a> • 
📧 <a href="mailto:kaushiktk015@gmail.com" style="color:#58a6ff;">kaushiktk015@gmail.com</a>
</p>

---

## 👨‍💻 About Me  
I'm a passionate engineer with a strong foundation in **Data Engineering, Data Science, Analytics, ML, Deep Learning, NLP, and Software Development**, driven to turn **raw data** into **actionable insights** and **reliable systems**.  
- 🛠 Skilled in **Azure, AWS, Databricks, PySpark, SQL** for building **scalable data pipelines** and **cloud solutions**  
- 📊 Proficient with **Power BI** & **Tableau** for **BI, dashboarding, and data-driven decision-making**  
- 🤖 Experienced in **Machine Learning, Deep Learning, and NLP** with **scikit-learn, XGBoost, TensorFlow, PyTorch, transformers, feature engineering, predictive modeling**  
- 💻 Strong in **Python, APIs, Git, Docker, Linux**, blending **software engineering best practices** with **data solutions**  
- 🚀 Passionate about designing **end-to-end solutions** that combine **engineering, analytics, NLP, and AI** to drive **measurable business impact**  

---

## 📌 Featured Projects

### 🔹 Data Science & Machine Learning

---

#### [ECG Anomaly Detection — LSTM Autoencoder (PyTorch)](https://github.com/tkaushik015/ECG-Anomaly-Detection)

`Python` · `PyTorch` · `MLflow` · `SHAP` · `FastAPI` · `GCP Cloud Run` · `scikit-learn`

> Unsupervised time-series anomaly detection on 5,000 cardiac sequences — trained exclusively on normal heartbeats, anomalies surfaced via reconstruction error spikes. 6 MLflow experiments across latent dims 16/32/64 identified latent dim 32 with 0.1 dropout as optimal.

```
Architecture   2-layer LSTM Autoencoder · latent dim 32 · 0.1 dropout (optimal of 3 configs)
Experiment     6 MLflow runs across latent dims 16 / 32 / 64 — systematic hyperparameter search
Threshold      F1-maximized on held-out eval set — not heuristic, not arbitrary
Explainability SHAP values surfacing top reconstruction-error contributors per sequence
Deployment     FastAPI inference endpoint · containerized · live on GCP Cloud Run
```

| F1 Score | ROC-AUC | False Positive Rate |
|:---:|:---:|:---:|
| **0.89** | **0.93** | **↓ 14%** vs baseline |

---

#### [GenFinance: Multi-Agent RAG for Financial Document Analysis](https://github.com/tkaushik015/GenFinance-Multi-Agent-RAG-System-for-Financial-Document-Analysis)

`Python` · `LlamaIndex` · `CrewAI` · `AutoGen` · `DeepEval` · `GPT-4o` · `Claude Sonnet`

> Production-grade multi-agent pipeline ingesting SEC filings and earnings call transcripts — routes queries across specialized agents, benchmarks LLM accuracy, and cuts analysis time from hours to minutes. Benchmarked GPT-4o and Claude Sonnet on 50 chart interpretation tasks using DeepEval — Claude Sonnet delivered better results at lower cost, driving final model selection.

```
Pipeline       LlamaIndex retrieval → CrewAI agent orchestration → AutoGen task delegation
Data Sources   SEC 10-K / 10-Q filings · quarterly earnings call transcripts
Evaluation     DeepEval framework · 50 chart interpretation tasks · hallucination scoring
LLM Selection  Claude Sonnet wins: lower hallucination rate AND lower cost than GPT-4o
Business ROI   Financial document analysis time cut from ~3 hours to under 25 minutes
```

| Analysis Time | Hallucination vs GPT-4o | Cost vs GPT-4o |
|:---:|:---:|:---:|
| **3 hr → 25 min** | **↓ 22%** | **↓ 40%** |

---

#### [BabyWeight Predictor: End-to-End MLOps on Vertex AI and Kubeflow](https://github.com/tkaushik015/CloudML-Engine-End-to-End-MLOps-Pipeline-on-GCP-Vertex-AI-Kubeflow-)

`Python` · `GCP Vertex AI` · `Kubeflow` · `BigQuery ML` · `Cloud Build` · `Terraform` · `Docker`

> Full MLOps lifecycle on GCP — compared BQML and AutoML on Vertex AI Pipelines using BigQuery Natality data, automated retraining with blue/green deployment, and live drift monitoring. Demonstrates production-readiness beyond just model accuracy.

```
Model Comparison  AutoML vs BQML on BigQuery Natality dataset — data-driven model selection
CI/CD Pipeline    Cloud Build triggers → Kubeflow Pipelines → auto-retrain on drift signal
Deployment        Blue/Green strategy · zero-downtime rollout · Vertex AI Model Registry
Monitoring        Feature distribution tracking · data drift alerts · lineage logging
Infrastructure    Terraform-provisioned GCP resources — reproducible, version-controlled IaC
```

| RMSE vs Baseline | Deploy Cycle Time | Deployment Strategy |
|:---:|:---:|:---:|
| **↓ 18%** (AutoML) | **4 hr → 35 min** | Blue/Green + Drift Detection |

---

### 🔹 Academic & Research

- [**DSCI-510-Final-Project**](https://github.com/tkaushik015/DSCI-510-Final-Project) – Advanced **data analysis & visualization** project (USC). End-to-end data collection, wrangling, EDA, and visual storytelling from USC's Applied Data Science program.
- [**Chat-DB-Project**](https://github.com/tkaushik015/Chat-DB-Project-main) – AI-powered **Text-to-SQL chatbot** (Python, Flask, Hugging Face, Airflow). HuggingFace transformer model translating natural language queries to SQL via a Flask API, orchestrated with Airflow.
- [**Real-Time Stock Trading Analytics Platform**](https://github.com/tkaushik015/Real-Time-Stock-Trading-Analytics-Platform) – Built a **real-time trading analytics platform** using APIs & ML insights. Live market data ingestion with ML-driven trading signals on an interactive analytics dashboard.

---

### 🔹 Data Engineering (Azure)

---

#### [NYC-TAXI-DataEngineering-Project](https://github.com/tkaushik015/NYC-TAXi-DataEngineering-Project)

`Azure ADF` · `Databricks` · `Delta Lake` · `PySpark` · `ADLS Gen2`

> Enterprise-scale batch pipeline processing 100GB+ of NYC taxi records. Full Medallion architecture — raw ingestion through to analytics-ready Gold layer serving both BI dashboards and ML feature stores.

```
Bronze   Raw ingestion → Azure Data Lake Storage Gen2 · schema-on-read
Silver   PySpark transforms · deduplication · type casting · null handling · validation
Gold     Aggregated business-ready Delta tables · Z-order optimized for query speed
Scale    100GB+ records · partitioned by date · optimized for Power BI DirectQuery
```

---

#### [Azure End-to-End Data Engineering Pipeline](https://github.com/tkaushik015/Enterprise-Data-Governance-and-Analytics-Framework/blob/main/README.md#clone-the-repo)

`Azure ADF` · `Databricks` · `Delta Lake` · `Unity Catalog` · `Power BI`

> Multi-team enterprise pipeline — incremental ingestion, full data governance with Unity Catalog lineage tracking, and a Power BI semantic layer. Built to production governance standards.

```
Ingestion    Incremental watermark-based loads · change data capture patterns
Governance   Unity Catalog · column-level lineage · row/column access control policies
Reporting    Power BI semantic layer · DirectQuery + import hybrid · scheduled refresh
```

---

#### [Healthcare Data Governance & ETL Optimization (Azure)](https://github.com/tkaushik015/Healthcare-Data-Governance-and-ETL-Optimization-Using-Azure)

`Azure` · `Databricks` · `SCD2` · `Delta Lake`

> SCD Type 2 for full historical tracking, schema evolution handling, and end-to-end data provenance — built to healthcare compliance standards on Azure.

```
SCD Type 2   Full history preserved · current/expired flag · effective dating
Evolution    Automated schema drift detection · backward-compatible migrations
Lineage      Column-level data provenance · audit-ready for healthcare compliance
```

---

### 🔹 Analytics & BI

---

#### [Adidas Sales Performance Analytics](https://github.com/tkaushik015/Adidas-Sales-Performance-Analytics-Insights-Driven-Decision-Making-with-Tableau)

`Tableau` · `SQL` · `Python`

> End-to-end analytics: data cleaning → dimensional modeling → interactive Tableau dashboard surfacing revenue KPIs, regional performance, product mix trends, and retailer-level breakdowns for non-technical stakeholders.

```
Analysis     Revenue trends · regional performance · product category mix · YoY comparisons
Dashboard    Interactive filters by region, retailer, product line · drill-down enabled
Key Insight  Identified top-performing SKUs by margin — not just volume — actionable for buyers
```

---

<p align="center">
<img src="https://github-readme-stats.vercel.app/api?username=tkaushik015&show_icons=true&theme=radical" height="150"/> 
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=tkaushik015&layout=compact&theme=radical" height="150"/>
</p>

</div>
