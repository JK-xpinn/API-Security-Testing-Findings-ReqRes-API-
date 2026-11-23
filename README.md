# API Security Testing Notes – ReqRes

A small practical exercise using Burp Suite to observe API request and response behaviour on the ReqRes public test API.

## Objective

Explore how selected endpoints respond to changes in request parameters and authentication-related headers. The exercise was intended for learning and documentation, not as a formal penetration test of a production application.

## Test Areas and Observations

### 1. Input handling

The tested `page` parameter accepted non-numeric and out-of-range values while returning HTTP 200 responses.

**Interpretation:** This is an input-handling observation. A successful HTTP response alone does not establish a security vulnerability; the expected behaviour depends on the API contract.

### 2. Predictable identifiers

Sequential user identifiers returned responses for the records available in the test dataset.

**Interpretation:** Predictable identifiers are not, by themselves, proof of insecure direct object reference (IDOR). IDOR requires evidence that a user can access an object they are not authorized to access. That was not established by this observation.

### 3. Authentication behaviour

Some tested requests without an API key returned successful responses, while requests with an invalid API key returned HTTP 401.

**Interpretation:** Authentication behaviour differed across the tested endpoints. The result should be compared with the documented requirements for each endpoint before classifying it as a security weakness.

## Tools

- Burp Suite
- Browser / HTTP client
- Manual request and response analysis

## Conclusion

This exercise provided practice in intercepting API traffic, modifying parameters, inspecting status codes, and distinguishing unusual behaviour from a confirmed vulnerability.

No production vulnerability is claimed from these observations. Further testing would require a clearly defined authorization model, endpoint requirements, and repeatable evidence of unauthorized access or impact.

## Disclaimer

ReqRes is a public test API. This repository records educational observations only. Do not use these notes as evidence of a vulnerability in a production service.
