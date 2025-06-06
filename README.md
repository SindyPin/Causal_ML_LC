# Causal Feature Selection from Integrated Genomic Resources Enhances Machine Learning Performance of Long COVID Early Detection

This repository contains **all code, data processing pipelines, and supplementary materials** required to reproduce the results from our paper:

> Piñero S.L. *et al.* (2025) *Causal Feature Selection from Integrated Genomic Resources Enhances Machine Learning Performance of Long COVID Early Detection* (CIKM '25).

Supplementary Materials, including complete gene lists, pathway annotations, and full model performance metrics, are available in `SM/`.

---

## 🧭 Project Overview & Methodology

> Long COVID (Post-Acute Sequelae of COVID-19) affects 10-40% of COVID-19 survivors, yet current diagnostic approaches rely on symptom presentation, precluding early intervention opportunities.

### 🔎 Key Innovations
- **Causal feature selection framework** that transforms mechanistic gene discovery into actionable ML features
- **Pre-symptomatic risk stratification** using molecular signatures before clinical manifestation
- **Integration of three causal inference methods**: Transcriptome-Wide Mendelian Randomization (TWMR), Control Theory (CT), and Differential Causal Effects (DCE)
- **Systematic evaluation across 16 ML models** including foundation model TabPFN
- **Biologically interpretable predictions** with each feature linked to explicit causal hypotheses

### 🎯 Our Approach
- Generate multiple causally-informed feature sets capturing distinct disease mechanisms
- Compare causal vs. variance-based feature selection across diverse ML architectures
- Demonstrate superior performance of compact causal panels (100-gene optimal)
- Validate biological relevance through literature curation (97/427 genes confirmed)
- Enable molecular-based risk assessment shifting from reactive to proactive care

![Causal Feature Selection Workflow](Workflow.png)

---

## 📊 Key Results

- **Causal features outperform traditional selection**: 1.4% precision improvement, 3.7% ROC-AUC improvement
- **500CTG subset achieves best performance**: Precision 0.678, ROC-AUC 0.631
- **TabPFN shows exceptional responsiveness** to causal features with 100-gene DCEG-Pathways achieving F1 0.760
- **Literature validation**: 22.7% of prioritized causal genes have established Long COVID roles

---

## 🗄️ Data Sources

Our framework integrates multiple genomic resources:

1. **GTEx eQTL data** (V8): 49 tissue-specific datasets for TWMR analysis
2. **Long COVID GWAS** (Lammi et al. 2023): 3,018 cases, 1,093,995 controls
3. **Mount Sinai RNA-seq** (GSE215865): 1,392 transcriptomic profiles
4. **Human PPI networks** (Vinayagam et al. 2011): Network backbone for CT
5. **KEGG pathways**: 348 human pathways for DCE analysis

Download required data:
- RNA-seq: [GSE215865](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE215865)
- Place `counts.txt.gz` and `sample_sheet.txt` in `data/`

---

## 🔧 Repository Structure

| Component | Description |
|-----------|-------------|
| `causal_inference/` | TWMR, CT, and DCE implementation scripts |
| `feature_selection/` | Causal feature set generation pipelines |
| `ml_models/` | 16 ML model implementations including TabPFN |
| `evaluation/` | Cross-validation and performance metric scripts |
| `visualization/` | Heatmaps, line plots, and performance figures |
| `SM/` | Supplementary materials and complete results |

### Key Scripts
- `twmr_analysis.R`: Transcriptome-Wide Mendelian Randomization
- `control_theory.py`: Network-based causal gene identification  
- `dce_pathways.R`: Differential Causal Effects computation
- `ML_Models.ipynb`: Complete ML pipeline with 16 models
- `literature_validation.py`: Gene validation against PubMed

---

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/SindyPin/Early_Detection_LongCOVID.git
cd Early_Detection_LongCOVID

# Install dependencies
pip install -r requirements.txt
R -e "source('install_packages.R')"

# Run causal feature selection
python run_causal_selection.py --method all

# Train and evaluate ML models
jupyter notebook ML_Models.ipynb
```

---

## 📈 Causal Feature Sets

| Feature Set | Size | Method | Description |
|-------------|------|---------|-------------|
| 31CG | 31 | MR+CT | High-risk causal genes from integrated analysis |
| 44DCEG | 44 | DCE | Differential causal effect genes |
| 411DCEG | 411 | DCE | Extended pathway-based causal genes |
| 500CTG | 500 | CT | Comprehensive control theory genes |
| 100-DCEG-Paths | 100 | DCE | Optimal compact causal panel |

---

## 📚 Citation

If you use this framework or data, please cite:

```bibtex
@inproceedings{pinero2025causal,
  author    = {Piñero, Sindy Licette and Le, Thuc Duy and Duong, Thi Nhu Ngoc and 
               Li, Xiaomei and Liu, Lin and Li, Jiuyong and Lee, Sang Hong},
  title     = {Causal Feature Selection from Integrated Genomic Resources Enhances 
               Machine Learning Performance of Long COVID Early Detection},
  booktitle = {Proceedings of the 34th ACM International Conference on Information 
               and Knowledge Management (CIKM '25)},
  year      = {2025},
  pages     = {1--10},
  location  = {Seoul, Korea}
}
```

---

## 🤝 License & Contact

This project is licensed under the MIT License.

For questions or collaborations:
- Open an issue on GitHub
- Email: [pinsy007@mymail.unisa.edu.au](mailto:pinsy007@mymail.unisa.edu.au)

---

## 🙏 Acknowledgments

This work was supported by:
- Australian Research Council Discovery Project (Grant DP230101122).
- University Presidents Scholarship (UPS) stipend.
