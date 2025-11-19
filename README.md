# Understanding the Reach and Impact of the Centers for Disease Control and Prevention’s Women’s Health Research, 2018–2023 (working)
## Summary:
Understanding the public health impact of women’s health research is crucial for improving health outcomes and guiding future research priorities. Bibliometric analysis offers a unique suite of tools to identify opportunities to increase impact and measure the dissemination of women’s health research. In the following analysis we aim to assess 5 indicators measuring media attention, policy citation, and academic ciation for publications encompassing research on breast cancer, acute rheumatic fever and chronic rheumatic heart diseases (ARF-CRHD), infections of the kidney, and Alzheimer’s disease. Our analysis demonstrates that CDC’s publications on these conditions did not demonstrate a gap in media attention, academic citations, and policy citations compared with other agency publications. These results underscore the agency’s effectiveness in disseminating its research on these topics and informs strategic decisions for those with a vested interst in disseminating women's health research. For more infomration on this analysis please visit our publication: [Dunkley, Victoria E., Joy Ortega, Martha Knuth, Christie Kim, Mary G. Reynolds, and Bao-Ping Zhu. "Understanding the Reach and Impact of the Centers for Disease Control and Prevention’s Women’s Health Research, 2018–2023." Journal of Women's Health.https://doi.org/10.1177/15409996251379401](https://www.liebertpub.com/doi/abs/10.1177/15409996251379401).

