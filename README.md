# GWAS_data

## GENEVA diabetes data

The Health Professionals Follow-up Study (HPFS) was launched in 1986 and organized by the National
Institutes of Health (NIH) as part of the Gene Environment Association Studies (GENEVA). 
The working dataset contains 2,558 subjects with 40,568 SNPs. As the
number of SNPs that are associated with BMI and related disorders and diseases is not expected
to be large, we further conduct a marginal screening based on SNPs' marginal associations with
BMI. This screening may help generate more reliable findings, although we note that this step is
not essential. We select the region of 10,000 consecutive SNPs with the smallest sum of p-values for
downstream analysis.


Finally, the GENEVA type 2 diabetes data: 2,558 subjects with 10000 SNPs, 8 environment factor

### diabetes_glm.RData
 
 - y: BMI
 - G (DataFrame): 2588*10000
 - E (DataFrame): 2588*8
 
### snp_information.RData
- DataFrame: 10000*8
- the snp infromation correspoing with G. 


## TCGA skin cutaneous melanoma data

The Cancer Genome Atlas (TCGA), as a hallmark cancer genetic program organized by the National
Cancer Institute (NCI), has published high quality genetic, epigenetic, transcriptomic, and
proteomic data. In this study, we consider skin cutaneous melanoma (SKCM) and download the
processed level 3 data from TCGA Provisional using the R package cgdsr.

For G factors, we consider mRNA gene expressions. The analyzed E factors include Age, AJCC nodes
pathologic stage (PN), Gender, Breslow's depth, and Clark level, all of which have been extensively
studied in the literature. In TCGA, gene expression measurements are z-scores, which have been
lowess-normalized, log-transformed and median-centered, and quantify the relative expressions of
tumor samples with respect to normals. Data are available on 298 subjects and 18,934 gene expressions.
Among the subjects, 152 died during follow-up. Marginal screening is also conducted,
and the 10,000 genes with the strongest marginal associations with survival are selected for G-E
interaction analysis.

### SKCM.RData

- G (DataFrame): gene factor. 298*10000
- E (DataFrame): environmental factor. 298*5
- y: min(T,C), where T is survival time and C is the censoring time. 298*1 
- delta: I(T< C). where delta indicates whether the lifetime T corresponds to an event (delta=  1) or is
censored (delta =  0). 298*1
