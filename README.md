# Covid19 Spread in US counties Project

In this project the aim is to analyze the daily new cases of covid 19 disease for US counties using methods like SVD, DMD, and SHRED. The analysis is based on COVID-19 case data for US counties from January 22, 2020, to March 9, 2023.

## Dataset Overview

For this purpose, the covid data for US counties (*time_series_covid19_confirmed_US.csv*) were downloaded. This data includes new disease cases daily from 2020-01-22 until 2023-03-09 for all US counties. 

In order to make reliable analysis, these numbers should be normalized based on the population of each county. Therefore, the population data for four years from 2020 to 2023 were dowloaded (*coest2023pop.xlsx*). 

The above mentioned data and related processes are available in *USdailyCovid.ipynb* notebook.

## Transition to Spatial Analysis

Then this normalized daily data of new covid incidences on county level were used to make thematic maps of US. The idea is to make these maps raster images with pixel resolution of 10 km to covert the discrete data to a more countinous nature. This is done because a previous attempt to apply SVD and DMD on discrete Covid19 data was unsuccessful and did not produce suitable results. By creating images we can try to extract spatial dynamics of disease spread. 

Therefore, the map of us counties were dowload (*cb_2018_us_county_500k/cb_2018_us_county_500k.shp*) and merged with the covid data to make daily images of the US. This process is carried out inside *UScovidSVD.ipynb* notebook. The resulting raster files have a size of (310, 586) and 1143 raster were created for the days in data range.

## Analysis Methods

After creating the rasters, they were stacked for futher analysis. Different methods that were presented in the class are applied to this data. In the *UScovid19SVD.ipynb* notebook, results of SVD, DMD, BOPDMD, SINDy, and SHRED are shown.

## Visualizing the Spread

The *us_daily_covid19_animation.gif* file is the animation of the 1143 rasters each showing the daily spread of the covid19 virus across US counties. By visual inspection of this animation, the spatial components derived from SVD are verified.
