# Project Milestone 1

## 1. Dataset Description

Our dataset, *120 Years of Olympic History: Athletes and Results*, was scraped from Sports Reference in May 2018 and published on Kaggle. It covers every modern Olympic Games from Athens 1896 through Rio 2016. The dataset consists of two files:

**athlete_events.csv** (271,116 rows, 15 columns). Each row represents one athlete competing in one event at a particular Games. The columns are:

| Column | Type | Description |
|--------|------|-------------|
| ID | Integer | Unique identifier for each athlete |
| Name | String | Athlete's full name |
| Sex | String | M or F |
| Age | Float | Athlete's age (missing for 3.5% of rows) |
| Height | Float | Height in centimeters (missing for 22.2% of rows) |
| Weight | Float | Weight in kilograms (missing for 23.2% of rows) |
| Team | String | Team name (may differ from country, i.e. "Denmark/Sweden") |
| NOC | String | National Olympic Committee 3-letter code |
| Games | String | Year and season combined (e.g., "1992 Summer") |
| Year | Integer | Year of the Games (1896–2016) |
| Season | String | "Summer" or "Winter" |
| City | String | Host city |
| Sport | String | Sport category (66 unique sports) |
| Event | String | Specific event within the sport (765 unique events) |
| Medal | String | Gold, Silver, Bronze, or NA (didnt win a medal) |

**noc_regions.csv** (230 rows, 3 columns) maps each NOC code to a country/region name and includes notes for historical entities (e.g., "URS" maps to Russia, with a note "Soviet Union"; "GDR" maps to Germany, with a note for East Germany). This is essential because NOC codes alone are not human-readable, and several codes correspond to nations that no longer exist.

**Important notes about the data:**

- The unit of observation is an *athlete-event*, not an *athlete* or a *medal*. A single athlete who competes in five events at one Games appears as five rows. This means naive row counts overstate participation and medal totals for team sports.
- Height and Weight are missing for roughly one-fifth of entries, skewing toward earlier Games when these attributes were not systematically recorded. Any analysis of physical attributes must account for this survivorship in the data.
- The Winter and Summer Games were held in the same year until 1992. After 1992 they were staggered . Analyses over time must account for this structural change.
- Medal = NA means the athlete did not win a medal, not that the data is missing. Of the 271,116 entries, 39,783 (14.7%) are medal-winning performances.

## 2. Questions & Visualizations

### Question 1: How has women's participation in the Olympics evolved over time, and does the rate of growth differ across regions and sports?

Women were excluded from the 1896 Games entirely; by 2016 they made up ~45% of competitors. This aggregate trend likely masks variation,some sports admitted women decades before others, and cultural barriers may have slowed growth in certain regions. This matters to the IOC and national federations working toward gender parity: understanding where progress has been slowest helps direct funding and policy. The dataset records each competitor's sex, NOC, sport, and year, giving us everything needed to track these trends.

### Visualization 1: Women's Share of Olympic Competitors Over Time (by Season)

