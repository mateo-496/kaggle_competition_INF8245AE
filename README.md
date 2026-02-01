# INF8245 – Predicting Antimicrobial Resistance from Genomes

This repository contains my work for the **INF8245 (Fall 2025)** Kaggle competition.

The goal of the project is to **predict bacterial resistance to antimicrobial drugs** from genomic data, focusing on *Escherichia coli* and the antibiotic **Cefepime**.

---

## Problem Overview

Antimicrobial resistance (AMR) is a major challenge in modern medicine. Through mutations in their genome, bacteria can acquire resistance mechanisms that make antibiotics ineffective. Being able to predict resistance directly from genomic sequences is an important step toward better diagnostics and treatment strategies.

In this competition, the task is a **binary classification problem**:

- **1** → resistant  
- **0** → susceptible  

Each sample corresponds to one *E. coli* genome.

---

## Data Representation

Each genome is provided as a DNA sequence (A, C, G, T), millions of bases long. To make this usable for machine learning, the genomes are represented using **k-mers**.

- A **k-mer** is a DNA substring of length *k*  
- Here, **k = 31**
- A sliding window of length 31 moves along the genome, one base at a time
- All observed 31-mers form a vocabulary

Each genome is then represented as a **bag-of-k-mers**:

- Rows → individual genomes  
- Columns → the **1 million most frequent 31-mers**  
- Values → raw counts of each k-mer in the genome  

This results in an **ultra-high-dimensional and sparse** feature matrix.

---

## Dataset

- ~3,000 *E. coli* genomes
- Tested against **Cefepime**
- Strong class imbalance
- Very high-dimensional feature space

The private test set is split into:
- A **random split**, similar to the training distribution
- A **phylogenetic split**, representing a different evolutionary branch and requiring strong generalization

Evaluation metric: **Macro F1-score**

---

## Repository Structure

- **`main.ipynb`**  
  Main notebook containing preprocessing, modeling, training, and evaluation on the public dataset.

- **`data_exploration.ipynb`**  
  Exploratory data analysis: class imbalance, feature inspection, metadata...

- **`Report.pdf`**  
  Written report describing the methodology, experiments, results, and discussion.

---

## Ranking
Ended 3rd out of 40 on the private test set.

## Contributors
- [Adrien Saouma](https://github.com/saoumadr)
- [Matéo Mangialomini](https://github.com/mateo-496)
- Maxime Tran
