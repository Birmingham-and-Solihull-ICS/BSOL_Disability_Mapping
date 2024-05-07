# BSOL Disability Mapping using ONS Census 2021 Data
Access the dashbord via this link: [Dashboard] (https://birmingham-and-solihull-ics.github.io/BSOL_Disability_Mapping/)

## Overview

This repository contains codes to create Leaflet maps showing the proportion of people living with disabilities in the BSOL footprints. The maps are displayed as a Quarto dashboard. 

## Dataset

The dataset provides Census 2021 estimates that classify usual residents in England and Wales by long-term health problems or disabilities. The estimates are as at Census Day, 21 March 2021.

Link to dataset: [ONS Disability Data] (https://www.ons.gov.uk/datasets/TS038/editions/2021/versions/3/filter-outputs/fe325de6-3443-47bf-be8d-3dcff4871406#get-data)

Link to LSOA Lookup: [LSOA 21 to Ward 22 to LAD 22 Lookup] (https://www.data.gov.uk/dataset/19a01ab0-2111-4c29-8a89-a6dd14ba845c/lsoa-2021-to-electoral-ward-2022-to-lad-2022-best-fit-lookup-in-ew-v3)

## Quarto Markdown Files

* **index.qmd**: The main markdown file saved in docs folder

## Methodology

**Data Preparation**

1. Enrich the data with Ward 22 and LAD 22 by joining the main data with the LSOA lookup
2. Limit the data to LADs in Birmingham and Solihull footprints
3. Calculate the denominator by grouping the data by LSOA code and summing up the Observation
4. Combine the Disability Categories 1 & 2 (optional)
5. Calculate the Proportion: (Observation / Denominator) * 100
6. Create 3 datasets in total, each for respective map for disability categories

**Create Heatmap**

1. Load datasets and save them as 'rds' files (for reusability in Quarto)
2. Load LSOA shapefile
3. Transform the shapefile from OSGB36 (British National Grid or BNG) to CRS 4326 (World Geodetic System 1984 or WGS 84)
4. Inner join each dataset with the LSOA shapefile based on the LSOA code
5. Define colour palette for the heatmap
6. Create a Leaflet map

## Environment Details

* **RStudio**: RStudio 2022.07.2+576 "Spotted Wakerobin" Release (e7373ef832b49b2a9b88162cfe7eac5f22c40b34, 2022-09-06) for Windows
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.8 Chrome/69.0.3497.128 Safari/537.36

* **Quarto**: 1.4.514

This repository is dual licensed under the [Open Government v3]([https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/) & MIT. All code can outputs are subject to Crown Copyright.
