# 🧬 Semantic NLP Filtering for Deep Learning Papers in Virology/Epidemiology

This project aims to filter and classify a dataset of 11,450 academic papers from PubMed to identify those implementing deep learning methods within the fields of virology and epidemiology. Two primary approaches were employed:
1. **Keyword-based filtering** using regular expressions.
2. **Semantic filtering** using a pre-trained BERT-based transformer model.

The objective was to accurately identify and categorize relevant papers based on their method types — **text mining**, **computer vision**, **both**, and **other** — and extract the specific deep learning methods mentioned within each relevant paper.

---

## 📂 Project Structure
The project includes the following main files:
- `keywords-based-filtering.ipynb`: Contains the keyword-based filtering approach.
- `transformer-based-filtering.ipynb`: Implements the semantic filtering approach using sentence-transformer-based embeddings.
- `keyword_filtered_papers.xlsx`: Output file containing papers identified through keyword filtering.
- `filtered_virology_epidemiology_papers_with_semantic_classification.xlsx`: Output file containing papers identified through semantic filtering.
- `README.md`: This document, explaining the purpose, approach, and instructions for running the code.

## 🚀 How to Run

1. Install the required libraries:
   ```bash
   pip install pandas nltk sentence-transformers openpyxl
2. Run the keyword-based filtering script in Jupyter notebook
3. Run the semantic filtering script in Jupyter notebook

The output files will be saved in the current directory.

---

## 📊 Solution Overview

### 1️⃣ Keyword-Based Filtering
The keyword-based filtering script (``keywords-based-filtering.ipynb`) leverages regular expressions to match specific terms within the **Title** and **Abstract** fields of each paper. It identifies relevant papers based on predefined lists of terms related to:
- Virology/Epidemiology
- Deep learning neural networks
- Computer vision techniques
- Text mining methods
- Generative AI and transformers

Each relevant paper is then categorized into one of four types based on the presence of terms indicating specific methods:
- **text mining**
- **computer vision**
- **both**
- **other**

#### Results
- **Relevant Papers**: 507 out of 11,450
  - **Method Type Breakdown**:
    - Text mining: 132
    - Computer vision: 17
    - Both: 1
    - Other: 357

### 2️⃣ Semantic Filtering
The semantic filtering script (`transformer-based-filtering.ipynb`) uses a pre-trained BERT-based model (`all-MiniLM-L6-v2`) from the Sentence Transformers library to capture the semantic meaning of the **Title** and **Abstract** text. This approach allows for identifying papers that may use different wording but contain relevant deep learning applications in virology and epidemiology.

Papers are included if they reach a specified cosine similarity threshold with predefined phrases related to deep learning, virology, and epidemiology. Classification is also based on cosine similarity, comparing each paper's text to the descriptions of the four categories.

#### Results
- **Relevant Papers**: 3,920 out of 11,450
  - **Method Type Breakdown**:
    - Text mining: 1,513
    - Computer vision: 201
    - Both: 1,428
    - Other: 778

---

## 📈 Comparison of Approaches

### Why Semantic Filtering Is More Effective
1. **Enhanced Semantic Understanding**: Unlike keyword-based filtering, which matches specific terms, semantic filtering captures the meaning of sentences. This allows it to identify relevant papers even when the exact keywords are not present.
2. **Higher Recall**: Semantic filtering identified 3,920 relevant papers compared to 507 identified by keyword filtering, achieving a broader and more accurate representation of deep learning applications in virology and epidemiology.
3. **Reduced Misclassification**: Keyword-based filtering may default to the "other" category due to the absence of specific keywords. In contrast, semantic filtering utilizes cosine similarity scores to more accurately classify the methods used in each paper.

---

## 📈 Resulting Dataset Statistics
| Approach           | Relevant Papers | Text Mining | Computer Vision | Both | Other |
|--------------------|-----------------|-------------|-----------------|------|-------|
| **Keyword-Based**  | 507             | 132         | 17              | 1    | 357   |
| **Semantic-Based** | 3,920           | 1,513       | 201             | 1,428| 778   |

---

## 📄 Explanation of NLP Techniques Used

1. **Keyword-Based Filtering**:
   - Utilized regular expressions to match predefined keywords.
   - Limited by the specific terms in its list, leading to potential misclassifications.

2. **Semantic Filtering**:
   - Implemented a BERT-based model to capture semantic similarities.
   - Used cosine similarity scores to filter relevant papers and classify methods more accurately.
   - Avoided misclassification due to flexible interpretation of text, resulting in higher recall and precision.

---

## 📋 Summary
This project demonstrates the application of semantic NLP techniques to efficiently filter and classify deep learning research papers. The semantic approach provides a more accurate and scalable alternative to traditional keyword-based methods, reducing the likelihood of missing relevant papers and improving classification accuracy.
