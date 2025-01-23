# User Management Screen Specification

## Overview
This document outlines the functional and design specifications for the user management screen. It is designed to help administrators efficiently handle user data and perform tasks such as viewing, adding, editing, and filtering user records.

## Functional Requirements
- The screen should provide the following functionalities:
  - Displaying a list of active users.
  - Allowing administrators to add new users through a form.
  - Editing and deleting existing user information.
  - Providing the ability to show or hide disabled users via a toggle.

- **Validation Rules:**
  - All fields in the "New User" form are mandatory except for the "Phone" field.
  - "Email" must adhere to a valid format (e.g., user@example.com).

## UI Components

### Action Buttons
- **New User**:
  - Positioned at the top-left corner of the interface.
  - Opens the "New User" form on the right side.

- **Save User**:
  - Appears at the bottom of the "New User" form.
  - Triggers form validation and saves the user data to the backend.

- **Hide Disabled User**:
  - Checkbox for toggling the visibility of disabled users in the table.

### User Table
- **Columns**:
  - **ID**: Unique identifier for users.
  - **User Name**: Displays the username.
  - **Email**: Shows the user's email address.
  - **Enabled**: Indicates active (`true`) or inactive (`false`) status.

- **Table Interactions**:
  - Clicking a row highlights the user and enables editing or viewing details.

### New User Form
- **Form Fields:**
  - **Username**:
    - Alphanumeric, 3-20 characters.
    - Mandatory.

  - **Display Name**:
    - Optional field for the full name display.

  - **Phone**:
    - Optional.

  - **Email**:
    - Must be a valid email address.

  - **User Roles**:
    - Dropdown to assign roles (`Guest`, `Admin`, `SuperAdmin`).

  - **Enabled**:
    - Radio button to toggle active or inactive status.

## Page Behavior
- **New User Button**:
  - Clears and displays the "New User" form.

- **Save User Button**:
  - Validates inputs and saves data.
  - On success, shows a confirmation message.

- **Hide Disabled User Checkbox**:
  - Filters out disabled users when selected.

## Initial Display State
- The table shows all active users.
- The "Hide Disabled User" checkbox is unchecked by default.
- The "New User" form remains hidden until the "New User" button is clicked.

## API Details
- **Add User Endpoint**:
  - **URL**: `POST /api/users`
  - **Payload**:
    ```json
    {
      "username": "string",
      "displayName": "string",
      "phone": "string",
      "email": "string",
      "roles": ["string"],
      "enabled": "boolean"
    }
    ```

- **Edit User Endpoint**:
  - **URL**: `PUT /api/users/{id}`

- **Delete User Endpoint**:
  - **URL**: `DELETE /api/users/{id}`

- **Get Users Endpoint**:
  - **URL**: `GET /api/users`
  - **Parameters**:
    - `enabled` (optional): Filters active or inactive users.

## Additional Notes for Developers
- Ensure robust client-side and server-side validation.
- Use inline messages or tooltips for validation errors.
- Implement pagination for large user datasets.
- Provide user feedback with loading indicators for all API interactions.

---
This document provides a comprehensive guide for developers to implement the user management interface effectively.

