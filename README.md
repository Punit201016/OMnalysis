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

1.	Upload data must be in the xlsx file for the label free quantitative proteomics data.
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
7.	After selecting the species, the user needs to convert the less informative ENSEMBLGENE ID or UniProt ID to more informative IDs using the _**ID conversion tab**_.
8.	Press the **_Submit button_** to perform the ID conversion and addition of converted ID column to the uploaded data.
9.	Press the **_Download button_** to download the converted ID table in CSV format.


# PCA
1. Principal component analysis (PCA) is an unsupervised dimension reduction method that allows us to understand the relationships among the attributes of expression data. PCA analysis calculates the principal components using the Euclidean distance and linear transformation of the expression data. It calculates the most significant variable in the provided data to calculate the first principal component (PC1), second principal component (PC2) and so on.
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_2.png" height = "500" width = "1000"> </img>
2.	Two types of PCA plots are provided, first is _**Variable PCA**_ plot that provides information about the direction and relationship among the variables (treatments) and second is **_Biplot PCA_** that visualize the features of variable PCA plot and observation (genes or proteins) of each treatment in single plot.
3.	Press _**Variable PCA**_ or **_Biplot PCA_** to generate transcriptomics variable PCA plot, biplot PCA plot in **_Plot visualization_** window. 
4.	Press Variable PCA or Biplot PCA to generate proteomics variable PCA plot, biplot PCA plot in Plot visualization Proteomic window.
5.	Most of the variables are explained in PC1 and PC2, however, to compare principal components, Select PC from **_Compare PCA for Biplot only drop-down tab_** is to **_explore and compare the other available PCs (PC1 vs PC2, PC2 vs PC3 and PC3 vs PC4)_**.
6.	Select one of the **_Format_** to download images in **_jpeg, png, pdf and tiff formats_**.
7.	Provide **_width, height_** and **_resolution_** to the **_output PCA plot_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px for width_**, **_height_** and **_resolution_** respectively.
8.	Press **_Download button_** to download the **_PCA plot_**.

# Plots
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_3.png" height = "700" width = "800"> </img>
1.	Scatter plot uses log fold change versus log counts per million to visualize your expression data in the form of up and down-regulated genes. Each dot in the scatter plot represents up-regulated genes (green colour), non-significant genes (black colour) and downregulated genes (red colour).
2.	Select from the **_Uploaded treatments_** checkboxes, Example- Treatment-1, then provide the **_numeric input Pvalue cutoff_** for both scatter and volcano plot and **_FC-cutoff for volcano plot_** to generate plots. The default numeric **_Pvalue cutoff_** is 0.001 and **_FC-cutoff_** is 1.2 for transcriptomics and change be changed.
3.	Provide plot name (Example- “Scatter plot of hbmec induced with WNV”) in **_Plot title option_**.
4.	Press one of the checkboxes of **_Plots_** to generate type of plot and **_Table_** to visualize each treatment data with converted ids on **_Scatter plot, Volcano plot or table output window_**.
5.	Select image format type from the drop-down **_Format_** tab. 
6.	Provide **_width, height_** and **_resolution_** to the **_output PCA plot_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px_** for **_width, height and resolution_**, respectively.
7.	Press **_Download button_** to download the **_PCA plot_**.
	

# Statistical filtering
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_4.png" height = "900" width = "800"> </img>
1.	With the help of checkbox button, select one from **_Treatments uploaded tab_** (**_Treatment-1, Treatment-2, Treatment-3 and Treatment-4_**) you can visualize the data and plot of the selected treatment on **_Filter data, Venn Diagram and Histogram_** window.
2.	Select one from the **_Omics Type_** drop down tab (Transcriptomics or Proteomics).
3.	Provide threshold numerical values in **_Statistical filtering tab input boxes_** provided to filter out the genes that are unable to cross the threshold values. The default value is 0 for all components (**_LogFC, LogCPM, Pvalue_**).
4.	Once the filtered data is visible on the **_Filter data window_**. Use the **_Venn Diagram checkbox_** to visualize the common significantly DEGs or abundance protein in the uploaded treatments. Use **_Split into Up and Down-regulated checkboxes_** to obtain common or different up and down-regulated genes in two groups of uploaded treatments.
5.	Provide **_width, height_** and **_resolution_** to the **_output Venn diagram and Histogram_** using **_numerical input tabs_**. The default values are **_20cm, 20cm and 300px for width, height and resolution_**, respectively.
6.	Use two separate **_Download tabs_**, first to download Venn diagram and second to download histogram.
7.	Click on the **_Histogram’s Treatment checkbox_** and one treatment checkbox to generate each treatment histogram showing the number of differentially expressed genes or proteins that falls on the log fold change range and **_All Treatment checkbox_** generate the total number of up and down-regulated genes or proteins available in each treatment in a single histogram.
8.	Use **_Title_** input tab to write the title to the generated diagram or histogram (example: - “Venn diagram or Histogram of Treatment-1”)
9.	Select Venn diagram and Histogram **_image format types_** from **_jpeg, png, pdf and tiff using the drop-down Format_** option.

