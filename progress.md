# CSC172 Association Rule Mining Project Progress Report
**Student:** Christian Dave J. Janiola, 2022-0137    
**Date:** December 14, 2025

**Repository:** [Anime Recommendations Database – Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)

## 📊 Current Status

| Milestone              | Status        | Notes                                        |
| ---------------------- | ------------- | -------------------------------------------- |
| Dataset Preparation    | ✅ Completed   | Anime ratings converted to transactions      |    
| Data Preprocessing     | ✅ Completed   | Filtering, merging, one-hot encoding applied |    
| EDA & Visualization    | ✅ Completed   | Transaction length + item frequency analysis |    
| Apriori Implementation | ✅ Completed   | Frequent itemsets and rules generated        |    
| Rule Evaluation        | ✅ Completed | Rule filtering and interpretation ongoing    |    

## 1. Dataset Progress

* **Total transactions:** ~50,000+ user transactions
* **Unique items:** Top 100 anime titles (after popularity filtering)
* **Matrix size:** ~50k transactions × 100 items (binary encoded)
* **Preprocessing applied:**

  * Removed unrated entries (rating = -1)
  * Kept only positively rated anime
  * Filtered users with low interaction counts
  * Filtered popular anime titles to reduce sparsity
  * One-hot encoding using TransactionEncoder

**Sample transaction preview:**
User 123 → ["Naruto", "Bleach", "One Piece"]

## 2. Exploratory Data Analysis (EDA) Progress

**Analyses Completed:**

* Distribution of transaction lengths (anime watched per user)
* Item frequency distribution for popular anime titles
* Identification of long-tail effects and sparsity

**Key Observations:**

* Most users watch a small subset of popular anime
* Transaction lengths are right-skewed, with a small number of highly active users
* Filtering popular titles significantly reduced sparsity and computation time

*(Visualizations include histograms and bar charts of transaction sizes and item frequencies.)*

## 3. Apriori & Rule Mining Progress

**Current Implementation:**

* Apriori algorithm applied with tuned support thresholds
* Maximum itemset length limited to 2 to control runtime
* Rules evaluated using support, confidence, and lift

**Post-processing:**

* Rules sorted primarily by lift to identify non-random associations
* Trivial sequel–prequel or franchise-based rules filtered using title similarity heuristics

**Preliminary Results:**

* Strong co-watching patterns observed among action and shōnen titles
* Lift values greater than 1 indicate meaningful associations beyond chance

## 4. Challenges Encountered & Solutions

| Issue                | Status     | Resolution                                       |    
| -------------------- | ---------- | ------------------------------------------------ |    
| Large dataset size   | ✅ Resolved | Filtered users and popular anime                 |    
| High memory usage    | ✅ Resolved | Reduced item dimensionality + low-memory Apriori |    
| Long Apriori runtime | ✅ Resolved | Limited itemset length and tuned support         |    
| Trivial sequel rules | ✅ Resolved | Title normalization and rule filtering           |    

## 4. Next Steps (Before Final Submission)