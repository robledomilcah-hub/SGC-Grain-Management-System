# SGC AI Discovery & Collaboration Log
**Course:** INTE 351 — Systems Analysis and Design  
**Case:** Sintang Grains Cooperative (SGC)  
**Topic:** Requirement-Driven Vibe Coding & AI Collaboration

## 1. Stakeholder needs identified

| Stakeholder | Problem from interview | System response |
|---|---|---|
| Cooperative Manager | Does not know the current stock until the next morning; needs a monthly board report. | Live inventory totals and a monthly activity summary. |
| Records Clerk | Handwritten records are difficult to read; needs quick entry and farmer delivery history. | A short delivery form, farmer lookup, and delivery history table. |
| Regional Grain Trader | Receives only verbal confirmation and has experienced order quantity differences. | Stock-checked buyer orders and a printable order confirmation slip. |

## 2. Core domain model

### Farmer
- Attributes: farmerID, name, contact
- Behavior: findFarmer(), viewDeliveryHistory()

### Grain
- Attributes: grainID, grainName, availableStock
- Behavior: addStock(quantity), deductStock(quantity), checkAvailability(quantity)

### Delivery
- Attributes: deliveryID, farmerID, grainID, quantityKg, deliveryDate
- Behavior: recordDelivery()

### Buyer
- Attributes: buyerID, buyerName, contact
- Behavior: placeOrder()

### Order
- Attributes: orderID, buyerID, grainID, quantityKg, orderDate, status
- Behavior: validateStock(), confirmOrder(), generateReceipt()

## 3. Relationships and business rules
- One Farmer can have many Deliveries.
- One Grain can be associated with many Deliveries.
- One Buyer can place many Orders.
- One Grain can be included in many Orders.
- A delivery increases the selected grain's available stock.
- A confirmed order decreases available stock.
- An order must not be confirmed when its quantity is greater than the current available stock.
- The order confirmation must show the exact buyer, grain, quantity, date, and order number.

## 4. Initial proposal vs. refined model

| Initial AI suggestion | Final refined decision | Reason |
|---|---|---|
| Add separate warehouse, supplier, truck, payment, and invoice entities. | Keep the prototype focused on Farmer, Grain, Delivery, Buyer, and Order. | These extra entities are not required by the three interviews. |
| Require many farmer details for every delivery. | Use farmer ID/name lookup and only ask for grain, quantity, and date. | The clerk needs to record deliveries quickly at the counter. |
| Allow buyers to submit an order and approve it later without checking stock. | Check current stock before confirming; reject over-stock orders. | This prevents SGC from promising grain that is unavailable. |
| Make a complex financial report. | Provide a simple monthly summary of received grain, ordered grain, and available stock. | The manager specifically requested a simple board report. |

## 5. Prompts used for AI collaboration

**Prompt 1 — Requirement discovery**  
"Based only on the three Sintang Grains Cooperative stakeholder interviews, identify the core entities, their attributes, behaviors, and relationships. Do not write code yet. Explain which stakeholder problem each entity solves."

**Prompt 2 — Counter-speed challenge**  
"How can the delivery form help the Records Clerk enter a farmer delivery in under 30 seconds? Reduce unnecessary fields and support quick farmer lookup."

**Prompt 3 — Inventory validation challenge**  
"Explain how the system can update grain stock immediately after a delivery and prevent a buyer from ordering more than the available quantity."

**Prompt 4 — Scope refinement**  
"Review your proposed entities. Remove features and data fields that are not supported by the interviews. Keep the model simple and appropriate for a small cooperative."

**Prompt 5 — Prototype request**  
"Build a simple responsive web prototype with a delivery form, live inventory dashboard, stock-verified buyer orders, printable confirmation receipt, and monthly report. Use a soft pink, lavender, and cream color palette. Use beginner-friendly HTML, CSS, and JavaScript."

## 6. Prototype features tested
- Recorded a delivery using a registered farmer, grain type, and quantity.
- Checked that the grain stock increased after saving a delivery.
- Placed a buyer order within available stock and checked that stock decreased.
- Entered an order greater than available stock and checked that the system rejected it.
- Opened and printed the buyer's order confirmation slip.
- Viewed the summary report.

## 7. Scope and limitations
This is a front-end classroom prototype. It stores demonstration data in the browser's local storage. It does not yet have a shared online database, user authentication, SMS notifications, or multi-user access. The sample farmer and starting grain stock records are for demonstration only and should be replaced with verified cooperative data in a real implementation.
