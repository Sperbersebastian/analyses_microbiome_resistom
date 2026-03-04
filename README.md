# Analysis Notebooks

This directory contains the core R Markdown notebooks used for the apple phyllosphere metagenomic analysis. 

The pipeline is designed to be executed sequentially (from `00` to `07`). Every notebook sources the `scripts/00_setup.R` file located in the project root to load required libraries, initialize paths, define helper functions (like CLR transformations and Aitchison distances), and load the sample metadata.

## Notebook Execution Order

1. **`00_setup.Rmd`**
   * **Purpose**: Sandbox for establishing global variables, exploring the structure of the `scripts/00_setup.R` file, and testing helper functions. 

2. **`01_community_composition.Rmd`**
   * **Purpose**: Profiles the microbial community structure using both high-resolution MAGs (species-level) and Read assemblies (genus-level). Performs Centered Log-Ratio (CLR) transformations and visualizes beta-diversity via Principal Component Analysis (PCA) biplots and PERMANOVA statistics.

3. **`02_alpha_diversity.Rmd`**
   * **Purpose**: Calculates within-sample diversity using Hill numbers (q=0: Richness, q=1: Shannon diversity, q=2: Simpson diversity). Includes comprehensive statistical testing (Kruskal-Wallis, Linear Models, Gamma GLMs) to compare diversity between organic and conventional management systems.

4. **`03_differential_abundance.Rmd`**
   * **Purpose**: Identifies specific microbial taxa, viruses, and plasmids that are significantly enriched or depleted depending on orchard management. Employs robust Differential Abundance (DA) frameworks specifically built for sparse compositional data, primarily **ANCOM-BC2** and **ALDEx2**.

5. **`04_resistome.Rmd`**
   * **Purpose**: Focuses entirely on the Antibiotic Resistance Genes (ARGs). Quantifies ARG loads (using Reads Per Kilobase per Genome Equivalent - RPKG), assesses ARG class and mechanism diversity, and compares ARG carriage between chromosomal contigs, MAGs, plasmids, and viruses.

6. **`05_genomic_context.Rmd`**
   * **Purpose**: Investigates the mobilome characteristics associated with ARGs. Predicts viral lifestyles (temperate vs. virulent) using DeepPhage, assesses plasmid mobility (conjugative vs. non-mobilizable) via MOB-typer, and integrates this context with the resistome profile.

7. **`06_quality_check.Rmd`**
   * **Purpose**: Generates essential quality control summaries and visualizations for the assembled genomes (MAG completeness vs. contamination), viral contig distributions, and assembled plasmid lengths.

8. **`07_community_resistome_coupling.Rmd`**
   * **Purpose**: Statistically evaluates the linkage between the overall microbial community structure and the functional resistome profile. Utilizes Mantel tests and Procrustes rotation analysis to determine if changes in taxonomy strictly predict changes in resistance capabilities.

---
*Note: Some supplementary notebooks (like `analysis_overview.Rmd` or `results_overview.Rmd`) may exist for summarizing final plots for publications or presentations.*
