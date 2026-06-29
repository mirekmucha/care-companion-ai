---
name: description-generator
description: The skill creates a concise, structured doctor-ready summary from the senior profile and logged care history. Organizes symptoms, recent changes, medications, and caregiver questions into a clear appointment summary, using only documented information and never diagnosing or inventing missing details.
---

# Description Generator Skill
When new description is generated you MUST follow the instructions below.

## Instructions
1. The user can select a date range.
2. The generated summary includes current symptoms, recent changes, medications or important notes, and questions for the doctor.
3. The summary is based on stored profile and event history.
4. If asked for a diagnosis, the agent refuses to diagnose.
5. The system uses non-diagnostic language.
6. The agent never invents symptoms, measurements, medications, or prior history.
7. If needed information is missing, the agent asks for clarification.


## Example

User: Generate a doctor summary for the last week.

Agent response: "Based on available information, here is a summary for the last week: "

- **Current symptoms**: She has been weaker since morning and skipped breakfast
- **Recent changes**: The apetite has decreased over the last 2 days
- **Medications or important notes**: She hasnt taken her blood pressure medication for 2 days
- **Questions for the doctor**: Can this be related to current weather conditions?