# Replication Study: HIV Self-Testing Promotion via Web-Based Platforms

## Study Overview

This replication study reproduces key findings from Stafylis et al. (2022), which investigated the relative effectiveness of social media sites, dating apps, and information search sites in promoting HIV self-testing among minority men who have sex with men (MSM). The original study enrolled 254 participants through advertisements on platforms including Facebook, Instagram, Grindr, Jack'd, Google, and Bing, offering free HIV home self-test kits to young (18-30 years) Black and Latino MSM at increased risk of HIV infection.

The primary objective was to compare HIV self-test kit ordering rates across three platform types using a Poisson regression model. The secondary objective explored associations between test kit ordering and participant characteristics, including HIV-related stigma, attitudes toward HIV treatment, and medical mistrust.

## Replicated Table 1

Table 1 presents the sociodemographic and behavioral characteristics of the 254 per-protocol participants. Our replication successfully reproduced the key statistics: the median age of 25 years (IQR 23-27), with 78.4% identifying as Black or African American and 26% as Hispanic/Latinx. The majority (82.7%) reported condomless receptive anal sex in the past 90 days, and 75.2% had ever tested for HIV during their lifetime. Among those who had tested, the median time since last test was 11 months (IQR 6-21). The complete replicated Table 1 is available in `result/reproduce_table1.html`.

## Replicated Results

For the primary analysis, we fitted a Poisson regression model with wave-by-platform interaction, using log(days) as an offset to estimate daily ordering rates. Our results confirmed that Jack'd (dating app) showed the highest ordering rate at 3.29 kits/day in Wave 2, significantly outperforming Instagram (0.34 kits/day) and Bing (0 kits/day). Wave 1 showed no significant differences across platforms (Facebook: 0.19, Grindr: 0.13, Google: 0.24 kits/day). The pairwise comparisons with Hochberg adjustment confirmed significant differences in Wave 2 (p < 0.001 for Jack'd vs. both Instagram and Bing). Full results are in `result/primary_analysis.html`.

For the secondary analysis, we reproduced three key associations between test kit ordering and participant attitudes. Using Fisher's exact test, we confirmed that participants who did not order a kit were significantly more likely to agree with "People in my life would leave if I had HIV" (48.1% vs. 33.7%, p = 0.035). Using Wilcoxon rank-sum tests, we found that non-orderers had higher mean scores on "I think that new HIV/AIDS treatments can eradicate the virus from your body" (3.8 vs. 3.1, p = 0.029), and orderers were more likely to disagree with "I could not be friends with someone who has HIV/AIDS" (p = 0.032). These results are detailed in `result/reproduce_secondary_outcomes.html`.

## Reflection

The replication was successful, with all key findings matching the published results. For Table 1, our statistics aligned exactly with the manuscript. The primary analysis required careful attention to the wave structure, as Wave 1 in the paper combined two data collection phases (WAVE values 1 and 4 in the dataset). The secondary analysis initially showed minor discrepancies in sample sizes (76 vs. 77 for the non-ordering group) until we discovered that participants with `ORA_REDEEMED == "Over 60 days"` should be classified as non-orderers alongside those with `ORA_REDEEMED == "No"`. After this correction, all three secondary outcome analyses matched the published p-values exactly (0.035, 0.029, and 0.032-0.033). This experience highlighted the importance of understanding data coding schemes and consulting supplementary materials for complete methodological details.

## References

Stafylis, C., Vavala, G., Wang, Q., McLeman, B., Lemley, S. M., Young, S. D., ... & Klausner, J. D. (2022). Relative effectiveness of social media, dating apps, and information search sites in promoting HIV self-testing: Observational cohort study. *JMIR Formative Research*, 6(9), e35648. https://doi.org/10.2196/35648. Available at: https://pmc.ncbi.nlm.nih.gov/articles/PMC9591705/

National Institute on Drug Abuse Clinical Trials Network. CTN-0083: Comparing Web-based Platforms for Promoting HIV Self-testing. https://ctnlibrary.org/protocol/ctn0083/

R packages used: `tidyverse` for data manipulation, `emmeans` for estimated marginal means and pairwise comparisons (https://cran.r-project.org/web/packages/emmeans/), and `kableExtra` for table formatting.
