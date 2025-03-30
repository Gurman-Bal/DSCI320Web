# Reports

<!-- - This folder should contain all the written reports for the DSCI 320 project milestones -->

## Introduction

With the growing accessibility of technology, gaming companies are continually seeking ways to enhance user engagement, with one key approach being platform accessibility. Today, games are available across multiple platforms, with Steam standing out as one of the most prominent. As a digital distribution service by Valve, Steam allows developers to create, gamers to play, and communities to connect (Steam, the Ultimate Online Game Platform, n.d.). With over 132 million monthly active users, Steam provides a well-rounded review of how games are faring (Backlinko, 2025). Thus, this study will look at 2023 to 2024 gaming trends on this platform by using a dataset compiled from the Steam API called the “Steam games Dataset 2025”, which is publicly available on Kaggle (Manhães, 2025).

The objective of this dataset is to display an easy way to process information through the Steam platform, with each row representing a game and 21 unique columns that describe the game’s attributes. The dataset includes over 71,000 games, allowing large enough data to see trends throughout this study's search space for areas of interest. Since the data was collected through the Steam API, this makes the data a reliable and ethical source for analysis. As 2025 is still ongoing, the dataset is being updated. Due to this, this study will use the previous years of 2023 and 2024 data to analyze.

The group members in this project are four University of British Columbia (UBC) students, Xueyong, Gurman, ZiXun, and Jen. Xueyong, with some experience in game development from UBC's CPSC 427 Video Game Programming course, is curious about how genres and categories influence player engagement and success. This is based on his theory on games, which is a video game requires more than just good programming from a technical aspect, engaging topics and compelling gameplay. Meanwhile, Gurman is relatively well-updated on gaming trends, and has noticed that recent years have been a disappointment for many major gaming companies in terms of user and monetary turnout. Thus, he is interested in analyzing how the overall sentiment has trended over 2024 for gaming developers. ZiXun is a finance student and has noticed different goals between free games and those that are more costly. Free and low-paid games prioritize gamers' accessibility and expand awareness, while high-paid games usually rely on their IP values and excellent game qualities. In the past few years, some popular games (CSGO, PUBG, etc.) have changed from paid to free. Thus, he is interested in how pricing models (free, low, medium and high) affect users’ and gaming media reviews to provide insight on data-driven decision-making for game monetization and flexible pricing strategies. Finally, due to her little experience in games, Jen is interested in expanding and trying out more games. She hopes that by analyzing review trends, she can determine what the top games of the year were in 2023 to 2024 and give them a try.

As this study will be developed by four students studying data visualization, the intended audience would be those with some experience in data analysisg. The project will aim to answer the interests of the group members and show the general state of games on Steam within the last couple of years.

## About the data

#### Data Abstraction

| **Attribute Name**      | **Data Type** | **Data Semantics (Meaning)**          | **Cardinality / Range**  |
| ----------------------- | ------------- | ------------------------------------- | ------------------------ |
| **steam_appid**         | Categorical   | Unique identifier for the game        | 58041                    |
| **name**                | Categorical   | Game title                            | 57768                    |
| **developers**          | Categorical   | Game developers                       | 42018                    |
| **publishers**          | Categorical   | Game publishers                       | 34571                    |
| **categories**          | Categorical   | Game categories (e.g., FPS, Strategy) | 42                       |
| **genres**              | Categorical   | Game genres                           | 33                       |
| **required_age**        | Ordinal       | Minimum required age to play          | [0, 97]                  |
| **n_achievements**      | Quantitative  | Number of in-game achievements        | [0, 9821]                |
| **platforms**           | Categorical   | Platforms the game is available on    | 3                        |
| **release_date**        | Temporal      | Official release date                 | [1997-06-30, 2025-01-23] |
| **additional_content**  | Categorical   | DLCs and expansions available         | 7083                     |
| **total_reviews**       | Quantitative  | Total number of user reviews          | [0, 1279700]             |
| **total_positive**      | Quantitative  | Total number of positive reviews      | [0, 1107275]             |
| **total_negative**      | Quantitative  | Total number of negative reviews      | [0, 172425]              |
| **review_score**        | Ordinal       | Aggregate review score                | [0, 9]                   |
| **review_score_desc**   | Categorical   | Review score description              | 19                       |
| **positive_percentual** | Quantitative  | Percentage of positive reviews        | [0, 100]                 |
| **metacritic**          | Quantitative  | Metacritic score                      | [0, 97]                  |
| **is_free**             | Categorical   | Whether the game is free              | 2                        |
| **price_initial (USD)** | Quantitative  | Initial price of the game in USD      | [0, 999.98]              |

