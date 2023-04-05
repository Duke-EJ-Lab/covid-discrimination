# How to use this repo
This is the base starting point for all EJ Lab projects. Starting all projects from this file structure gives a framework that helps make our data and code more uniform, helping with reproducibility and keeping institutional knowledge as students join and leave projects.

To get more in depth info on the lab, procesess, the tech stacks we use and how to get set up visit the [EJ orientation guide repo](). 

As you go on you'll fill in parts of the generalized documentation below. Wherever you need to fill something in we've used the key **XXXX** to signify it. 

## Repo overall structure

The starting repo structure looks like this. 

```
repo
 ├── code
 │	 ├── 00_functions.R 
 │	 ├── 01_clean_data.R 
 │	 ├── eda
 │	 │	 └──yy_mm_dd_goal.R
 │	 └── supplemental
 │	 	 	 └── create_simplified_data.R
 └── figures
  	 ├── raw
  	 └── final
```
Main analysis files that would need to be run to reproduce the results should be stored directly in the `code` folder, numbered in order. 

The starting `00_functions.R` file is a base file that every other file will reference in order to read in libraries, define functions that are commonly used across the analysis, and define the paths to the github and data. The second file `01_clean_data` is just a starting point that shows how to read in the first file using `source(code/00_functions.R)` - rename, change, or delete at your hearts content.

Code that you test out but isn't necessary for reproduction should be stored in the `code/eda` (exploratory data analysis - EDA) folder, titled by date and what the code is investigating. The file in the repo gives an example for what the header can include. Saving your exploratory work can be really helpful down the line so you can remember what you've tried, and people new to the project can learn about what's been done so far.

Figures directly output from your code should be saved in the `code/figures/raw` folder. The final figures for the paper, dashboard, or other final product go in the `code/figures/final` folder. 

## Code + Repo Formatting 

### Commenting

Every code file should start with something that looks like this and contains:
* the creator
* who else is working/has worked on this file
* when it was last edited
* a one or two sentence description of what the file is trying to do 
* what the output of the file is.

```
########################################################################################
# Created by: Anne Driscoll
# Other contributors: Chris Timmins, Kay Jowers
# Last edited on: 8/31/22
#
# This file creates a cleaned dataset of all US flights that is used throughout 
# the rest of the analysis in this project. 
#
# In the cleaned file each observation is an airport-year, and gives total number of 
# flights, along with taxi time and several delay metrics. 
########################################################################################
```

If the file is tackling more than one task at a time, it helps to break up the sections for readability, so that others can follow what the code is doing. That might look something like this:

```
# Load data --------------------------------------------------------------------

# Filter data to only TX airports ----------------------------------------------

# Plot number of flights over time ---------------------------------------------
```

Blocks of code should include more detailed commenting throughout, so that your collaborators can follow your code without spending too much time looking through the details of your code and the functions you call - reduce the mental load!

### File Naming

Good examples would be `process_pm_data.R`, or `create_figure_2.R`. Bad examples would be `CAFO2trylm.R` or `analysis.R`. 

Most of the work we do will be a bunch of ordered files, and these should be numbered. Using the examples above, they should be named in order - `01_process_pm_data.R` and `02_create_figure_2.R` (assuming no files in between!). These can always be changed if you need to add steps in between!

### Object naming

Variable and function names should be lowercase, and use an underscore to separate words. Try to be concise! Good examples would be `day_one` or `first_day`, bad examples would be `first_day_in_the_data` or `dotm1`.

This is largely lifted from Hadley Wickham's [style guide](http://adv-r.had.co.nz/Style.html). Additional guidance can be found there, but these are the most important parts for us.

## Getting started

**Delete everything before the project title** when the repo is ready to be shared, but the below documentation structure will help make sure your hard work is all documented so people can expand upon it in the future!

# Project Title: **XXXX**

This is a repo supporting the paper: **XXXX**. 

Abstract: ***XXXX*** Write a few sentence abstract on what the project is investigating to orient people to the code here. What data are you using? What is the motivation? What is the hypothesis? Think 30,000 feet for this section.

## Using Results

The code to replicate this project is 

This repo contains all the code needed to replicate the results but none of the data needed due to Data Use Agreements, instead we provide our data structures below so that given access to the same data you'll be able to re-run the analysis. Protected data is used in this project

On our end data is hosted in the institution Box system, but by changing the `data_path` variable in `00_functions.R`, you can point to wherever you host your data. This means as long as you follow the data structure given below, you shouldn't need to change paths throughout the project. 

## Scripts

* 00_functions.R: This file is used to load in packages and define custom functions that are used throughout the analysis. It also defines the file path to our Duke Box data folder and the local location of the github repo, so that when reproducing you can give the head of your data folder, rather than having to change every file path in the project. 
* ***XXXX***

### Supplemental

### EDA - Exploratory Data Analysis

## Issues, Constraints and Choices

## Data

### Necessary data folder structure necessary to reproduce

**XXXX** - This is just an example folder structure, this should be replaced with the folder structure within the Duke Box folder you're using. It is super important to update this when you are wrapping up or passing on a project. 

```
project_folder
 ├── airport
 │	 ├── airport_locations.csv
 │   └── [Month]_[Year]_ontime.csv (for Jan-Dec 2006-2018)
 ├── boundaries
 │   ├── GACC
 │   │	 └── National_GACC_Current_20200226.shp (and associated dbf, prj) 
 │	 └── state_fips_codes.csv
 ├── pm
 │ 	 └── epa_station_level_pm25_data.rds
 └── powerplants
  	 ├── Plant_Y[Year].xls (2006 - 2010)
  	 ├── Plant_Y[Year].xlsx (2011 -  2018)
  	 ├── overview_[Year].csv (2006 - 2018)
  	 └── emissions_[Year].csv  (2006 - 2018)
```

