# QOL Variables Aggregation and Analysis

This repository contains a suite of Python classes using the ArcPy library to perform spatial data aggregation and analysis for Quality of Life (QOL) variables as part of the Urban Institute's projects. The provided classes allow for proximity analysis, voter participation analysis, impervious surface analysis, and general aggregation of spatial data.


## Introduction

This repository is designed to support the Urban Institute's analysis of various QOL variables through spatial data processing using ArcPy. The custome libraries allow for sophisticated spatial joins, proximity analyses, summary statistics, and the ability to export results to CSV files.

## Classes and Methods

### Aggregate

The `Aggregate` class executes aggregation of point feature classes within polygon features, such as neighborhoods or other administrative boundaries.

**Methods:**
- `withinNPA(NPA, AggregateFeature, OutputName)`: Aggregates point features completely contained within a polygon.
- `withNPAID(InFeature, NPA, OutputName)`: Assigns NPA IDs to point features within a polygon.

### Proximity

The `Proximity` class performs proximity analysis to determine distances between tax parcels and proximity feature classes (e.g., parks, schools).

**Methods:**
- `__init__(TaxParcelFeatureClass, ProximityFeatureClass, OutputForProximityAnalysis)`: Initializes the class with the necessary feature classes.
- `merge(*FeatureClassesToBeMerged)`: Merges multiple feature classes for proximity analysis.
- `addfield(NewFieldName)`: Adds a new field to the feature class.
- `nearanalysis()`: Computes the distance between tax parcels and proximity features, and identifies residential parcels within a specified distance.
- `summarize(NearResidentialOutputTable, HousingUnitsTable, Geodatabase)`: Summarizes residential units near the proximity features.
- `exportcsv(OutputDirectory, FinalCSVName)`: Exports the summary results to a CSV file.

### Voters

The `Voters` class analyzes voter participation by spatially joining geocoded voter data with neighborhood polygons and summarizing voter activity.

**Methods:**
- `__init__(voterparticipation, NPA, SummaryTableName)`: Initializes the class with voter participation data and NPA features.
- `spatialjoin()`: Executes a spatial join to assign NPA IDs to voters.
- `summary(*FieldsToBeSummarized)`: Summarizes the total and active voters within each NPA.
- `export(OutputDirectory, FinalCSVName)`: Exports the summarized voter data to a CSV file.

### Impervious

The `Impervious` class analyzes impervious surfaces by performing union and intersect operations on residential and commercial land use features, and summarizing the impervious surface area within NPAs.

**Methods:**
- `__init__(residential, commercial, UnionOutputname)`: Initializes the class with residential and commercial land use features.
- `union()`: Performs a union operation on the residential and commercial feature classes.
- `dissolve()`: Dissolves the unioned feature class to prepare for further analysis.
- `intersect(NPAFeatureclass, IntersectOutput)`: Intersects the dissolved features with NPAs and calculates the impervious surface area.
- `exportcsv(OutputDirectory, Filename)`: Exports the impervious surface summary to a CSV file.

## Setup and Dependencies

### Prerequisites
- ArcGIS Pro with ArcPy installed
- Python 3.x
- Pandas library for data manipulation
- Basic understanding of GIS concepts and spatial data

### Installation
1. Clone this repository:
   ```sh
   git clone https://github.com/yourusername/QOL-Aggregation-Analysis.git
   ```
2. Navigate to the project directory:
   ```sh
   cd QOL-Aggregation-Analysis
   ```
3. Ensure you have the necessary Python libraries installed:
   ```sh
   pip install pandas numpy
   ```

## Usage

1. **Initialize and use the classes**: Import the required classes from the script and create instances for your data analysis.
2. **Run methods**: Use the provided methods to perform spatial joins, proximity analysis, summarization, and export results.
3. **Export results**: Export the final outputs to CSV files for further analysis or reporting.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This repository aims to provide a comprehensive toolkit for spatial data analysis in urban environments, aiding in the evaluation and enhancement of Quality of Life metrics. If you have any questions or need further assistance, please feel free to reach out.
