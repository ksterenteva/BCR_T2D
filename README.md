# Analysis of BCR repertoire in patients with type 2 diabetes

### scRepertoire

To identify differences in clonal diversity of the B-cell receptor (BCR) repertoire between patients with type 2 diabetes mellitus (T2D) and controls, a quantitative analysis was performed using the clonalDiversity function of the scRepertoire package. Clonotypes were defined based on strict CDR3-sequence matching, and diversity was assessed using several metrics: the Shannon index, inverse Simpson index, Gini-Simpson index, normalised entropy, and richness scores including Chao1 and ACE. For most metrics, no significant differences were found between groups. However, the Chao1 score, which reflects the estimated number of unique clones taking into account rare clones, was markedly higher in T2D patients compared to controls (362,753 vs 118,857, respectively), which may indicate an increase in rare clonal populations in diabetic patients. Analysis of BCR repertoire in patients with type 2 diabetes

BCRs are formed by somatic recombination of the gene segments **Variable (V)**, **Diversity (D)** and **Joining (J)**, which provides a wide variety of antigen-recognition domains. The most variable region of the receptor is **CDR3**, formed at the V-D-J junction region, and it is this region that determines the specificity of antigen interaction. Therefore, to better understand the B-cell receptor (BCR) repertoire in patients with type 2 diabetes mellitus (T2D), we quantitatively analysed the frequency of observation of the V-, D- and J-segments of immunoglobulin heavy chain (IGH).
To assess the statistical significance of differences, Fisher's criterion followed by correction for multiple testing (FDR) was applied. The results of the analysis did not reveal any segment whose frequency of use differed significantly between groups (q-value < 0.05). In addition, visualisation of the distribution of V-, J- and VJ-segments also showed a high degree of similarity of profiles between the groups: differences in frequencies were minimal. Thus, based on the results of this study, we can conclude that the repertoire of immunoglobulin segments in B-cells of T2D patients and healthy subjects is similar.


<img width="357" alt="image" src="https://github.com/user-attachments/assets/b0acdc36-e78b-448c-9027-707b9ba676f1" />
<img width="316" alt="image" src="https://github.com/user-attachments/assets/b5661ae5-319f-417b-8b3a-fd3b8f25e11e" />
<img width="401" alt="image" src="https://github.com/user-attachments/assets/171cb1c5-e23c-4619-8968-33dcd4a92c22" />

### Benisse 

In this study, we performed an integrative analysis of single B-cell data (single-cell RNA-seq and scBCR-seq) obtained from type 2 diabetic patients and healthy donors to identify B-cell clusters potentially involved in diabetes-specific pathological processes.

For this purpose, we used the Benisse algorithm, a model developed to jointly analyse B-cell receptor (BCR) and transcriptomic data (gene expression) at the level of individual B-cells (single-cell). The model translates each CDR3H sequence into a numerical vector. Next, contrastive learning is applied so that BCRs with similar specificity are closer to each other in this embedding space. In the next step, Benisse trains a new latent space in which nearby BCRs point to similar receptors and simultaneously corresponding cells have similar transcriptome profiles. In this latent space, a sparse graph is constructed where nodes are B-cell clonotypes and edges are similarity-based (expression-corrected) connections between BCRs. This graph allows to identify BCR networks, i.e. groups of B-cells similar in origin and function.

This analysis identified 2921 clusters, of which 1645 contained more than one cell. However, subsequent statistical analysis using the permutation test and adjustment for multiple testing did not identify any B cell clusters enriched with cells from patients with type 2 diabetes (T2D) compared to controls.

### Monocle3



