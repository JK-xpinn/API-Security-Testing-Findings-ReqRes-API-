## API Security Testing Findings (ReqRes API)

Testing was conducted using Burp Suite on the ReqRes API to evaluate authentication, authorization, and input validation controls.

### 1. Input Validation Weakness
The `page` parameter accepts non-numeric and out-of-range values while still returning HTTP 200 responses. The system defaults or ignores invalid inputs instead of rejecting them.

### 2. Object Enumeration
User IDs from 0–13 were accessible, returning valid responses. This indicates predictable object access patterns typical of test APIs.

### 3. Authentication Enforcement
Requests without an API key still returned successful responses (200 OK) for most endpoints. However, invalid API keys returned 401 Unauthorized, indicating partial enforcement of authentication controls.

### 4. Conclusion
The API demonstrates stable behavior and consistent responses but lacks strict input validation and uniform authentication enforcement on all endpoints. These findings are primarily observational due to the nature of the testing environment.
