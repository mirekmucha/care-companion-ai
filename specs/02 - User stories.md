## User stories

### Epic: Senior Profile

**US-01**  
As a family caregiver, I want to create a senior profile so that the agent can use real care context in future interactions.

**Acceptance criteria**
- The user can save full name, age, chronic conditions, allergies, mobility notes, emergency contact, and care notes.
- The system validates required fields.
- The saved profile becomes available to the agent.

**US-02**  
As a family caregiver, I want to edit the senior profile so that the system uses the most current information.

**Acceptance criteria**
- The user can update profile fields after creation.
- The updated data is used in later interactions.
- The system stores the last updated timestamp.

### Epic: Care Logging

**US-03**  
As a family caregiver, I want to log a care event in natural language so that I can quickly capture important observations.

**Acceptance criteria**
- The user can submit a free-text note.
- The system classifies the note into an event type.
- The system stores the event with timestamp and summary.
- The event appears in event history.


**US-04**  
As a family caregiver, I want to review event history so that I can track what has happened recently.

**Acceptance criteria**
- Events are shown in reverse chronological order.
- Each event includes timestamp, type, short summary, and attention level.
- History is available as context for later outputs.

### Epic: Memory Use

**US-05**  
As a family caregiver, I want the agent to use profile data and recent history so that the output is context-aware instead of generic.

**Acceptance criteria**
- The agent uses relevant profile information in later responses.
- The agent uses recent events when generating outputs.
- The agent can reflect repeated or recent patterns.


### Epic: Doctor Summary

**US-06**  
As a family caregiver, I want to generate a doctor summary for a selected date range so that I can prepare for an appointment efficiently.

**Acceptance criteria**
- The user can select a date range.
- The generated summary includes current symptoms, recent changes, medications or important notes, and questions for the doctor.
- The summary is based on stored profile and event history.

### Epic: Safety Boundaries

**US-7**  
As a user, I want the agent not to diagnose medical conditions so that the application remains safe and responsible.

**Acceptance criteria**
- If asked for a diagnosis, the agent refuses to diagnose.
- The system uses non-diagnostic language.
- The UI displays a medical disclaimer.

**US-8**  
As a user, I want the agent to avoid fabricated information so that I can trust the output.

**Acceptance criteria**
- The agent never invents symptoms, measurements, medications, or prior history.
- If needed information is missing, the agent asks for clarification.

## Suggested MVP

For the smallest useful MVP, implement:
- US-01
- US-02
- US-03
- US-04
- US-05
- US-06
- US-07
- US-08