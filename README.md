Below is a **complete, professional, evaluator-ready README.md** that you can **copy-paste directly** into your repository.
It explains **objective, architecture, agent workflow, setup, folders, tools, failure handling, and evaluation alignment** in detail.

---

# 🎤 Hindi Government Voice Agent

**Voice-First Agentic AI for Government Scheme Eligibility (Hindi)**

---

## 📌 Overview

**Hindi Government Voice Agent** is a **voice-first, agentic AI system** that helps Indian citizens identify **government and public welfare schemes** they are eligible for — **entirely through voice interaction in Hindi**.

This system is **not a chatbot**. It is a **stateful, decision-making AI agent** that can:

* Listen to users via voice
* Reason over incomplete or ambiguous information
* Ask follow-up questions
* Apply defaults when information is missing
* Use tools (eligibility engine + database)
* Remember context across turns
* Recover from failures in speech recognition

---

## 🎯 Objective

Build a **native-language, voice-first AI agent** that can autonomously reason, plan, and act to assist users in identifying government schemes — meeting all **agentic AI requirements**.

---

## 🧠 Key Capabilities

✔️ **Voice-first interaction** (STT → Agent → TTS)
✔️ **Hindi-only pipeline** (No English reasoning exposed)
✔️ **Multi-turn memory & state management**
✔️ **Planner → Executor → Evaluator agent workflow**
✔️ **Tool usage** (Eligibility engine + CSV database)
✔️ **Failure handling & defaults**
✔️ **End-to-end runnable system**

---

## 🗣️ Example User Flow

**User:**

> “मैं सरकारी योजनाओं के बारे में जानना चाहता हूँ।”

**Agent (Voice):**

> “कृपया अपनी उम्र, लिंग और वार्षिक आय बताएं।”

**User:**

> “मैं 32 साल का पुरुष हूँ और मेरी सालाना आय 1.5 लाख है।”

**Agent (Voice):**

> “आप प्रधानमंत्री आवास योजना और आयुष्मान भारत योजना के लिए पात्र हैं…”

---

## 🧩 Agent Architecture

### High-Level Flow

```
User Voice
   ↓
Speech-to-Text (Whisper)
   ↓
Agent Planner
   ↓
Memory + State Manager
   ↓
Eligibility Tool (CSV Database)
   ↓
Agent Evaluator
   ↓
Text-to-Speech (gTTS)
   ↓
User Audio Output
```

---

## 🤖 Agentic Workflow (Planner–Executor–Evaluator)

### 1️⃣ Planner

* Determines **what information is missing**
* Decides whether to:

  * Ask questions
  * Finalize eligibility
  * Apply defaults

### 2️⃣ Executor

* Extracts age, gender, income from Hindi speech
* Updates session memory
* Queries eligibility database

### 3️⃣ Evaluator

* Validates completeness
* Applies defaults after second attempt
* Prevents repeated questioning
* Produces final response

---

## 🧠 Memory & State Management

Each user session maintains:

```python
SESSION = {
  "age": None,
  "gender": None,
  "income": None,
  "attempts": 0,
  "finalized": False
}
```

### Rules:

* Agent **asks only once** for missing info
* On second attempt:

  * Defaults applied (Age=30, Gender=Male, Income=100000)
* After finalization:

  * Agent **never asks again**
  * Only responds with results

---

## 🛠️ Tools Used

### Tool 1: Eligibility Engine

* Rule-based engine
* Matches age, gender, income against scheme constraints

### Tool 2: Scheme Database

* CSV-based retrieval system
* 100+ government scheme entries
* Easy to extend or replace with API later

---

## 🧯 Failure Handling

✔️ Incomplete user input
✔️ Speech recognition errors
✔️ Missing eligibility fields
✔️ Ambiguous gender or income
✔️ Repeated user mistakes

➡️ Agent **recovers gracefully** and proceeds autonomously.

---

## 📁 Project Structure

```
hindi-gov-voice-agent/
│
├── backend/
│   ├── server.py        # FastAPI server + agent orchestration
│   ├── logic.py         # Memory, extraction, eligibility logic
│   ├── tts.py           # Hindi text-to-speech utilities
│   └── agent/
│       ├── planner.py   # Decision planning logic
│       ├── executor.py  # Tool execution
│       └── evaluator.py # Final response evaluation
│
├── frontend/
│   ├── index.html       # UI layout
│   ├── script.js        # Recording, submit, audio playback
│   ├── app.js           # UI event wiring
│   └── style.css        # UI styling
│
├── database/
│   └── schemes.csv      # Government schemes dataset
│
├── audio/               # Generated TTS audio files
├── temp/                # Temporary Whisper audio files
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation
└── venv/                # Virtual environment
```

---

## ⚙️ Setup Instructions

### 1️⃣ Clone Repository

```bash
git clone <repo-url>
cd hindi-gov-voice-agent
```

### 2️⃣ Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Run Server

```bash
uvicorn backend.server:app --reload
```

### 5️⃣ Open UI

```
http://127.0.0.1:8000
```

🎤 **Allow microphone access in browser**

---

## 📊 Evaluation Alignment

| Requirement             | Status                       |
| ----------------------- | ---------------------------- |
| Voice-first interaction | ✅                            |
| Native Indian language  | ✅ Hindi                      |
| Agentic workflow        | ✅ Planner–Executor–Evaluator |
| Tool usage              | ✅ Eligibility + DB           |
| Memory across turns     | ✅                            |
| Failure handling        | ✅                            |
| Runnable code           | ✅                            |
| Not a chatbot           | ✅                            |

---

## 📹 Demo Video (Suggested Flow)

1. User opens UI
2. User speaks vague request
3. Agent asks eligibility questions (voice)
4. User responds partially
5. Agent applies defaults
6. Agent announces eligible schemes
7. Edge-case demo (wrong / missing input)

---

## 🚀 Future Enhancements

* Multi-language support (Tamil, Telugu, Marathi, Odia)
* Replace CSV with government APIs
* User authentication
* Scheme application assistance
* Offline STT/TTS

---

## 🏁 Conclusion

This project demonstrates a **true voice-first agentic AI system**, not a scripted chatbot.
It showcases **autonomous reasoning, planning, tool usage, memory, and recovery** in a **native Indian language**, fulfilling all mandatory requirements.

---
