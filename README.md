# YouTube-RAG-FAISS-OpenRouter-QA
Youtube video helper Agent

# YouTube RAG Assistant

An AI-powered YouTube Question Answering application built using **Retrieval-Augmented Generation (RAG)**.

The application extracts a YouTube video's transcript, splits it into meaningful chunks, generates vector embeddings using OpenRouter, stores those embeddings in FAISS, retrieves the most relevant content for a user's question, and uses an LLM to generate a contextual answer.

---

## Overview

Large language models cannot automatically access the content of a YouTube video. This project solves that problem by creating a simple RAG pipeline around the video's transcript.

Instead of sending the complete transcript to the LLM for every question, the application:

1. Extracts the YouTube video ID.
2. Retrieves the video transcript.
3. Splits the transcript into smaller chunks.
4. Generates embeddings for each chunk.
5. Stores the embeddings in a FAISS vector index.
6. Converts the user's question into an embedding.
7. Performs similarity search against the FAISS index.
8. Retrieves the most relevant transcript chunks.
9. Sends the retrieved context and question to an LLM.
10. Generates the final answer.

---

## Architecture

```text
                    YouTube Video
                         |
                         v
                  YouTube URL
                         |
                         v
                 Extract Video ID
                         |
                         v
                 Fetch Transcript
                         |
                         v
                  Text Chunking
                         |
                         v
              Generate Embeddings
                         |
                         v
                    FAISS Index
                         |
                         |
              +----------+----------+
              |                     |
              v                     v
        User Question       Generate Query
                              Embedding
                                  |
                                  v
                         Similarity Search
                                  |
                                  v
                        Relevant Chunks
                                  |
                                  v
                              LLM
                                  |
                                  v
                           Final Answer
