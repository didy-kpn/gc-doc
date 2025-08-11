# Tasks: {{args}}

## 1. Implementation Plan
[Brief description of the implementation approach, e.g., "The implementation will be done in a test-driven manner, starting with the data model, followed by the service layer, and finally the API endpoints."]

## 2. Atomic Task Requirements
- **File Scope**: Touches 1-3 related files maximum.
- **Single Purpose**: Has one clear, testable outcome.
- **Agent-Friendly**: Clear, imperative instructions with minimal ambiguity.

## 3. Task Format Guidelines
- Use checkbox format: `- [ ] 1. Task Description`
- **Specify files**: Always include exact file paths to create/modify.
- **Reference design/requirements**: Map each task to the design sections and requirements it fulfills. `_Design: 8_`, `_Requirements: 3.1_`

---

- [ ] **1. Task: Write failing unit tests for the `{{args}}` data model.**
  - **Files to create:** `src/models/{{args}}.test.ts`
  - **Details:** Based on the data contract in the design document, write unit tests that verify the validation logic. Test both valid and invalid data scenarios. The tests should fail initially.
  - **_Leverage: `jest`, `zod`_**
  - **_Design: 8_**, **_Requirements: 3.1_**

- [ ] **2. Task: Create the `{{args}}` data model to pass the tests.**
  - **Files to create:** `src/models/{{args}}.ts`
  - **Details:** Implement the TypeScript interface and Zod schema for the `{{args}}` model. Ensure all tests from the previous task now pass.
  - **_Leverage: `src/models/Base.ts`_**
  - **_Design: 8_**, **_Requirements: 3.1_**

- [ ] **3. Task: Write failing integration tests for the POST /api/{{args}} endpoint.**
  - **Files to create:** `src/api/{{args}}.test.ts`
  - **Details:** Write an integration test that sends a POST request to the (not-yet-existing) endpoint and asserts a 201 response and correct database state.
  - **_Leverage: `supertest`, `jest`_**
  - **_Design: 7_**, **_Requirements: 3.1_**

- [ ] **4. Task: Implement the POST /api/{{args}} endpoint to pass the tests.**
  - **Files to create/modify:** `src/api/{{args}}.ts`, `src/services/{{args}}Service.ts`
  - **Details:** Create the service and API endpoint logic required to handle the POST request, validate data, and save it to the database. Ensure the integration test passes.
  - **_Leverage: `express`, `zod`_**
  - **_Design: 7_**, **_Requirements: 3.1_**
