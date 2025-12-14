# CSC172 Association Rule Mining Project Progress Report
**Student:** Christian Dave J. Janiola, 2022-0137    
**Date:** December 14, 2025

**Repository:** [Anime Recommendations Database – Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)

## 📊 Current Status
| Milestone | Status | Notes |
|-----------|--------|-------|
| Dataset Preparation | ✅ Completed | 53,766 transactions processed |
| Data Preprocessing | ✅ Completed | One-hot encoded matrix ready |
| EDA & Visualization | ✅ Completed | Item frequencies + basket sizes done |
| Apriori Implementation | ⏳ Not Started  | Initial run next |
| Rule Evaluation | ⏳ Not Started | Planned for next day |


## 1. Dataset Progress
- **Total transactions:** 53,766
- **Unique items:** 100 → filtered to top 25 (lift > 1)
- **Matrix size:** 53,766 transactions × 100 items
- **Preprocessing applied:** removed unrated entries, keep only "liked" anime, Keep users who rated at least N anime, filter popular anime, one-hot encoding

**Sample transaction preview:**
User 123 → ["Naruto", "Bleach", "One Piece"]


## 2. EDA Progress

**Key Findings (so far):**
![Item Frequency Distribution](results/item_frequencies.png)
- Top 5 items: whole milk(25.3%), other vegetables(19.1%), rolls/buns(17.4%)
- Average basket size: 2.4 items
- 68% transactions contain 1-3 items

**Current Metrics:**
| Metric | Value |
|--------|-------|
| Transactions cleaned | 9,708/9,835 (98.7%) |
| Sparsity reduced | 0.12% → 2.1% |
| Top item support | whole milk: 0.253 |

## 3. Challenges Encountered & Solutions
| Issue | Status | Resolution |
|-------|--------|------------|
| High matrix sparsity | ✅ Fixed | Filtered to top 50 items |
| Memory usage (1.2GB) | ✅ Fixed | Sparse matrix format |
| Infrequent items | ⏳ Ongoing | Tuning min_support threshold |

## 4. Next Steps (Before Final Submission)
- [ ] Complete co-occurrence heatmap
- [ ] Run initial Apriori (min_support=0.02)
- [ ] Generate top 25 rules with metrics
- [ ] Create rule scatter plot 
- [ ] Record 5-min demo video
- [ ] Write complete README.md 
