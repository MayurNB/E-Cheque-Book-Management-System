# Transaction Workflow

## 1. Overview

The E-Cheque Book Management System models a payment request as a sequence of approval stages involving the payer's bank and the recipient's bank.

The application stores transaction information in MySQL and updates the transaction status as workflow actions are performed.

This workflow represents internal application processing. It does not execute a real bank transfer.

## 2. Payment Initiation

The transaction begins when a payer chooses the payment option.

The general process is:

1. The payer opens the cheque-style payment interface.
2. The payer searches for the recipient using the recipient's ID.
3. The application displays the matching recipient information.
4. The payer selects the intended recipient.
5. The payer enters the payment amount and scheduled date.
6. The payer confirms and submits the payment request.
7. The application records the transaction and makes it available for the subsequent workflow stages.

The cheque-style record contains transaction information such as payer details, recipient details, amount, scheduled date, cheque number, bank details, purpose, and status.

## 3. Four-Stage Approval Process

### Stage 1: Payer Bank Branch Staff

The payment request is presented for review by the payer's bank branch staff.

The staff member can perform the available approval or rejection action. Approval allows the request to proceed to the next stage.

### Stage 2: Payer Bank Manager

After the first stage is approved, the request proceeds to the payer's bank manager.

The manager reviews the request and performs the available approval or rejection action. Approval allows the request to proceed to the recipient's bank.

### Stage 3: Recipient Bank Branch Staff

The request then reaches the recipient's bank branch staff for review.

Approval allows the request to proceed to the recipient bank manager.

### Stage 4: Recipient Bank Manager

The recipient's bank manager performs the final approval stage.

Once this stage is approved, the application marks the transaction as completed.

## 4. Workflow Summary

The normal approval sequence is:

Payer initiates payment → Payer bank branch staff → Payer bank manager → Recipient bank branch staff → Recipient bank manager → Completed

Each stage represents a separate review action in the application.

## 5. Transaction Rejection

A participant with an available rejection action can reject a transaction during the workflow.

When a rejection action is performed, the transaction status changes to indicate rejection. The request does not continue through the normal approval sequence as though it had been approved.

The exact status transitions depend on the application's implemented logic.

## 6. Transaction Cancellation

The application includes cancellation options for the payer, recipient, and bank staff or managers.

When an available cancellation action is performed, the transaction status is updated to indicate cancellation.

Cancellation is distinct from rejection: rejection represents a decision not to approve the request, while cancellation represents an action to stop the request.

## 7. Transaction Status Tracking

The application stores transaction status information in MySQL.

Relevant participants can review the transaction and its status through the available application pages. After a workflow action updates the stored status, users may need to refresh or reopen the relevant page to see the latest information.

The application is not confirmed to provide automatic real-time status updates.

The status labels known to be used or associated with the workflow include:

* Pending
* Approved
* Rejected
* Cancelled
* Completed

These labels should not be interpreted as a complete list of every internal status value or intermediate transition.

## 8. Scheduled Date

The payer enters a scheduled date when creating the payment request. The scheduled date is stored with the transaction information.

The application's exact date-based processing mechanism has not been documented here, so this document does not claim that a background scheduler or automatic bank-processing mechanism is implemented.

## 9. Agreement-Related Workflow

The application also supports an agreement workflow associated with a transaction.

1. The payer selects a recipient and enters the payment details.
2. The payer provides the available agreement information, including terms and purpose.
3. The application stores the agreement details and links them to the transaction.
4. The recipient can accept or reject the agreement.
5. The agreement decision affects the transaction status.

This functionality records agreement-related information within the application. It should not be interpreted as a legally verified electronic contract or digital-signature service.

## 10. Workflow Limitations

* The approval sequence is managed within the application.
* The system does not transfer real money.
* No live banking API integration is claimed.
* Status tracking relies on stored application data rather than confirmed real-time notifications.
* The workflow represents an academic implementation and should not be treated as a production banking process.

## Related Documentation

* [Project README](../README.md)
* [System Overview](system-overview.md)
* [Database Overview](database-overview.md)
* [Implementation Status](implementation-status.md)
* [Limitations and Security](limitations-and-security.md)
