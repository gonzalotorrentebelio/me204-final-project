# ME204 Final Project: [Popular movies across the Decades]


| GitHub username                           | LSE ID            |
| ----------------------------------------- | ----------------- |
| `gonzalotorrentebelio`                    | `250099860`       |



Remove the unused row if you work alone.
Replace every `[bracketed]` placeholder once you fill it in.

## The question

How have the most popular movies changed across the decades (1960–2020) in terms of genres, runtime, and rating?

## Key findings

Across the 1,220 most-voted films of 1960–2020, popular cinema changed in *form*, not in favour:

- Genres flipped from drama to action. Drama fell from ~22% of genre mentions in the 1960s to ~5% by the 2020s (−17.4 pts); Action rose from ~4% to ~20% (+15.9 pts).
- Runtime is U-shaped. Average length dipped to 109.3 min in the 1980s, then climbed to a peak of 124.9 min in the 2010s.
- Ratings stayed flat. Decade means held inside a narrow 7.11–7.40 band, so audiences' average verdict barely moved.

## Data source

All data comes from the [TMDB API](https://developer.themoviedb.org/) (The Movie Database), a public authenticated API. The project collects, for each year in the range:

- the genre reference table,
- the most-voted movies of that year (`/discover/movie`),
- the full details of each of those movies (`/movie/{id}`), including runtime.
- All classnotes from the LSE course (slides from the lectures, syllabus notes on moodle)


No static/manually-downloaded dataset is used; the API is the sole and main source.

This product uses the TMDB API but is not endorsed or certified by TMDB.

## Setting up the environment

I used Python 3.10. To install what the notebooks need:

```bash
pip install -r requirements.txt
```

## Making a key

1. Create a free account at [themoviedb.org](https://www.themoviedb.org/) and request an API key: Settings → API → Request an API Key (Developer).
2. Copy `.env.example` to `.env` and paste your key:

   ```
   TMDB_API_KEY=your_key_here
   ```

`.env` is git-ignored, so the real key is never committed. `.env.example` shows the required variable without any secret.

## Order to run things

Run the notebooks top to bottom, and in this order (I usually do Restart Kernel then Run All so the cell numbers come out clean):

| Order | File | Reads | Does | Writes |
| ----- | ---- | ----- | ---- | ------ |
| 1 | `notebooks/NB01-Data-Collection.ipynb` | TMDB API (needs `.env`) | Collects the genres, the most-voted movies per year, and the details of each movie | Raw JSON in `data/raw/tmdb/` |
| 2 | `notebooks/NB02-Data-Transformation.ipynb` | `data/raw/tmdb/` | Cleans the raw files into two tidy tables, one row per movie and one row per movie-genre (using `explode`) | `data/processed/movies.csv`, `data/processed/movie_genres.csv` |
| 3 | `notebooks/NB03-gonzalotorrentebelio-Data-Analysis.ipynb` | `data/processed/` | Explores runtime, genres and ratings by decade | Figures in `docs/assets/`, plus the printed findings |

NB01 and NB02 can be re-run safely. If a file is already on disk they just reuse it instead of downloading again.

## Notes on decisions

- CSV over SQLite: two tidy tables are enough for this analysis, so CSV is used rather than adding a database only for appearance.
- `explode` for genres: a movie has several genres at once; the long `movie_genres` table makes per-decade genre counts straightforward.
- Missing values: unknown runtimes/budgets (stored as `0` by TMDB) are converted to `NaN` in NB02 so they do not distort averages.

## AI use

I used Claude while working on this. Mainly to help finish the README from my own draft, to tidy up some of the code (helper functions, print formatting, the plots), for translation, and to sort out the folder structure. I checked the code myself and confirmed every number in the findings against my own data, so the analysis and the conclusions are mine.