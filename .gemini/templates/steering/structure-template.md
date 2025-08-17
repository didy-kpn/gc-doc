# Project Structure

## 1. Directory Organization
[Define your project's directory structure with brief explanations. Provide examples for different project types to illustrate common patterns.]

*   **General/Web Application Example:**
    ```
    project-root/
    ├── docs/         # Documentation files
    ├── src/          # Source code
    │   ├── api/      # API endpoints and controllers
    │   ├── components/ # Reusable UI components (for frontend)
    │   ├── models/   # Data models and types
    │   └── services/ # Business logic
    ├── tests/        # Test files
    ├── config/       # Configuration files
    └── package.json  # Project metadata and dependencies (e.g., for Node.js)
    ```

*   **CLI Tool Example (Python):**
    ```
    cli-tool-root/
    ├── docs/         # Documentation
    ├── src/          # Source code
    │   ├── cli/      # Main CLI entry point and command definitions
    │   ├── core/     # Core logic and utilities
    │   └── utils/    # Helper functions
    ├── tests/        # Unit and integration tests
    ├── config/       # Default configuration
    ├── scripts/      # Helper scripts (e.g., build, deploy)
    └── requirements.txt # Python dependencies
    ```

*   **Library/SDK Example (Go):**
    ```
    library-root/
    ├── docs/         # Documentation
    ├── internal/     # Internal packages not exposed to users
    ├── pkg/          # Publicly exposed packages/modules
    │   ├── auth/
    │   └── client/
    ├── examples/     # Usage examples
    ├── tests/        # Tests
    ├── go.mod        # Go module definition
    └── README.md
    ```

*   **Data Processing Project Example:**
    ```
    data-project-root/
    ├── data/         # Data storage
    │   ├── raw/      # Raw, immutable input data
    │   ├── processed/ # Cleaned and transformed data
    │   └── output/   # Final results, reports
    ├── notebooks/    # Jupyter notebooks for exploration/analysis
    ├── src/          # Source code for processing scripts/pipelines
    │   ├── ingest/
    │   ├── transform/
    │   └── models/   # Data models/schemas
    ├── tests/        # Tests for processing logic
    ├── config/       # Configuration for data sources, pipelines
    └── requirements.txt # Dependencies
    ```

## 2. Naming Conventions
[Define consistent naming conventions for files, components, variables, types, etc. Provide examples relevant to the project's primary language(s) and ecosystem.]

*   **Files**:
    *   [e.g., `kebab-case.ts` (TypeScript/JavaScript)]
    *   [e.g., `snake_case.py` (Python)]
    *   [e.g., `snake_case.go` (Go)]
*   **Components/Modules/Packages**:
    *   [e.g., `PascalCase.tsx` (React Components)]
    *   [e.g., `PascalCase` (Go packages/types)]
    *   [e.g., `snake_case` (Python modules/packages)]
*   **Variables/Functions**:
    *   [e.g., `camelCase` (JavaScript/TypeScript)]
    *   [e.g., `snake_case` (Python, Go)]
*   **Types/Interfaces**:
    *   [e.g., `PascalCase` (TypeScript, Go)]
    *   [e.g., `PascalCase` or `snake_case` (Python, depending on context/framework)]

## 3. Code Organization Principles
[Outline the fundamental principles guiding how code is structured and organized within the project.]

1.  **Single Responsibility Principle (SRP):** Each file, module, or component should have one clear, well-defined purpose or responsibility.
2.  **Modularity:** Code should be organized into reusable, independent modules or packages with clear interfaces, minimizing coupling between them.
3.  **Separation of Concerns:** Different aspects of the system (e.g., UI, business logic, data access) should be handled by distinct parts of the codebase.
4.  **Consistency:** Maintain consistent coding style, patterns, and conventions throughout the project.
5.  **Readability:** Code should be easy to understand and maintain by other developers.