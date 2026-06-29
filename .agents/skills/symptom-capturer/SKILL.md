---
name: symptom-capturer
description: The skill responsible for capturing new senior symptom reports, asking relevant follow-up questions, and converting caregiver input into structured symptom records without diagnosing or inventing details.
---

# Symptom Capturer Skill
When new symptom is captured you MUST follow the instructions below.

## Instructions
1. The user can submit a free-text note.
2. The system classifies the note into an event type.
3. The system stores the event with timestamp and summary.
4. The event appears in event history.
5. If the note lacks key details, the agent asks short follow-up questions.

## Example

User: "She has been weaker since morning and skipped breakfast"

Agent response: "I have recorded this as a new event. I'll mark it as needing attention. Would you like me to set a reminder for you to check in on her later?"