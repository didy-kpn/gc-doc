# Tasks: {{args}}

## 1. Implementation Plan
[Brief description of the implementation approach, e.g., "The implementation will be done in a test-driven manner, starting with the data model, followed by the service layer, and finally the API endpoints."]

## 2. Atomic Task Requirements
**Each task must meet these criteria for optimal agent execution:**
- **File Scope**: Touches 1-3 related files maximum.
- **Single Purpose**: Has one clear, testable outcome.
- **Agent-Friendly**: Clear, imperative instructions with minimal ambiguity.

## 3. Task Format Guidelines
- Use checkbox format: `- [ ] 1. Task Description`
- **Specify files**: Always include exact file paths to create/modify.
- Reference requirements using: `_Requirements: 3.1, 4.0_`
- Reference existing code to leverage using: `_Leverage: path/to/file.ts_`

--- 
*Example Tasks:*

- [ ] **1. Task: Create the data model and validation schema.**
  - **Files:** `src/models/{{args}}.ts`
  - **Details:** Implement the TypeScript interface and Zod schema for the `{{args}}` model, based on the data contracts in `design.md`.
  - **_Leverage: `src/models/Base.ts`_**
  - **_Requirements: 3.1_**

- [ ] **2. Task: Write unit tests for the data model.**
  - **Files:** `src/models/{{args}}.test.ts`
  - **Details:** Write unit tests to verify the validation logic of the `{{args}}` model. Test both valid and invalid data scenarios.
  - **_Leverage: `jest`, `zod`_**
  - **_Requirements: 3.1_**

- [ ] **3. Task: Implement the business logic in a service layer.**
  - **Files:** `src/services/{{args}}Service.ts`
  - **Details:** Create a service class that handles the core business logic for creating, updating, and retrieving `{{args}}` data.
  - **_Leverage: `src/services/DatabaseService.ts`_**
  - **_Requirements: 3.1, 3.2_**
