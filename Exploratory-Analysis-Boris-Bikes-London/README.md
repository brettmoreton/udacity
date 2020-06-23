# Boris Bikes - A Data-Powered Journey
## by Brett Moreton


## Dataset

> I decided to use a dataset produced by Transport for London (TfL) which details the use of the city's biycle hire scheme, which are currently branded as Santander Cycles, after the bank Santander who currently sponsor them. To me and many other Londoners of my generation, they will always be Boris Bikes, and I will refer to them as such henceforce.

> TfL is London's transport authority, who have remit for all travel matters across the city. Like many government bodies they are making the data their operations accumulate available for public use, and Boris Bike data is accessible via this link: https://cycling.data.tfl.gov.uk/

> The dataset is large. For 2019 there are over 10 million journeys recorded, and these files run to 1.3gb in size. My Exploration Notebook has code which will allow you to download the relevant data to your local machine, so you can run the same explorations as I have.

> Originally I had planned to run analysis on the whole of 2019, however my laptop was not powerful enough to run the data operations on such a large dataset. Even printing summary information about the dataset was taking around 20seconds to run. Therefore I decided to focus my analysis on a 4 week period in July 2019. For the purposes of this exercise, I believe this is sufficient, however as July tends to be a warmer summer month, the findings cannot necessarily be extrapolated to other months in the year. I gave consideration to running this analysis with the full year of data on a cloud based machine to benefit from greater compute, and will likely do this in the future for my own personal interest.

> TfL require me to adhere to terms and conditions which apply to this data. I can confirm I am in compliance with these, and details can be found here: https://tfl.gov.uk/corporate/terms-and-conditions/transport-data-service

## Summary of Findings

> After gathering, assessing and cleaning my data I decided to take an iterative, "look-and-see" approach to my initial data exploration, to see where the data would lead me. Here is a summary of the journey.

