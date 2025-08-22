# Design: {{args}}

## 1. Overview
[High-level description of the feature and its place in the overall system.]

## 2. Requirements Mapping
[Traceability matrix showing how design components map to specific requirements from `requirements.md`.]
- **Component [Component Name]:** Fulfills Requirement(s) 3.1, 3.2
- **API Endpoint `/api/{{args}}`:** Fulfills Requirement(s) 3.1

## 3. Steering Document Alignment
- **Technical Standards (`tech.md`):** [How the design follows documented technical patterns and standards.]
- **Project Structure (`structure.md`):** [How the implementation will follow project organization conventions.]

## 4. Code Reuse Analysis
- **Existing Components to Leverage:**
  - `[Component/Utility Name]`: [How it will be used.]
- **Integration Points:**
  - `[Existing System/API]`: [How the new feature will integrate.]

## 5. Architecture
[Describe the overall architecture and design patterns used. Include a Mermaid diagram for clarity.]

```mermaid
graph TD
    A[Client] --> B[API Gateway]
    B --> C[Service: {{args}}]
    C --> D[Data Access Layer]
    D --> E[Database]
```

## 6. Data Flow
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

## 7. API Endpoints
| Method | Route                  | Purpose                | Auth?    | Request Body (Example) | Success Codes | Error Codes       |
|--------|------------------------|------------------------|----------|------------------------|---------------|-------------------|
| POST   | /api/{{args}}           | Create a new resource  | Required | `{ "name": "example" }`  | 201           | 400, 401, 500     |
| GET    | /api/{{args}}/{id}      | Get a single resource  | Required | N/A                    | 200           | 401, 404, 500     |

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
*Example for TypeScript:*
```typescript
// Invariant: name must not be empty.
interface {{args}} {
  id: string;
  name: string;
  createdAt: Date;
}
```

## 9. Security Considerations
- **Authentication:** All endpoints will be protected and require a valid JWT.
- **Authorization:** [Specify roles, e.g., Only "Admin" users can delete resources.]
- **Input Validation:** All incoming data will be validated using Zod to prevent injection attacks.

## 10. Performance Considerations
- **Indexing:** The `name` field in the `{{args}}` table will be indexed to ensure fast lookups.
- **Caching:** [Specify caching strategy if applicable, e.g., GET responses will be cached for 5 minutes.]

## 11. Testing Strategy
- **Unit Testing:** Service logic and utility functions will be unit-tested in isolation.
- **Integration Testing:** API endpoints will be tested to verify their interaction with the database and other services.
- **End-to-End Testing:** The critical user flow of creating and viewing a resource will be tested via E2E tests.
