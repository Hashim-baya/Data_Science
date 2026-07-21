# Problem Statement

## Student Academic Performance Analytics and Prediction System

**Author:** Hashim Baya Nassoro (S13/02928/23)
**Institution:** Egerton University — Department of Computer Science
**Supervisor:** Dr. Zachary Bosire
**Date:** 21/07/2026

---

## 1. Background

Educational institutions generate substantial volumes of student data every academic term, including attendance registers, assignment and coursework records, disciplinary logs, library usage statistics, and examination results. In practice, this data is typically stored for administrative and compliance purposes and is rarely subjected to systematic analysis. Consequently, patterns that could inform teaching strategy, resource allocation, and student support — such as which factors most strongly predict poor performance, or which students are quietly falling behind — remain hidden within institutional records.

The emergence of Educational Data Mining (EDM) and Learning Analytics (LA) as established research areas reflects a broader recognition that data-driven approaches can meaningfully improve educational outcomes. However, the practical adoption of these techniques within individual institutions remains limited, largely due to a lack of accessible tooling and analytical capacity rather than a lack of underlying data.

## 2. Problem Statement

Educational institutions collect extensive student records but rarely use them to proactively improve academic performance. Academic performance issues are typically identified only *after* final examinations, at which point opportunities for intervention have already passed. There is currently no systematic, data-driven mechanism within many institutions to:

- Identify, in a rigorous and quantifiable way, which factors most strongly influence a student's final academic performance;
- Estimate a student's likely final examination score before it is recorded;
- Determine, in advance, whether a student is at risk of failing; or
- Flag students who are at risk of underperforming or dropping out early enough for meaningful intervention to occur.

This gap between data availability and data utilization represents a missed opportunity for institutions to move from a *reactive* model of academic support (responding to poor results after the fact) to a *proactive* model (identifying and supporting at-risk students before outcomes are finalized).

## 3. Research Questions

This project is guided by the following research questions:

1. **RQ1:** Which student attributes (demographic, socio-economic, behavioral, and academic) have the strongest influence on final examination performance?
2. **RQ2:** Can a student's final examination score be accurately predicted using historical and behavioral data available prior to the examination?
3. **RQ3:** Can a student's likelihood of passing or failing be reliably classified in advance, using the same set of predictive factors?
4. **RQ4:** Which combination of factors is most indicative of a student being at risk of underperformance or dropout, and can this be used to construct an early-warning indicator?

## 4. Objectives

### 4.1 General Objective

To design and evaluate a data-driven analytics and prediction system that identifies the key drivers of student academic performance and predicts final examination outcomes using regression and classification techniques.

### 4.2 Specific Objectives

1. To collect and document a large-scale, realistic student performance dataset that reflects common real-world data quality challenges (missing values, duplicates, inconsistent categorical labels, and outliers).
2. To clean and pre-process the dataset, resolving identified data quality issues in a documented, reproducible manner.
3. To conduct exploratory data analysis (EDA) to uncover patterns, correlations, and relationships between student attributes and academic performance.
4. To engineer features that improve model interpretability and predictive performance.
5. To build and evaluate a **Linear Regression** model to predict students' continuous final examination scores.
6. To build and evaluate a **Logistic Regression** model to classify students as likely to Pass or Fail.
7. To compare model performance using appropriate quantitative evaluation metrics.
8. To translate model findings into actionable, evidence-based insights and recommendations for academic institutions.

## 5. Justification / Significance

This project addresses a genuine and recurring institutional problem — the underutilization of available student data — using an approach that is both methodologically sound and practically deployable. Its significance lies in three areas:

- **Academic:** The project demonstrates the complete data science lifecycle (collection, cleaning, EDA, feature engineering, modeling, evaluation) applied to a realistically imperfect dataset, rather than a pre-cleaned academic exercise, reflecting the conditions data scientists actually encounter in practice.
- **Practical:** The resulting classification model has direct applicability as an early-warning tool, enabling teachers and administrators to identify at-risk students before final examinations, when intervention is still possible.
- **Contextual:** The project contributes to the growing body of Learning Analytics research relevant to resource-constrained educational settings, where early identification of at-risk students can have an outsized impact on outcomes.

## 6. Scope

This project covers the analysis of a large-scale student performance dataset comprising demographic, socio-economic, behavioral, and academic variables (see `data_dictionary.md` for full column-level documentation). The scope includes:

- Data cleaning and pre-processing
- Exploratory data analysis
- Feature engineering
- Supervised model development: Linear Regression (continuous score prediction) and Logistic Regression (binary pass/fail classification)
- Model evaluation and comparison
- Derivation of business insights and recommendations

**Out of scope:** deep learning approaches, real-time data pipelines, integration with live institutional information systems, and longitudinal (multi-year) tracking of individual students. These are noted as potential directions for future work.

## 7. Expected Outcomes

- A cleaned, analysis-ready student performance dataset with full documentation of the cleaning process applied.
- An exploratory data analysis report identifying key patterns and relationships in the data.
- A trained and evaluated Linear Regression model predicting `Final_Exam_Score`.
- A trained and evaluated Logistic Regression model predicting `Pass_Fail`.
- A model comparison report, evaluated using R², RMSE, and MAE (regression) and Accuracy, Precision, Recall, F1-score, and ROC-AUC (classification).
- A set of business insights and actionable recommendations for academic institutions, derived from model findings.

## 8. Limitations

As with any predictive model built on observational data, this analysis cannot account for every factor influencing student performance — variables such as teacher quality, classroom environment, and student mental health are not captured in the dataset and may account for a portion of unexplained variance in outcomes. Linear and Logistic Regression, while highly interpretable, assume approximately linear relationships between predictors and outcomes and may not fully capture non-linear interactions between variables. These limitations, and their implications for how model outputs should be interpreted, are discussed further in the final analysis report.

---

*Related documents in this repository: `data_dictionary.md` (dataset schema and known data quality issues), `Project_Proposal.docx` (full project proposal), and the analysis notebook(s) implementing the methodology described above.*
