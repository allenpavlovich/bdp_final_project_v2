# Amazon Reviews Analysis - Project Structure

## Project Organization

```
final_project/
│
├── notebooks/
│   ├── 1_Initial_Data_Loading.ipynb        # Basic data loading and exploration
│   ├── 2_Data_Cleaning_EDA.ipynb           # Data cleaning and exploratory analysis
│   ├── 3_Timeline_Analysis.ipynb           # Analysis of review trends over time
│   ├── 4_Product_Category_Analysis.ipynb   # Analysis of products and categories
│   ├── 5_Reviewer_Analysis.ipynb           # Analysis of reviewer behavior
│   ├── 6_Text_Similarity_Analysis.ipynb    # LSH implementation for similarity detection
│   └── 7_Final_Report_Generation.ipynb     # Generate insights for presentation
│
├── intermediate_data/                      # References to intermediate processed data
│   ├── reviews_processed/                  # Processed reviews data
│   ├── meta_processed/                     # Processed metadata
│   ├── category_timelines/                 # Category timeline data
│   └── similarity_results/                 # Results from similarity analysis
│
└── presentation/                           # Final presentation materials
    ├── figures/                            # Generated figures
    └── Amazon_Reviews_Analysis.pptx        # Final presentation
```