![](https://www.vera.org/dist/img/logo_full.svg)

# ICE Detention Trends Data
Vera’s [ICE Detention Trends](http://vera.org/ice-detention-trends) dashboard reveals an unprecedented level of detail about ICE detention populations—nationally and across the 1,397 facilities in which ICE detained people—on each day of the 16-year period from fiscal year 2009 through mid-fiscal year 2025 (October 1, 2008, through June 10, 2025). This repository includes the aggregated data visualized in the dashboard, including information on:

- Midnight population: the daily number of people detained at midnight
(nationally and by facility).
- 24-hour population: the number of people detained for any part of a given day,
including those whom ICE transferred or booked-out of custody before midnight
(nationally and by facility). While ICE relies solely on midnight populations in
its reporting, Vera includes both types of daily populations—midnight and
24-hour—as the two can differ drastically.
- Book-ins: the daily number of people ICE booked into custody (nationally).
- Book-outs: the daily number of people ICE booked out of custody (nationally).
- Facility names, locations, and types (as coded by ICE in other datasets, where available).

## About the Data
This dashboard primarily draws from ICE detention datasets obtained through Freedom of Information Act (FOIA) requests, shared with Vera by David Hausman, assistant professor of law, University of California, Berkeley, and the American Civil Liberties Union (ACLU). The initial version of this dashboard, launched in August 2023, used data from October 1, 2008, through March 30, 2020 (“Dataset I”). Vera updated this tool in July 2025 to add more recent data. The current iteration of the tool uses data from October 1, 2008, through June 10, 2025 (fiscal year 2009 through mid-fiscal year 2025). The data includes detention history information for every person in ICE custody during this time. 

The structure of Dataset I, used for the original dashboard release in August 2023, posed several challenges for researchers seeking to analyze ICE operations. Most notably, the dataset does not link together separate detention stints for people whom ICE transferred to one or more facility after their initial book-in. To overcome this limitation, Vera developed a novel algorithm to construct individual detention histories from a person’s initial book-in to their final-book out, inclusive of any transfers. Doing so allowed Vera to combine records across spreadsheets, account for duplicated data, and compute detention populations. 

Vera later received updated datasets (“Dataset II” and “Dataset III”) that included anonymized identifiers that linked records across a person’s detention history. These newer datasets are nearly identical in form to the original dataset, with some exceptions requiring a revised method of calculating detention population statistics, as described in Vera’s technical appendix. Vera used these different datasets to calculate statistics for different time periods, with some exceptions explained in the technical appendix:
- Dataset I: October 1, 2008, through September 30, 2013;
- Dataset II: October 1, 2013, through September 30, 2023; and
- Dataset III: October 1, 2023, through June 10, 2025.

Differences in facility populations before and after the respective date boundaries (i.e., from September 30 to October 1, 2013, and from September 30 to October 1, 2023) may at least partially reflect differences in how ICE compiled the different datasets, rather than a population change alone.

Vera counts each unique facility code in the ICE detention data as a distinct facility. Some facility codes appear to reflect different units or buildings in the same or adjacent physical property as another code. Other facility codes reflect facility “types” other than a detention center, such as hospitals or hotels. Vera did not combine or group facility codes for two reasons. First, there is no available ICE source to combine such codes for the entire ICE network. Second, the fact that ICE uses distinct codes in these instances indicates that they carry some significance in data entry.

The original datasets included facility names and codes, but no information on location or facility type. Vera drew from additional datasets and public sources to geocode facility locations and assign facility types. Given the lack of a comprehensive, up-to-date ICE source to assign facility types to all 1,397 facility codes in the dataset, Vera’s categorizations should be interpreted as best-known facility type. To simplify map filtering options, Vera grouped facility types assigned by ICE, as well as ones manually entered by Vera, into the following categories:
- Non-Dedicated: IGSA (Inter-governmental Service Agreement).
- Dedicated: DIGSA (Dedicated IGSA), SPC (Service Processing Center), CDF (Contract Detention Facility).
- Federal: USMS IGA (U.S. Marshals Service Inter-governmental Agreement), BOP (Bureau of Prisons), USMS CDF (U.S. Marshals Service Contract Detention Facility), DOD (Department of Defense), MOC (Migrant Operations Center). Because ICE can be added to other federal agencies’ facility contracts or agreements through a “rider,” Vera reports federal facilities as a separate category, rather than grouped with other categories such as non-dedicated facilities.
- Hold/Staging.
- Family/Youth: Family, Family Staging, Juvenile. ICE’s use of the “Juvenile” facility type reflects ICE detention and does not refer to facilities used to detain unaccompanied children in the custody of the Office of Refugee Resettlement (ORR).
- Medical: Facilities coded by ICE as “Hospital” and medical or mental health facilities manually coded by Vera.
- Hotel: Facilities coded by ICE as “Hotel” and facilities manually coded by Vera.
- Other/Unknown: Facilities coded by ICE as “Other” or ones for which Vera was unable to assign facility type.

See the [technical appendix](https://vera.org/ice-detention-trends/files/dashboard_appendix.pdf?) for more detail about Vera’s classification of facility types.

Vera chose to present the ICE detention data “as is” to the greatest extent possible, including any inconsistencies or errors that may be present in the data compiled and shared by ICE. For example, Vera retained data entries that indicated lengths of stay lasting zero minutes and those that showed people as being detained in two places at once during a transfer. Notably, some detention facilities in the older dataset were missing from the newer data in the period in which the two datasets overlap (see technical appendix). Other researchers have noted similar gaps, inconsistencies, and errors in ICE detention records.  

For more information about the data and Vera's methodology, see the accompanying [technical appendix](https://vera.org/ice-detention-trends/files/dashboard_appendix.pdf?).

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
    |   |-- FY2020.csv
    |   |-- FY2021.csv
    |   |-- FY2022.csv
    |   |-- FY2023.csv
    |   |-- FY2024.csv
    |   `-- FY2025.csv
    `-- metadata/
        `-- facilities.csv
```

## `national.csv`
National population statistics for each day between October 1, 2008, and June 10, 2025, including midnight population, 24-hour population, book-ins, and book-outs.

| Variable     | Type      | Description                                                                                                                   |
| ------------ | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| date         | `date`    | The date for which each metric is reported (`yyyy-mm-dd` format)                                                              |
| daily_pop    | `numeric` | 24-hour population:  the number of people detained for any part of a given day, including those whom ICE transferred or booked-out of custody before midnight  |
| midnight_pop | `numeric` | Midnight population: the daily number of people detained at midnight                                                  |
| book_in      | `numeric` | Book-ins: the number of people booked into ICE custody                                                                        |
| book_out     | `numeric` | Book-outs: the number of people booked out of ICE custody                                                                     |


## `facility/`
### `FY20XX.csv`
Facility-level population statistics for each day between October 1, 2008, and June 10, 2025, including midnight population and 24-hour population.  To make file sizes more manageable, Vera split the data into separate .csv files by fiscal year (October 1 of the previous year through September 30 of a given year). Note: fiscal year 2025 is a partial fiscal year covering October 1, 2024, to June 10, 2025.

| Variable                | Type      | Description                                                                                                                   |
| ----------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| detention_facility_code | `string`  | The unique identifier used in the ICE detention data for each facility                                                        |
| date                    | `date`    | The day each count is reported for (`yyyy-mm-dd` format)                                                                      |
| daily_pop               | `numeric` | 24-hour population:  the number of people detained for any part of a given day, including those whom ICE transferred or booked-out of custody before midnight |
| midnight_pop            | `numeric` | Midnight population: the daily number of people detained at midnight                                                  |

## `metadata/`
### `facilities.csv`
A lookup table mapping each detention_facility_code to information about the facility, drawing from supplemental ICE data and other sources. (See technical appendix for more detail.)

| Variable                | Type      | Description                                                                                        |
| ----------------------- | --------- | -------------------------------------------------------------------------------------------------- |
| detention_facility_code | `string`  | The unique identifier used in the ICE detention data for each facility                             |
| detention_facility_name | `string`  | The facility name associated with the detention_facility_code in the ICE detention data            |
| latitude                | `numeric` | The latitude coordinate of the facility location                                                   |
| longitude               | `numeric` | The longitude coordinate of the facility location                                                  |
| city                    | `string`  | The city in which the facility is located                                                          |
| state                   | `string`  | The state abbreviation code. This also includes codes for U.S. territories (e.g. "PR" for "Puerto Rico") and Cuba ("CU") for facilities at Naval Station Guantanamo Bay. |
| type_detailed           | `string`  | The facility type as coded by ICE in supplemental data sources where available                     |
| type_grouped            | `string`  | Vera's categorization of facility types to simplify map filtering options for the dashboard.       |

# License
By downloading the data, you hereby agree to all the terms specified in this
license: [License.md](License.md).

# Credits
Data analysis: Noelle Smart, Zachary Lawrence, and Neil Agarwal

Data engineering: Zachary Lawrence and Neil Agarwal

Design and development: Neil Agarwal

Writing: Noelle Smart
Editing: Léon Digard

# Acknowledgements
Vera thanks [David Hausman](https://www.david-hausman.com/), and the American Civil Liberties Union (ACLU) for providing the detention-stint-level ICE detention [datasets](https://deportationdata.org/) acquired through FOIA requests which are visualized in this dashboard. Vera also thanks the following organizations for making available the supplemental ICE datasets Vera used to process the data and geocode facilities: Human Rights Watch, Transactional Records Access Clearinghouse, National Immigrant Justice Center, Immigrant Legal Resource Center, and the Marshall Project.

Vera would like to thank the following current and former colleagues for their support and guidance on this project: Nina Siulc, Jacquelyn Pavilon, Bethany Costello, Kenny Lam, Liz Kenney, Karen Ball, Megan Diamondstein, Chris Henrichson, and Lizzie Allen. The authors wish to acknowledge the work of Dennis Kuo, who contributed to the development of the Detention Stay ID algorithm during his time as senior data scientist at Vera.

# Contact
For more information, contact [urep@vera.org](urep@vera.org).
