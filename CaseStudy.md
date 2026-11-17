# Ipak Yoli Ceramica
> version: 0.0.0.2

The company Ipak Yoli Ceramica brings tiles from ceramic factories in China and sells it from its warehouses in Uzbekistan. The database is used to support the catalogue, shipments, stock, sales, deliveries, payment and returns/write-offs.

Each product has a unique code, name, width and length in mm, pieces per box and square metres per box. It is associated with one or more categories (floor, wall, style or surface), and a category can also be related to a parent category. Stock is kept in stock pieces, one record for each product in its respective warehouse. Pieces are used to calculate square metres and boxes.

A shipment is one container with a unique container number, dispatch date, arrival date and a status of pending or approved. Items could be in a container from several suppliers, suppliers being factories with a name and country. The pair of supplier and product is unique for each shipment and each shipment line contains a record with supplier, product, warehouse and quantity. Stock has no value without the owner's approval of the shipment.

Only the owner can be an administrator. There is one account of manager in each warehouse for the person who receives goods, loads vehicles and supervises. Each user account is assigned a specific role of either administrator, warehouse manager, or shop, and will have a unique login. There are only one account per shop. Change to stock, shipments and sales are tracked in an audit log, with user, time and action recorded.

There are two types of buyer. Shops consist of independent businesses with a unique number, name, address (street, city, region), multiple phone numbers and a status of active or blocked. They can buy it later without any limits, but unpaid sale after 7 days will trigger an alert for the administrator. The admin can only block a shop, after which no new sale can be made to that shop. Other times a customer pays the entire amount on the spot and appears at the warehouse, and is documented with name and phone number, for a sale to the walk-in customer.

A sale has a unique invoice number, a unique receipt number within the shop, a date, a total discount and USD to UZS exchange rate and source of this exchange rate (bank or manual). Every line contains different product, a quantity which is not more than stock in the dispatching warehouse, the USD price per square metre and the discount.

There can be more than one delivery in a sale, and none delivery date is earlier than the sale date. A delivery will have a method – either self-pickup, shop driver, warehouse delivery, staff vehicle or truck depot, and a cost – the money paid for delivery, and a payer – the shop or warehouse where the delivery will take place, and a driver phone – the phone number of the driver (unless self-pickup). If a line is a sale line, then the delivery lines are the same, and the maximum amount of sale lines delivered is the maximum amount of lines ordered.

Shop payment may be split into multiple payments and multiple payments may be issued for one sale, but the total of the payment(s) may not exceed the total of the sale.

The changes in Stocks will alter one stock record. Adjustment: Customer return, write-off or combination of both, such as "customer returns damaged tiles". A return is a single line of sale, no more than what was sold minus any returns made before, and will require the administrator's approval after 30 days of delivery. There must be a reason for a write-off and cannot be more than the stock available.