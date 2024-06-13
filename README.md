# Analyzing Olympic Data

## Tech Stack
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
## Description

The main goal of this project was to showcase what I've learned in Python (numpy) and SQL. The goal was to analyze olympic medals won by different countries in the 2016 Olympics.



I extracted a .csv file from a preloaded dataset and filtred it to only include the 2016 olympics and grouped it by team, event, medals earned, and population.

```
# Calculate event medals
event_medals = olympics_full.query("year == 2016")\
  .groupby(["team_clean", "event", "medal", "population"], as_index=False)["medal"].first()

# Preview the DataFrame
event_medals

```

I then grouped the data by the team and the population to count the number of medals each country won. I visualized the number of gold medals by country using Plotly, creating a choropleth map.


![alt text](<DataLab plot.png>)





The map shows that the US has the most gold medals for the year 2016 at 2529, while Peru has the least number at one.


The database isn't shown in my files, but I queried a MariaDB database containing information on world nations to get more data. The query is then stored as a pandas dataframe called nations_data

```
SELECT 
 name as country,
 year,
 population
FROM countries 
INNER JOIN country_stats USING(country_id)
```


The next chart is a bar chart that is used to visualize the number of medals per 10 million people for the top 20 countries.


![alt text](<DataLab plot-1.png>)

# To dos:

- Create a website to showcase the data.