---
title: "10+ Complex typeScript type defining Tips for Development"
seoTitle: "10+ Complex typeScript type defining Tips for Development"
seoDescription: "I'd be happy to provide you with an advanced TypeScript example involving complex typing."
datePublished: Thu Aug 10 2023 04:00:09 GMT+0000 (Coordinated Universal Time)
cuid: cll4ms99v000d09l3cxk4cus0
slug: 10-complex-typescript-type-defining-tips-for-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691605125575/deee2d91-59b2-4b38-9784-25effd141f43.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691605212546/37b2fc9d-d274-49ab-a3cf-586e8a3c4b98.png
tags: web-development, typescript, beginners

---

let's take a look at how you can build complex types in TypeScript using examples of JSON-like structures.

## 1.Plain object

```typescript
const fullName: { firstName: string; lastName: string } = {
  firstName: 'Lakshmanan',
  lastName: 'Arumugam'
};

console.log(fullName.firstName)
// Output Lakshmanan
```

## 2.**Numeric Enum Variable Assignment**

```typescript
enum Weekend {
  Friday = 5,
  Saturday,
  Sunday
};

// Assign a valid value of Weekend
const today: Weekend = 7;  // No bug
console.log(`Today is the ${today}th day of the week!`);
// Output: "Today is the 7th day of the week!"
```

## 3.**Array Type Inference on Tuple**

```typescript
const threeWords: [ string, number, string] = ['Won', 5, 'games'];

// Calling .concat() on a tuple returns an array
let moreWords = threeWords.concat(['last', 'night']);

// An array is expandable
moreWords[5] = ('!');

console.log(moreWords);
// Output: ["Won", 5, "games", "last", "night", "!"]
```

## 4.Array of basic type

```typescript
const marks: number[] = [ 100, 500, 300, 200, 400 ]

console.log("mark value", marks[0])

// Output: 100
```

## 5.Array Generic type

```typescript
// zipcodes is an array of strings
let zipcodes: Array<string> = ['03255', '02134', '08002', '03063'];

// Pushing a number to zipcodes will generate an error
// Error: Argument of type 'number' is not assignable to parameter of type 'string'.
zipcodes.push(05115);
```

## 6.Object key string and value

```typescript
interface StatusObject {
    id: number;
    name: string;
}

interface Status {
    [key: string]: StatusObject
}

const statusValues: Status = {
    "0": { "id": 0, "name": "Available" },
    "1": { "id": 1, "name": "Ready" },
    "2": { "id": 2, "name": "Started" }
 };

 console.log(statusValues["0"].name)
//  Output: "Available"
```

## 7.Array of object

```typescript

interface Color {
    color: string;
    value: string;
}

const colors:Color[] = [
	{
		color: "red",
		value: "#f00"
	},
	{
		color: "green",
		value: "#0f0"
	}
]

console.log(colors[0].color)
// Output: "red"
```

## 8.Highly nested object and array values

```typescript
interface Bakery {
    id:      string;
    type:    string;
    name:    string;
    ppu:     number;
    batters: Batters;
    topping: Topping[];
}

interface Batters {
    batter: Topping[];
}

interface Topping {
    id:   string;
    type: string;
}


const bakery: Bakery =  {
  "id": "0001",
  "type": "donut",
  "name": "Cake",
  "ppu": 0.55,
  "batters": {
    "batter": [
      {
        "id": "1001",
        "type": "Regular"
      }
    ]
  },
  "topping": [
    {
      "id": "5001",
      "type": "None"
    }
  ]
}

console.log(bakery.batters.batter[0].id)
// Output: "1001"
```

## 9.Object value required field(Utility)

```typescript
interface Car {
  make: string;
  model: string;
  mileage?: number;
}

let FordCard: Required<Car> = {
  make: 'Ford',
  model: 'Focus',
  mileage: 12000 // `Required` forces mileage to be defined
};

let KiaCard: Required<Car> = {
  make: 'Ford',
  model: 'Focus'
};

//Error
//Property 'mileage' is missing in type '{ make: string; model: string; }' but required in type 'Required<Car>'.
```

## 10.Inheritance existing type defintion

```typescript
interface Brand {
  brand: string;
}

interface Model extends Brand {
  model: string;
}

class Car implements Model {
  brand;
  model;
  constructor(brand: string, model: string) {
    this.brand = brand;
    this.model = model;
  }
  log() {
    console.log(`Drive a ${this.brand} ${this.model} today!`);
  }
}

const myCar: Car = new Car('Nissan', 'Sentra'); 
myCar.log();

// Output: "Drive a Nissan Sentra today!"
```

## 11.Complex API response typing

```typescript
// Define types for product and customer
type Product = {
  id: number;
  name: string;
  price: number;
  stock: number;
};

type Customer = {
  id: number;
  name: string;
  email: string;
};

// Define types for order and order status
type OrderStatus = "pending" | "processing" | "shipped" | "delivered" | "cancelled";

type Order = {
  id: number;
  customer: Customer;
  products: { product: Product; quantity: number }[];
  status: OrderStatus;
};

// Define type for the inventory management system
type InventorySystem = {
  products: Product[];
  customers: Customer[];
  orders: Order[];
  addProduct: (product: Product) => void;
  addCustomer: (customer: Customer) => void;
  placeOrder: (order: Order) => void;
};

// Create an instance of the inventory management system
const inventory: InventorySystem = {
  products: [],
  customers: [],
  orders: [],
  addProduct(product) {
    this.products.push(product);
  },
  addCustomer(customer) {
    this.customers.push(customer);
  },
  placeOrder(order) {
    // Check if products are in stock before placing the order
    for (const { product, quantity } of order.products) {
      const availableProduct = this.products.find(p => p.id === product.id);
      if (!availableProduct || availableProduct.stock < quantity) {
        throw new Error(`Product ${product.name} is out of stock.`);
      }
    }

    // Deduct ordered quantities from the product stock
    for (const { product, quantity } of order.products) {
      const availableProduct = this.products.find(p => p.id === product.id);
      if (availableProduct) {
        availableProduct.stock -= quantity;
      }
    }

    this.orders.push(order);
  },
};

// Example usage
const newProduct: Product = { id: 1, name: "Widget", price: 10, stock: 100 };
inventory.addProduct(newProduct);

const newCustomer: Customer = { id: 1, name: "Alice", email: "alice@example.com" };
inventory.addCustomer(newCustomer);

const newOrder: Order = {
  id: 1,
  customer: newCustomer,
  products: [{ product: newProduct, quantity: 3 }],
  status: "pending",
};
inventory.placeOrder(newOrder);

console.log(inventory);
// Output: 
// {
//   "products": [
//     {
//       "id": 1,
//       "name": "Widget",
//       "price": 10,
//       "stock": 97
//     }
//   ],
//   "customers": [
//     {
//       "id": 1,
//       "name": "Alice",
//       "email": "alice@example.com"
//     }
//   ],
//   "orders": [
//     {
//       "id": 1,
//       "customer": {
//         "id": 1,
//         "name": "Alice",
//         "email": "alice@example.com"
//       },
//       "products": [
//         {
//           "product": {
//             "id": 1,
//             "name": "Widget",
//             "price": 10,
//             "stock": 97
//           },
//           "quantity": 3
//         }
//       ],
//       "status": "pending"
//     }
//   ]
// }
```

## Conclusion:

This example demonstrates how TypeScript's advanced typing features can be used to ensure type safety and structure in a complex application scenario.

For more examples check out [my blogs](https://lakshmananarumugam.com/)