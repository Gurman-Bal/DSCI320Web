### Gurmandeep Bal

#### Question 1:
The research goal of this visualization is to answer: does a game higher with the existence of a certain category? This visualization shows that there does seem to be a difference in score when certain categories exist. Notice that the area under the single-player line, Multiplayer line, and Co-op line seem to be larger on the right-side end of the graph where the higher rated game is compared to the center of the graph where mediocre games exist.

I have chosen a line graph to show the trends of the review scores as we progress from lower end games to higher end ones. This is compared to the Total count of the all the total reviews that exist for each score point. The color channel is based on the Category type. The Bar chart and Pie chart help supplement this view by showing the total number of categories which exist as there could be an over representation bias. There does seem like there is way more single player games than any other category, however the rest of the categories share equal space. There are two interactions that exist here, first is that we can click and select any category to show just color just for that category. Second is that our dropdown allows us to have a blown-up view of a particular category on the line graph.

This view could be made better by having a reset button to return a chosen dropdown state to the original view. The line graph also has a large exasperation at score = 0 due to the shear number of games that have been rated at this score. One solution would be to just ignore this as the difference between a 1 game and 0 game is negligible and perhaps have a different graph comparing the that point for each category separately while cleaning up the main view of the line chart.

<center>Figure 1:</center>

![Figure 1:](/images/gSketches/ms3_1.png)

#### Question 2:

The research goal of this visualization is to answer: In general, do games with more achievements have more categories associated with them? And are games with more achievement good games? This visualization shows that there does seem to be a difference where higher rated games tend to lean towards having more categories than the lower ranked games. This is noticed by how the area of the top-rated games have a sizable shift towards the higher end of the x axis compared to the lower rated games chart. This can also be shown by the bottom graph as one can see the movement of data from one side to the other as we go from lower rated games to higher rated ones. 

I have chosen area graphs to represent the number of categories on the x axis vs the total amount of achievements on the y axis. I have done this since there is so much data, other marks could become too cluttered and confusing. The color mark is then used to show how much each area belongs to a certain rating of games. This allows us to see the trends of how high rated games tend to behave given these two variables. To take a closer look at each individual score, another chart was added to show the same data but for one score rating at a time, which can be controlled by a slider. Essentially the top graphs can show us a holistic view while the bottom one can help see a more precise look to help us answer the question. 

This view could be made better by having perhaps lines which also show where the Metacritic score falls onto this data and see if any comparisons can be made from that. Also, perhaps instead of stacked area charts, maybe if they were facted instead it would make the visualization look a bit cleaner.

<center>Figure 2:</center>

![Figure 2:](/images/gSketches/ms3_2.png)

#### Question 3:

The research goal of this visualization is to answer: Does a game which has more categories associated with it do better than ones who meet few categories?  This visualization shows that there does seem to be a difference as the higher rated games tend to contain more categories than the lower rated ones. This is noticed by how the density of the top-rated games has a much longer tail to the higher counts of categories than the lower rated ones.

I have chosen density graphs as since I am using most of the large dataset, this would be an excellent way to showcase large data in an interpretable way. The density is comprised of the count of categories that each game has based on the count again for the x axis. Then to show how the scores compare to the counts, a bar chart with radio buttons will show the trend of the scores in the data. This graph shows that good games tend have a large range of how many categories they tend to have. The pie chart shows how many games have a particular number of categories, which allows us to see if there are any data significance to take into consideration. The bar chart and the pie chart are using this color theme since it allows us to more easily distinguish between sections while also showing ordinal progression.

This view could be made better by having a different view for the pie chart since some of the slices are very thin and are not as visible. There could also be more interactivity where we could be able to control the size of the data for the density to see how sample size effects this finding.


<center>Figure 3:</center>

![Figure 3:](/images/gSketches/ms3_3.png)

### Xueyong Zhang

#### Research Question Focus: Game genres and categories combination

1. What combinations of game genres and categories are closely associated(appear together in a game)?

