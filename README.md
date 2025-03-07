## Motivation for Analysis
The official Washington State open data portal provides datasets on various topics, including professional licensing, business registrations, government operations, and economic trends. The Washington State Certified Public Accountants dataset lists individuals who hold WA CPA credentials, have held WA CPA credentials, or are WA CPA candidates. While primarily used for credential verification and disciplinary tracking, this data offers deeper insights into CPA demographics, renewal rates, career longevity, and industry trends. Understanding licensing patterns such as how long CPAs maintain their credentials, what groups of people receive the most board violations, or where nonresident WA CPAs are based would provide valuable insights for policymakers, firms, and future accountants.

Informative links:
[Washington State Open Data Portal](https://data.wa.gov/)



## Data Overview
This dataset, originally published by the Washington State Board of Accountancy, contains a comprehensive list of 47,931 unique records of WA residents and nonresidents who are current CPAs, former CPAs, or CPA candidates. The data includes key details such as license number, name, status (active, lapsed, revoked, suspended, retired, deceased), original issue date, expiration date, and state or country of residence. The data is structured by individual records, with each row representing a CPA or CPA candidate along with their CPA status. 

Due to privacy constraints and the way the data is organized, integrating additional datasets proved challenging; CPA license numbers would be the most reliable way to connect datasets, but this information is rarely made publicly available. As a result, this analysis primarily focuses on insights directly taken from this verified dataset. Additional analysis can build off of my work by requesting CPA Firm or business registration data, including the license numbers of all CPAs, to establish even deeper insights into accounting career paths, firm affiliations, industry concentrations, and potential correlations between firm size and rate of CPA disciplinary action. 

Links to Data Sources:

[Washington State Certified Public Accountants Dataset](https://data.wa.gov/Consumer-Protection/Washington-State-Certified-Public-Accountants/6du3-3h9e/about_data)


[Link to My Project Repository](https:)


## Data Cleaning Process


Before effectively using this dataset, I first needed to perform some minor cleaning and structuring. I started by structuring the CPA data by normalizing city names with the “norm_city” dimension to merge identical city entries ("Seattle" vs. "SEATTLE"). I then created measures to group different CPA categories, ensuring the counts of CPA licenses accurately capture the proper groups; for example, when finding the CPA renewal rates, I cannot include the license number of CPA candidates who are unable to renew a certification they don’t fully have yet. In addition, to streamline analysis, I built repeat calculation measures, dimensions, and nested functions for complex queries. I also experimented with views, reducing code repetition for queries like 8 and 13. Finally, I used bar graphs, line graphs, and tooltips to enhance data visualization and provide deeper insights.



## Summary of Findings
The findings below are directly sourced from the WA state CPA dataset using queries I wrote to analyze the data. Insights can be used to interpret the CPA landscape in WA, offering valuable context on licensing trends, career longevity, and regulatory patterns. I encourage anyone to build upon this work using the GitHub Web Editor to expand my analysis and identify more data trends or insights. 

There was a large spike in both retired CPAs and newly certified CPAs in 2002. Notably, this spike follows the major legislation changes relating to the Sarbanes-Oxley Act of 2002 in response to widespread corporate fraud and misstatements. The inverse nature of these trendlines highlights the demand for qualified CPAs and the strict SOX regulations that led many to reassess their accounting careers. [Queries 1 and 2]

<img src="Newly Certified WA CPAs Over Time.png" alt=" Line-chart: Newly Certified WA CPAs Over Time [Query 1]" width="50%">
<img src="Retired WA CPAs Over Time.png" alt=" Line-chart: Retired WA CPAs Over Time [Query 2]" width="50%">

Of the WA CPAs living in WA, the majority reside in Seattle (2,413 CPAs), followed by Bellevue (791 CPAs) and then Spokane (593 CPAs). [Query 5]

<img src="WA Resident CPAs by City.png" alt=" Bar-chart: WA Resident CPAs by City [Query 5]" width="50%">

California has the most current WA CPAs (730 total) living outside of WA but within the United States. [Query 13}

Japan has more Washington CPAs than any U.S. state outside of Washington combined. I found this discovery interesting as it underscores the demand for accounting expertise in commerce between the U.S. and Japan, the lack of residency requirements for Washington CPAs, and the prestige of a Washington license over other states (Query 4)

<img src="WA CPAs Living Outside of WA.png" alt=" ToolTip, Bar-chart: WA CPAs Living Outside of WA [Query 4]" width="50%">

Washington resident CPAs face a 0.37% suspension rate and a 0.07% license revocation rate. (Query 7)

Even though Japan has the highest number of WA CPAs outside of Washington, the UAE, China, other US States, and Canada all have higher suspension rates—suggesting that Japanese accountants may adapt better to American accounting standards. (Query 9)

<img src="Nonresident CPA Suspensions by Country.png" alt=" Data Table: Nonresident CPA Suspensions by Country [Query 9]" width="50%">


93.65% of WA resident CPAs renew their CPA license at least once. (Query 11)

90.76% of non-residents renew their WA CPA license at least once. (Query 12)


Since 2010 there has been a major increase in non-CPA CPA firm owners. This lends insight into the challenge of the CPA credential process and regulatory changes allowing non-CPAs to own CPA firms (Query 14)


<img src="Increase in Non-CPA CPA Firm Owners" alt=" Line-chart: Increase in Non-CPA CPA Firm Owners [Query 14]" width="50%">


The average WA CPA career length is 15.2 years, and the longest-serving WA CPA is a gentleman named Delmar Pearson, who maintained his license for 69.8 years. A wonderful aspect of working with Malloy is the opportunity to make discoveries you might never have expected, and Delmar Pearson is a perfect example of this. Upon learning of this extraordinary accomplishment, I researched Mr. Delmar Pearson and discovered his beautifully written obituary. Delmar was a veteran and family man, lived to be 99 years old, and holds the record for the longest maintained CPA in WA history. Delmar represents a hero in the accounting community, and I hope his story is not soon forgotten. More on Delmar can be found 

<img src="Avg CPA Career Length and Longest Serving CPA.png" alt=" Data Table: Avg CPA Career Length and Longest Serving CPA [Query 6]" width="50%">

[here](https://www.legacy.com/us/obituaries/legacyremembers/delmar-pearson-obituary?id=9019091) (Query 6)
