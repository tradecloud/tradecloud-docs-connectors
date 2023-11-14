---
description: Order Events overview.
---

# Order Events

When using the order webhook you may configure and receive below order events.

### Order is issued or updated by buyer

The buyer can issue new order lines or update existing issued lines.

If confirmed delivery schedule or prices are updated, this will become a reopen request.

| OrderEvent                  | Webhook Configuration |
| --------------------------- |-----------------------|
| `OrderIssuedByBuyer`        | New order is issued by the buyer |
| `OrderLinesIssuedByBuyer`   | Additional order lines are added by the buyer |
| `OrderLinesReissuedByBuyer` | Updated order lines are reissued by the buyer |
| `OrderLinesUpdatedByBuyer`  | Order and line fields other than prices & delivery schedules are updated by the buyer |

### Order confirmed by supplier or buyer

The supplier can either accept, reject or propose an alternative (see next section).

- Accepted means that the supplier confirmed the order line(s) as requested by the buyer.
- Rejecting means that the supplier cannot deliver the order line(s) at all.
- Confirmed by supplier happens when the supplier confirms and [Auto Confirm](https://docs.tradecloud1.com/api/processes/order/buyer/issue/indicators#auto-confirm) has been enabled by the buyer.
- Confirmed by buyer is used when the buyer migrates already confirmed order lines to Tradecloud.

| OrderEvent                      | Webhook Configuration                     |
| ------------------------------- | ----------------------------------------- |
| `OrderLinesAcceptedBySupplier`  | Order lines are accepted by the supplier  |
| `OrderLinesRejectedBySupplier`  | Order lines are rejected by the supplier  |
| `OrderLinesConfirmedBySupplier` | Order lines are confirmed by the supplier |
| `OrderLinesConfirmedByBuyer`    | Order lines are confirmed by the buyer    |


### Order proposal by supplier

The supplier can propose an alternative delivery schedule or prices.

The buyer either approves or rejects the proposal.

| OrderEvent                            | Webhook Configuration                                        |
| --------------------------------------| ------------------------------------------------------------ |
| `OrderChangesProposedBySupplier`      | Order changes are proposed by the supplier                   |
| `OrderChangesProposalApprovedByBuyer` | By supplier proposed order changes are approved by the buyer |
| `OrderChangesProposalRejectedByBuyer` | By supplier proposed order changes are rejected by the buyer |

### Order updated by supplier

The supplier can update existing order lines.

If delivery schedule or prices are updated this will become either a proposal or reopen request.

| OrderEvent                     | Webhook Configuration                        |
| ------------------------------ | -------------------------------------------- |
| `OrderLinesUpdatedBySupplier`  | Order and line fields other than prices & delivery schedules are updated by the supplier |
| `OrderLinesItemDetailsChanged` | Order lines item details are changed by the supplier | 

### Order reopen request by buyer

The buyer can request to reopen confirmed order lines.

The supplier can either approve or reject the reopen request.

| OrderEvent                                  | Webhook Configuration                        |
| ------------------------------------------- | -------------------------------------------- |
| `OrderLinesReopenRequestedByBuyer`          | Order lines reopen is requested by buyer     |
| `OrderLinesReopenRequestApprovedBySupplier` | Buyer reopen request is approved by supplier |
| `OrderLinesReopenRequestRejectedBySupplier` | Buyer reopen request is rejected by supplier |

### Order reopen request by supplier

The supplier can request to reopen confirmed order lines.

The buyer can either approve or reject the reopen request.

| OrderEvent                               | Webhook Configuration                        |
| ---------------------------------------- | -------------------------------------------- |
| `OrderLinesReopenRequestedBySupplier`    | Order lines reopen is requested by supplier  |
| `OrderLinesReopenRequestApprovedByBuyer` | Supplier reopen request is approved by buyer |
| `OrderLinesReopenRequestRejectedByBuyer` | Supplier reopen request is rejected by buyer |

### Order lines cancelled by buyer

The buyer can cancel order lines without request.

| OrderEvent                   | Webhook Configuration                  |
| ---------------------------- | -------------------------------------- |
| `OrderLinesCancelledByBuyer` | Order lines are cancelled by the buyer |

### Order lines completed by buyer

The buyer can complete and revert completion of order lines.

| OrderEvent                           | Webhook Configuration                           |
| ------------------------------------ | ----------------------------------------------- |
| `OrderLinesCompletedByBuyer`         | Order lines are completed by the buyer          |
| `CompletedOrderLinesRevertedByBuyer` | Completed order lines are reverted by the buyer |

### Order lines logistics

Both buyer and supplier can update delivery schedule logistics fields `status`, `etd` and `eta`

| OrderEvent                                             | Webhook Configuration |
| ------------------------------------------------------ | --------------------- |
| `OrderLinesDeliveryScheduleLogisticsUpdatedByBuyer`    | Delivery schedule logistics fields are updated by the buyer    |
| `OrderLinesDeliveryScheduleLogisticsUpdatedBySupplier` | Delivery schedule logistics fields are updated by the supplier |

### Order contacts

Both buyer and supplier can update their order contact.

| OrderEvent                         | Webhook Configuration                                |
| ---------------------------------- | ---------------------------------------------------- |
| `OrderContactReassignedByBuyer`    | Buyer order contacts are reassigned in the portal    |
| `OrderContactReassignedBySupplier` | Supplier order contacts are reassigned in the portal |

### Maintenance

Buyer and supplier can resend order lines to their ERP system.

Order lines can be synced from the tradecloud.nl to the the Tradecloud One platform.

| OrderEvent              | Webhook Configuration                        |
| ----------------------- | -------------------------------------------- |
| `OrderResentByBuyer`    | The order is manually resent by the buyer    |
| `OrderResentBySupplier` | The order is manually resent by the supplier |
| `OrderSynced`           | The order is synced from the legacy platform |
