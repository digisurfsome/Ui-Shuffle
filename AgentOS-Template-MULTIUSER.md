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
- Architecture Type: Streamlit app with authentication
- Folder Structure:
  - app.py (main file)
  - config.yaml (auth config)
  - requirements.txt

### Technology Stack
- Frontend: Streamlit
- Backend: Python
- Deployment: Railway
- Auth: streamlit-authenticator

### Authentication Standard
VERSION B: App With User Data

Implement user authentication using streamlit-authenticator with IP whitelist bypass.

REQUIRED IN requirements.txt:
- streamlit
- streamlit-authenticator
- pyyaml

REQUIRED FILE config.yaml:
credentials:
  usernames:
    admin:
      email: admin@email.com
      name: Admin
      password: admin123
cookie:
  name: app_cookie
  key: super-secret-random-key-change-this
  expiry_days: 30

REQUIRED AUTH CODE at TOP of main Streamlit file before any app logic:

import streamlit as st
import streamlit_authenticator as stauth
import yaml

WHITELISTED_IPS = ["136.49.112.9"]

def get_client_ip():
    headers = st.context.headers
    return headers.get("x-forwarded-for", "").split(",")[0].strip() or headers.get("x-real-ip", "")

with open('config.yaml') as f:
    config = yaml.safe_load(f)

authenticator = stauth.Authenticate(
    config['credentials'],
    config['cookie']['name'],
    config['cookie']['key'],
    config['cookie']['expiry_days']
)

client_ip = get_client_ip()
if client_ip in WHITELISTED_IPS:
    st.session_state["authentication_status"] = True
    st.session_state["username"] = "admin"
    st.session_state["name"] = "Admin"
else:
    authenticator.login()

if st.session_state.get("authentication_status"):
    if client_ip not in WHITELISTED_IPS:
        authenticator.logout(location='sidebar')

    current_user = st.session_state["username"]

    # ALL APP CODE GOES HERE
    # Use current_user to key any user-specific data

elif st.session_state.get("authentication_status") is False:
    st.error('Username/password is incorrect')
else:
    st.warning('Please enter your username and password')
    st.stop()

USER DATA ISOLATION RULE: All stored data must be keyed by current_user so each user only sees their own data.

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
VERSION B: Has user data/projects (streamlit-authenticator with IP bypass)

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
- Data Models: [What user data is stored]
- Dependencies: [What libraries needed]
- Edge Cases: [What to handle]

---

## TASK

[Your specific request for this session]

Build this Streamlit app following the standards above. Implement the authentication system exactly as specified in the Standards Layer. Make sure all user data is isolated using the current_user variable. Create the config.yaml file and include all dependencies in requirements.txt.
