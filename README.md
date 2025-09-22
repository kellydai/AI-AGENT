# Customer Request Handler Workflow

An automated, AI-powered n8n workflow for handling incoming partnership or customer inquiries. It captures, processes, enriches, and responds to requests efficiently, ensuring professional and personalized follow-up.

## 📋 Overview

This workflow automates the entire lifecycle of a customer inquiry, from the moment a potential partner fills out a contact form to sending a tailored response and notifying the internal team. It leverages AI (via OpenRouter and Google Gemini) and RAG (Retrieval Augmented Generation) to generate highly customized email content based on the requester's details and your company's service documentation.

## ⚙️ Core Functions / Steps

### 1. 🤖 AI-Powered Response Generation (The "Brain")
- **Node:** `AI Agent1`
- **Function:** This is the core intelligence of the workflow. It uses an AI agent that:
  - Confirms receipt of the request
  - Queries a Pinecone vector database (`n8n2`) containing your company's service information
  - Selects up to 5 relevant services tailored to the customer's `Request description`
  - Generates a structured JSON output containing a professionally drafted email with personalized intro, service highlights, and 3 follow-up questions

### 2. 📚 Knowledge Base Management (Separate Flow)
- **Nodes:** `Manual Trigger` → `Download file` → `Extract from File` → ... → `Pinecone Vector Store`
- **Function:** This is a separate, manually triggered sub-workflow for populating the Pinecone vector store. It downloads a document (e.g., a Company Profile PDF) from Google Drive, processes it, and stores its information in the vector database so the AI agent can use it for RAG.

## 🎯 Applicability & Use Cases

This workflow is highly adaptable and can be applied in various scenarios:

### 1. 🤝 Partnership & Business Development
**Primary Use Case:** As designed, it's perfect for handling inbound partnership inquiries. It ensures quick, informed, and personalized initial contact, making your business appear responsive and professional.

### 2. 📊 Sales Lead Qualification
Modify the AI agent's prompt to ask qualifying questions. The workflow can automatically score leads based on `Company size`, `Region`, and request content, routing high-priority leads to a sales team immediately.

### 3. 🛠️ Customer Support Triage
Adapt the form and AI prompt to handle general customer support queries. The AI can pull answers from a knowledge base (via RAG) to provide instant, accurate first-line support, only escalating complex issues to human agents.

### 4. 🎪 Event or Webinar Follow-up
Change the form to capture registrants for an event. The workflow can then send a personalized thank-you email with relevant resources (pulled from your vector store) based on the attendee's stated interests.

### 5. 📦 Product Information Requests
Ideal for businesses with complex product catalogs. The AI can generate emails that highlight specific products or features relevant to the customer's inquiry, effectively acting as an automated pre-sales engineer.

## 🚀 Platform 
**n8n** - Workflow automation platform

## Sample email

<img width="1306" height="1220" alt="image" src="https://github.com/user-attachments/assets/6170251c-4fb6-40e1-8bfe-42fe1d432420" />
<img width="1318" height="1196" alt="image" src="https://github.com/user-attachments/assets/67295f65-7c84-4880-8430-b1106b4465d9" />
<img width="1302" height="870" alt="image" src="https://github.com/user-attachments/assets/7631f38d-79e2-4388-8f0c-65114bc4ef38" />

