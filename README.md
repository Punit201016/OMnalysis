# OMnalysis: An intergrated web application to visulaize and analyze differential quantitative data
OMnalysis is developed using R shiny, flexdashboard and bioconductor packages. This tool targets researchers who are new to RNA-seq technology and often depends on commercial vendors or core faciltiy to sequence and analyze their data. 
There are open source R packages such as DeSeq2 and edgeR that are extensively used to identify differentially expressed genes from the count data. The filtering of DEGs using FDR value or Fold change value is still the matter of discuss among the scientific community, therefore the young reseachers face difficulty to make actionable insight. OMnalysis uses the list of genes produced from edgeR with count per million normalization, significance value (P-value) and fold change value assigned to each lsit of gene over or under expressed in the treatments. 

![OMnalysis workflow](https://github.com/Punit201016/OMnalysis/blob/main/www/OMnalysis_1.png)

The app is hosted on shiny.io link https://omnalysis.shinyapps.io/OMnalysis/

# Instructions
1. You can run this app on your desktop after installing R base and R studio.
2. Once the environment is ready, install packages required for OMnalysis.
3. Install R shiny supporting packages.
4. install.packages(c("flexdashboard", "dplyr", "shiny", "shinydashboard", "DT", "tidyverse", "shinythemes", "tidyr", "gplots", "tibble", "gridExtra", "RColorBrewer", "slickR", "devtools", "ggbiplot", "factoextra", "ggplot2", "data.table", "VennDiagram", "fields", "wordcloud", "SBGNview", "europepmc"))
5. Install Bioconductor packages using Install.packages("BiocManager")
6. install.packages(c("AnnotationDbi", "Biobase", "BiocFileCache", "BiocGenerics", "BiocParallel", "BiocVersion", "biomaRt", "Biostrings", "clusterProfiler", "DO.db", "DOSE", "EnhancedVolcano", "enrichplot", "fgsea", "GO.db", "GOSemSim", "graph", "graphite", "IRanges", "KEGGgraph", "KEGGREST", "org.Bt.eg.db", "org.Gg.eg.db", "org.Hs.eg.db", "org.Ss.eg.db", "pathview", "qvalue", "reactome.db", "ReactomePA", "Rgraphviz", "S4Vectors", "XVector", "zlibbioc"))

DATA FORMAT
strong(p("
1. Upload data must be in comma-separated-value (.CSV) file."),
p("2.	Headers must be true in the uploaded file."),
p("3.	The first column must be biomarkers (In transcriptomics – Ensembl accession number)."),
p("4.	Column names must be ENSEMBLE, logFC, log CPM, PValue for all four uploaded treatments of transcriptomics study."),