### Journey Durations
> First I wanted to look at journey durations. This univariate exploration was best done via a histogram, however the data was presented in seconds (eg, hours/minutes/**seconds**) and was heavily skewed to the right. I performed a log transformation of the durations and converted seconds to minutes, which led to a highly interpretable histogram of journey durations.

> The main outcome from this was a conclusion that a significant percentage of journeys are "short" in duration, lasting less than one hour.

### Popular Days for Cycling
> The next question I had was to question which days of the week were most popular for hiring Boris Bikes. Would Friday's be quieter, because people tend to work from home on Friday's? Would Monday be busiest, when everyone is eager to burn of the weekends excesses? How busy would weekends be in comparison to weekdays?

> I used the datetime function to extract the named day of the week and with this data I plotted bar charts. The outcome showed that Wednesday was the most popular day of the week, with over 160,000 journeys made on the 4 Wednesday's in my sample data. As I suspected, Friday was the quietest day of the weekdays, and Saturday and Sunday were both similarly quiet compared to weekday journeys. I expect that tourists will be making up the large majority of journeys on the weekends, and there were still almost 240,000 journey's made over the 8 Saturday's and Sunday's in the data sample. London is popular!

### Saturday Night's Alright For Cycling
> Now we know that Wednesday is the most popular day for cycling, but what time on Wednesday's, and what time on Fridays, Saturdays, Sundays? I split the 24 hour period in to 6 blocks of 4 hours and created a bar chart to visualise the most popular times of day for Boris Bike journeys.

> It turns out that on weekdays, the evening (4-8pm) and the morning (8-12noon) are the two most popular times. Most likely these are the times that London's hardworking busy-bees are getting themselves to and from the office, as fast as possible. At the weekends this dynamic changes and the midday (12-4pm) is most popular for journeys. Those lazy tourists!

### Here, There, Everywhere
> Next, I decided it would be interesting to see where Boris Bikes journeys were taking people. As there are so many docking stations (787 of them!) it would not be feasible to look at this on a docking station basis. I decided to supplement the data provided by TfL by giving each docking station a compass flag (North, East, South, West, or Central) and it's Zone. From a (simple) transport perspective London is split into 6 Zones. Zone 1 covers central London, Zone 2 forms a ring around Zone 1, and this pattern continues, moving outwards and deeper into Greater London.

> My data sources for this additional data gathering were my own local knowledge of the city, complemented by:

>> * http://content.tfl.gov.uk/london-rail-and-tube-services-map.pdf
>> * https://tfl.gov.uk/modes/cycling/santander-cycles/find-a-docking-station

> Simple bar chart plots showed that Central London was the most popular starting and ending point for a majority of journey's, but these charts hid detail that I thought would be interesting. I used a Sankey Diagram plot to show where individual journey's (on a compass basis) started and ended. This fascinating plot shows, among other detail, some commuter journeys over the 4 week period as follows:

>> Over 13,500 journeys starting from North London ending in Central London
>> Over 57,800 journeys starting from East London ending in Central London
>> Over 49,300 journeys starting from South London ending in Central London
>> Over 35,600 journeys starting from West London ending in Central London

### Utilisation Rates
> With such few journeys from North London when compared to other areas, I then looked at the number of docking stations in North, East, South and West London and quickly realised that North London has very many fewer docking stations - with only 17, versus 135 in East London.

> With relatively fewer docking stations, I wanted to see if North Londoner's have a higher utilisation rate, by showing the average number of journey's started per day from the 4 compass areas. The 5 number summaries are useful here, and these are well illustrated through box and violin plots.

> The visualisation shows that the average number of journey's per day from each docking station, grouped by compass area, was about the same, in the range of 35-38 journeys per docking station per day. Interestingly, the docking stations in North London had a minimum average usage per day of 17 journeys. The nearest competitor to this was West London's docking stations with an average minimum of just 6 journeys per day. This is shown in the visualisation by the lack of a tail to the North's plot. This shows that, although North London has fewer docking stations, they are very well utilised, and I suspect they need to be restocked quite quickly throughout peak commuter hours. North London might be in line for an expansion in it's docking stations in the near future - properties close to new docking stations could be seeing an increase in value!

### COVID-19 and Lockdown
> The UK and London went into official "lockdown" on 23rd March 2020, with all citizens required to stay at home unless they had Key Worker status, or could not do their jobs from home. The number of commuters in to London plummeted, and tourists were either already gone or obliged to stay in their hotels/accommodation until they left the UK. The Government's daily coronavirus briefing used data from Google Maps and TfL to show how the movement of people had slowed dramatically.

> I decided to take a look at the data, to see what happened to Boris Bike hire during these turbulent times. This is a fascinating chart which shows the significant decrease in cycle journeys as the UK Lockdown began on 23rd March. We can see significant decreases in journeys made as the lockdown comes in to force, and for the week ending 31st March there were 68,184 journeys made across London. At the same time last year there was around 200,000. Interestingly the number of journeys made then begins to increase in April, however not to "normal" April levels as per 2019. Perhaps this was down to people using Boris Bikes to commute instead of trains, tubes and buses, while significant numbers of London's residents were locked down.

> The UK's Lockdown measures were eased on 11th May, and from this date we can see the number of journeys taken on Boris Bikes spikes significantly. In the week ending 26th May a high of 312,668 journeys was made in one week. I would need to look at data from 2018 and previous years, but I suspect this will be an all time high.

## Key Insights for Presentation

> For my presentation I will show how and when Boris Bikes are used. First we will look at the duration of a typical journey, and then see what days and what time of day these journey's happen. We'll look where journey's are starting and ending, and see that North London has significantly fewer docking stations when compared to East, South and West London. But who has the highest utilisation rates? Let's find out.

## Resources Used

* With thanks to TfL for making it's data available
* Stack Overflow, obviously
# udacity
# udacity/Boris-Bikes-Exploratory-Analysis