![Women's Share of Olympic Competitors](viz1_gender_participation.png)

**Description:** This line chart tracks the percentage of female competitors at each Olympic Games from 1896 to 2016, with separate lines for the Summer and Winter Games.

**Insight into Question 1:** The visualization reveals that women's participation was essentially zero before 1900, grew slowly through the mid-20th century, and then accelerated sharply from the 1970s onward, likely reflecting Title IX in the United States (1972), the IOC's push to add women's events, and broader societal shifts toward gender equity in sport. By 2016, the Summer Games approached 45% female participation. The Winter Games follow a broadly similar trajectory but with a notable lag, likely because Winter sports historically had fewer women's events. This visualization establishes the overall trend that Question 1 seeks to unpack further by region and sport.

### Question 2: Does hosting the Olympic Games give a country a measurable home-field advantage in winning medals?

The tradition of hosting Olympic Games in different countries encourages residents of that country to attend the games, as well as increasing advertisements for athletes of that country as well. With the home crowd on their side, will athletes representing the country hosting the Olympics perform better or worse than they have in years prior? We decided to look at this by creating a bar chart that shows the host country's Olympic medal number in the year that they were hosting the Olympics in comparison to the average of the other years where they were not hosting the Olympics. We create a lookup table mapping city to country, then perform aggregate counts over the dataset for the number of medals won. 

## Visualization 2: 

![Medals Won By Countries when Hosting vs Not Hosting](medals_host_country.png)

**Description:** This bar chart compares the amount of medals won by countries when they are hosting the Olympics vs the average across other years when they are not. 

**Insight into Question 2:** This visualization reveals that countries typically win a lot more medals when they are hosting that year vs the other years when they are not hosting. This is likely due to the fact that when a country is hosting, athletes are fueled to impress the home crowd and may also have much more incentive to do well due to sponsorships. In addition, the host country may be able to choose judges or staff that could skew the results in favor of their country's athletes, though it is uncommon. 

### Question 3: Does age metrics affect Winter and Summer Games atheletes differently?

The Olympic Games represent peak athletic performance across many different disciplines, and some athletes become better at their sport as they get older, and others may reach their peak at a certain age. We know in general, sports competitions favor the young and uninjured athletes over the vetarans, but we are unsure of this hypothesis for every single sport. As a result, we would like to explore the variance of age in sports, identifying which sports have the greatest variance and age and attempting to draw conclusions about the nature of the sport as a result. We divided this into four categories of Winter vs Summer games, as well as male vs female athletes to separate variables we think may play a part. 

## Visualization 3:

![Athlete Age Distribution for Summer and Female athletes](viz3_1.png)
![Athlete Age Distribution for Summer and Male athletes](viz3_2.png)
![Athlete Age Distribution by Winter and Female athletes](viz3_3.png)
![Athlete Age Distribution by Winter and Male athletes](viz3_4.png)

**Description:** These visualizations show the standard deviation of the ages of each sport by sex and Olympic season. 

**Insight into Question 3:** This visualization shows that most sports have very similar medians. However, the outliers show that there are certain sports that have much larger standard deviations. Additionally, while most sports have similar medians between the different sexes, there are certain sports such as gymnastics, shooting, and others that do have a significant difference in median and spread. This could be due to the nature of the sport and activities that they have to perform.

### Question 4: Which countries have the widest distribution of medals across Summer and Winter?

Some countries have more dominance in the summer sports, and others have more dominance in the winter sports, while some have no dominance at all at the Olympics. We wanted to investigate what countries have medals in the Summer or Winter Olympics, or even both. This allows us to recognize trends within the countries, and even point out a few countries that have the most dominance in both. 

## Visualization 4: 

![Summer vs Winter Olympic Medal Counts by Country](viz4.png)

**Description:** This scatterplot shows the numbers of medals won for all summer games (x axis) and winter games (y axis) for each country (represented by a point).

**Insight into Question 4:** This visualization reveals that there are certain countries that performed relatively well in both the Summer and Winter Olympics. However, there were some teams such as Austria that won significantly more medals in the Winter Olympics than the Summer Olympics. The results can be related to the number of athletes for each team in general, and also the strength in skills/training/resources and popularity of a sport in each country. This allows us to see trends in the country's regions corresponding to their performance at the Winter/Summer Olympics respectively. 

<!--

### Question 5: How does the season of the Olympics (Summer or Winter) influence medal patterns in different countries/teams?

Each country performs differently for each summer or winter Olympics. But which teams are stronger in both? In the summer? In the winter? This can be compared using a scatterplot, with the x-axis the number of summer medals and the y-axis the number of winter medals. Each point will represent a country, allowing us to compare each country's performances and how others did as well.

### Question 6: How does the age distribution of Olympic athletes vary by sport and sex?

Some Olympic athletes begin their careers at a very young age, but there is a wide range in different ages that compete. Are there certain sports that have more of a certain age group competing that other sports? And does this change for different genders? This can show which sports have competitors that are only from a certain age range or have more flexibility. We will look at this by creating box plots for each sport and gender and comparing distributions.

### Question 7: On average, how many games (years not events) do athletes compete in by country?

### Question 8: Which sports have the highest athlete specialization versus multi-event participation?

### Question 9: Which sports have the highest probability of winning a medal once an athlete competes?

### Question 10: How has the number of Olympic events changed over time within each sport?

### Question 11: Do athletes tend to win medals at younger or older ages depending on the sport?

-->