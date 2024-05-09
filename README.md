# WebTalk-Fusion: Next.js + FastAPI Chat Integration

WebTalk-Fusion is an innovative application that enables seamless chat functionality by harnessing the power of Next.js as the frontend and FastAPI as the backend. Leveraging LangChain for dynamic web interactions, this hybrid app offers users an intuitive chatbot interface for engaging conversations.

![Chatbot Interface](images/chatbot.png)

## Key Features

- **Dynamic Web Interaction with LangChain**: Utilizes the latest LangChain version to extract information and interact with websites dynamically.
- **Versatile Language Model Integration**: Supports various language models, including GPT-4, providing users with flexibility in choosing the most suitable model.
- **User-Friendly Next.js Frontend**: The interface is designed to be user-friendly and accessible for users with diverse technical backgrounds.

## Operational Mechanics

The application seamlessly integrates the Python/FastAPI server into the Next.js app under the `/api/` route. This integration is facilitated through the [`next.config.js` rewrites](https://github.com/digitros/nextjs-fastapi/blob/main/next.config.js), directing requests prefixed with `/api/:path*` to the FastAPI server located in the `/api` folder. During local development, FastAPI runs on `127.0.0.1:8000`, while in production, it operates as serverless functions on Vercel.

## Setting Up Instructions

1. Install dependencies:
   ```bash
   npm install
   ```
2. Create a `.env` file with your OpenAI API key:
   ```
   OPENAI_API_KEY=[your-openai-api-key]
   ```
3. Start the development server:
   ```bash
   npm run dev
   ```
4. Access the application at [http://localhost:3000](http://localhost:3000). The FastAPI server runs on [http://127.0.0.1:8000](http://127.0.0.1:8000).

For backend-only testing:

```bash
conda create --name nextjs-fastapi-your-chat python=3.10
conda activate nextjs-fastapi-your-chat
pip install -r requirements.txt
uvicorn api.index:app --reload
```

## Maintaining Chat History (TODO List)

Options for preserving chat history include:

- **Global Variable**: Simple but not scalable or consistent.
- **In-Memory Database/Cache**: Scalable solutions like Redis for storing chat history.
- **Database Storage**: Robust and persistent method, suitable for production environments.

## Understanding RAG Algorithms

RAG (Retrieval Augmented Generation) enhances language models with context retrieved from a custom knowledge base. The process involves fetching HTML documents, splitting them into chunks, and vectorizing these chunks using embedding models like OpenAI's. This vectorized data forms a vector store, enabling semantic searches based on user queries. The retrieved relevant chunks are then used as context for the language model, forming a comprehensive response to user inquiries.

## Implementing Context Retrieval

The `get_vectorstore_from_url` function extracts and processes text from a given URL, while `get_context_retriever_chain` forms a chain that retrieves context relevant to the entire conversation history. This pipeline approach ensures that responses are contextually aware and accurate.

## Inspiration and References

- [chat-with-websites](https://github.com/alejandro-ao/chat-with-websites)
- [next13-ai-saas](https://github.com/AntonioErdeljac/next13-ai-saas)
