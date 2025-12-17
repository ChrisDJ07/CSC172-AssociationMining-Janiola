# CSC172 Association Rule Mining Project Proposal
**Student:** Christian Dave J. Janiola, 2022-0137  
**Date:** December 12, 2025

## 1. Project Title

Mining Anime Co-Watching and Recommendation Patterns Using the Apriori Algorithm

## 2. Problem Statement

Anime streaming platforms and digital recommendation systems rely on understanding viewer behavior to deliver personalized content. With thousands of anime titles available and highly diverse user preferences, identifying meaningful co-watching patterns becomes difficult without automated data mining techniques.

This project aims to apply association rule mining to uncover co-watching relationships among anime titles using user rating histories from the Anime Recommendations Database. By analyzing which anime are frequently watched together by the same users, the study seeks to reveal hidden viewing patterns, shared audience interests, and implicit recommendation structures. The results may contribute to a better understanding of user behavior in online media consumption and demonstrate how association rule mining can be applied to large-scale recommender datasets.

## 3. Objectives

* Transform user rating logs into a transaction-style dataset suitable for association rule mining.
* Apply the Apriori algorithm to generate frequent itemsets from anime co-watching data.
* Discover and evaluate association rules using support, confidence, and lift metrics.
* Filter out trivial associations (e.g., sequel–prequel relationships) to focus on meaningful co-watching patterns.
* Interpret the resulting rules to gain insights into viewer preferences and potential recommendation patterns.

## 4. Dataset Plan

* **Source:** Anime Recommendations Database (Kaggle)

  * [https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)
* **Files Used:**

  * `rating.csv` — user–anime rating history
  * `anime.csv` — anime metadata (title, genre, type, number of episodes)
* **Domain:** Online media consumption / recommender systems
* **Acquisition:** The dataset will be downloaded directly from Kaggle. Rating data will be merged with anime metadata to associate user ratings with anime titles.

To reduce computational complexity and improve the quality of association rules, the analysis will focus on:

* Users who rated at least **5 anime** with a positive score
* The **top 100 most frequently rated anime titles**

These constraints help control dataset size while preserving meaningful co-occurrence patterns.

## 5. Technical Approach

* **Preprocessing:**

  * Remove ratings with a value of `-1` (watched but not rated).
  * Retain only positively rated anime to represent user preference.
  * Merge rating data with anime titles for readability and interpretation.
  * Group records by `user_id` to construct transactions, where each transaction represents the list of anime watched by a user.
  * Filter infrequent anime titles to reduce sparsity and computational overhead.

* **Transaction Encoding:**

  * Convert transactions into a one-hot encoded matrix using `TransactionEncoder` from the mlxtend library.

* **Algorithm:** Apriori Algorithm

  * Generate frequent itemsets using a minimum support threshold (approximately 0.01–0.05).
  * Limit maximum itemset length (e.g., `max_len = 2`) to control runtime.
  * Derive association rules and evaluate them using confidence and lift metrics.

* **Post-processing:**

  * Sort rules primarily by lift and secondarily by confidence.
  * Apply heuristic filtering to remove trivial rules caused by sequel–prequel or franchise continuation effects.

* **Tools & Environment:**

  * Python, pandas, mlxtend, matplotlib
  * Jupyter Notebook (with optional execution on Google Colab if needed)

## 6. Expected Challenges & Mitigations

* **Challenge 1: Large dataset size (~6 million ratings)**

  * *Mitigation:*

    * Restrict analysis to popular anime titles
    * Filter out low-interaction users
    * Tune support thresholds to reduce candidate itemsets

* **Challenge 2: Sparse transaction matrix**

  * *Mitigation:*

    * Remove infrequent items
    * Focus on active users with sufficient transaction lengths

* **Challenge 3: High computational cost of Apriori**

  * *Mitigation:*

    * Limit maximum itemset size
    * Use low-memory mode in Apriori
    * Reduce item dimensionality through filtering

* **Challenge 4: Trivial or uninformative rules (e.g., sequel–prequel relationships)**

  * *Mitigation:*

    * Apply title-based similarity heuristics to filter franchise-related rules
    * Emphasize lift-based ranking to highlight non-random associations
