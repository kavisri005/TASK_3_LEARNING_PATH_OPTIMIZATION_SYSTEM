
# Task 3 — Learning Path Optimization System

**AI & ML Internship Program | SkillXYZ Learning**

An intelligent Learning Path Optimization System built on the HarvardX–MITx Person-Course
dataset (2012–2013), covering 641K+ learner-course records across 16 courses and 9 domains.

---

## 📌 Business Understanding

SkillXYZ Learning serves 15M+ learners across 80+ countries, but **43% of learners never
complete their first learning path**. The existing recommendation system is popularity-based
("students who watched this also watched..."), not skill-based — learners skip prerequisites,
abandon paths midway, and revisit failed concepts.

**Goal:** Move beyond a simple "next course" recommender to a full learning journey optimizer
that considers a learner's current skill level, engagement behavior, and course sequence.

## 🔍 Data Exploration

- **Dataset:** HarvardX–MITx Person-Course Academic Dataset
- **Size:** 641,138 rows × 27 columns, 16 courses, 9 domains, ~476K unique learners
- **Key findings:**
  - Computer Science dominates enrollments; Foundational courses make up ~78% of enrollments
  - Certification rates vary sharply by domain and by course level (Foundational vs Advanced)
  - A meaningful share of learners attempt Advanced courses with no Foundational course in
    the same domain — a direct driver of path abandonment

## 🧠 Machine Learning Models

### Model 1 — Learning Readiness Score (Random Forest Classifier)
Predicts the probability a learner will certify based on engagement features (events, active
days, video plays, forum posts, engagement score, grade). Output is scaled into a **0–100
Learning Readiness Score** and bucketed into three bands:
- Ready for Advanced (≥70)
- Building Readiness (40–69)
- Needs Foundation Support (<40)

Evaluated with Accuracy, ROC-AUC, Confusion Matrix, and Feature Importance.

### Model 2 — Learner Segmentation (K-Means Clustering)
Clusters learners into 4 behavioral personas using course breadth, engagement, active days,
completion rate, and readiness score:
- **At-Risk Learner** — low engagement, low completion
- **Casual Explorer** — moderate engagement, low follow-through
- **Steady Progressor** — consistent engagement, moderate completion
- **High Achiever** — high engagement, high completion, high readiness

Visualized via PCA projection; validated with Silhouette Score.

### Skill Gap Analysis
Per-learner logic identifying domains touched-but-not-certified and domains never explored,
used to seed the roadmap generator.

### Personalized Learning Roadmap Generator
Rule-based engine that sequences Foundational → Advanced courses within each skill-gap domain,
adjusts pacing by readiness score, and appends a capstone/certification milestone with an
estimated completion time.

### Career Readiness Indicator (Bonus)
Maps domain coverage/certification to career tracks (Data Scientist, ML Engineer, Public Health
Analyst, Software Engineer, Research Scientist) and produces a 0–100 fit score per career goal.

## 📊 Dashboard

An interactive Plotly dashboard (built directly in the notebook) visualizes:
- Learner persona distribution
- Readiness band distribution
- Average engagement by persona
- Certification rate by domain

## 💡 Business Insights

- Four distinct learner personas require different interventions (nudges, gamification,
  mentorship, advanced tracks)
- Learners skipping foundational courses are a measurable, targetable segment
- Engagement depth (active days, events) predicts certification better than raw enrollment
- Domains with low certification rates are candidates for redesigned onboarding content
- Readiness-based pacing can replace one-size-fits-all course sequencing

## 🚀 Future Enhancements

- Adaptive learning with real-time readiness score updates
- Reinforcement learning for end-to-end path optimization
- AI mentor layer (LLM) to explain recommendations in natural language
- Real-time skill tracking streamed from the LMS

## 🛠️ Tech Stack

Python · Pandas · Scikit-learn (Random Forest, K-Means, PCA) · Matplotlib · Seaborn · Plotly

## 📁 Repository Structure

\```
TASK_3_LEARNING_PATH_OPTIMIZATION_SYSTEM/
├── data/
│   └── cleaned_courses.csv
├── notebooks/
│   └── Task31_Learning_Path_Optimization_System.ipynb
├── dashboards/
│   ├── learner_profile_dashboard.csv
│   ├── learning_roadmaps_dashboard.csv
│   └── course_summary_dashboard.csv
├── reports/
├── README.md
└── requirements.txt
\```

## ▶️ How to Run

1. Open the notebook in Google Colab
2. Run all cells
3. Upload `cleaned_courses.csv` when prompted
4. All models, visualizations, and dashboard exports run end-to-end

---
*Submitted as part of the AI & ML Internship Program — SkillXYZ Learning*
