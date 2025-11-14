# 🎵 Spotify Streaming Analysis — ETL, EDA, Statistical Testing & Dashboard


# 🧩 Table of Contents

- [Overview](#-overview)  
- [Team Members](#-team-members)  
- [Project Goal & Business Requirements](#-project-goal--business-requirements)  
- [Dataset Information](#-dataset-information)  
- [ETL Pipeline & Data Preparation](#-etl-pipeline--data-preparation)  
- [Exploratory Analysis & Correlations](#-exploratory-analysis--correlations)  
- [Hypothesis Testing](#-hypothesis-testing)  
  - [H1 — Danceability & Energy vs Popularity](#h1--danceability--energy-vs-popularity)  
  - [H2 — Explicit vs Clean Tracks](#h2--explicit-vs-clean-tracks)  
  - [H3 — Genre Popularity Differences](#h3--genre-popularity-differences)  
- [Dashboard Design & Storytelling](#-dashboard-design--storytelling)  
- [Data Management, Tools & Methodology](#-data-management-tools--methodology)  
- [Key Insights](#-key-insights)  
- [Ethics, Generative AI & Governance](#-ethics-generative-ai--governance)  
- [Limitations & Known Issues](#-limitations--known-issues)  
- [Version Control & Collaboration](#-version-control--collaboration)  
- [Reflections & Learning](#-reflections--learning)  
- [References](#-references)

---
You can view the interactive dashboard here: https://public.tableau.com/app/profile/andrea.ferreira4559/viz/Spotify-Analysis-Dashboard/Dashboard1

![Dashboard](https://github.com/user-attachments/assets/95d52e73-e820-4fbd-bf32-4b162c157534)



## 📖 Overview

This repository contains the work completed for the **Data Analytics with AI Hackathon: Dashboard Essentials**, focused on analysing Spotify track-level data to understand what drives a song’s popularity.

From a data-analytics perspective, the project delivers:

- A transparent **ETL and data-cleaning pipeline**
- **Exploratory Data Analysis (EDA)**, including correlation analysis
- **Hypothesis testing** using correlation, Welch’s t-test, and one-way ANOVA
- An interactive **Tableau dashboard** to communicate findings
- Supporting documentation on **data ethics, limitations, and tooling**
- Collaborative development using **GitHub version control**

---

# 👥 Team Members

| Name                     | Role                |
|--------------------------|---------------------|
| **Elmi Farah**           | Project Manager     |
| **Marsella Gounaridou**  | Data Architect      |
| **Andrea Ferreira Payares** | Data Analyst   |

---

# 🎯 Project Goal & Business Requirements

Spotify track popularity is influenced by artistic, cultural, and behavioural factors. As data analysts, our goal is to:

- Understand the **drivers of track popularity**
- Quantify relationships between **audio features, explicit content, genre, and popularity**
- Provide **evidence-based insights** to support:
  - Smarter **playlist curation**
  - **Genre performance** benchmarking
  - **Artist advisory** analytics
  - Future **recommendation-system improvements**

We focus on three core **research questions**:

1. **Do audio characteristics (danceability, energy, etc.) influence popularity?**  
2. **Are explicit tracks less popular than clean tracks?**  
3. **Do genres differ significantly in popularity?**  

These are formalised as hypotheses H1–H3 in the **Hypothesis Testing** section.

---

# 📊 Dataset Information

## Source

- **: — Spotify Track and Audio Features Dataset**
- Downloaded manually and stored locally for ETL processing.

## File Used

- `tracks.csv` — local copy of the Kaggle dataset

## Dimensions

- Approx. **114,000 rows × 20+ columns** (varies slightly by dataset version).

## Key Columns

| Column                         | Description                                   |
|--------------------------------|-----------------------------------------------|
| `track_id`                     | Unique Spotify identifier                     |
| `track_name`                   | Song title                                    |
| `artists`                      | Credited artist(s)                            |
| `track_genre`                  | Spotify-defined genre                         |
| `explicit`                     | 1/0 indicator for explicit lyrics             |
| `popularity`                   | Popularity score (0–100)                      |
| `danceability`                 | Rhythmic movement score                       |
| `energy`                       | Perceived intensity/aggression                |
| `valence`                      | Positivity / mood score                       |
| `tempo`                        | Beats per minute                              |
| `acousticness`                 | Acoustic character                            |
| `instrumentalness`            | Instrumental dominance                        |
| `speechiness`                 | Spoken-word content                           |
| (plus other Spotify audio features) |                                           |

### Removed / Unused Columns

To simplify analysis and avoid unnecessary noise, we dropped:

- `time_signature`  
- `mode`  
- Additional overly descriptive metadata fields not used in modelling or EDA  

---

# ⚙️ ETL Pipeline & Data Preparation

We built a structured ETL process to ensure data quality, reproducibility, and suitability for statistical tests and dashboarding.

## 1. Data Acquisition

- Downloaded dataset from Kaggle
- Loaded with `pandas.read_csv()`
- Performed initial checks:
  - Shape (rows/columns)
  - Column names and dtypes
  - Basic distribution patterns
  - Structural inconsistencies or obvious errors

## 2. Data Cleaning & Preprocessing

### ✔ Handling Missing Values

- Inspected completeness of:
  - `popularity`
  - Core audio features (`danceability`, `energy`, `tempo`, etc.)
- Removed rows missing **essential analysis fields**
- Ensured no `NaN` values in key numeric columns used for statistics

### ✔ Standardising Data Types

- Converted string-formatted numeric columns → `float`/`int`
- Normalised booleans (`explicit` → 0/1)
- Standardised genre strings:
  - Lowercased
  - Trimmed whitespace
  - Applied consistent hyphen use

### ✔ Removing Duplicates

- Removed duplicate `track_id` entries
- Dropped fully duplicated rows

### ✔ Genre Harmonisation

- Cleaned genre labels (lowercasing, hyphen consistency)
- For hypothesis testing (ANOVA), **removed rare genres** with fewer than 30 tracks to ensure stable group sizes

### ✔ Column Reduction

- Dropped metadata that did not add analytical value (e.g., fields not used in EDA, modelling, or dashboard)

### ✔ Final Validation

- Rechecked row counts after filtering
- Confirmed dtypes were as expected
- Validated that audio features fell within plausible ranges (e.g., 0–1 for normalised features)

The final cleaned dataset was saved under `data/processed/` and used in the EDA, hypothesis testing, and dashboard.

---

# 🔍 Exploratory Analysis & Correlations

## EDA Focus Areas

We performed exploratory analysis to understand:

- Overall **popularity distribution**
- **Genre frequencies** and imbalance
- Outliers and skewness in audio features
- Pairwise correlations between features and popularity

### Visual Tools

- **Seaborn**: boxplots, histograms, heatmaps  
- **Matplotlib**: hexbin plots, bar charts  
- **Plotly**: interactive violin plots  

## Correlation Analysis

A correlation heatmap between audio features and popularity revealed:

| Feature        | Correlation with Popularity | Interpretation                          |
|----------------|-----------------------------|-----------------------------------------|
| Danceability   | ≈ **+0.09**                 | Very small positive correlation         |
| Energy         | ≈ **0 / slightly negative** | No meaningful linear relationship       |
| Valence        | ≈ 0                         | Mood not strongly tied to popularity    |
| Tempo          | ≈ 0                         | Little to no linear relationship        |
| Acousticness   | ≈ 0                         | No strong association                   |
| Other features | ≈ 0                         | All near-zero correlations              |


**Key EDA conclusion:**  
Audio features show **very weak linear correlations** with popularity, suggesting that popularity is heavily influenced by external factors (e.g., playlisting, artist fame, marketing) rather than the raw audio feature values alone.

---

# 📈 Hypothesis Testing

We formalised our core research questions into three hypotheses and tested them using appropriate statistical methods.

---

## H1 — Danceability & Energy vs Popularity

### Hypothesis

> **H1:** Tracks with higher danceability and energy are associated with higher popularity.

This hypothesis assesses whether Spotify’s popularity score (0–100) increases for songs with:

- **Higher rhythmic intensity** (`danceability`)
- **Higher perceived intensity** (`energy`)

### Method

- **Correlation analysis** between:
  - Popularity vs `danceability`
  - Popularity vs `energy`
- Visual validation through:
  - **Seaborn correlation heatmap**
  - **Matplotlib hexbin plot** (energy vs popularity, using a 500-track sample to reduce overplotting)

### Findings

- **Danceability**:  
  - Very small positive correlation (~0.09) with popularity  
- **Energy**:  
  - No meaningful correlation; slightly negative in this sample  
- Heatmap shows **all correlations with popularity close to zero**
- Hexbin plot trend line for energy vs popularity slopes **slightly downward**, confirming at best a weak negative relationship


| Correlation Heatmap | Energy vs Popularity (Hexbin) |
|---------------------|-------------------------------|
| <img src="https://github.com/user-attachments/assets/378dc126-c177-4ab3-9ec3-182a0ad511a0" width="350"/> | <img src="https://github.com/user-attachments/assets/66137047-9202-45df-83e1-058c2752d139" width="350"/> |


### Conclusion

- **H1 is not supported.**  
- There is **no strong evidence** that higher danceability or energy leads to higher popularity.
- Overall statistical pattern indicates that audio intensity and rhythmic movement alone **do not strongly influence popularity** in this dataset.

---

## H2 — Explicit vs Clean Tracks

### Hypothesis

> **H2:** Explicit tracks have lower average popularity than clean (non-explicit) tracks.

This tests whether the `explicit` flag is associated with a difference in popularity.

### Method

- **Welch’s t-test** to compare mean popularity between:
  - Explicit tracks (`explicit = 1`)
  - Clean tracks (`explicit = 0`)
- Visualisations:
  - **Seaborn boxplot** (popularity by explicit flag)
  - **Matplotlib histogram** (popularity distribution by explicit flag)
  - **Plotly violin plot** (explicit vs clean)

### Statistical Interpretation

- Welch’s t-test is appropriate due to potentially unequal variances and group sizes.
- Key indicators:
  - **p-value**:
    - If `p < 0.05`, difference in means is statistically significant
  - **Cohen’s d**:
    - Effect size (small / medium / large)

### Findings

From the visuals and tests:

- Clean tracks show **slightly higher median and average popularity**
- Explicit tracks:
  - Have more spread
  - Display more low-popularity observations
- Distributions overlap substantially, indicating a **small but real effect**
- Welch’s t-test indicates the difference is **statistically significant**, with a **small effect size**

| Boxplot (Explicit vs Clean) | Histogram (Explicit vs Clean) |
|-----------------------------|-------------------------------|
| <img src="https://github.com/user-attachments/assets/0c268ca4-3557-46fb-a0e7-19a4870a6ee9" width="350"/> | <img src="https://github.com/user-attachments/assets/01402aeb-d02d-4b30-b358-a76d844f0537" width="350"/> |

![violin](https://github.com/user-attachments/assets/59500c6d-06ca-4ef3-8493-5b9539c78120)

### Conclusion

- **H2 is supported, but the effect is modest.**
- Explicit tracks are, on average, **slightly less popular** than clean tracks.
- Explicitness appears to influence popularity **modestly**, not strongly enough to be considered the primary driver.

---

## H3 — Genre Popularity Differences

### Hypothesis

> **H3:** Popularity differs significantly across genres.

This explores whether certain genres consistently achieve higher popularity scores.

### Method

- **One-way ANOVA** comparing popularity across the **top 8 most frequent genres**
- Requirements:
  - Each genre group must contain **at least 30 tracks**
- Visualisations:
  - **Seaborn bar plot** of median popularity by genre
  - Distribution plots to inspect variability within each genre

### Findings

- One-way ANOVA returns a **statistically significant result** (p < 0.05)
- Median popularity by genre varies visibly:
  - Some genres consistently exhibit higher central tendency in popularity
  - Others are consistently lower, even when controlling for basic cleaning rules

| Genre Popularity Lineplot | Genre Median Popularity Barplot |
|---------------------------|----------------------------------|
| <img src="https://github.com/user-attachments/assets/de2f8795-cb7c-4094-97da-24a7b56fb2eb" width="350"/> | <img src="https://github.com/user-attachments/assets/38f27ff5-db16-41bf-92a4-01f3e7530286" width="350"/> |


### Conclusion

- **H3 is supported.**
- Genre is a **meaningful factor** in popularity, with significant differences across genres.

---

# 🖥️ Dashboard Design & Storytelling

🔗 **Tableau Public Dashboard**  
https://public.tableau.com/app/profile/andrea.ferreira4559/viz/Spotify-Analysis-Dashboard/Dashboard1  

The dashboard translates the ETL and statistical findings into an interactive experience.

## 1. Overview & KPIs

High-level metrics summarise the dataset:

- **Average Popularity**
- **Average Track Duration**
- **Percentage of Explicit Tracks**
- **Average Tempo**

These KPIs provide context before the user dives into relationships and genres.

---

## 2. Hypotheses & Correlation Exploration

The second section focuses on **feature-popularity relationships**, directly reflecting H1–H3:

### Danceability vs Popularity (Scatter Plot)

- Visualises the relationship between **danceability** and **popularity**
- Trend/regression line reveals a **slight negative or near-flat relationship** in the filtered top tracks
- Confirms that simple “more danceable = more popular” assumptions do **not** hold strongly

  ![Hypothesis 1 — Danceability vs Popularity (Scatter Plot)](https://github.com/user-attachments/assets/159c11da-21cc-4a76-b0f5-00f1c36a1d82)


### Explicit vs Non-Explicit (Box Plot)

- Compares popularity distributions by `explicit` flag
- Clean tracks show:
  - Slightly higher median popularity
- Explicit tracks show:
  - Greater variability and more low-popularity tracks
- Aligns with the **Welch’s t-test** results for H2

### Popularity by Tempo Range (Bar Chart)

- Groups tracks into tempo bands (e.g., `<110 BPM`, `110–130 BPM`, `>130 BPM`)
- Shows that **tracks above 130 BPM** have the **highest average popularity**
- Supports the idea of a mild relationship between higher tempo and popularity, though overall correlations remain weak

Together, these visuals allow users to **explore correlations and distributions** behind the hypotheses.

---

## 3. Top 10 Most Popular Tracks

- **Horizontal bar chart** of the **Top 10 tracks** by popularity
- Presents a recognisable view of individual songs and artists
- Connects abstract statistical observations back to real-world, well-known tracks

![Top10 Most Popular Tracks ](https://github.com/user-attachments/assets/789013b2-9162-48e6-86af-afcde1d04ff9)

---

## 🎛️ Interactivity & User Experience

- **Genre filter** (dropdown) to focus on specific genres and review how correlations and distributions change
- Hover tooltips with detailed track-level metrics
- Cross-chart filtering, where applicable, to support **self-service exploration**

---

## 📖 Storytelling Flow

The dashboard is structured as a **narrative journey**:

1. **Start with KPIs** → “What does this dataset look like overall?”  
2. **Move to hypotheses and correlations** → “How do audio features, explicitness, and tempo relate to popularity?”  
3. **End with top tracks** → “Which songs exemplify these patterns?”

This design ensures:

- **Technical users** can follow the logic from ETL → EDA → statistics → visuals.
- **Non-technical users** can intuitively explore through charts, filters, and familiar songs.

---

# 📂 Data Management, Tools & Methodology

## Data Management

- **Version Control**:
  - Git + GitHub for tracking notebook changes and code evolution
  - Raw data excluded from version control via `.gitignore`  
- **Storage Structure**:
  - `data/raw/` — original Kaggle CSV
  - `data/processed/` — cleaned, analysis-ready dataset  
- **Documentation**:
  - Notebooks contain step-by-step commentary and debugging notes
  - README describes the full pipeline and statistical decisions

## Tools Used

- **Pandas** — data loading, cleaning, transformations
- **NumPy** — numerical operations and support utilities
- **Matplotlib** — base plotting (histograms, hexbin plots, bar charts)
- **Seaborn** — statistical visualisation (boxplots, heatmaps)
- **Plotly** — interactive violin plots and exploratory visuals
- **SciPy** — hypothesis tests (Welch’s t-test, one-way ANOVA)
- **Scikit-learn** — minor preprocessing utilities
- **Tableau** — dashboard creation and storytelling
- **Git & GitHub** — collaborative development and version control

## Methodology Justification

- **Data Collection**:
  - Kaggle is a reliable, structured source; local storage avoids API limits.
- **Data Cleaning**:
  - Essential to remove inconsistencies that could bias statistical tests.
- **EDA & Statistics**:
  - Visuals validate numerical findings and prevent misinterpretation.
- **Feature Preparation**:
  - Ensures fair, comparable groups across genres and explicit flags.
- **Statistical Testing**:
  - Correlation, Welch’s t-test, and ANOVA are standard tools for numerical + categorical analysis.

This approach supports **transparency, reproducibility, and analytical rigour**.

---

# 💡 Key Insights

From the combined ETL, EDA, hypothesis testing, and dashboard exploration:

1. **Audio Features vs Popularity**
   - Most audio features show **very weak linear correlations** with popularity.
   - There is **no simple formula** like “high danceability and energy guarantee high popularity”.

2. **Explicit vs Clean Tracks**
   - Clean tracks are **slightly more popular on average** than explicit tracks.
   - Effect is statistically significant but **small** — explicitness is not the dominant factor.

3. **Tempo & Popularity**
   - Tracks with **tempo above 130 BPM** display higher average popularity.
   - This suggests a mild preference for faster, more energetic songs, although correlation magnitudes remain low.

4. **Genre Differences**
   - Genres differ **significantly** in their popularity distributions (ANOVA).
   - Some genres consistently achieve higher median popularity, underlining the importance of **genre context**.

5. **Overall Perspective**
   - Popularity is **multi-factorial**, shaped by:
     - Genre
     - Marketing and playlisting
     - Artist recognition
     - Subtle interactions of audio features
   - Analytics can highlight patterns and tendencies, but cannot fully capture external influences.

---

# ⚖️ Ethics, Generative AI & Governance

## Data Ethics

- The dataset contains **no personal listener data** — only track-level information.
- We treat Spotify’s **popularity score** as:
  - An internal, algorithmically derived metric
  - Potentially influenced by opaque recommendation and playlist mechanisms

We therefore:

- Present popularity as an **indicator**, not a perfect ground truth.
- Avoid overstating causation; we focus on **correlations and associations**.

## Generative AI Usage

- Generative AI tools (e.g., Copilot / assistants) were used **only for**:
  - Documentation structuring
  - Explanatory drafting
  - Occasional debugging guidance
- All analytical decisions, test choices, and interpretations were **reviewed and validated by humans**.
- Dataset is public and compliant with educational, non-commercial usage.

---

# ⚠️ Limitations & Known Issues

1. **Genre Imbalance**
   - Some genres have very few samples and were excluded from ANOVA.
   - Results therefore focus on the **most frequent genres**.

2. **Time-Dependence of Popularity**
   - Popularity is a **snapshot** and can change over time.
   - Analysis does not explicitly model temporal trends.

3. **Algorithmic Nature of Audio Features**
   - Spotify audio features are algorithmically estimated and may not perfectly represent musical qualities.

4. **Binary Explicit Flag**
   - `explicit` is a simple 0/1 indicator; it does not account for intensity, context, or cultural perception of explicit content.

These limitations should be considered when interpreting insights or attempting to generalise beyond this dataset.

---

# 🧾 Version Control & Collaboration

## Branches

- **`Marsella-branch`** — ETL development, data cleaning, validation
- **`Elmi-branch`** — README, documentation, workflow setup
- **`Andrea-branch`** — EDA, statistical tests, Tableau dashboard

## Workflow

- Pull latest `main` before starting work
- Commit frequently with descriptive messages
- Use Pull Requests for merging into `main`
- Resolve conflicts and run quick checks before merging

## Project Board

A GitHub Project Board tracked work through:

- **Backlog** → **To Do** → **In Progress** → **Review/QA** → **Done**

This helped coordinate tasks and maintain visibility across the team.

---

# 🪞 Reflections & Learning

This section can be extended by each team member. Example topics:

- New skills developed in **ETL and data engineering**
- Better understanding of **inferential statistics** (correlation, t-tests, ANOVA)
- Experience transforming **notebooks into dashboards**
- Lessons learned about:
  - Handling real-world data imperfections
  - Collaborating via GitHub and project boards
  - Communicating analytical insights to non-technical audiences

---

# 📚 References

**Datasets & Platforms**

- Kaggle — Spotify Track and Audio Features Dataset  
- Tableau Public  

**Library Documentation**

- **Pandas** — https://pandas.pydata.org  
- **NumPy** — https://numpy.org  
- **Matplotlib** — https://matplotlib.org  
- **Seaborn** — https://seaborn.pydata.org  
- **SciPy** — https://scipy.org  
- **Plotly** — https://plotly.com  

**Statistical & EDA Foundations**

- Tukey, J. W. (1977). *Exploratory Data Analysis.*  
- SciPy Documentation — Hypothesis Testing Reference  

---
