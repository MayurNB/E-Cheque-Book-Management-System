# Database Overview

## 1. Introduction

The E-Cheque Book Management System uses MySQL to store application data, including user accounts, bank and branch information, transactions, approval-related information, and agreements.

The database supports the application's payment workflow by maintaining transaction records and their associated status information.

## 2. Database Tables

The application uses separate tables for the following main entities.

### 2.1 Users

The users table stores information associated with application users.

User records are associated with relevant bank and branch information where applicable. These records support login and user-related operations within the application.

### 2.2 Banks and Branches

Bank and branch information is stored in the database to represent the banking entities involved in the application's workflow.

The system uses this information in association with users and transactions.

### 2.3 Transactions

The transactions table stores the main payment-request information.

Transaction information includes details associated with the payer, recipient, amount, scheduled date, cheque information, purpose, and status.

The transaction record is central to the application's payment and approval workflow.

### 2.4 Approval-Related Information

Approval-stage information is stored mainly in the transaction records rather than in a separate record for every approval action.

This information supports the sequential approval workflow involving the payer's bank branch staff, payer's bank manager, recipient's bank branch staff, and recipient's bank manager.

### 2.5 Agreements

The agreements table stores agreement-related information associated with a transaction.

The agreement information can include terms and purpose, together with details needed for the recipient's acceptance or rejection workflow.

## 3. High-Level Data Relationships

The application connects related records to support its main operations.

* User records are associated with relevant bank and branch information.
* Transaction records contain or reference information associated with the payer and recipient.
* Transaction records maintain the approval-related information used by the workflow.
* Agreement records are associated with their relevant transactions.
* Some database foreign keys and constraints are used to maintain relationships between records.

This is a conceptual overview of the known relationships. Exact table definitions, column names, foreign-key columns, and cardinalities have not been documented here because they have not yet been verified against the actual database schema.

## 4. Database Connectivity

The application uses MySQLi to connect Core PHP pages to the MySQL database.

Database operations support application functions such as:

* Retrieving user and recipient information.
* Recording payment requests.
* Storing transaction and agreement information.
* Reading transaction records and their statuses.
* Updating records when workflow actions are performed.

## 5. Data Flow

A typical payment-related data flow is:

1. The user enters payment information through the web interface.
2. PHP processes the submitted form.
3. The application performs its available validation.
4. Database operations store or retrieve the relevant information.
5. Subsequent workflow actions update transaction-related records.
6. Relevant pages retrieve the stored information for display.

This describes the general application flow rather than a verified, line-by-line account of every database operation.

## 6. Data Integrity Considerations

The database uses some foreign keys and constraints to support relationships between records.

The exact constraints and their coverage should be confirmed by inspecting the actual database schema before making stronger claims about referential integrity or transaction consistency.

## 7. Security Considerations

The database layer has important limitations that should be considered:

* Some SQL queries are constructed by inserting PHP variables directly into query strings.
* Prepared statements should be used consistently to reduce SQL injection risk.
* Database credentials should be kept out of public repositories.
* Database errors and sensitive information should not be exposed to users.
* Access to user and transaction records should be restricted appropriately.

The application should not be described as production-ready for financial data without a thorough security review.

## 8. Future Improvements

Potential database improvements include:

* Reviewing and documenting the complete schema.
* Using prepared statements for database operations.
* Strengthening foreign-key and validation rules where appropriate.
* Reviewing transaction consistency across approval stages.
* Adding suitable database indexes for frequently queried records.
* Maintaining database backups and a secure configuration process.

These are improvement suggestions, not claims that the features are already implemented.

## Related Documentation

* [Project README](../README.md)
* [System Overview](system-overview.md)
* [Transaction Workflow](transaction-workflow.md)
* [Implementation Status](implementation-status.md)
* [Limitations and Security](limitations-and-security.md)
