# Authentication API Test Cases

## TC-AUTH-001 — Login with valid credentials

**Method:** POST  
**Endpoint:** `/auth/login`  
**Priority:** High  
**Type:** Positive / Functional

### Test Data

```json
{
  "username": "emilys",
  "password": "emilyspass"
}
```

### Expected Result

- Status code is `200 OK`
- User data is returned
- `accessToken` is returned
- `refreshToken` is returned
- Returned username is `emilys`

---

## TC-AUTH-002 — Login with invalid password

**Method:** POST  
**Endpoint:** `/auth/login`  
**Priority:** High  
**Type:** Negative / Authentication

### Test Data

```json
{
  "username": "emilys",
  "password": "wrongpassword"
}
```

### Expected Result

- Login is rejected
- Error response is returned
- No `accessToken` is generated
- Protected user data is not returned

---

## TC-AUTH-003 — Login with empty password

**Method:** POST  
**Endpoint:** `/auth/login`  
**Priority:** High  
**Type:** Negative / Validation

### Test Data

```json
{
  "username": "emilys",
  "password": ""
}
```

### Expected Result

- Request is rejected
- Validation error is returned
- Error message indicates that username and password are required
- No `accessToken` is generated

---

## TC-AUTH-004 — Login with non-existent username

**Method:** POST  
**Endpoint:** `/auth/login`  
**Priority:** High  
**Type:** Negative / Authentication

### Test Data

```json
{
  "username": "user_does_not_exist_123",
  "password": "emilyspass"
}
```

### Expected Result

- Login is rejected
- Invalid credentials error is returned
- No `accessToken` is generated

---

## TC-AUTH-005 — Access protected endpoint with valid Bearer Token

**Method:** GET  
**Endpoint:** `/auth/me`  
**Priority:** High  
**Type:** Positive / Authentication

### Preconditions

- User is successfully logged in
- Valid `accessToken` is available

### Authorization

`Bearer Token`

### Expected Result

- Status code is `200 OK`
- Authenticated user data is returned
- Returned username is `emilys`

---

## TC-AUTH-006 — Access protected endpoint without Bearer Token

**Method:** GET  
**Endpoint:** `/auth/me`  
**Priority:** High  
**Type:** Negative / Authentication

### Preconditions

- No access token is provided

### Authorization

`No Auth`

### Expected Result

- Request is rejected
- Status code is `401 Unauthorized`
- Error message indicates that an access token is required
- Protected user data is not returned

---

## TC-AUTH-007 — Access protected endpoint with corrupted Bearer Token

**Method:** GET  
**Endpoint:** `/auth/me`  
**Priority:** High  
**Type:** Negative / Authentication

### Preconditions

- Valid access token was obtained
- Several characters in the token were manually changed

### Authorization

`Bearer Token`

### Expected Result

- Request is rejected
- Authentication error is returned
- Protected user data is not returned
