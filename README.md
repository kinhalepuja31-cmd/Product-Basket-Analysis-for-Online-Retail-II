# Product-Basket-Analysis-for-Online-Retail-II
 Task 29

•	Project Objective

The main goal of this project is to analyze historical customer transactions to identify which items are frequently purchased together. By discovering these relationships, businesses can implement data-driven product bundling strategies, optimize cross-selling algorithms, and enhance recommendation systems to boost average order value.

•	Tech Stack & Tools

1.	Language: Python
2.	Libraries:Pandas, NumPy, Itertools, Collections (Counter), Matplotlib, Seaborn
3.	Environment: Jupyter Notebook / Google Colab
4.	Dataset: Online Retail II Dataset (Years 2009-2011)

•	Step-by-Step Methodology & Approach

1. Data Loading & Inspection

-	Merged transactional logs from two sheets (`Year 2009-2010` and `Year     2010-2011`) into a single consolidated dataset.

2. Data Cleansing
   
-	Dropped missing values specifically in the `Description` column to ensure clear item tracking.
-	Kept rows with null `Customer ID` fields to avoid discarding valid guest-checkout transaction data.
-	Stripped trailing whitespaces from `Description` to prevent duplicate entities.
-	Extracted and eliminated all canceled transactions (invoices prefixed with 'C') to focus purely on finalized purchases.
  
 3. Transaction Basket Isolation
    
-	Grouped data by unique `Invoice` IDs to structure actual purchase baskets.
-	Filtered out all single-item baskets, focusing exclusively on multi-item baskets to ensure valid candidate pairs.
  
 4. Co-occurrence Generation & Frequency Counting
    
-	Leveraged `itertools.combinations` to extract item pairs from transactions.
-	Excluded self-pairs and pre-sorted text names alphabetically to eliminate duplicates like `(Item A, Item B)` and `(Item B, Item A)`.

5. Advanced Metrics Assessment
   
-	Computed association parameters across all item combinations to measure relationship strength:
-	Support: Overall baseline occurrence frequency of the product pair.
-	Confidence: Prediction accuracy of buying Item B given that Item A is already purchased.
-	Lift: The true strength of the association rule. Filtered out rare pairs (co-occurrences < 30) to eliminate low-frequency noise.

•	Key Findings & Outcomes

-	Top Association Pair:The strongest relationship discovered was between the BLUE KNITTED EGG COSY and the PINK KNITTED EGG COSY. 
-	Statistical Strength: This pairing demonstrated an exceptionally high Lift score of 782.1, proving that a buyer selecting the blue version is  782 times more likely to purchase the pink version compared to an average baseline customer.
-	High-Value Segments: Niche home decor items and decorative signs showed strong micro-segment purchasing trends, making them highly suitable for direct catalog cross-selling strategies.
