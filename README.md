# Comparative Analysis of Skeletal Muscle Gene Expression

## Executive Summary

Gene expression can differ between individuals and biological groups. Examining these differences helps researchers investigate patterns of gene activity and understand how gene expression varies between male and female skeletal muscle samples.

Using Python, pandas, NumPy, SciPy, and Matplotlib, I analyzed publicly available gene expression data from the Genotype-Tissue Expression (GTEx) project. The analysis compared gene expression in skeletal muscle samples from male and female participants, using transcripts per million (TPM) as the expression measurement.

The initial metadata contained 742 skeletal muscle samples: 510 male and 232 female. After matching the metadata with the gene expression data, 569 samples remained, including 398 male and 171 female samples.

I used Welch's independent two-sample t-test to compare gene expression between the two groups and applied Bonferroni correction to account for multiple comparisons. The analysis included three visualizations: a sample distribution chart, a top 10 gene expression chart, and a volcano plot.

The results highlighted several genes with substantially higher average expression in the male sample group, including EIF1AY, RPS4Y1, KDM5D, USP9Y, and UTY. This project demonstrates how Python can be used to prepare biological data, conduct statistical comparisons, identify expression patterns, and visualize analytical results.

## Research Question

Do males and females express genes differently in skeletal muscle tissue?

### Objectives

- Compare gene expression between male and female skeletal muscle samples.
- Match sample metadata with gene expression measurements.
- Calculate average gene expression for each group.
- Use statistical testing to investigate differences in gene expression.
- Apply Bonferroni correction to account for multiple comparisons.
- Visualize gene expression patterns and statistical results.
- Interpret findings while acknowledging the limitations of the analysis.

## Dataset

The data comes from the Genotype-Tissue Expression (GTEx) project, which provides publicly available information about gene expression across human tissues.

**Gene Expression Dataset:** `GTEx_Analysis_2017-06-05_v8_RNASeQCv1.1.9_gene_tpm.gct`

**Sample Metadata:** `GTEx_Analysis_v8_Annotations_SampleAttributesDS.txt`

**Participant Metadata:** `GTEX_Analysis_v8_Annotations_SubjectPhenotypesDS.txt`

