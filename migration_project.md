---
layout: default
title: Western Tanager Migration
---

# Western Tanager Migration

<a title="http://www.naturespicsonline.com/, CC BY-SA 3.0 &lt;https://creativecommons.org/licenses/by-sa/3.0&gt;, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Western_Tanager_(male).jpg"><img width="256" alt="Western Tanager (male)" src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/7b/Western_Tanager_%28male%29.jpg/256px-Western_Tanager_%28male%29.jpg?20060722052324"></a>


For this project, I made a dynamic plot that shows the migration of Western Tanagers throughout ecosystems in North America. To create this plot, I used observation data from the Global Biodiversity Information Facility (GBIF) and the ecoregions defined by the Resolve Ecoregions of the World project. 

## Western Tanagers

Western Tanagers are migratory songbirds with distinctive colorings. I personally find them quite beautiful, and I think of their arrival in my home in Montana as a sign that spring is ending, and summer is truly arriving. Western Tanagers spend the winter in Central America, and then migrate northward, reaching as far north as northern British Columbia and Alberta, before turning around and flying south for the winter. Interestingly, [as noted by the Audubon Society](https://www.audubon.org/field-guide/bird/western-tanager), Western Tanagers' migration lasts late into the spring, yet they don't spend long at their summer destination, beginning the southward journey by early fall. The Audubon Society notes that "some birds [are] seen away from breeding areas as late as mid-June and as early as mid-July." This tracks with my experience of Western Tanager migration - I typically see them pass through Bozeman in late May or early June.

## GBIF Observations 

The [GBIF network](https://www.gbif.org/) strives to collect data about all types of life on Earth, and provide those data to anyone interested. [The data come from diverse sources](https://www.gbif.org/what-is-gbif), including community observations or citizen scientists. These various streams mean that the GBIF database is quite robust, but may introduce sources of bias that I've corrected for. 

## Resolve Ecoregions

The [Resolve Ecoregions](https://www.resolve.ngo/projects/ecoregions-world) is a depiction of the many ecoregions that cover our planet. In a nutshell, ecoregions depict the geographic extent of a given ecosystem, and represent the full group of biodiversity that depends on the region defined. You can read more about the Ecoregion project [here](https://data-gis.unep-wcmc.org/portal/home/item.html?id=0127920779a64e3f98925f2d3da3b847), or check out the full paper on it [here](https://doi.org/10.1093/biosci/bix014).

## Methods

To visualize Western Tanager migration, I performed the following steps. First, I downloaded a shapefile of the Resolve Ecoregions and utilized the GBIF API to download the dataset of Western Tanager occurrences in 2024. Then, after selecting just the information I needed from the GBIF dataset, I merged the Ecoregions and GBIF files using a spatial join. This resulted in a new file that indicated the Ecoregion each occurence took place in, and discarded any Ecoregions that had no occurrences. After joining the files, I organized the occurrences by ecoregion and month, and normalized the occurence data to account for various sources of bias (further discussion below). Once I had completed all of these steps, I created the plot presented below! For a deeper look, check out the notebook I used below.

## Western Tanager Migration in 2024

<div class="plot-container">
    <iframe src="./projects/migration/western_tanager_migration.html"></iframe>
</div>

<style>
.plot-container {
    width: 100%;
    height: 0;
    padding-bottom: 60%;
    position: relative;
}

.plot-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
}
</style>

## Bias Correction
Because GBIF incorporates citizen scientist observations, it's important to consider how the populations of observers might impact the dataset. Two important sources of bias to consider are sampling density and temporal biases. Lastly, it's also important to consider the identification abilities of observers.

Consider the difference in number of observations between dissimilar locations, such as Denver, CO and Chama, NM. Denver is a metropolitan, densely populated area close to the Rocky Mountains, though it is actually located on the edge of the Plains. Meanwhile, Chama is nestled in the mountains, but is quite rural and sparsely populated. It's reasonable to assume that there would be more observations in Denver than Chama, because there's far more people in Denver than in Chama. However, we wouldn't want to assume that more observations in one area (such as an urbanized area) is indicative of more occurrences of Tanagers in that area. To control for this potential source of bias, I normalized the occurence data by the area of the ecoregion.

In addition, consider the potential difference in number observations at different times of the year. For example, it's reasonable to assume that there might be fewer observations of a species during the winter, because it's cold outside and people aren't as interested in birdwatching. Thus, fewer observations of a species might not be indicative of the lack of presence of that bird, but of a lack of observers. To account for this, I normalized the occurence data by the month as well.

I've also removed extremely rare occurrences of birds. These were occurrences of one bird in an ecoregion and month, which is more likely a misidentification than an occurence of the bird.

## Plot Discussion

In January, February, and March, my plot shows Western Tanagers are mostly in Central America, with a notable population in the southeast United States. By April, their migration clearly begins, and observations are noted across the entire Western US, though the bulk of the population remains in the southwestern US and northern Mexico. The migration proceeds northward through July, with the bulk of the observations in early summer found in the northwestern US and western Canada. The northernmost extent of the Western Tanager migration in 2024 appears to be in the Yukon and Northwestern Territories, potentially reaching as far as the Arctic Ocean. This range is greater than other sources have noted, and may indicate a northern expansion of the Western Tanager's range as the climate warms.

By August, the Western Tanager migration clearly reverses, with much of the population having returned to the southwest and northern Mexico. This matches the migration patterns noted by the Audubon Society, as mentioned above. In September and October, there is a notable population moving through southern California and then Baja California, while the populations in the southwest US and northern Mexico appear to start spreading out across Central America. The remainder of the year shows growing concentrations of observations in Central America, indicating more birds completing their migration cycles. 

There are notable observations in the Upper Midwest and Quebec/New Brunswick throughout the fall, which does not track with common range maps from the [Cornell Ornithology Lab](https://www.allaboutbirds.org/guide/Western_Tanager/overview) or the [Audubon Society](https://www.audubon.org/field-guide/bird/western-tanager), though the Audubon Society notes that Western Tanagers may be observed in Northeast Canada and New England, and [community observations shown by Cornell](https://www.allaboutbirds.org/guide/Western_Tanager/maps-sightings) indicate the presence of Western Tanagers on the East Coast and Northeastern Canada. Further investigation into the GBIF observations might be merited to figure out if these occurrences are due to a more expanded range than previously thought, or possible misidentification of other tanagers, such as the Scarlet or Summer Tanager.

## Sources

To see the code I used for this project, and reproduce my work, please check out [this Jupyter notebook](./projects/migration/western_tanager_migration_notebook.html).

GBIF Observations:

GBIF.org (23 October 2025) GBIF Occurrence Download [https://doi.org/10.15468/dl.pqnfvt](https://doi.org/10.15468/dl.pqnfvt)


Resolve Ecoregions:

[https://data-gis.unep-wcmc.org/portal/home/item.html?id=0127920779a64e3f98925f2d3da3b847](https://data-gis.unep-wcmc.org/portal/home/item.html?id=0127920779a64e3f98925f2d3da3b847)
[https://doi.org/10.1093/biosci/bix014](https://doi.org/10.1093/biosci/bix014)
