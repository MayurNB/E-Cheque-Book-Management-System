# Implementation Status

## 1. Purpose

This document summarizes the known implementation status of the E-Cheque Book Management System.

The project was developed as an academic web application using Core PHP and MySQL. This document distinguishes functionality reported as implemented from details that have not yet been verified against the original source code or database.

## 2. Functionality Implemented

Based on the project's described behavior, the following functionality was implemented:

### 2.1 Login and Sessions

* Login using user credentials.
* PHP sessions to maintain the login state.
* Session checks on pages that display user-specific information.

### 2.2 User and Bank Management

* Administrative functionality for managing user accounts.
* Management of bank and branch information.
* Associations between users and relevant bank or branch records.

### 2.3 Payment and Cheque Records

* Recipient lookup using a recipient ID.
* Entry of payment amount and scheduled date.
* Creation and storage of transaction information.
* A cheque-style interface displaying payment-related details.

### 2.4 Approval Workflow

* Four sequential approval stages.
* Approval actions at each stage.
* Rejection functionality.
* Cancellation options for the payer, recipient, and bank staff or managers.
* Transaction status updates following workflow actions.
* Completion after the final approval stage.

### 2.5 Transaction Tracking

* Storage of transaction information and status in MySQL.
* Pages for viewing transaction-related information and history.
* Status visibility after refreshing or reopening the relevant page.

### 2.6 Agreement Workflow

* Entry and storage of agreement-related details.
* Association between agreement records and transactions.
* Recipient acceptance or rejection of an agreement.
* Transaction status changes associated with the agreement decision.

### 2.7 Form Processing and Database Operations

* Browser-side and PHP-side validation for relevant form submissions.
* MySQL database connectivity through MySQLi.
* Separate PHP files for many individual pages and actions.

## 3. Technical Implementation

| Area                    | Known implementation                  |
| ----------------------- | ------------------------------------- |
| Backend                 | Core PHP                              |
| Programming style       | Primarily procedural                  |
| Database                | MySQL                                 |
| Database access         | MySQLi                                |
| Frontend                | HTML, CSS, Bootstrap                  |
| Login state             | PHP sessions                          |
| Development and testing | Local environment with manual testing |

## 4. Details Not Yet Verified

The following details require inspection of the original source code or database before making specific claims:

* Exact database table definitions and column names.
* Complete foreign-key definitions and relationship cardinalities.
* The exact list of internal transaction status values.
* The mechanism used for scheduled-date-based behavior.
* The precise rules determining which bank branch receives each request.
* Whether agreement confirmation uses a drawn signature, uploaded signature, or another mechanism.
* Reproducible installation and database-import instructions.
* The availability of screenshots or a currently runnable demonstration.

These details are intentionally left unconfirmed rather than inferred.

## 5. Known Limitations

The application has limitations that are important to acknowledge:

* It does not process real bank transfers.
* It does not integrate with live banking APIs.
* Status updates require users to refresh or reopen the relevant page to see changes.
* Role-specific permissions should not be represented as a complete enterprise-grade RBAC implementation.
* SQL queries are often constructed by inserting PHP variables directly into query strings.
* Passwords are stored in plain text in the described implementation.
* Automated testing and a reproducible deployment process have not been established.

## 6. Testing Status

The application was manually tested in a local PHP and MySQL environment.

No automated test suite or currently working public demonstration has been confirmed.

The original project is not currently available for a fresh live demonstration, so the current status is documented from the implementation details known about the project.

## 7. Documentation Principles

This repository aims to describe the academic project accurately.

* Implemented functionality is described based on the known project behavior.
* Unverified implementation details are identified explicitly.
* Security improvements are not presented as existing features.
* Suggested improvements are separated from current functionality.
* The project is not represented as a production banking platform.

## Related Documentation

* [Project README](../README.md)
* [System Overview](system-overview.md)
* [Transaction Workflow](transaction-workflow.md)
* [Database Overview](database-overview.md)
* [Limitations and Security](limitations-and-security.md)
