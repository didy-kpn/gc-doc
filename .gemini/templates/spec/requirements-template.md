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

### Requirement 3.2: [Another Major Feature Area]
**User Story:** As a [role], I want [another feature], so that [another benefit].

**Acceptance Criteria:**
1.  **WHEN** [event] **AND** [condition], **THEN** the system **SHALL** [response].

## 4. Non-Functional Requirements
- **Security:** [e.g., All API endpoints for this feature must be authenticated via JWT. Input data must be validated to prevent XSS.]
- **Performance:** [e.g., The API response time for GET requests must be under 200ms on average.]
- **Reliability:** [e.g., The service must maintain 99.9% uptime and handle concurrent requests gracefully.]
- **Usability:** [e.g., Error messages returned by the API must be clear and actionable.]