### Data sources

**XXXX** - this is an example that matches the above data structure. We have a simple description of what the data is, when it was downloaded, and a direct link that people can follow to find the data. 

* data/airport: Airport data come from [here](https://www.transtats.bts.gov/ONTIME/) including airport locations, quarterly ticketing, and monthly on-time status. Data was downloaded 10/10/2021.

* data/boundaries/GACC: The [GACC boundaries](https://hub.arcgis.com/datasets/nifc::national-gacc-boundaries) can be downloaded [here](https://opendata.arcgis.com/datasets/7dc5f4a286bd47e0aaafa0ab05302fe9_0.gdb). Data was downloaded 7/18/2021.

* data/pm: Raw data come from the [EPA download portal](https://www.epa.gov/outdoor-air-quality-data/download-daily-data) and are slightly processed to create the file linked above using the script `code/supplemental/create_simplified_epa_data.R` in case you would like to update the data in the future. 

* data/powerplants/overview_[YYYY].csv: same process for emissions data above starting from [here](https://www.eia.gov/beta/electricity/data/browser/#/topic/1?agg=2,0,1&fuel=vtvv&sec=g&geo=g&freq=A&datecode=2006&tab=overview&start=200101&end=201710). 


# Packages needed

**XXXX** 

## sessionInfo()

**XXXX** Just copy and paste the output from when you run sessionInfo() here!

```
R version 3.6.1 (2019-07-05)
Platform: x86_64-apple-darwin15.6.0 (64-bit)
Running under: macOS Mojave 10.14.2

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib
LAPACK: /Library/Frameworks/R.framework/Versions/3.6/Resources/lib/libRlapack.dylib

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

attached base packages:
[1] splines   datasets  stats     graphics  grDevices utils     methods   base     

other attached packages:
 [1] RSelenium_1.7.5   BAMMtools_2.1.7   ape_5.3           Hmisc_4.3-0       ggplot2_3.3.2     Formula_1.2-3     survival_3.1-8   
 [8] lattice_0.20-38   imputeTS_3.0      signal_0.7-6      openxlsx_4.1.4    velox_0.2.0       gdata_2.18.0      raster_3.3-13    
[15] readr_1.3.1       stringr_1.4.0     tidyr_1.1.2       dplyr_1.0.2       ncdf4_1.17        geosphere_1.5-10  rgdal_1.5-18     
[22] rgeos_0.5-2       sp_1.4-4          sf_0.8-0          data.table_1.13.2

loaded via a namespace (and not attached):
  [1] backports_1.2.0     plyr_1.8.5          usethis_1.5.1       digest_0.6.27       htmltools_0.4.0     fansi_0.4.1        
  [7] magrittr_1.5        checkmate_1.9.4     memoise_1.1.0       cluster_2.1.0       remotes_2.1.0       xts_0.11-2         
 [13] askpass_1.1         forecast_8.10       tseries_0.10-47     prettyunits_1.1.1   colorspace_1.4-1    rvest_0.3.5        
 [19] pan_1.6             xfun_0.11           callr_3.5.1         crayon_1.3.4        jsonlite_1.7.1      lme4_1.1-25        
 [25] zoo_1.8-6           glue_1.4.2          gtable_0.3.0        pkgbuild_1.1.0      weights_1.0         semver_0.2.0       
 [31] quantmod_0.4-15     jomo_2.6-10         scales_1.1.1        stinepack_1.4       DBI_1.1.0           ggthemes_4.2.0     
 [37] Rcpp_1.0.5          htmlTable_1.13.3    units_0.6-5         foreign_0.8-72      htmlwidgets_1.5.1   httr_1.4.1         
 [43] gplots_3.0.1.1      RColorBrewer_1.1-2  acepack_1.4.1       ellipsis_0.3.1      mice_3.6.0          pkgconfig_2.0.3    
 [49] XML_3.98-1.20       nnet_7.3-12         tidyselect_1.1.0    rlang_0.4.8         munsell_0.5.0       tools_3.6.1        
 [55] cli_2.1.0           generics_0.1.0      audio_0.1-7         devtools_2.2.1      broom_0.7.2         yaml_2.2.0         
 [61] binman_0.1.1        processx_3.4.4      knitr_1.26          fs_1.3.1            zip_2.0.4           caTools_1.17.1.3   
 [67] purrr_0.3.4         mitml_0.3-7         nlme_3.1-142        xml2_1.2.2          compiler_3.6.1      rstudioapi_0.11    
 [73] curl_4.3            e1071_1.7-3         testthat_3.0.0      tibble_3.0.4        statmod_1.4.35      stringi_1.5.3      
 [79] ps_1.4.0            desc_1.2.0          Matrix_1.2-18       classInt_0.4-2      nloptr_1.2.2.2      urca_1.3-0         
 [85] vctrs_0.3.4         pillar_1.4.6        lifecycle_0.2.0     lmtest_0.9-37       bitops_1.0-6        wdman_0.2.4        
 [91] R6_2.5.0            latticeExtra_0.6-28 KernSmooth_2.23-16  gridExtra_2.3       sessioninfo_1.1.1   codetools_0.2-16   
 [97] boot_1.3-23         MASS_7.3-51.4       gtools_3.8.1        assertthat_0.2.1    pkgload_1.1.0       openssl_1.4.1      
[103] rprojroot_1.3-2     withr_2.3.0         fracdiff_1.5-1      parallel_3.6.1      hms_0.5.2           quadprog_1.5-8     
[109] grid_3.6.1          rpart_4.1-15        timeDate_3043.102   class_7.3-15        minqa_1.2.4         TTR_0.23-5         
[115] base64enc_0.1-3 
```
