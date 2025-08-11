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

## 5. Data Flow
[Describe how data flows through the system for the main user scenarios. Use a sequence diagram.]

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant DB
    
    User->>Frontend: Perform Action (e.g., Submit Form)
    Frontend->>API: POST /api/{{args}}
    API->>DB: Insert new record
    DB-->>API: Return new record
    API-->>Frontend: Respond with 201 Created
    Frontend-->>User: Show success message
```

## 6. API Endpoints
[Provide a detailed API endpoint table.]

| Method | Route                  | Purpose                | Auth?    | Success Codes | Error Codes       |
|--------|------------------------|------------------------|----------|---------------|-------------------|
| GET    | /api/{{args}}           | List all resources     | Required | 200           | 401, 500          |
| POST   | /api/{{args}}           | Create a new resource  | Required | 201           | 400, 401, 500     |
| GET    | /api/{{args}}/{id}      | Get a single resource  | Required | 200           | 401, 404, 500     |
| PUT    | /api/{{args}}/{id}      | Update a resource      | Required | 200           | 400, 401, 404, 500|
| DELETE | /api/{{args}}/{id}      | Delete a resource      | Required | 204           | 401, 404, 500     |

## 7. Components and Interfaces
### Component: [Component Name]
- **Purpose:** [What this component does.]
- **Interfaces/API:** [Public methods, API endpoints, props.]
- **Dependencies:** [What it depends on.]

## 8. Data Models & Entity Relationships

### Entity Relationship Diagram
```mermaid
erDiagram
    USER ||--o{ {{args}} : "creates"
    {{args}} {
        string id
        string name
        datetime created_at
    }
    USER {
        string id
        string username
    }
```

### Data Contracts (Language-Specific)
*This section defines language-specific types and invariants. Example for TypeScript:*
```typescript
// Invariant: email must be a valid email format.
interface {{args}} {
  id: string;
  name: string;
  // ... other properties
  createdAt: Date;
  updatedAt: Date;
}
```

## 9. Error Handling
- **Scenario 1:** [Description of a potential error.]
  - **Handling:** [How the system will handle it.]
  - **User Impact:** [What the user will see.]

## 10. Testing Strategy
- **Unit Testing:** [Key components/logic to unit test.]
- **Integration Testing:** [Key integration points to test.]
- **End-to-End Testing:** [Critical user flows to test via E2E.]