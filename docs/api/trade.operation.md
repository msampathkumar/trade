# trade.operation

This module contains the class definitions of Operation and Daytrade.
You can use them by just:

```python
import trade
operation = trade.Operation(args...)
```


## trade.operation.Operation
An operation represents the purchase or the sale of an asset.

### Attributes:  
+ date: A string 'YYYY-mm-dd', the date the operation occurred.
+ asset: An Asset instance, the asset that is being traded.
+ quantity: A number representing the quantity being traded.
    - Positive quantities represent a purchase.
    - Negative quantities represent a sale.
+ price: The raw unitary price of the asset being traded.
+ comissions: A dict of discounts. String keys and float values
  representing the name of the discounts and the values
  to be deducted from the operation.
+ taxes: A dict of taxes. string keys and float values
  representing the name of the taxes and the values of the
  taxes to be applied to the operation. Tax values are always
  represented as a percentage. Taxes are applied based on the
  volume of the operation.

### Properties:

#### real_value
Returns the quantity * the real price of the operation.

#### real_price
Returns the real price of the operation.

The real price is the price with all comissions and taxes
already deducted or added.

#### total_comission
Return the sum of all comissions included in this operation.

#### volume
Returns the quantity of the operation * its raw price.


## trade.operation.Daytrade
A daytrade operation.

Daytrades are operations of purchase and sale of an Asset on
the same date.

### Attributes:
+ asset: An asset instance, the asset that is being traded.
+ quantity: The traded quantity of the asset.
+ purchase: A Operation object representing the purchase of the asset.
+ sale: A Operation object representing the sale of the asset.

### Properties

#### result
Returns the profit or the loss generated by the daytrade.

### Methods:

#### init(self, date, asset, quantity, buy_price, sale_price)
Creates the daytrade object.

Base on the informed values this method creates 2 operations:
- a purchase operation
- a sale operation

Both operations (self.purchase and self.sale) can be treated
like any other operation when it comes to taxes and prorate
of commissions.


Copyright (c) 2015 Rafael da Silva Rocha  
rocha.rafaelsilva@gmail.com  
http://github.com/rochars/trade  
http://trade.readthedocs.org  