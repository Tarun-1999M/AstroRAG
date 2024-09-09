# RAG System for Astronomical Text Retrieval and Response Generation

## Introduction
This project implements a Retrieval-Augmented Generation (RAG) system for astronomical text, using the book *Introduction to Astronomy* by Forest Ray Moulton. The system extracts relevant information from the text and generates answers to user queries based on the retrieved content.

## Features
- Convert PDF text to structured sentences and chunks
- Retrieve relevant text using FAISS and sentence embeddings
- Use the `gemma-2-2b-it` model to generate conversational responses based on retrieved chunks

## Project Workflow

1. **Text Extraction**:
   - The PDF is read using the `fitz` library.
   - Each page of the book is divided into sentences.
   - Sentences are grouped into chunks of 10 sentences for efficient retrieval.

2. **Embeddings**:
   - Sentence embeddings are generated using the `sentence-transformers` model `all-mpnet-base-v2`.
   - The embeddings are indexed using FAISS for fast retrieval of relevant text chunks.

3. **Retrieval**:
   - The system retrieves the most relevant sentence chunks based on user queries.
   - FAISS is used to search the indexed embeddings for efficient matching of queries to text.

4. **Response Generation**:
   - The `gemma-2-2b-it` model in float 16 precision is used for response generation.
   - A conversational prompt template is applied to the model to generate user-friendly outputs.

## Example Query

**User Query**: "What is the sun made up of?"

**Generated Response**:

<bos> The sun is composed of many elements, with the photosphere (the visible surface) containing a majority of the elements. The reversing layer is a sheet of gas with many terrestrial elements like calcium and iron in a vaporous state. The chromosphere, located above the reversing layer, is a layer of gas that gets its scarlet color from the incandescent hydrogen and calcium it contains. Heavier elements like iron and calcium are found in the reversing layer, while lighter elements like hydrogen and helium are found in the chromosphere. \n<end_of_turn>



## Technologies Used
- **fitz**: For PDF text extraction.
- **Sentence Transformers**: For generating embeddings using `all-mpnet-base-v2`.
- **FAISS**: For efficient retrieval of sentence embeddings.
- **gemma-2-2b-it**: For generating responses based on retrieved chunks.
- **PyTorch**: For deep learning operations with `gemma-2-2b-it` in float 16 mode.

## Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/astronomy-rag.git
    ```

2. **Navigate to the project directory**:
    ```bash
    cd astronomy-rag
    ```

3. **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Download the PDF**:
   Place the PDF *Introduction to Astronomy* by Forest Ray Moulton in the project directory.

## Usage

1. **Run the script** to generate embeddings and store them using FAISS:
    ```bash
    python generate_embeddings.py
    ```

2. **Run the retrieval and response system** to query the text and generate answers:
    ```bash
    python generate_response.py --question "What is the sun made up of?"
    ```

## Project Structure

- `/src`: Contains the source code.
- `/data`: Stores the PDF file and FAISS index.
- `/models`: Pre-trained models and embeddings.
- `/outputs`: Generated responses.

## Results
- Efficient retrieval of relevant astronomical information.
- High-quality conversational responses using `gemma-2-2b-it` for scientific questions.
- Example queries include "What is the sun made up of?" with detailed, accurate responses.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

