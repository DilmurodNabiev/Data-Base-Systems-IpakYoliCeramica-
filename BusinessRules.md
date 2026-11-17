# Business Rules
> version: 0.0.0.6

1. STRUCTURAL RULES (RELATIONSHIPS AND MULTIPLICITY)
---------------------------------------------------

BR1: Each product must belong to one or many categories; a category may contain zero or many products.

BR2: Each category may have at most one parent category; a category may have zero or many child categories.

BR3: Each sale must be made to exactly one buyer, who is either a shop or a walk-in customer; a buyer may have zero or many sales.

BR4: Each sale must contain one or more sale lines, and each sale line must refer to exactly one product.

BR5: Each shipment (container) must contain one or more shipment lines, each for exactly one supplier, one product and one receiving warehouse; one shipment may mix suppliers.

BR6: Each delivery must belong to exactly one sale; a sale may have zero (not yet dispatched) or many deliveries (partial delivery).

BR7: Each delivery must contain one or more delivery lines, each referring to exactly one sale line of that sale.

BR8: Each payment must be made by exactly one shop and may be allocated to one or many sales; a sale may receive zero or many payments.

BR9: Each stock record must link exactly one product to exactly one warehouse, with at most one record for each product and warehouse pair.

BR10: Each stock adjustment must be a customer return, a write-off, or both, and must affect exactly one stock record; each return must also refer to exactly one sale line.

BR11: Each user account must have exactly one role, from Admin, Warehouse manager or Shop.

BR12: Each user account with the Shop role must belong to exactly one shop.


2. KEY AND UNIQUENESS RULES
---------------------------

BR13: Each product code, each shop number and each user login (including shop credentials) must be unique across its table.

BR14: Each sale must have a unique invoice number, and the combination of shop and paper-receipt number must also be unique.

BR15: A product may appear at most once in the same sale, and a supplier and product pair may appear at most once in the same shipment.


3. DOMAIN AND ATTRIBUTE RULES
-----------------------------

BR16: A product's tile width and length (in millimetres), pieces per box and m2 per box must each be greater than 0, and width, length and pieces per box must be whole numbers.

BR17: Every quantity on a sale, shipment, delivery or stock adjustment must be a positive whole number of pieces, and a stock record's quantity must be a whole number of at least 0.

BR18: A sale line's price per m2 in USD must be greater than 0, and its discount must be at least 0 and less than that price.

BR19: A sale's total discount must be at least 0 and no greater than the sale subtotal.

BR20: Each sale must store the USD to UZS exchange rate used, which must be greater than 0, with its source recorded as either Bank (suggested automatically) or Manual (edited).

BR21: A delivery's method must be one of: Self-pickup, Shop driver, Warehouse delivery, Staff personal vehicle, or Truck depot, and its driver phone number is required unless the method is Self-pickup.

BR22: A delivery's cost must be at least 0, and its payer must be either Shop or Warehouse.

BR23: A shipment's status must be either Pending or Approved, and its arrival date may not be earlier than its dispatch date.

BR24: A shop's status must be either Active or Blocked.

BR25: A delivery may not be dated before its sale, and a return may not be dated before the delivery of its sale line.

BR26: A product's square metres and boxes are calculated from pieces, using pieces per box and m2 per box, and are not stored separately.


4. ENTERPRISE RULES (SPANNING MORE THAN ONE TABLE)
--------------------------------------------------

BR27: A sale line may only be recorded if its quantity does not exceed the available stock of that product in the dispatching warehouse.

BR28: A shipment's quantities may only be added to stock after the shipment's status has been set to Approved by an Admin.

BR29: A new sale may not be created for a shop whose status is Blocked, and only an Admin may block or unblock a shop.

BR30: The total delivered quantity for a sale line must not exceed the quantity ordered on that sale line.

BR31: The total returned quantity for a sale line must not exceed the quantity delivered minus quantities already returned.

BR32: A return dated more than 30 days after the delivery may only be accepted if an Admin marks it as an approved exception.

BR33: The total payments allocated to a sale must not exceed that sale's final total after discounts and returns.

BR34: A write-off must record a reason, and its quantity must not exceed the available stock of that product in that warehouse.

BR35: A sale to a walk-in customer must be recorded as fully paid on the date of sale.

BR36: A shop sale that remains unpaid more than seven days after its sale date must raise an alert for the Admin.

BR37: Every change to stock, shipments and sales must be recorded in an audit log with the user, time and action.