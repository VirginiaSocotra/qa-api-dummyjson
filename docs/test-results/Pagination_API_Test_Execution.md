# Pagination API Test Execution

## Test Environment

- API: DummyJSON
- Tool: Postman
- Test Type: Manual API Testing

---

## TC-PAGINATION-001 — Get first page of users

**Actual Result:**
- Status code: `200 OK`
- 10 users were returned
- Users from the beginning of the collection were displayed
- No users were skipped

**Status:** Pass

---

## TC-PAGINATION-002 — Get second page of users

**Actual Result:**
- Status code: `200 OK`
- 10 users were returned
- First 10 users were skipped
- Users 11–20 were returned
- No duplicate users from the previous page were found

**Status:** Pass

---

## TC-PAGINATION-003 — Get third page of users

**Actual Result:**
- Status code: `200 OK`
- 10 users were returned
- First 20 users were skipped
- Users 21–30 were returned
- No duplicate users from previous pages were found

**Status:** Pass

---

## TC-PAGINATION-004 — Request users with limit set to zero

**Actual Result:**
- Status code: `200 OK`
- All 208 users were returned
- `limit=0` was treated as no limit

**Status:** Observation

### Notes

The API returns all available users when `limit=0`.

This behavior should be compared with the API specification before determining whether it is expected.

---

## TC-PAGINATION-005 — Skip more users than available

**Actual Result:**
- Status code: `200 OK`
- Empty users array was returned
- Response included:
  - `total: 208`
  - `skip: 1000`
  - `limit: 0`

**Status:** Pass

---

## TC-PAGINATION-006 — Use negative skip value

**Actual Result:**
- Status code: `400 Bad Request`
- No users were returned
- Error message: `Invalid 'skip' - should be a positive number`

**Status:** Pass
