---
description: Order Documents Events overview.
---

# Order Documents Events

The buyer and supplier can attach documents to the order or line.

| OrderDocumentEvent                 | Webhook Configuration                                         |
| ---------------------------------- | ------------------------------------------------------------- |
| `OrderDocumentsAttachedByBuyer`    | Document(s) are attached to the order or line by the buyer    |
| `OrderDocumentsAttachedBySupplier` | Document(s) are attached to the order or line by the supplier |

{% hint style="warning" %}
Please note these events are not published when documents are embedded in the order and not explicitly attached.
{% endhint %}
