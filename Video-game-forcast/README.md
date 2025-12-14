# TripleTen Integrated Project - Video Game Sales Forecasting

This was my first integrated project in the TripleTen Data Science program. It brought together everything I had learned so far — from data cleaning and preprocessing to exploratory analysis, visualization, and hypothesis testing — in a real-world case study. I enjoyed applying my skills to a dataset that reflects the global video game industry.

### Video Game Sales

The goal of the project was to identify patterns that determine whether a game succeeds or not. By analyzing historical sales data, platforms, genres, and review scores, I built a forecasting model to spot potential big winners and plan advertising campaigns for 2017.

#### The Data

The dataset contained information on video games released up to 2016, with the following features:

- `Name`: Title of the video game  
- `Platform`: Console or system (e.g., Xbox, PlayStation, Nintendo)  
- `Year_of_Release`: Release year  
- `Genre`: Category of the game (e.g., Action, Sports, RPG)  
- `Publisher`: Company that released the game  
- `NA_sales`, `EU_sales`, `JP_sales`, `Other_sales`: Regional sales figures (in USD millions)  
- `Global_sales`: Total worldwide sales (calculated as the sum of all regions)  
- `Critic_Score`: Review score from critics (0–100)  
- `User_Score`: Review score from users (0–10)  
- `Rating`: ESRB age rating (e.g., Teen, Mature)  

The dataset was provided by TripleTen, adapted from Kaggle’s public dataset. Data for 2016 may be incomplete.

#### The Process

- **Data preparation:**  
  - Standardized column names and converted data types  
  - Handled missing values and TBD entries with clear documentation  
  - Created a new column for total global sales  

- **Exploratory analysis:**  
  - Examined release trends across years and platforms  
  - Compared platform lifecycles (emerging vs. declining)  
  - Built box plots to compare global sales distributions by platform  
  - Analyzed correlations between critic/user reviews and sales  

- **Regional profiles:**  
  - Identified top platforms and genres in NA, EU, and JP  
  - Compared ESRB rating effects across regions  

- **Hypothesis testing:**  
  - Tested whether average user ratings of Xbox One and PC were the same  
  - Tested whether average user ratings for Action and Sports genres differed  
  - Applied statistical methods (variance, standard deviation, t-tests) with clear null/alternative hypotheses  

### Results

Explaining my results at each step was a key part of the process. I found that:

- Certain platforms (e.g., PlayStation, Xbox) dominated global sales, while others declined over time.  
- Genres like Action and Sports consistently drove higher sales, though regional preferences varied.  
- Critic and user scores showed measurable correlation with sales, especially on popular platforms.  
- ESRB ratings influenced sales differently across regions, with Mature-rated games performing better in NA/EU than in JP.  
- Hypothesis testing confirmed differences in user ratings between genres, while platform ratings were more similar than expected.  

This project gave me valuable experience in combining EDA, visualization, and statistical testing to produce actionable insights.  

Please have a look at the Jupyter Notebook included for a full description of results.
