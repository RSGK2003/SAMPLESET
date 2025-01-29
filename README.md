# SAMPLESET
Project Workflow
PDF Text Extraction:

Reads and extracts text from a specified page of a PDF document.
Table Content Identification:

Identifies tabular content using pattern matching to exclude irrelevant text.
Structured Data Generation:

Extracts numerical values and keys into a dictionary format for tabular structure.
Data Preprocessing:

Handles missing values, converts negative values, and normalizes data into a Pandas DataFrame.
Embedding Creation:

Converts financial data into dense embeddings using SentenceTransformer.
Index Creation:

Builds a FAISS index for efficient similarity-based retrieval of embeddings.
Query Retrieval:

Matches the query to the closest data points in the FAISS index using embeddings.
Generative Answer Creation:

Uses a generative model (flan-t5-large) to craft a concise and accurate response based on retrieved data.
Challenges Addressed
Inconsistent Table Formats: Used pattern matching to identify and standardize data extraction.
Missing Values: Implemented padding for incomplete rows or columns.
Negative Value Representation: Standardized formats by converting parentheses-enclosed values into negative floats.
Efficient Retrieval: Used FAISS indexing for high-performance similarity-based searches.
Contextual Answer Generation: Combined retrieval with generative modeling to ensure relevance.
Dependencies
Python 3.8+
Libraries:
pdfplumber
sentence-transformers
transformers
faiss
numpy
pandas
Future Enhancements
Extend support for multi-page document processing.
Add advanced filtering mechanisms for customized indexing.
Improve the robustness of table detection for diverse financial report formats.
