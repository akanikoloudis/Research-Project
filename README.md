Congressional RAG Pipeline

A Retrieval-Augmented Generation (RAG) pipeline for answering questions based on U.S. congressional hearing transcripts. This project was developed as part of the Bachelor of Computer Science and Engineering final research project at TU Delft.

Overview

This project implements a modular RAG pipeline for question answering using the LlamaIndex framework and OpenAI models. It focuses on the challenges of interpreting complex, unstructured political documents and aims to improve response faithfulness, relevance, and completeness.

Features
	•	Supports BM25, dense vector retrieval, and LLM-based reranking strategies.
	•	Compatible with multiple chunk sizes (4, 5, 6, and 10 sentences).
	•	Designed for open-ended and multiple-choice question formats.
	•	Uses GPT-4o-mini for response generation.
	•	Evaluation performed using LLM-based scoring (GPT-3.5 Turbo) and human expert assessment.

System Architecture

The pipeline consists of three main components:
	1.	Retrieval: Extract relevant passages using sparse/dense methods.
	2.	Augmentation: Format retrieved text into prompts.
	3.	Generation: Use an LLM to generate answers based on the retrieved context.

All components are built with the LlamaIndex framework and utilize the Chroma vector store for fast retrieval.

Installation

pip install llama-index
pip install openai
pip install chromadb
pip install mistralai
pip install rank_bm25


Setup
	1.	API Keys:
	•	OpenAI API key (for GPT-4o-mini, GPT-4-Turbo, and GPT-3.5 Turbo).
	•	Mistral embedding model key.
	2.	Transcripts:
	•	Add your congressional transcripts in .pdf format inside the ./data directory.

Configuration

Key parameters can be edited in the notebook header:
	•	CHUNK_SIZE = 4 | 5 | 6 | 10
	•	TOP_K = 3
	•	RETRIEVAL_METHOD = 'bm25' | 'vector' | 'rerank'
	•	QA_FORMAT = 'open-ended' | 'multiple-choice'

Usage

The pipeline can be run from the Jupyter notebook:
	1.	Load transcripts and split into sentence-window chunks.
	2.	Generate embeddings and build index.
	3.	Retrieve top-k passages based on a user query.
	4.	Construct a prompt and generate the response using GPT-4o-mini.
	5.	Evaluate answers using GPT-3.5 Turbo or human rubric.

Evaluation Metrics

Each response is rated on:
	•	Completeness: How fully it answers the question.
	•	Relevance: How focused it is on the query.
	•	Faithfulness: How true it is to the provided context.

Scoring is performed automatically (LLM) and manually (domain expert).

Results Summary
	•	LLM-based reranking with 10-sentence chunks provided the best performance.
	•	BM25 showed diminishing returns with longer chunks.
	•	Dense retrieval was effective across all chunk sizes.

Limitations
	•	Only 3 hearing transcripts used.
	•	No dynamic chunk sizing or adaptive reranking.
	•	Human evaluation limited to 24 questions.
	•	Costs related to OpenAI and Mistral API use.

Reproducibility
	•	Fully reproducible with the provided code and README.
	•	Parameters are global and easy to adjust.
	•	Hosted on GitHub (replace with actual repo).

Ethical Use
	•	Uses only public domain data.
	•	Avoids hallucinations by grounding answers strictly in retrieved text.
	•	Intended as a decision-support tool, not a replacement for expert analysis.

Citation

If you use this work, please cite the accompanying thesis:

Nikoloudis, A. A. (2025). A Question-Answering Pipeline for Congressional Hearings using Retrieval-Augmented Generation. TU Delft.

⸻

For questions or contributions, contact: Alexandros Aristomenis Nikoloudis | TU Delft
