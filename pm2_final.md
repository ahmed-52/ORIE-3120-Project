# Project Milestone 2

## Data Analysis Method - Predictive Model

### Question 1: How has women's participation in the Olympics evolved over time, and does the rate of growth differ across regions and sports?

To answer this question, we decided to create a model that would predict women's participation in the Olympics for the next four Olympic cycles. We modeled the aggregate for both summer and winter games, and then modeled the number across all the sports to see in which sport would the rate of growth increase the most. 

We decided to explore this question further, as we would like to see how women's involvement has grown over time, and if there is any external influences we can relate this to. 

## Data Analysis Method - Linear Regression
### Question 2: Does hosting the Olympic Games give a country a measurable home-field advantage in winning medals?

To answer this question, we used linear regression to estimate whether hosting the Olympics is associated with a higher medal count. 

First, we created a country-year dataset where each country’s medal count was recorded for each Olympic year. We then added a Host variable, where Host = 1 if the country hosted the Olympics that year and Host = 0 if they did not host. This model allowed us to estimate the average difference in medal count between host and non-host countries.

For the graph, we created a medal boost comparison based on each host country’s usual Olympic performance. For each host country, we calculated its average medal count in non-host years and compared that to the number of medals it won in its host year. This produced a “medal boost” value, defined as: 

Medal Boost = Host Year Medal Count − Average Non-Host Medal Count

Then, we used a second linear regression model to predict Host Year Medal Count using Average Non-Host Medal Count. This model estimated how many medals a host country would expect to win based on its usual Olympic performance. The second graph shows the residuals from this model, which is the difference between the actual host-year medal count and the model’s predicted host-year medal count. Bars with values above zero show countries that overperformed relative to the model, while bars below zero show countries that underperformed.

The visualization from Milestone 1 and the analysis from Milestone 2 show that countries typically win significantly more medals when they are hosting that year compared to the years where they are not hosting. This is could be due to the fact that when a country is hosting, athletes are fueled to impress the home crowd and may also have much more incentive to do well due to sponsorships. Additionally, it could also be due to increased investment they are hosting, larger team sizes, and overall increase in preparation of the athletes for the game they host.
