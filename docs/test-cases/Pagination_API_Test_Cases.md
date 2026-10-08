# Pagination API Test Cases

## TC-PAGINATION-001 — Get first page of users

**Method:** GET  
**Endpoint:** `/users?limit=10&skip=0`  
**Priority:** Medium  
**Type:** Positive / Pagination

### Expected Result

- Status code is `200 OK`
- 10 users are returned
- First user set starts from the beginning of the collection
- No users are skipped

---

## TC-PAGINATION-002 — Get second page of users

**Method:** GET  
**Endpoint:** `/users?limit=10&skip=10`  
**Priority:** Medium  
**Type:** Positive / Pagination

### Expected Result

- Status code is `200 OK`
- 10 users are returned
- First 10 users are skipped
- Next set of users is returned
- No duplicate users appear from the previous page

---

## TC-PAGINATION-003 — Get third page of users

**Method:** GET  
**Endpoint:** `/users?limit=10&skip=20`  
**Priority:** Medium  
**Type:** Positive / Pagination

### Expected Result

- Status code is `200 OK`
- 10 users are returned
- First 20 users are skipped
- Next set of users is returned
- No duplicate users appear from previous pages

---

## TC-PAGINATION-004 — Request users with limit set to zero

**Method:** GET  
**Endpoint:** `/users?limit=0&skip=0`  
**Priority:** Medium  
**Type:** Boundary / Pagination

### Expected Result

- API behavior is recorded
- Request does not cause a server error
- Returned data is checked against API specification

---

## TC-PAGINATION-005 — Skip more users than available

**Method:** GET  
**Endpoint:** `/users?limit=10&skip=1000`  
**Priority:** Medium  
**Type:** Boundary / Negative

### Expected Result

- Status code is `200 OK`
- Empty users array is returned
- API does not return a server error

---

## TC-PAGINATION-006 — Use negative skip value

**Method:** GET  
**Endpoint:** `/users?limit=10&skip=-1`  
**Priority:** Medium  
**Type:** Negative / Validation

### Expected Result

- Request is rejected
- Validation error is returned
- Negative `skip` value is not accepted
