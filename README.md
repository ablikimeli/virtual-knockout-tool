# virtual-knockout-tool
 Virtual Knockout Tool – a computational method that simulates gene deletions using single‑cell RNA‑seq data. By constructing a gene regulatory network from wild‑type samples and mathematically removing the target gene, it predicts functional consequences without physical experiments.
# Virtual Knockout Tools Collection

A curated collection of computational tools for **in-silico gene knockout** experiments using single-cell RNA sequencing data.

## What is Virtual Knockout?

Virtual knockout (KO) refers to computational methods that simulate the functional deletion of a gene without physical CRISPR or RNAi experiments. These tools predict downstream transcriptional changes and regulatory effects by computationally perturbing gene regulatory networks (GRNs) constructed from wild-type (WT) scRNA-seq data alone.

## Why Virtual Knockout?

- **Cost-effective**: No cell culture, no animal models, no gene editing reagents needed
- **Scalable**: Systematically knockout hundreds or thousands of genes simultaneously
- **Cell-type specific**: Leverages single-cell resolution for precise predictions
- **Accelerates research**: Predicts outcomes before committing to expensive animal KO experiments

## How It Works

Most virtual knockout tools follow a similar pipeline:
1. **Construct GRN**: Build a gene regulatory network from WT scRNA-seq data
2. **Simulate KO**: Remove all outgoing edges of the target gene (or use other perturbation strategies)
3. **Compare networks**: Align the perturbed network to the original to identify differentially regulated genes
4. **Interpret results**: Enrichment analysis reveals affected pathways and biological processes

---

## Main Methods & Tools

### 1. GRN Perturbation Methods

#### 🔬 scTenifoldKnk

A machine learning workflow that performs virtual knockout experiments by constructing gene regulatory networks from scRNA-seq data, then removing outgoing edges of the target gene. Manifold alignment compares original and perturbed networks to identify differentially regulated genes.

- **Paper**: Osorio, D. et al. *Patterns*, 2022, 3(3), 100434. DOI: [10.1016/j.patter.2022.100434
        
        ](https://doi.org/10.1016/j.patter.2022.100434
        
        )
- **Preprint**: bioRxiv, DOI: [10.1101/2021.03.22.436484
        
        ](https://doi.org/10.1101/2021.03.22.436484
        
        )
