# Resume / Candidate Screening System

**Future Interns - Machine Learning Task 3**

## Overview

This project builds a machine learning system that automatically screens, scores, and ranks candidate resumes against a job description, and identifies missing skills for top candidates — mirroring how real resume screening tools work in HR-tech platforms.

## Objective

Hiring teams often receive hundreds of resumes for a single role, making manual screening slow and inconsistent. This project explores whether resume text can be used to:

1. Score each candidate's resume against a job description based on textual similarity
2. Rank candidates by role fit
3. Identify which required skills are missing from a candidate's resume

## Dataset

[Resume Dataset](https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset) (Kaggle) — 2,484 resumes across 24 job categories, with resume text and category labels.

## Target Role

**Information Technology** — a custom job description was written covering common IT skills (Python, SQL, Windows Server, troubleshooting, technical support, cloud computing, cybersecurity, project management, networking, communication).

## Approach

1. **Text Cleaning** — lowercasing, punctuation removal, and stopword removal applied consistently to both resumes and the job description
2. **Similarity Scoring** — TF-IDF vectorization of all resumes and the job description using a shared vocabulary, followed by cosine similarity to score each resume against the job description
3. **Ranking** — candidates sorted by similarity score to produce a shortlist
4. **Skill Gap Identification** — each top candidate's resume checked against a list of required skills to flag what's missing
5. **Visualization** — bar chart comparing similarity scores across the top 10 candidates

## Results

7 of the top 10 ranked candidates belonged to the Information Technology category, confirming the scoring logic correctly surfaces role-relevant resumes. A few resumes from adjacent categories (Aviation, BPO, Consultant) also scored highly due to shared vocabulary like "systems," "technical," or "project management" — a realistic overlap seen in real hiring too.

## Key Finding

Most top-ranked candidates, including those in the IT category, were flagged as missing "python" in their resume text. This is most likely a keyword-matching limitation rather than a genuine skill gap — candidates may describe relevant experience using different terminology (e.g., "scripting," "automation"), or work in IT roles where Python isn't a core requirement (e.g., network administration, technical support).

## Limitations

This system relies on keyword and phrase-based text similarity, not true semantic understanding. It cannot recognize skills described in different words, cannot verify actual proficiency, and treats all matched terms with equal weight. A production-grade system would benefit from named entity recognition for skill extraction or semantic embeddings that capture meaning beyond exact word matches.

## Business Takeaway

This system works well as a fast first-pass filter to narrow a large resume pool into a shortlist, but final hiring decisions should always involve human review — particularly given the keyword-matching limitations identified above.

## Tools Used

- Python, Jupyter Notebook
- NLTK (text preprocessing)
- Scikit-learn (TF-IDF, cosine similarity)
- Matplotlib (candidate comparison chart)

## Files

- `resume_screening.ipynb` — full notebook with code, outputs, and analysis
- `Resume.csv` — dataset used
