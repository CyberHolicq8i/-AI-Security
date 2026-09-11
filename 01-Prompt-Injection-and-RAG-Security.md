# 🛡️🤖 Indirect Prompt Injection Through RAG

## What I Learned

Traditional cybersecurity and AI security can overlap in the same attack.

A good example is an **indirect prompt injection attack against a RAG-based AI system**.

Instead of attacking the LLM directly through the chatbot, an attacker may place malicious instructions inside a document or another source of data that the AI system later retrieves.

---

## 🔴 Example Attack Chain

Attacker
↓
Uploads or poisons a document
↓
Document enters the application's data source
↓
Content is processed and indexed
↓
Embeddings are stored in a vector database
↓
User asks the AI a related question
↓
RAG retrieves the malicious content
↓
The LLM reads the hidden/malicious instructions
↓
Prompt Injection occurs

---

## 🧠 Important Concept

The **vector database is not the LLM's brain**.

It stores representations of information that can later be retrieved.

In a RAG system:

1. Documents are collected.
2. Their content is split into chunks.
3. The chunks are converted into embeddings.
4. The embeddings are stored in a vector database.
5. A user's question is used to retrieve relevant chunks.
6. Those chunks are provided to the LLM as context.
7. The LLM generates its answer.

This means an attacker does not necessarily need direct access to the vector database.

If an application allows documents, webpages, emails, tickets, or other external information to enter its knowledge pipeline, malicious instructions could potentially reach the LLM through that data.

---

# 🛡️ Where Classic Cybersecurity Fits

Traditional cybersecurity protects the infrastructure surrounding the AI system.

Examples include:

- Authentication
- Authorization
- File upload security
- Malware scanning
- Input validation
- API security
- Network security
- Access control
- Logging and monitoring
- Incident response

For example, cybersecurity controls may determine:

> "Should this user be allowed to upload this document?"

---

# 🤖 Where AI Security Fits

AI Security focuses on what happens when AI models interact with potentially untrusted information.

Examples include:

- Prompt injection
- Indirect prompt injection
- RAG poisoning
- Unsafe tool use
- Model manipulation
- Data poisoning
- Excessive agency
- AI output validation
- LLM security testing

For example, AI Security asks:

> "What happens if the document itself contains instructions designed to manipulate the LLM?"

---

# 🛡️ + 🤖 Hybrid AI Security

A secure AI application needs both disciplines.

**Classic Cybersecurity**

protects the:

User → Application → API → Infrastructure → Database

**AI Security**

protects the:

Data → Retrieval → Prompt → LLM → Tools → Output

Together:

Cybersecurity + AI/LLM Security = AI Security Engineering

---

## 🔵 Defensive Thinking

Possible defenses include:

- Treat retrieved documents as untrusted input.
- Separate system instructions from retrieved content.
- Apply strict permissions to AI tools.
- Validate sensitive actions outside the LLM.
- Monitor unusual AI behavior.
- Restrict which data sources can enter the RAG pipeline.
- Scan and validate uploaded content.
- Apply least privilege to AI agents.
- Require human approval for high-impact actions.

---

## 🎯 Key Takeaway

The biggest lesson for me was realizing that securing an AI system is not just about securing the model.

The entire pipeline matters.

An attacker may exploit traditional application weaknesses to reach an AI system, or manipulate information that the AI later trusts.

That is why I am studying both:

**🛡️ Classical Cybersecurity + 🤖 AI Security**

rather than treating them as completely separate fields.
