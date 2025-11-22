# ⚡ MockMate Pro

**AI-Powered Career Coach & Interview Simulator**

Ace your dream job with real-time voice simulation, behavioral analysis, and instant professional feedback.

---

![logo](https://cdn-icons-png.flaticon.com/512/4712/4712009.png)

Badges:
- ![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
- ![Streamlit](https://imgshields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
- ![Gemini](https://img.shields.io/badge/Google%20Gemini-8E75B2?style=for-the-badge&logo=google%20gemini&logoColor=white)
- ![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## Overview

**MockMate Pro** is a full-cycle interview simulation platform that mimics high-pressure interview environments. Powered by Google Gemini, it conducts adaptive technical, behavioral, and situational interview rounds, listens to voice input, analyzes answers in real time, and generates a professional PDF performance report.

The project addresses the **"Interview Practice Partner"** problem from the Eightfold.ai assignment.

---

## Demo Showcase

1. The Launchpad
   Configure role, experience level, and focus areas (e.g., System Design, Soft Skills).
   ![Landing Page Screenshot](assets/landing_page.png)

2. Real-Time Simulation
   Voice-enabled interaction with "Thinking" indicators and dynamic typing effects. The AI adapts to your answers.
   ![Live Interview Screenshot](assets/interview_live.png)

3. Performance Analytics
   Instant feedback on Communication vs. Technical skills, with a detailed breakdown.
   ![Analysis Dashboard Screenshot](assets/analysis_dashboard.png)

Sample report: [assets/MockMate_Report.pdf]

---

## Key Features

- 🎙️ Voice-to-Text Integration (microphone input, required by assignment)
- 🧠 Adaptive AI Logic (contextual follow-ups, assessed under Agentic Behaviour)
- 🎨 Glassmorphism UI with Dark Mode (Prioritizes conversation quality over just functionality)
- 📊 Quantitative Scoring (skill-level breakdown, required assessment)
- 📥 Export transcript (JSON) and formatted PDF report (Professional deliverable)

---

## Technical Implementation & Design Decisions (For Evaluators)

### 1. Architectural Notes
The application is split into three main files:
* **`interview_state.py`**: Manages the persistent session state (`dataclass`), including the full transcript, role configuration, and current interview stage.
* **`interview_agent.py`**: Contains the core AI logic, including dynamic system prompt generation, `gTTS` voice output, and the feedback report generation using a robust Regex-based JSON cleaner.
* **`app.py`**: Handles all Streamlit UI, state persistence, input/output, and the custom FPDF report generation class.

### 2. Intelligent Flow Control
* **Stage Advancement:** The system uses a hidden keyword (`"MOVING_ON"`) in the agent's response to signal stage completion, allowing the AI to naturally conclude a topic before the system forces a transition.
* **Gemini Configuration:** The final feedback report is generated using `response_mime_type: "application/json"` to ensure structured output, and a low temperature (`0.2`) for analytical consistency.

### 3. Addressing Evaluation Criteria

| Criteria | Implementation Detail |
| :--- | :--- |
| **Prioritize Conversation Quality** | Extensive use of custom CSS in `app.py` to create a polished, intuitive, and modern UI that enhances user engagement over plain Streamlit components. |
| **Interaction Mode** | Supports both Text Chat and Microphone Input (`streamlit-mic-recorder`), with `gTTS` providing audio responses for a fully voice-preferred experience. |
| **Technical Implementation** | Uses dynamic system instructions to adapt tone and required knowledge based on the user's selected **Role** and **Experience Level**. |

### 4. Demo Scenarios Handled (Required)

| Scenario | Agent Behavior Demonstrated |
| :--- | :--- |
| **The Efficient User** | The AI interviewer is prompted to **"Dig Deeper"** if the candidate's answer is shallow, ensuring the assessment is thorough, not brief. |
| **The Edge Case User** | The AI's system prompt instructs it to **"gently steer the conversation back to the topic"** if the user goes off-topic or provides invalid inputs, maintaining focus on the interview stage. |

---

## Installation

Prerequisites:
- Python 3.10+
- Google Gemini API Key

1. Clone the repository
```bash
git clone [https://github.com/27arya23/Eightfold_Interview_Agent.git](https://github.com/27arya23/Eightfold_Interview_Agent.git)
cd Eightfold_Interview_Agent

2. Create and activate a virtual environment

python -m venv venv
# Windows
.\venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Add environment variables Create a .env in the project root:

GEMINI_API_KEY=your_api_key_here

5. Run the app

streamlit run app.py

## Project Structure

Eightfold_Interview_Agent/
├── app.py                 # Main Streamlit application
├── interview_agent.py     # AI logic & prompt engineering
├── interview_state.py     # Session state management
├── requirements.txt       # Python dependencies
├── .env                   # API keys (exclude from VCS)
└── assets/                # Images and sample PDF
    ├── landing_page.png
    ├── interview_live.png
    └── MockMate_Report.pdf


## License
Distributed under the MIT License. See LICENSE for details.

---

Built with 💜
