# Retrieval-Augmented-Generation (RAG)

### Course: Natural Language Processing (2023-2024)  
### Master's Degree: Physics of Data, University of Padova (IT)

## Overview

This project was developed as part of the final exam for the Natural Language Processing course during the academic year 2023-2024. The work was carried out individually during my second year in the Master's degree program in *Physics of Data* at the University of Padova.

The goal of the project was to develop a Retrieval-Augmented Generation (RAG) model for the domain of our choice. In my case, I chose to build a RAG application for retrieving and generating responses to questions about Sherlock Holmes books.

## Data

In this project, the dataset used can be downloaded from this [Kaggle repository](https://www.kaggle.com/datasets/talesgomes27/sherleck-books) which contains the four main Sherlock Holmes novels and a collection of short stories across five additional books. For this project, the focus was placed on the following four novels:

- *A Study in Scarlet*
- *The Sign of Four*
- *The Hound of the Baskervilles*
- *The Valley of Fear*

These four books were used to create a Retrieval-Augmented Generation application capable of generating accurate and contextually relevant textual responses related to the Sherlock Holmes stories.

## Methods and Models

The pipeline for the RAG project includes the following steps:

1. **Load the Textual Data**  
   The Sherlock Holmes books are loaded into the system as text, ready for processing and embedding.

2. **Text Normalization and Preprocessing**  
   We preprocess the text to remove noise (Guthenberg project info), normalize the data and tokenize it into useful units for further embedding.

3. **Embeddings and Similarity Search**  
   Various sentence embedding models were tested to determine which best captured semantic relationships in the dataset. The tested models include:
   - `sentence-transformers/all-MiniLM-L12-v2`
   - `sentence-transformers/all-mpnet-base-v2`
   - `sentence-transformers/multi-qa-MiniLM-L6-cos-v1`
   
   Based on performance (evaluated using similarity search on a set of predefined queries), we chose the best embedding model for the retrieval component.

4. **Building a Retrieval Chain**  
   We constructed a retrieval pipeline that uses the embeddings to find relevant passages from the text in response to user queries. The retrieval system is tightly integrated with a generative model.

5. **Generative Model: LLaMA-2**  
   For text generation, we employed the `Llama-2-7b-chat-hf`, a large language model (LLM) with 7 billion parameters. This model generates human-like responses based on the retrieved text passages.

6. **Text Generation Pipeline Setup**  
   The pre-trained LLaMA-2 model and its tokenizer are initialized to generate text with specific parameters, including:
   - **Temperature**: Controls the randomness of the output.
   - **Max Tokens**: Limits the length of generated responses.
   
   These parameters can be fine-tuned to achieve more precise or creative responses depending on the user's needs.

7. **Prompt Engineering**  
   The effectiveness of the model is improved by refining the input prompts. A series of increasingly complex questions about Sherlock Holmes stories were used to test and enhance the model's performance.

8. **Qualitative Evaluation**  
   The system's responses were evaluated qualitatively by adjusting various components such as:
   - Embedding models
   - Temperature settings
   - Maximum token length  
   
   These adjustments were aimed at generating more contextually accurate and semantically rich answers.

## Conclusion

The development of this RAG project demonstrated the power of combining information retrieval techniques with large language models to create a system capable of answering questions about specific domains—in this case, the Sherlock Holmes novels. The pipeline efficiently retrieves relevant information and generates coherent, context-aware responses.