#### EDA

- General

  First, we created histograms to observe all the quantitative attributes. Since there were too many 0 values in most of the numerical columns, these values were filtered out to provide a clearer visualization.

  <center>Figure 1:</center>

  ![Figure 1:](/images/general/xz_hist_numerical_non_zero.png)

  Despite the filtering, some columns like `n_achievements`, `total_reviews`, `total_positive`, `total_negative`, and `price_intial` were extremely left-skewed.

  To view the outliers, we made boxplots for all the quantitative attributes.

  <center>Figure 2:</center>

  ![Figure 2:](/images/general/xz_boxplot.png)

  Again, we can see all columns were very left-skewed, while there were plenty of outliers on the right side.

  We created simple boxplots to display univariate summaries for all categorical variables. However, due to the sheer number of unique categories in some attributes, such as `name` and `developers`, we decided to limit our analysis to only account for the top 20.

  <center>Figure 3:</center>

  ![Figure 3:](/images/general/all_cat_EDA.png)

  Notable observations include `platforms`, where Windows dominates against all the other platforms, `review_score_desc`, where most games had no user reviews, and `is_free`, which revealed that the majority games on Steam are not free.

- Xueyong Zhang:

  For `developers`, `publishers`, `categories`, `genres`, `platforms`, there are lists in each cell since a game can belong to multiple categories and genres. To address this, I derived unique values from those columns and listed them out in cell 8 of the analysis.

  Then, I exploded the data for `genres` and `categories` columns separately and made a colored histogram for them, as those two columns are the primary focus of my research question:

  <center>Figure 4:</center>

  ![Figure 4:](/images/xz/xz_hist_genres.png)

  <center>Figure 5:</center>

  ![Figure 5:](/images/xz/xz_hist_categories.png)
  We can see games with Indie, Casual, Action, and Adventure genres are particularly numerous and all have relatively high average review scores. In comparison, games categorized as Single-player, Family Sharing, and Steam Achievements are also abundant but tend to have relatively low average review scores.

  Then, I made a heatmap to explore what combinations of game genres and categories were popular and occur together most frequently:

  <center>Figure 6:</center>

  ![Figure 6:](/images/xz/xz_heatmap.png)
  The popular categories and genres identified in the previous two histograms appear to have frequent combinations in the data.

  Finally, I created a scatter plot to explore the correlation between Metacritic scores and the percentage of positive reviews, as I hypothesize that these two variables are likely to show a positive correlation:

  <center>Figure 7:</center>
  	
    ![Figure 7:](/images/xz/xz_scatter.png)

  The plot reveals a positive correlation between Metacritic scores and the percentage of positive reviews, despite the significant number of 0 values in the Metacritic variable.

- Gurmandeep Bal:

   I transformed the data to better suit my needs, which includes making each category their own observed row. I also extracted the top 10 most producing developers.

  Then I dropped some of the categories which were not produced by at least a majority of developers since then it would not be a fair comparison among all developers. I also dropped categories that do not pertain to gameplay if they did not show up a lot among the top 10 (like HDR support)

  Finally, I graphed a visualization which showed the distribution of categories for each developer to see how many of each genre each developer produced. This helped me decide which categories to drop and will also assist in considering sample sizes as I dive deeper into my research question.

  <center>Figure 8: Distribution of categories for each developer</center>

  ![Figure 8:](/images/gSketches/catDev.png)

  I then did the same for each publisher to help consider the second research question. For all the same reasons above

  

  I also made a box plot to see the distribution of ratings for each developer to identify any potential outliers. Some developers have unusual distributions, which will need to be considered later when working on my research question. This was done for both the developer and publisher to help answer each respected research question

  <center>Figure 9: Ratings of Developers</center>

  ![Figure 9:](/images/gSketches/catBox.png)

  <center>Figure 10: Count of Achievements</center>

  ![Figure 10:](/images/gSketches/10.png)

  Then to help answer the last research question, I have created bar charts to show if the number of categories for the top and bottom developers have any impact on score

  <center>Figure 12: Impact of number of categories on score</center>

  ![Figure 11:](/images/gSketches/carRates.png)