2. What combinations of game genres and categories are easiler to gain possitive reviews and high score?

3. What combinations of game genres and categories are trending over years?

#### DashBoards:

##### View 1 for Research Question 1:

![Dashboard_view_1_xz:](/images/xz/view_1.gif)

##### **Explaination**:

On the left side, the heatmap enables the audience to get the records of games of all combinations of genres and categories, genres and categories are encoded by x and y axis and sorted by the rank of number of games that falls in the column(genre or category). They are also filtered by the range selector to show only top genres and categories by their rank, which make sure there won't be too many steps in the heat map which cause overwhelming and distraction. The number of games which are quantitative is binned and encoded by color channel by the brightness of color, which adheres to the *Effectiveness* principle because the nature of brightness of color represents ordinal data(binned quantitative data). And the audience can select the grid on the heatmap to make the two pie charts on the right side to focus on the selected genre and category respectively. The selected genre and category are highlighted by stroke on the pie chart, highlighted by stroke and opacity on the heatmap. This adheres to the *popup* and *grouping* characteristic. In the pie charts, categories and genres(categorical) are encoded by color, and their portion of game records(quantitative) are encoded as the area(or angle) in the circle, this adheres to the *Effectiveness* principle again because the right type of data are encoded by the effective channels. Finally, there are tooltips on heatmap and pie charts that show the exact number of games, which make up for the lack of accuracy of color brightness and area channels.

##### View 2 for Research Question 2:

![Dashboard_view_2_xz:](/images/xz/view_2.gif)

##### **Explaination**:

On the left side, there are two histograms which encode categories and genres using the x axis and sorted by y axis respectively. The number of games is encoded by y axis using the length channel, length is a good channel to encode quantitative data and there is alignment at the bottom so it accurately reflects the game count data by comparing the top of bars. They enable the audience to select categories and genres by clicking the bar. There is a bi-directional linking between two histograms: each histogram will reflect the other’s histogram’s selection result so that they are also focused on the category(or genre) that the other histogram selected. The selected bar uses color brightness channel to encode review score which is ordinal. So the bar shows the review score distribution sorted: by position from the bottom to top, review score from the lowest(0) to highest(10), and color from bright and dark. This adhere to the *Grouping* and *Effectiveness* principle. On the right side, the histogram shows the distribution of review score description of the game with specific genre and category selected by two left side histograms. We can multi-select the bar to filter out the game with that kind of review score description in the two left side histograms, the selected bars are grey in color so it is clear to the audience that they are filtered out. This enables the audience to filter out games that have 0 or low reviews in the histogram so that we know if the low review scores in the bar are due to no or few sample sizes. Finally, there are tooltips on all histograms that show the exact number of games, review score and review score description, which makes the audience clearer to see the details even though the area in the bar is small and makes up for the lack of each area’s accuracy in the stacked bar.

##### View 3 for Research Question 3:

![Dashboard_view_3_xz:](/images/xz/view_3.gif)

##### **Explaination**:

Similarly to dashboard view 2, there are two histograms that enable users to select specific genre and category, the differences are: (1) they are side by side in the bottom in position. (2) there is no review score encoded in the histogram by color brightness because it is not helpful for this research question, so the channel is removed to prevent distraction and overwhelming. (3) There are range selection bars to enable users to select the top ranked categories and genres included in the histogram instead of including all categories and genres(however, the audience still has the option to show all by clicking the checkbox). This reduced the steps in the histogram where adhere to the *Discriminability* characteristic. In the line chart above, the loess value is computed in order to get a smooth trend and encoded by a thunk line with high opacity, and mean value encoded by a thin line with low opacity because it fluctuates by time more but represents the original data in more details. And the line chart is interactive so that the line chart will show a vertical line on where the audience has their mouse hover on, and show the number of the x axis value of the loess line intersecting with the vertical line. This enables the audience to have an accurate number for a specific time. Also, the user can zoom in and out, and pan on the chart to change the range of y axis, to change the range of time shown on the line chart, the change will also apply to the two selection histograms so that they only show the year range limited by the line chart. So there is a bidirectional linking between two selection histograms and the line chart: selection histograms can select the lines shown on the line chart, and the line chart can change the year range filtered on the selection histograms.


