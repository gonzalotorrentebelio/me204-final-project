# ME204 Final Project: [Popular movies across the Decades]


| GitHub username                           | LSE ID            |
| ----------------------------------------- | ----------------- |
| `gonzalotorrentebelio`                    | `250099860`       |
| `[second username, if working in a pair]` | `[second LSE ID]` |


Remove the unused row if you work alone.
Replace every `[bracketed]` placeholder once you fill it in.

## The question

How have the most popular movies changed across the decades (1960–2020) in terms of genres, runtime, and rating?

## Key findings

Across the 1,220 most-voted films of 1960–2020, popular cinema changed in *form*, not in *favour*:

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