- ZiXun Fang

  First, I further refined the clean data by removing unnecessary attributes and filtering the games include only those with at least 50 reviews. This threshold was set to exclude games with insufficient user feedback, as a lower number of reviews may not provide a reliable representation of a game's reception. I chose 50 reviews as a reasonable cutoff, given that most players on Steam do not leave reviews. Even with only 50 reviews, the game's rating can still offer meaningful insights.

  | **Price Group** | **Avg Positive Percentual** | **Avg Metacritic Score** |
  | --------------- | --------------------------- | ------------------------ |
  | Free            | 76.86                       | 72.78                    |
  | Low             | 81.90                       | 70.55                    |
  | Medium          | 82.56                       | 74.83                    |
  | High            | 80.95                       | 78.16                    |
  | Premium         | 77.69                       | 80.87                    |

  I then made an analysis table to show the average positive review percentage and average Metacritic scores. This will help me get an initial idea of the general ratings for each price category. From the table above we can tentatively tell that the price of the game has a positive effect on media ratings.

  <center>Figure 12:</center>

  ![Figure 12:](/images/zxDiagrams/correlation_heatmap.JPG)

  I also created a correlation heatmap to see the correlation coefficients between the selected attributes. If any of the attributes have a correlation coefficient that is too high or too low, I can consider not analyzing those attributes together.

      <center>Figure 103:</center>
  
  ![Figure 13b:](/images/zxDiagrams/bar_chart_eda1.png)
  
      <center>Figure 10c:</center>
  
  ![Figure 13c:](/images/zxDiagrams/bar_chart_eda2.png)

  Two bar charts above examine the relationship between gaming pricing and gamers' positive reviewing rates. Bar Charts clearly demonstrates that for gamers, the price of a game doesn't seem to be one of the things that influences their opinions of a game. This will help me focus on other factors in my subsequent research.

- Jen

  Since my area of interest is to look at the trending games from 2023-2024, I decided to explore and compare the positive and negative reviews against all the reviews Steam games have received.

      <center>Figure 14a and b:</center>

  ![Figure 14a and b:](/images/Jen/figure_1_eda.png)

  From the Total Positive Reviews to Total Reviews scatterplot (Figure 11a), there seems to be a positive correlation between total reviews on Steam and total positive reviews. Although most range from 0 to under 600,000 reviews and positive reviews, there is one game, Counter-Strike 2, that dominates at a high end of over a million reviews and positive reviews (Figure 11a). Interestingly, the developers for that game, Valve, are the same developers for Steam. Finally, the majority of the games are not free, but Counter-Strike 2 is free.

  In contrast, the Total Negative Reviews to Total Reviews scatterplot (Figure 11b) has much fewer reviews in general compared to Figure 11a. The graph also does not appear to have a distinct correlation between negative reviews and total reviews, with most of the games grouped together near the x-axis. Finally, similar to Figure 11a, Counter-Strike 2 dominates at the high end of the graph, with the only game having over 160,000 negative reviews (Figure 11b).

  Since most of the games in Figure 11b were clustered within the 0-20,000 range, I decided to apply a square root transformation to the data for better visualization.

      <center>Figure 12a and b:</center>

  ![Figure 15a and b:](/images/Jen/figure_2_eda.png)

  Comparing the Total Negative Reviews to Total Reviews Exponential Graph (Figure 12b) to the Total Positive Reviews to Total Reviews Exponential Graph (Figure 12a), I noticed that some of the games, such as Call of Duty and PUBG: BATTLEGROUNDS, had a low positive to negative review ratio of about 2:1 (Figure 12). In comparison, games like HELLDIVERS 2 exhibited a much higher ratio of 4:1 (Figure 12).

  Finally, I analyzed the games with the highest review scores relative to total reviews.

      <center>Figure 13a and b:</center>

  ![Figure 16a and b:](/images/Jen/figure_3_eda.png)

  Despite having a large number of total reviews, Counter-Strike 2 consistently maintains a high review score, ranging from 8.0 to 9.0 (Figure 13a). It is followed by Rust, Cyberpunk 2077, and Goobies, all of which also received review scores within the 8.0–9.0 range (Figure 13a).

  In contrast, the heatmap showing the percentage of positive reviews relative to total reviews (Figure 13b) reveals that Counter-Strike 2, Rust, and Cyberpunk 2077 fall within the 80-90% range, while Goobies stands out with a much higher percentage, between 90-100% (Figure 13b).

