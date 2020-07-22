# SQL Capstone

## Overview

This capstone project is built around using SQL to clean and modify a data set describing phasor measurement unit (PMU) electrical usage data.

## Development

Phasor measurement units record electrical supply and usage characteristics at the end user, such as frequency, voltage, and amperage.  You have available in the compressed file `pmu-data.tar.gz` a collection of CSV files which contain readings taken between 1:46 p.m. on April 21, 2014, and 7:20 a.m. on April 22, 2014.  Since the device is sampling ten times a second, there are 632,540 time samples with 30–46 recorded values at each time step.

-    [`pmu-data.tar.gz`](repo:./resources/pmu-data.tar.gz)

You first need to load the CSV files into the database as a single database.

Next, you have been asked to clean the data prior to an analysis of the system response to external factors such as weather or propagating grid load changes.  The data are fairly messy however, and may contain invalidating features such as:

- missing data, which may show up as an incorrect number of columns.
- misaligned data, which may show up as values outside of the expected range or of the wrong type.  For instance, the frequency should always be near 60 Hz, and the voltage near 120 V.  Feel free to suggest or attempt to apply other criteria as appropriate (such as that strings should read `"Good"` instead of other values).

Your solution should check for missing data and for misaligned data.  This will mean establishing the normal limits of the field.  (For instance, the phase cannot go beyond $-180$ to $180$ degrees.)

Bad data should not be corrected, but should simply be removed from the record (*i.e.*, you can remove the entire record for that time step or fill in blanks for the bad data.  Some PMUs recorded data at a different interval from the others, though, and these data are not invalid.  (Examine the files to see what this means.)

Compose a SQL script to process the data into a clean database.  Your script should load each file, filter out bad data according to the criteria given above, and export a cleaned-up version in a _single_ database file.  (You do not need to submit the cleaned database, as the script should be able to produce it on demand given the CSV files in the same directory.)

## Progress & Completion

You should fork this project and work exclusively in the `sql/` folder.  We expect you to compose one script:

- `pmu-clean.sql` as described above.


First, you should analyze the data set and determine the range and behavior of values.  For each numeric field, what is the actual range, mean, median, and standard deviation?  For each text field, what are the possible values?




