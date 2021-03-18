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

# DATA FORMAT

1.  Upload data must be in comma-separated-value (.CSV) file.
2.  Headers must be true in the uploaded file.
3.	The first column must be biomarkers (In transcriptomics – Ensembl accession number).
4.	Column names must be ENSEMBLE ID, log FC, log CPM, P-value for all four uploaded treatments of transcriptomics study.

![Input data](https://github.com/Punit201016/OMnalysis/blob/main/www/upload_table.png)
5. The data must be as shown in the data screenshot above.

# UPLOAD DATA
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_1.PNG" height = "600" width = "400"> </img>
1.  The app features can be explored using the **Differentially expressed example data tab**.
2.  Use the preloaded RNA-seq data of human brain microvascular endothelial cell line induced with four neuroinvasive pathogens (West Nile Virus and Tick-borne encephalitis virus protein E domain DIII and Neisseria meningitidis and its ligand MafA), capable to cause central nervous system infection. The raw data is published and can be acessed using https://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-8052/?query=wnv and https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6904618/.
3.  Using **Upload Expression data Browse tab** the CSV file of expression matrix upto four experimental conditions with expression value (log fold change), a measure of significance (P-value), count of reads (log counts per million) can be uploaded. 
4.  After uploading you may select from the currently provided species Human, Chicken, Pig and Cow with the help of a dropdown **select a species tab** to perform further analysis.
5.  After selecting the species user needs to convert the less informative ENSEMBLGENE ID to more informative IDs using the **ID conversion tab**.
6.  After mandatory ID conversion of list of genes in expression data,  user needs to click on the **SUBMIT button** to perform the ID conversion. 
7.  The result of ID conversion can be downloaded using the **Download button** in CSV format.

# PCA
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_2.PNG" height = "500" width = "700"> </img>
1.	Principal component analysis (PCA) is an unsupervised dimension reduction method that allows us to understand the relationships among the attributes of expression data. PCA analysis calculates the principal components using the Euclidean distance and linear transformation of the expression data. It calculates the most significant variable in the provided data to calculates first principal component (PC1), second principal component(PC2) and so on.
2.	Two types of PCA plots are provided, first  is **variable PCA plot** that provides information about the direction and relationship among the variables (treatments) and second is **Biplot PCA** that visualize the features of variable PCA plot and observation (genes) of a specific variable in single plot.
3.	Most of the variables are explained in PC1 and PC2, however, **only for Biplot PCA drop-down tab** is available to **explore and compare the other available PCs**.
4.	The output of the reactive plot can be downloadble in four supporting **image formats jpeg, png, pdf and tiff**.
5.	The **dimension and the resolution of output PCA plot** can be adjusted with the help of **numerical input tabs**. The default value are 20, 20 and 300 for width, height and resolution respectively.
6. After providing all the necessary information you can download the **PCA plot using Download button.**
# Plots
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_3.PNG" height = "600" width = "700"> </img>
1.	Scatter plot uses log fold change versus log counts per million to visualize your expression data in the form of up and down-regulated genes. Each dot in the scatter plot represents up-regulated genes (green colour),  non-significant genes (black colour) and downregulated genes (red colour).

2.	The **slider input option** is available for the user to provide the **numeric input P-value cutoff** for both plots and **FC-cutoff for volcano plot** required to generate plots. The default numeric P-value cutoff is 0.02 and FC-cutoff is 1.2.
3.	Using **plot title option** user can write a title to the generated plot (example:- Treatment-1).
4.	Volcano plot uses log fold change versus -log10 (P-value), so that the most significant and highly upregulated and downregulated genes can be visualized. In the volcano plot each red rhombus shape represents the gene with gene name.
5.	After selecting the treatment user have to click on the **checkbox of plots** required to generate plots and table to visualize the each treatment data with converted ids.
6.	The output of the plots can be downloadable in four supporting image formats jpeg, png, pdf and tiff **using the drop-down format option**.
7.	The dimension and the resolution of output plots can be adjusted with the help of **numerical input tabs**. The default value is 20, 20 and 300 for width, height and resolution, respectively.
8.	After providing all the necessary information user can download the plots with the help of **Download button**.

# Statistical filtering
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_4.PNG" height = "600" width = "700"> </img>
1.	With the help of **checkbox button treatments 1, 2, 3 and 4** you can visualize the data and plot of the selected treatment.
2.  **Three numerical input boxes** are provided to filter out the genes that are unable to cross the threshold values. Three statistical parameters are log counts per million (expression value), log fold change (magnitude of change) and P-value (value of significance) provided to obtain significantly differentially expressed genes.
3.	Use the **Venn diagram checkbox** to visualize the common significantly DEGs in the uploaded treatments. Also, you can use a Venn diagram to obtain common or different up and down-regulated genes in two group of treatments.
4.	The dimension and the resolution of output Venn diagram and histogram can be adjusted with the help of **numerical input tabs**.The default value is 20, 20 and 300 for width, height and resolution, respectively.
5.	Two separate **download tabs** first and second are provided to download Venn diagram and histogram, respectively.
6.	Using **histogram** you can visualize the number of differentially expressed genes that falls on the log fold change range. Additionally, by using **all treatment checkbox** you can visualize the total number of up and down-regulated genes avialble in each treatment in a single histogram.
7.	Using **Title** option you can write the title to the generated diagram or histogram (example:- Treatment-1)
8.	The Venn diagram and histogram can be downloadable in four supporting **image formats jpeg, png, pdf and tiff using the drop-down format option.**
9.	The generated diagram can be downloaded using the **Download button.**

# Gene ontology (GO) enrichment analysis
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_5.PNG" height = "500" width = "800"> </img>
1.	Use the **ontology classes checkbox** to perform the categorical analysis of your expression data, either in the biological process (multiple molecular activities integrates to perform a process) or molecular function (activities at the molecular level by gene product) or cellular component (site of function concerning cellular structure).
2. 	**P-value cutoff** and the **q-value cutoff** are provided to obtain enriched test and significantly enriched test, respectively. The default p-value and q-value cutoff is 0 and can be adjusted to 0.01 and 0.05.
3.	The methods provided to perform **gene ontology enrichment analysis** are **over-represented analysis (ORA)**, (based on hypergeometric test and mapping of genes to the annotated biological vocabulary) and **gene set enrichment analysis** (GSEA), (based on the Kolmogorov Smirnov test and consider gene set with their log fold change value).
4.	The gene ontology analysis main panel is populated with **subtabs Ontology result-1, Ontology result-2, Ontology result-3, and  Ontology result-4** each subtab shows the output result of the analysis.
5.	After providing the necessary inputs click on the **Go button** it launch the enrichment analysis. Please keep in mind that the same input values will be used for all treatments.
6.	In the **drop-down pAadjust method tab** 7 adjustment methods Holm, Hochberg, Hommel,  Bonferroni,  Benjamini and Hochberg (BH),  Benjamini and Yekutieli (BY), FDR and none are provided to control false postive result. Above mentioned first four methods control the family-wise error rate (probability of making one or more false discoveries) and      remaining methods control the expected proportion of discoveries that are rejected falsely (FDR). We suggest FDR correction methods for a more reliable result.
7.	From the ontology result table, you need to provide one go term by selecting only one row and same GO term in all the treatments. This information will be used for the           visualization of heatmaps in the next **GO heatmaps panel**.
8.	These gene ontology result can be downloaded in CSV format by **clicking on treatment checkbox and Download button**.

# GO heatmaps
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_6.PNG" height = "600" width = "800"> </img>
1.	GO heatmaps are the expression values of genes that mapped to the biological term while performing gene ontology enrichment analysis.
2.	It is mandatory to **select at least two similar enriched GO terms from the previous tabular output of GO enrichment analysis of two treatments.**
3.	Two options are available **checkbox ORA and GSEA heatmap visualization to generate the heatmap**, however, the output heatmap depends on the previous **GO enrichment analysis method.**
4.	With the help of **checkbox button treatments 1, 2, 3 and 4** you can **visualize the heatmap and a word cloud of the selected treatment**. It is mandatory to select **at least two treatments to generate the heatmap.**
5.	To adjust the **column, row text and col key size three numerical tabs are available** and the default value for **column text, row text and colour key size is 1.2, 1.2 and 0.04** respectively.
6.	You can provide **text input to assign a title for heatmap**.
7.	The **heatmap and word cloud** can be **downloadable in four supporting image formats jpeg, png, pdf and tiff** using the **drop-down format option**.
8.	The **dimension and the resolution of output heatmap and word cloud** can be adjusted with the help of **numerical input in tabs plot width, plot height and plot resolution**. The default value is 20, 20 and 300 for width, height and resolution respectively.
9.	After providing the necessary information user can **download the generated heatmap using the Download button.**
10.	Word cloud in GO heatmaps shows the **enriched GO texts** that have the highest to lowest number of genes mapped to it.
11.	With the help of **word cloud checkbox** user can generate the word cloud of **selected treatment and type of enrichment method used.**
12.	Using the **max words numeric input tab option** you can increase or decrease the number of enriched go terms visualization in the word cloud. The default value of the maximum words in the word cloud in 100.
13.	The generated word cloud diagram can be **downloaded using the Download button.**
14.	After examining the annotation using GO enrichment analysis, you may proceed to **pathway enrichment analysis**.

# Pathway enrichment analysis
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_7.PNG" height = "600" width = "900"> </img>
1.	This section provides the databases and methods available to perform pathway analysis.
2.	The options provided are **over-represented analysis (ORA), (based on hypergeometric test), gene set enrichment analysis (GSEA), (based on the Kolmogorov Smirnov test), network topology analysis (NTA), ( uses genes, their expression value, and network arrangements (edges and nodes), Reactome pathway analysis uses Reactome database to perform pathway analysis.**
3.	The **default p-value cutoff is 0** and can be adjusted to get significant result, however, 0.05 p-value cutoff can be used as it is applied in the first filter to discard the non-significant gene set and then by removing **false positives result by applying pAdjust mehtod**. This stringency may result in a fewer number of gene set ranked.
4.	In enrichment analysis, gene sets are compared multiple times to the universal datasets and in each run it increases the chances of a false positive result, to overcome this problem multiple adjustment methods are provided.
5.	In the **drop-down pAadjust method tab** 7 adjustment methods Holm, Hochberg, Hommel,  Bonferroni,  Benjamini and Hochberg (BH),  Benjamini and Yekutieli (BY), FDR and to bypass these methods none is available. Above mentioned first four methods control the family-wise error rate (probability of making one or more false discoveries) and remaining methods control the expected proportion of discoveries that are rejected falsely (FDR). We suggest FDR correction methods for a more reliable result.
6. To support **NTA four database** are provided, **biocarta (protein sets participating in the pathway), panther (a curated and comprehensive database to classify protein and their genes through evolutionary relationship), NCI-Nature Pathway Interaction Database (Signaling pathways composed of human biomolecular interactions and cellular processes) and pharmgkb (a comprehensive resource that provides information about how human genetic variation affects the response to medications).**
7.	After providing the inputs, **click on the Go tab to launch the pathway enrichment analysis.** Please keep in mind that in each treatment, the same set of information will be used to **execute pathway enrichment analysis**. 
8.  To **perform pathway enrichment analysis in all treatments** you don’t need to click and provide input each time, instead, you can click on the **subtabs Pathway result-2, Pathway result-3, and Pathway result-4" to execute analysis.**
9.	Pathway enrichment analysis section has **subtabs, Pathway result-1, Pathway result-2, Pathway result-3, and Pathway result-4.** Once the analysis completed a table of enrichment pathways will be displayed in the pathway subtabs.
10.	From the pathway analysis result table, you need to **select one same enriched pathway by selecting only one row in all treatments**. This information will be used for the visualization of the expressed gene in the next section enriched pathway visualization.
11.	These Pathway enrichment result can also be downloaded in **CSV format by clicking on treatment checkbox and Download button**.

# Enriched pathway visualization
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_8.PNG" height = "500" width = "900"> </img>
1.	After selecting the single and same pathway in all the treatments from the pathway enrichment result table, you can visualize the pathway using **pathway visualization tabs and according to the pathway enrichment method performed earlier.**
2.	**Three options are  available Pathway ORA, Pathway GSEA, ReactomePA**. You can select any one of them and view the output on the right side **subtabs panel of ORA pathway output or GSEA pathway output or Reactome pathway output.**
3.	If the previous pathway enrichment analysis was ORA then only ORA pathway will be visualized in the ORA pathway output subtab, if not, it will show an error.
4.	Once you are on the ORA, GSEA or  pathway output, you can visualize genes set of four treatments with their log fold change value. The colour code can be changed using **three tabs highly expressed (High), medium expressed (Medium) and lowly expressed genes (Low)**
5.	The default colour code for high is green, for medium grey and low in red. You can **select more colour combination from the none, red, green, yellow, blue, and grey to visualize the expression values on enriched pathway.**
6.	Once you have selected the colour code, select among the treatments provided under the **header Treatments uploaded that you desire to visualize on the enriched pathway.**
7. The output from the reactome pathway analysis can be intrepret using the below notation image.
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_10.PNG" height = "600" width = "800"> </img>
8.	Keep in mind that the visualization of pathways depends on the **pathway enrichment analysis method and selection of the same pathway in all treatments.**
9.	On the **left bottom, Download tab** is provided to download the **pathway image of ORA, GSEA and ReactomePA output in PNG image format**."))
# Literature info
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_9.PNG" height = "600" width = "800"> </img>
img(src = "./www/om_9.png", height = 200, width = 980)
strong(p("1.	This section provides the option to retrieve the information from the Europe PMC by providing biomarkers id, species, disease, cell or tissue type in the text input tab provided below ", span(strong("Literature search header.", style = "color:white; background-color: black"))),
p("2.	The Literature retrieval limit has an input option to provided number that will decide the fetching of the literatures in number."),
p("3.	Once the literature search and retrieval limit is provided, you can proceed with the ", span(strong("submit button", style = "color:white; background-color: black"))," to perform the retrieval of scientific literature."),
p("4.	After completion of the retrieval process, the result in tabular form will appear in the right side subtab literature info panel."), 
p("5.	On literature info table you have to select one scientific literature row at a time to view the abstract and other information on the next subtab", span(strong(" Abstract info.", style = "color:white; background-color: black"))),
p("6.	If the keyword provided in the Literature search is not correct then the result may produce an error or blank table of literature info."))
