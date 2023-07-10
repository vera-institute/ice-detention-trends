![](https://www.vera.org/dist/img/logo_full.svg)

# ICE Detention Trends Data
Vera’s [ICE Detention Trends](http://vera.org/ice-detention-trends) dashboard reveals an unprecedented level of detail about ICE detention populations, both nationally and in the 1,081 facilities in which ICE detained people, on each day between October 1, 2008, and March 30, 2020—fiscal year (FY) 2009 to mid-FY2020.
This repository
includes the aggregated data visualized in the dashboard, including information
on:

- Midnight population: the daily number of people detained at midnight
(nationally and by facility).
- 24-hour population: the number of people detained for any part of a given day,
including those whom ICE transferred or booked-out of custody before midnight
(nationally and by facility). While ICE relies solely on midnight populations in
its reporting, Vera includes both types of daily populations—midnight and
24-hour—as the two can differ drastically.
- Book-ins: the daily number of people ICE booked into custody (nationally).
- Book-outs: the daily number of people ICE booked out of custody (nationally).
- Facility names, locations, and types (as coded by ICE in other datasets).

## About the Data
The dashboard primarily draws from ICE detention datasets released through a
Freedom of Information Act (FOIA) request, shared with Vera by David Hausman,
assistant professor of law, University of California, Berkeley. To overcome
limitations of the original data, Vera developed a novel algorithm to construct
individual detention histories, from a person's initial book-in to their
final-book out, inclusive of any transfers. Doing so allowed Vera to account for
duplicated data and compute detention populations. Vera drew from additional ICE
datasets for information on facility locations and facility types. Otherwise,
Vera chose to present the ICE detention data "as is" to the greatest extent
possible, including any inconsistencies or errors that may be present in the
data compiled and shared by ICE. For more information about the data and Vera's
methodology, see the accompanying [technical
appendix](https://vera.org/ice-detention-trends/files/dashboard_appendix.pdf?).


# Data Dictionaries
The directory tree below outlines the organization of this repository, followed
by data dictionaries for each data file.

```
ice-detention-trends/
    |-- README.md
    |-- License.md
    |-- national.csv
    |-- facility/
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
National population statistics for each day between October 1, 2008, and March 30,
2020, including midnight population, 24-hour population, book-ins, and
book-outs.

| Variable     | Type      | Description                                                                                                                   |
| ------------ | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| date         | `date`    | The date for which each metric is reported (`yyyy-mm-dd` format)                                                              |
| daily_pop    | `numeric` | 24-hour population: the number of people detained at any point during a given day, including those booked out before midnight |
| midnight_pop | `numeric` | Midnight population: the number of people detained at 11:59pm on a given day                                                  |
| book_in      | `numeric` | Book-ins: the number of people booked into ICE custody                                                                        |
| book_out     | `numeric` | Book-outs: the number of people booked out of ICE custody                                                                     |


## `facility/`
### `FY20XX.csv`
Facility-level population statistics for each day between October 1, 2008, and March
30, 2020, including midnight population and 24-hour population.  To make file
sizes more manageable, Vera split the data into separate .csv files by fiscal
year (October 1 of the previous year through September 30 of a given year).
FY2020 is a partial fiscal year covering October 1, 2019, to March 30, 2020.

| Variable                | Type      | Description                                                                                                                   |
| ----------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| detention_facility_code | `string`  | The unique identifier used in the ICE detention data for each facility                                                        |
| date                    | `date`    | The day each count is reported for (`yyyy-mm-dd` format)                                                                      |
| daily_pop               | `numeric` | 24-hour population: the number of people detained at any point during a given day, including those booked out before midnight |
| midnight_pop            | `numeric` | Midnight population: the number of people detained at 11:59pm on a given day                                                  |

## `metadata/`
### `facilities.csv`
A lookup table mapping each detention_facility_code to information about the
facility, drawing from supplemental ICE data and other sources. (See technical
appendix for more detail.)

| Variable                | Type      | Description                                                                                        |
| ----------------------- | --------- | -------------------------------------------------------------------------------------------------- |
| detention_facility_code | `string`  | The unique identifier used in the ICE detention data for each facility                             |
| detention_facility_name | `string`  | The facility name associated with the detention_facility_code in the ICE detention data            |
| type_detailed           | `string`  | The facility type as coded by ICE in supplemental data sources                                     |
| latitude                | `numeric` | The latitude coordinate of the facility location                                                   |
| longitude               | `numeric` | The longitude coordinate of the facility location                                                  |
| city                    | `string`  | The city in which the facility is located                                                          |
| state                   | `string`  | The state abbreviation code. This includes codes for U.S. territories (e.g. "PR" for "Puerto Rico") |

# License
By downloading the data, you hereby agree to all the terms specified in this
license: [License.md](License.md).

# Credits
Data analysis: Noelle Smart and Zachary Lawrence
Data engineering: Zachary Lawrence
Design and development: Jill Hubley
Writing: Noelle Smart
Editing: Léon Digard

# Acknowledgements
Vera thanks [David Hausman](https://www.david-hausman.com/), assistant professor
of law, University of California, Berkeley, for providing the
detention-stint-level ICE detention datasets acquired through FOIA requests
which are visualized in this dashboard. Vera also thanks the following
organizations for making available supplemental ICE datasets Vera used to
process the data and geocode facilities: Human Rights Watch, Transactional
Records Access Clearinghouse, National Immigrant Justice Center, Immigrant Legal
Resource Center, and the Marshall Project.

Vera would like to thank the following colleagues for their support in providing
editing, design, and guidance: Nina Siulc, Chris Henrichson, Jasmine Heiss,
Jacob Kang-Brown, Kica Matos, Will Snowden, and Lizzie Allen. The authors wish
to acknowledge the work of Dennis Kuo, who contributed to the development of the
Detention Stay ID algorithm as a former Senior Data Scientist at Vera.

# Contact
For more information, contact Noelle Smart, principal research associate, at
nsmart@vera.org.
