# Users API Test Execution

## Test Environment

- API: DummyJSON
- Tool: Postman
- Test Type: Manual API Testing

---

## TC-USERS-001 — Get existing user by ID

**Actual Result:**
- Status code: `200 OK`
- User with `id = 1` was returned
- User data was present in the response

**Status:** Pass

---

## TC-USERS-002 — Get non-existent user by ID

**Actual Result:**
- Status code: `404 Not Found`
- Response body did not contain user data

**Status:** Pass

---

## TC-USERS-003 — Create user with valid data

**Actual Result:**
- Status code: `201 Created`
- Submitted data was returned
- New `id` was generated

**Returned ID:** `11`

**Status:** Pass

---

## TC-USERS-004 — Create user with invalid data

**Actual Result:**
- Status code: `201 Created`
- API accepted empty `name`
- API accepted empty `username`
- API accepted invalid email format
- New `id` was generated

**Status:** Observation

### Notes

The API accepts invalid user data and still returns `201 Created`.

This behavior should be compared with API validation requirements before being reported as a defect.

---

## TC-USERS-005 — Partially update user

**Actual Result:**
- Status code: `200 OK`
- User `id` remained `1`
- Email was changed to `newemail@test.com`
- Other original user fields were returned

**Status:** Pass

---

## TC-USERS-006 — Fully update user

**Actual Result:**
- Status code: `200 OK`
- User `id` remained `1`
- Submitted fields were returned:
  - `name`
  - `username`
  - `email`
- Fields not included in the request were not returned

**Status:** Pass

---

## TC-USERS-007 — Delete existing user

**Actual Result:**
- Status code: `200 OK`
- Response body was empty
- No server error was returned

**Status:** Pass

### Notes

DummyJSON simulates update and delete operations, so changes are not permanently stored.
