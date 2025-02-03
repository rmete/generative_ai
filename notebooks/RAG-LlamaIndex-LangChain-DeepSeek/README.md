# **RAG with LlamaIndex, LangChain, and DeepSeek**  

## **Overview**  
This project implements a **Retrieval-Augmented Generation (RAG)** system using:  

- **LlamaIndex** for indexing and retrieving relevant documents  
- **LangChain** for integrating retrieval and generation workflows  
- **DeepSeek-R1** as the large language model (LLM) for response generation  

The system fetches relevant passages from indexed documents and uses DeepSeek to generate informed responses.

---

## **Key Components**  

### **1. LlamaIndexRetriever (Retrieval Engine)**  
- Uses **Ollama Mistral** embeddings to retrieve **relevant documents**  
- Supports **customizable passage retrieval** (default: **15 passages**)  
- Extracts **full text** from relevant documents, not just embeddings  

### **2. DeepSeekLLM (Generation Engine)**  
- Queries **DeepSeek-R1** (locally hosted) to generate responses  
- Extracts **reasoning** and **answer** using `<think>` tags  
- Returns **relevant documents, prompt, and response** in structured JSON  

### **3. generate_response (End-to-End Execution)**  
- **Retrieves** documents from LlamaIndex  
- **Formats** context-aware prompts for DeepSeek  
- **Generates** responses using DeepSeek-R1  
- **Returns** a structured JSON containing:  
  - **Prompt**: The generated query  
  - **Reasoning**: DeepSeek's step-by-step analysis  
  - **Answer**: Final response to the question  
  - **Relevant Documents**: Extracted text from retrieved sources  

---

## **Setup Instructions**  

### **1. Install Dependencies**  
Ensure you have the required Python packages installed:  
```bash
pip install langchain llama-index requests
```

### **2. Setup Ollama and DeepSeek-R1**  
1. **Install Ollama** ([Ollama Docs](https://ollama.com/))  
2. **Pull the DeepSeek model**:  
   ```bash
   ollama pull deepseek-r1:32b
   ```
3. **Run DeepSeek locally**:
   ```bash
   ollama run deepseek-r1:32b
   ```

---

## **Usage**  

### **Run the RAG System**
You can run the retrieval and generation pipeline with the following command:

```python
query = "What are my dental benefits?"
response = generate_response(query, index=None, num_passages=15)
print("DeepSeek R1 Response:", response["answer"])
print("DeepSeek R1 Reasoning:", response["reasoning"])
print("Relevant Documents:", response["relevant_documents"])
```

### **Example Output**
```json
{
  "prompt": "Given the following context, answer the question concisely. [...]",
  "reasoning": "The retrieved documents contain information about Blue Shield's dental plan. The deductible is $50 per individual and $150 per family.",
  "answer": "Your MetLife dental deductible is $50 per individual and $150 per family.",
  "relevant_documents": [
    "MetLife Dental Plan: Deductible - $50 per individual, $150 per family. Includes preventive, basic, and major services."
  ]
}
```

---

## **Customization**  

### **Modify Number of Passages Retrieved**  
Change the number of retrieved documents in `generate_response`:
```python
response = generate_response(query, index=None, num_passages=20)
```

### **Use a Prebuilt Index**
If you have an existing index, load it:
```python
from llama_index.core import load_index_from_storage, StorageContext

storage_context = StorageContext.from_defaults(persist_dir="mistral_index_storage")
index = load_index_from_storage(storage_context)

query = "Explain my HMO benefits."
response = generate_response(query, index=index)
```

---

## **Future Improvements**
- Add **multi-turn conversations** with memory  
- Improve **prompt structuring** for better LLM responses  
- Support **different embedding models** (e.g., Hugging Face)  

