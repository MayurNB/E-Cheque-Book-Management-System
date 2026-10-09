# System Overview

## 1. Introduction

The E-Cheque Book Management System is an academic web application developed to model cheque-based payment requests and their approval process.

The system provides a centralized interface for managing users, banks, branches, payment transactions, and agreement-related information. It records transaction details and tracks the request through multiple approval stages.

The application was developed using Core PHP and MySQL, with Bootstrap, HTML, and CSS for the user interface.

## 2. Project Objectives

The main objectives of the project are:

* To manage user accounts and bank-related information.
* To provide an interface for initiating payment requests.
* To maintain transaction records in a MySQL database.
* To model a sequential approval process involving two banks.
* To allow relevant participants to track transaction status.
* To support rejection and cancellation through available actions.
* To record agreement information associated with selected transactions.

## 3. System Users

### Administrator

The administrator manages the system's user accounts, banks, and branches.

### Payer

The payer initiates a payment request by selecting a recipient and entering the payment details, including the amount and scheduled date.

### Recipient

The recipient is associated with the payment request and can review relevant transaction information. The agreement workflow also allows the recipient to accept or reject an agreement.

### Payer Bank Branch Staff

The payer's bank branch staff reviews the payment request during the first approval stage.

### Payer Bank Manager

The payer's bank manager reviews the request during the second approval stage.

### Recipient Bank Branch Staff

The recipient's bank branch staff reviews the request during the third approval stage.

### Recipient Bank Manager

The recipient's bank manager performs the fourth and final approval stage.

**Note:** The system contains different participants and approval stages, but its role-specific interface and permission controls should not be interpreted as a fully implemented enterprise-grade role-based access control system.

## 4. Main System Modules

### 4.1 Login and Session Management

Users log in using their credentials. PHP sessions maintain the login state, and application pages check the session before displaying user-specific information.

### 4.2 User and Bank Management

The administrative functionality supports managing user accounts, banks, and branches. User records can be associated with relevant bank and branch information.

### 4.3 Payment Management

The payment module allows a payer to select a recipient, enter the transaction amount and scheduled date, and submit a payment request.

The application stores transaction information in MySQL and presents the associated cheque-style record.

### 4.4 Approval Management

The approval module represents the four-stage transaction approval workflow. Each stage provides an approval action, and the transaction progresses through the stages in sequence.

Available rejection and cancellation actions can change the transaction status.

### 4.5 Transaction History and Status Tracking

Transaction records are stored in the database so relevant participants can review their information and current status.

Status updates are visible when the relevant page or record is refreshed or reopened. The application does not provide confirmed automatic real-time updates.

### 4.6 Agreement Management

The agreement module records additional information associated with a transaction, such as terms and purpose. The recipient can accept or reject an agreement, and the decision affects the associated transaction status.

## 5. High-Level Application Architecture

The application follows a basic PHP web application architecture.

1. **Presentation layer:** HTML, CSS, and Bootstrap provide the user interface.
2. **Application layer:** Core PHP handles page requests, form processing, application logic, and workflow actions.
3. **Database layer:** MySQL stores user, bank, transaction, approval-related, and agreement information. MySQLi is used for database connectivity.

Most application pages and actions are implemented through separate PHP files.

## 6. Technology Stack

| Layer                   | Technology                      |
| ----------------------- | ------------------------------- |
| Frontend                | HTML, CSS, Bootstrap            |
| Backend                 | Core PHP                        |
| Programming approach    | Primarily procedural PHP        |
| Database                | MySQL                           |
| Database connectivity   | MySQLi                          |
| Authentication state    | PHP sessions                    |
| Development environment | Local PHP and MySQL environment |

## 7. Scope of the Application

The system demonstrates how a payment request can be recorded, reviewed, and tracked through a sequence of approval stages.

It is a workflow management and simulation application, not a real banking or payment-processing platform. It does not transfer money between actual bank accounts or connect to live banking APIs.

## 8. Related Documentation

* [Project README](../README.md)
* [Transaction Workflow](transaction-workflow.md)
* [Database Overview](database-overview.md)
* [Implementation Status](implementation-status.md)
* [Limitations and Security](limitations-and-security.md)
