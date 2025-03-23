# 🎬 Enhancing Search Engine Relevance for Video Subtitles (Shazam for Subtitles)

## 📌 Project Overview
In the digital content era, improving search relevance for video subtitles can enhance accessibility and content discoverability. This project builds an **AI-powered subtitle search engine**, enabling users to retrieve subtitles by providing an **audio snippet** from a movie or TV series. The system supports both **keyword-based** and **semantic search** methods to improve accuracy.

## 🚀 Features
- **Audio-Based Search:** Users provide a **2-minute audio clip**, and the system retrieves relevant subtitles.
- **Keyword-Based Search:** Implements **TF-IDF & BOW** for exact text matches.
- **Semantic Search:** Uses **BERT-based SentenceTransformers** for context-aware results.
- **Efficient Data Storage:** Stores subtitle embeddings in **ChromaDB** for fast retrieval.
- **Cosine Similarity Matching:** Finds the most relevant subtitle snippets based on embeddings.

## 🏗️ Architecture
1. **Data Ingestion:**
   - Read and preprocess subtitle data from `eng_subtitles_database.db`.
   - Clean subtitle text (remove timestamps, unwanted characters, etc.).
   - Convert subtitles into **vector embeddings**.
   
2. **Vectorization Methods:**
   - **TF-IDF / BOW** for keyword-based search.
   - **BERT-based embeddings** for semantic search.
   - **Document Chunking:** To avoid information loss, subtitles are divided into overlapping chunks before embedding.

3. **Database Storage:**
   - Store embeddings in **ChromaDB** for quick access.

4. **Query Processing:**
   - Convert the user’s **audio query to text** using **Whisper AI**.
   - Generate embeddings for the query.
   - Compute **cosine similarity** to find relevant subtitles.

## 🔧 Tech Stack
- **Programming Language:** Python
- **Database:** SQLite, ChromaDB
- **Libraries:** Pandas, NumPy, Scikit-learn, re, sqlite3
- **NLP Techniques:** TF-IDF, BERT (SentenceTransformers)
- **Audio Processing:** OpenAI Whisper

## 📂 Dataset
- The subtitle data is stored in `eng_subtitles_database.db`.
- Contains a table `zipfiles` with:
  - `num`: Unique subtitle ID
  - `name`: Subtitle file name
  - `content`: Binary compressed subtitle file (encoded in 'latin-1')

## 📜 Installation & Setup
```bash
# Clone the repository
git clone https://github.com/your-username/subtitle-search-engine.git
cd subtitle-search-engine

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
```

## 🏃‍♂️ Usage
```python
python main.py  # Start the search engine
```

## 📌 Future Enhancements
- **Integrate Speech-to-Text API** for better transcription accuracy.
- **Enhance Chunking Strategy** to improve contextual understanding.
- **Deploy as a Web App** using FastAPI or Streamlit.

## 🤝 Contributing
Feel free to fork the repo and submit pull requests to improve the project!

