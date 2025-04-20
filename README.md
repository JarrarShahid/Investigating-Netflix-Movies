# Investigating-Netflix-Movies

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)  
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-orange.svg)  
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)  
![Status: Complete](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

A Jupyter Notebook for exploratory data analysis (EDA) of Netflix movies released in the 1990s. You’ll dive into a rich dataset of titles, filter for 1990s movies, and uncover insights on durations, genre‐specific patterns, and more.

---

## 📌 Project Overview

Netflix, founded in 1997, evolved from DVD rentals into a streaming giant. This notebook is part of a production‐company research effort focusing on **nostalgic 1990s movies**. We perform EDA to understand:

- How many Netflix movies were released in the 1990s  
- Duration patterns (mean, median, mode, min/max)  
- Most common duration  
- Prevalence of short (< 90 min) Action movies  

---

## 📂 Dataset: `netflix_data.csv`

A comma‐separated file containing metadata for all Netflix titles.

| Column        | Description                                  |
|---------------|----------------------------------------------|
| `show_id`     | Unique show identifier                       |
| `type`        | “Movie” or “TV Show”                         |
| `title`       | Name of the title                            |
| `director`    | Director(s)                                  |
| `cast`        | Main cast members                            |
| `country`     | Country of origin                            |
| `date_added`  | Date added to Netflix                        |
| `release_year`| Year the title was released                  |
| `duration`    | For movies: minutes; for TV shows: seasons   |
| `description` | Brief synopsis                               |
| `genre`       | Primary genre(s)                             |

---

## ⚙️ How It Works

The analysis notebook (`notebook.ipynb`) follows these steps:

1. **Load libraries & data**  
   ```python
   import pandas as pd
   import matplotlib.pyplot as plt
   df = pd.read_csv("netflix_data.csv")

2. Filter 1990s movies
   ```python
   movies = df[(df['type'] == 'Movie') & (df['release_year'] >= 1990) & (df['release_year'] <= 1999)]

3. Count total movies in 1990s
   ```python
   print(f"Total number of movies in the 1990s: {len(movies)}")

4. Compute duration stats
   ```python
   movies['duration_minutes'] = movies['duration']
   print(movies['duration_minutes'].describe())

5. Plot histogram
   ```python
   plt.figure(figsize=(10, 6))
   plt.hist(movies['duration_minutes'].dropna(), bins=30, color='skyblue', edgecolor='black')
   plt.title('Distribution of Movie Durations (1990s)')
   plt.xlabel('Duration (minutes)')
   plt.ylabel('Number of Movies')
   plt.show()

6. Find most common duration
   ```python
   most_common_duration = movies['duration_minutes'].mode()[0]
   duration = int(most_common_duration) 
   print(f"Most common movie duration in the 1990s: {duration} minutes")

7. Short Action movies (< 90 min)
   ```python
   short_action_movies = movies[(movies['duration_minutes'] < 90) & (movies['genre'].str.contains('Action', na=False, case=False))]
   short_movie_count = len(short_action_movies)
   print(f"Number of short action movies (less than 90 minutes): {short_movie_count}")

---

## 🚀 Getting Started

1. Clone this repo
   ```
   git clone https://github.com/JarrarShahid/Investigating-Netflix-Movies.git
   cd Investigating-Netflix-Movies
   ```
2. Install dependencies
   ```
   pip install pandas matplotlib jupyter
   ```
3. Launch the notebook
   ```
   jupyter notebook notebook.ipynb
   ```
---

## 🧑‍💻 Author

Built by a Software Engineer who enjoys creating useful tools that help people make better everyday decisions.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.







































