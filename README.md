# **The Gene Expression Interpretation & Functional Enrichment Analysis of Glioblastoma**
 
## **Description**
This project is centered around the analysis of a Glioblastoma gene expression dataset. The project is split into three parts:
1. Interpretation of the gene expression dataset using RStudio
2. Functional enrichment analysis on the upregulated genes
3. Visualization of the functional enrichment analysis results using RStudio

Dataset:https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv

You will need the following packages in RStudio:
1. gplots - Heatmap generation: 
2. dplyr - Data manipulation
3. ggplot2 - Functional enrichment analysis visualization

These packages can be installed using install.packages() and loaded using library()

The following functional enrichment analysis tools can be used 
1. ShinyGO: http://bioinformatics.sdstate.edu/go/
2. GOrilla: https://cbl-gorilla.cs.technion.ac.il/
3. PANTHER: https://geneontology.org/

### **Gene Expression Interpretation**
1.The URL is to be pasted directly to RStudio, then read using read.csv
  > url <- "https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv"

  - You can customize the rows and columns to be included using row.names() or col.names()
2. Heatmaps are generated using heatmap.2() from gplots. Please note that the dataset is directly converted to the matrix form using as.matrix() 
     - The heatmap is completely customizable, from removing dendrograms, to clustering the rows and columns, to alternating the scale, to the color palette used and more.
     - For other color palette options, use https://colorspace.r-forge.r-project.org/articles/hcl_palettes.html
     - If you recieve an error related to the margins, simply make the plot pane larger with your pointer, or reduce the margin using margins() .
     - If you face any issues with the graphic display, use dev.off()

### **Functional Enrichment Analysis**
1. The data is separated into two groups according to column names, due to their similarity
2. To subset the groups into upregulated and downregulated genes:
     - calculate the fold changes using means. There are many possible formulas for this, but the log2 formula was used to accurately display the difference between the over and under expressed genes on our set
     - calculate the p-value using the t.test forumla
     - subset the genes according to the p-value and fold change of choice.
4. Visualize the fold change and negative log of p-values to observe the split
5. Extract the geneIDs into a txt file and paste the list into the functional enrichment site of choice. In this project, we've used PANTHER as the main site, and ShinyGO for conformation. We've configured the tool to provide us with pathways under the GOdatabase with a FDR cutoff of 0.05.
        - We've only used the upregulated genes for this project. The steps are applicable for both datas separately or together

### **Functional Enrichment Analysis Visualization**
1. Group the pathway name, the number of genes, and the negative log10 of the FDR generated from the website
2. Generate a simple plot using ggplot2. The plot can be customizable. Some of the simple plots can be:
     - Lollipop plot
     - Line plot
     - Bubble plot
     - Dot plot
