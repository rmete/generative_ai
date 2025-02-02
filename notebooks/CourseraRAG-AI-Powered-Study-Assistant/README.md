# CourseraRAG-AI-Powered-Study-Assistant

## Project Overview

CourseraRAG-AI-Powered-Study-Assistant is a project designed to enhance the study process using cutting-edge retrieval and generative AI techniques. It is built to help students efficiently find and understand course material by retrieving relevant content from a structured database of lecture transcripts and textbooks while generating AI-powered answers based on user queries.

### Key Features

1. **Retrieval System**
   - Utilizes a comprehensive corpus of educational materials, including lecture transcripts and textbook chapters.
   - Extracts the most relevant documents for user queries, ensuring accurate and helpful responses.

2. **Generative AI (Powered by OpenAI APIs)**
   - Generates coherent and contextually rich answers based on the retrieved documents.
   - Uses OpenAI’s advanced language models to enhance understanding and provide high-quality information.

3. **Interactive User Interface**
   - Allows users to input questions and receive AI-generated responses in a structured manner.
   - Displays the retrieved documents along with AI-generated answers for transparency and verification.

---

## Dataset Information

⚠️ **Dataset Not Included**
This project was developed using a dataset from Coursera, which is not publicly available. To comply with data-sharing restrictions, the dataset is not uploaded. However, the notebook is structured so you can substitute your own dataset for retrieval and generation.

---

## Project Workflow

### 1. Data Preprocessing
- Converts textbook PDFs into structured text files, segmented by chapters.
- Extracts and organizes lecture transcripts for easy retrieval.
- Implements text preprocessing, including tokenization, lemmatization, and stopword removal.

### 2. Retrieval System
- Implements TF-IDF vectorization to convert text into numerical representations.
- Uses cosine similarity to rank and retrieve the most relevant documents based on user queries.
- Supports both lecture transcripts and textbook chapters for comprehensive content retrieval.

### 3. AI-Generated Answers
- Queries OpenAI's GPT-4 API to generate responses based on retrieved documents.
- Constructs context-aware prompts to enhance answer quality.
- Incorporates a parallel processing pipeline to handle multiple queries efficiently.

### 4. User Interaction
- Provides a menu-driven interface for users to interact with the system.
- Supports querying study materials based on specific guiding questions.
- Displays both retrieved documents and AI-generated responses for a complete learning experience.

---

## Technologies Used

- **Python**: Core programming language for data processing and model integration.
- **OpenAI API**: Provides generative AI capabilities.
- **TF-IDF Vectorization**: Used for document ranking and retrieval.
- **Cosine Similarity**: Measures document relevance to user queries.
- **NLTK & Scikit-learn**: Libraries for text preprocessing and analysis.
- **Google Colab**: Environment for development and execution.

---

## How to Use

1. **Prepare Your Dataset**
   - Ensure you have lecture transcripts and textbook chapters in text format.
   - Store files in organized directories (e.g., `/Lectures`, `/Textbook`).

2. **Run the Notebook**
   - Install required dependencies (`pip install openai nltk scikit-learn`).
   - Execute the preprocessing cells to extract and structure your dataset.

3. **Ask Questions**
   - Use the interactive menu to enter queries.
   - View retrieved documents and AI-generated responses.

4. **Modify for Your Needs**
   - Replace the dataset with your own structured text corpus.
   - Adjust the retrieval parameters to fine-tune relevance scoring.

---

## Future Enhancements

- Implementing a **vector-based retrieval system** using embeddings for improved accuracy.
- Enhancing the UI with a **web-based interface** for better user experience.
- Expanding to support **multi-modal data** such as images and video transcripts.

---

## Acknowledgments

This project was developed as part of the **CS 410 Final Project** for Coursera. Special thanks to the Coursera community for providing structured learning resources that inspired this implementation.

For inquiries, feel free to reach out!

