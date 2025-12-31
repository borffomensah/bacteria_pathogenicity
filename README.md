# Predicting Bacterial Pathogenicity Using Machine Learning on Genomic Features
📊 Project Overview
This project presents an interpretable machine learning framework designed to distinguish between pathogenic and non-pathogenic strains of Escherichia coli. 
By analyzing specific genomic signatures—such as genome size, GC content, and gene counts—this model provides a scalable strategy for early risk assessment and genomic surveillance.

🔗 Live Demo: https://bacteriapathogenicity.streamlit.app

# Biological Context
Bacterial pathogenicity is the ability of bacteria to cause disease, often facilitated by "virulence factors" found on mobile genetic elements. 
Traditional culture-based diagnostics are slow; however, with the rise of Whole Genome Sequencing (WGS), we can now use computational methods to identify high-risk strains in hours rather than days.

This study focuses on four key genomic features:
1. Genome Size: Pathogenic strains often have larger genomes due to the acquisition of Pathogenicity Islands (PAIs).

2. GC Content: Shifts in GC percentage often indicate horizontal gene transfer from foreign species.

3. Virulence Gene Count: Direct markers of an organism's ability to invade a host.

4. AMR Gene Count: The presence of Antimicrobial Resistance (AMR) genes often correlates with increased pathogenicity in clinical settings.

# 🛠️ Technical Workflow
# Data Acquisition & Quality Control
Source: 217 E. coli genomes curated from NCBI RefSeq.

1. Filtering: Genomes were filtered using CheckM to ensure >95% completeness and <5% contamination.

Balance: The dataset is nearly perfectly balanced (109 pathogenic vs. 108 non-pathogenic).

2. Feature Engineering
Used Biopython to parse FASTA files for size and GC content.

Developed a custom keyword-based extraction tool to scan GFF annotation files for virulence and AMR-related determinants (e.g., toxins, adhesins, beta-lactamases).

3. Machine Learning Pipeline
Model: Logistic Regression (chosen for its high interpretability and efficiency).

Evaluation: 80:20 stratified train-test split.

Explainability: Integrated SHAP (SHapley Additive exPlanations) values to visualize how each genomic feature contributes to a specific prediction.

# 📈 Results & Performance
The model achieved near-perfect discrimination on the test set:
# MetricScore
Accuracy0.98
Precision0.98
Recall0.98
F1-Score0.98

# Key Findings:
Virulence gene count was the strongest predictor of pathogenicity.

Lower GC content and Larger Genome Size were consistently associated with pathogenic strains, likely reflecting the acquisition of foreign genetic material through horizontal gene transfer.

# 💻 Tech Stack
Language: Python 3.10

Libraries: scikit-learn, pandas, numpy, biopython, SHAP

Deployment: Streamlit

Bioinformatics Tools: ncbi-genome-download

# Repository Structure
data/: Contains the processed feature matrix (ecoli_features.csv).

notebooks/: Jupyter notebooks for data exploration and model training.

src/: Python scripts for feature extraction and preprocessing.

main.py: The Streamlit web application code.

models/: Serialized trained model (.joblib).