## Data Sources:
1. **CDC WONDER**: The mortality data used to identify the conditions with the highest relative mortality risk for U.S females (2018-2021) was queried using [CDC WONDER](https://wonder.cdc.gov/). CDC WONDER abstracts cause of death data from the National Vitatl Statistics System (NVSS) and categorizes conditions  for data analysis using according to the National Center for Health Statistics’ (NCHS) [List of 113 Selected Causes of Death and Enterocolitis due to Clostridium difficile, and COVID-19](https://www.cdc.gov/nchs/data/dvs/Part9InstructionManual2020-508.pdf) (updated October 2020 to include World Health Organization updates to ICD-10 for data year 2020).
2. **CDC Science Clips**: [CDC Science Clips](https://www.cdc.gov/library/about/index.html) is a database of CDC-authored publications maintained by the Stephen B. Thacker CDC Library. Science Clips publications from 2018 to 2023 were utilized to generate bibliometric indicators assessing media. Additionally, publications from 2018 to 2020 were used to calculate policy and academic indicators. Data was pulled from Science Clips on September 24, 2024.
3. **Altmetric (Proprietary)**: Media attention (proxied from the Altmertic Attentnion Score), academic citation (parsed from Dimension citations) and policy ciation data was queried using digital object identified information (DOI) using the Altmetric Explorer. Access to this granularity of data requires a license. A free alternative to querying academic citation data exists in the form of the free Dimensions API. Bibliometric indicators were calculated using data from publications indexed in Altmetric and BMJ Impact Analytics accessed on December 16, 2024.
4. **BMJ Impact Analytics (Proprietary)**: Additional policy and clinical guidance data was queried using DOIs that were input into BMJ Impact Analytics. Access to this data requires a license.Bibliometric indicators were calculated using data from publications indexed in Altmetric and BMJ Impact Analytics accessed on December 16, 2024.
   
##  Analysis Methodology:
*All analysis was conducted using Python 3.11.7.*
1. Idenitfy conditions that result in high relative mortality risk for U.S. females using NVSS data queried through CDC WONDER **(Code notebook 1 & 2)**.
2. Identify CDC-authored publications on conditions with the highest relative mortality risk for U.S. females using CDC Science Clips.
3. Query media attention, academic citation, and policy citation data from Altmetric and BMJ Impact Analytics.
4. Merge bibliometric indicator data to relevant publications and calculate media attention, academic citation, and policy citation  indicators **(Code notebook 3 & 4)**. The bibliometric indictators in this analysis are:
      - **Percent of publications with media attention**: Assess what proportion of publications on a given topic received any media attention.
      - **Median media attention**: Assess the distribution of media attention for publications on a given topic.
      - **Percent of publications with academic citation**: Assess what proportion of publications on a given topic received any academic citation.
      - **Median academic citation**: Assess the distribution of academic attention for publications on a given topic.
      - **Percent of publications policy citation**: Assess what proportion of publications on a given topic received any policy citation.
6. Generate data visualization **(Code notebook 5)**

## Applicable Research:
The framework of this research is useful for those who want to track the impact of published scientific manuscripts. Post-publication information offers insight into research uptake and can inform future research practices and resource allocation.
## Repo Explained:
*The following repo makes use of 3 parent folders for data, code, and results. For data visualizations and additional supplemental infomration (search string and supplemental file description) please refer to the publication.* 
```
womens_health_publication_impact/
├── data/
│   ├── CDC_WONDER_4_YEAR_TOTAL.xlsx                                                      # Overarching sex-stratified 2018-2021 mortality totals (this populates table 1)
│   └── NVSS_2018_2021_Sex_Stratified_NCHS_Grouping_AgeAdjusted.xlsx/                     # Sex-stratified age-adjusted condition specific dataset (Identifies conditions of interest)
├── code/
│   ├── 1_Initial_Relative_Mortality_Analysis.ipynb
│   ├── 2_Creation_of_Supplemental_Table.ipynb
│   ├── 3_Merge_Indicator_Information_to_SciClips.ipynb
│   ├── 4_Creating_ Bibliometric_Indicator_Table.ipynb                                                       
│   └── 5_Combined_Line_and_Dot_Plot.ipynb                                                    
├── results/
│     ├──RelativeMortalityInitialOutput.xlsx                                              # Output from code notebook 1
│     ├──SupplementalDataTable.xlsx                                                       # Output from code notebook 2
│      ├──202501_Bibliometric Indicator Table.xlsx                                        # Output from code notebook 4
│   └── Bibliometrics/                                                                    # Publications and data used to cacluate bibliometric indicators
│      └── Altmetric Data Pull/                                                           # 2018-2023 indicator data pulled on 12/16 (used for all indicators)
│        ├──Altmetric_20241216_2018_2023_SciClips_Publications_SciClips.xlsx  
│        ├──Altmetric_20241216_2018_2023_Rheumatic_Publications_SciClips.xlsx  
│        ├──Altmetric_20241216_2018_2023_Kidney_Publications_SciClips
│        ├──Altmetric_20241216_2018_2023_BreastCancer_Publications_SciClips.xlsx 
│        ├──Altmetric_20241216_2018_2023_Alzheimers_Publications_SciClips.xlsx  
│      └── BMJ Data Pull/                                                                 # 2018-2020 indicator data pulled on 12/16 ( only used for policy indicator)
│        ├──BMJ_20241216_2018_2020_SciClips_Publications_SciClips.xlsx  
│        ├──BMJ_20241216_2018_2020_Rheumatic_Publications_SciClips.xlsx  
│        ├──BMJ_20241216_2018_2020_Kidney_Publications_SciClips
│        ├──BMJ_20241216_2018_2020_BreastCancer_Publications_SciClips.xlsx 
│        ├──BMJ_20241216_2018_2020_Alzheimers_Publications_SciClips.xlsx  
│      └── SciClips Publications/                                                         # 2018-2023 publications on conditions of interest
│        ├──2018_2023_SciClips_Publications_SciClips.xlsx  
│        ├──2018_2023_Rheumatic_Publications_SciClips.xlsx  
│        ├──2018_2023_Kidney_Publications_SciClips.xlsx  
│        ├──2018_2023_BreastCancer_Publications_SciClips.xlsx  
│        ├──2018_2023_Alzheimer_Publications_SciClips.xlsx  
│      └── SciClips Publications plus Indicators/                                         # Publication and indicators merged output
│        ├──2018_2023_SciClips_Publications_SciClips_Indicators.xlsx   
│        ├──2018_2023_Rheumatic_Publications_SciClips_Indicators.xlsx   
│        ├──2018_2023_Kidney_Publications_SciClips_Indicators.xlsx   
│        ├──2018_2023_BreastCancer_Publications_SciClips_Indicators.xlsx 
│        ├──2018_2023_Alzheimer_Publications_SciClips_Indicators.xlsx 
└── README.md
```

**General disclaimer** This repository was created for use by CDC programs to collaborate on public health related projects in support of the [CDC mission](https://www.cdc.gov/about/cdc/#cdc_about_cio_mission-our-mission).  GitHub is not hosted by the CDC, but is a third party website used by CDC and its partners to share information and collaborate on software. CDC use of GitHub does not imply an endorsement of any one particular service, product, or enterprise. 

**Additional disclaimer** Generative AI  was used to generate and refine code for this analysis. 

## Public Domain Standard Notice
This repository constitutes a work of the United States Government and is not
subject to domestic copyright protection under 17 USC § 105. This repository is in
the public domain within the United States, and copyright and related rights in
the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
All contributions to this repository will be released under the CC0 dedication. By
submitting a pull request you are agreeing to comply with this waiver of
copyright interest.

## License Standard Notice
The repository utilizes code licensed under the terms of the Apache Software
License and therefore is licensed under ASL v2 or later.

This source code in this repository is free: you can redistribute it and/or modify it under
the terms of the Apache Software License version 2, or (at your option) any
later version.

This source code in this repository is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the Apache Software License for more details.

You should have received a copy of the Apache Software License along with this
program. If not, see http://www.apache.org/licenses/LICENSE-2.0.html

The source code forked from other open source projects will inherit its license.

## Privacy Standard Notice
This repository contains only non-sensitive, publicly available data and
information. All material and community participation is covered by the
[Disclaimer](DISCLAIMER.md)
and [Code of Conduct](code-of-conduct.md).
For more information about CDC's privacy policy, please visit [http://www.cdc.gov/other/privacy.html](https://www.cdc.gov/other/privacy.html).

## Contributing Standard Notice
Anyone is encouraged to contribute to the repository by [forking](https://help.github.com/articles/fork-a-repo)
and submitting a pull request. (If you are new to GitHub, you might start with a
[basic tutorial](https://help.github.com/articles/set-up-git).) By contributing
to this project, you grant a world-wide, royalty-free, perpetual, irrevocable,
non-exclusive, transferable license to all users under the terms of the
[Apache Software License v2](http://www.apache.org/licenses/LICENSE-2.0.html) or
later.

All comments, messages, pull requests, and other submissions received through
CDC including this GitHub page may be subject to applicable federal law, including but not limited to the Federal Records Act, and may be archived. Learn more at [http://www.cdc.gov/other/privacy.html](http://www.cdc.gov/other/privacy.html).

## Records Management Standard Notice
This repository is not a source of government records, but is a copy to increase
collaboration and collaborative potential. All government records will be
published through the [CDC web site](http://www.cdc.gov).

## Additional Standard Notices
Please refer to [CDC's Template Repository](https://github.com/CDCgov/template) for more information about [contributing to this repository](https://github.com/CDCgov/template/blob/main/CONTRIBUTING.md), [public domain notices and disclaimers](https://github.com/CDCgov/template/blob/main/DISCLAIMER.md), and [code of conduct](https://github.com/CDCgov/template/blob/main/code-of-conduct.md).
