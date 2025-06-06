# Analysis of BCR repertoire in patients with type 2 diabetes

### scRepertoire

To identify differences in clonal diversity of the B-cell receptor (BCR) repertoire between patients with type 2 diabetes mellitus (T2D) and controls, a quantitative analysis was performed using the clonalDiversity function of the scRepertoire package. Clonotypes were defined based on strict CDR3-sequence matching, and diversity was assessed using several metrics: the Shannon index, inverse Simpson index, Gini-Simpson index, normalised entropy, and richness scores including Chao1 and ACE. For most metrics, no significant differences were found between groups. However, the Chao1 score, which reflects the estimated number of unique clones taking into account rare clones, was markedly higher in T2D patients compared to controls (362,753 vs 118,857, respectively), which may indicate an increase in rare clonal populations in diabetic patients. Analysis of BCR repertoire in patients with type 2 diabetes

BCRs are formed by somatic recombination of the gene segments **Variable (V)**, **Diversity (D)** and **Joining (J)**, which provides a wide variety of antigen-recognition domains. The most variable region of the receptor is **CDR3**, formed at the V-D-J junction region, and it is this region that determines the specificity of antigen interaction. Therefore, to better understand the B-cell receptor (BCR) repertoire in patients with type 2 diabetes mellitus (T2D), we quantitatively analysed the frequency of observation of the V-, D- and J-segments of immunoglobulin heavy chain (IGH).
To assess the statistical significance of differences, Fisher's criterion followed by correction for multiple testing (FDR) was applied. The results of the analysis did not reveal any segment whose frequency of use differed significantly between groups (q-value < 0.05). In addition, visualisation of the distribution of V-, J- and VJ-segments also showed a high degree of similarity of profiles between the groups: differences in frequencies were minimal. Thus, based on the results of this study, we can conclude that the repertoire of immunoglobulin segments in B-cells of T2D patients and healthy subjects is similar.

<p>
  <img src="https://github.com/user-attachments/assets/b0acdc36-e78b-448c-9027-707b9ba676f1" width="250" />
  <img src="https://github.com/user-attachments/assets/b5661ae5-319f-417b-8b3a-fd3b8f25e11e" width="250" />
  <img src="https://github.com/user-attachments/assets/171cb1c5-e23c-4619-8968-33dcd4a92c22" width="250" />
</p>


### Benisse 

In this study, we performed an integrative analysis of single B-cell data (single-cell RNA-seq and scBCR-seq) obtained from type 2 diabetic patients and healthy donors to identify B-cell clusters potentially involved in diabetes-specific pathological processes.

For this purpose, we used the Benisse algorithm, a model developed to jointly analyse B-cell receptor (BCR) and transcriptomic data (gene expression) at the level of individual B-cells (single-cell). The model translates each CDR3H sequence into a numerical vector. Next, contrastive learning is applied so that BCRs with similar specificity are closer to each other in this embedding space. In the next step, Benisse trains a new latent space in which nearby BCRs point to similar receptors and simultaneously corresponding cells have similar transcriptome profiles. In this latent space, a sparse graph is constructed where nodes are B-cell clonotypes and edges are similarity-based (expression-corrected) connections between BCRs. This graph allows to identify BCR networks, i.e. groups of B-cells similar in origin and function.

This analysis identified 2921 clusters, of which 1645 contained more than one cell. However, subsequent statistical analysis using the permutation test and adjustment for multiple testing did not identify any B cell clusters enriched with cells from patients with type 2 diabetes (T2D) compared to controls.

### Partis 

Partis is an HMM-based framework for identifying V(D)J recombinations, estimating the frequency of somatic hypermutations in immunoglobulin sequences, and identifying clonal families and germline. It is built on the HMM ham compiler and the Smith-Waterman ig-sw annotation toolkit. 

Analysis of the results obtained using the Partis tool and visualized by UMAP demonstrated that the frequency of somatic hypermutations was significantly higher in memory cells compared to naive B cells, which is consistent with reality. Biologically, naive B cells are cells that have not yet encountered antigen. Their immunoglobulin (Ig) genes retain the germinal sequence, that is, they do not contain SHM. Upon activation, the naive B cell migrates to the germinative center where active proliferation occurs. The cells undergo SHM by the action of the enzyme AID (activation-induced cytidine deaminase). This leads to the accumulation of point mutations in variable regions of Ig genes. Cells whose receptors have an increased affinity for the antigen receive survival signals and differentiate into memory cells or plasma cells. Many studies show that the frequency of SHM in memory cells can range from 5 to 10% of substitutions in variable regions, whereas in naive cells this figure is close to 0%, which is confirmed in our case. 

At the same time, the level of mutations in atypical B cells is comparable to that in naive cells and for the most part their number is 0.

<p align="center">
  <img width="468" src="https://github.com/user-attachments/assets/406dd9e9-b668-4a9b-9d64-63ec49c142ad" style="display:inline-block; margin-right:10px;" />
  <img width="468" src="https://github.com/user-attachments/assets/d5abf24a-b45e-4151-b926-ef3e0c989fed" style="display:inline-block;" />
</p>

### Monocle3

We used Monocle3 to analyse expression data of single B cells derived from type 2 diabetic patients and healthy donors. Monocle3 is an R-based single-cell analysis tool designed to study cell populations, reconstruct cell developmental trajectories over time (pseudo-time) and perform differential expression analysis.

First, Monocle3 uses the UMAP or PCA method to represent multidimensional data in 2D or 3D space. This allows cells to be visualized and compared to each other based on their overall expression profile. The program then constructs a minimal graph that connects clusters of cells as a branching structure. This is a graph with branching and pathways - it models the intended development or change of cells. Internally, Monocle3 uses a principal graph learning algorithm that traverses cell densities and connects them by the shortest distance, creating a developmental trajectory. Next, an initial cluster was chosen from where development begins. This is an important point because the pseudo-time is calculated from this point. The pseudo-time for each cell is then calculated, which is simply a numerical value that reflects the distance along the trajectory from the root cell. This allowed us to visualize a potential pathway for B-cell differentiation or activation.

Pseudotime analysis revealed a single trajectory of B-cell differentiation starting from naive B cells (B naive) and moving to memory cells (B memory), which can be traced both in healthy donors and in patients with type 2 diabetes. At the same time, a group of B atypical cells forms a separate cluster spatially isolated from the main trajectory in the graph, indicating their participation in alternative biological processes unrelated to this lineage of differentiation.

<p align="center">
  <img src="https://github.com/user-attachments/assets/87c3ade2-64a0-416f-aea1-e04731ca2ff0" width="300" />
  <img src="https://github.com/user-attachments/assets/48d34edc-8798-4e0e-b9e6-d41cbbd7a92c" width="300" />
</p>


The presented visualizations show a two-dimensional projection (UMAP) of all studied B cells, colored according to the pseudotimes for 1 fig, calculated using the Monocle3 algorithm; for 2 fig, the coloring corresponds to the donor type (red - healthy, blue - T2D). Each point corresponds to a single cell, and the color reflects its position along the developmental trajectory: from purple (initial states of B naive cells, pseudotime ≈ 0) to yellow (late states, B memory cells, pseudotime ≈ 9).
Black lines on the graph represent the topological trajectory - the assumed path of cell transitions from one functional state to another. Rings indicate branching and key nodes of the trajectory, where, presumably, the separation of cellular states takes place. Numbers are identifiers of graph nodes, which the program assigns automatically. They do not carry any biological meaning.    





