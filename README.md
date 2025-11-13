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
- [Insights](#-storytelling--insights)
- [Ethics & Governance](#-ethics--governance)
- [Version Control & Documentation](#-version-control--documentation)
- [Presentation](#-presentation)
- [Reflections](#-wrap-up--reflections)
- [References](#-references)

---

## 👥 Team Members
| Name | Role 
|:--|:--|
|Elmi Farah|Project Manager|
|Marsella Gounaridou|Data Architect|
|Andrea Ferreira Payares|Data Analyst|

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
## 💡 Insights

From analysing the Spotify dataset and exploring the dashboard, we were able to identify several interesting patterns about what makes certain songs more popular than others. These insights are based on the audio features, popularity scores, and trends across multiple genres.

### **General Track Characteristics**
- The average popularity across the dataset shows that most tracks fall into a “moderately popular” range rather than extremely high or low.
- The majority of songs have an average tempo and duration, suggesting that extremely long or unusually fast/slow tracks are less common in mainstream listening.

### **Danceability vs Popularity**
One of our original expectations was that highly danceable songs would be more popular. However, the data showed the **opposite** trend.  
There is a **small negative correlation**, meaning that in this dataset, tracks with higher danceability scores tended to have slightly lower popularity. This highlights how assumptions do not always match real data.

### **Explicit vs Non-Explicit Songs**
Popular belief might suggest that explicit songs are less likely to perform well. Our analysis showed that:
- **Explicit songs are not significantly less popular**  
- Both explicit and non-explicit songs have very similar popularity distributions  
This means explicit content does not strongly influence how well a track performs.

### **Tempo Ranges & Popularity**
Tempo does appear to have a small influence on popularity:
- Tracks with a **tempo above 130 BPM** had the highest average popularity  
- The 110–130 BPM range, which is often seen as a “sweet spot” for energetic songs, was slightly lower  
The effect is subtle, but it shows that faster songs may have a slight advantage in this dataset.

### **Top 10 Most Popular Songs**
The top tracks give a quick snapshot of what listeners responded to the most. These songs usually share common traits:
- Clear production  
- Strong rhythmic structure  
- Recognisable artists  
- Broad genre appeal  
This section helps users connect the data back to real music they may know.

---

Overall, the analysis shows that song popularity is influenced by multiple factors rather than a single feature. Danceability, tempo, and explicit content all play roles, but none of them alone can fully explain popularity. The dashboard helps users explore these relationships visually and understand how different characteristics interact.

---
## ⚖️ Ethics

For this project, we used a public Spotify dataset from Kaggle that contains information about songs, their audio features, and popularity scores. The dataset does **not** include any personal listener data, so there are no privacy concerns or risks around identifying individuals. Everything we analysed is purely track-level information.

While working on the project, we kept a few ethical points in mind:

- **Dataset Source & Use:**  
  The dataset is publicly available and shared for learning and analysis. We are using it fairly and giving full credit to the original creator on Kaggle.

- **No Personal Data:**  
  Since the data only includes details about songs and artists, it is safe to use and does not require any special permissions.

- **Possible Bias in the Data:**  
  The dataset may not represent all genres, regions, or artists equally. Some musical styles may appear more often than others, which means certain insights might lean toward the genres that are over-represented.

- **Popularity Score Limitations:**  
  Spotify’s popularity metric is based on their own internal system. This could favour certain artists, trends, or markets. For this reason, we treat popularity as an indicator, not a perfect measure.

- **Responsible Interpretation:**  
  When presenting insights, we avoid overstating results or suggesting causation where it doesn’t exist. Our analysis is based only on what the dataset shows, and we highlight limitations where needed.

Overall, we made sure the data was used responsibly, respectfully, and within the boundaries of what the dataset allows. The goal of this project is purely educational, focused on building skills in ETL, analysis, visualisation, and teamwork.

---
## 🧾 Version Control & Documentation

We used Git and GitHub throughout the project to collaborate smoothly and keep all work organised. Each team member worked from their own dedicated branch to avoid conflicts and to keep changes clear and easy to track.

### **Branches Used**
Each member created a personal branch for their tasks:
- **Marsella-branch** – ETL development, data cleaning, and data validation  
- **Elmi-branch** – Project management, README development, documentation, and workflow setup  
- **Andrea-branch** – Exploratory analysis, visualisations, and dashboard creation  

Working from separate branches meant we could all build different parts of the project at the same time without interfering with each other’s files.

### **Workflow**
- We pulled the latest changes from `main` before starting new work.  
- Each member committed frequently with clear messages to show progress.  
- Once a piece of work was ready, it was pushed to GitHub and reviewed.  
- We merged branches into `main` through pull requests after checking for conflicts and testing the changes.

This ensured the codebase stayed clean and stable throughout the hackathon.

### **Project Board Usage**
We used a shared **GitHub Project Board** to manage tasks from start to finish. Our board included:
- **Backlog** – All ideas and tasks we wanted to include  
- **To Do** – Tasks ready to work on  
- **In Progress** – Tasks actively being completed  
- **Review / QA** – Items that needed checking before final approval  
- **Done** – Completed tasks  

We moved tasks across the board as we progressed, which helped us stay organised, divide work fairly, and keep track of deadlines.

### **Documentation**
- The README file was updated throughout the hackathon to reflect real progress.
- All sections (ETL, analysis, dashboard, ethics, insights, etc.) were filled based on completed project work.
- Screenshots, links, and explanations were added as the dashboard developed.
- This helped ensure clarity for judges and made our workflow transparent from start to finish.

Overall, version control and structured documentation helped us collaborate effectively, avoid issues, and stay aligned as a team while building the project.

---

## 🗣️ Presentation
_(Add notes or a link to your final slides or demo once completed.)_

---

## 🪞 Reflections
_(Each team member can share what they learned, challenges faced, or how the collaboration went.)_

---

## 📚 References 
_(List dataset source, key libraries, and supporting resources.)