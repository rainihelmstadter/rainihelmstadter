# Urban Greenspace and Depression Prevalence in Chicago, IL

## Introduction
For this project, I investigated the relationship between urban greenspace and depression prevalence in Chicago, IL. Urban greenspaces are widely known to have a variety of impacts on public health outcomes, from _____ to _______ to ________ (add sources here). In a previous project, I have investigated how greenspace influenced asthma rates in Chicago. For this project, I was interested in investigating how greenspaces influence mental health outcomes, rather than physical health outcomes. Specifically, I investigated depression rates. Common treatment recommendations for depression can include regular exercise and interaction with nature; access to greenspace could obviously impact these treatments. Previous studies have investigated this topic. ____ found ______; ______ found _______.

Greenspaces are often unfairly distributed across cities due to histories of redlining and inadequate funding. Typically, neighborhoods with less greenspace are home to marginalized communities.

## Methods
To investigate this question, I utilized data from the [CDC Places](https://www.cdc.gov/places/tools/data-portal.html) dataset and [NAIP imagery](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-aerial-photography-national-agriculture-imagery-program-naip) accessed through the [Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/) (MPC). The CDC Places dataset _______. NAIP imagery ___________. I accessed the MPC using the STAC API. I used the NAIP imagery to calculate NDVI statistics on greenspace for each census tract. 

First, I downloaded census tracts from the CDC, and then utilized the Socrata API to download data on depression rates for each census tract in 2023. Next, I gathered the MPC URL(s) for the NAIP imagery that corresponds to each census tract. This list of URLs was then be used to compute the NDVI statistics on the MPC. The statistics were: fraction vegetated, or fraction of the census tract that has vegetated (green) landcover; edge density, or how divided up or cohesive the greenspace in a tract is; and mean patch size, which is the average size of a greenspace in the given tract. To identify edges for the edge density, I performed a convolution using a 3x3 kernel. After computing NDVI statistics, I made chloropleth plots to visually compare depression rates and the various greenspace statistics. Finally, I used a linear regression model to better understand how strong the relationship between greenspace and depression rates is. I used a train-test-split method to test the data, as well as investigate spatial bias. Before performing the regression, I log transformed some variables to ensure issues of collinearity and normal distribution didn't interfere.

## Results

## Discussion

## Conclusion

## Sources

## Notebook