## Research Questions

- Xueyong Research question focus: Game genres and categories combination

  1. What combinations of game genres and categories are closely associated(appear together in a game)?
  2. What combinations of game genres and categories are easiler to success(gain possitive and total reviews, high score and media critique)?
  3. What combinations of game genres and categories are trending over years?

  As a UBC student who took CPSC 427: Video Game Programming, I have experience in video game development. But in the gaming industry, success goes beyond strong technical programming — it also depends on how different genres and categories of the game interact to shape player experience. I am particularly interested in exploring the relationship between game genres and categories to understand their impact on both commercial and critical success. I plan to measure success using key indicators such as total reviews, positive review percentage, and Metacritic scores. Analyzing these connections can offer valuable insights into game design trends and player preferences, benefiting both developers and publishers.

- Gurmandeep Research Question: Which genres a particular studio do well at making

  1. Which categories are most popular with the top 10 developers who made the greatest number of games.

  2. In general, do games with more achievements have more categories associated with them? And are games with more achievements good games?

  3. Does a game which has more categories associated with it do better than ones who meet few categories?


  My first two research questions will be to ask which categories do the top 10 studios and publishers who made the most number of games do well at making. Doing well can be determined by looking at the metacritic score, total positive score, looking at the positive score percentage, and looking at the number of achievements in the game. This is relevant and interesting as it will keep determining what categories a particular publisher is good at making, thus suggesting that the next game they make of the same category will also be good. This is feasible as the required data is available and novel as we have no metric for this question. This is ethical as this data was collected ethically.

  As for my third reaserch question, I want to see if games which focus on one defining feature are 'better' than jack of all trade games. Using the same metrics of 'good' as before, its realivant because should we be able to see some sort of trend with number of cetegories implying better or worse games, new games may be judged based on this factor. This is feasible as the required data is available and novel as we have no metric for this question. This is ethical as this data was collected ethically.


- ZiXun Research Question Focus: Indivisual Gamers Reviews vs. Media Reviews

1. Is there a significant difference in gamers and gaming media ratings for free,  low-paid, medium-paid, and high-paid games?
2. Is there a significant difference in gamers and gaming media ratings across different game categories?
3. Is there a significant difference in gamers and gaming media ratings between indie games and non-indie games?

  My research question aims to explore the relationship between game pricing strategies and positive reviews. Positive reviews will focus on the percentage of positive reviews on Steam and Metacritic scores. Despite the controversy surrounding gaming media ratings, such as those from IGN (Imagine Games Network - A giant gaming and entertainment media based in the U.S. It's renowned for its extensive coverage of video games, movies, TV shows and comics. IGN's game reviews are often controversial due to industry bias, political correctness and mismatched player expectations); I believe these ratings tend to be more objective than personal reviews, which can often be influenced by bias or negative sentiment toward other games. By examining this relationship, we can see if players have a higher tolerance for free or low-paid games. This insight could also help explain why some popular game publishers convert paid games into free-to-play titles.

