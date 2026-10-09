# Limitations and Security

## 1. Introduction

The E-Cheque Book Management System is an academic web application developed using Core PHP, MySQL, HTML, CSS, and Bootstrap.

The project demonstrates transaction record management and a multi-stage approval workflow. However, its current implementation has security and reliability limitations that would need to be addressed before considering a real-world financial application.

## 2. Known Security Limitations

### 2.1 SQL Injection Risk

Some database queries are constructed by inserting PHP variables directly into SQL query strings.

This approach can expose the application to SQL injection if user-controlled values are not handled safely.

**Potential improvement:** Use prepared statements consistently with MySQLi, validate input, and avoid constructing SQL queries from untrusted input.

### 2.2 Plain-Text Password Storage

Passwords are stored as plain text in the described implementation.

This is a significant security weakness because exposed database records could reveal users' original passwords.

**Potential improvement:** Store passwords using PHP's `password_hash()` function and verify them using `password_verify()`. Existing passwords would need a secure migration or reset strategy.

### 2.3 Session Security

The application uses PHP sessions to maintain login state and checks sessions on pages that display user-specific information.

However, these checks alone do not establish that session management is secure.

**Potential improvements:**

* Regenerate session IDs after successful authentication.
* Configure appropriate cookie flags.
* Implement suitable session expiration and logout handling.
* Review authorization checks on every sensitive operation.

### 2.4 Role and Permission Enforcement

The application includes different participants in the transaction approval workflow. However, its role-specific interface and permission controls should not be considered a complete enterprise-grade role-based access control system.

**Potential improvement:** Implement centralized server-side authorization checks that verify the user's identity, role, permitted action, and relationship to the relevant transaction.

### 2.5 Input Validation

The application uses browser-side and PHP-side validation for relevant forms.

Browser-side validation can be bypassed, so server-side validation remains essential.

**Potential improvements:**

* Validate all submitted values on the server.
* Validate amounts, dates, identifiers, and permitted state transitions.
* Apply appropriate database constraints.
* Return safe and understandable error messages.

### 2.6 Sensitive Data Protection

The application stores user and transaction-related information in MySQL.

The current project has not been established as a production-grade system for protecting sensitive financial data.

**Potential improvements:** Minimize stored personal information, protect database credentials, restrict database access, use HTTPS in deployment, and avoid exposing sensitive data through errors or logs.

## 3. Transaction Integrity and Workflow

The application represents transactions through sequential approval stages and stored status values.

A production-oriented implementation would require additional verification of transaction consistency, authorization, and concurrent updates.

Potential improvements include:

* Enforcing valid state transitions on the server.
* Using database transactions where multiple related updates must succeed or fail together.
* Preventing unauthorized or repeated approval actions.
* Recording an auditable history of approval, rejection, and cancellation events.
* Testing concurrent requests and unexpected workflow sequences.

These are suggested improvements, not claims that all such controls currently exist.

## 4. Reliability and Testing

The application was manually tested in a local PHP and MySQL environment.

An automated test suite and a reproducible deployment process have not been confirmed.

Potential improvements include:

* Unit tests for individual functions.
* Integration tests for database operations.
* Workflow tests covering approval, rejection, and cancellation.
* Tests for invalid inputs and unauthorized actions.
* Documented installation and database setup instructions.

## 5. Production Readiness

The project is an academic transaction workflow application, not a production banking platform.

It does not transfer real money or integrate with live banking APIs.

Before any real-world financial use, the system would require substantial security engineering, comprehensive testing, secure credential handling, access-control enforcement, auditability, deployment hardening, and appropriate financial and legal review.

## 6. Future Improvements

The following improvements could strengthen the project:

1. Replace direct SQL string construction with prepared statements.
2. Introduce secure password hashing.
3. Strengthen authentication, session handling, and server-side authorization.
4. Review database constraints and transaction consistency.
5. Add a detailed approval audit trail.
6. Add automated tests for key workflows.
7. Document reproducible local setup and deployment.
8. Review privacy, data retention, and sensitive-information handling.

## 7. Learning Outcome

Reviewing these limitations helps identify the difference between a working academic prototype and a system suitable for sensitive real-world use.

It also provides a foundation for future improvements in secure PHP development, database design, authorization, testing, and software reliability.

## Related Documentation

* [Project README](../README.md)
* [System Overview](system-overview.md)
* [Transaction Workflow](transaction-workflow.md)
* [Database Overview](database-overview.md)
* [Implementation Status](implementation-status.md)
