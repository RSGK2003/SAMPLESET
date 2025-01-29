# **Financial Statement Query System (RAG-based)**

## **Overview**

This project implements a Retrieval-Augmented Generation (RAG) pipeline to process financial data from PDF documents and provide meaningful answers to user queries. The system extracts tabular financial data, processes it into a structured format, embeds the data for similarity-based retrieval, and uses a generative model to craft context-aware responses.

## **Features**

- **PDF Text Extraction**: Extracts content from financial PDF documents with page-specific targeting.
- **Tabular Data Processing**: Identifies and structures tabular data from the extracted content.
- **Contextual Embedding**: Embeds financial data into vector representations for similarity search.
- **Efficient Indexing**: Utilizes FAISS for fast and scalable similarity-based data retrieval.
- **Query Answering**: Combines retrieval and generative models to provide concise and accurate answers to user queries.

## **Technologies Used**

- **Programming Language**: Python  
- **Libraries**:
  - PDF Processing: `pdfplumber`
  - Natural Language Processing: `SentenceTransformer`, `transformers`
  - Machine Learning: `faiss`, `numpy`, `pandas`
  - Data Manipulation: `re`, `json`

## **Installation**

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_folder>
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Download the pre-trained models:
   - Sentence Embedding: `all-MiniLM-L6-v2` from `sentence-transformers`
   - Generative Model: `google/flan-t5-large` from `transformers`

## **Usage**

### **Pipeline Initialization**
The pipeline processes the financial data and prepares the system for answering queries.

```python
from pipeline import pipeline

pl = pipeline()
pl.processing('Sample Financial Statement.pdf', 2)
```

### **Query Handling**
Retrieve answers to user queries using the RAG pipeline.

```python
answer = pl.rag_pipeline("What is the total tax for Quarterly 2023?")
print(answer)
```

## **Project Workflow**

1. **PDF Text Extraction**:
   - Reads and extracts text from a specified page of a PDF document.

2. **Table Content Identification**:
   - Identifies tabular content using pattern matching to exclude irrelevant text.

3. **Structured Data Generation**:
   - Extracts numerical values and keys into a dictionary format for tabular structure.

4. **Data Preprocessing**:
   - Handles missing values, converts negative values, and normalizes data into a Pandas DataFrame.

5. **Embedding Creation**:
   - Converts financial data into dense embeddings using `SentenceTransformer`.

6. **Index Creation**:
   - Builds a FAISS index for efficient similarity-based retrieval of embeddings.

7. **Query Retrieval**:
   - Matches the query to the closest data points in the FAISS index using embeddings.

8. **Generative Answer Creation**:
   - Uses a generative model (`flan-t5-large`) to craft a concise and accurate response based on retrieved data.

## **Challenges Addressed**

- **Inconsistent Table Formats**: Used pattern matching to identify and standardize data extraction.
- **Missing Values**: Implemented padding for incomplete rows or columns.
- **Negative Value Representation**: Standardized formats by converting parentheses-enclosed values into negative floats.
- **Efficient Retrieval**: Used FAISS indexing for high-performance similarity-based searches.
- **Contextual Answer Generation**: Combined retrieval with generative modeling to ensure relevance.

## **Dependencies**

- Python 3.8+
- Libraries: 
  - `pdfplumber`
  - `sentence-transformers`
  - `transformers`
  - `faiss`
  - `numpy`
  - `pandas`

## **Future Enhancements**

- Extend support for multi-page document processing.
- Add advanced filtering mechanisms for customized indexing.
- Improve the robustness of table detection for diverse financial report formats.