- Jen Research question:
  What were the top 5 games of the year in 2023-2024 based on trends of ratings?

      As someone who always reads reviews before trying a game, I find that the general consensus often reflects the actual state of the game. This consistent observation sparked my interest in identifying the top 5 most popular games of 2023-2024 based on rating trends. To achieve this, I will analyze games with the highest average among a combination of factors: review scores, the ratio of positive to negative reviews, and the percentage of positive reviews, while also considering total reviews. This approach is feasible, as it relies on quantifiable metrics already provided by the dataset. These metrics also allow for meaningful comparison, providing insight into what drives a game's popularity. By determining which game has the highest count of positive reviews or review scores, a clear metric for popularity can be established.

      The question also carries a layer of sophistication, as it involves analyzing multiple attributes collectively rather than relying on a single factor, making it novel. Additionally, the question is inherently interesting as the results may be surprising, either showing a competitive tie near the top or a single game dominating. Since the data is publicly available, and the data itself is collected through Steam API, the study meets ethical standards. Finally, as this study revolves around the analysis of Steam games, this question is relevant towards understanding gaming trends and consumer behavior within the digital market.

## Task Analysis

Research Question 1: Identify 2024 game of the year based on rating trend
Task 1: Find Extremum
Which game in 2024 has the highest rating. We need to determine the highest-rated game of 2024 by aggregating ‘positive_percentual’ and ‘metacritic’. Media ratings usually have a greater impact on game awards, so we need to carefully consider the weighting between two attributes.

Task 2: Sort
Rank games by a composite score and group by date (month in 2024)

Research Question 2: Which genres a particular studio does well at making
Task 3: Cluster
Which game genres are indie game studios keen to produce?
How to tell if it's an indie game studio is an issue, and we may need additional ways to categorize the dataset.

Task 4: Compute Derived Value
What is the average rating (individual player ratings and media ratings) for all games during 2023-2024?

Task 5: Filter
Which are the top 10 studios that will produce the most games in 2023-2024, and what types of games do they produce?

Research Question 3: Is there a significant difference in users’ and gaming medias’ positive reviews for free, low-paid, medium-paid and high-paid games

Task 6: Cluster
Group games by price tiers (e.g. Free, 0-10, 10-30, 30-50 and 50+)
Are there some price tier games that exhibit a similar scoring structure?

Task 7: Find Anomalies
Detect characters of high-priced games (50+) with user scores significantly below media scores.

Task 8: Compare
Do free games have higher `positive_percentual` or `metacritic` scores than paid games? (compare with different price tier)

Research Question 4: Which genres are most frequently associated with key game categories (e.g., Multiplayer, Single-player, Co-op) and whether certain categories contribute to a game’s success.

Task 9: Correlate
Is there a correlation between game genres and success? Or we can say what genre-category pairs can more likely to be successful?
Map genre-category pairs (e.g., "Action + Multiplayer") to success metrics (positive_percentual). Use heatmap to find the correlation.

Task 10: Retrieve Value
What game genre or combination of game genres is mentioned the most between 2023-2024? How many times was the most mentioned game genre mentioned?

Distinct Tasks (9): Find Extremum, Sort, Cluster, Computer Drived Value, Filter, Find Anomalies, Compare, Correlate, Retrieve Value
Distinct Attributes (8): release_year, genres, price_category, positive_percentual, metacritic, total_reviews, positive_percentual, categories

## Preliminary Sketches

