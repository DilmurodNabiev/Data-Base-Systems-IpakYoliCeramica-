# Ipak Yoli Ceramica
> version: 0.0.0.1

Ipak Yoli Ceramica imports ceramic tiles from China’s ceramic factories and sells them from their warehouses in Uzbekistan. The catalogue, shipments, stock, sales, deliveries, payments, returns and write-offs are supported by the database.

Each product has a unique code, name, width and length in millimetres, pieces per box and square metres per box. It is a member of one or more categories, e.g., floor, wall, style or surface and a category can have a parent category. Stock is held in lots, each lot has a stock record, one stock record per product per warehouse. Pieces used for calculating square metres and boxes.

A shipment consists of one container and has a dispatch date, arrival date and shipment status. A container can contain products from multiple suppliers (factories, each with its name and country) and multiple suppliers can produce the same product. A supplier appears once per shipment line and a product appears once per shipment line, the number of pieces received is indicated, along with the receiving warehouse and the supplier. Once the stock is shipped, it does not enter stock until the owner approves them.

Administrator=Owner. Each warehouse has one manager who receives goods, loads vehicles and supervises. Each user account will have a distinct login and only one role (admin, warehouse manager or shop). Change to stock, shipments and sales are tracked in an audit log with the user and time.

There are two types of buyers. Shops are stand-alone businesses that have a unique number, name, address (street, city, region) and have multiple phone numbers. They might be able to pay later, no credit limit. If the sales are not paid for over seven days, the system notifies the admin. The administrator can deny access to a shop and there will be no new sale to the shop. At times a walk-in customer will purchase a product from the warehouse and pays the full amount at the time of the sale and is recorded and associated with the sale name and phone number.

The sale is the invoice for one paper receipt, the invoice number is unique for this paper receipt, the receipt number is unique for this paper receipt in the shop, the date, the total discount, the USD to UZS exchange rate and its origin (bank or manual). Each line is a product, with a quantity that does not exceed the dispatching warehouse's stock, a price per square metre and a discount.

There can be multiple deliveries for a sale. The delivery can be made by a method or by a self-pickup service, by a shop driver or a warehouse delivery, by a staff vehicle or a staff truck depot; it has a cost; it has a payer (shop or warehouse); a driver phone (unless self-pickup). The delivered includes the sale lines, and the total delivered won't be allowed to exceed the quantity ordered.

Shop payment can be spread over multiple sales and a sale can be covered by multiple payments, but no more than the total of the sale. A return is a return of a single sale that contains one or more lines. After 30 days from delivery it needs the administrator’s approval. Reason write off for damaged tiles not to exceed stock.