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
- **Reference requirements**: Map each task to the requirements it fulfills. `_Requirements: 3.1_`
- **Reference existing code**: Note any existing code to leverage. `_Leverage: path/to/file.ts_`

--- 
*Example TDD-style Tasks:*

- [ ] **1. Task: Write failing unit tests for the `{{args}}` data model.**
  - **Files:** `src/models/{{args}}.test.ts`
  - **Details:** Write unit tests to verify the validation logic of the `{{args}}` model. Test both valid and invalid data scenarios. The tests should fail initially.
  - **_Leverage: `jest`, `zod`_**
  - **_Requirements: 3.1_**

- [ ] **2. Task: Create the `{{args}}` data model to pass the tests.**
  - **Files:** `src/models/{{args}}.ts`
  - **Details:** Implement the TypeScript interface and Zod schema for the `{{args}}` model, based on the data contracts in `design.md`. Ensure all tests from the previous task now pass.
  - **_Leverage: `src/models/Base.ts`_**
  - **_Requirements: 3.1_**

- [ ] **3. Task: Write failing integration tests for the `{{args}}` service.**
  - **Files:** `src/services/{{args}}Service.test.ts`
  - **Details:** Write integration tests for the service layer. Mock the database layer. Test the core business logic (create, update, get).
  - **_Leverage: `jest`_**
  - **_Requirements: 3.1, 3.2_**

- [ ] **4. Task: Implement the `{{args}}` service to pass the tests.**
  - **Files:** `src/services/{{args}}Service.ts`
  - **Details:** Create a service class that handles the core business logic for `{{args}}` data. Implement the methods needed to make the integration tests pass.
  - **_Leverage: `src/services/DatabaseService.ts`_**
  - **_Requirements: 3.1, 3.2_**