- Xueyong Zhang

  #### Low-fidelity Sketch 1:

  ![Low-fidelity Sketch 1:](/images/xz/xz_low_sketch1.png)
  Critique:
  The heatmap can end up having too many grids because there are 42 categories and 33 genres for the game. So there may be too many steps in the heatmap which may make the audience overwhelming and destructed. Furthermore, use a sequential color map for the number of games that fall in that category-genre combination loss accuracy because the number of games can range from 0 to 40000. However, only 15 combinations have the count above 10000. While most of the grids have a count difference just in a very small part of the color map, which is hard for viewers to tell their color difference even though their count has a significant difference. For example, in the heatmap I created in EDA, you can barely see the color difference in the grid with count 1 and the grid with count 500, while the count is significantly different. And because we used the color channel encoding count, it is hard to pick another channel to highlight the selected grid that the user focused on. On the other hand, for the line plot on the right side that focused on the game genre and category user selected. It is very beneficial to encode year on the x-axis. It provides time series information so that the audience can see the trend of certain game’s success metrics over years. Some genres and categories may have been popular several years ago but declined over the years. Audience can be informed of those trends by the time series line plot.

  #### Low-fidelity Sketch 2:

  ![Low-fidelity Sketch 2:](/images/xz/xz_low_sketch2.png)
  Critique:
  This visualization uses two histograms instead of heatmap to let the audience choose the genres and categories they want to focus on. Firstly it is less overwhelming and more intuitive for users to select. Secondly the highlight using color is more noticeable. Also the number of games is encoded by bar length instead of grid color lightness, which is more accurate. For the focused plot, instead of the time series line plot, the visualization uses pie charts to better show the portion of each field in categorical columns. It is clearer for the audience to get the proportion information such as the ratio of game with selected category in the game with selected genre; the ratio of review score level or the ratio of positive reviews. However, it misses the year information and numeric success metrics such as metacritic, initial price, total reviews(we can also show that in tooltip but that is not visualization anymore). So, less information is presented in the plot, and there can be too many pie charts if there are too many categorical success metrics.

  #### Low-fidelity Sketch 3:

  ![Low-fidelity Sketch 3:](/images/xz/xz_low_sketch3.png)
  Critique:
  This visualization requires the audience to select genres from drop down to combine with the category encoded in x axis. Also the audience can select from dropdown to make y axis encode different numerical columns and color encode different categorical data. The numerical data can be encoded using x axis with great accuracy and simplicity, which enable the audience to use less effort to digest the numerical information the visualization provided. However, for categorical data, the stacked bar chart has some drawbacks. Firstly, it is hard for users to derive the portion information from the chart. In addition, because the numerical data is encoded with bar height on y axis, the bar cannot be normalized, so the audience is harder to derive information from bars with small height, especially for categories with more fields(steps). And also the time information is missing so less information is presented in the visualization.

  #### High-fidelity Sketch:

  ![High-fidelity Sketch:](/images/xz/xz_high_sketch.png)
  Explanation:
  The two selection histograms in the bottom enable two charts above to focus on specific combinations of categories and genres of games, which uses select in visualization manipulation and user interaction. In the histograms, categories and genres are encoded by x axis and sorted by y axis value, each bar represents a type in the categorical data. The game count is encoded by y axis as the bar length, length is a good channel to encode quantitative data and there is alignment at the bottom so it accurately reflects the game count data. Finally, the color highlights the selected combinations of categories and genres to focus on the two charts above, and also classify the different combination groups by distinct color hue and the legend on the right side, this adheres to the Enclosure / Common Region principle that makes the audience draw attention to groups of category-genres combinations.
  For the focused charts above, we encode categorical columns in the pie chart color and the portion of each type of the column as area in the circle, and encode numerical columns in the line chart as the y coordinate of the points in the line. This adheres to the Effectiveness principle that most effective channels are selected for numerical and categorical data. Also, in the line chart, different combinations selected in the histograms are encoded by different lines with different color hues. This adhered to the superimpose in the facet chart so that the audience can compare the trends of multiple combinations by lines with different colors.
  And the line chart is interactive so that the line chart will show a vertical line on where the auidence have thier mouse hover on, and show the number of the x axis value of each line intersect with the vertical line. This enables auidence to have an accurate number for a specifc year. Also, the user can zoom in and out, and pan on the chart to change the range of y axis, to change the range of years showed on the line chart, the change will also apply to the two selection histograms so that the histogram only shows the year range limited by the line chart. So there is a bidirectional linking between two selection histograms and the line chart: selection histograms can select the lines showed on the line chart, and the line chart can change the year range filtered on the selection histograms.

