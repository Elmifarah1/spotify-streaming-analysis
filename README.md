# 🎵 Spotify Streaming Analysis

## 📖 Overview
This project is being developed as part of the **Data Analytics with AI Hackathon: Dashboard Essentials**.  
Our team is analysing Spotify streaming data to explore how different audio features, genres, and release trends influence a song’s popularity.

We are building an **interactive dashboard** that makes it easy for users to explore the data, uncover patterns, and gain insights through clear visual storytelling.  
Alongside the dashboard, the project includes full ETL processing, exploratory analysis, and applied analytics that link directly to the hackathon’s Learning Outcomes (LO1–LO11).

Through collaborative teamwork, the project demonstrates:
- A complete **ETL pipeline** for preparing and validating streaming data  
- Detailed exploration of song attributes and popularity trends  
- An **interactive dashboard** that allows dynamic filtering and visual insights  
- Clear, ethical, and well-documented project delivery aligned with the hackathon specification  

---

## 🧩 Table of Contents
- [Overview](#-overview)
- [Team Members](#-team-members)
- [Project Goal](#-project-goal)
- [Dataset Information](#-dataset-information)
- [ETL & Data Quality](#-etl--data-quality)
- [Exploratory Analysis](#-exploratory-analysis)
- [Analytics & Hypotheses](#-analytics--hypotheses)
- [Dashboard Design](#-dashboard-design)
- [Storytelling & Insights](#-storytelling--insights)
- [Ethics & Governance](#-ethics--governance)
- [Version Control & Documentation](#-version-control--documentation)
- [Presentation](#-presentation)
- [Wrap-Up & Reflections](#-wrap-up--reflections)
- [References](#-references)

---

## 👥 Team Members
| Name | Role 
|:--|:--|
|Elmi Farah|Project Manager |
|  |  |
|  |  |
|  |  |

---

## 🎯 Project Goal
The aim of this project is to analyse Spotify’s music dataset to understand the relationship between song attributes and streaming popularity.  
We want to identify key patterns, trends, and characteristics that drive listener engagement — for example, how features like energy, danceability, tempo, or valence vary across genres and time periods.

Alongside the analysis, we are building an **interactive dashboard** that allows users to:
- Explore audio features across genres and years  
- Visualise trends in popularity over time  
- Compare characteristics of top-performing tracks  
- Discover insights in a clear, accessible way  

Overall, the goal is to use data analytics, visualisation, and ethical AI support to tell a data-driven story about modern music trends.

---

## 📊 Dataset Information
For this project, we are using the **Spotify Tracks Dataset** published on Kaggle.  
Dataset link: *“Spotify Songs Dataset – Kaggle”* by Maharshi Pandya.

The dataset contains thousands of songs with detailed information, including:
- **Track details** (track name, artist, album, release date)
- **Popularity score**
- **Audio features**, such as:
  - danceability  
  - energy  
  - valence (positivity)  
  - tempo  
  - loudness  
  - acousticness  
  - instrumentalness  
  - speechiness  
  - liveness  
- **Genre labels**  
- **Duration** and other metadata  

This dataset is well-structured and ideal for exploring how music characteristics influence streaming behaviour. It supports the creation of visualisations, statistical tests, and interactive dashboards aligned with the hackathon requirements.

---

## ⚙️ ETL & Data Quality
_(Document the process of loading, cleaning, and validating the data. Include missing value handling, type conversions, and data integrity checks.)_

---

## 🔍 Exploratory Analysis
_(Highlight early trends and patterns found in the data through descriptive statistics and visualisations.)_

---

## 📈 Analytics & Hypotheses
_(List your hypotheses, statistical tests, and any analytical models applied.)_

---

## 🖥️ Dashboard Design
This dashboard provides a comprehensive analysis of Spotify streaming data, focusing on what makes songs popular across genres and features. It is organized into three key sections, each designed to explore different dimensions of track characteristics and their influence on popularity.

**[View Dashboard on Tableau Public](https://public.tableau.com/app/profile/andrea.ferreira4559/viz/Spotify-Analysis-Dashboard/Dashboard1)**

---

### 1. Overview & KPIs
This section provides a snapshot of the dataset:

- **Average Popularity:** Shows the mean popularity score across all tracks.  
- **Average Duration:** Highlights the typical track length in milliseconds.  
- **% Explicit Tracks:** Displays the proportion of songs flagged as explicit.  
- **Average Tempo:** Summarizes the average beats per minute (BPM) across tracks.  

---

### 2. Hypothesis Testing
This section investigates three hypotheses about track features and popularity:

- **Hypothesis 1 — Danceability vs Popularity (Scatter Plot):**  
  *Conclusion:* The scatter plot shows a statistically significant **negative correlation** between danceability and popularity. Contrary to the initial hypothesis, tracks with higher danceability scores tend to be less popular in this filtered dataset (Top 1200 tracks, 21 genres). The regression line slopes downward, and the p‑value confirms the relationship is not random.

- **Hypothesis 2 — Explicit vs Non‑Explicit Songs (Box Plot):**  
  *Conclusion:* Explicit songs are not significantly less popular than non‑explicit songs. Both categories show similar distributions, with non‑explicit songs having a tiny edge in median and maximum popularity.

- **Hypothesis 3 — Popularity Distribution by Tempo Range (Bar Chart):**  
  *Conclusion:* The analysis shows that songs above 130 BPM have the highest average popularity, while the hypothesized 110–130 BPM range is slightly lower. Tempo does influence popularity, but the effect is subtle across ranges.

---

### 3. Highlights
This section emphasizes standout tracks:

- **Top 10 Most Popular Tracks (Horizontal Bar Chart):**  
  Displays track names (optionally with artists) ranked by Spotify popularity score.  
  Provides an intuitive highlight of familiar songs, making the dashboard engaging for non‑technical audiences.

---

## Interactivity
To enhance user exploration, the dashboard includes filters tailored to the dataset:

- **Track Genre (Dropdown):** Explore popularity trends across different genres.  
---

### Storytelling
The dashboard is designed as a **narrative journey**:

- It begins with **KPIs** that set the stage, giving users a quick overview of the dataset.  
- It then moves into **hypothesis testing**, where each chart challenges assumptions about what drives popularity — danceability, explicitness, and tempo.  
- Finally, it concludes with **highlights**, showcasing the Top 10 tracks to connect insights back to familiar songs.  

This storytelling flow ensures that **technical audiences** can explore correlations and statistical evidence, while **non‑technical audiences** can follow a clear storyline that connects abstract features (like tempo or danceability) to recognizable music. The combination of overview, analysis, and highlights makes the insights both **accessible and compelling**.

---

## 💡 Storytelling & Insights
_(Explain the key insights derived from your analysis and how the dashboard communicates them visually.)_

---

## ⚖️ Ethics & Governance
_(Summarise ethical considerations — dataset licence, bias, privacy, and governance practices.)_

---

## 🧾 Version Control & Documentation
_(Explain how the project was managed on GitHub — branching, commits, project board workflow, and README updates.)_

---

## 🗣️ Presentation
_(Add notes or a link to your final slides or demo once completed.)_

---

## 🪞 Wrap-Up & Reflections
_(Each team member can share what they learned, challenges faced, or how the collaboration went.)_

---

## 📚 Referencesgit 
_(List dataset source, key libraries, and supporting resources.)