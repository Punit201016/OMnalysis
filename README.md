# OMnalysis: An intergrated web application to visulaize and analyze differential quantitative data
OMnalysis is developed using R shiny, flexdashboard and bioconductor packages. This tool targets researchers who are new to RNA-seq technology and proteomics study and often depends on commercial vendors or core facilities to sequence and analyze their data. Although exploration of the identified list of genes and proteins is also tedious and challenging (Figure 1).
There are open source R packages such as DeSeq2 and edgeR that are extensively used to identify differentially expressed genes from the count data. The filtering of DEGs using FDR value or Fold change value is still the matter of discussion among the scientific community, therefore the young researchers face difficulty to make actionable insight. OMnalysis uses the list of genes produced from edgeR’s glmTreat with count per million normalization, significance value (P-value) and fold change value assigned to each list of gene over or under expressed in the treatments (Figure 2). Whereas, for label-free relative quantitative proteomics data must contain the columns of UniProt ID, FDR-adjusted P-value and Fold Change in an excel file with each sheet of an experimental condition named Treatment1, Treatment2, Treatment3 and Treatment4 (Figure 3).

![OMnalysis workflow](https://github.com/Punit201016/OMnalysis/blob/main/www/OMnalysis_1.png)

The app is hosted on shiny.io link https://omnalysis.shinyapps.io/OMnalysis/

# Instructions
1. You can run this app on your desktop after installing R base version4.0.3 and R studio
version 1.4.1106.
2. Once the environment is ready, install packages required for OMnalysis.
3. Install R shiny supporting packages.
4. install.packages(c(&quot;flexdashboard&quot;, &quot;dplyr&quot;, &quot;shiny&quot;, &quot;shinydashboard&quot;, &quot;DT&quot;,
&quot;tidyverse&quot;, &quot;shinythemes&quot;, &quot;tidyr&quot;, &quot;gplots&quot;, &quot;tibble&quot;, &quot;gridExtra&quot;, &quot;RColorBrewer&quot;,
&quot;slickR&quot;, &quot;devtools&quot;, &quot;ggbiplot&quot;, &quot;factoextra&quot;, &quot;ggplot2&quot;, &quot;data.table&quot;,
&quot;VennDiagram&quot;, &quot;fields&quot;, &quot;wordcloud&quot;, &quot;SBGNview&quot;, &quot;europepmc&quot;, &quot;shinyjs&quot;,
&quot;futile.logger&quot;, &quot;rio&quot;, &quot;plyr&quot;))
5. Install Bioconductor packages version 3.12 using Install.packages(&quot;BiocManager&quot;)
6. install.packages(c(&quot;AnnotationDbi&quot;, &quot;Biobase&quot;, &quot;BiocFileCache&quot;, &quot;BiocGenerics&quot;,
&quot;BiocParallel&quot;, &quot;BiocVersion&quot;, &quot;biomaRt&quot;, &quot;Biostrings&quot;, &quot;clusterProfiler&quot;, &quot;DO.db&quot;,
&quot;DOSE&quot;, &quot;EnhancedVolcano&quot;, &quot;enrichplot&quot;, &quot;fgsea&quot;, &quot;GO.db&quot;, &quot;GOSemSim&quot;,
&quot;graph&quot;, &quot;graphite&quot;, &quot;IRanges&quot;, &quot;KEGGgraph&quot;, &quot;KEGGREST&quot;, &quot;org.Bt.eg.db&quot;,
&quot;org.Gg.eg.db&quot;, &quot;org.Hs.eg.db&quot;, &quot;org.Ss.eg.db&quot;, &quot;pathview&quot;, &quot;qvalue&quot;, &quot;reactome.db&quot;,
&quot;ReactomePA&quot;, &quot;Rgraphviz&quot;, &quot;S4Vectors&quot;, &quot;XVector&quot;, &quot;zlibbioc&quot;, &quot;STRINGdb&quot;,
&quot;SPIA&quot;, &quot;SBGNview&quot;))

# DATA FORMAT TRANSCRIPTOMICS

1.  Upload data must be in comma-separated-value (.CSV) file for transcriptomics data.
2. Headers must be true in the uploaded file.
3. The first column must be biomarkers (In transcriptomics – Ensembl accession
number).
4. Column names must be ENSEMBLEGENE, logFC, logCPM, Pvalue for all four
uploaded treatments of transcriptomics study.
5. The data must be as shown in the data screenshot below.

![Input data](https://github.com/Punit201016/OMnalysis/blob/main/www/upload_table.png)

# DATA FORMAT PROTEOMICS

1.	Upload data must be in xlsx file for the label free quantitative proteomics data.
2.	Headers must be true in the uploaded file.
3.	The first column must be biomarkers (In proteomics – UniProt ID).
4.	Column names must be UniProt ID, FDR-adjusted P-value and Fold Change for all four uploaded treatments of proteomics study.
5.	The data must be as shown in the data screenshot below. 

![Input data](https://github.com/Punit201016/OMnalysis/blob/main/www/prot_table.png)

# UPLOAD DATA
1.	The app features can be explored using the **_Differentially expressed example data tab_** for transcriptomics analysis and **_Proteomics abundance example data_** for proteomics data analysis.
2.	In side panel below, use the preloaded RNA-Seq data produced by challenging human brain microvascular endothelial cells induced with Borrelia burgdorferi (Treatment1) and Neisseria meningitidis (Treatment2), Streptococcus pneumoniae (Treatment3) and West Nile Virus (Treatment4).
3.	In the side panel below, use the preloaded label free proteomics example data of milk whey samples collected at different time point (36, 42, 57 and 81 hours) from cow intramammary infection induced with Streptococcus uberis bacteria (Mudaliar, et al., 2016).
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_1.png" height = "800" width = "800"> </img>
4.	Select the **_Upload Expression Data Browse tab_**, to upload your own transcriptomics data in CSV file up to four experimental conditions with expression value (log fold change), a measure of significance (P-value), count of reads (log counts per million).
5.	Select the second **_Upload Expression Data Browse tab_**, to upload your own proteomics data in xlsx format file up to four experimental conditions with UniProt ID, FDR-adjusted P-value and Fold Change.
6.	Once the data is uploaded (**ONLY ONE OMICS TYPE at a time**), select the species provided in the select a species tab (Human, Chicken, Pig and Cow) with the help of a dropdown to perform further analysis.
7.	After selecting the species user needs to convert the less informative ENSEMBLGENE ID or UniProt ID to more informative IDs using the _**ID conversion tab**_.
8.	Press the **_Submit button_** to perform the ID conversion and addition of converted ID column to the uploaded data.
9.	Press the **_Download button_** to download the converted ID table in CSV format.


# PCA
1. Principal component analysis (PCA) is an unsupervised dimension reduction method that allows us to understand the relationships among the attributes of expression data. PCA analysis calculates the principal components using the Euclidean distance and linear transformation of the expression data. It calculates the most significant variable in the provided data to calculates first principal component (PC1), second principal component (PC2) and so on.
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_2.png" height = "500" width = "1000"> </img>
2.	Two types of PCA plots are provided, first is _**Variable PCA**_ plot that provides information about the direction and relationship among the variables (treatments) and second is **_Biplot PCA_** that visualize the features of variable PCA plot and observation (genes or proteins) of each treatment in single plot.
3.	Press _**Variable PCA**_ or **_Biplot PCA_** to generate transcriptomics variable PCA plot, biplot PCA plot in **_Plot visualization_** window. 
4.	Press Variable PCA or Biplot PCA to generate proteomics variable PCA plot, biplot PCA plot in Plot visualization Proteomic window.
5.	Most of the variables are explained in PC1 and PC2, however, to compare principal components, Select PC from **_Compare PCA for Biplot only drop-down tab_** is to **_explore and compare the other available PCs (PC1 vs PC2, PC2 vs PC3 and PC3 vs PC4)_**.
6.	Select one of the **_Format_** to download images in **_jpeg, png, pdf and tiff formats_**.
7.	Provide **_width, height_** and **_resolution_** to the **_output PCA plot_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px for width_**, **_height_** and **_resolution_** respectively.
8.	Press **_Download button_** to download the **_PCA plot_**.

# Plots
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_3.png" height = "700" width = "900"> </img>
1.	Scatter plot uses log fold change versus log counts per million to visualize your expression data in the form of up and down-regulated genes. Each dot in the scatter plot represents up-regulated genes (green colour), non-significant genes (black colour) and downregulated genes (red colour).
2.	Select from the **_Uploaded treatments_** checkboxes, Example- Treatment-1, then provide the **_numeric input Pvalue cutoff_** for both scatter and volcano plot and **_FC-cutoff for volcano plot_** to generate plots. The default numeric **_Pvalue cutoff_** is 0.001 and **_FC-cutoff_** is 1.2 for transcriptomics and change be changed.
3.	Provide plot name (Example- “Scatter plot of hbmec induced with WNV”) in **_Plot title option_**.
4.	Press one of the checkboxes of **_Plots_** to generate type of plot and **_Table_** to visualize each treatment data with converted ids on **_Scatter plot, Volcano plot or table output window_**.
5.	Select image format type from the drop-down **_Format_** tab. 
6.	Provide **_width, height_** and **_resolution_** to the **_output PCA plot_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px_** for **_width, height and resolution_**, respectively.
7.	Press **_Download button_** to download the **_PCA plot_**.
	

# Statistical filtering
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_4.png" height = "900" width = "900"> </img>
1.	With the help of checkbox button, select one from **_Treatments uploaded tab_** (**_Treatment-1, Treatment-2, Treatment-3 and Treatment-4_**) you can visualize the data and plot of the selected treatment on **_Filter data, Venn Diagram and Histogram_** window.
2.	Select one from the **_Omics Type_** drop down tab (Transcriptomics or Proteomics).
3.	Provide threshold numerical values in **_Statistical filtering tab input boxes_** provided to filter out the genes that are unable to cross the threshold values. The default value is 0 for all components (**_LogFC, LogCPM, Pvalue_**).
4.	Once the filtered data is visible on the **_Filter data window_**. Use the **_Venn Diagram checkbox_** to visualize the common significantly DEGs or abundance protein in the uploaded treatments. Use **_Split into Up and Down-regulated checkbox_** to obtain common or different up and down-regulated genes in two group of uploaded treatments.
5.	Provide **_width, height_** and **_resolution_** to the **_output Venn diagram and Histogram_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px for width, height and resolution_**, respectively.
6.	Use two separate **_Download tabs_**, first to download Venn diagram and second to download histogram.
7.	Click on the **_Histogram’s Treatment checkbox_** and one treatment checkbox to generate each treatment histogram showing the number of differentially expressed genes or proteins that falls on the log fold change range and **_All Treatment checkbox_** generate the total number of up and down-regulated genes or proteins available in each treatment in a single histogram.
8.	Use **_Title_** input tab to write the title to the generated diagram or histogram (example: - “Venn diagram or Histogram of Treatment-1”)
9.	Select Venn diagram and Histogram **_image format types_** from **_jpeg, png, pdf and tiff using the drop-down Format_** option.

# Gene ontology (GO) enrichment analysis
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_5.png" height = "500" width = "800"> </img>
1.	Select the **_Omics Type_** according to the uploaded data types.
2.	Use the **_Gene ontology classes checkbox_** to perform the categorical analysis of your expression data, either clicking on the **_GO Biological Process_** (multiple molecular activities integrates to perform a process) or **_GO Molecular Function_** (activities at the molecular level by gene product) or **_GO Cellular Component_** (site of function concerning cellular structure). 
3.	After selecting one of the **_Gene ontology classes_**, provide **_Pvalue cutoff_** and the **_q-value cutoff ORA_**. The default Pvalue and q-value cutoff is 0 and can be adjusted.
4.	Select one of the provided adjustment methods from **_pAadjust Method tab_**. List are Holm, Hochberg, Hommel, Bonferroni, Benjamini and Hochberg (BH), Benjamini and Yekutieli (BY), FDR to control false positive result. Above mentioned first four methods control the family-wise error rate (probability of making one or more false discoveries) and remaining methods control the expected proportion of discoveries that are rejected falsely (FDR). We suggest FDR correction methods for a more reliable result.
5.	Select one of the provided **_Enrichment analysis method, GO ORA_** (based on hypergeometric test and mapping of genes to the annotated biological vocabulary) and **_GO GSEA_**(based on the Kolmogorov Smirnov test and consider gene set with their sorted log fold change value).
6.	After providing the necessary inputs click on the **_Go! button_** to launch the enrichment analysis. Please keep in mind that the same input values will be used for all treatments to maintain the standard of enrichment analysis.
7.	The result of the enrichment analysis is visualized on the **_subtabs Ontology result-1, Ontology result-2, Ontology result-3, and Ontology result-4_**.
8.	From the ontology result table, **_select one enriched GO term by selecting only one row and same GO term in all the treatments_**. This information will be used for the generation of heatmaps in the next **_GO heatmaps section_**.
9.	**_Download GO result_** in CSV format by **_clicking on treatment checkbox_** and then on **_Download button_**.


# GO heatmaps
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_6.PNG" height = "700" width = "800"> </img>
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
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_8.PNG" height = "300" width = "1200"> </img>
1.	After selecting the single and same pathway in all the treatments from the pathway enrichment result table, you can visualize the pathway using **pathway visualization tabs and according to the pathway enrichment method performed earlier.**
2.	**Three options are  available Pathway ORA, Pathway GSEA, ReactomePA**. You can select any one of them and view the output on the right side **subtabs panel of ORA pathway output or GSEA pathway output or Reactome pathway output.**
3.	If the previous pathway enrichment analysis was ORA then only ORA pathway will be visualized in the ORA pathway output subtab, if not, it will show an error.
4.	Once you are on the ORA, GSEA or  pathway output, you can visualize genes set of four treatments with their log fold change value. The colour code can be changed using **three tabs highly expressed (High), medium expressed (Medium) and lowly expressed genes (Low)**
5.	The default colour code for high is green, for medium grey and low in red. You can **select more colour combination from the none, red, green, yellow, blue, and grey to visualize the expression values on enriched pathway.**
6.	Once you have selected the colour code, select among the treatments provided under the **header Treatments uploaded that you desire to visualize on the enriched pathway.**
7. The output from the reactome pathway analysis can be intrepret using the below notation image.
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_10.PNG" height = "700" width = "800"> </img>
8.	Keep in mind that the visualization of pathways depends on the **pathway enrichment analysis method and selection of the same pathway in all treatments.**
9.	On the **left bottom, Download tab** is provided to download the **pathway image of ORA, GSEA and ReactomePA output in PNG image format**.
# Literature info
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_9.PNG" height = "250" width = "1300"> </img>
1.	This section provides the option to retrieve the information from the Europe PMC by providing biomarkers id, species, disease, cell or tissue type in the **text input tab provided below Literature search header.**
2.	The Literature retrieval limit has an input option to provided number that will decide the fetching of the literatures.
3.	Once the literature search and retrieval limit is provided, you can **proceed with the submit button to perform the retrieval of scientific literature.**
4.	After completion of the retrieval process, the result in tabular form will appear in the right side subtab literature info panel.
5.	On literature info table you have to **select one scientific literature row at a time to view the abstract and other information on the next subtab Abstract info.**
6.	If the keyword provided in the Literature search is not correct then the result may produce an error or blank table of literature info.
