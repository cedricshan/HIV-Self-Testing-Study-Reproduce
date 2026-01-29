# Replication Study: HIV Self-Testing Promotion via Web-Based Platforms

## Interactive Results

View the complete analysis results:

| Analysis | View Online |
|----------|-------------|
| Table 1: Participant Characteristics | [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/reproduce_table1.html) |
| Primary Analysis: Poisson Model | [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/primary_analysis.html) |
| Secondary Analysis: Attitudes & Stigma | [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/reproduce_secondary_outcomes.html) |

## Study Overview

This replication study reproduces key findings from Stafylis et al. (2022), which investigated the relative effectiveness of social media sites, dating apps, and information search sites in promoting HIV self-testing among minority men who have sex with men (MSM). The original study enrolled 254 participants through advertisements on platforms including Facebook, Instagram, Grindr, Jack'd, Google, and Bing, offering free HIV home self-test kits to young (18-30 years) Black and Latino MSM at increased risk of HIV infection.

The primary objective was to compare HIV self-test kit ordering rates across three platform types using a Poisson regression model. The secondary objective explored associations between test kit ordering and participant characteristics, including HIV-related stigma, attitudes toward HIV treatment, and medical mistrust.

## Replicated Table 1

Table 1 presents the sociodemographic and behavioral characteristics of the 254 per-protocol participants. Our replication successfully reproduced the key statistics: the median age of 25 years (IQR 23-27), with 78.4% identifying as Black or African American and 26% as Hispanic/Latinx. The majority (82.7%) reported condomless receptive anal sex in the past 90 days, and 75.2% had ever tested for HIV during their lifetime. Among those who had tested, the median time since last test was 11 months (IQR 6-21). The complete replicated Table 1 is available in [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/reproduce_table1.html).

## Replicated Results

For the primary analysis, we fitted a Poisson regression model with wave-by-platform interaction, using log(days) as an offset to estimate daily ordering rates. Our results confirmed that Jack'd (dating app) showed the highest ordering rate at 3.29 kits/day in Wave 2, significantly outperforming Instagram (0.34 kits/day) and Bing (0 kits/day).  Full results are in [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/primary_analysis.html).

For the secondary analysis, we reproduced three key associations between test kit ordering and participant attitudes. Using Fisher's exact test, we confirmed that participants who did not order a kit were significantly more likely to agree with "People in my life would leave if I had HIV" (48.1% vs. 33.7%, p = 0.035). Using Wilcoxon rank-sum tests, we found that non-orderers had higher mean scores on "I think that new HIV/AIDS treatments can eradicate the virus from your body" (3.8 vs. 3.1, p = 0.029), and orderers were more likely to disagree with "I could not be friends with someone who has HIV/AIDS" (p = 0.032). These results are detailed in [View Report](https://htmlpreview.github.io/?https://github.com/cedricshan/HIV-Self-Testing-Study-Reproduce/blob/main/result/reproduce_secondary_outcomes.html).

## Reflection

This replication was successful, with all conclusions accurately matching the published results. The process demonstrated a rigorous replication workflow. First, I identified the key findings from the published article, including the exploratory data analysis results presented in Table 1, the primary outcome (comparing HIV self-test kit ordering rates across three platform types using a Poisson regression model with wave-by-platform interaction), and the secondary outcomes (associations between test kit ordering and participant attitudes toward HIV, treatment beliefs, and stigma using Fisher's exact test and Wilcoxon rank-sum tests). Next, I confirmed the key variables and performed data preprocessing, such as filtering to the per-protocol sample and creating derived variables. Then, I consulted Appendix 1 and Appendix 3 to verify the specific modeling approaches and statistical testing methods. Finally, I implemented the replication through programming in R.

During this process, discrepancies between replicated results and original results occurred frequently. In such cases, I learned to first check whether the overall conclusions were consistent and whether key indicators like p-values were substantially different. Once the overall analysis plan was confirmed to be correct, I could then carefully analyze the specific reasons for any differences. For example, the secondary analysis initially showed a sample size of 76 instead of 77 for the non-ordering group, which was resolved after discovering that participants with `ORA_REDEEMED == "Over 60 days"` should be classified as non-orderers.

Additionally, integrating multiple sources to complete the replication proved challenging. The manuscript itself provided the overall research context, key findings, and statistical conclusions. Appendix 1 provided the SAS code for the Poisson regression model, which guided my R implementation. Appendix 3 provided detailed tables of secondary outcome results, including the specific statistical tests used (Fisher's exact test vs. Wilcoxon rank test). The data dictionary provided variable definitions and coding schemes. The dataset itself provided the raw data requiring careful inspection to understand actual value distributions. The key lesson from this task is that having a clear understanding of the overall file structure and the relationships between different sources at the outset makes the replication process much more efficient.

## References

Stafylis, C., Vavala, G., Wang, Q., McLeman, B., Lemley, S. M., Young, S. D., ... & Klausner, J. D. (2022). Relative effectiveness of social media, dating apps, and information search sites in promoting HIV self-testing: Observational cohort study. *JMIR Formative Research*, 6(9), e35648. https://doi.org/10.2196/35648. Available at: https://pmc.ncbi.nlm.nih.gov/articles/PMC9591705/

National Institute on Drug Abuse Clinical Trials Network. CTN-0083: Comparing Web-based Platforms for Promoting HIV Self-testing. https://ctnlibrary.org/protocol/ctn0083/

R packages used: `tidyverse` for data manipulation, `emmeans` for estimated marginal means and pairwise comparisons (https://cran.r-project.org/web/packages/emmeans/), and `kableExtra` for table formatting.


