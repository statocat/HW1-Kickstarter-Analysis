# Kickstarting with Excel

## Overview of Project

An up-and-coming playwright, Louise, would like to run a crowdsourced fundraising campaign to raise at least $10,000 her new play, *Fever*. Louise wants to ensure her fundraising goal will be met, so she has asked for help constructing a data-driven approach to ensure her campaign is a success. 

### Purpose

A dataset containing key information about over 4000 kickstarter campaigns will be used to determine which key factors contribute to the success of a campaign. Particular attention is paid to data pertaining to campaigns focused on fundraising for theater and plays to be most applicable to the client. These insights are visualized in two charts to inform Lousie on how to give her fundraising campaign the best chance of being successful.

## Analysis and Challenges

The kickstarters campaigns data is organized in an Excel workbook. Some data cleaning was needed to get facilitate the analysis. In particular, data pertaining to the launch and end dates of the campaigns was stored as UNIX timestamps. These were converted to human-readable dates in two new columns called **start_date** and **end_date** using the formula ``` =(((VALUE/60)/60)/24)+DATE(1970,1,1)``` where ```VALUE``` is the UNIX timestamp. Next, a new column, **start_year**, was added to the dataset containing the year a campaign was launched using the YEAR function. 

In addition to cleaning the data pertaining to the time campaigns took place, data relating the type of campaign needed attention. Specifically, information regarding the category and subcategory was stored in one column separated by a delimeter, "/". This data was easily split into two columns named **Category** and **Subcategory** at the delimeter, "/", using the **Text to Columns** tool under the **Data** tab.

### Analysis of Outcomes Based on Launch Date

It was discovered that the time of year a kickstarter campaign is launched is predictive of the likelihood of meeting the campaign goal. To arrive at this conclusion, a pivot table and chart was constructed. The pivot table showed the count of **successful**, **failed**, or **canceled** campaigns organized according to the month in which they were launched. Notably, **live** campaigns were excluded since their outcome cannot yet be determined.  Since the client is particularly interested in theater, a filter was applied so that only data from that category was included in the table. A second filter was applied so that data may be sub-selected by the year in which a campaign was launched if desired.

![TheaterOutcomesByLaunchDateTable](https://user-images.githubusercontent.com/87917568/188524829-c2e6f140-4a5c-49ac-a0eb-b1352e56b64d.png)


This data was visualized in a Pivot Chart constructed of a line graph. A data series for each potential outcome, **successful**, **failed**, or **canceled** is plotted. From this chart, one can see that campaigns launched in the months of January through April and August through December have a minor to moderately higher chance of success than failure. This is good news for the client -- no matter when she launches her campaign, this data suggests the chance of success are better than 50-50. However, it is clear that the best time to launch a fundraising campaign for theater projects is in early summer in the months of May and June when the ratio of successful to failed campaigns is highest. The dead of winter, in October through December would be the worst time to launch a campaign as the ratio of successful to failed campaign declines to nearly 1:1. Finally, the number of canceled campaigns tends to remain consistently low throughout the year.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/87917568/188524884-d6ca6a0f-1878-489e-90e8-d47a9759e008.png)


### Analysis of Outcomes Based on Goals

Further analysis of data belonging to the *plays* subcategory revealed that careful timing is not the only factor that determines a campaign's success. In fact, thoughtful consideration of the fundraising goal is also needed.

The number of **successful**, **failed**, and **canceled** campaigns conducted for plays was tabulated and categorized based on the goal amounts utilizing the COUNTIFS formula. The total number of campaigns in each goal amount range was found using the SUM formula and in turn used to compute the percentage of **successful**, **failed**, and **canceled** campaigns. 

This data was visualized in a line graph including a data series for each potential outcome, **successful**, **failed**, and **canceled**. Notably, there were no canceled campaigns across all groups of goal amounts in fundraising campaigns for plays. From this chart, one can conclude that campaigns with fundraising goals less than 15,000 or between 35,00 and 45,000 in the national currency the campaign was conducted tend to have a greater chance of success than failure.


*NOTE: one should be careful in considering the relative value across currencies and perhaps should only consider data arising from campaigns conducted in the same country.*


However, campaigns with fundraising goals less than 5,000 tend to have a much higher chance of success than campaigns with a goal between 10,000 and 15,000. This means that Louise would be wise to consider trimming her budget to around $5000 if possible to increase her odds of completing a successful campaign.

One limitation of this chart is that by plotting percentages one does not get a sense of the relative size of each group of goal amounts. In fact, nearly 85% of all fundraising campaigns for plays have goals of $10,000 or less, putting Louise's fundraising goal in the upper quartile. And while plays with goals between 35,000 and 45,000 also have a high probability of success, less than 1% of campaigns fall in that grouping and further analysis of other factors contributing to their success should be sought after.

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/87917568/188524901-b4e7acbc-b84a-465e-884e-f4907a6d2c4d.png)


## Results

***- What are two conclusions you can draw about the Outcomes based on Launch Date?***

    1. Historically, the best time to launch a campaign is early summer i.e. May to June.

    2. Historically, the worst month to launcha campaign is December


***- What can you conclude about the Outcomes based on Goals?***
    1. Campaigns with goals of 5000 or less have a higher likelihood of success than campaigns with a goal of 10,000-14,999.

    2. There are no successful fundraising campaigns for plays in this data set with a goal between 45,000 and 49,999.

***- What are some limitations of this dataset?***

     It would be interesting to know the identity of the campaigners, how many campaigns they have conducted, and the outcomes of each campaign. 

     It would also be interesting to have marketing data to determine if runnning ads or other forms of outreach were utilized for each campaign.  

     We do not have information about the distribution of donations in each campaign - did most of the money come from cumulative small donations or a          few large donations. We are only able to compute the average donation - not the median which is a more robust statistic.


***- What are some other possible tables and/or graphs that we could create?***

    It would be interesting to know how the length of duration of a campaign impacts its success. To visualize this, we could create a new column in           the data set and utilize the DATEDIF formula with arguments date1, date2, and "m" to compute the duration of each campaign in months. A line chart         plotting the counts of each outcome category vs duration could be used to visualize the data.

    It would be interesting to know how the average donation size impacted the success of a campaign. Often kickstarter campaigns include tiered               incentives for backers. This information could be utilized to determine how to distribute the tiers. This data could be tabulated and visualized           similarly to the second analysis, but instead of grouping by goal amount the data would be grouped by average donation amount.
