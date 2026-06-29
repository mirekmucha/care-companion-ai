# Care Companion Assistant 👵🤖

**Care Companion Assistant** is an AI-powered assistant designed for family caregivers of older adults. It reduces caregiver cognitive load by turning scattered daily observations, symptoms, and care details into structured, context-aware records and doctor-ready summaries.

---

## 🚀 Key Features

1. **👵 Senior Profile**
   - Maintain a dedicated profile for a senior, tracking details such as age, chronic conditions, allergies, mobility notes, emergency contacts, and general care preferences.
   
2. **🤖 Intelligent Care Logging**
   - Log daily care events (symptoms, medication, observation, incident, appointment, etc.) using natural language.
   - The assistant automatically interprets, classifies, and logs the details with structured tags and attention levels.
   - Provides interactive follow-up questions to fill in critical missing details.

3. **🧠 Context-Aware Memory**
   - The assistant references the active profile and logged event history to provide personalized, context-aware answers, avoiding generic or stateless advice.

4. **📋 Doctor-Ready Appointment Summaries**
   - Generate structured medical appointment summaries over a chosen date range.
   - Summarizes active symptoms, recent changes, current medications/notes, and potential questions for the clinician.
   - Traceability view details exactly which logged events were used to construct the summary.

5. **🛡️ Safety & Non-Diagnostic Boundaries**
   - Enforces a strict boundary against medical diagnosis or inventing clinical details.
   - Recommends contacting emergency services or professional clinicians when high-attention events are encountered.
   - Clear disclaimers indicating it is a support tool, not a substitute for professional medical advice.

---

## 🛠️ Technology Stack

- **Frontend**: Vanilla HTML5, CSS3, and JavaScript (ES6+).
- **Styling**: Modern, premium, responsive custom CSS design featuring cohesive HSL color variables, smooth transitions, and glassmorphism cards.
- **State & Storage**: Client-side storage using `localStorage` for complete user privacy and offline capability.

---

## 📁 Directory Structure

```text
CareCompanionAgent/
├── .agents/            # Custom AI agent guidelines & templates
├── specs/              # Product specifications and user stories
│   ├── 01 - High-level spec.md
│   ├── 02 - User stories.md
│   └── 03 - Bdd spec.md
├── app.js              # Application logic and local AI simulation / handling
├── index.html          # Core application structure & layouts
├── index.css           # Premium stylesheet & UI/UX design tokens
└── README.md           # Project documentation (this file)
```

---

## 🚦 Getting Started

1. **Clone the repository**:
   ```bash
   git clone https://github.com/mirekmucha/care-companion-ai.git
   cd care-companion-ai
   ```
2. **Run the application**:
   - Simply open `index.html` directly in any modern web browser.
   - Or, run a local development server (e.g., using VS Code Live Server or python `http.server`):
     ```bash
     python -m http.server 8000
     ```
     Then open `http://localhost:8000` in your browser.

---

## 🔍 Developer Tools & Logging

To help developers verify that the agent's code is properly invoked:
- **Application Logs**: Key operations (user input submission, safety checks, event classification, and summary generation) are logged to the browser's developer console with the prefix `[Care Companion Assistant]`.
- **How to view the logs**:
  1. Open the application in your browser.
  2. Open the developer tools (Press `F12` or `Ctrl + Shift + I` / `Cmd + Option + I`).
  3. Navigate to the **Console** tab to view live agent invocations and execution details.

## 💾 Local Persistence
- All senior profile details and logged care history are saved locally inside the browser's `localStorage` (scoped to the site's origin/domain). No data is sent to external servers, providing offline functionality and privacy out of the box.

---

## 📄 License & Disclaimer

This project is intended for demonstration and caregiver support organizational purposes only. It is **not** a substitute for professional medical advice, diagnosis, or treatment. Always consult with a qualified healthcare provider regarding any medical conditions.