- **GitHub**: [cailab-tamu/scTenifoldKnk](https://github.com/cailab-tamu/scTenifoldKnk) (R/MATLAB/Python)
- **CRAN**: [scTenifoldKnk](https://cran.r-project.org/package=scTenifoldKnk)
- **Documentation**: [ReadTheDocs](https://sctenifold.readthedocs.io)
- **Languages**: R, MATLAB, Python

---

#### 🔬 GenKI (Gene Knockout Inference)

Uses a variational graph autoencoder (VGAE) to learn latent representations of genes from WT scRNA-seq data. Virtual KO is simulated by removing all edges of the target gene from the GRN, and differences are discerned through latent parameters of the trained VGAE.

- **Paper**: Yang, Y. et al. *Nucleic Acids Research*, 2023, 51(13), 6578-6592. DOI: [10.1093/nar/gkad450
        
        ](https://doi.org/10.1093/nar/gkad450
        
        )
- **GitHub**: [yjgeno/GenKI](https://github.com/yjgeno/GenKI)
- **Language**: R/Python

---

#### 🔬 PRS (Perturbation Response Scanning) / scPII

Adapts a perturbation-response framework originally developed for protein structural dynamics to identify gene modules most susceptible to perturbation. Introduces scPII, a data-driven metric derived from GRNs that quantifies system-level responses to gene perturbations.

- **Paper**: Gupta, S., Romero, S., Cai, J.J. bioRxiv, 2025. DOI: [10.64898/2025.12.15.694358
        
        ](https://doi.org/10.64898/2025.12.15.694358
        
        )
- **Status**: Preprint (December 2025)
- **Code**: Not yet released as dedicated package (from Cai Lab)

---

### 2. Trajectory-Based Methods

#### 🔬 Celloracle

Predicts how transcriptional factor (TF) knockouts alter cell differentiation trajectories and cell fate decisions. Constructs base GRNs using scATAC-seq data, pre-built promoter networks, or user-defined TF-target lists. Uniquely capable of simulating cell fate transitions.

- **Paper**: Kamimoto, K. et al. *Cell Systems*, 2020, 11(4), 343-354. DOI: [10.1016/j.cels.2020.08.013
        
        ](https://doi.org/10.1016/j.cels.2020.08.013
        
        
        
        )
- **GitHub**: [morris-lab/Celloracle](https://github.com/morris-lab/Celloracle)
- **Language**: Python

> **Note**: Celloracle is specifically designed for TF knockout analysis and requires scATAC-seq or pre-defined GRN data. Not suitable for all gene types.

---

### 3. Machine Learning-Enhanced Methods

#### 🔬 MUSIC

Model-based integrated pipeline for single-cell CRISPR screening data analysis, capable of prioritizing gene perturbation effects at the cellular heterogeneity level.

- **Paper**: Duan, B. et al. *Nature Communications*, 2019, 10, 2233. DOI: [10.1038/s41467-019-10284-3
        
        ](https://doi.org/10.1038/s41467-019-10284-3
        
        
        
        )
- **Code**: R package (See paper for access details)
- **Language**: R

> **Note**: MUSIC requires real KO sample data from single-cell CRISPR screens, making it distinct from purely WT-based tools.

---

#### 🔬 GeneSPIDER2

A large-scale GRN simulation and benchmarking tool that can generate realistic single-cell gene expression data with perturbations (including knockdowns). While primarily a simulation/benchmarking tool, it is the only tool that allows simulations of knockdown perturbations using a GRN as the basis for data generation.

- **Paper**: Garbulowski, M. et al. *Bioinformatics Advances*, 2024, 6(3), lqae121. DOI: [10.1093/bioadv/lqae121
        
        ](https://doi.org/10.1093/bioadv/lqae121
        
        
        
        )
- **GitHub**: Not specified (MATLAB toolbox)

---

#### 🔬 OneSC

A platform for simulating cell state transitions using stochastic differential equations governed by a regulatory network of core TFs. Can be used to predict effects of gene perturbations on developmental trajectories.

- **Paper**: Alanis-Lobato, G. et al. *Bioinformatics*, 2024. DOI: [10.1093/bioinformatics/btae654
        
        ](https://doi.org/10.1093/bioinformatics/btae654
        
        )
- **Code**: Available through Oxford Bioinformatics publication

---

## Other Relevant Tools

| Tool | Description | Link |
|------|-------------|------|
| **scTenifoldNet** | Base network construction workflow (underpins scTenifoldKnk) | [GitHub](https://github.com/cailab-tamu/scTenifoldNet) |
| **PertFlow** | Cloud-based workflow for perturbational modeling on scRNA-seq | [Zenodo](https://zenodo.org/records/8326003) |
| **IQCELL** | Predicts effects of gene perturbations on developmental trajectories | [Publication](https://katalog.ub.uni-leipzig.de) |
| **Celcomen** | Spatial causal disentanglement for perturbation modeling | [GitHub](https://github.com/celcomen) |

---

## Key Review Articles

- **Overview of Virtual Knockout Methods** (Bilibili article, 2026): "不用养细胞、不用CRISPR！单细胞虚拟敲除，零实验搞定基因功能预测" — A comprehensive Chinese review covering scTenifoldKnk, Celloracle, and related tools [Link](https://www.bilibili.com/opus/1186906824938356741)

- **Robustness and applicability of functional genomics tools on scRNA-seq data** (Mendeley): Discusses in-silico perturbation simulation strategies [Link](https://www.mendeley.com)

---

## Citation

If you use these tools in your research, please cite the original papers for the respective tools:

```bibtex
@article{osorio2022scTenifoldKnk,
  title={scTenifoldKnk: An efficient virtual knockout tool for gene function predictions via single-cell gene regulatory network perturbation},
  author={Osorio, D. and Zhong, Y. and Li, G. et al.},
  journal={Patterns},
  volume={3},
  number={3},
  pages={100434},
  year={2022},
  doi={10.1016/j.patter.2022.100434}
}

@article{yang2023genki,
  title={Gene knockout inference with variational graph autoencoder learning single-cell gene regulatory networks},
  author={Yang, Y. and Li, G. and Zhong, Y. et al.},
  journal={Nucleic Acids Research},
  volume={51},
  number={13},
  pages={6578-6592},
  year={2023},
  doi={10.1093/nar/gkad450}
}

@article{kamimoto2020celloracle,
  title={Celloracle: Dissecting cell fate decisions through gene regulatory network inference},
  author={Kamimoto, K. and Hoffmann, C. M. and Morris, S. A.},
  journal={Cell Systems},
  volume={11},
  number={4},
  pages={343-354},
  year={2020},
  doi={10.1016/j.cels.2020.08.013}
}
