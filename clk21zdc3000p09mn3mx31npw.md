---
title: "15 Advanced TypeScript Tips for Development"
seoTitle: "15 Advanced TypeScript Tips for Development"
seoDescription: "Mastering TypeScript: Tips and Tricks for Efficient and Maintainable Code"
datePublished: Fri Jul 14 2023 04:02:34 GMT+0000 (Coordinated Universal Time)
cuid: clk21zdc3000p09mn3mx31npw
slug: 15-advanced-typescript-tips-for-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689307030872/082db9a5-b75d-484e-944a-bd970e86593e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689307346755/231870b5-aeef-4d87-b588-cc68f5bd3057.png
tags: reactjs, typescript

---

**1.Optional Chaining (?.):**  
Optional chaining allows you to safely access nested properties or methods without worrying about null or undefined values. It short-circuits the evaluation if any intermediate property is null or undefined.

```css
const user = {
  name: 'John',
  address: {
    city: 'New York',
    postalCode: '12345'
  }
};


const postalCode = user.address?.postalCode;
console.log(postalCode); // Output: 12345

const invalidCode = user.address?.postalCode?.toLowerCase();
console.log(invalidCode); // Output: undefined
```

**2.Nullish Coalescing Operator (??):**  
The nullish coalescing operator provides a default value when a variable is null or undefined.

```css
const name = null;
const defaultName = name ?? 'Unknown';
console.log(defaultName); // Output: Unknown

const age = 0;
const defaultAge = age ?? 18;
console.log(defaultAge); // Output: 0
```

**3.Type Assertion:**  
Type assertion allows you to explicitly define the type of a variable when TypeScript is unable to infer it.

```css
const userInput: unknown = 'Hello World';
const strLength = (userInput as string).length;
console.log(strLength); // Output: 11
```

**4.Generics:**  
Generics enable you to create reusable components that can work with a variety of types.

```css
function reverse<T>(items: T[]): T[] {
  return items.reverse();
}

const numbers = [1, 2, 3, 4, 5];
const reversedNumbers = reverse(numbers);
console.log(reversedNumbers); // Output: [5, 4, 3, 2, 1]

const strings = ['a', 'b', 'c'];
const reversedStrings = reverse(strings);
console.log(reversedStrings); // Output: ['c', 'b', 'a']
```

**5.key of Operator:**  
The key of the operator returns a union of all known property names of a given type.

```css
interface User {
  id: number;
  name: string;
  email: string;
}

function getUserProperty(user: User, property: keyof User) {
  return user[property];
}

const user: User = {
  id: 1,
  name: 'John Doe',
  email: 'john@example.com'
};

const name = getUserProperty(user, 'name');
console.log(name); // Output: John Doe

const invalidProperty = getUserProperty(user, 'age'); // Error: Argument of type '"age"' is not assignable to parameter of type '"id" | "name" | "email"'
```

**6.Type Guards:**  
Type guards allow you to narrow down the type of a variable within a conditional block, based on a certain condition.

```css
function logMessage(message: string | number) {
  if (typeof message === 'string') {
    console.log('Message: ' + message.toUpperCase());
  } else {
    console.log('Value: ' + message.toFixed(2));
  }
}

logMessage('hello'); // Output: Message: HELLO
logMessage(3.14159); // Output: Value: 3.14
```

**7.Intersection Types:**  
Intersection types allow you to combine multiple types into a single type, creating a new type that has all the properties and methods of the intersected types.

```css
interface Loggable {
  log: () => void;
}

interface Serializable {
  serialize: () => string;
}

type Logger = Loggable & Serializable;

class ConsoleLogger implements Loggable {
  log() {
    console.log('Logging to console...');
  }
}

class FileLogger implements Loggable, Serializable {
  log() {
    console.log('Logging to file...');
  }

  serialize() {
    return 'Serialized log data';
  }
}

const logger1: Logger = new ConsoleLogger();
logger1.log(); // Output: Logging to console...

const logger2: Logger = new FileLogger();
logger2.log(); // Output: Logging to file...
console.log(logger2.serialize()); // Output: Serialized log data
```

