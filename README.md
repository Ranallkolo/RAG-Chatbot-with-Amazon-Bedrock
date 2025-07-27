<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a RAG Chatbot in Bedrock

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-rag-bedrock)

**Author:** Abdulrahman Abdulkadir  
**Email:** abdabdulkadir62@gmail.com

---

## Set Up a RAG Chatbot in Bedrock

![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_d5e8f1g2)

---

## Introducing Today's Project!

RAG (Retrieval Augmented Generation) is a method that improves AI responses by retrieving relevant info from a knowledge base before generating answers. In this project, I will demonstrate RAG by using a model that first searches a knowledge base, then generates accurate responses based on what it finds.


### Tools and concepts

Services I used were Amazon Bedrock, S3, and OpenSearch Serverless. Key concepts I learnt include Retrieval Augmented Generation (RAG), chunking, embeddings, vector stores, and how to configure and fine-tune a knowledge base to improve chatbot performance.


### Project reflection

This project took me approximately a few hours spread over two days. The most challenging part was configuring the Knowledge Base correctly and troubleshooting model compatibility for RAG. It was most rewarding to see the chatbot accurately answer questions using my own project data.


I did this project today to deepen my understanding of how Retrieval Augmented Generation works using Amazon Bedrock. It helped me apply what I’ve learned about AWS services like S3, OpenSearch, and embeddings in a real use case. Yes, this project met my goals—it improved my skills in setting up a knowledge base, fine-tuning chatbot behavior, and showcasing my AWS project experience effectively.


---

## Understanding Amazon Bedrock

Amazon Bedrock is a fully managed service that lets you build and scale generative AI applications using foundation models from top providers via an API. I'm using Bedrock in this project to easily implement RAG by connecting a knowledge base to a powerful language model without managing any infrastructure.


My Knowledge Base is connected to S3 because that's where the source documents are stored. S3 is a scalable object storage service that Bedrock uses to access and sync the data used for retrieval during RAG operations.


In an S3 bucket, I uploaded text documents containing information relevant to my project, such as FAQs and product details. My S3 bucket is in the same region as my Knowledge Base because Bedrock requires both to be in the same region for smooth integration and performance.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_b5c8d1e2)

---

## My Knowledge Base Setup

My Knowledge Base uses a vector store, which means it stores and indexes embeddings for fast similarity searches. When I query my Knowledge Base, OpenSearch will quickly find the most relevant chunks by comparing vector embeddings, enabling accurate and efficient retrieval during RAG interactions.


Embeddings are numerical representations of text that help the model understand and compare meanings. The embeddings model I'm using is Titan Text Embeddings v2 because it’s optimized for use with Amazon Bedrock, providing accurate and efficient search and retrieval within the Knowledge Base.


Chunking is the process of breaking large documents into smaller, manageable sections to improve retrieval accuracy. In my Knowledge Base, chunks are set to default settings, allowing Bedrock to automatically divide the content for optimal search and response generation.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_p9r2s5t8)

---

## AI Models

AI models are important for my chatbot because they understand language, retrieve relevant information, and generate natural responses. Without AI models, my chatbot would only follow fixed scripts and couldn’t handle complex or dynamic questions.


To get access to AI models in Bedrock, I had to request model access through the Bedrock console and wait for approval. AWS needs explicit access because these models are powerful, often third-party, and access must be granted to ensure proper usage and cost control.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_model-access-proof)

---

## Syncing the Knowledge Base

Even though I already connected my S3 bucket when creating the Knowledge Base, I still need to sync because syncing processes the documents, generates embeddings, and updates the vector store so the content can be retrieved and used by the AI model during queries.


The sync process involves three steps:

1. **Ingesting** – Bedrock retrieves the data from the connected data source (S3).
2. **Processing** – Bedrock chunks the data into smaller pieces and creates embeddings by converting the text into numerical vectors.
3. **Storing** – Bedrock stores the processed vectors in the vector store (OpenSearch Serverless) for efficient retrieval during queries.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_sync-screenshot)

---

## Testing My Chatbot

I initially tried to test my chatbot using Llama 3.1 8B as the AI model, but it didn’t support on-demand RAG for my Knowledge Base. I had to switch to Llama 3.3 70B because it’s available on demand and fully supports RAG, allowing the chatbot to retrieve and generate accurate responses using my synced data.



When I asked about topics unrelated to my data, my chatbot still gave a helpful answer using the model’s built-in knowledge. This proves that the AI can generate responses even without retrieval, but for domain-specific questions, it relies on the synced Knowledge Base.


You can also turn off the Generate Responses setting to test only the retrieval part of RAG. This lets you see which documents the Knowledge Base returns without the AI model generating a full response, helping you check if your data is being retrieved correctly.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_d5e8f1g2)

---

## Upgrading My Chatbot

In a project extension, I looked into increasing the number of source chunks, which are the top relevant text sections retrieved from the Knowledge Base. This will improve my chatbot's responses by giving it more context to generate accurate and detailed answers.


I also added a custom prompt that tells my chatbot to answer questions based on the student’s completed AWS and AI projects. It’s instructed to always highlight the AWS services used and the skills the student learnt, even if the question doesn’t ask directly. This ensures every response reinforces the student’s learning and showcases their hands-on experience.


After adjusting the source chunks and the generation prompt, my chatbot's response became more detailed and relevant to my actual projects. It now includes specific AWS services I used and highlights the skills I gained, making the answers more personalized and informative compared to the more generic responses it gave before.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/ai-rag-bedrock_improved-response)

---

---
