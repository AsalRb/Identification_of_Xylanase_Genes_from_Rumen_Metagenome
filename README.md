# Bioinformatics Project 2 – Identification of Xylanase Genes from Rumen Metagenome

> Identification of microbial xylanase enzyme genes from the ruminant rumen metagenome using bioinformatics tools. _
> *This project is part of the Introduction to Bioinformatics course.*

---

## Overview

This project focuses on **discovering xylanase genes** from the rumen metagenome of ruminants, a rich microbial ecosystem known for its lignocellulose-degrading capabilities.

* **Why important?**

  * Xylanases hydrolyze xylan, the second most abundant polysaccharide in nature.
  * Applications include **biofuel production**, **animal feed digestibility**, **paper/pulp bleaching**, and **biotechnology**.
  * Thermostable and pH-resistant xylanases are particularly valuable for harsh industrial processes.

* **Objective:**

  * Identify and analyze **potential xylanase gene sequences** from assembled metagenomic contigs.
  * Reduce redundancy by clustering.
  * Build models for conserved regions to refine candidate sequences.

Dataset: [Rumen metagenome contigs (Google Drive)](https://drive.google.com/file/d/14PGwsGuL2ouY-_fv0yrzijGnBMSjREU6/view)
Reference thermostable xylanases: *thermo\_xylanase* dataset

---

## Project Structure

```
Project2/
├── Inputs/                              # Input datasets (assembled contigs, thermo_xylanase sequences, configs)
├── part1/                               # Step 1: BLAST+ search for candidate thermostable xylanases
├── part2/                               # Step 2: Clustering with CD-HIT and representative sequence selection
├── part3/                               # Step 3: Conserved region modeling (HMM, PSSM) and filtering
│
└── Bioinformatics Project 2_Asal Rabiee.pdf   # Full project report
```

---

## Workflow

### Part 1 – Identification of Candidate Sequences

* Compare contigs against known thermostable xylanases.
* Tools: **BLAST+**, DIAMOND, HMMER.
* Output: candidate contigs + protein translations.

### Part 2 – Clustering and Representative Selection

* Cluster similar sequences (97% threshold) with **CD-HIT**.
* Select longest sequence from each cluster as representative.
* Output: non-redundant representative sequences.

### Part 3 – Conserved Region Modeling and Filtering

* Build models for conserved regions of a chosen xylanase subfamily.

  * **Methods:** PSSM, HMM, or regular expressions.
* Filter representative sequences against model.
* Output: refined set of high-confidence xylanase gene candidates.

---

## Key Results

* Candidate contigs with similarity to thermostable xylanases identified.
* Protein translations extracted for candidate sequences.
* Clusters generated with CD-HIT; redundant sequences removed.
* HMM models of conserved regions built and used to refine candidate set.

---

## Tools & Dependencies

* [BLAST+](https://blast.ncbi.nlm.nih.gov/doc/blast-help/downloadblastdata.html#downloadblastdata)
* [CD-HIT](http://weizhongli-lab.org/cd-hit/)
* [Clustal Omega](https://www.ebi.ac.uk/Tools/msa/clustalo/)
* [HMMER](http://hmmer.org/)
* Optional: DIAMOND, machine learning–based methods

---

## Getting Started

### 1. Clone repository

```bash
git clone https://github.com/<your-username>/Bioinformatics-Project2.git
cd Bioinformatics-Project2
```

### 2. Install dependencies

On Ubuntu/Debian:

```bash
sudo apt-get update
sudo apt-get install ncbi-blast+ cd-hit hmmer clustalo
```

### 3. Run pipeline

* Place input contigs and `thermo_xylanase` sequences into `Inputs/`.
* Run commands for each part:

  * **part1/** → similarity search (BLAST+, DIAMOND, or HMMER)
  * **part2/** → clustering with CD-HIT
  * **part3/** → build HMM/PSSM model and filter sequences

---

## Notes

* For large datasets, similarity thresholds (E-value, % identity) should be carefully chosen.
* Clustering reduces redundancy and simplifies downstream analyses.
* Only final candidate sets and key results are retained in the repo; intermediate large files should be re-generated if needed.

