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
- [Insights](#-insights)
- [Ethics](#-ethics)
- [Version Control & Documentation](#-version-control--documentation)
- [Presentation](#-presentation)
- [Reflections](#-reflections)
- [References](#-references)

---

## 👥 Team Members
| Name | Role |
|:--|:--|
| Elmi Farah | Project Manager |
| Marsella Gounaridou | Data Architect |
| Andrea Ferreira Payares | Data Analyst |

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

**Kaggle — Spotify Track and Audio Features Dataset**  
Downloaded manually and stored locally for ETL processing.

The dataset includes:
- Track metadata  
- Artist information  
- Genre labels  
- Full suite of Spotify audio features (danceability, energy, valence, etc.)

---

### 1. 📁 Spotify Tracks Dataset

#### **File Used**
`tracks.csv` — local copy of the Kaggle dataset.

#### **Dimensions**
Approx. **114,000 rows × 20+ columns** (depending on dataset version).

#### **Key Columns**

| Column | Description |
|--------|-------------|
| `track_id` | Unique Spotify identifier |
| `track_name` | Song title |
| `artists` | Credited artist(s) |
| `track_genre` | Spotify-defined genre |
| `explicit` | 1/0 indicator for explicit lyrics |
| `popularity` | Popularity score (0–100) |
| `danceability` | Rhythmic movement score |
| `energy` | Intensity / loudness perception |
| `valence` | Positivity / mood score |
| `tempo` | Beats per minute |
| `acousticness` | Acoustic feel score |
| `instrumentalness` | Probability track is instrumental |
| `speechiness` | Spoken-word presence |
| `liveness` | Live performance probability |

#### **Removed / Unused Columns**
Dropped to simplify analysis:
- `time_signature`
- `mode`
- Excess descriptive metadata

---

## 📌 Business Requirements

Spotify track popularity depends on many factors — audio characteristics, genre, tempo, and cultural trends.  
Understanding these drivers can support:

- Smarter playlist curation  
- Genre performance benchmarking  
- Artist advisory analytics  
- Better recommendation-system decisions  

---

## 🎯 Research Questions (H1–H3)

Below are the project’s three key hypotheses and summaries.

---

### 🧪 H1 — Do Higher Danceability & Energy Lead to Higher Popularity?

#### **Hypothesis**
**H1:** Tracks with higher danceability and energy will have higher popularity.

This tests whether rhythmic intensity and high-energy songs are more likely to be streamed.

#### **Summary of Findings**

- **Danceability** has a *very weak positive correlation* with popularity (~0.09).  
- **Energy** has a *slightly negative* or near-zero correlation.  
- **Overall:** Audio features alone do **not** strongly influence popularity.  
- External factors (playlisting, marketing, artist fame) likely matter more.

#### **Conclusion**
❌ **H1 is not supported.**  
Higher danceability and energy do *not* strongly predict popularity.

#### **Visual Evidence**

**1. Correlation Heatmap**  
Shows correlation values between popularity and audio features.

- All values near zero → no meaningful predictive relationship.  

*(Insert heatmap image here.)*

**2. Hexbin Plot (Energy vs Popularity — Sample 500)**  
Uses the first 500 rows for visibility.

- Trend line slopes slightly downward  
- No strong pattern  
- Popularity stays mid-range regardless of energy  

*(Insert hexbin plot here.)*

#### **Final Assessment**

| Evidence Type | Result | Supports H1? |
|---------------|--------|--------------|
| Correlation Heatmap | Weak correlations | ❌ No |
| Hexbin Plot | Slight negative pattern | ❌ No |
| Statistical Summary | No strong effects | ❌ No |

---

### 🧪 H2 — Explicit Tracks Are Less Popular Than Clean Tracks

#### **Hypothesis**
**H2:** Explicit tracks have lower average popularity than clean tracks.

#### **Statistical Test**
Welch’s t-test comparing explicit vs. non-explicit tracks.

Replace values with your own results:
- `n_explicit = X`  
- `n_clean = Y`  
- `t = t_value`  
- `p = p_value`  
- `Cohen’s d = d_value`  
- `mean_explicit = E`  
- `mean_clean = C`

**Interpretation:**  
- If **p < 0.05** → difference is statistically significant  
- Cohen’s d shows effect size (small, medium, large)

#### **Visual Evidence**

- **Boxplot — Popularity by Explicit Flag:**  
  Slightly higher median popularity for clean tracks.

- **Histogram — Popularity Distribution:**  
  Clean tracks dominate across most popularity ranges.

- **Violin Plot (Plotly):**  
  Clean tracks show a tighter distribution with a slightly higher central value.

#### **Conclusion**
✔️ **H2 is supported, but the effect is small.**  

Explicit songs tend to be **slightly** less popular, but the difference is not dramatic.

---

### 🧪 H3 — Genre Popularity Differences
 
#### **Hypothesis**
Popularity differs significantly across genres.

#### **Statistical Test**
One-way ANOVA on the top 8 most common genres.

**Result:**  
The ANOVA test shows a significant difference between genre groups.  
✔️ **H3 is supported.**

#### **Visual Analysis**

- **Median Popularity by Genre (Bar Plot):**  
  Shows which genres consistently perform better.

#### **Interpretation**

1. **Audio characteristics & popularity:**  
   Weak or inconsistent relationships.

2. **Explicit vs clean tracks:**  
   Clean tracks perform slightly better.

3. **Genre differences:**  
   Genre has the strongest effect on popularity.

---

## 🧱 Project Plan & Methodology

### **1. Data Acquisition**
- Downloaded from Kaggle  
- Loaded via `pandas.read_csv()`  
- Initial checks: shape, dtypes, distributions, missing values  

### **2. Data Cleaning & Preprocessing**

✔ Missing values handled  
✔ Numeric conversions  
✔ Boolean standardisation  
✔ Duplicate removal  
✔ Genre harmonisation  
✔ Column reduction  
✔ Validation of ranges, dtypes, and counts  

Cleaned dataset saved to `data/processed/`.

### **3. Exploratory Data Analysis**
Using:
- Seaborn  
- Matplotlib  
- Plotly  

Focus areas:
- Summary statistics  
- Popularity patterns  
- Genre frequency  
- Correlation structure  

### **4. Data Preparation**
Prepared for:
- Hypothesis testing  
- Group comparisons  
- Visualisation  

Transformations:
- Explicit → binary  
- Genre filtering  
- Outlier removal  

### **5. Statistical Analysis**
Techniques:
- Correlation matrix  
- Welch’s t-test  
- One-way ANOVA  

Libraries:
- SciPy  
- NumPy  
- Pandas  

### **6. Visualisation**
Tools:
- Matplotlib  
- Seaborn  
- Plotly  

Visuals include:
- Heatmaps  
- Hexbin plots  
- Boxplots  
- Violin plots  
- Bar charts  

---

## 🗂 Data Management

### ✔ Version Control
- Git + GitHub branches  
- Pull requests  
- Project board tracking  

### ✔ Data Storage
- `data/raw/`  
- `data/processed/`  

### ✔ Documentation
- Step-by-step explanations in notebooks  
- Debugging notes  

---

## ⚙ Methodology Justification

- Kaggle dataset is reliable and structured  
- ETL ensures cleanliness for valid statistics  
- EDA and tests validate relationships visually and numerically  
- Workflow is reproducible and transparent  

---

## 📦 Tools Used

- **Pandas**  
- **NumPy**  
- **Matplotlib**  
- **Seaborn**  
- **Plotly**  
- **SciPy**  
- **Scikit-learn**

---

## ⚠️ Limitations

1. Genre imbalance  
2. Popularity changes over time  
3. Audio feature estimation by Spotify  
4. Explicit flag lacks nuance  

---

## 📘 Knowledge Gained

- Inferential statistics  
- ETL debugging  
- Advanced data cleaning  
- Grouped analysis  

---

## 🔍 Exploratory Analysis

Before testing our hypotheses, we carried out exploratory data analysis (EDA) to understand the overall structure and behaviour of the Spotify tracks dataset. This helped us spot early patterns, check for issues, and decide which features were most useful for deeper analysis.

### General Overview

We started with some basic checks:

- Looked at the **shape of the dataset** (rows and columns).  
- Reviewed **data types** to make sure numeric fields (e.g. popularity, tempo, danceability) were correctly stored as numbers.  
- Checked for **missing values** and duplicates, especially in key fields like `track_id` and `popularity`.  
- Confirmed that popularity scores fell within the expected **0–100** range.  

This initial step confirmed that the dataset was well structured and suitable for analysis after cleaning.

### Distributions & Descriptive Statistics

We then explored how key features are distributed:

- **Popularity:** Most tracks sit in a “moderately popular” range rather than extremely high or low.  
- **Tempo:** The majority of songs cluster around a typical BPM range, with fewer very slow or very fast tracks.  
- **Duration:** Most tracks fall within a standard song length, with only a small number of very long or very short tracks.  

We used summary statistics (mean, median, min, max) and histograms to spot outliers and skewed distributions.

### Correlation Checks

To understand how audio features relate to popularity, we created a **correlation heatmap** including variables such as:

- popularity  
- danceability  
- energy  
- valence  
- tempo  

The correlations with popularity were generally **weak**, which suggested that popularity cannot be explained by a single audio feature alone. This result helped guide our hypothesis testing and dashboard design.

### Genre & Explicitness Patterns

We also explored how tracks differ by:

- **Genre:** Looked at the most common genres in the dataset and their average popularity.  
- **Explicit flag:** Compared the number and proportion of explicit versus non-explicit tracks.  

These early comparisons showed that:

- Some genres appear more frequently and may influence overall trends.  
- Explicit tracks form a clear subset that can be analysed separately when testing popularity differences.  

### Visualisation Tools

For EDA, we mainly used:

- **Seaborn and Matplotlib** for histograms, boxplots, and correlation heatmaps.  
- **Plotly** for interactive exploration when needed.  

Overall, the exploratory analysis gave us a solid understanding of the dataset, highlighted potential limitations (such as weak correlations and genre imbalance), and helped us shape the three main hypotheses we tested later in the project.

---

## 📈 Analytics & Hypotheses

Our analysis focused on three main hypotheses:

1. **H1 – Do higher danceability and energy lead to higher popularity?**  
2. **H2 – Are explicit tracks less popular than clean tracks?**  
3. **H3 – Does popularity differ significantly across genres?**  

We combined **statistical tests** (correlations, Welch’s t-test, one-way ANOVA) with **visual analysis** to test these questions. The detailed results and interpretations are documented in the H1, H2, and H3 sections above.

---

## 🖥️ Dashboard Design

This dashboard provides a comprehensive analysis of Spotify streaming data, focusing on what makes songs popular across genres and features. It is organised into three key sections, each designed to explore different dimensions of track characteristics and their influence on popularity.

**[View Dashboard on Tableau Public](https://public.tableau.com/app/profile/andrea.ferreira4559/viz/Spotify-Analysis-Dashboard/Dashboard1)**

---

### 1. Overview & KPIs

This section provides a snapshot of the dataset:

- **Average Popularity:** Mean popularity score across all tracks.  
- **Average Duration:** Typical track length in milliseconds.  
- **% Explicit Tracks:** Proportion of songs flagged as explicit.  
- **Average Tempo:** Average beats per minute (BPM) across tracks.  

---

### 2. Hypothesis Testing

This section visualises the three core hypotheses:

- **Hypothesis 1 — Danceability vs Popularity (Scatter Plot):**  
  *Conclusion:* The scatter plot shows a statistically significant **negative correlation** between danceability and popularity. Contrary to the initial hypothesis, tracks with higher danceability scores tend to be less popular in this filtered dataset (Top 1200 tracks, 21 genres). The regression line slopes downward, and the p-value confirms the relationship is not random.

- **Hypothesis 2 — Explicit vs Non-Explicit Songs (Box Plot):**  
  *Conclusion:* Explicit songs are not significantly less popular than non-explicit songs. Both categories show similar distributions, with non-explicit songs having a tiny edge in median and maximum popularity.

- **Hypothesis 3 — Popularity Distribution by Tempo Range (Bar Chart):**  
  *Conclusion:* The analysis shows that songs above 130 BPM have the highest average popularity, while the hypothesised 110–130 BPM range is slightly lower. Tempo does influence popularity, but the effect is subtle across ranges.

---

### 3. Highlights

This section emphasises standout tracks:

- **Top 10 Most Popular Tracks (Horizontal Bar Chart):**  
  Displays track names (optionally with artists) ranked by Spotify popularity score.  
  Provides an intuitive highlight of familiar songs, making the dashboard engaging for non-technical audiences.

---

### Interactivity

To enhance user exploration, the dashboard includes filters tailored to the dataset:

- **Track Genre (Dropdown):** Explore popularity trends across different genres.  

---

### Storytelling

The dashboard is designed as a **narrative journey**:

- It begins with **KPIs** that set the stage, giving users a quick overview of the dataset.  
- It then moves into **hypothesis testing**, where each chart challenges assumptions about what drives popularity — danceability, explicitness, and tempo.  
- Finally, it concludes with **highlights**, showcasing the Top 10 tracks to connect insights back to familiar songs.  

This storytelling flow ensures that **technical audiences** can explore correlations and statistical evidence, while **non-technical audiences** can follow a clear storyline that connects abstract features (like tempo or danceability) to recognisable music. The combination of overview, analysis, and highlights makes the insights both **accessible and compelling**.

---

## 💡 Insights

From analysing the Spotify dataset and exploring the dashboard, we were able to identify several interesting patterns about what makes certain songs more popular than others. These insights are based on the audio features, popularity scores, and trends across multiple genres.

### General Track Characteristics

- The average popularity across the dataset shows that most tracks fall into a “moderately popular” range rather than extremely high or low.  
- The majority of songs have an average tempo and duration, suggesting that extremely long or unusually fast/slow tracks are less common in mainstream listening.  

### Danceability vs Popularity

One of our original expectations was that highly danceable songs would be more popular. However, the data showed the **opposite** trend.  
There is a **small negative correlation**, meaning that in this dataset, tracks with higher danceability scores tended to have slightly lower popularity. This highlights how assumptions do not always match real data.

### Explicit vs Non-Explicit Songs

Popular belief might suggest that explicit songs are less likely to perform well. Our analysis showed that:

- **Explicit songs are not significantly less popular**  
- Both explicit and non-explicit songs have very similar popularity distributions  

This means explicit content does not strongly influence how well a track performs.

### Tempo Ranges & Popularity

Tempo does appear to have a small influence on popularity:

- Tracks with a **tempo above 130 BPM** had the highest average popularity  
- The 110–130 BPM range, which is often seen as a “sweet spot” for energetic songs, was slightly lower  

The effect is subtle, but it shows that faster songs may have a slight advantage in this dataset.

### Top 10 Most Popular Songs

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

### Branches Used

Each member created a personal branch for their tasks:

- **Marsella-branch** – ETL development, data cleaning, and data validation  
- **Elmi-branch** – Project management, README development, documentation, and workflow setup  
- **Andrea-branch** – Exploratory analysis, visualisations, and dashboard creation  

Working from separate branches meant we could all build different parts of the project at the same time without interfering with each other’s files.

### Workflow

- We pulled the latest changes from `main` before starting new work.  
- Each member committed frequently with clear messages to show progress.  
- Once a piece of work was ready, it was pushed to GitHub and reviewed.  
- We merged branches into `main` through pull requests after checking for conflicts and testing the changes.  

This ensured the codebase stayed clean and stable throughout the hackathon.

### Project Board Usage

We used a shared **GitHub Project Board** to manage tasks from start to finish. Our board included:

- **Backlog** – All ideas and tasks we wanted to include  
- **To Do** – Tasks ready to work on  
- **In Progress** – Tasks actively being completed  
- **Review / QA** – Items that needed checking before final approval  
- **Done** – Completed tasks  

We moved tasks across the board as we progressed, which helped us stay organised, divide work fairly, and keep track of deadlines.

### Documentation

- The README file was updated throughout the hackathon to reflect real progress.  
- All sections (ETL, analysis, dashboard, ethics, insights, etc.) were filled based on completed project work.  
- Screenshots, links, and explanations were added as the dashboard developed.  

This helped ensure clarity for judges and made our workflow transparent from start to finish.

---

## 🗣️ Presentation

_(Add notes or a link to your final slides or demo once completed.)_

---

## 🪞 Reflections

_(Each team member can share what they learned, challenges faced, or how the collaboration went.)_

---

## 📚 References 

_(List dataset source, key libraries, and supporting resources.)_