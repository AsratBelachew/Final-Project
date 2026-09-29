# Capstone - Movie Recommendation System

This project builds a content-based movie recommendation system using movie genres and user-generated tags. TF-IDF converts the combined text features into numerical vectors, and cosine similarity identifies movies with similar content. 

MovieLens Latest Small was selected because it contains movie metadata, genres, user ratings, and tags. It is suitable for both content-based recommendations and an optional collaborative/quality signal.

The included dataset is for development and education. See data/raw/README.txt for source and license information.
## Project deliverables

- `notebooks/movie_recommendation_system.ipynb` - complete, executed analysis
- `data/raw/` - MovieLens CSV files and data documentation
- `data/processed/movie_features.csv` - prepared item features
- `outputs/recommendations_toy_story.csv` - sample Top-10 results
- `outputs/eda_summary.csv` - key data statistics
- `reports/Capstone8_Summary_Report.pdf` - two-page project report
- `reports/figures/` - charts used in the notebook and report

## Dataset

MovieLens Latest Small was created by GroupLens Research at the University of Minnesota.

- Dataset page: https://grouplens.org/datasets/movielens/latest/
- Direct ZIP: https://files.grouplens.org/datasets/movielens/ml-latest-small.zip
- Size used: 9,742 movies, 610 users, and 100,836 ratings

The data files are included so the notebook runs immediately. See `data/raw/README.txt` for usage terms.

## Installation

1. Install Python 3.10 or newer.
2. Open a terminal in the project folder.
3. Install the packages:

```bash
pip install -r requirements.txt
```

4. Start Jupyter:

```bash
jupyter notebook
```

5. Open `notebooks/movie_recommendation_system.ipynb` and select **Run All**.

## Method

1. Load and validate `movies.csv`, `ratings.csv`, and `tags.csv`.
2. Explore users, movies, ratings, sparsity, and genre frequency.
3. Combine each movie's genres and normalized tags.
4. Create a TF-IDF item-feature matrix.
5. Calculate cosine similarity between a selected movie and all other movies.
6. Optionally blend 85% content similarity with 15% Bayesian rating quality.
7. Return Top-N movies with shared-genre/tag explanations.

## Example

The executed notebook recommends ten movies similar to `Toy Story (1995)` and saves them to CSV. To try another movie:

```python
find_titles("matrix")
recommend_movies("Matrix, The (1999)", top_n=5)
```

## Main findings

- The rating matrix is 98.30% sparse, supporting a content-based approach for items with metadata.
- Drama and Comedy are the most frequent genres.
- Recommendations are interpretable because every row states its shared genres or tags.
- The rating blend favors reliable, well-rated movies while keeping content similarity dominant.

## Limitations

Metadata may be incomplete, broad genres can produce similar scores, and the model does not fully learn an individual user's taste. Future work could add user profiles, matrix factorization, richer metadata, and Precision@K evaluation.

## Reproducibility

The notebook uses fixed input files and deterministic calculations. Run all cells from top to bottom to regenerate every processed file, table, and figure.

