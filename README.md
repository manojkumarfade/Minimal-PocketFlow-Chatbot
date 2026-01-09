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

