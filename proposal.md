# CSC172 Association Rule Mining Project Proposal
**Student:** [Your Name], [ID]  
**Date:** December 12, 2025

## 1. Project Title 
Mining Anime Co-Watching and Recommendation Patterns Using Apriori Algorithm


## 2. Problem Statement
Anime streaming platforms and recommendation systems rely heavily on understanding viewer behavior to improve personalization. With thousands of anime titles available, identifying meaningful co-watching patterns is challenging without automated methods.

This project aims to discover association rules among anime titles using user rating histories from the Anime Recommendations Database. By analyzing what anime titles are commonly watched together, the study can uncover hidden patterns in viewer preferences, genre affinities, and community trends. These insights may support better recommendation algorithms and help understand user behavior in digital media consumption.

## 3. Objectives
- Transform user-rating logs into a transaction-style dataset suitable for association rule mining.

- Apply the Apriori algorithm to generate frequent itemsets and discover significant co-watching rules.

- Evaluate rules based on support, confidence, and lift to identify strong associations.

- Provide insights into viewing habits, genre linkages, and potential recommendation patterns.

## 4. Dataset Plan
- Source: [Anime Recommendations Database – Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database) (~10K transactions, 169 items)
    - Files Used:
        - rating.csv — user–anime rating history
        - anime.csv — anime metadata (names, genres, type, episodes)
- Domain: GOnline media consumption / recommendation systems
- Acquisition: Downloaded directly from Kaggle. Will merge rating.csv with anime.csv to convert each user's watched anime into a transaction list.

#### To reduce computational load, analysis will focus on:
- Users who rated at least 10 anime
- Top 300 most-rated anime titles

## 5. Technical Approach
- Preprocessing:
    - Remove ratings with -1 (watched but no score).

    - Merge rating data with anime titles.

    - Group by user_id to create transactions (list of anime watched per user).

    - Optionally filter infrequent anime to control dataset size.

Convert transactions to one-hot encoding using TransactionEncoder.
- Algorithm: Apriori Algorithm
    - min_support ≈ 0.01 – 0.05

    - Generate frequent itemsets

    - Derive association rules using metrics: lift, confidence, leverage
- Framework: Python + pandas + mlxtend + matplotlib/seaborn
- Environment: Jupyter Notebook / Google Colab

## 6. Expected Challenges & Mitigations
- Challenge 1: Extremely large dataset (~6M ratings)

    - Mitigation:

        - Limit analysis to top 300 anime titles

        - Filter low-interaction users

        - Use support threshold tuning

- Challenge 2: Sparse itemset matrix

    - Mitigation:

        - Apply minimum support pruning

        - Remove ultra-rare anime to reduce sparsity

- Challenge 3: Long Apriori runtime

    - Mitigation:

        - Reduce max length of itemsets (e.g., max_len=3)

        - Increase support threshold as needed

- Challenge 4: Duplicate or trivial genre-based rules

    - Mitigation:

        - Analyze rules by title and genre

        - Sort rules by lift to filter meaningful associations