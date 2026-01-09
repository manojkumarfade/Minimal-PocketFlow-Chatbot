# 🧠 Minimal PocketFlow Chatbot (TypeGPT + Colab)

A clean, lightweight **terminal-based AI chatbot** built in **Google Colab** using a **minimal PocketFlow-style architecture** and the **TypeGPT API**.

This project demonstrates how to structure an LLM chatbot using small, composable nodes instead of monolithic scripts.

---

## 🚀 What This Project Does

- Creates an interactive chatbot in Google Colab
- Maintains full conversation memory
- Sends user input to a Large Language Model (LLM)
- Prints AI responses in real time
- Loops until the user exits

The design is intentionally simple, readable, and extendable.

---

## 🛠️ Tech Stack Used

- **Python**
- **Google Colab**
- **TypeGPT API** (OpenAI-compatible chat API)
- **PocketFlow-inspired architecture**
- **Colab Secrets** for secure API key handling

No frameworks. No async complexity. No external dependencies beyond `requests`.

---

## 🧩 Architectural Idea (PocketFlow Style)

Instead of writing one large script, the chatbot is split into **Nodes**.

Each node has **one responsibility**:


This makes the logic:
- Easier to understand
- Easier to debug
- Easier to extend (RAG, tools, agents)

---

## 📁 Project Components Explained

### 1️⃣ Imports & Environment Setup

Used to:
- Make HTTP requests (`requests`)
- Handle flow execution (`copy`)
- Load secrets securely from Colab (`userdata`)

Nothing executes here — this cell only prepares the environment.

---

### 2️⃣ TypeGPT API Configuration

- Reads the API key from **Colab Secrets**
- Defines a helper function to call the chat completion endpoint
- Sends conversation history in OpenAI-style format

This keeps all LLM logic isolated in one place.

---

### 3️⃣ Minimal PocketFlow Engine

Defines:
- `Node`: a single unit of work
- `Flow`: a controller that runs nodes in sequence

Each node decides what the **next node** will be.
Returning `None` ends the flow.

This replaces complex state machines with a simple loop.

---

### 4️⃣ InputNode (User Input)

Responsibilities:
- Reads user input from the terminal
- Detects `exit` / `quit` commands
- Stores user input in shared memory

This node is the **entry point** of every chat turn.

---

### 5️⃣ MemoryNode (Conversation Storage)

Responsibilities:
- Maintains full chat history
- Stores messages in `{role, content}` format
- Ensures the LLM receives conversation context

This is what makes the chatbot *context-aware*.

---

### 6️⃣ APINode (LLM Interaction)

Responsibilities:
- Sends conversation history to TypeGPT
- Receives assistant response
- Handles API errors safely
- Stores assistant reply back into memory

This node is where intelligence happens.

---

### 7️⃣ DisplayNode (Output)

Responsibilities:
- Prints the assistant response to the user
- Keeps the UI clean and readable
- Sends control back to the input node

After this node, the loop continues.

---

### 8️⃣ Flow Wiring

Nodes are connected like this:




This creates a continuous conversational loop.

---

### 9️⃣ Running the Chatbot

- Initializes shared memory
- Inserts a system prompt
- Starts the flow execution

The chatbot remains active until the user exits.

---

## 🔐 API Key Setup (Important)

This project uses **Google Colab Secrets**.

Steps:
1. Open **Colab → Settings → Secrets**
2. Add a key named:
3. Paste your TypeGPT API key as the value

⚠️ Never hardcode API keys in notebooks or GitHub repos.

---

## ▶️ How to Run

1. Open the notebook in Google Colab
2. Add your API key to Colab Secrets
3. Run all cells
4. Start chatting in the terminal
5. Type `exit` to stop

---

## 🧠 Why This Design Matters

- Modular nodes instead of messy scripts
- Clear separation of concerns
- Easy to extend into:
- RAG pipelines
- Tool calling
- Agents
- Streamlit apps
- Multi-model routing

This structure scales from **toy chatbot → production agent**.

---

## 🔮 Possible Extensions

- Add document-based Q&A (RAG)
- Add chat memory trimming
- Add tool calling
- Convert to Streamlit UI
- Add multi-agent routing
- Add logging and analytics

---

## 📌 Summary

This project shows how to:
- Build a chatbot cleanly
- Think in flows, not scripts
- Keep LLM systems understandable
- Write code others can actually read

Simple. Powerful. Extendable.
