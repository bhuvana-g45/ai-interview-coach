# 🎙️ AI Interview Coach — Generative AI Mock Interview & Assessment Suite

An interactive, zero-backend Generative AI web application that prepares students for technical and behavioral campus placements. Candidates select a target job role, answer dynamically generated interview questions via **live voice (Speech-to-Text)** or **text**, complete **role-specific MCQs and live coding challenges with automated test cases**, and receive real-time **Clarity & Confidence** feedback.

---

## ✨ Key Features

1. **Dynamic Role & Resume-Aware Question Generation**
   - Supports preset roles (*Java Backend Developer, Software Developer, Data Analyst, Generative AI Engineer, HR Round*) as well as any custom role.
   - Incorporates candidate resume highlights and conversation history to generate adaptive follow-up questions.
2. **Multimodal Voice & Text Interview Mode**
   - **AI Voice Output (TTS):** Reads interview questions aloud using the browser `SpeechSynthesis` API.
   - **Live Speech-to-Text (STT):** Transcribes spoken answers in real time via the `Web Speech API` (`SpeechRecognition`).
   - **Speech Telemetry Engine:** Computes live **Words Per Minute (WPM)** and detects filler/hedging words (*"um", "uh", "like", "basically", "actually"*).
   - **AI Clarity & Confidence Evaluator:** Grades responses (`1–10`) on structural clarity and assertive delivery, highlights improvements, and rewrites the candidate's answer into a high-impact STAR-format response.
3. **Interactive Technical Assessment Mode (MCQs + Live Coding)**
   - **Auto-Graded MCQs:** Generates 3 conceptual multiple-choice questions per role with instant explanations.
   - **In-Browser Coding Sandbox & Test Runner:** Generates 2 coding problems with executable test cases (`PASS` / `FAIL` verification) and **Live AI Big-O Time/Space Complexity Review**.
4. **Zero-Cost, Zero-Backend Architecture**
   - Runs 100% client-side in Chrome/Edge with BYOK (Bring Your Own Key) support for **Groq Free API** and **Google AI Studio (Gemini Flash)**, plus an **Offline Demo Mode** fallback.

---

## 🏗️ System Architecture

```text
+-------------------------------------------------------------------+
|                     Frontend (HTML5 + Tailwind CSS + JS)          |
|                                                                   |
|  [Role & Resume Setup] ---> [Prompt & Context Builder]            |
|                                      |                            |
|         +----------------------------+--------------------+       |
|         |                                                 |       |
|         v                                                 v       |
|  [Voice & Text Interview]                      [Technical Round]  |
|   - Web Speech API (STT/TTS)                    - Dynamic MCQs    |
|   - WPM & Filler Telemetry                      - JS Sandbox Eval |
|         |                                                 |       |
|         +----------------------------+--------------------+       |
|                                      |                            |
|                                      v                            |
|                     [LLM Inference Layer (REST API)]              |
|               Groq (OpenAI-compatible) / Google Gemini            |
|                    (Strict JSON Schema Enforcement)               |
+-------------------------------------------------------------------+
