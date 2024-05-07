# BSOL Disability Mapping using ONS Census 2021 Data
Access the dashbord via this link: [Dashboard](https://birmingham-and-solihull-ics.github.io/BSOL_Disability_Mapping/)

## Overview

This repository contains code to create Leaflet maps showing the proportion of people living with disabilities in the BSOL footprints. The maps are displayed on a Quarto dashboard. 

## Dataset

The dataset provides Census 2021 estimates that classify usual residents in England and Wales by long-term health problems or disabilities. The estimates are as at Census Day, 21 March 2021.

Link to dataset: [ONS Disability Data](https://www.ons.gov.uk/datasets/TS038/editions/2021/versions/3/filter-outputs/fe325de6-3443-47bf-be8d-3dcff4871406#get-data)

Link to LSOA Lookup: [LSOA 21 to Ward 22 to LAD 22 Lookup](https://www.data.gov.uk/dataset/19a01ab0-2111-4c29-8a89-a6dd14ba845c/lsoa-2021-to-electoral-ward-2022-to-lad-2022-best-fit-lookup-in-ew-v3)

## Quarto Markdown Files

* **index.qmd**: The main markdown file saved in docs folder

## Methodology

**Data Preparation**

1. Enrich the data by joining the main dataset with the LSOA lookup to include information on Ward 22 and LAD 22.
2. Filter the data to include only Local Authority Districts (LADs) within the Birmingham and Solihull footprints.
3. Calculate the denominator by grouping the data by LSOA code and summing the "Observation" column.
4. Optionally, combine the Disability Categories 1 and 2 into a single category.
5. Calculate the proportion as: (Observation/Denominator)×100
6. Create a total of three datasets, one for each respective disability category map.

**Create Heatmap**

1. Load the datasets and save them as '.rds' files for reusability in Quarto.
2. Load the LSOA shapefile.
3. Transform the shapefile from OSGB36 (British National Grid or BNG) to CRS 4326 (World Geodetic System 1984 or WGS 84).
4. Perform an inner join between each dataset and the LSOA shapefile based on the LSOA code.
5. Define the color palette for the heatmap.
6. Create a Leaflet map to visualize the data.

## Environment Details

* **RStudio**: RStudio 2022.07.2+576 

* **Quarto**: 1.4.514

This repository is dual licensed under the [Open Government v3]([https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) & MIT. All code can outputs are subject to Crown Copyright.
