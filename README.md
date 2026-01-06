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

Test Case ID,         Description,                                   Test Steps,                            Test Data,                               Expected Result
TC-01,                Verify password requires special characters,    1. Open Registration page             Email: test@care.com             "System displays error: ""Password must include a special character."
                                                                      2. Enter a valid email.               Password: Pass1234
                                                                      3. Enter password ""Pass1234"" 
                                                                      (no special char)
                                                                      4. Click Register.

TC-02                Verify successful registration                   1. Open Registration page             Email: test@care.com             "System displays as registration is successful"
                                                                      2. Enter a valid email.               Password: Pass1234#
                                                                      3. Enter password ""Pass1234#""
                                                                      4. Click Register.
