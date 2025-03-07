## Motivation for Analysis
The official Washington State open data portal provides datasets on various topics, including professional licensing, business registrations, government operations, and economic trends. The Washington State CPA dataset lists individuals who hold WA CPA credentials, have held WA CPA credentials, or are WA CPA candidates. While primarily used for credential verification and disciplinary tracking, this data offers deeper insights into CPA demographics, renewal rates, career longevity, and industry trends. Understanding licensing patterns such as how long CPAs maintain their credentials, what groups of people receive board violations, or where nonresident WA CPAs live, would provide valuable insights for policymakers, firms, and future accountants.

Informative link:
[Washington State Open Data Portal](https://data.wa.gov/)



## Data Overview
This dataset, originally published by the Washington State Board of Accountancy, contains a comprehensive list of 47,931 unique records of WA residents and nonresidents who are current CPAs, former CPAs, or CPA candidates. The data includes key details such as license number, name, status (active, lapsed, revoked, suspended, retired, deceased), original issue date, expiration date, and state or country of residence. The data is structured by individual records, with each row representing a CPA or CPA candidate along with their CPA status. 

Due to privacy constraints and the way the data is organized, integrating additional datasets proved challenging; CPA license numbers would be the most reliable way to connect datasets, but this information is rarely made publicly available. As a result, this analysis primarily focuses on insights directly taken from this verified dataset. Additional analysis can build off of my work by requesting CPA Firm or business registration data, including the license numbers of all CPAs, to establish even deeper insights into accounting career paths, firm affiliations, industry concentrations, and potential correlations between firm size and rate of CPA disciplinary action. For example, many Washington CPAs live in Japan; if we could obtain firm data from Japanese accounting firms, we could analyze which types of accountants require an American CPA license and compare the presence of American CPAs in Japanese "Big 4" firms versus smaller independent firms with less international presence.   

Links to Data:
[Washington State CPA Dataset](https://data.wa.gov/Consumer-Protection/Washington-State-Certified-Public-Accountants/6du3-3h9e/about_data),
[My Repository](https://github.com/LoganFitz1/Washington-State-CPA-Trends-and-Insights.git)


## Data Cleaning Process


Before effectively using this dataset, I first needed to perform some minor cleaning and structuring. I started by structuring the CPA data by normalizing city names with the “norm_city” dimension to merge identical city entries ("Seattle" vs. "SEATTLE"). I then created measures to group different CPA categories, ensuring the counts of CPA licenses accurately capture the proper groups; for example, when finding the CPA renewal rates, I cannot include the license number of CPA candidates who are unable to renew a certification they don’t fully have yet. In addition, to streamline analysis, I built repeat calculation measures, dimensions, and nested functions for complex queries. I also experimented with views, reducing code repetition for queries like 8 and 13. Finally, I used bar graphs, line graphs, and tooltips to enhance data visualization and provide deeper insights.



## Summary of Findings
The findings below are directly sourced from the WA state CPA dataset using queries I wrote to analyze the data. Insights can be used to interpret the CPA landscape in WA, offering valuable context on licensing trends, career longevity, and regulatory patterns. I encourage anyone to build upon this work using the GitHub Web Editor to expand my analysis and identify more data trends or insights. 

- There was a **large spike in both retired CPAs and newly certified CPAs in 2002**. Notably, this spike follows the legislation changes relating to the Sarbanes-Oxley Act of 2002 in response to widespread corporate fraud and misstatements. The inverse nature of these trendlines highlight the demand for a stable number of qualified CPAs and the strict SOX regulations that led many to reassess their accounting careers (Queries 1 and 2).

| **<img src="Newly Certified WA CPAs Over Time.png" alt=" Line-chart: Newly Certified WA CPAs Over Time [Query 1]" width="65%">**|**Query 1: Newly Certified WA CPAs Over Time** |
|-------|----|

| **<img src="Retired WA CPAs Over Time.png" alt=" Line-chart: Retired WA CPAs Over Time [Query 2]" width="65%">**|**Query 2: Retired WA CPAs Over Time** |
|-------|----|


- Of the current CPAs living in WA State, **a majority consisting of 2,413 reside in Seattle**, followed by **Bellevue at 791**, and **Spokane third at 593 CPAs** (Query 5).

| **<img src="WA Resident CPAs by City.png" alt=" Bar-chart: WA Resident CPAs by City [Query 5]" width="55%">**|**Query 5: WA Resident CPAs by City** |
|-------|----|


- California has the most number of current WA CPAs living outside of WA but within the United States **at 730 CPAs** (Query 13).

- **Japan has more Washington CPAs than any U.S. state outside of Washington combined**. I found this discovery interesting as it underscores the demand for accounting expertise in commerce between the U.S. and Japan, the lack of residency requirements for Washington CPAs, and the prestige of a Washington license over other states (Query 4).

| **<img src="WA CPAs Living Outside of WA.png" alt=" ToolTip, Bar-chart: WA CPAs Living Outside of WA [Query 4]" width="85%">**|**Query 4: WA CPAs Living Outside of WA** |
|-------|----|


- Washington resident CPAs face a **0.37% suspension rate** and a **0.07% license revocation rate** (Query 7).

- Even though Japan has the highest number of WA CPAs outside of Washington, **the UAE, China, other US States combined, and Canada all have higher suspension rates**—suggesting that Japanese accountants may adapt better to American accounting standards (Query 9).

| **<img src="Nonresident CPA Suspensions by Country.png" alt=" Data Table: Nonresident CPA Suspensions by Country [Query 9]" width="65%">**|**Query 9: Nonresident CPA Suspensions by Country** |
|-------|----|


- **93.65%** of WA resident CPAs renew their CPA license at least once (Query 11).

- **90.76%** of non-residents renew their WA CPA license at least once (Query 12).


- **Since 2010** there has been a **major increase in non-CPA CPA firm owners**. This lends insight into the challenge of the CPA credential process and regulatory changes allowing non-CPAs to own CPA firms (Query 14).

| **<img src="Increase in Non-CPA CPA Firm Owners.png" alt=" Line-chart: Increase in Non-CPA CPA Firm Owners [Query 14]" width="60%">**|**Query 14: Increase in Non-CPA CPA Firm Owners** |
|-------|----|



- **The average WA CPA career length is 15.2 years**, and the **longest-serving WA CPA is a gentleman named Delmar Pearson, who maintained his license for 69.8 years**. A wonderful aspect of working with Malloy is the opportunity to make discoveries you might never have expected, and Delmar Pearson is a perfect example of this. Upon learning of this extraordinary accomplishment, I researched Mr. Delmar Pearson and discovered his beautifully written obituary. Delmar was a veteran and family man, lived to be 99 years old, and **holds the record for the longest maintained CPA in WA history**. Delmar represents a hero in the accounting community, and I hope his story will not be forgotten soon. More on Delmar can be found [here](https://www.legacy.com/us/obituaries/legacyremembers/delmar-pearson-obituary?id=9019091) (Query 6).

| **<img src="Avg CPA Career Length and Longest Serving CPA.png" alt=" Data Table: Avg CPA Career Length and Longest Serving CPA [Query 6]" width="115%">**|**Query 6: Avg CPA Career Length and Longest Serving CPA** |
|-------|----|


## Licensing
The CSV file was sourced from the Washington State open data portal and is available for public use: [Washington State Certified Public Accountants Dataset](https://data.wa.gov/Consumer-Protection/Washington-State-Certified-Public-Accountants/6du3-3h9e/about_data). All other data files and visualizations have been created by Logan Fitzpatrick for Gonzaga University Graduate School of Business as part of the MSBA-622-01 Data Science for Business (Spring 2025) course. These materials are available under the Creative Commons [CC BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/). The code in this repository is licensed under the [MIT License](https://opensource.org/license/mit/).

## Directions on How to Use GitHub Web Editor

Are you logged into github? Just press the period key right now. This will load the web editor. Then install the Malloy extension. Feel free to explore, experiment, and learn more about Washington State CPAs!
See images below for direction references:
| **Step**   | **Image Preview** |
|--------|-----------|
| `Step 1 - Press allow` | <img src="step1.png" width="50%"> |
| `Step 2 - Click the Blocks, search for Malloy, install` | <img src="step2.png" width="50%"> |
| `Step 3 - Click Trust` | <img src="step3.png" width="50%"> |
| `Step 4 - Click a .malloynb file` | <img src="step4.png" width="50%"> |
| `Step 5 - Press Run` | <img src="step5.png" width="50%"> |


