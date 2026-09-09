# Instagram Data Analysis and SQLite Database Project

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![SQLite](https://img.shields.io/badge/Database-SQLite-lightblue)
![Pandas](https://img.shields.io/badge/Library-Pandas-purple)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Internship](https://img.shields.io/badge/Internship-Alfido%20Tech-red)

An end-to-end Instagram data science and database analysis project developed as part of the **Alfido Tech Data Science Internship**.

This project combines multiple Instagram CSV files into a structured SQLite database and analyzes user activity, posts, likes, comments, hashtags, followers, and engagement patterns using Python, Pandas, SQL, data visualization, and machine-learning techniques.

---

## Project Links

- **GitHub Repository:**  
  [Instagram Analysis](https://github.com/KartikKachwahe/instagram-analysis)

- **Complete Jupyter Notebook:**  
  [View Project Notebook](https://github.com/KartikKachwahe/instagram-analysis/blob/main/Alfido_Tech_Instagram_Complete_Data_Science_Project.ipynb)

> If your notebook is stored inside a `notebook` folder, update the notebook link to include `/notebook/`.

---

## Project Overview

Social-media platforms generate large amounts of interconnected data. A single Instagram user can create posts, receive likes and comments, follow other users, and use hashtags.

Analyzing separate CSV files directly can be difficult because the relationships between users, photos, likes, comments, followers, and hashtags are stored in different tables.

This project solves that problem by:

1. Loading all Instagram CSV files.
2. Validating and cleaning the data.
3. Creating a relational SQLite database.
4. Defining relationships between the tables.
5. Running SQL queries to generate business and engagement insights.
6. Performing exploratory data analysis using Python.
7. Visualizing important Instagram activity patterns.
8. Applying data science techniques to understand engagement.

---

## Project Objectives

The main objectives of this project are:

- Import and examine multiple Instagram datasets.
- Understand the structure and relationship of each table.
- Identify missing, duplicate, and invalid records.
- Clean and preprocess the data.
- Create a relational SQLite database.
- Load cleaned DataFrames into SQLite tables.
- Retrieve information using SQL queries and joins.
- Measure user, photo, like, comment, hashtag, and follower activity.
- Identify the most active and most engaging users.
- Find the most liked and commented posts.
- Analyze popular and trending hashtags.
- Calculate engagement-related KPIs.
- Visualize important patterns and distributions.
- Generate actionable recommendations for users and platforms.

---

## Dataset Description

The project uses seven connected CSV files.

| Dataset | Description |
|---|---|
| `users.csv` | User identification, username, and account creation details |
| `photos.csv` | Photos or posts uploaded by users |
| `likes.csv` | Records showing which users liked which photos |
| `comments.csv` | Comments made by users on photos |
| `follows.csv` | Follower and followee relationships |
| `photo_tags.csv` | Connection between photos and hashtags |
| `tags.csv` | Hashtag names and identifiers |

Together, these files represent a simplified relational Instagram database.

---

## Dataset Relationships

```text
users
 ├── uploads ───────────────► photos
 ├── gives ─────────────────► likes
 ├── writes ────────────────► comments
 └── follows other users ───► follows

photos
 ├── receives ──────────────► likes
 ├── receives ──────────────► comments
 └── contains ──────────────► photo_tags

tags
 └── connected to photos ───► photo_tags
```

### Primary Relationships

| Parent Table | Child Table | Relationship |
|---|---|---|
| `users` | `photos` | One user can upload many photos |
| `users` | `likes` | One user can like many photos |
| `photos` | `likes` | One photo can receive many likes |
| `users` | `comments` | One user can write many comments |
| `photos` | `comments` | One photo can receive many comments |
| `users` | `follows` | Users can follow other users |
| `photos` | `photo_tags` | One photo can contain multiple tags |
| `tags` | `photo_tags` | One tag can be used on multiple photos |

---

## Project Workflow

```text
Business Understanding
        ↓
Load Multiple CSV Files
        ↓
Data Understanding
        ↓
Data Quality Assessment
        ↓
Data Cleaning and Validation
        ↓
Create SQLite Database
        ↓
Create and Populate Tables
        ↓
SQL-Based Analysis
        ↓
Exploratory Data Analysis
        ↓
Feature Engineering
        ↓
Engagement Analysis
        ↓
Data Visualization
        ↓
Insights and Recommendations
```

---

## Data Cleaning and Preprocessing

The project performs the following preprocessing steps:

- Loaded all CSV files into separate Pandas DataFrames.
- Stored the DataFrames in a Python dictionary for organized access.
- Checked dataset dimensions and column names.
- Examined data types and summary statistics.
- Identified missing values.
- Detected duplicate records.
- Removed unnecessary duplicate rows.
- Converted date columns into proper datetime format.
- Validated user and photo identifiers.
- Verified relationships between parent and child tables.
- Checked for orphan records with missing parent IDs.
- Standardized text columns.
- Prepared cleaned data for SQLite insertion.
- Used meaningful table and column names.

These steps improve data quality and ensure that SQL queries produce reliable results.

---

## SQLite Database

SQLite is used because it is:

- Lightweight
- Serverless
- Easy to use with Python
- Suitable for small and medium analytical projects
- Stored inside a single database file
- Supported directly by Python’s `sqlite3` module

### Database Components

```python
import sqlite3

conn = sqlite3.connect("instagram_analysis.db")
cursor = conn.cursor()
```

- `conn` represents the connection between Python and the SQLite database.
- `cursor` is used to execute SQL statements and retrieve results.

### Main Database Tables

- `users`
- `photos`
- `likes`
- `comments`
- `follows`
- `photo_tags`
- `tags`

The cleaned Pandas DataFrames are loaded into these tables so that information can be retrieved using joins, aggregations, subqueries, and common table expressions.

---

## SQL Concepts Used

The project demonstrates the following SQL concepts:

- `SELECT`
- `WHERE`
- `ORDER BY`
- `GROUP BY`
- `HAVING`
- `COUNT`
- `COUNT(DISTINCT)`
- `SUM`
- `AVG`
- `MIN`
- `MAX`
- `INNER JOIN`
- `LEFT JOIN`
- Multiple-table joins
- Subqueries
- Common Table Expressions
- Window functions
- Ranking
- Conditional aggregation
- Null handling
- Views
- Relational database analysis

---

## Key Performance Indicators

The project calculates important Instagram KPIs such as:

| KPI | Meaning |
|---|---|
| Total Users | Number of registered user accounts |
| Total Photos | Number of uploaded photos |
| Total Likes | Total number of likes |
| Total Comments | Total number of comments |
| Total Follow Relationships | Number of follower-followee connections |
| Total Hashtags | Number of available hashtags |
| Average Posts per User | Average number of photos uploaded by each user |
| Average Likes per Photo | Average engagement received through likes |
| Average Comments per Photo | Average engagement received through comments |
| Engagement per Photo | Combined likes and comments for each photo |
| User Engagement | Combined activity performed or received by a user |
| Most Active User | User with the highest platform activity |
| Most Popular Photo | Photo with the highest engagement |
| Most Popular Hashtag | Hashtag used on the largest number of photos |

---

## Exploratory Data Analysis

### 1. User Analysis

The user analysis examines:

- Total registered users
- User registration over time
- Oldest users
- Newest users
- Users with the highest number of posts
- Users who have never posted
- Users with the highest activity
- Inactive or low-engagement accounts

### 2. Photo Analysis

The photo analysis identifies:

- Total uploaded photos
- Photos uploaded by each user
- Most active content creators
- Users with no photo uploads
- Most liked photos
- Most commented photos
- Most engaging photos

### 3. Likes Analysis

The likes table is used to determine:

- Total likes on the platform
- Likes received by each photo
- Likes received by each content creator
- Users who gave the most likes
- Photos that received the most likes
- Average number of likes per photo
- Accounts with unusual liking behavior

### 4. Comment Analysis

The comments dataset is analyzed to understand:

- Total comments
- Comments received by each photo
- Comments written by each user
- Most active commenters
- Most commented photos
- Average comments per photo
- Comment text patterns
- Frequently used words
- Comment length distribution

### 5. Followers Analysis

The followers dataset is used to calculate:

- Followers per user
- Following count per user
- Most-followed users
- Users following the highest number of accounts
- Follower-to-following ratio
- Users with no followers
- Potentially influential users

### 6. Hashtag Analysis

The hashtag analysis identifies:

- Total unique hashtags
- Most frequently used hashtags
- Number of photos associated with each hashtag
- Popular content categories
- Underused hashtags
- Hashtag engagement based on likes and comments

---

## Feature Engineering

The project can create analytical features such as:

| Feature | Description |
|---|---|
| `post_count` | Number of photos uploaded by a user |
| `likes_given` | Number of likes given by a user |
| `likes_received` | Likes received on a user’s photos |
| `comments_given` | Comments written by a user |
| `comments_received` | Comments received on a user’s photos |
| `followers_count` | Number of followers |
| `following_count` | Number of accounts followed |
| `engagement_count` | Combined likes and comments |
| `engagement_rate` | Engagement relative to followers or posts |
| `follower_following_ratio` | Followers divided by following count |
| `account_age` | Time since account registration |
| `comment_length` | Number of characters or words in a comment |

These features transform raw transactional records into useful measures of user behavior and content performance.

---

## Data Science Techniques

### Descriptive Analysis

Descriptive analysis explains what happened on the platform.

Examples:

- Total users
- Total photos
- Total likes
- Total comments
- Most popular hashtags
- Average engagement

### Diagnostic Analysis

Diagnostic analysis helps explain why some users or photos receive more engagement.

Factors examined include:

- Posting frequency
- Number of followers
- Hashtag usage
- Likes received
- Comments received
- User activity
- Content popularity

### Text Analysis

Comment text can be analyzed using:

- Text cleaning
- Lowercase conversion
- Punctuation removal
- Stop-word removal
- Tokenization
- Word-frequency analysis
- Comment-length analysis

### User Segmentation

Users can be grouped according to:

- Posting activity
- Likes given
- Comments written
- Followers
- Following count
- Engagement received

Possible segments include:

- Highly active creators
- Popular creators
- Engaged community members
- Passive users
- Inactive users

### Anomaly Detection

Unusual user behavior can be identified using:

- Extremely high liking activity
- Abnormally high following activity
- Repetitive comments
- Very low content contribution
- Activity much higher than the normal user range

Anomalies should be investigated further and should not automatically be treated as fraudulent behavior.

---

## Main Insights Generated

This project can help identify:

- The most active Instagram users
- Users who have never posted
- Users with the most followers
- Users with unusually high activity
- The most liked photos
- The most commented photos
- The most engaging content
- The most popular hashtags
- Hashtags associated with high engagement
- Differences between creators and passive users
- Patterns in comments and user interactions
- Potential influencers based on followers and engagement
- Possible promotional or bot-like behavior

Exact numerical results are available in the executed notebook outputs.

---

## Business Recommendations

### 1. Improve User Activation

Users who register but never upload content should receive:

- Onboarding guidance
- Content-creation prompts
- Personalized post suggestions
- Notifications encouraging their first upload

### 2. Reward High-Quality Creators

Creators with consistently strong engagement can be supported through:

- Creator-reward programs
- Greater content visibility
- Collaboration opportunities
- Verification or recognition programs

### 3. Improve Hashtag Recommendations

Popular and high-engagement hashtags can be used to create a recommendation system that helps users choose relevant tags for their posts.

### 4. Personalize User Feeds

Likes, comments, followers, and hashtags can help recommend:

- Relevant posts
- Similar creators
- Interesting hashtags
- Accounts to follow

### 5. Detect Suspicious Activity

Accounts with extremely high likes, comments, or follow actions should be reviewed for:

- Automated behavior
- Spam
- Fake engagement
- Bot-like activity

### 6. Re-Engage Inactive Users

Users with low activity can receive personalized reminders, trending-content recommendations, and creator suggestions.

### 7. Support Potential Influencers

Users with high engagement and a strong follower base can be considered for:

- Brand partnerships
- Sponsored content
- Promotional campaigns
- Creator-development programs

### 8. Improve Content Strategy

Creators can improve engagement by studying:

- Their best-performing posts
- Effective hashtags
- Posting frequency
- Audience reactions
- Comment activity

---

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- SQLite
- SQL
- Matplotlib
- Seaborn
- Scikit-learn
- Natural Language Processing
- Git
- GitHub

---

## Recommended Repository Structure

```text
instagram-analysis/
│
├── README.md
├── requirements.txt
│
├── notebook/
│   └── Alfido_Tech_Instagram_Complete_Data_Science_Project.ipynb
│
├── data/
│   ├── users.csv
│   ├── photos.csv
│   ├── likes.csv
│   ├── comments.csv
│   ├── follows.csv
│   ├── photo_tags.csv
│   └── tags.csv
│
├── database/
│   └── instagram_analysis.db
│
├── images/
│   ├── user_activity.png
│   ├── top_photos.png
│   ├── popular_hashtags.png
│   └── engagement_analysis.png
│
└── report/
    └── Instagram_Analysis_Project_Report.pdf
```

> Only show files and folders that actually exist in your repository.

---

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/KartikKachwahe/instagram-analysis.git
```

### 2. Open the Project Folder

```bash
cd instagram-analysis
```

### 3. Create a Virtual Environment

```bash
python -m venv .venv
```

### 4. Activate the Environment

For Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

For macOS or Linux:

```bash
source .venv/bin/activate
```

### 5. Install the Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Alternatively, use:

```bash
pip install -r requirements.txt
```

### 6. Add the Dataset Files

Place all seven CSV files inside the `data` or `upload` directory:

```text
users.csv
photos.csv
likes.csv
comments.csv
follows.csv
photo_tags.csv
tags.csv
```

### 7. Start Jupyter Notebook

```bash
jupyter notebook
```

Open the project notebook and select:

```text
Kernel → Restart & Run All
```

---

## Requirements

Add the following content to `requirements.txt`:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

The Python standard library already includes `sqlite3`, so it normally does not need to be installed separately.

---

## Limitations

- The dataset represents a limited sample of Instagram activity.
- It may not represent the current Instagram platform.
- Likes and comments measure engagement but not necessarily content quality.
- Missing or incomplete relationships can affect the analysis.
- High activity does not automatically indicate suspicious behavior.
- Text analysis without language detection may misinterpret multilingual comments.
- Engagement rate depends on the exact business definition used.
- The project database is designed for analysis and learning, not production-scale Instagram traffic.

---

## Future Improvements

- Develop an interactive Streamlit dashboard.
- Add sentiment analysis for comments.
- Build an engagement-prediction model.
- Create a hashtag recommendation system.
- Perform network analysis of follower relationships.
- Visualize user networks using NetworkX.
- Apply community-detection algorithms.
- Add bot or anomaly-detection models.
- Create a content recommendation system.
- Build an automated ETL pipeline.
- Add model explainability using SHAP.
- Deploy the project through a web application.

---

## Conclusion

This project demonstrates a complete data-analysis and relational-database workflow:

```text
Multiple CSV Files
→ Data Validation
→ Data Cleaning
→ SQLite Database Creation
→ SQL Analysis
→ Exploratory Data Analysis
→ Feature Engineering
→ Engagement Analysis
→ Visualization
→ Insights
→ Business Recommendations
```

The project shows how raw social-media data can be transformed into a structured database and meaningful insights. It demonstrates practical knowledge of Python, Pandas, SQL, SQLite, data visualization, relational data modeling, and social-media analytics.

---

## Author

**Kartik Kachwahe**

B.Tech in Information Technology  
Aspiring Data Analyst and Data Scientist

- **GitHub:** [KartikKachwahe](https://github.com/KartikKachwahe)

---

 If you found this project useful, consider giving the repository a star.
