# Gene Expression Analysis for Predicting Breast Cancer Treatment Response  

## Overview  
This repository contains an RNA-Seq analysis pipeline aimed at identifying gene expression differences to predict the effectiveness of a breast cancer drug treatment. By comparing gene expression profiles of responders and non-responders, we aim to uncover biomarkers that could help in assessing treatment efficacy.  

## Workflow  

### 1. **Preprocessing & Quality Control**  
- Downloaded raw sequencing reads from GEO.  
- Performed adapter trimming using Cutadapt.  
- Conducted quality control (QC) using FastQC.  
- Aligned reads to the reference genome.  
- Counted reads per gene using featureCounts.  
- Checked expression levels of specific genes (e.g., *IFNGR1*) across different samples to verify data quality.  

### 2. **Differential Expression Analysis**  
- Used DESeq2 to normalize counts and handle noise from low-expression genes.  
- Identified significantly upregulated and downregulated genes between treatment responders and non-responders.  
- Created:  
  - **Heatmap**: Showed distinct expression patterns between groups.  
  - **Volcano plot**: Highlighted differentially expressed genes (*BRCA2* was expected to be significant based on prior research but was not in this dataset).  
  - **Bar plot**: Visualized the top 10 upregulated and downregulated genes.  

### 3. **Functional Enrichment Analysis**  
- **HumanMine**: Identified key upregulated genes (*SCT, LIPH, PGLYRP4*) and downregulated genes (*ISLR, AVIL, HES7*).  
- **g:Profiler**:  
  - **Upregulated genes**: Linked to immune activation, coagulation cascades, lipid metabolism, and cholesterol synthesis, suggesting an immune response in patients who responded to treatment.  
  - **Downregulated genes**: Related to cell development and response to growth factors, which aligns with the expected suppression of tumor growth in successful treatment cases.  
- **GORILLA**: Showed enrichment of genes involved in positive regulation of cell death, supporting the idea that treatment responders activate apoptotic pathways to eliminate cancer cells.  
- **GSEA**:  
  - **Non-responders** showed enrichment in tumor resistance pathways (*TGF-β signaling, melanoma, and other cancer-related pathways*).  
  - These genes were absent in responders, suggesting they successfully responded to treatment and did not activate resistance mechanisms.  

## Conclusion  
This analysis identified gene expression signatures that distinguish responders from non-responders to a breast cancer drug treatment. Upregulated pathways in responders reflect immune activation and metabolic adaptation, while downregulated genes correspond to suppressed tumor growth. Importantly, non-responders showed activation of tumor resistance pathways, which may explain treatment failure. The absence of these pathways in responders suggests that gene expression profiling could serve as a predictive tool for treatment effectiveness.  

Future work could refine gene selection, account for potential confounding factors, and validate findings using independent datasets. Identifying key biomarkers could help personalize treatment strategies for breast cancer patients.  