**Source:** [GTEx Portal - Adult GTEx Downloads](https://www.gtexportal.org/home/downloads/adult-gtex/bulk_tissue_expression)

The gene expression dataset contains gene-level TPM measurements for individual samples. The annotation files provide sample and participant information used to identify skeletal muscle samples and group them by sex.

### Key Measurement

- **TPM (Transcripts Per Million):** A normalized measure of RNA abundance used to quantify gene expression.

### Sample Overview

- Initial skeletal muscle samples: 742
- Initial male samples: 510
- Initial female samples: 232
- Final matched samples: 569
- Final male samples: 398
- Final female samples: 171

The final sample counts reflect the samples successfully matched between the metadata and gene expression data used in the analysis.

## Research Motivation

Gene expression provides information about the activity of genes in biological samples. Comparing expression between groups can help identify patterns associated with biological differences.

This project investigates the following questions:

- Which genes show differences in average expression between male and female skeletal muscle samples?
- Which genes have the strongest statistical evidence for differences between the two groups?
- How do the average expression levels of selected genes compare between male and female samples?
- How can data visualizations help communicate the results of a gene expression analysis?

The goal was to use Python and statistical methods to investigate differences in skeletal muscle gene expression while distinguishing observed patterns from conclusions that the analysis cannot establish.

## Methodology

1. Loaded the GTEx gene expression data and annotation files into Python.
2. Examined the metadata to identify skeletal muscle samples and their associated sex information.
3. Matched sample metadata with the corresponding gene expression measurements.
4. Identified 742 initial skeletal muscle samples, consisting of 510 male and 232 female samples.
5. Matched the metadata with the expression data, resulting in 569 samples: 398 male and 171 female.
6. Calculated average gene expression for the male and female sample groups.
7. Applied Welch's independent two-sample t-test to compare gene expression between the groups.
8. Applied Bonferroni correction to adjust p-values for multiple comparisons.
9. Ranked the results by adjusted p-value to identify the top 10 genes displayed in the visualization.
10. Created a sample distribution chart, a top 10 gene expression chart, and a volcano plot.
11. Calculated the volcano plot's horizontal-axis values using the log2 ratio of male and female mean expression after adding a pseudocount of 1 TPM to each mean.
12. Exported the gene-level statistical results to `muscle_male_vs_female_results.csv`.

## Skills

**Python:** Data analysis, data manipulation, statistical analysis, and working with large datasets

**Pandas and NumPy:** Data loading, data cleaning, metadata matching, grouping, calculating averages, and numerical operations

**SciPy:** Welch's independent two-sample t-test and statistical hypothesis testing

**Matplotlib:** Data visualization, sample distribution charts, gene expression comparisons, volcano plots, and chart labeling

**Data Analysis:** Exploratory data analysis (EDA), comparative analysis, multiple-testing correction, ranking results, and interpreting statistical findings

**Research Skills:** Working with public scientific datasets, developing research questions, documenting methodology, interpreting biological measurements, and communicating limitations

## Results & Visualizations

The analysis compared gene expression between male and female skeletal muscle samples. Welch's independent two-sample t-test was used to compare group means, and Bonferroni correction was applied to account for multiple comparisons. The following visualizations summarize the sample distribution and key gene expression results.

### 1. Sample Distribution by Sex

This chart shows the distribution of skeletal muscle samples included in the final analysis. After matching the sample metadata with the gene expression data, the analysis included 569 samples: 398 male and 171 female.

![Sample Distribution by Sex](images/sample_distribution.png)

### 2. Top 10 Differentially Expressed Genes

This chart compares average gene expression between male and female skeletal muscle samples for the top 10 genes ranked by Bonferroni-adjusted p-value.

![Top 10 Differentially Expressed Genes](images/top_10_genes.png)

The results highlighted **EIF1AY, RPS4Y1, KDM5D, USP9Y, and UTY**, which showed higher average expression in the male sample group.

EIF1AY had an average expression of approximately 25.21 TPM in males, compared with approximately 0.022 TPM in females. RPS4Y1 had an average expression of approximately 131.93 TPM in males, compared with approximately 0.256 TPM in females.

These values describe differences in group averages and should not be interpreted as proof that the genes are exclusively expressed in males.

### 3. Volcano Plot

The volcano plot displays gene expression differences alongside statistical significance.

![Volcano Plot](images/volcano_plot.png)

The horizontal axis shows the log2 expression ratio calculated using a pseudocount of 1 TPM added to each group's mean expression. The vertical axis shows the negative log10 of the Bonferroni-adjusted p-value.

This visualization helps identify genes with differences in expression and shows the statistical evidence associated with those differences. Statistical significance should be interpreted using the adjusted p-values and the threshold indicated in the plot.

### Summary of Findings

- **Sample composition:** The final analysis included 569 matched skeletal muscle samples, with 398 male samples and 171 female samples.
- **Higher expression in males:** Several highlighted genes, including EIF1AY and RPS4Y1, had substantially higher average expression in the male group.
- **Statistical comparison:** Welch's t-test and Bonferroni correction were used to evaluate expression differences while accounting for multiple comparisons.
- **Visualization:** The three charts summarize sample composition, selected gene expression patterns, and the relationship between expression ratios and statistical significance.
- **Interpretation:** The results describe observed gene expression patterns and do not establish causation or prove that these differences lead to specific changes in muscle function.

## Biological Interpretation

The highlighted genes include Y-chromosome-associated genes, which is consistent with the substantially higher expression observed in the male sample group.

EIF1AY and RPS4Y1 are associated with protein synthesis, while KDM5D, USP9Y, and UTY encode proteins involved in other cellular processes, including gene regulation and protein function.

The expression patterns illustrate how gene expression measurements can differ between biological groups. However, group-level expression comparisons alone cannot establish the biological mechanisms responsible for those differences or determine how they affect muscle physiology.

The results should therefore be interpreted as observed gene expression patterns rather than direct evidence of differences in muscle strength, performance, or other physical characteristics.

## Limitations

- The number of male samples (398) was greater than the number of female samples (171) in the final matched dataset.
- The analysis compares group-level expression patterns and does not establish that sex is the only factor associated with the observed differences.
- Potential confounding factors, such as age, health status, and other participant characteristics, were not included as covariates in the described statistical comparison.
- Welch's t-test compares group means but does not model all the characteristics of RNA-sequencing data.
- Bonferroni correction addresses multiple testing but does not eliminate every possible source of bias or analytical limitation.
- The volcano plot uses a pseudocount of 1 TPM when calculating the expression ratio. Consequently, its horizontal axis is not the ordinary log2 ratio of the unadjusted group means.
- Genes with very low expression may have less stable relative expression estimates.
- The analysis identifies statistical differences but does not establish causation or prove that a gene's expression difference produces a particular biological outcome.
- The findings depend on the samples, expression measurements, statistical methods, and thresholds used in the analysis.

## Next Steps

1. Investigate potential confounding factors by incorporating relevant participant characteristics into an appropriately specified statistical model.
2. Examine the complete set of statistically significant genes and report the number that pass the selected adjusted p-value threshold.
3. Explore chromosome annotations and functional enrichment to investigate the biological processes represented by the results.
4. Compare the findings with results from established RNA-sequencing differential-expression tools, such as DESeq2 or edgeR, using suitable input data and methods.
5. Create additional visualizations, such as heatmaps, to compare expression patterns across selected genes.
6. Improve reproducibility by documenting software versions, data-processing decisions, and analysis settings.

## Tools & Technologies

- Python
- pandas
- NumPy
- SciPy
- Matplotlib
- Jupyter Notebook
- GTEx gene expression and annotation datasets

## Conclusion

This project used Python to compare gene expression between male and female skeletal muscle samples from the GTEx dataset. After matching the expression data with the sample metadata, the analysis included 569 samples: 398 male and 171 female.

Welch's independent two-sample t-test and Bonferroni correction were used to investigate differences in gene expression. The results highlighted EIF1AY, RPS4Y1, KDM5D, USP9Y, and UTY, with particularly large differences in average expression for EIF1AY and RPS4Y1.

The project demonstrates practical experience with data preparation, metadata matching, statistical testing, multiple-testing correction, visualization, and scientific interpretation using Python. It also highlights the importance of accurately reporting analytical methods, distinguishing statistical findings from biological conclusions, and acknowledging limitations when working with real-world scientific data.
