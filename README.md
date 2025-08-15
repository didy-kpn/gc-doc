[English](README.md) | [日本語](README_ja.md) | [Français](README_fr.md)

# gemini-cli-spec

This repository contains a set of custom commands and templates to enable a powerful, specification-driven development workflow within the Gemini CLI.

This workflow guides you and the AI through a structured process of software development, from initial idea to implementation, ensuring high-quality outcomes and clear documentation.

## Gemini CLI Spec-Driven Workflow

### Overview

The Gemini CLI Spec-Driven Workflow is a structured methodology for developing software in collaboration with an AI assistant. It formalizes the development process into distinct, sequential phases, each with a clear purpose and deliverable. By following this workflow, you can ensure that every feature is well-defined, designed, and broken down into manageable tasks before any code is written.

**Key benefits include:**
- **Clarity & Precision**: Ensures requirements and design are clearly defined and approved before implementation.
- **Quality Assurance**: Incorporates automated validation and mandatory human approval at each stage.
- **Consistency**: Uses templates to create consistent, high-quality documentation.
- **Efficiency**: Provides a clear, step-by-step process that streamlines AI-assisted development.

### Prerequisites

To use this workflow, you need a functioning Gemini CLI environment. The workflow is defined by the files within the `.gemini/` directory of this project. As long as you are running `gemini` from this project's root directory, the custom commands will be available.

### How to Use

The workflow follows a sequence of commands. You must run them in the specified order for each feature you develop.

**The development lifecycle for a new feature `<spec-name>`:**

1.  **Setup Steering Documents (Optional but Recommended)**
    - Run `/spec steering` to analyze your project and create foundational documents (`product.md`, `tech.md`, `structure.md`) that will guide the AI.

2.  **Initialize the Specification**
    - Run `/spec create <spec-name>`
    - This creates a dedicated directory and a `spec.json` file to track the progress of your new feature.

3.  **Define Requirements**
    - Run `/spec requirements <spec-name>`
    - The AI generates a `requirements.md` file, detailing user stories and acceptance criteria in EARS format.

4.  **Create the Technical Design**
    - Run `/spec design <spec-name>`
    - After you approve the requirements, the AI generates a `design.md` file, including architecture, data models, API endpoints, and more.

5.  **Generate Implementation Tasks**
    - Run `/spec tasks <spec-name>`
    - After you approve the design, the AI breaks it down into a list of small, atomic coding tasks in `tasks.md`.

6.  **Implement Tasks**
    - Run `/spec implement <spec-name> <task-id>`
    - Implement each task one by one, following a Test-Driven Development (TDD) approach.

7.  **Check Progress**
    - At any time, run `/spec status <spec-name>` to see the current status of your specification.

### Commands

| Command                                   | Description                                                                                                                              |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `/spec create <spec-name>`                | Initializes a new specification. Creates the spec directory and the `spec.json` tracking file.                                           |
| `/spec requirements <spec-name>`          | Generates a detailed `requirements.md` file based on project context and templates.                                                      |
| `/spec design <spec-name>`                | Generates a comprehensive `design.md` technical document after you approve the requirements.                                           |
| `/spec tasks <spec-name>`                 | Generates a list of atomic, executable coding tasks in `tasks.md` after you approve the design.                                          |
| `/spec implement-contract <spec-name> <task-id>` | Phase 1: Implements API contracts and generates a `testcase.md` file for a task.                                                         |
| `/spec implement-red <spec-name> <task-id>`      | Phase 2: Creates a failing test based on the test cases (Red).                                                                           |
| `/spec implement-green <spec-name> <task-id>`    | Phase 3: Writes the minimum code to make the test pass (Green).                                                                          |
| `/spec implement-refactor <spec-name> <task-id>` | Phase 4: Refactors the code, finalizes the task, and performs cleanup.                                                                   |
| `/spec status <spec-name>`                | Shows the current progress of a specification, including which phases are complete and the task completion percentage.                   |
| `/spec steering`                          | Intelligently creates or updates the core steering documents (`product.md`, `tech.md`, `structure.md`) that provide project-wide context. |

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

Copyright (c) 2025 didy
