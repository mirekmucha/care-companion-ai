## MVP specification

### Product name
**Care Companion Agent**

### Product summary
Care Companion Agent is an AI assistant for family caregivers of older adults. The product helps caregivers maintain a senior profile, log care-related events in natural language, use stored context across interactions, generate doctor-ready summaries, and enforce safe non-diagnostic behavior.

### Goal
Reduce caregiver cognitive load by turning scattered observations into structured, context-aware support. 

### In-scope features
1. Senior profile  
2. Care logging  
3. Memory use  
4. Doctor summary  
5. Safety boundaries

### Out of scope
- Daily care plan
- Notifications and reminders
- Calendar integration
- Multi-patient support
- Wearable or device integration
- External medical system integration
- Billing, auth, and advanced collaboration

## Functional specification

### 1. Senior profile
The system must allow the caregiver to create and update a profile for one older adult. The profile provides the core context used by the agent during later actions.

**Stored fields**
- Full name
- Age
- Chronic conditions
- Allergies
- Mobility notes
- Emergency contact
- General care notes
- Last updated timestamp

**Expected behavior**
- The system validates required fields before saving.
- The saved profile is available to the agent in later workflows.
- Profile changes are reflected in future responses and summaries.

### 2. Care logging
The system must let the caregiver enter observations and care-related events in natural language. The agent should interpret the note, classify it, and save it as a structured event.

**Supported event types**
- Symptom
- Medication
- Observation
- Incident
- Appointment
- Other

**Expected behavior**
- The caregiver can enter a free-text note.
- The agent classifies the note into an event type.
- If the note lacks key details, the agent asks short follow-up questions.
- The event is stored with timestamp, summary, tags, and attention level.
- Event history is visible in reverse chronological order.

### 3. Memory use
The system must use profile and recent history as memory context for future interactions. The goal is to avoid stateless, generic outputs.

**Expected behavior**
- The agent uses profile details when answering relevant prompts.
- The agent uses recent care events when generating outputs.
- The agent can recognize repeated or recent patterns.
- If historical data is unavailable, the system explicitly states limited context rather than pretending it knows more.

### 4. Doctor summary
The system must generate a concise summary for a medical appointment based on stored data. This output should help the caregiver prepare, not replace medical judgment.

**Summary sections**
- Current symptoms
- Recent changes
- Medications / important notes
- Questions for the doctor

**Expected behavior**
- The caregiver selects a date range.
- The system generates a structured summary using the profile and relevant event history.
- The summary can be copied.
- The system should support basic traceability by showing which events were used or by clearly grounding the output in stored history.

### 5. Safety boundaries
The system must stay within clear safety limits. It should support caregiving organization, not diagnosis.

**Expected behavior**
- The agent must not provide a medical diagnosis.
- The agent must not invent measurements, symptoms, medications, or history.
- The agent should ask clarifying questions when needed.
- The agent should recommend contacting a clinician or emergency services when the situation appears serious.
- The system should display a clear disclaimer that it is not a substitute for professional medical advice.

## Non-functional requirements

### Usability
- The main workflows should be understandable without technical knowledge.
- A caregiver should be able to save a note and generate a summary with minimal onboarding.

### Transparency
- The system should make it reasonably clear when it is using profile data and history.
- The system should not imply hidden knowledge outside stored context.

### Reliability
- Saved data should remain consistent across profile, event history, and summary generation.
- A failed save or incomplete summary should result in a clear user-facing message.

### Safety
- Safety rules must apply in every conversation and output flow.
- Non-diagnostic behavior takes priority over fluency or completeness. 


## Antigravity-ready short brief

Use this as the short implementation brief:

- Build a web app called **Care Companion Agent**.
- Scope is limited to: senior profile, care logging, memory use, doctor summary, and safety boundaries.
- The system is for one family caregiver supporting one older adult.
- The app must save structured profile data, convert natural-language notes into care events, reuse context from stored profile and recent events, generate a doctor-ready summary for a selected date range, and enforce non-diagnostic safety behavior.
- Do not implement planning, reminders, notifications, multi-user support, or external integrations in this version.