\# Amazon Prime Video – Exploratory Data Analysis



An exploratory data analysis of the Amazon Prime Video catalogue, done in Python with Pandas, Matplotlib and Seaborn. I looked at what the catalogue contains, how it has grown over time, how titles are rated, and where the data is incomplete, and I turned the results into suggestions for a streaming business.



\## Project Overview



This is an individual project. The dataset has information on nearly 10,000 movies and TV shows, including content type, release year, genres, production countries, runtime, age certification, IMDb scores and votes, and TMDB popularity and scores. A second dataset lists the people (actors and directors) connected to each title.



\## Business Objective



Streaming platforms compete by growing and improving their content libraries. The objective of this project is to find patterns in the Amazon Prime Video catalogue that can support content decisions.



\## Dataset



\- `titles.csv`: one row per title, with `id`, `title`, `type`, `description`, `release\_year`, `age\_certification`, `runtime`, `genres`, `production\_countries`, `seasons`, `imdb\_id`, `imdb\_score`, `imdb\_votes`, `tmdb\_popularity` and `tmdb\_score`.

\- `credits.csv`: the people connected to each title, with their role (actor or director).



Source: AlmaBetter



\## What I Did



\*\*Understanding the data\*\*

\- Loaded both datasets and checked their shape, data types and duplicates.

\- Visualised missing values with a heatmap and a bar chart, and read the meaning of each column before deciding what to do with the gaps. Some are expected, for example `seasons` is empty for movies.



\*\*Preparing the data\*\*

\- Checked that every title `id` is unique.

\- Converted `genres` and `production\_countries` from text to Python lists with `ast.literal\_eval()`, then used `explode()` so a title with several genres or countries is counted once under each.

\- Created a `release\_decade` column from `release\_year`.

\- Kept missing values instead of dropping or filling them blindly. In the age-certification charts, missing values are shown as "Not Rated".

\- Treated very long runtimes as possible outliers to investigate, not as errors to delete.



\*\*Analysis\*\*

I made 15 charts that cover:

\- Catalogue composition: content type, genres, production countries, age certifications

\- Trends over time: titles by release year, movies vs TV shows by year

\- Ratings and popularity: IMDb and TMDB ratings by type, IMDb vs TMDB, votes vs score, score and runtime distributions, a correlation heatmap and a pair plot



\## Key Findings



\### Movies far outnumber TV shows

!\[Distribution of movies and TV shows](images/01\_content\_type.png)



The catalogue has about 8,500 movies and about 1,350 TV shows, roughly 86% to 14%.



\### Drama and Comedy lead the genres

!\[Top 10 genres](images/02\_top\_genres.png)



Drama is the biggest genre with about 4,750 titles, followed by Comedy (about 3,000), Thriller, Action and Romance. A title with several genres is counted under each one.



\### Most titles are produced in the United States

!\[Top 10 production countries](images/03\_production\_countries.png)



The United States leads with about 5,300 titles, followed by India (about 1,070), the United Kingdom (about 930) and Canada (about 530). Countries are shown by their country codes.



\### The catalogue is full of recent content

!\[Titles released by year](images/04\_release\_trend.png)



Releases stay low for most of the 20th century, then climb steeply from the 2000s and peak around 2021 at about 850 titles. The sharp drop in the final year is probably because the data for that year is incomplete, so I did not read it as a real decline.



\### IMDb and TMDB scores move together, but not perfectly

!\[IMDb score vs TMDB score](images/05\_imdb\_vs\_tmdb.png)



Titles with higher IMDb scores generally have higher TMDB scores, but there is a wide spread around the trend.



\### Correlation between the numerical variables

!\[Correlation heatmap](images/14\_correlation\_heatmap.png)



IMDb and TMDB scores have a moderate positive correlation (0.58). Release year and seasons are negatively correlated (-0.41). IMDb votes and TMDB popularity are only weakly related (0.26), and runtime has almost no relationship with ratings (about -0.10).



\### Other findings from the notebook

\- TV shows have a higher average IMDb and TMDB rating than movies in this dataset.

\- Titles with many IMDb votes do not necessarily have the highest scores, so popularity and rating measure different things.

\- A large part of the catalogue has no age certification.



\## Recommendations



\- Keep a balanced and varied content portfolio. Movies are the majority, so adding high-quality TV shows could improve variety and long-term engagement.

\- Use the genre, country, rating and popularity insights when deciding what to acquire or produce. Less-represented genres and countries are chances to diversify.

\- Do not judge content by ratings or vote counts alone. Look at ratings, popularity and engagement together.

\- Improve metadata completeness, especially age certification, to support better recommendations and audience targeting.



\## Limitations



\- The data counts titles, not viewing, so it shows what is in the catalogue and not what people watch.

\- IMDb and TMDB scores are audience ratings and only indicate quality roughly.

\- The credits dataset is loaded and checked, but the actors and directors are not analysed in this notebook.



\## Tools



Python, Pandas, NumPy, Matplotlib, Seaborn, Google Colab



\## Repository Structure



```

amazon-prime-video-python-eda/

│

├── Datasets/

│   ├── titles.csv

│   └── credits.csv

│

├── Notebook/

│   └── Amazon\_Prime\_Video\_EDA.ipynb

│

├── images/

│   ├── 01\_content\_type.png

│   ├── 02\_top\_genres.png

│   ├── 03\_production\_countries.png

│   ├── 04\_release\_trend.png

│   ├── 05\_imdb\_vs\_tmdb.png

│   └── 14\_correlation\_heatmap.png

│

├── requirements.txt

└── README.md

```



\## How to Run



1\. Clone or download the repository and keep the folder structure as it is.

2\. Install the libraries: `pip install -r requirements.txt`

3\. Open `Notebook/Amazon\_Prime\_Video\_EDA.ipynb` and run the cells from top to bottom. The notebook reads the data from `../Datasets/`, so run it from inside the `Notebook` folder.



In Google Colab, upload `titles.csv` and `credits.csv` and change the two paths in the data-loading cell to the uploaded file names.



\## Author



Vaibhav Deshmukh



vaibhavd8080@gmail.com

