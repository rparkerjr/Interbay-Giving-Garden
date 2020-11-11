# Interbay-Giving-Garden
Historic donation records for the Interbay Giving Garden, Seattle, WA. 

## Raw Data
Interbay Giving Garden leadership kept records of produce harvested by kind and weight in pounds; data was tracked for the Giving Garden plots as well as individual donations. This data was available in .xls format for years 2009-14, and in paper format for 2017-20. Records for 2015-16 are unavailable and for some reason 2019 is incomplete. Excel files were manually converted to .csv and column names standardized as follows:

- date : date, date of harvest/donation
- produce : string, categorical, type of produce harvested/donated
- gardener : string, donating party (Individual data only)
- weight : float [##.#], recorded weight in pounds for the given produce

## Cleansing and Blending
The Excel data was in good shape, no corruption or null values, dates were in a good date format but are converted to ISO format. I manually converted Excel to csv, removing formatting and a running total column. Added a 'gardener' column and populated it with 'Giving Garden' for those records, and combined it with the individual donation data.

Created a separate file (produce_mapping.csv) to translate duplicate values and combine others into broader rollup groups. Also created meta fields such as 'week' and 'year' to help bucket out the data.

### Nutrition Data
I found a spreadsheet with lots of nutritional data by food item (https://tools.myfooddata.com/nutrition-facts-database-spreadsheet.php) and will be adding this in the future.

## Output Data
Cleaned .csv output as 'Giving Garden Combined.csv'
- date : ISO formatted date
- produce : string, categorical, type of produce harvested/donated as entered
- gardener : string, categorical, donating party
- weight : float [##.#], recorded weight in pounds for the given produce
- week : integer, ISO week of donation
- year : integer, 4-digit year of donation
- prod_name : string, cleaned and standardized produce name
- generic_name : string, generic rollup produce name
- prod_group : string, broad rollup category
