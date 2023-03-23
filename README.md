![](https://www.vera.org/dist/img/logo_full.svg)

# ICE Detention Trends Dataset
Data showing daily facility level populations across all known ICE detention facilities
from October 1, 2008 to March 30, 2020. The underlying data were acquired through FOIA
requests with IDs 2017-ICFO-34275 and 2019-ICFO-10844 and were both made available to
Vera by David Hausman. Further processing of this underlying data enables
aggregating the number of unique people detained by ICE to the daily level.

This dataset also includes facility information produced by aggregating data from The
Marshall Project, The National Immigrant Justice Center, datasets acquired though FOIA
that have been made publicly available, the ICE detention stats spreadsheet on the web,
the ICE dedicated/non-dedicated facilities spreadsheet and web-scraped public data.

For more details on how we counted the number of people detained by ICE and
aggregated facility metadata, please see the accompanying ICE Detention Trends
Technical Appendix: <!-- TODO: Link here -->.

Additionally, this work relies on the creation of a `detention_stay_id` to
enable us to count the number of unique people detained over a given timeframe
(i.e. each day). For more details on this work, please see the accompanying
whitepaper: <!-- TODO: Link person_id whitepaper -->.

Vera's dashboard visualizing this data is available here: <!-- TODO: Fill in link -->.

# Data Dictionaries
In this dataset, we include information on:
1. The number of unique people detained each day and over midnight by ICE at a daily facility level
1. The number of unique people detained each day and over midnight by ICE at a daily national level
1. The number of national book-in and book-out events daily
1. Name, location and type information for facilities used by ICE to detain people

The directory tree below outlines the organization, followed by data dictionaries for
each data file:

```
ice-detention-trends/
    |-- README.md
    |-- License.md
    |-- national.csv
    |-- faciltiy/
    |   |-- FY2009.csv
    |   |-- FY2010.csv
    |   |-- FY2011.csv
    |   |-- FY2012.csv
    |   |-- FY2013.csv
    |   |-- FY2014.csv
    |   |-- FY2015.csv
    |   |-- FY2016.csv
    |   |-- FY2017.csv
    |   |-- FY2018.csv
    |   |-- FY2019.csv
    |   `-- FY2020.csv
    `-- metadata/
        `-- facilities.csv
```


## `national.csv`
National counts which includes the number of people detained each day as well as the
number of book-in and book-outs.
| Variable                | Type        | Description                                                                              |
| ----------------------- | ----------- | --------------------------------------------------------------------- |
| date                    | `timestamp` | The day each count is reported for (`yyyy-mm-dd` format)              |
| pop_24h                 | `numeric`   | The number of unique people detained on each day of the month         |
| pop                     | `numeric`   | The number of unique people detained over each midnight of the month  |
| book_in                 | `numeric`   | The number of people booked into ICE's detention network              |
| book_out                | `numeric`   | The number of people booked out of ICE's detention network            |


## `faciltiy/`
### `FY20XX.csv`
Daily population counts at the facility level:
| Variable                | Type        | Description                                                                    |
| ----------------------- | ----------- | ------------------------------------------------------------------------------ |
| detention_facility_code | `string`    | ICE facility level unique identifier, i.e. Detention Location Code (detloc)    |
| date                    | `timestamp` | The day each count is reported for (`yyyy-mm-dd` format)                       |
| pop_24h                 | `numeric`   | The number of unique people detained on the given day                          |
| pop                     | `numeric`   | The number of unique people detained over midnight (i.e. measured at 11:59pm)  |

Note that the first 30 days have Null values for the 30-day moving average counts
because not enough time has passed to compute the average.


## `metadata/`
### `facilities.csv`
A lookup table mapping each Detention Location Code to information about the facility:

| Variable                | Type      | Description                                                                                |
| ----------------------- | --------- | ------------------------------------------------------------------------------------------ |
| detention_facility_code | `string`  | ICE facility level unique identifier, i.e. Detention Location Code (detloc)                |
| type_detailed           | `string`  | ICE provided facility type. For more details on mapping, see <!-- TODO: link mapping -->   |
| latitude                | `numeric` | The physical location of the facility                                                      |
| longitude               | `numeric` | The physical location of the facility                                                      |
| state                   | `string`  | The census state code, this includes codes for US teritories (e.g. "PR" for "Puerto Rico") |
| detention_facility_name | `string`  | The name of the facility as seen in FOIA 2017-ICFO-34275 and FOIA 2019-ICFO-10844          |


# License
By downloading the data, you hereby agree to all the terms specified in this license: [License.md](License.md).


# Contributors
<!-- TODO -->
