# Users API Test Cases

## TC-USERS-001 — Get existing user by ID

**Method:** GET  
**Endpoint:** `/users/1`  
**Priority:** High  
**Type:** Positive / Functional

### Expected Result

- Status code is `200 OK`
- User with `id = 1` is returned
- Required user fields are present
- Returned data corresponds to the requested user

---

## TC-USERS-002 — Get non-existent user by ID

**Method:** GET  
**Endpoint:** `/users/999999`  
**Priority:** Medium  
**Type:** Negative / Functional

### Expected Result

- Status code is `404 Not Found`
- Non-existent user data is not returned

---

## TC-USERS-003 — Create user with valid data

**Method:** POST  
**Endpoint:** `/users`  
**Priority:** High  
**Type:** Positive / Functional

### Test Data

```json
{
  "name": "Anna Test",
  "username": "anna_test",
  "email": "anna@test.com"
}
```

### Expected Result

- Status code is `201 Created`
- Submitted user data is returned
- New `id` is generated

---

## TC-USERS-004 — Create user with invalid data

**Method:** POST  
**Endpoint:** `/users`  
**Priority:** Medium  
**Type:** Negative / Validation

### Test Data

```json
{
  "name": "",
  "username": "",
  "email": "not-an-email"
}
```

### Expected Result

- API behavior should be checked against validation requirements
- Invalid input should not cause a server error
- Validation behavior should be documented

---

## TC-USERS-005 — Partially update user

**Method:** PATCH  
**Endpoint:** `/users/1`  
**Priority:** High  
**Type:** Positive / Functional

### Test Data

```json
{
  "email": "newemail@test.com"
}
```

### Expected Result

- Status code is `200 OK`
- User `id` remains `1`
- Email is updated
- Other user fields remain unchanged

---

## TC-USERS-006 — Fully update user

**Method:** PUT  
**Endpoint:** `/users/1`  
**Priority:** High  
**Type:** Positive / Functional

### Test Data

```json
{
  "name": "Anna Test",
  "username": "anna_test",
  "email": "anna@test.com"
}
```

### Expected Result

- Status code is `200 OK`
- User `id` remains `1`
- Resource is replaced with submitted data
- Fields not included in the request may not be present in the response

---

## TC-USERS-007 — Delete existing user

**Method:** DELETE  
**Endpoint:** `/users/1`  
**Priority:** High  
**Type:** Positive / Functional

### Expected Result

- Delete request is processed successfully
- No server error is returned
- Response body may be empty depending on API behavior
