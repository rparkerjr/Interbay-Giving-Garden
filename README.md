# Interbay-Giving-Garden
Historic donation records for the Interbay Giving Garden, Seattle, WA. Data is collected and reported to the City of Seattle(???) who are primarily interested in poundage donated. All other metrics and analyses are for the interest of the Giving Garden leadership team, individual donors, and volunteers.

## Raw Data
Interbay Giving Garden leadership kept records of produce harvested by kind and weight in pounds; data was tracked for the Giving Garden plots as well as individual donations. This data was available in .xls format for years 2009-14, and in paper format for 2017-20. Records for 2015-16 are unavailable and for some reason 2019 is incomplete. 

All data is self-reported and until 2020 weighing was done plastic bins and an analog scale. Weights were rounded to the nearest half pound, recorded in a paper log, and transferred to Excel at a later date. The data is subject to possible issues such as improper tare weight; human error in reading, rounding, or recording values; and other clerical mistakes. In mid-2020 a new digital scale was procured and weights began being recorded to the nearest tenth of a pound which should lead to better overall accuracy.

Excel files were manually converted to .csv and column names standardized as follows:

- date : date, date of harvest/donation
- produce : string, categorical, type of produce harvested/donated
- gardener : string, donating party (Individual data only)
- weight : float [##.#], recorded weight in pounds for the given produce

## Cleansing and Blending
The Excel data was in good shape with no corruption and few null values, dates were converted to ISO format 'YYYY-MM-DD'. I manually converted Excel to csv, removed formatting and a running total column. To the Giving Garden data I added a 'gardener' column, populated it with 'Giving Garden', and combined it with the individual donation data.

### Produce Mapping
I created `produce_mapping.csv` to translate some produce names and combine others into broader rollup groups. The initial process was a manual one; I exported the list of unique values from the combined `produce` column, unified various spellings and labels in `prod_name`, created a `generic_name` free from varietal or other minor differentiators, and grouped items together under a much broader `prod_group`.

From this base it may be possible to build some basic regex decision making for automatically finding new entries.

### Year and Week Markers
To simplify slicing and filtering I added `week` and `year` fields. Leadership was interested in viewing the data based on the weekly harvesting schedule rather than on a monthly basis, and seasons are reported at an annual level.

### Giving Garden Flag
Added a `gg` field to indicate whether a record is for the Giving Garden or an Individual.

### Nutrition Data
I found a spreadsheet with lots of nutritional data by food item (https://tools.myfooddata.com/nutrition-facts-database-spreadsheet.php) and would like to add this in the future.

## Output Data
Cleaned .csv output as 'Giving Garden Combined.csv'
- date : ISO formatted date
- produce : string, categorical, type of produce harvested/donated as entered
- gardener : string, categorical, donating party
- weight : float [##.#], recorded weight in pounds for the given produce
- week : integer, ISO week of donation
- year : integer, 4-digit year of donation
- gg : string, categorical, indicates Giving Garden or Individual donation, simplified from gardener
- prod_name : string, cleaned and standardized produce name
- generic_name : string, generic rollup produce name
- prod_group : string, broad rollup category

### Working File
The Jupyter notebook which does a lot of the processing is also available and shows some summary statistics.