**8.Mapped Types:**  
Mapped types allow you to create new types by transforming the properties of an existing type.

```css
interface User {
  id: number;
  name: string;
  email: string;
}

type PartialUser = { [K in keyof User]?: User[K] };

const partialUser: PartialUser = {
  name: 'John Doe',
  email: 'john@example.com'
};

console.log(partialUser); // Output: { name: 'John Doe', email: 'john@example.com' }
```

**9.String Literal Types and Union Types:**  
TypeScript supports string literal types and union types, which can be used to define specific sets of values for a variable.

```css
type HttpMethod = 'GET' | 'POST' | 'PUT' | 'DELETE';

function sendRequest(url: string, method: HttpMethod) {
  // send request logic here...
}

sendRequest('/users', 'GET');
sendRequest('/users', 'POST');
sendRequest('/users/1', 'PUT');
sendRequest('/users/1', 'DELETE');
```

**10.Decorators:**  
Decorators allow you to modify or extend the behaviour of classes, methods, properties, and other declarations.

```css
function uppercase(target: any, propertyKey: string) {
  let value = target[propertyKey];

  const getter = () => value;
  const setter = (newValue: string) => {
    value = newValue.toUpperCase();
  };

  Object.defineProperty(target, propertyKey, {
    get: getter,
    set: setter,
    enumerable: true,
    configurable: true
  });
}

class Person {
  @uppercase
  name: string;
}

const person = new Person();
person.name = 'John Doe';
console.log(person.name); // Output: JOHN DOE
```

**11.Index Signatures:**  
Index signatures allow you to define dynamic property names and their corresponding types in an interface or type.

```css
interface Dictionary {
  [key: string]: number;
}

const scores: Dictionary = {
  math: 90,
  science: 85,
  history: 95
};

console.log(scores['math']); // Output: 90
console.log(scores['english']); // Output: undefined
```

**12.Type Inference with Conditional Statements:**  
TypeScript can infer the types based on conditional statements, allowing for more concise code.

```css
function calculateTax(amount: number, isTaxable: boolean) {
  if (isTaxable) {
    return amount * 1.1; // Type: number
  } else {
    return amount; // Type: number
  }
}

const taxableAmount = calculateTax(100, true);
console.log(taxableAmount.toFixed(2)); // Output: 110.00

const nonTaxableAmount = calculateTax(100, false);
console.log(nonTaxableAmount.toFixed(2)); // Output: 100.00
```

**13.Readonly Properties:**  
TypeScript provides the read-only modifier to define properties that can't be modified after initialization.

```css
class Circle {
  readonly radius: number;

  constructor(radius: number) {
    this.radius = radius;
  }

  getArea() {
    return Math.PI * this.radius ** 2;
  }
}

const circle = new Circle(5);
console.log(circle.radius); // Output: 5

// circle.radius = 10; // Error: Cannot assign to 'radius' because it is a read-only property

console.log(circle.getArea()); // Output: 78.53981633974483
```

**14.Type Aliases:**  
Type aliases allow you to create custom names for existing types, providing more semantic meaning and improving code readability.

```css
type Point = {
  x: number;
  y: number;
};

type Shape = 'circle' | 'square' | 'triangle';

function draw(shape: Shape, position: Point) {
  console.log(`Drawing a ${shape} at (${position.x}, ${position.y})`);
}

const startPoint: Point = { x: 10, y: 20 };
draw('circle', startPoint); // Output: Drawing a circle at (10, 20)
```

**15.Type Guards with Classes:**  
Type guards can also be used with classes to narrow down the type of an object instance.

```css
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Dog extends Animal {
  bark() {
    console.log('Woof!');
  }
}

function makeSound(animal: Animal) {
  if (animal instanceof Dog) {
    animal.bark(); // Type: Dog
  } else {
    console.log('Unknown animal');
  }
}

const dog = new Dog('Buddy');
const animal = new Animal('Unknown');

makeSound(dog); // Output: Woof!
makeSound(animal); // Output: Unknown animal
```