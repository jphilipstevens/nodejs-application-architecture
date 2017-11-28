# Node.js: beyond the route layer

> A discussion about how Node.js projects can be organized.


## Features

Shopping API with products, orders and bills.
* Products
  * Can be listed, created, found by id, deleted
  * Have an identifier, a name, a price and a weight
  * Products can be sorted by name, price or weight
* Orders
  * Can be created, listed, found by id and deleted
  * Have a status, a product list, a shipment amount, a total amount and a weight
  * Orders status can be pending, paid or canceled
  * Are offered 5% discount when the price exceeds 1000€
  * Shipment costs 25€ for every 10 more kg (50€ for 20kg, 75€ for 30kg, etc.)
* Bills
  * Can be listed
  * Have an amount and a creation date
  * Are automatically generated when an order status is set to paid


# What's wrong?

The file `index.js` owns each and every responsibility:
  * server initialization
  * route declaration
  * HTTP deserialization
  * business logic
  * database bindings
  * HTTP serialization
  
This has consequences:
  * code cannot be tested at the unit level
  * current tests can take a long time to run since they all hit the database
  * no abstraction to help reasoning
  * code repeats itself
  * the code is made of side-effects
  * code is not expressive
    
  
## License

[MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2017-2017 Simon Renoult.
