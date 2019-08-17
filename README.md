# Interbay-Giving-Garden
Historic donation records for the Interbay Giving Garden, Seattle, WA. 

## Raw Data
Interbay Giving Garden leadership kept records of produce harvested by kind and weight in pounds. This data was available in .xls format for years 2009-14, and in paper format for 2017-18. Records for 2015-16 are unavailable.

- Date : datetime, date of harvest/donation
- Produce : string, categorical, type of produce harvested/donated
- Weight (Lbs.) : float [##.#], recorded weight in pounds for the given produce
- Running Total : float [##.#], cumulative weight in pounds

Paper records were entered manually into Google sheets, saved as .csv, and treated the same as the existing Excel data.

## Cleansing
The Excel data was in good shape, no corruption or null values, dates were in a good date format, produce names were standardized with minimal duplication. The only issue of note was the 2010 data incorrectly showed 2011 as the year in the date column, which was corrected in the script. The Running Total column was dropped as it can be calculated on the fly. Simplified column names.

## Blending
Created a separate Produce Map file to translate duplicate values and combine others into broader groups. I found a spreadsheet with lots of nutritional data by food item (https://tools.myfooddata.com/nutrition-facts-database-spreadsheet.php) and added the id field to this map as well. This way we can pull in  calorie and other nutritional data


