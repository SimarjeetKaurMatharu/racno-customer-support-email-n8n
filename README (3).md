# RACNO Customer Support Email Auto-Responder

**AI-powered email support system that automatically classifies incoming emails and replies to customer queries using a knowledge base — built with n8n.**

The system monitors Gmail, filters only RACNO-related support emails, retrieves relevant information from the knowledge base, and sends professional automated replies.

---

## Demo

| Workflow Canvas | Example Reply |
|----------------|---------------|
| ![Workflow Canvas](assets/n8n-canvas.png) | ![Sample Reply](assets/sample-reply.png) |

> Replace the placeholders above with your actual screenshots.

---

## Problem

Customer support teams receive a high volume of emails. Many are repetitive questions about products, policies, or FAQs. Manually reading, classifying, and replying to every email is time-consuming and slows down response time.

## Solution

This workflow automatically:
1. Monitors incoming Gmail messages
2. Classifies whether the email is related to RACNO customer support
3. Retrieves relevant information from the knowledge base (Pinecone)
4. Generates a professional reply using an AI Agent
5. Sends the reply back to the customer

---

## Architecture

---

## Key Features

- **Automatic email classification** — Only processes RACNO-related support emails
- **RAG-powered responses** — Answers are grounded in the official knowledge base
- **Professional tone control** — Formal language, no emojis, consistent sign-off
- **Fully automated replies** — Sends responses without human intervention
- **Low-code implementation** — Built entirely in n8n for easy maintenance

---

## Tech Stack

| Layer              | Technology                          |
|--------------------|-------------------------------------|
| Orchestration      | n8n                                 |
| Email Source       | Gmail                               |
| Classification     | Google Gemini (Text Classifier)     |
| LLM                | Google Gemini Chat Model            |
| Agent Framework    | n8n AI Agent                        |
| Knowledge Base     | Pinecone (RAG)                      |
| Embeddings         | Google Gemini                       |

---

## How the AI Agent Behaves

- Starts every reply with **“Hello There”**
- Uses formal language only
- Does **not** use emojis
- Signs off as **Miss Helpful from RACNO Wood and Precision pvt. ltd.**
- Retrieves information from the Pinecone knowledge base when needed

---

## Repository Structure

---

## How to Import & Run

### Prerequisites
- An n8n instance (Cloud or self-hosted)
- Gmail account with API access
- Google Gemini API key
- Pinecone account + index (with RACNO knowledge base)

### Steps

1. **Import the workflow**
   - Open n8n → Workflows → Import from File
   - Select `workflow/customer-support-email-workflow.json`

2. **Create the required credentials**
   - Gmail OAuth2
   - Google Gemini (PaLM) API
   - Pinecone API

3. **Configure the nodes**
   - Attach Gmail credentials to the **Gmail Trigger** and **Reply to a message** nodes
   - Attach Gemini credentials to the classifier and agent
   - Configure the Pinecone node with your index and namespace

4. **Activate the workflow**

5. **Test**
   - Send a test email related to RACNO to the connected Gmail account
   - Check that the system classifies it correctly and sends a reply

---

## Design Decisions

| Decision | Why |
|---------|-----|
| Text Classifier before the Agent | Prevents the system from replying to unrelated emails |
| Agent + Tool (RAG) pattern | Allows the model to pull accurate information from the knowledge base |
| Strict system prompt | Ensures consistent, professional, and on-brand replies |
| Automatic Gmail reply | Fully closes the loop without human intervention |

---

## Limitations

- Currently replies only in plain text
- No human review / approval step before sending
- Relies on the quality of the knowledge base in Pinecone
- Classification depends on the quality of the category descriptions
- No conversation memory across multiple emails from the same customer

---

## Future Improvements

- [ ] Add a human approval step before sending replies
- [ ] Support HTML email replies
- [ ] Add conversation memory / thread awareness
- [ ] Log all classified emails and replies for review
- [ ] Improve classification with more detailed categories
- [ ] Add fallback when the knowledge base has no relevant information
- [ ] Multi-language support

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

**Built with n8n • Powered by Google Gemini & Pinecone**