# Requirements: {{args}}

## 1. Introduction
[Provide a brief overview of the feature, its purpose, and its value to users. This section should be concise and set the stage for the detailed requirements that follow.]

## 2. Project Type & Scope
[Clearly define the type of project this document pertains to and its overall scope. This helps in tailoring the interpretation of subsequent sections.]

*   **Project Type**: [e.g., Web Application (Frontend/Backend), CLI Tool, Library/SDK, Automated Trading System, Desktop Application, Mobile App, Data Processing Script]
*   **Primary Purpose**: [What is the main problem this project solves or the primary value it delivers?]
*   **Non-Goals**: [What is explicitly out of scope for this project/feature?]

## 3. Alignment with Product Vision
[Explain how this feature supports the goals outlined in `docs/steering/product.md` or the overarching product/project vision.]

## 4. System Capabilities & Behaviors (Functional Requirements)
*All acceptance criteria MUST use the EARS (Easy Approach to Requirements Syntax) format.*
[Describe the specific functions and behaviors the system must perform. These are the "what" the system does.]

### Capability 4.1: [Major Feature Area or System Function]
**Stakeholder Goal/System Goal:** As a [role/system], I want [capability], so that [benefit/outcome].

**Acceptance Criteria:**
1.  **WHEN** [a specific event occurs], **THEN** the system **SHALL** [perform a specific action].
2.  **IF** [a specific condition is true], **THEN** the system **SHALL** [have a specific property].

**Examples for diverse project types:**

*   **Web Application (User-facing):**
    *   **Stakeholder Goal:** As a registered user, I want to log in securely, so that I can access my personalized dashboard.
    *   **Acceptance Criteria:**
        1.  **WHEN** a user submits valid credentials to the login form, **THEN** the system **SHALL** authenticate the user and redirect them to `/dashboard`.
        2.  **IF** a user submits invalid credentials, **THEN** the system **SHALL** display an error message "Invalid username or password."
*   **CLI Tool:**
    *   **System Goal:** The CLI tool shall process a given input file and output transformed data.
    *   **Acceptance Criteria:**
        1.  **WHEN** the `process` command is executed with a valid `--input` file path, **THEN** the system **SHALL** read the file content.
        2.  **WHEN** the input file is successfully processed, **THEN** the system **SHALL** write the transformed data to standard output in JSON format.
        3.  **IF** the `--output` flag is provided, **THEN** the system **SHALL** write the transformed data to the specified file instead of standard output.
*   **Automated Trading System:**
    *   **System Goal:** The trading system shall execute buy/sell orders based on predefined strategy signals.
    *   **Acceptance Criteria:**
        1.  **WHEN** a buy signal is generated for a specific asset, **THEN** the system **SHALL** place a market buy order on the configured exchange.
        2.  **IF** an order fails to execute within 500ms, **THEN** the system **SHALL** log the failure and attempt to cancel the order.
*   **Developer Tool/Library:**
    *   **Stakeholder Goal:** As a developer, I want to use the `parseConfig` function, so that I can easily load application settings from a YAML file.
    *   **Acceptance Criteria:**
        1.  **WHEN** `parseConfig` is called with a valid YAML file path, **THEN** the system **SHALL** return a JavaScript object representing the configuration.
        2.  **IF** the YAML file contains syntax errors, **THEN** the system **SHALL** throw a `ConfigParsingError` with a descriptive message.

### 5. Quality Attributes & Constraints (Non-Functional Requirements)
[These define how well the system performs its functions, its constraints, and overall quality characteristics. Provide specific, measurable, achievable, relevant, and time-bound (SMART) metrics where possible.]

#### 5.1. Interaction Model & Interfaces
[How robust, usable, and consistent are the ways users or other systems interact with this system?]
*   **CLI Tool**: The CLI shall provide clear, concise help messages for all commands and flags.
*   **Web UI**: The user interface shall be responsive and render correctly on screen sizes from 320px to 1920px width.
*   **Web API**: All API endpoints shall return consistent error structures for different error types (e.g., 400 Bad Request, 401 Unauthorized).
*   **Automated Trading System**: The system's internal messaging interface for strategy signals shall be asynchronous and non-blocking.

#### 5.2. Data Management & Persistence
[How is data handled, stored, retrieved, and maintained? Consider integrity, consistency, and volume.]
*   **Data Processing Script**: The script shall process input files up to 10GB in size without exceeding 4GB of RAM.
*   **Web Application**: User profile data shall be stored in a PostgreSQL database and replicated across two availability zones.
*   **Automated Trading System**: All executed orders and trade fills shall be persistently logged to an immutable ledger within 100ms of confirmation from the exchange.
*   **Library**: Configuration data loaded by the library shall be validated against a predefined schema.

#### 5.3. Operations & Monitoring
[How is the system deployed, run, observed, and maintained in production?]
*   **All Project Types**: The system shall log critical errors and warnings to standard error.
*   **Web Service/Trading System**: The system shall expose Prometheus-compatible metrics for CPU usage, memory consumption, and request/order processing rates.
*   **CLI Tool**: The CLI tool shall provide a `--verbose` flag to enable detailed logging for debugging purposes.
*   **Automated Trading System**: The system shall send an alert to the operations team via PagerDuty if the connection to any exchange API is lost for more than 30 seconds.

#### 5.4. Performance & Scalability
[How fast, responsive, and capable is the system under various loads?]
*   **CLI Tool**: The script shall process 1 million records from an input file within 5 seconds.
*   **Web API**: 95% of API requests shall be served within 150ms under a load of 100 concurrent users.
*   **Automated Trading System**: The latency from receiving a market data update to placing a corresponding order shall not exceed 50ms.
*   **Web Application**: The application shall support 10,000 concurrent active users without degradation in response time.

#### 5.5. Security & Reliability
[How is the system protected from threats, and how resilient is it to failures?]
*   **All Project Types**: All sensitive configuration data (e.g., API keys, database credentials) shall be loaded from environment variables or a secure vault, not hardcoded.
*   **Web Application**: All user authentication shall use industry-standard OAuth 2.0 flows, and passwords shall be stored using bcrypt with a minimum cost factor of 12.
*   **Automated Trading System**: The system shall automatically attempt to reconnect to exchange APIs up to 5 times with exponential backoff in case of connection loss.
*   **Automated Trading System**: Private keys for cryptocurrency wallets shall be stored in a hardware security module (HSM) or equivalent secure enclave.
*   **CLI Tool**: The tool shall validate all command-line arguments to prevent shell injection vulnerabilities.

#### 5.6. Integration Points & Dependencies
[How does the system interact with external services, APIs, or hardware, and what are its external dependencies?]
*   **All Project Types**: The system shall be compatible with Python 3.9 and 3.10.
*   **Web Application**: The system shall integrate with Stripe for payment processing, adhering to their API version `2023-10-16`.
*   **Automated Trading System**: The system shall support integration with Binance and Coinbase Pro exchange APIs.
*   **Data Processing Script**: The script shall be able to read data from S3 buckets using AWS SDK v2.

#### 5.7. Testing & Validation
[How will the system's correctness, quality, and adherence to requirements be ensured?]
*   **All Project Types**: Unit test coverage for core logic shall be at least 80%.
*   **Web Application**: End-to-end tests shall cover all critical user flows (e.g., user registration, login, main feature usage).
*   **Automated Trading System**: The trading strategy shall be backtested against 5 years of historical market data, demonstrating a positive Sharpe ratio.
*   **CLI Tool**: Integration tests shall verify the correct behavior of the CLI for various valid and invalid input combinations.