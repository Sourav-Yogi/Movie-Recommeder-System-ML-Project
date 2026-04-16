# 🎬 Movie Recommender System

A content-based movie recommendation web app built with Python, Streamlit, and the TMDB API. Select any movie and instantly get 5 similar recommendations with posters fetched live from The Movie Database.

---

## 📸 Demo

> Select a movie → Click "Show Recommendation" → See 5 similar movies with posters.

---

## 🚀 Features

- Content-based filtering using cosine similarity
- Movie posters fetched live via TMDB API
- Interactive UI built with Streamlit
- Secure API key management via `.env`

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas / NumPy | Data processing |
| Scikit-learn | CountVectorizer + Cosine Similarity |
| NLTK | Porter Stemmer for text normalization |
| Streamlit | Web UI |
| TMDB API | Fetch movie posters |
| Pickle | Model serialization |

---

## 📁 Project Structure

```
Movie Recommender System/
│
├── app.py                  # Streamlit frontend app
├── movieRecommender.ipynb  # Model building notebook
├── movie_list.pkl          # Pickled movie dataframe
├── similarity.pkl          # Pickled similarity matrix
├── .env                    # API key (never commit this!)
├── .gitignore
└── README.md
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/your-username/movie-recommender-system.git
cd movie-recommender-system
```

### 2. Install dependencies
```bash
pip install streamlit requests pandas numpy scikit-learn nltk python-dotenv
```

### 3. Get a TMDB API Key
1. Sign up at [https://www.themoviedb.org/signup](https://www.themoviedb.org/signup)
2. Go to **Settings → API → Create → Developer**
3. Copy your API key

### 4. Create a `.env` file
In the root of the project, create a `.env` file:
```
TMDB_API_KEY=your_api_key_here
```

### 5. Generate the model files
Run the Jupyter notebook `movieRecommender.ipynb` top to bottom. This will generate:
- `movie_list.pkl`
- `similarity.pkl`

> **Dataset required:** Download `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` from [Kaggle TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) and place them inside an `archive/` folder.

### 6. Run the app
```bash
streamlit run app.py
```

---

## 🧠 How It Works

1. **Data Merging** — The movies and credits datasets are merged on the `title` column.
2. **Feature Extraction** — Key features (genres, keywords, cast, crew, overview) are combined into a single `tags` column.
3. **Text Normalization** — Tags are stemmed using NLTK's `PorterStemmer` to reduce words to their root form.
4. **Vectorization** — `CountVectorizer` converts tags into a bag-of-words matrix (top 5000 features).
5. **Similarity** — Cosine similarity is computed between all movie vectors.
6. **Recommendation** — For a selected movie, the top 5 most similar movies are returned.

---

## 🔐 Environment Variables

| Variable | Description |
|---|---|
| `TMDB_API_KEY` | Your personal TMDB API key |

---

## ⚠️ Important Notes

- Never commit your `.env` file to GitHub. Add it to `.gitignore`.
- The `similarity.pkl` file can be large (~100MB+). Consider adding it to `.gitignore` and regenerating locally.
- If posters fail to load, check that your TMDB API key is valid and active.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).