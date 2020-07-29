# SQL Capstone

## Overview

This capstone project is built around using SQL to explore a data set describing phasor measurement unit (PMU) electrical usage data.

## Development

Phasor measurement units record electrical supply and usage characteristics at the end user, such as frequency, voltage, and amperage.  You have available (in the database file [`pmu.db`](./pmu.db) readings taken between 1:46 p.m. on April 21, 2014, and 7:20 a.m. on April 22, 2014.  Since the device is sampling ten times a second, there are 632,540 time samples with 30–46 recorded values at each time step.

Each data measurement has a tag describing its date and time (the record or row) and its `LOCATION:TYPE` along with a quality tag.  The types are as follows:

- `F`, frequency in Hz
- `DF`, rate of change of frequency
- `S`, should be 0 (otherwise, you can ignore this field)
- `UTKV`, voltage (should be near 110–120 V)
- `UTKVH`, phase (should be in the range -180–+180)

A quality tag reports on how good the data are considered by the device, and this should generally be `GOOD`.

## Progress & Completion

You should fork this project.  We expect you to work on a copy of the database and produce a short report.

First, you should analyze the data set and determine the range and behavior of values.  For operations, you can cast `VARCHAR` or `TEXT` fields to a more appropriate type, for dates/times or numeric values (`REAL` or `INTEGER`).  For each numeric field, what is the actual range, mean, median, and standard deviation?  For each text field, what are the possible values?

You should check for any:

- missing data
- misaligned data, which may show up as values outside of the expected range or of the wrong type.  For instance, the frequency should always be near 60 Hz, and the voltage near 110–120 V; the phase should be -180–+180 degrees
- bad data (you should exclude data which are not `GOOD`)

Bad data should not be corrected, but should simply be removed from the record (*i.e.*, you can remove the entire record for that time step or fill in blanks for the bad data.  Some PMUs recorded data at a different interval from the others, though, and these data are not invalid.  (Examine the `TSV` file to see what this means.)

You should summarize the devices involved (such as `OWER`), and the data collected from each device.

You should report on aggregate data as well:  median value and range per hour and per week.

Finally, export the data and produce plots of the data.  You can use any tool to plot the data after you extract the data using SQL.  You should be able to output the appropriate fields from your database by reasoning analogically from this snippet of code (which is based on a different database):

```sql
.headers on
.mode csv
.output data.csv
SELECT customerid,
       firstname,
       lastname,
       company
FROM customers;
```

Your report should briefly describe each of these steps, summarize the data in an accessible format, and include an appendix with the necessary SQL code.