#### Tasks summaries:

- Retrieve Value: retrieve the average positive review percentual for specific genre and category of game in a specific time point.
- Filter: filter only the specific game genre and category, and time range.
- Compute Derived Value: the losse value of positive review percentual for specific genre and category of game in a specific time point. The count of game for every combination of genre and category. The count and percentual of different review scores for each game genre and category.
- Find Extremum: When does each game with specific genre and category have the highest average positive review percentual over time.
- Sort: rank game genre and category by number of games.
- Characterize Distribution: What is the distrubution of review scores for games with different genre and category
- Cluster: Is there any clusters of genres and categories that usaually appear together in a game.


### ZiXun Fang

#### Tasks: Cluster, Find Anomalies, Compare

The violin plot successfully cluster games into four price tiers: free, low, medium and high. These plots reveal rating distributions within each price group, making readers easy to identify similar scoring structure and compare differences in reviews between gaming medias and players.

All three visualizations don't directly accomplish this task, but we can find violin distributions of those games that have extreme values (e.g. average gamer review <= 2 or total number of reviews > 100000) by using brush in scatterplots. 

All three visualizations accomplish compare tasks. Violin plots focus on the comparison between different price groups. We can compare the difference in gamer ratings between different price groups of games, and we can also compare the difference in gamer ratings and media ratings for the same price group. Scatterplot and barchart focus on comparing the difference between gamer ratings and media ratings for indie and non-indie games. Scatterplot also looks at the link between ratings and game popularity.

#### Final Visualization Dashboard

<center>Dashboard_ZiXun:</center>

![Dashboard_ZiXun:](/images/zxDiagrams/final_viz_interactions_1.gif)

#### Research Question 1: How do rating distributions from users and gaming media compare across different price tiers, and what does this reveal about valuation of games at various price points?

The goal of this visualization is to explore how game ratings from both users and media vary across different price tiers.

I chose violin plots because they provide rich information about distribution shapes that simple bar charts or box plots couldn't capture. The violin's width at any given y-value represents the density of observations at that rating, making it easy to identify rating clusters. For marks, I used area marks to show distribution density, while y-axis encodes the primary quantitative variable (rating scores). Horizontal position separates the four price categories, and color distinguishes between price tiers for additional visual reinforcement.

The interactive components allow readers to further explore these relationships. The brush selection on scatter plots filters these violin plots to show distributions for specific subsets of games. The indie/non-indie radio buttons enable comparing how these price-rating relationships differ between indie and non-indie titles.

The chart could be improved by adding reference lines for median values. It would make direct comparisons between price groups more precise, but I haven't figured out how to add layers in each plot.

#### Research Question 2: Is there a significant difference in gamers and gaming media ratings across different game categories, and how does this vary between indie and non-indie games?

I designed bar charts that display average ratings for different game categories, with color encoding distinguish between indie and non-indie games. The reason I chose the bar chart is that it helps readers to clearly see the difference between gamer ratings and media ratings for the same game category, and the trend of ratings for all game categories in the respective ratings. 

The bar charts use rectangle marks with vertical position encoding the average rating and horizontal position representing different game categories. Interactive elements include category hover highlighting, which emphasizes specific categories across both charts when hovering, and the indie/non-indie filter that shows how ratings change when focusing on specific game types. These interactions can direct the reader's attention to key comparisons.

The current visualization has limitations in the readability of category labels due to their diagonal orientation and overlap. One possible improvement is to use drop-down to display fewer categories at a time. Another way is to set a width slider for the bar chart to improve readability.

#### Research Question 3: Is there a significant difference in how gamers and gaming media rate indie games compared to non-indie games across different levels of popularity as measured by total review counts?

