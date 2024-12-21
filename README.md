

---

# Medical RAG (Retrieval-Augmented Generation) Knowledge Base

This project builds a **Medical Retrieval-Augmented Generation (RAG) Knowledge Base** using **Next.js**, **LangChain**, and **Pinecone** as the vector database. The system processes medical documents (e.g., PDF files) and stores their embeddings in a vector database, enabling efficient similarity search to retrieve relevant information in response to user queries.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies](#technologies)
- [Setup and Installation](#setup-and-installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)

## Overview

This application provides a user-friendly interface for uploading medical documents such as PDFs, converting them into chunks, and storing their embeddings in a vector database (Pinecone). The system uses **LangChain** for chunking documents and **Hugging Face's embedding models** to generate embeddings. These embeddings can be searched efficiently for retrieving relevant information from medical knowledge bases.

## Features

- Upload and process medical documents (PDF, text files).
- Chunk large documents and generate vector embeddings using an **ONNX-based model**.
- Store document embeddings in Pinecone for efficient similarity search.
- Progress bar for tracking the embedding process.
- Easily extendable to include more medical documents and enhance the knowledge base.

## Technologies

- **Next.js**: For building the front-end and API routes.
- **LangChain**: For document chunking and embedding.
- **Pinecone**: Vector database for storing document embeddings.
- **Hugging Face Transformers**: To generate embeddings using pre-trained models.
- **TypeScript**: For type safety.
- **Shadcn UI**: For building the UI components.

## Setup and Installation

### 1. Clone the Repository
```bash
git clone https://github.com/ShantamShukla/medicalrag.git
cd medicalrag
```

### 2. Install Dependencies
Ensure you have Node.js (version 18 or above) installed. Then install the required packages:

```bash
npm install
```

### 3. Environment Variables
Create a `.env` file in the root of the project and add the following environment variables:

```bash
PINECONE_API_KEY=your_pinecone_api_key
```

You can obtain your Pinecone API key by signing up at [Pinecone](https://www.pinecone.io).

### 4. Set Up Pinecone
- Log in to [Pinecone](https://www.pinecone.io) and create an index.
- Use **1024** as the dimension for embeddings, and **cosine** similarity as the metric.

### 5. Run the Application
After setting up, run the development server:

```bash
npm run dev
```

Your app will now be running at `http://localhost:3000`.

## Configuration

The following configurations are essential for the app:

- **Pinecone Index Name**: The name of the index in which document embeddings are stored.
- **Namespace**: You can store different document sets in Pinecone under separate namespaces.

You can specify these in the UI before uploading files.

## Usage

### 1. Upload Documents
- Open the app at `http://localhost:3000`.
- Select PDF or text files from your local system.
- Specify the **index name** and **namespace** for storing embeddings.
- Click the **Upload** button to begin the embedding process.

The progress bar will track the process, and embeddings will be pushed to the Pinecone database.

### 2. View Stored Vectors
Once the embeddings are processed and stored, you can view them in your Pinecone dashboard.

### 3. Searching Embeddings (Future Feature)
You can extend the app by building a search interface to query the stored embeddings and retrieve relevant information.

## Project Structure

```
├── pages/
│   ├── api/
│   │   └── updatedatabase.ts  # API route to handle document uploading and embedding
│   ├── index.tsx              # Main page for uploading documents
├── utils/
│   ├── updateVectorDB.ts      # Utility function to chunk, embed, and upload vectors
├── components/
│   └── UI components for the project
├── documents/                 # Place for storing documents
├── config.ts                  # Configuration file (batch sizes, etc.)
├── .env                       # Environment variables
└── README.md                  # This readme file
```

## Troubleshooting

### 1. Fetch Errors
If you encounter the error:
```
Failed to find any user-provided fetch implementation. Using global fetch implementation.
```
Ensure you are running **Node.js version 18+**, which provides a global `fetch` function. You can update Node.js using:
```bash
nvm install 18
nvm use 18
```

### 2. Missing API Key
If the vectors are not being pushed to Pinecone, ensure your API key is correctly configured in the `.env` file.

### 3. Large File Processing
For large PDF documents, the embedding process may take time. Let it run until the progress bar shows completion.

---
