---
description: Webhook Events overview.
---

# Webhook Events

## Order Process Events

### Order issued and updated by buyer

The buyer can issue new order lines or update existing issued lines.

If confirmed delivery schedule or prices are updated this will become a reopen request.

| OrderEvent                  | Webhook Configuration                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------- |
| `OrderIssuedByBuyer`        | New order is issued by the buyer                                                      |
| `OrderLinesIssuedByBuyer`   | Additional order lines are added by the buyer                                         |
| `OrderLinesReissuedByBuyer` | Updated order lines are reissued by the buyer                                         |
| `OrderLinesUpdatedByBuyer`  | Order and line fields other than prices & delivery schedules are updated by the buyer |

### Order confirmed by supplier

The supplier can either accept, reject or propose an alternative (see next section).

| OrderEvent                     | Webhook Configuration                    |
| ------------------------------ | ---------------------------------------- |
| `OrderLinesAcceptedBySupplier` | Order lines are accepted by the supplier |
| `OrderLinesRejectedBySupplier` | Order lines are rejected by the supplier |

### Order proposal by supplier

The supplier can propose an alternative delivery schedule or prices.

The buyer either approves or rejects the proposal.

| OrderEvent                                                                  | Webhook Configuration                                        |
| --------------------------------------------------------------------------- | ------------------------------------------------------------ |
| `OrderChangesProposedBySupplier`                                            | Order changes are proposed by the supplier                   |
| <p><code>OrderChangesProposalApproved</code></p><p><code>ByBuyer</code></p> | By supplier proposed order changes are approved by the buyer |
| <p><code>OrderChangesProposalRejected</code></p><p><code>ByBuyer</code></p> | By supplier proposed order changes are rejected by the buyer |

### Order updated by supplier

The supplier can update existing order lines.

If delivery schedule or prices are updated this will become either a proposal or reopen request.

| OrderEvent                                                                     | Webhook Configuration                                                                    |
| ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| `OrderLinesUpdatedBySupplier`                                                  | Order and line fields other than prices & delivery schedules are updated by the supplier |
| <p><code>OrderLinesItemDetailsChanged</code></p><p><code>BySupplier</code></p> | Order lines item details are changed by the supplier                                     |

### Order reopen request by buyer

The buyer can request to reopen confirmed order lines.

The supplier can either approve or reject the reopen request.

| OrderEvent                                                               | Webhook Configuration                        |
| ------------------------------------------------------------------------ | -------------------------------------------- |
| <p><code>OrderLinesReopenRequested</code></p><p><code>ByBuyer</code></p> | Order lines reopen is requested by buyer     |
| `OrderLinesReopenRequestApprovedBySupplier`                              | Buyer reopen request is approved by supplier |
| `OrderLinesReopenRequestRejectedBySupplier`                              | Buyer reopen request is rejected by supplier |

### Order reopen request by supplier

The supplier can request to reopen confirmed order lines.

The buyer can either approve or reject the reopen request.

| OrderEvent                                                                  | Webhook Configuration                        |
| --------------------------------------------------------------------------- | -------------------------------------------- |
| <p><code>OrderLinesReopenRequested</code></p><p><code>BySupplier</code></p> | Order lines reopen is requested by supplier  |
| `OrderLinesReopenRequestApprovedByBuyer`                                    | Supplier reopen request is approved by buyer |
| `OrderLinesReopenRequestRejectedByBuyer`                                    | Supplier reopen request is rejected by buyer |

### Order lines cancelled by buyer

The buyer can cancel order lines without request.

| OrderEvent                   | Webhook Configuration                  |
| ---------------------------- | -------------------------------------- |
| `OrderLinesCancelledByBuyer` | Order lines are cancelled by the buyer |

### Order lines completed by buyer

The buyer can complete and revert completion of order lines.

| OrderEvent                                                                 | Webhook Configuration                           |
| -------------------------------------------------------------------------- | ----------------------------------------------- |
| `OrderLinesCompletedByBuyer`                                               | Order lines are completed by the buyer          |
| <p><code>CompletedOrderLinesReverted</code></p><p><code>ByBuyer</code></p> | Completed order lines are reopened by the buyer |

### Order lines logistics

Both buyer and supplier can update delivery schedule logistics fields `status`, `etd` and `eta`

| OrderEvent                                                                                   | Webhook Configuration                                          |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| <p><code>OrderLinesDeliverySchedule</code></p><p><code>LogisticsUpdatedByBuyer</code></p>    | Delivery schedule logistics fields are updated by the buyer    |
| <p><code>OrderLinesDeliverySchedule</code></p><p><code>LogisticsUpdatedBySupplier</code></p> | Delivery schedule logistics fields are updated by the supplier |

### Order contacts

Both buyer and supplier can update their order contact.

|                                                                          |                                                    |
| ------------------------------------------------------------------------ | -------------------------------------------------- |
| `OrderContactReassignedByBuyer`                                          | Buyer order contacts are updated via the portal    |
| <p><code>OrderContactReassigned</code></p><p><code>BySupplier</code></p> | Supplier order contacts are updated via the portal |



### Order maintenance

Buyer and supplier can resend order lines to their ERP system.

Order lines can be synced from the tradecloud.nl to the the Tradecloud One platform.

| OrderEvent              | Webhook Configuration                        |
| ----------------------- | -------------------------------------------- |
| `OrderResentByBuyer`    | The order is manually resent by the buyer    |
| `OrderResentBySupplier` | The order is manually resent by the supplier |
| `OrderSynced`           | The order is synced from the legacy platform |

## Order Document Events

The buyer and supplier can attach documents to the order.

Please note these events are not published when documents are embedded in the order.

| OrderDocumentEvent                | Webhook Configuration                                         |
| --------------------------------- | ------------------------------------------------------------- |
| `OrderDocumentsAttachedByBuyer`   | Document(s) are attached to the order or line by the buyer    |
| `OrderDocumentsAttachedBySupplie` | Document(s) are attached to the order or line by the supplier |

## Shipment Events

The supplier can send a despatch advice which will trigger a `ShipmentDespatchedBySupplier` event.

The buyer can resend a shipment to their ERP which will trigger a `ShipmentResentByBuyer` event.

| ShipmentEvent                  | Webhook Configuration |
| ------------------------------ | --------------------- |
| `ShipmentDespatchedBySupplier` | n/a                   |
| `ShipmentResentByBuyer`        | n/a                   |
