---
title: "Enum in javascript 🤯"
seoTitle: "Enum in javascript"
seoDescription: "In JavaScript, there is no built-in enum type like in some other programming languages (e.g., Typescript, Java or C#)."
datePublished: Wed Jul 26 2023 04:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clkj76h4y00040amieje8cgq9
slug: enum-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690307100996/db746d93-d782-4d9f-8a34-ce839b9e7eee.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690309002767/9985430f-e852-451d-a0da-3f2be3d070db.png
tags: javascript, web-development, beginner, typescript

---

In JavaScript, there is no built-in `enum` type like in some other programming languages (e.g., Java or C#). However, you can create enumerations using various techniques. One common approach is to use objects or constants to represent the enum values. Here's an example of how to create an "enum" in JavaScript:

# In Javascript

### **Example 1: Using Object**

```javascript
const Colors = {
  RED: 'red',
  GREEN: 'green',
  BLUE: 'blue',
};

// Usage
const selectedColor = Colors.BLUE;
console.log(selectedColor); // Output: "blue"
```

### **Example 2: Using Constants**

```javascript
const RED = 0;
const GREEN = 1;
const BLUE = 2;

// Usage
const selectedColor = BLUE;
console.log(selectedColor); // Output: 2
```

It's important to note that using objects for enums allows you to define more meaningful names for the enum values, making the code more self-explanatory. On the other hand, using constants may be preferred for simpler scenarios where you don't require complex enum values.

### **Example 3: Enum with Methods**

You can also add methods to your "enum" by using object literals and defining functions as values:

```javascript
const Operation = {
  ADD: (a, b) => a + b,
  SUBTRACT: (a, b) => a - b,
  MULTIPLY: (a, b) => a * b,
  DIVIDE: (a, b) => a / b,
};

// Usage
console.log(Operation.ADD(2, 3)); // Output: 5
console.log(Operation.MULTIPLY(4, 5)); // Output: 20
```

### **Example 4: Enum with Symbol Keys**

Using symbols as keys provide more privacy, as the properties can't be easily accessed from outside the enum object.

```javascript
const Colors = {
  RED: Symbol(),
  GREEN: Symbol(),
  BLUE: Symbol(),
};

// Usage
const selectedColor = Colors.BLUE;
console.log(selectedColor === Colors.BLUE); // Output: true
```

### **Example 5: Enum with Read-only Properties**

In this example, we create an object with read-only properties using `Object.defineProperty`.

```javascript
const DaysOfWeek = {};

Object.defineProperty(DaysOfWeek, "MONDAY", {
  value: 1,
  writable: false,
  enumerable: true,
  configurable: false,
});

Object.defineProperty(DaysOfWeek, "TUESDAY", {
  value: 2,
  writable: false,
  enumerable: true,
  configurable: false,
});

// Usage
console.log(DaysOfWeek.MONDAY); // Output: 1
console.log(DaysOfWeek.TUESDAY); // Output: 2

// Trying to modify the enum values will have no effect
DaysOfWeek.MONDAY = 99;
console.log(DaysOfWeek.MONDAY); // Output: 1 (unchanged)
```

### **Example 6: Using a Class**

You can also use a class to create an enum-like structure.

```javascript
class Direction {
  static NORTH = new Direction('North');
  static EAST = new Direction('East');
  static SOUTH = new Direction('South');
  static WEST = new Direction('West');

  constructor(name) {
    this.name = name;
  }
}

// Usage
const myDirection = Direction.NORTH;
console.log(myDirection.name); // Output: "North"
```

### **Example 7: Enum with Additional Properties**

You can include additional properties for each enum value.

```javascript
const PizzaToppings = {
  PEPPERONI: { name: 'Pepperoni', price: 2.5 },
  MUSHROOMS: { name: 'Mushrooms', price: 1.8 },
  ONIONS: { name: 'Onions', price: 1.2 },
};

// Usage
const selectedTopping = PizzaToppings.PEPPERONI;
console.log(selectedTopping.name); // Output: "Pepperoni"
console.log(selectedTopping.price); // Output: 2.5
```

### **Example 8: Enum with Custom Methods**

You can add custom methods to the "enum" objects to perform specific actions based on the enum value.

```javascript
const TrafficLight = {
  RED: 'red',
  YELLOW: 'yellow',
  GREEN: 'green',
  isRed: function (color) {
    return color === TrafficLight.RED;
  },
  isYellow: function (color) {
    return color === TrafficLight.YELLOW;
  },
  isGreen: function (color) {
    return color === TrafficLight.GREEN;
  },
};

// Usage
console.log(TrafficLight.isRed(TrafficLight.RED)); // Output: true
console.log(TrafficLight.isGreen('blue')); // Output: false
```

### **Example 9: Enum with String Values and Descriptions**

In this example, we'll create an "enum" with string values and include descriptions for each value.

```javascript
const Gender = {
  MALE: 'M',
  FEMALE: 'F',
  OTHER: 'O',
};

// Function to get the description for a gender value
Gender.getDescription = function (gender) {
  switch (gender) {
    case Gender.MALE:
      return 'Male';
    case Gender.FEMALE:
      return 'Female';
    case Gender.OTHER:
      return 'Other';
    default:
      return 'Unknown';
  }
};

// Usage
console.log(Gender.getDescription(Gender.FEMALE)); // Output: "Female"
console.log(Gender.getDescription('X')); // Output: "Unknown"
```

### **Example 10: Enum with Autogenerated Numeric Values**

Here, we create an "enum" where the numeric values are generated automatically.

```javascript
const DaysOfWeek = {
  MONDAY: 1,
  TUESDAY: 2,
  WEDNESDAY: 3,
  THURSDAY: 4,
  FRIDAY: 5,
  SATURDAY: 6,
  SUNDAY: 7,
};

// Usage
const dayNumber = DaysOfWeek.FRIDAY;
console.log(dayNumber); // Output: 5
```

### **Example 11: Enum with Object Methods**

In this example, we use object methods to encapsulate behaviour within the "enum".

```javascript
const Coin = {
  PENNY: {
    value: 0.01,
    flip: function () {
      return Math.random() >= 0.5 ? 'Heads' : 'Tails';
    },
  },
  NICKEL: {
    value: 0.05,
    flip: function () {
      return Math.random() >= 0.5 ? 'Heads' : 'Tails';
    },
  },
  DIME: {
    value: 0.10,
    flip: function () {
      return Math.random() >= 0.5 ? 'Heads' : 'Tails';
    },
  },
  QUARTER: {
    value: 0.25,
    flip: function () {
      return Math.random() >= 0.5 ? 'Heads' : 'Tails';
    },
  },
};

// Usage
const randomCoin = Math.random() >= 0.5 ? Coin.QUARTER : Coin.DIME;
console.log(randomCoin.flip()); // Output: Either "Heads" or "Tails"
```

These examples demonstrate different ways of creating enum-like structures in JavaScript, each tailored to different scenarios and use cases. Choose the approach that best fits your application's needs and coding style.

# **In Typescript:**

TypeScript enums offer several advantages over traditional JavaScript enums or other approaches to represent constants or related values. Some of the key advantages include:

1. **Type Safety**: TypeScript enums provide type safety, ensuring that you can only assign values that are part of the enum's defined set. This helps catch errors early during development and provides better tooling support, including autocompletion and type checking.
    
2. **Readable Code**: Enum members in TypeScript can have descriptive names, making your code more self-explanatory and easier to read and understand.
    
3. **Autocompletion and Intellisense**: When using TypeScript enums, your IDE can offer autocompletion and intellisense suggestions for enum members, reducing the likelihood of typos and making the coding process more efficient.
    
4. **Reverse Mapping**: TypeScript enums support reverse mapping, allowing you to get the string name (key) of an enum member based on its value. This feature can be useful when you need to convert between numeric values and their associated symbolic names.
    
5. **Enum Functions**: You can add functions and static members to TypeScript enums, enabling you to encapsulate behaviour specific to the enum values.
    
6. **Namespace and Augmentation**: You can use namespaces and module augmentation to extend existing enums, adding new members or functions without modifying the original definition.
    
7. **Enums with Different Value Types**: TypeScript allows enums to have members with different types, providing greater flexibility in representing related values.
    
8. **Heterogeneous Enums**: TypeScript supports heterogeneous enums, where members can have different underlying data types, such as strings and numbers.
    
9. **Bit Flags**: TypeScript enums can be used as bit flags, allowing you to represent multiple options with a single value and perform bitwise operations on them.
    
10. **Stronger Refactoring Support**: When you change an enum value or add a new member, the TypeScript compiler will highlight all the places where the enum is used, making it easier to refactor your code.
    
11. **Better Debugging**: Enums in TypeScript retain their names during debugging, making it easier to interpret their values in the developer tools.
    

Overall, TypeScript enums provide a powerful and expressive way to define related constants and related values, offering the benefits of type safety, readability, and enhanced tooling support. They help make your code more robust, maintainable, and less error-prone, making TypeScript an excellent choice for building scalable and reliable applications.

Now implemented in TypeScript to create strongly-typed enumerations:

### **Example 1: Enum with Union Type**

```typescript
enum Colors {
  RED = 'red',
  GREEN = 'green',
  BLUE = 'blue',
}

// Usage
const selectedColor: Colors = Colors.BLUE;
console.log(selectedColor); // Output: "blue"
```

### **Example 2: Enum with Numeric Values**

```javascript
enum Direction {
  NORTH = 1,
  EAST,
  SOUTH,
  WEST,
}

// Usage
const myDirection: Direction = Direction.NORTH;
console.log(myDirection); // Output: 1
```

### **Example 3: Enum with Additional Properties**

```typescript
enum PizzaToppings {
  PEPPERONI = 'Pepperoni',
  MUSHROOMS = 'Mushrooms',
  ONIONS = 'Onions',
}

// Additional properties for each enum value
interface ToppingInfo {
  name: string;
  price: number;
}

const ToppingsInfo: { [key in PizzaToppings]: ToppingInfo } = {
  [PizzaToppings.PEPPERONI]: { name: 'Pepperoni', price: 2.5 },
  [PizzaToppings.MUSHROOMS]: { name: 'Mushrooms', price: 1.8 },
  [PizzaToppings.ONIONS]: { name: 'Onions', price: 1.2 },
};

// Usage
const selectedTopping: PizzaToppings = PizzaToppings.PEPPERONI;
console.log(ToppingsInfo[selectedTopping].name); // Output: "Pepperoni"
console.log(ToppingsInfo[selectedTopping].price); // Output: 2.5
```

### **Example 4: Enum with String Values and Descriptions**

```typescript
enum Gender {
  MALE = 'M',
  FEMALE = 'F',
  OTHER = 'O',
}

// Function to get the description for a gender value
function getGenderDescription(gender: Gender): string {
  switch (gender) {
    case Gender.MALE:
      return 'Male';
    case Gender.FEMALE:
      return 'Female';
    case Gender.OTHER:
      return 'Other';
    default:
      return 'Unknown';
  }
}

// Usage
const selectedGender: Gender = Gender.FEMALE;
console.log(getGenderDescription(selectedGender)); // Output: "Female"
```

### **Example 5: Enum with Custom Methods**

```javascript
enum TrafficLight {
  RED = 'red',
  YELLOW = 'yellow',
  GREEN = 'green',
}

// Custom methods for the enum
namespace TrafficLight {
  export function isRed(color: TrafficLight): boolean {
    return color === TrafficLight.RED;
  }

  export function isYellow(color: TrafficLight): boolean {
    return color === TrafficLight.YELLOW;
  }

  export function isGreen(color: TrafficLight): boolean {
    return color === TrafficLight.GREEN;
  }
}

// Usage
console.log(TrafficLight.isRed(TrafficLight.RED)); // Output: true
console.log(TrafficLight.isGreen('blue')); // Output: false
```

### **Example 6: Enum with Methods and Static Members**

In this example, we create an enum with additional methods and static members.

```typescript
enum MathOperation {
  ADD = 'add',
  SUBTRACT = 'subtract',
  MULTIPLY = 'multiply',
  DIVIDE = 'divide',
}

namespace MathOperation {
  export function performOperation(op: MathOperation, a: number, b: number): number {
    switch (op) {
      case MathOperation.ADD:
        return a + b;
      case MathOperation.SUBTRACT:
        return a - b;
      case MathOperation.MULTIPLY:
        return a * b;
      case MathOperation.DIVIDE:
        return a / b;
      default:
        throw new Error('Invalid operation');
    }
  }

  export const availableOperations: MathOperation[] = [
    MathOperation.ADD,
    MathOperation.SUBTRACT,
    MathOperation.MULTIPLY,
    MathOperation.DIVIDE,
  ];
}

// Usage
console.log(MathOperation.performOperation(MathOperation.ADD, 5, 3)); // Output: 8
console.log(MathOperation.availableOperations); // Output: ["add", "subtract", "multiply", "divide"]
```

### **Example 7: Enum with Computed Values**

You can use computed values in TypeScript enums, which allows for more dynamic behaviour.

```typescript
enum Season {
  SPRING = 1,
  SUMMER = getSummer(),
  AUTUMN = 4,
  WINTER = 5,
}

function getSummer(): number {
  return Season.SPRING + 1;
}

// Usage
console.log(Season.SPRING); // Output: 1
console.log(Season.SUMMER); // Output: 2 (computed based on getSummer())
console.log(Season.AUTUMN); // Output: 4
```

### **Example 8: Enum with Symbols**

You can use symbols in TypeScript enums to create unique, non-enumerable properties.

```typescript
const Colors = {
  RED: Symbol('red'),
  GREEN: Symbol('green'),
  BLUE: Symbol('blue'),
} as const;

type Color = typeof Colors[keyof typeof Colors];

// Usage
const selectedColor: Color = Colors.GREEN;
console.log(selectedColor); // Output: Symbol(green)
```

### **Example 9: Heterogeneous Enums**

TypeScript allows heterogeneous enums where enum members have different value types.

```typescript
enum Status {
  Active = 'ACTIVE',
  Inactive = 0,
}

// Usage
const userStatus: Status = Status.Active;
console.log(userStatus); // Output: "ACTIVE"
console.log(Status.Inactive); // Output: 0
```

### **Example 10: Computed Enum Member Names**

You can use expressions to compute enum member names.

```typescript
const prefix = 'ITEM_';

enum Items {
  FIRST = prefix + 'A',
  SECOND = prefix + 'B',
  THIRD = prefix + 'C',
}

// Usage
console.log(Items.FIRST); // Output: "ITEM_A"
console.log(Items.SECOND); // Output: "ITEM_B"
```

### **Example 11: Enum with Methods and Different Value Types**

In this example, we create an enum with methods and members having different value types.

```typescript
enum MediaType {
  IMAGE = 'image',
  VIDEO = 'video',
  AUDIO = 'audio',
}

interface MediaInfo {
  type: MediaType;
  url: string;
  duration?: number;
}

namespace MediaFactory {
  export function createMedia(type: MediaType, url: string, duration?: number): MediaInfo {
    return { type, url, duration };
  }
}

// Usage
const image = MediaFactory.createMedia(MediaType.IMAGE, 'https://example.com/image.jpg');
const video = MediaFactory.createMedia(MediaType.VIDEO, 'https://example.com/video.mp4', 120);
console.log(image);
console.log(video);
```

### **Example 12: Enum with Enum Values as Parameters**

In this example, we create an enum with members that take the enum values as parameters.

```typescript
enum MathOperator {
  ADD = '+',
  SUBTRACT = '-',
  MULTIPLY = '*',
  DIVIDE = '/',
}

namespace MathCalculator {
  export function calculate(operator: MathOperator, a: number, b: number): number {
    switch (operator) {
      case MathOperator.ADD:
        return a + b;
      case MathOperator.SUBTRACT:
        return a - b;
      case MathOperator.MULTIPLY:
        return a * b;
      case MathOperator.DIVIDE:
        return a / b;
      default:
        throw new Error('Invalid operator');
    }
  }
}

// Usage
console.log(MathCalculator.calculate(MathOperator.ADD, 5, 3)); // Output: 8
console.log(MathCalculator.calculate(MathOperator.MULTIPLY, 4, 5)); // Output: 20
```

### **Example 13: Enum with Reverse Mapping**

You can create an enum with reverse mapping, allowing you to get the key by value.

```typescript
enum Fruit {
  APPLE = 1,
  ORANGE = 2,
  BANANA = 3,
}

namespace Fruit {
  export function getKeyByValue(value: number): string | undefined {
    return Object.keys(Fruit).find((key) => Fruit[key as keyof typeof Fruit] === value);
  }
}

// Usage
console.log(Fruit.getKeyByValue(2)); // Output: "ORANGE"
```

### **Example 14: Enum with String Literal Values**

You can use string literals as enum values for more explicit typing.

```typescript
type Status = 'ACTIVE' | 'INACTIVE' | 'PENDING';

const userStatus: Status = 'ACTIVE';
console.log(userStatus); // Output: "ACTIVE"
```

### **Example 15: Enum with Bit Flags**

You can create an enum with bit flags to represent multiple options.

```typescript
enum Permission {
  READ = 1 << 0,
  WRITE = 1 << 1,
  EXECUTE = 1 << 2,
}

const userPermission: Permission = Permission.READ | Permission.WRITE;

console.log(userPermission & Permission.READ); // Output: 1 (READ is set)
console.log(userPermission & Permission.EXECUTE); // Output: 0 (EXECUTE is not set)
```

Thanks for reading:)

**Some other my typescript articles:**

[15 Advanced TypeScript Tips for Development](https://lakshmananarumugam.com/15-advanced-typescript-tips-for-development)  
[Beyond Tradition: Innovating with Component-Driven Development in Typescript](https://lakshmananarumugam.com/beyond-tradition-innovating-with-component-driven-development-in-react-typescript)