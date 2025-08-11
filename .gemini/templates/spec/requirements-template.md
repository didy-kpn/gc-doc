# Requirements: {{args}}

## 1. Introduction
[Provide a brief overview of the feature, its purpose, and its value to users.]

## 2. Alignment with Product Vision
[Explain how this feature supports the goals outlined in `.gemini/steering/product.md`.]

## 3. Functional Requirements
*All acceptance criteria MUST use the EARS (Easy Approach to Requirements Syntax) format.*

### Requirement 3.1: [Major Feature Area]
**User Story:** As a [role], I want [feature], so that [benefit].

**Acceptance Criteria:**
1.  **WHEN** [a specific event occurs], **THEN** the system **SHALL** [perform a specific action].
2.  **IF** [a specific condition is true], **THEN** the system **SHALL** [have a specific property].
3.  (Example) **WHEN** the user clicks the "Save" button, **THEN** the system **SHALL** persist the form data to the database.

### Requirement 3.2: [Another Major Feature Area]
**User Story:** As a [role], I want [another feature], so that [another benefit].

**Acceptance Criteria:**
1.  **WHEN** [event] **AND** [condition], **THEN** the system **SHALL** [response].
2.  (Example) **IF** the user is an "Admin" **AND** they are on the settings page, **THEN** the system **SHALL** display the "Delete Project" button.

## 4. Non-Functional Requirements
- **Security:** [e.g., All API endpoints for this feature must be authenticated via JWT.]
- **Performance:** [e.g., The user dashboard must load in under 2 seconds.]
- **Reliability:** [e.g., The service must maintain 99.9% uptime.]