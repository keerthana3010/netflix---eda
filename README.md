# Netflix Content Analysis

Exploratory data analysis of the Netflix catalogue: what it contains, how fast it grew, where it comes from and who it is made for.

Built as the **Data Science Mini Project** for the Codomax Digital Solutions programme.

**Author:** Keerthana R

## Problem statement

Netflix's catalogue is large and changes constantly. This project cleans a public dataset of Netflix titles and answers six questions:

1. How is the catalogue split between movies and TV shows?
2. How has the pace of new additions changed over the years?
3. Which countries, genres and audience ratings dominate?
4. How long are movies, and how many seasons do TV shows run?
5. When are titles added, and how old are they when they arrive?
6. How does India compare with the other big contributors?

## Dataset

- **Netflix Movies and TV Shows**, 7,787 titles and 12 columns (type, title, director, cast, country, date added, release year, rating, duration, genres, description).
- Original source: Kaggle, *Netflix Movies and Television Shows* by Shivam Bansal. The copy in `data/` comes from the TidyTuesday repository (2021-04-20).
- The data is a snapshot that runs to January 2021.

## Approach

1. **Load and inspect:** shape, missing values, duplicates.
2. **Clean:** parse `date_added`, fill missing director, cast, country and rating with `"Unknown"`, split `duration` into movie minutes and TV seasons, take the first listed country as the primary country, group 14 rating codes into five audience groups, and expand multi-genre titles into one row per genre.
3. **Explore:** 12 visualizations built with matplotlib and seaborn, each titled with the finding it shows.
4. **Summarise:** key numbers, insights, limitations and next steps at the end of the notebook.

## Key findings

| Finding | Number |
|---|---|
| Movies vs TV shows | 69% / 31% |
| Titles added per year, 2016 to 2019 | 443 to 2,153 (about 4.9x) |
| Titles released in 2015 or later | 70% |
| Share of titles from the top 3 countries (US, India, UK) | 61% |
| Top genres | Dramas (movies), TV Dramas (TV) |
| Adult-rated titles | 47% of movies, 42% of TV shows |
| Median movie length | 98 minutes |
| TV shows with only one season | 67% |
| Busiest / quietest month for additions | December / February |
| Titles added within 2 years of release | 64% |

**India:** second-largest contributor with 956 titles (92% movies). 64% of its titles are Dramas, and its movies have a median length of 127 minutes against 93 for the other top-8 countries.

![Titles added per year](images/02_added_per_year.png)

![Country and genre heatmap](images/11_country_genre_heatmap.png)

## Limitations

- Snapshot data to January 2021, so 2021 is excluded from yearly trends.
- Only titles still on Netflix at that time are included, so "added per year" does not count titles that were later removed.
- Co-productions are counted once, under the first listed country.
- A title can have several genres, so genre counts add up to more than the number of titles.
- 31% of titles have no director listed (mostly TV shows).
- The analysis is descriptive: it shows what the catalogue looks like, not why.

## Project structure

```
netflix-eda/
├── netflix_eda.ipynb     # full analysis with outputs
├── data/
│   └── netflix_titles.csv
├── images/               # charts saved by the notebook
├── requirements.txt
└── README.md
```

## How to run

```bash
git clone <your-repo-url>
cd netflix-eda
pip install -r requirements.txt
jupyter notebook netflix_eda.ipynb
```

Run all cells from top to bottom. The notebook reads `data/netflix_titles.csv` and writes charts to `images/`.

## Tools

Python, pandas, NumPy, matplotlib, seaborn, Jupyter.
