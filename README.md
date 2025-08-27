# 🧬 Nuclear Heterogeneity Analysis Using Deep Learning Models  
**Comparative evaluation of Cellpose and StarDist for nuclei segmentation in H&E histopathology images**

## 📌 Overview
This project investigates **nuclear heterogeneity** in H&E-stained histopathology images by comparing two state-of-the-art deep learning models: **Cellpose** and **StarDist**.  
The study evaluates segmentation quality, extracted nuclear features, statistical significance, and clustering validity to determine which model produces more biologically consistent results.

## 📂 Repository Contents
nuclear-heterogeneity-analysis/
│── notebooks/

│ └── analysis_cellpose_stardist.ipynb # Main analysis notebook

│── Nuclear_Heterogeneity_Report.pdf # Final report

│── data/ # (structure only, not included)

│ ├── CAtiles/ # Tumor region masks

│ ├── HEtiles/ # H&E-stained images

│ └── QUPath_CSVs/ # Feature CSVs per image

│── features/ # Example CSV outputs

│ ├── cellpose_nuclear_features.csv

│ ├── cellpose_shape_features.xlsx

│ └── ...

│── figures/ # Sample images & plots

│── README.md

│── requirements.txt

│── LICENSE

> ⚠️ Dataset is **not distributed** here due to size and restrictions. Folder structure and sample CSVs are provided for reproducibility.

## 🗂 Dataset Structure
- **CAtiles/** → 33 folders × 5 tumor masks each  
- **HEtiles/** → 33 folders × 5 H&E image tiles each  
- **QUPath_CSVs/** → 33 folders × 5 CSVs each (per image measurements)  

Each image can be visualized as:  
1. H&E image  
2. StarDist mask  
3. CA mask  
4. StarDist mask restricted to nuclei inside CA  

## 🔬 Features Compared (19 total)
- **Spatial:** Centroid X, Centroid Y  
- **Shape:** Area, Length, Circularity, Solidity, Max/Min diameter  
- **Staining:** Hematoxylin & Eosin (mean, median, min, max, std)  
- **Counts:** Nuclei Count  

## 📊 Analyses Performed
| Analysis Type           | Purpose                               | Tools |
|-------------------------|---------------------------------------|-------|
| t-test / Mann–Whitney U | Statistical significance              | `scipy.stats` |
| Cohen’s d               | Effect size                           | `matplotlib` |
| Box/Violin plots        | Distribution differences              | `seaborn` |
| Correlation heatmap     | Feature relationships                 | `seaborn` |
| Bland–Altman plots      | Agreement level                       | `matplotlib` |
| Coefficient of Variation| Feature stability                     | `numpy` |
| Classifier importance   | Identify discriminative features      | `sklearn` |

## 🏆 Scorecard Criteria
Weighted evaluation combining statistical, clustering, and retention metrics:

| Metric                  | Weight | Better |
|-------------------------|--------|--------|
| Silhouette Score        | 0.25   | Higher |
| Davies–Bouldin Index    | 0.15   | Lower  |
| Calinski–Harabasz Index | 0.15   | Higher |
| Mean p-value (t-test)   | 0.20   | Lower  |
| Mean \|Cohen’s d\|      | 0.15   | Higher |
| Total Nuclei Retained   | 0.10   | Higher |

## 🚀 How to Run
1. Clone this repo:
   ```bash
   git clone https://github.com/<YOUR-USERNAME>/nuclear-heterogeneity-analysis.git
   cd nuclear-heterogeneity-analysis
   ````
2. Create environment:
   ```bash
   pip install -r requirements.txt
   ````
4. Open the Notebook
   ```bash
   jupyter lab notebooks/MIAA.ipynb
   ````
## 📄 Report
The full written report (with background, methods, results, discussion, and references) is available here:
👉 reports/Nuclear_Heterogeneity_Report.pdf

## 📜 License
Released under the MIT License – see LICENSE for details.

## ✨ Author
Sania Dutta

## 🙏 Acknowledgments
This project was carried out under the supervision of **Dr. Arkadiusz Gertych**,  
Faculty of Biomedical Engineering, Silesian University of Technology.
