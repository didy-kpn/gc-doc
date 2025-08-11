# Design: {{args}}

## 1. Overview
[High-level description of the feature and its place in the overall system, referencing key requirements from `requirements.md`.]

## 2. Steering Document Alignment
- **Technical Standards (`tech.md`):** [How the design follows documented technical patterns and standards.]
- **Project Structure (`structure.md`):** [How the implementation will follow project organization conventions.]

## 3. Code Reuse Analysis
[What existing code (components, services, utilities) will be leveraged, extended, or integrated with this feature.]
- **Existing Components to Leverage:**
  - `[Component/Utility Name]`: [How it will be used.]
- **Integration Points:**
  - `[Existing System/API]`: [How the new feature will integrate.]

## 4. Architecture
[Describe the overall architecture and design patterns used. Include a Mermaid diagram for clarity.]

```mermaid
graph TD
    A[Client] --> B[API Gateway]
    B --> C[Service: {{args}}]
    C --> D[Data Access Layer]
    D --> E[Database]
```

## 5. Components and Interfaces
### Component: [Component Name]
- **Purpose:** [What this component does.]
- **Interfaces/API:** [Public methods, API endpoints, props.]
- **Dependencies:** [What it depends on.]

## 6. Data Models & Contracts (Language-Specific)
*This section defines language-specific types and invariants. Example for TypeScript:*
```typescript
// Invariant: email must be a valid email format.
interface User {
  id: string;
  name: string;
  email: string;
}
```

## 7. Error Handling
- **Scenario 1:** [Description of a potential error.]
  - **Handling:** [How the system will handle it.]
  - **User Impact:** [What the user will see.]

## 8. Testing Strategy
- **Unit Testing:** [Key components/logic to unit test.]
- **Integration Testing:** [Key integration points to test.]
