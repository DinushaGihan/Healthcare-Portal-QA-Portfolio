# Healthcare Patient Portal - QA Project

## Project Overview
This project demonstrates end-to-end Quality Assurance for a Healthcare Patient Portal, covering Manual Testing, API Testing, and Automation.

## Phase 1: Requirement Analysis & Manual Testing
### Feature: User Registration
**Requirement:** Users must be able to create an account with a valid email and a secure password.

**Test Scenarios:**
1. [Positive] Register with a valid email and a valid password.
2. [Negative] Register with an invalid email format (e.g., "test@com").

### Test Case: Password Complexity

|Test Case ID,         |Description,                                   |Test Steps,                       |Test Data,                       |Expected Result|
|:---                  |:---                                           |:---                              |:---                             |:---
|TC-01                 |Verify password requires special characters,   |1. Open Registration page         |Email: test@care.com             |"System displays error: ""Password must include a special character."
                                                                       2. Enter a valid email.           |Password: Pass1234               |
                                                                       3. Enter password ""Pass1234""(no special char) 
                                                                       4. Click Register.                |                                 |
                                                                       
|:---                  |:---                                           |:---                              |:---                             |:---
|TC-02                 |Verify successful registration                 |1. Open Registration page         |Email: test@care.com             |"System displays as registration is successful"
|                      |                                               |2. Enter a valid email.           |Password: Pass1234#              |
|                      |                                               |3. Enter password ""Pass1234#""   |                                 |
|                      |                                               |4. Click Register.                |                                 |

## Phase 2: Bug Reporting

A standard bug report includes these key fields:
**Title**: A concise summary of the problem.
**Severity**: How much it impacts the business (Critical, Major, Minor).
**Steps to Reproduce**: The exact clicks needed to see the bug.
**Actual Result**: What currently happens.
**Expected Result**: What should happen.

### Bug Report: [BUG-001] White screen on successful registration
**Severity:** Critical  
**Priority:** High  

**Environment:** Google Chrome (Version 120.0), Windows 11  

**Steps to Reproduce:**
1. Navigate to the Registration page.
2. Enter a valid email (e.g., test@care.com).
3. Enter a valid password (e.g., Pass1234#).
4. Click the 'Register' button.

**Actual Result:** The screen turns completely white; no confirmation message appears.  
**Expected Result:** User should be redirected to a 'Success' page and receive a confirmation email.

## Phase 3: API Testing (Postman)

### API Test Case: User Registration Endpoint
**Endpoint:** `POST /api/v1/register`  
**Description:** Verify that the backend correctly processes registration data.

| Test Scenario                | Expected Status Code               | Expected Response Message |
| :---                         | :---                               | :---                      |
| Valid registration data      | 201 Created                        | "User created successfully" |
| Missing password field       | 400 Bad Request                    | "Password is required" |
| Email already exists         | 409 Conflict                       | "Email already in use" |

## Phase 4: Automation (Conceptual)

### Automation Logic: User Registration
To automate **TC-02** (Successful Registration), the script will follow these logic steps:
1. **Navigate:** `browser.get("https://healthcare-portal.com/register")`
2. **Input Email:** Find element by ID `email-field` and type `test@care.com`.
3. **Input Password:** Find element by ID `password-field` and type `Pass1234#`.
4. **Click:** Find element by ID `register-btn` and click.
5. **Verify:** Check if the URL changes to `/dashboard` or if a success message appears.

## Phase 5: User Acceptance Testing (UAT).

Imagine a Doctor finishes a long shift and needs to review a patient's lab results. If the system is too complicated, they might miss critical information.

UAT Script: Doctor Reviews Lab Report

|Step   |Action                                    | Business Requirement,                                  |  Pass/Fail|
|:---   |:---                                      |:---                                                    |:---
|1      |Log in with Doctor Credentials             | Ensure HIPAA-compliant secure access.                  |  [ ]|
|2      |"Search for Patient ""John Doe"""          | Doctor must find the patient in under 5 seconds.       |  [ ]|
|3      |"Click on ""Latest Lab Results"""          | Results should be displayed in chronological order.    |  [ ]|
|4      |"Click ""Download PDF"""                   | The report must be legible for printing.               |  [ ]|
|5      |"Mark report as ""Reviewed"""              | System must timestamp when the doctor saw it.          |  [ ]|


