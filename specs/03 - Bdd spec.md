Feature: Senior profile
  In order to give the agent reliable care context
  As a family caregiver
  I want to create and maintain a senior profile

  Scenario: Create a valid senior profile
    Given no senior profile exists
    When the caregiver creates a profile with a full name, age, chronic conditions, allergies, mobility notes, emergency contact, and care notes
    Then the system should save the senior profile
    And the saved profile should be available for future agent interactions

  Scenario: Prevent saving a profile with missing required data
    Given no senior profile exists
    When the caregiver tries to save a profile without a required field
    Then the system should reject the save
    And the system should show which required information is missing

  Scenario: Update an existing senior profile
    Given a senior profile already exists
    When the caregiver changes one or more profile fields
    Then the system should save the updated profile
    And future agent outputs should use the updated profile data

  Scenario: Use a single active senior profile in MVP
    Given a senior profile already exists
    When the caregiver opens the application
    Then the system should load the existing profile as the active senior context


Feature: Care logging
  In order to keep track of symptoms and important care events
  As a family caregiver
  I want to record care notes in natural language

  Scenario: Save a symptom note as a structured care event
    Given a senior profile exists
    When the caregiver logs the note "She has been weaker since morning and skipped breakfast"
    Then the system should classify the note as a care event
    And the system should save a structured event record
    And the record should include a timestamp, event type, short summary, and attention level

  Scenario: Save a medication-related note
    Given a senior profile exists
    When the caregiver logs the note "She missed her evening blood pressure medication"
    Then the system should classify the note as a medication event
    And the event should be stored in the care history

  Scenario: Show care history in reverse chronological order
    Given multiple care events exist
    When the caregiver views the care history
    Then the newest event should appear first
    And each event should show its timestamp, type, summary, and attention level


Feature: Memory use
  In order to avoid generic or stateless responses
  As a family caregiver
  I want the agent to use stored profile and history context

  Scenario: Use senior profile context in a relevant response
    Given a senior profile exists with chronic conditions and mobility notes
    When the caregiver asks for help that depends on the senior context
    Then the agent response should reflect relevant profile information

  Scenario: Use recent care history in a later interaction
    Given recent care events exist in the history
    When the caregiver asks for a response that depends on recent events
    Then the agent should use the recent history as part of its answer

  Scenario: Acknowledge limited context when history is missing
    Given a senior profile exists
    And no care history exists
    When the caregiver requests an output that depends on recent history
    Then the system should state that historical context is limited
    And the system should not imply knowledge of events that were never logged


Feature: Doctor summary
  In order to prepare for a medical appointment
  As a family caregiver
  I want to generate a concise doctor summary from stored information

  Scenario: Generate a doctor summary for a selected date range
    Given a senior profile exists
    And care events exist within a selected date range
    When the caregiver requests a doctor summary for that date range
    Then the system should generate a structured summary
    And the summary should include current symptoms
    And the summary should include recent changes
    And the summary should include medications or important notes
    And the summary should include questions for the doctor

  Scenario: Base the doctor summary on stored profile and care history
    Given a senior profile exists
    And relevant care events exist
    When the caregiver generates a doctor summary
    Then the summary should be grounded in stored profile data and logged events
    And the system should not add unsupported claims

  Scenario: Copy the generated doctor summary
    Given a doctor summary has been generated
    When the caregiver chooses to copy the summary
    Then the system should provide the generated summary as a copyable result

  Scenario: Handle a request when not enough history exists
    Given a senior profile exists
    And there are too few or no care events in the selected date range
    When the caregiver requests a doctor summary
    Then the system should indicate that the summary is based on limited history
    And the system should avoid inventing missing details


Feature: Safety boundaries
  In order to keep the product safe and trustworthy
  As any user
  I want the agent to stay within non-diagnostic boundaries

  Scenario: Refuse to provide a medical diagnosis
    Given the caregiver asks the agent for a diagnosis
    When the user asks "What illness does she have?"
    Then the agent should refuse to diagnose
    And the response should communicate that the system is not a substitute for professional medical advice

  Scenario: Avoid inventing measurements or facts
    Given the caregiver logs a note without any measurements
    When the user provides only a general symptom description
    Then the agent should not invent temperature, blood pressure, glucose, medication, or history details

  Scenario: Ask for clarification instead of guessing
    Given the caregiver provides an incomplete or ambiguous note
    When the missing information is important to the output
    Then the agent should ask a clarifying question
    And the agent should not guess the missing facts

  Scenario: Show the product safety disclaimer
    Given the caregiver is using the application
    When the caregiver views an agent-generated medical-related output
    Then the system should display a disclaimer that the product does not replace professional medical advice