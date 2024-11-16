## Multi-Document RAG Agent Architecture

The **Multi-Document RAG Agent** is an intelligent query routing system built to retrieve and process information from large sets of documents efficiently. It uses a Retrieval-Augmented Generation (RAG) framework to select the most relevant documents and passages, significantly improving query response accuracy and efficiency. By generating concise summaries for each document, the system creates a robust mapping mechanism that aligns user queries with the most relevant documents. These summaries encapsulate the core content of documents, streamlining the retrieval process and enabling precise targeting of relevant data.

![Diagram 1](https://github.com/user-attachments/assets/bbc60fee-d603-4a41-a96b-a2e689056c17)
## Features  
- **Smart Document Selection**: Utilizes vector similarity search combined with document summaries to effectively map queries to the most relevant documents.  
- **Granular Retrieval**: Breaks documents into passages for fine-tuned retrieval, further narrowing down the search space.  
- **Adaptive Query Processing**: Differentiates between general and document-specific queries for optimal handling.  
- **Efficient Token Usage**: Leverages document summaries to minimize unnecessary resource consumption, focusing only on high-relevance data.  


## Technologies Used
- **LLM**: Google Gemini
- **Framework**: LangChain
- **Vector Database**: Pinecone
- **Language**: Python


## How It Works
![Diagram 2](https://github.com/user-attachments/assets/a550a18b-34c8-4c8b-a6ec-f8bafff34941)


### Data Preparation
1. **Document Summarization**:
   - Summarize documents using LangChain.
   - Generate embeddings for summaries and store them in a Pinecone namespace `summary_embeddings` with a unique document ID.

2. **Passage Embedding**:
   - Split documents into 1000-word chunks.
   - Convert these passages into embeddings and store them in the `passages_embeddings` namespace, linked with document IDs.

### Query Processing
3. **Query Classification**:
   - Use a one-shot classifier to determine if a query is general or requires document retrieval.

4. **Summary Matching**:
   - For document queries, generate embeddings and perform similarity searches on `summary_embeddings`.
   - Retrieve the top 3 document summaries.

5. **Document Selection**:
   - Use the retrieved summaries to identify relevant document IDs via a `document_selection_prompt`.

6. **Passage Matching**:
   - Extract the top 10 relevant passages from the selected documents using similarity search on the user query and passage embeddings.

7. **Final Response Generation**:
   - Use the retrieved passages and the query to generate the final response.

## Key Advantages
1. **Efficiency**: Reduces unnecessary token consumption by narrowing down search results.
2. **Flexibility**: Handles multi-document queries and retrieves answers spanning multiple documents.
3. **Scalability**: Optimized for large document sets with vector search.


## Limitations
- **Edge Cases**: Struggles with large-scale queries requiring data from many documents (e.g., insights from 40+ documents simultaneously).
- **Potential Information Loss**: When multiple documents are retrieved, combining passages may omit some details.


# Demo Video: [Watch on Canva](https://www.canva.com/design/DAGOL1_fKr8/dfN6twr4KGkWXtTChWPJ6Q/watch?utm_content=DAGOL1_fKr8&utm_campaign=share_your_design&utm_medium=link&utm_source=shareyourdesignpanel)
