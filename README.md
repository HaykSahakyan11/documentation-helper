# 🦜 LangChain Documentation Helper

<div align="center">

**My implementation of the LangChain documentation assistant: RAG over the LangChain docs, built with LangChain, Tavily, Pinecone and Streamlit**

<br>

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![LangChain](https://img.shields.io/badge/LangChain-🦜🔗-green.svg)](https://langchain.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B.svg)](https://streamlit.io/)
[![Pinecone](https://img.shields.io/badge/Pinecone-🌲-orange.svg)](https://pinecone.io/)
[![Tavily](https://img.shields.io/badge/Tavily-🔍-purple.svg)](https://tavily.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

[![udemy](https://img.shields.io/badge/Based%20on%20the%20LangChain%20Udemy%20Course-by%20Eden%20Marco-green)](https://www.udemy.com/course/langchain/)

</div>

## 🎯 Overview

The **LangChain Documentation Helper** is my take on the project from Eden Marco's [LangChain Udemy course](https://www.udemy.com/course/langchain/). It is a slim version of [chat.langchain.com](https://chat.langchain.com/): an AI-powered web app that answers questions about the LangChain documentation using Retrieval-Augmented Generation (RAG), with Tavily-based crawling and an agent that decides when to retrieve context and cites its sources.

Many thanks to [Eden Marco](https://github.com/emarco177) for the excellent course and the original [reference repository](https://github.com/emarco177/documentation-helper). This repo is my own implementation and follow-along of it.

### ✨ Key Features

**RAG Pipeline Flow:**

1. 🌐 **Web Crawling**: Site mapping and content extraction using Tavily (`TavilyMap` + `TavilyExtract`)
2. 📚 **Document Processing**: Chunking of the LangChain documentation with `RecursiveCharacterTextSplitter`
3. 🔍 **Vector Storage**: Embeddings (`text-embedding-3-small`) indexed in Pinecone for fast similarity search
4. 🎯 **Intelligent Retrieval**: A retrieval tool the agent calls to fetch the most relevant documentation chunks
5. 🧠 **Context-Aware Generation**: LangChain agent (`create_agent`) that answers using the retrieved context, with source citations
6. 💬 **Interactive Interface**: Chat UI powered by Streamlit, with an expandable list of sources per answer
7. 🚀 **Real-time Processing**: Fast end-to-end pipeline from query to response

## 🛠️ Tech Stack

<div align="center">

| Component | Technology | Description |
|-----------|------------|-------------|
| 🖥️ **Frontend** | Streamlit | Interactive chat interface |
| 🧠 **AI Framework** | LangChain 🦜🔗 | Orchestrates the agent and retrieval pipeline |
| 🔍 **Vector Database** | Pinecone 🌲 | Stores and retrieves document embeddings (Chroma supported for local use) |
| 🌐 **Web Crawling** | Tavily | Site mapping and content extraction |
| 🤖 **LLM** | OpenAI GPT | Powers the conversational AI |
| 🐍 **Backend** | Python | Core application logic |

</div>

## 🚀 Quick Start

### Prerequisites

- Python 3.11
- [Pipenv](https://pipenv.pypa.io/)
- [OpenAI API key](https://platform.openai.com/api-keys)
- [Pinecone API key](https://app.pinecone.io/) and an index named `langchain-doc-index`
- [Tavily API key](https://app.tavily.com/) (required - for documentation crawling)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/HaykSahakyan11/documentation-helper.git
   cd documentation-helper
   ```

2. **Set up environment variables**

   Create a `.env` file in the root directory:
   ```env
   PINECONE_API_KEY=your_pinecone_api_key_here
   OPENAI_API_KEY=your_openai_api_key_here
   TAVILY_API_KEY=your_tavily_api_key_here  # Required - for documentation crawling
   ```

3. **Install dependencies**
   ```bash
   pipenv install
   ```

4. **Ingest LangChain Documentation** (Run the ingestion pipeline)
   ```bash
   pipenv run python ingestion.py  # Uses Tavily to crawl and index documentation
   ```

5. **Run the application**
   ```bash
   pipenv run streamlit run main.py
   ```

6. **Open your browser** and navigate to `http://localhost:8501`

## 📁 Project Structure

```
documentation-helper/
├── backend/                          # Core backend logic
│   └── core.py                       # Retrieval tool, agent and run_llm()
├── chroma_db/                        # Local vector database (optional Chroma setup)
├── main.py                           # Streamlit application entry point
├── ingestion.py                      # Document ingestion pipeline
├── logger.py                         # Logging utilities
├── Tavily Demo Tutorial.ipynb        # 📚 Tutorial: Introduction to Tavily API
├── Tavily Crawl Demo Tutorial.ipynb  # 📚 Tutorial: Advanced Tavily crawling techniques
├── LICENSE                           # MIT License
└── Pipfile, Pipfile.lock             # Dependencies
```

### 📚 Tutorial Notebooks

The project includes Jupyter notebooks from the course that serve as hands-on tutorials:

- **`Tavily Demo Tutorial.ipynb`**: Introduction to Tavily API basics and core functionality
- **`Tavily Crawl Demo Tutorial.ipynb`**: Advanced tutorial covering Tavily's crawling capabilities, including TavilyMap and TavilyExtract features

## 🔧 Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `PINECONE_API_KEY` | Your Pinecone API key for vector storage | ✅ |
| `OPENAI_API_KEY` | Your OpenAI API key for LLM access | ✅ |
| `TAVILY_API_KEY` | Your Tavily API key for documentation crawling | ✅ |

## 📚 Learning Resources

This project is my hands-on way of learning:
- 🦜 LangChain framework and agent implementation
- 🔍 Vector search and embeddings
- 💬 Conversational AI development
- 🏗️ RAG (Retrieval-Augmented Generation) architecture

## 🙏 Credits

- **[Eden Marco](https://github.com/emarco177)** - author of the [LangChain Udemy course](https://www.udemy.com/course/langchain/) and the original project this one is based on
- [LangChain](https://langchain.com/), [Tavily](https://tavily.com/), [Pinecone](https://pinecone.io/) and [Streamlit](https://streamlit.io/) for the tooling

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🌟 Support

If you find this project helpful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting issues
- 💡 Suggesting improvements

---

<div align="center">

### 🔗 Connect with Me

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/HaykSahakyan11)

**Built by Hayk Sahakyan, based on the course by Eden Marco**

</div>