- Gurman

  #### Low-fidelity Sketch 1:

  ![](/images/gSketches/1.jpg)

  One critique of this graph is that it is perhaps too simple. But it is important in determining how to take in account how many games a particular developer/studio makes. Without any colour it could be hard to distinguish the bars but this is ment to just be a simple glance of the data. Another critique is that by having many studios in a line, the time it takes for eyes to scan from one end to another may hinder the time it takes to interpret the data.

  #### Low-fidelity Sketch 2:

  ![](/images/gSketches/7.jpg)

  Here we have a faceted view of all the studios and all the different categories each one has compared to the avg user rating for all of them. Given that each genre will be coloured, it could end up being too much data shown to the user as there are likely to be 30 or so coloured bars that will be displayed. With this large amount of things to view, this could also increase the time it takes a reader to interpret everything. However it will be useful to determine which studio has the most popular games belonging to a genre.

  #### Low-fidelity Sketch 3:

  ![](/images/gSketches/3.jpg)

  Here we have a boxplot which shows the overall positive and negative views for all games from a particular studio as well as a line showcasing the metacritic score to serve as a baseline seeing the difference between critic and general audience scores. One critique of the boxplots is that it could be confusing to look at many of them and compare, as well as it could be difficult to interpret any statistic from them. This is rectified by having a drop down so one may only look at 1 studio at a time to compare the metrics.

  #### High-fidelity Sketch:

  ![](/images/gSketches/8.jpg)

  In this high fidelity sketch which compares the avg score based on category for each studio (for simplicity, I have made one but this will be done across all 10 studios). This figure adheres to the theoretical principles since its interactive, does not have too many colours, is simple to view and a lot of data can be interpreted from it
  

- ZiXun Fang

  #### Low-fidelity Sketch 1:

  ![Low-fidelity Sketch 1](/images/zxDiagrams/1.JPG)

  The bar chart can effectively show the distribution of games across different price zones, but it doesn’t directly show whether price affects game ratings. I should add more dimensions like average rating per category in the bar chart to show whether certain categories tend to have higher or lower ratings.

  #### Low-fidelity Sketch 2:

  ![Low-fidelity Sketch 2:](/images/zxDiagrams/2.JPG)
  The box plot can effectively show the distribution of positive review percentages across different price tiers. We can know median, variance, and outliers for each price zone, but I should bold some lines like median or a trend line for better comparison and readability improvement. Right now, it is still hard to compare different price categories.

  #### Low-fidelity Sketch 3:

  ![Low-fidelity Sketch 3:](/images/zxDiagrams/3.JPG)
  The line chart effectively shows the trend of positive percentual across all prices. However, the chart can only show the overall trend. Sometimes, the data may not be a linear trend, and it is hard to compare different groups. It would be much better to segment them by different price zones or colour them by different price zones.

  #### High-fidelity Sketch:

  ![High-fidelity Sketch:](/images/zxDiagrams/4.JPG)
  The high-fidelity sketch is a combination of low-fidelity sketches and more dimensions. Not every game has both review points and Metacritic scores, so we added a pie chart to show the percentage of these two types of games. The combination of different charts provides both a distribution of context and treating trends. We add some bottoms, like years and different metric values, to switch diagrams in a single chart. This interactive element allows viewers to explore specific price ranges or categories. The chart on the right is a more detailed chart within each price zone. The problem with this chart is that it is only categorized by price zone a categorical data. In the future, we would like to do additional categorization according to some processed game genres (in each game genre, we will study the effect of price on the rating).

