# Authentication API Test Execution

## Test Environment

- API: DummyJSON
- Tool: Postman
- Test Type: Manual API Testing

---

## TC-AUTH-001 — Login with valid credentials

**Actual Result:**
- Status code: `200 OK`
- User data returned
- `accessToken` returned
- `refreshToken` returned
- Username: `emilys`

**Status:** Pass

---

## TC-AUTH-002 — Login with invalid password

**Actual Result:**
- Status code: `400 Bad Request`
- Error message: `Invalid credentials`
- `accessToken` was not returned

**Status:** Pass

---

## TC-AUTH-003 — Login with empty password

**Actual Result:**
- Status code: `400 Bad Request`
- Error message: `Username and password required`
- `accessToken` was not returned

**Status:** Pass

---

## TC-AUTH-004 — Login with non-existent username

**Actual Result:**
- Status code: `400 Bad Request`
- Error message: `Invalid credentials`
- `accessToken` was not returned

**Status:** Pass

---

## TC-AUTH-005 — Access protected endpoint with valid Bearer Token

**Actual Result:**
- Status code: `200 OK`
- Authenticated user data returned
- Username: `emilys`

**Status:** Pass

---

## TC-AUTH-006 — Access protected endpoint without Bearer Token

**Actual Result:**
- Status code: `401 Unauthorized`
- Error message: `Access Token is required`
- Protected user data was not returned

**Status:** Pass

---

## TC-AUTH-007 — Access protected endpoint with corrupted Bearer Token

**Actual Result:**
- Status code: `500 Internal Server Error`
- Error message: `invalid signature`
- Protected user data was not returned

**Status:** Observation

### Notes

The API rejects the corrupted token, but returns `500 Internal Server Error`.

For an invalid authentication token, an authentication-related client error such as `401 Unauthorized` would normally be expected. This behavior should be verified against the API specification before reporting it as a defect.