# Gene ontology (GO) enrichment analysis
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_5.png" height = "600" width = "900"> </img>
1.	Select the **_Omics Type_** according to the uploaded data types.
2.	Use the **_Gene ontology classes checkbox_** to perform the categorical analysis of your expression data, either clicking on the **_GO Biological Process_** (multiple molecular activities integrates to perform a process) or **_GO Molecular Function_** (activities at the molecular level by gene product) or **_GO Cellular Component_** (site of function concerning cellular structure). 
3.	After selecting one of the **_Gene ontology classes_**, provide **_Pvalue cutoff_** and the **_q-value cutoff ORA_**. The default Pvalue and q-value cutoff is 0 and can be adjusted.
4.	Select one of the provided adjustment methods from the **_pAadjust Method tab_**. List are Holm, Hochberg, Hommel, Bonferroni, Benjamini and Hochberg (BH), Benjamini and Yekutieli (BY), FDR to control false positive results. Above mentioned first four methods control the family-wise error rate (probability of making one or more false discoveries) and remaining methods control the expected proportion of discoveries that are rejected falsely (FDR). We suggest FDR correction methods for a more reliable result.
5.	Select one of the provided **_Enrichment analysis method, GO ORA_** (based on hypergeometric test and mapping of genes to the annotated biological vocabulary) and **_GO GSEA_**(based on the Kolmogorov Smirnov test and consider gene set with their sorted log fold change value).
6.	After providing the necessary inputs click on the **_Go! button_** to launch the enrichment analysis. Please keep in mind that the same input values will be used for all treatments to maintain the standard of enrichment analysis.
7.	The result of the enrichment analysis is visualized on the **_subtabs Ontology result-1, Ontology result-2, Ontology result-3, and Ontology result-4_**.
8.	From the ontology result table, **_select one enriched GO term by selecting only one row and same GO term in all the treatments_**. This information will be used for the generation of heatmaps in the next **_GO heatmaps section_**.
9.	**_Download GO result_** in CSV format by **_clicking on treatment checkbox_** and then on **_Download button_**.


