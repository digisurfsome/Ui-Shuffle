# Project: [Project Name]

I'm using the Agent OS spec-driven development system. Below is the structured context for this project:

---

## STANDARDS LAYER

### Coding Conventions
- Language: Python (Streamlit)
- Style Guide: PEP 8
- Key Patterns:
  - Use Streamlit components and session state
  - Keep UI clean and minimal
  - Handle errors gracefully with user-friendly messages

### Architecture Standards
- Architecture Type: Single-file Streamlit app
- Folder Structure: Simple flat structure

### Technology Stack
- Frontend: Streamlit
- Backend: Python
- Deployment: Railway

### Authentication Standard
VERSION A: Simple Tool (No User Data)

This is a simple tool with no user-specific data storage. Authentication will be handled at the deployment level via Railway nginx basic auth proxy. Do not implement any authentication in the app code itself.

No auth code needed in the app. I will add Railway proxy auth at deployment.

---

## PRODUCT LAYER

### Vision
[What problem does this solve? What's the ultimate goal?]

### Target Users
[Who is this for?]

### Core Use Cases
1. [Use case 1]
2. [Use case 2]
3. [Use case 3]

---

## SPEC LAYER

### Current Feature: [Feature Name]

#### Overview
[Brief description of what this feature does]

#### Authentication Type
VERSION A: Simple tool, no user data (Railway proxy auth at deployment)

#### Requirements
1. [Functional requirement 1]
2. [Functional requirement 2]
3. [Technical requirement 1]

#### User Stories
- As a [user type], I want to [action] so that [benefit]

#### Acceptance Criteria
- [Criterion 1]
- [Criterion 2]
- [Criterion 3]

#### Technical Specification
- Dependencies: [What libraries needed]
- Edge Cases: [What to handle]

---

## TASK

[Your specific request for this session]

Build this Streamlit app following the standards above. Create a clean, functional tool. Do not add any authentication code - that will be handled at deployment level.
