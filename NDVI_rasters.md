---
layout: default
title: NDVI Recovery after the Las Conchas Fire
---

# NDVI Recovery after the Las Conchas Fire

<a title="Larry1732, CC BY 2.0 &lt;https://creativecommons.org/licenses/by/2.0&gt;, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:View_from_Window_-_Las_Conchas_Fire.jpg"><img width="600" alt="View from Window - Las Conchas Fire" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/View_from_Window_-_Las_Conchas_Fire.jpg/512px-View_from_Window_-_Las_Conchas_Fire.jpg?20110708193432"></a>

For this project, I investigated how vegetation health, shown using (NDVI) recovered after a major forest fire in New Mexico. The Las Conchas fire, which took place in 2011, burned over 150,000 acres near Los Alamos, New Mexico. It was the largest fire on record at the time, and threatened the Los Alamos National Laboratory. I experienced this fire while I was in high school roughly 50 miles southeast in Santa Fe, New Mexico. It was intense to watch - I remember seeing the red glow of fire in the mountains at night, and we would often wake up to ash particles scattered across the hood of our car.


# Background

Fire is not new to the southwest, and it is often an important part of forest cycles. However, as the southwest warms and experiences increased incidence of fires [(Mueller et al. 2020)](https://doi.org/10.1016/j.foreco.2019.117861), we may see major ecosystem shifts or changes in the wake of a fire, as suggested by various researchers such as [Rother and Veblen 2016](https://doi.org/10.1002/ecs2.1594). Indeed, the mountains around Los Alamos look markedly different, even 10 or 15 years after the fire. Given this, I was curious to see how vegetation recovered in the area burned by the Las Conchas fire in the years after the fire.


# MTBS Fire Boundary

To explore this question, I used data from the [Monitoring Burn Severity (MTBS) group](https://www.mtbs.gov/) and NDVI data I acquired from the NASA EarthData repository. I first downloaded the boundary of the Las Conchas fire from MTBS. This gave me a geospatial polygon that I could use to select specific grid cells in the NDVI data. The plot below shows the extent of the fire:

<embed type="text/html" src="./projects/NDVI/Las_Conchas_fire_bound.html" width="900" height="1100">


# NDVI Rasters

Using the fire boundary from MTBS, I downloaded NDVI rasters from NASA Appeears, utilizing an api that will (hopefully) be released sometime soon. The api allows the user to input a boundary as part of their query, which makes it really easy to download the exact area of interest. I utilized data from the MODIS project, with a resolution of 250 meters and a 16-day flyover frequency. I downloaded data between the years 2006 and 2011 (5 years before the fire to 10 years after the fire) and between April 1 and September 30. The month range was intended to be representative of the growing season in New Mexico, though it is somewhat arbitrary and based on my anecdotal experience.

# Methods

To investigate how vegetation health recovered after the fire, I first divided the NDVI dataset into two groups: inside the fire boundary, and outside the fire boundary. I then found the annual mean for NDVI inside and outside the boundary, and plotted those two lines to see how NDVI had changed on an annual basis. I also subtracted the outside annual mean NDVI from the inside annual mean NDVI to just visualize the difference. In addition, I created a sequence of plots that show how NDVI changed spatially from a 2006-2010 baseline to each successive year.

# Results

<embed type="text/html" src="./projects/NDVI/Mean_NDVI_In_Out_Fire.html" width="600" height="500">
This plot shows annual mean NDVI inside (red) and outside (blue) the fire boundary. NDVI inside the boundary is higher than outside for the first five years (2006-2010) in the dataset, but quickly plunges below NDVI outside the fire boundary in 2011. This shows the immediate impact of the Las Conchas fire. In subsequent years after the fire, NDVI inside the fire boundary recovers to levels near NDVI outside the boundary. By 2018, the two regions are nearly identical. However, NDVI inside the boundary never returns to pre-fire levels.


<embed type="text/html" src="./projects/NDVI/NDVI_Mean_Diff_line.html" width="600" height="500">
This plot shows the difference between NDVI inside and outside the fire boundary. The patterns are largely identical to the previous plot, but attention to the scale reveals how closely the two match; the difference in NDVI approaches 0 by 2018. 2012 shows the largest difference, as this is the year immediately after the fire.


<embed type="text/html" src="./projects/NDVI/NDVI_Recovery.html" width="900" height="1100">
If you have trouble viewing the plot due to screen size, feel free to 
[check it out on a separate page here.](projects/NDVI/NDVI_Recovery_big_frame.html)


This plot (or series of plots) reveals clear spatial changes in NDVI within the fire boundary. In the 2006-2010 baseline period, nearly all of the area inside the fire boundary has high NDVI, demonstrated by the dark green coloring of the plot. In 2011, most of the area inside the boundary has low NDVI, as the fire burned. In following years, NDVI in parts of the burned area climbs within 3-4 years. There is a distinct swath from the southwest corner of the burned area through the center of the area that clearly recovers quickly. However, there are also notable areas that do not see major increases in NDVI, such as the north-central and southeast sections of the burned area. Even by 2021, these areas do not seem to recover much. 


# Implications of plots

<embed type="text/html" src="./projects/NDVI/Las_Conchas_fire_bound_no_alpha.html" width="500" height="750">
This map shows the boundary of the Las Conchas fire again. Feel free to zoom or pan in and out as you compare this map to the spatial map of NDVI recovery. Do you notice any characteristics of areas that didn't see much recovery in NDVI?

My results indicate that while vegetation in some parts of the area burned by the Las Conchas fire did recover to some extent, vegetation across the area did not recover to previous levels. This indicates that either the areas burned are experiencing some kind of ecosystem shift, perhaps from common paradigms such as Douglas Fir-Aspen to Ponderosa Pine-Gamble Oak forests, or even Piñon-Juniper forests, or that recovery from fires akin to the Las Conchas fire may take longer than the dataset I used can show. (source here)?

Further, vegetation in some areas did not seem to recover much at all, which is interesting. This could be a result from fires burning intensely and creating inhospitable areas, or the areas could be experiencing an ecosystem shift as the climate warms. I find the southeast corner of the fire near Bandelier National Monument most interesting. In the baseline period, this area seems similar to the rest of the burned region with relatively high NDVI; by 2021, it more closely resembles the areas to the west, which, from personal experience, are lower and more desert-like. This matches results from Rother and Veblen 2016, who found that "conifer regeneration was most limited in xeric settings, including more southerly aspects and elevations closer to lower treeline"; this perfectly describes the area we see most limited recovery from.

Indeed, my step-parent, who likes to hike in this area, describes an area that used to be full of Ponderosa pines as a "wasteland". Pictures from their hikes are included below to offer additional context. To me, this region seems to exemplify a change in ecosystem after a fire, and I hypothesize that climate may have a role in this. 


# Sources

To see the Jupyter notebooks I used to perform this analysis, please check out the following links:

[notebook to download data](projects/NDVI/las-conchas-download.html)

[notebook to wrangle rasters](projects/NDVI/las-conchas-plot.html)

[notebook to visualize NDVI data](projects/NDVI/las-conchas-visualize.html)


I downloaded the fire boundary data from MTBS using [this portal.](https://www.mtbs.gov/direct-download)

The NASA EarthDATA Appeears repository can be found at [this link.](https://appeears.earthdatacloud.nasa.gov/)