# GO heatmaps
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_6.png" height = "700" width = "800"> </img>
1. It is mandatory to **_select at least two similar enriched GO terms from the previous tabular output of GO enrichment analysis of two treatments._**
2. Select one of the **_GO ORA_** or **_GO GSEA_** methods from **_Heatmap visualization_**.
3. Click on at least two checkbox buttons from **_Treatments 1, 2, 3 and 4_** to generate **_heatmap (Example if you select Treatment-1 and 3, Treatment-2 will automatically include in the heatmap._** 
4. Adjust value in _**col text size, row text size**_ and **_col key size numerical tabs_**. The default value for **_col text size, row text siz_e** and **_col key size_** are **_1.2, 1.2 and 0.04_**, respectively.
5. Provide text in the **_Title for heatmap input tab_** to provide main text on heatmap.
6. Download **_Heatmap and word cloud_** using image **_Format drop down tab_**. 
7. Adjust **dimension and resolution of output heatmap and word cloud** using numerical input in tabs Plot width, Plot height and Plot resolution. The default value is 20cm, 20cm and 300px for width, height and resolution, respectively.
8. After providing the necessary information download the generated heatmap using the **_Download button_**.
9. Generate **_Word cloud_** of the selected treatment using **_Word cloud checkbox_**.
10. Provide the **_max words numeric input tab option_** to increase or decrease the number of enriched go terms visualization in the **_word cloud_**. The default value of the maximum words in the word cloud is 100.
11. Press the second **_Download button_** to download the generated word cloud diagram.


# Pathway enrichment analysis
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_7.png" height = "600" width = "900"> </img>
1. Select the **_Omics Type_** according to the uploaded data types.
2. Select one of the options provided in **_Select Pathway analysis Method (Over-represented analysis (ORA), Gene set enrichment analysis (GSEA), Network Topology Analysis (Human), ReactomePA (Human) and STRING_** to perform pathway analysis.
3. Provide numeric input in the **_Pvalue cutoff tab_** and select one of the **_pAdjusted Method tabs_** to overcome the chances of getting false positive results. Note that stringency cutoff value may result in a fewer number of gene set enrichment ranked pathways.
**_Network Topology Analysis (Human)_** is supported by **_four databases_** first,  **_biocarta (protein sets participating in the pathway)_**, second, **_panther (a curated and comprehensive database to classify protein and their genes through evolutionary relationship)_**, third, **_NCI-Nature Pathway Interaction Database (Signaling pathways composed of human biomolecular interactions and cellular processes)_** and fourth, **_pharmgkb (a comprehensive resource that provides information about how human genetic variation affects the response to medications)_**.
Once the above steps are checked, click on the **_Go! tab_** to launch the pathway enrichment analysis. 
Click on the **_subtabs to perform pathway enrichment analysis for “Pathway result-2, Pathway result-3, and Pathway result-4"_**.
From the pathway analysis result table, **_select one row with the same enriched pathway in all treatments_**. This information will be used for the visualization of the expressed gene or proteins in the next section **_Enriched pathway visualization_**.
Click on the **_Pathway enrichment result Treatments_** and then **_Download button_** to download result in **_CSV format_**.

# Enriched pathway visualization
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_8.png" height = "300" width = "1200"> </img>
1. After selecting the single and same pathway in all the treatments from the **_pathway enrichment result table_**, you can visualize the pathway using **_pathway visualization tabs and according to the pathway enrichment method performed in the previous section of OMnalysis_**. 
2. Select one of the **_Pathway ORA, Pathway GSEA, ReactomePA_** and **_STRING PPI_** checkbox provided in **_Pathway visualization_**. You can select any one of them and view the output on the right-side **_subtab panels ORA pathway output_** or **_GSEA pathway output_** or **_Reactome pathway output_** or **_STRING network_**.
3. If the previous pathway enrichment analysis was ORA, then only the ORA pathway will be visualized in the **_ORA pathway output subtab_**, if not, it will show an error.
4. Select the color code from three drop down tabs for **_highly expressed (Up)_**, **_No induced or absent expressed (No sign)_** and **_supressed genes or proteins (Down)_**.
5. The default colour code for **_Up is green_**, **_No sign grey_** and **_Down in red_**. You can select more colour combination from the **_none, red, green, yellow, blue, and grey to visualize the expression values on enriched pathway_**.
6. Select the **_Treatments uploaded_** to visualize the enriched pathway of **_Treatment-1, Treatment-2, Treatment-3, Treatment-4_**.
7. The output from the reactome pathway analysis can be interpreted using the below notation image.	
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_10.png" height = "700" width = "800"> </img>
8. Keep in mind that the visualization of pathways depends on the **_pathway enrichment analysis method_** and **_selection of the same pathway in all treatments_**.
9. Press the **_Download tab_** to download the **_pathway image of ORA, GSEA and ReactomePA and STRING output in PNG image format_**.
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_11.jpg" height = "700" width = "800"> </img>

# Literature info
<img src = "https://github.com/Punit201016/OMnalysis/blob/main/www/om_9.png" height = "250" width = "1400"> </img>
1. This section provides the option to retrieve the information from the Europe PMC by providing **_biomarkers name, species, disease, cell or tissue type_** in the **_text input tab below Literature search_**.
2. The **_Literature retrieval limit_** has an input option to provide a number that will decide the fetching of the literatures. The default is 100.
3. Once the literature search and retrieval limit are provided, you can **_proceed with the submit button to perform the retrieval of scientific literature_**.
4. The result in tabular form will appear in the **_literature info subtabs_**.
5. **_Select one scientific literature row_** in **_literature info table_** at a time to view the abstract and other information on the **_next subtab Abstract info_**.
6. If the keyword provided in the Literature search is not correct then the result may produce an error or blank table of literature info.
	