- Jen

  #### Low-fidelity Sketch 1:

  ![Low-fidelity Sketch 1:](/images/Jen/low_fidelity_1.png)

  A simple starting point is to use a histogram to compare the number of reviews or positive reviews a game has, thus is the first low-fidelity sketch idea. However, while this provides a direct and basic overview and is a great starting point for all users, it lacks depth. It does not account for the percentage of positive and negative reviews, which helps the understanding of whether a game left a positive or negative impression based on review ratios. Additionally, the histogram offers little context about the game itself, such as its genre or developer, which could provide deeper insights into trends and user sentiment.

  #### Low-fidelity Sketch 2:

  ![Low-fidelity Sketch 2:](/images/Jen/low_fidelity_2.png)

  This figure uses a bubble plot to show the review scores against total reviews, aggregated by game count. It shows slightly more information than the first low-fidelity sketch, but review scores are not enough to determine whether a game is popular or not. Despite this limitation, the tree-map offers a unique and visually engaging approach, appealing to users who appreciate less conventional visualizations.

  #### Low-fidelity Sketch 3:

  ![Low-fidelity Sketch 3:](/images/Jen/low_fidelity_3.png)

  This figure uses a scatterplot to showcase the total positive, negative, and review scores against total reviews. This sketch was based on Figure 11a and 11b. It also incorporates color to show whether a game is free or not, adding a multivariate element. The scatterplot is useful in identifying trends in reviews based on these three quantifiable metrics, and by placing them side-by-side, they become easily comparable. However, to make meaningful comparisons, these metrics will need to be normalized. To enhance this visualization further, a tooltip could be added to provide additional context and expand the information displayed. Despite these improvements, the lack of a combined metric still makes it challenging to pinpoint the highest trending games.

  #### High-fidelity Sketch:

  ![High-fidelity Sketch:](/images/Jen/high_fidelity.png)

  By incorporating the ideas from the low-fidelity sketches, the idea behind the high fidelity sketch is to feature an interactive graph with aggregation. First, the ratios for positive to negative reviews against total reviews for the top 1000 games will be normalized and computed. Using this data, there will be one bubble chart to show the review ratio against total reviews with the size of each bubble representing the count of games within each section. A threshold slider will be added, where a scatterplot will be shown as the slider is moved, showing the position of each individual game. Finally, a tooltip will be added to show additional information about each individual game, including whether the game is free, the developers, the game name, and its genre.

## Next Steps

| **Plan**    | **Xueyong**                                                                                                                                                | **Gurmandee**                                                                                                                                              | **ZiXun**                                                                                                                                                  | **Jen**                                                                                                                                                    |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Week 10** | 1. Apply the feedback to other reasearch questions and sketches 2. Start implementing the visualization using Altair 3. polish report                      | 1. Apply the feedback to others reasearch questions and sketches 2. Start implementing the visualization using Altair 3. polish report                     | 1. Apply the feedback to others reasearch questions and sketches 2. Start implementing the visualization using Altair 3. polish report                     | 1. Apply the feedback to others reasearch questions and sketches 2. Start implementing the visualization using Altair 3. polish report                     |
| **Week 11** | 1. Keep implementing the visualization using Altair 2. Provide feedback on others visualization 3. sharing progress, avoid similarities on each others vis | 1. Keep implementing the visualization using Altair 2. Provide feedback on others visualization 3. sharing progress, avoid similarities on each others vis | 1. Keep implementing the visualization using Altair 2. Provide feedback on others visualization 3. sharing progress, avoid similarities on each others vis | 1. Keep implementing the visualization using Altair 2. Provide feedback on others visualization 3. sharing progress, avoid similarities on each others vis |
| **Week 12** | 1. Finish up implementing visualization 2. merge my PR and review otheres PR 3. Prepare the deliverables for PM3                                           | 1. Finish up implementing visualization 2. merge my PR and review otheres PR 3. Prepare the deliverables for PM3                                           | 1. Finish up implementing visualization 2. merge my PR and review otheres PR 3. Prepare the deliverables for PM3                                           | 1. Finish up implementing visualization 2. merge my PR and review otheres PR 3. Prepare the deliverables for PM3                                           |
| **Week 13** | 1. Deploy all visualizations on web 2. prepare for prsentation                                                                                             | 1. prepare for prsentation                                                                                                                                 | 1. prepare for prsentation                                                                                                                                 | 1. prepare for prsentation                                                                                                                                 |
| **Week 14** | 1. Prepare the deliverables for PM4. 2. present and demo visualizations                                                                                    | 1. Prepare the deliverables for PM4. 2. present and demo visualizations                                                                                    | 1. Prepare the deliverables for PM4. 2. present and demo visualizations                                                                                    | 1. Prepare the deliverables for PM4. 2. present and demo visualizations                                                                                    |

## References

Manhães, S. (2025, January 27). Steam games dataset 2025. Kaggle.
https://www.kaggle.com/datasets/srgiomanhes/steam-games-dataset-2025

Steam, the ultimate online game platform. Steam, The Ultimate Online Game Platform. (n.d.).
https://store.steampowered.com/about/

Steam usage and catalog stats for 2025. Backlinko. (2025, January 31).
https://backlinko.com/steam-users