The goal of this visualization is to explore the relationship between game popularity (as measured by the total number of reviews) and ratings. The scatterplot helps the reader to clearly see if there is a clear trend between the total number of reviews and the game ratings. Unfortunately, according to the scatterplot we can see that there is no clear relationship between game popularity and ratings, and that the ratings of some games that are continuously updated may change due to new content.

The review count slider filters games by popularity, allowing examination of rating patterns across different popularity thresholds. The brush selection enables focusing on specific regions of the popularity-rating space, with those selections propagating to the violin plots. Additionally, the year slider allows temporal filtering to account for potential rating trends over time. Games that do not meet the threshold are made transparent to allow readers to better focus on the games they filter out. These interactions are important in this plot because they also affect other visualizations to analyze different scenarios.

The scatterplot could be further optimized, for example by adding separate trend lines for indie and non-indie games to more clearly show the differences in scoring patterns.


### Jen Wang

#### Research Question Focus: Most popular Steam games

<center>Dashboard_Jen:</center>

![Dashboard_Jen:](/images/Jen/viz_1.png)

This visualization aims to answer what the top 5 games of the year in 2023-2024 based on total number of reviews. It incorporates a scatterplot and a histogram to analyze patterns in top trending games on Steam from 2023-2024. The data has been filtered to only include games that have over 10,000 reviews, as any less than that would not be very indicative that the game is popular. The histogram provides an overview of the distribution of positive review percentages across all games, which allows users to easily assess the overall sentiment trends. Meanwhile, the scatterplot maps is more detailed. It maps total reviews on the x-axis and the positive-negative review ratio on the y-axis. Each point on the scatterplot represents a game, and brushing over a group of points reveals a detailed table with additional metadata, such as the developers, genres and review score descriptions.
The histogram is encoded using bar marks with the x-axis representing binned positive review percentages and the y-axis showing the count of games within each bin. This choice leverages the position channel, which is preattentive and allows for effective comparison of relative frequencies. By implementing brushing selection, users can interactively highlight sections of the histogram, filtering the scatterplot to show only games that fall within a specified positive review range. A bidirectional linking is implemented with the scatterplot, where the brushing selection highlights points on the scatterplot that correlate to the highlighted positive percentual bar.
To answer the question, the top 5 games ranked first by total reviews, with review ratio as a secondary criteria, are highlighted in red to draw immediate attention to them. All other points are initially grayed out but turn blue when selected via brushing, reinforcing interactive focus and ensuring that user-defined subsets remain visually distinguishable.
The table view encodes categorical data using text marks, appearing only when points from the scatterplot are interacted with. This on-demand detail prevents visual clutter while maintaining information hierarchy.
The visualization can use several improvements. A legend clarifying red-highlighted games as the top 5 could provide additional context without requiring users to infer from color alone. Additionally, the bidirectional linking between the histogram and the scatterplot is yet to be fully implemented properly and requires further improvement. Finally, properties, such as width and height can be adjusted so the visualization sits fully in view in one frame.


<center>Dashboard_Jen:</center>

![Dashboard_Jen:](/images/Jen/viz_2.png)

This visualization is extremely similar to the first visualization, however it answers the question of top 5 trending games based on positive-negative review ratio as the main criteria, and total reviews as the secondary criteria. It shares the same critiques as the visualization above.
Finally, the table helps answers the metadata trends of the popular games based on each criteria. As there is no graph or plot that can represent so many categorical attributes at once, the table is the best option. However, the properties of the table can be adjusted so the text appears in one full window view.
This visualization is extremely similar to the first visualization, however it answers the question of top 5 trending games based on positive-negative review ratio as the main criteria, and total reviews as the secondary criteria. It shares the same critiques as the visualization above.
Finally, the table helps answers the metadata trends of the popular games based on each criteria. As there is no graph or plot that can represent so many categorical attributes at once, the table is the best option. However, the properties of the table can be adjusted so the text appears in one full window view.



