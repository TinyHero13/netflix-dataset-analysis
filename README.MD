# Netflix Dataset Analysis

An exploratory data analysis (EDA) of the Netflix catalog using **DuckDB**, **Pandas**, and **Plotly**. The project covers data cleaning, deduplication, transformation, and answering key business questions through SQL queries and interactive visualizations.

> **Note:** Since Plotly charts are interactive, they don't render on GitHub. For the best experience, view the full notebook on Google Colab:
> [Open in Google Colab](https://colab.research.google.com/drive/15XLKWOjrphG7lSvQEA7ffv5xBciRl5LJ?usp=sharing)

---

## Dataset

The dataset (`netflix.csv`) contains **7,789 rows** and **11 columns** describing movies and TV shows available on Netflix.

### Data Dictionary

| Column | Description |
|---|---|
| `Show_Id` | Unique identifier for each show |
| `Category` | Content type: `Movie` or `TV Show` |
| `Title` | Title of the show |
| `Director` | Director(s) of the show |
| `Cast` | Cast members |
| `Country` | Country of origin |
| `Release_Date` | Date the show was added to Netflix |
| `Rating` | Age rating (e.g., TV-MA, PG-13, R) |
| `Duration` | Runtime in minutes (movies) or number of seasons (TV shows) |
| `Type` | Genre tags (e.g., Dramas, Comedies, Documentaries) |
| `Description` | Synopsis of the show |

---

## Tech Stack

- **[DuckDB](https://duckdb.org/)** — in-process SQL analytics engine for fast data querying and transformation
- **[Pandas](https://pandas.pydata.org/)** — data manipulation and inspection
- **[Plotly](https://plotly.com/python/)** — interactive charts and visualizations

---

## Data Cleaning

- **Duplicate removal:** Identified and removed 2 duplicate rows using DuckDB's `QUALIFY row_number()` window function.
- **Date formatting:** Converted `Release_Date` from a string (e.g., `"January 8, 2021"`) to a proper `DATE` type using `strptime`.
- **Year extraction:** Added a `Year` column extracted from `Release_Date` for easier time-based analysis.

---

## Questions Answered

1. **House of Cards** — What is the show ID and who directed it?
2. **Year with the most releases** — Visualized with a bar chart and a line chart.
3. **Movies vs. TV Shows** — Count breakdown shown with bar and pie charts.
4. **All titles released in 2000** — No data found for that year.
5. **Indian TV Shows** — Listed all 71 TV shows from India.
6. **Top 10 directors** — Directors with the most content on Netflix, split by movies and TV shows.
7. **Filtered records** — Shows where `Category = Movie AND Type = Comedies` OR `Country = United Kingdom`.
8. **Tom Cruise filmography** — Found 2 movies: *Rain Man* and *Magnolia*.
9. **Age ratings** — Listed all 14 distinct ratings; `TV-MA` is the most common (2,863 titles).
10. **Canadian TV-14 movies** — 26 films found.
11. **TV Shows rated 'R' after 2018** — Only 1: *The Hateful Eight: Extended Version*.
12. **Maximum duration** — Longest movie: 312 minutes; longest TV show: 16 seasons.
13. **Country with most TV Shows** — United States (866), followed by the United Kingdom (256) and Japan (184).
14. **Sorted by year** — Dataset ordered from most recent to oldest releases.
15. **Combined filter** — Movies with Dramas OR TV Shows tagged as Kids' TV (2,520 results).

---

## Visualizations

| Chart | Description |
|---|---|
| Bar chart | Releases per year |
| Line chart | Release trend over time |
| Bar + Pie chart | Movies vs. TV Shows distribution |
| Bar chart | Age rating distribution |
| Horizontal bar chart | Top content types by category |
| Bar chart (Top 10) | Longest movies and TV shows by duration |
| Histogram | Duration distribution for movies and TV shows |

---

## Key Insights

- **2019** was the peak year for Netflix content additions (2,153 titles).
- **Movies** account for ~69% of the catalog; **TV Shows** make up ~31%.
- **TV-MA** is the most common age rating, representing ~37% of all content.
- **Jan Suter** and **Raúl Campos** are the most prolific directors on the platform.
- **The United States** dominates both movie and TV show production on Netflix.
- Brazil has **29 TV shows** in the catalog.
