# Customer_Service_Chatbot_Coffe_Shop
An AI-powered, agent-based chatbot designed to elevate customer service in coffee shop apps. Built with LLMs, NLP, and RAG, this chatbot can take orders, answer menu questions, provide personalized recommendations, and ensure safe interactions.


### **🧠 System Overview:**
A user interacts with a **mobile application (Firebase-powered)**. Their queries are sent to an **API Endpoint** which is backed by a multi-agent architecture, using **Serverless LLaMA 3.1**, a **vector database (Pinecone)**, and **trained recommendation models**.

---

### **🧠 Backend Components:**

#### **API Endpoint / Agent Coordinator**
- All user input hits this central endpoint.
- The **Agent Coordinator** orchestrates which downstream agent will handle the query.

---

### **📱 Frontend (User Side):**
- A mobile app UI (possibly built using Flutter or React Native).
- The app uses **Firebase** for authentication, analytics, or real-time syncing.
- The user can browse items (e.g., coffee products), ask for recommendations, or place orders.

---


### **1. Guard Agent**
- Acts as a **content filter** or **safety check**.
- It checks whether the user’s query is **safe or appropriate** (e.g., no harmful or off-topic queries).

#### 👉 If **Not Safe**:
- Sends a response back directly to the user.

#### 👉 If **Safe**:
- Passes the query to the **Input Classifier Agent**.

---

### **2. Input Classifier Agent**
- Classifies the query into types: `Order`, `Recommendation`, or `Details`.
- Routes the query to the corresponding agent.

---

### **3. Task-specific Agents**
- **Order Agent**: Handles user orders.
- **Recommendation Agent**: 
  - Uses a **trained model** or **Serverless LLaMA 3.1** to understand preferences.
  - Integrates with **Pinecone vector database** for semantic search and contextual recommendations.
- **Details Agent**: Provides more details about a specific product.

---

### **4. Response Agent**
- Gathers the results from the chosen task agent.
- Sends the response back to the user app.

---

### **💡 LLM + Vector DB Integration**
- **Serverless LLaMA 3.1** powers natural language understanding and generation.
- **Pinecone** is used for **retrieval-augmented generation (RAG)**:
  - Stores vector embeddings of items (or past queries).
  - Enables fast, relevant semantic searches to power the recommendation system.

---

### 🔁 **Flow Summary:**
1. User query → API → Guard Agent → Input Classifier
2. Input Classifier → [Order | Recommendation | Details Agent]
3. Agent (optionally) queries LLaMA + Pinecone + trained models
4. Response Agent sends back output to user

---

### **✅ Possible Use Cases:**
- AI-powered personalized recommendations.
- Natural language food ordering (e.g., "Get me something with caramel").
- Product info (e.g., "Tell me more about the Pumpkin Latte").
- Moderation of inappropriate queries.
