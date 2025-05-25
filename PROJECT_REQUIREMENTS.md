# Final Project: Amazon Reviews Light

## Project Overview

**Big Data and Cloud Computing Final Project: Investigating the Impact of AI Technologies on Fraudulent Amazon Reviews Using Similarity Analysis**

With the rise of generative AI tools, it has become easier to mass-produce convincing but fake reviews. These can significantly distort product trustworthiness, affect consumer behavior, and reduce platform credibility. Detecting these AI-generated patterns through big data similarity techniques provides insights for content moderation, detection, and policy.

**Research Question:** Do AI technologies contribute to fraudulent or redundant product reviews, and can these be detected using scalable similarity-based analysis?

## Data Source

Amazon Reviews Archive stored in Google Cloud Storage: `gs://msca-bdp-data-open/final_project_reviews`  
**Overall data size:** ~75 GiB

### Data Structure

Two subfolders with three preselected categories containing parquet files:

1. **reviews_parquet** (`gs://msca-bdp-data-open/final_project_reviews/reviews_parquet`)
   - User Reviews dataset with ratings, review text, and helpfulness votes

2. **meta_parquet** (`gs://msca-bdp-data-open/final_project_reviews/meta_parquet`)
   - Product details including descriptions, pricing, and raw image data

## Required Analysis Steps

### 1. Data Cleaning and Preparation
- Discard irrelevant or obviously erroneous data
- Review deeply nested data structure to select appropriate data elements
- Remove poorly populated or duplicate variables

### 2. Exploratory Data Analysis (EDA)

#### Timeline Analysis
- What is the timeline of the data? Do you see significant peaks and valleys?
- Do you see any data collection gaps?
- Do you see any outliers? Remove obvious outliers before plotting the timeline
- Do you see any spikes? Are these spikes caused by real activities/events?

#### Product and Category Analysis
- What are the top 10 products with the most reviews?
- How does their review count trend over time?
- How does review volume vary across product categories (e.g., Books, Electronics, Beauty)?
- Do certain categories see spikes in review volume during specific months (e.g., holidays, sales)?
- Are products with extremely high average ratings (4.9–5.0) also the most-reviewed?
- Is there a relationship between product price and average rating or review volume?

#### Text Analysis
- What are the most common words or phrases in 5-star vs. 1-star reviews?

### 3. Reviewer Analysis
- Identify the most active reviewers by count
- Do top reviewers write across diverse categories or just a few?

### 4. Uniqueness and Similarity Analysis

#### Text Similarity Assessment
- How unique are the "title" and "review" values? (Pick only ONE category, apply sampling if needed)
- Are they mostly unique? Or are people usually just copy-pasting the same text?
- Use LSH to measure uniqueness/similarity
- Visualize "review titles" and "review texts" duplication
- Visualize "review titles" and "review texts" duplication for each of the top 5 products

**Note:** This is not topic modeling (LDA/LSA) – but text similarity analysis

#### Temporal Similarity Comparison
Compare the effectiveness of similarity-based detection (choose one best suited for Big Data volumes: SimHash, MinHash, LSH) on:
- Recent reviews (e.g., 2022–2023) 
- Older reviews (pre-2022)

**Research Question:** Are similarity detection techniques less effective on recent data due to more advanced or diversified AI-generated reviews?

## Submission Requirements

### Files to Submit
1. **Jupyter notebooks** (actual program codes)
2. **PowerPoint presentation** (PPTX or PDF format)
   - Submit directly to Canvas (not zipped) for SpeedGrader compatibility

### Presentation Requirements (8-12 pages recommended)

#### Content Structure
1. **Executive Summary**
2. **Methodology and source data overview**
3. **Conclusions and actionable recommendations**

#### Presentation Guidelines
- Should be self-sufficient (no need to read notebooks after reviewing slides)
- Clearly answer all questions with supporting plots/tables/numbers
- Right amount of supporting material (not too much, not too little)
- Clear, logical, well-organized, simple presentation
- Proper English with spell check
- Production-quality plots that are easily readable
- All statements/conclusions 100% supported by data analysis

#### Technical Requirements
- No fuzzy plots, untitled plots, unreadable labels, or overlapping labels
- Fix formatting issues before submission
- Consider saving in alternative formats (PDF, HTML) if Canvas corrupts formatting

## Suggested Implementation Steps

1. **Data Structure Understanding**
   - Amazon reviews data comes in nested format
   - Understand structure/fields to parse elements correctly

2. **Sampling Strategy**
   - Perfectly fine to run analysis on data samples
   - Ensure findings can be generalized to entire dataset

3. **Data Preprocessing**
   - Eliminate obviously erroneous records
   - Use EDA and web search for best criteria
   - Reduce data volume by eliminating unnecessary fields and bad data
   - Choose appropriate storage format (Parquet, CSV, JSON) for intermediate results

4. **Big Data Best Practices**
   - **Do NOT** cache all data in Spark memory (will cause crashes and point deductions)
   - Dry run notebooks on small cached samples before running on entire dataset
   - Avoid Cartesian products, record loss, infinite loops, bad joins
   - Do NOT create single notebook for everything
   - Save intermediate analysis steps
   - Filtered results should be much smaller and process quickly

## Execution Environment

**Dataproc Instance:** `adsp-bdp-dataproc-students-0X` (assigned to your CNetID)
- Read data directly from GCS bucket using Spark
- Provided as-is (no support or uptime guarantee)
- **Must back up notebooks frequently** (laptops, Box, Google Drive, etc.)

**Alternative:** Working on `adsp-bdp-serverless-students-0X`

**Starter Resources:** Jupyter Notebook provided

## Important Notes

- These are large files - **DO NOT wait until the last day!**
- Start early to avoid performance issues

## Grading Rubric

| Component | Points |
|-----------|---------|
| Executive Summary with meaningful insights | 10 |
| Methodology and source data overview | 5 |
| Data clean-up and filtering / EDA | 10 |
| Timeline analysis | 10 |
| Product and Categories analysis | 15 |
| Common words and reviewers analysis | 10 |
| Reviews uniqueness analysis | 20 |
| Conclusions and actionable recommendations | 20 |
| **Total Grade** | **100** |