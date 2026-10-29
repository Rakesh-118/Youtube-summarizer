# 🎬 YouTube Summarizer & RAG Chatbot

An AI-powered content assistant built with **Streamlit, LangChain, Google Gemini, Groq, and FAISS** that summarizes YouTube videos and web pages, then allows users to ask questions about the extracted content using Retrieval-Augmented Generation (RAG).

## 🚀 Features

- **YouTube Video Summarization:** Extracts video transcripts and generates concise, structured summaries.
- **Website Summarization:** Loads website content and summarizes it using chunk-based processing.
- **RAG-Powered Chatbot:** Ask questions about the processed content and receive context-based answers.
- **Semantic Search:** Uses Hugging Face embeddings and FAISS for efficient similarity search.
- **Interactive Interface:** Provides a Streamlit interface with separate summarization and chatbot sections.
- **Content Management:** Clear processed data or load new content without restarting the application.
- **Progress Indicators:** Displays processing status and progress while summarizing web pages.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core application logic |
| Streamlit | Interactive web interface |
| LangChain | LLM orchestration and RAG pipeline |
| Google Gemini (Gemma) | Content summarization |
| Groq (Llama 3.1 8B Instant) | Context-based question answering |
| Hugging Face Embeddings | Text vectorization |
| FAISS | Vector storage and similarity search |
| YouTube Transcript API | YouTube transcript extraction |
| WebBaseLoader | Website content extraction |
| RecursiveCharacterTextSplitter | Splitting content into manageable chunks |
| python-dotenv | Environment variable management |

## 🏗️ How It Works

### 1. Content Extraction
The application accepts a YouTube video URL or a website URL.

- For YouTube videos, it extracts the available transcript.
- For websites, it loads the page content using LangChain's `WebBaseLoader`.

### 2. Summarization
The extracted text is passed to a Google generative AI model to produce a readable summary. Website content is split into chunks and summarized individually.

### 3. Text Embeddings
The extracted content is split into smaller chunks and converted into vector embeddings using the `all-MiniLM-L6-v2` Hugging Face model.

### 4. Vector Storage
FAISS stores the embeddings and enables similarity-based retrieval of relevant content.

### 5. Question Answering
When a user submits a question:

1. The retriever searches for relevant content chunks.
2. The retrieved context is passed to the Groq-hosted Llama model through a LangChain retrieval chain.
3. The model generates an answer grounded in the retrieved content.

## 📂 Project Structure

```text
Youtube-summarizer/
└── Summarizer-with-RAG-Chatbot/
    ├── app.py
    ├── README.md
    └── requirements.txt
```

> The structure above reflects the current folder arrangement. You can move the three files to the repository root later if you want the app to run directly from the root directory.

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.10 or later (depending on dependency compatibility)
- Git
- A Google AI API key
- A Groq API key
- An internet connection

### 1. Clone the Repository

```bash
git clone https://github.com/Rakesh-118/Youtube-summarizer.git
cd Youtube-summarizer
```

If your project files remain inside the nested directory shown above, run:

```bash
cd Summarizer-with-RAG-Chatbot
```

### 2. Create a Virtual Environment

**Windows:**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the same directory as `app.py`:

```env
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_google_api_key
HUGGINGFACE_API_KEY=your_huggingface_api_key
```

Replace the placeholder values with your actual API keys.

**Security:** Never commit your `.env` file or expose API keys in your source code. Add `.env` to `.gitignore` before pushing your project to GitHub.

### 5. Run the Application

```bash
streamlit run app.py
```

Streamlit will provide a local URL, usually `http://localhost:8501`, where you can access the application.

## 📖 Usage

1. Launch the application.
2. Paste a YouTube video URL or a website URL into the input field.
3. Click **Summarize YouTube Video** or **Summarize Webpage**.
4. Read the generated summary.
5. Use the chatbot panel to ask questions about the processed content.
6. Clear the existing content or process another URL when needed.

### Supported Sources

- YouTube videos with accessible transcripts or captions.
- Public web pages accessible to the application.
- Articles, blog posts, and documentation pages.

## 🔑 API Configuration

| Variable | Purpose |
|---|---|
| `GOOGLE_API_KEY` | Access to Google's generative AI service |
| `GROQ_API_KEY` | Access to the Groq-hosted Llama model |
| `HUGGINGFACE_API_KEY` | Hugging Face API authentication, if required by your configuration |

The embedding model used in the code is `all-MiniLM-L6-v2`. Depending on the environment, it may be downloaded locally without a Hugging Face API key.

## ⚠️ Limitations

- YouTube videos must have transcripts or captions accessible through the transcript API.
- Some websites may block automated content extraction.
- Summary quality depends on the source content and the selected language models.
- API rate limits, service availability, and network connectivity may affect processing.
- The current implementation processes content in session state; persistent storage across application restarts is not configured.
- The chatbot is designed to answer questions using the currently processed content.

## 🔮 Future Improvements

- Add support for uploading PDF and text documents.
- Store chat history and enable multi-turn conversations.
- Improve transcript extraction and error handling.
- Add support for multiple languages.
- Introduce caching to reduce repeated API calls.
- Add automated tests for summarization, extraction, and retrieval components.
- Deploy the application to a cloud hosting platform.

## 🤝 Contributing

Contributions, suggestions, and bug reports are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a pull request describing your improvements.

## 📄 License

No license has been specified yet. Add an appropriate open-source license if you intend to allow others to reuse, modify, or distribute this project.

---

**Built with Python, LangChain, Streamlit, and generative AI.**
