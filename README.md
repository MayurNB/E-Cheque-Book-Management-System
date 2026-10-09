# E-Cheque Book Management System

## Overview

The E-Cheque Book Management System is an academic web application developed using Core PHP, MySQL, HTML, CSS, and Bootstrap.

The application models a cheque-based payment workflow in which a payment request passes through multiple approval stages before reaching its final status. It also includes transaction tracking and an agreement workflow.

The project demonstrates database-backed transaction management, user interaction, and sequential approval processing.

**Important:** This application records and manages transactions internally. It does not transfer real money or connect to live banking systems.

## Features

* User account and bank management
* Bank and branch management
* Payment initiation using recipient details
* Amount and scheduled-date entry
* Four-stage transaction approval workflow
* Transaction status tracking and history
* Rejection and cancellation options
* Cheque-style transaction records
* Agreement creation and recipient acceptance or rejection
* MySQL-based record storage

## Technology Stack

| Component             | Technology               |
| --------------------- | ------------------------ |
| Backend               | Core PHP                 |
| Programming approach  | Primarily procedural PHP |
| Database              | MySQL                    |
| Database connectivity | MySQLi                   |
| Frontend              | HTML, CSS, Bootstrap     |
| Login sessions        | PHP Sessions             |

## Transaction Approval Workflow

1. The payer initiates a payment request.
2. The payer's bank branch staff reviews the request.
3. The payer's bank manager reviews the request.
4. The recipient's bank branch staff reviews the request.
5. The recipient's bank manager performs the final approval.
6. The transaction is marked as completed after final approval.

The application also supports rejection and cancellation actions through its available functionality.

## Agreement Workflow

The agreement functionality allows the payer to enter agreement details associated with a transaction. The recipient can accept or reject the agreement, and the decision affects the transaction status.

## Database

The application uses MySQL tables for users, banks and branches, transactions, approval-related information, and agreements.

Approval-stage information is stored mainly in transaction records.

## Project Documentation

Detailed documentation will be added progressively:

* `docs/system-overview.md`
* `docs/transaction-workflow.md`
* `docs/database-overview.md`
* `docs/implementation-status.md`
* `docs/limitations-and-security.md`

## Scope and Limitations

This project was developed for academic purposes to explore web application development and transaction approval workflows.

It is not a production banking system. It does not execute real bank transfers or integrate with banking APIs. Its implementation and security limitations are documented separately.

## Learning Outcomes

* Core PHP web application development
* MySQL database connectivity using MySQLi
* PHP session-based login
* Form processing and validation
* Transaction record and status management
* Sequential approval workflows
* Database relationships and application security considerations
