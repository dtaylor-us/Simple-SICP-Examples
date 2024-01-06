# TypeScript Examples

TypeScript is a superset of JavaScript that brings static type definitions to the language, enhancing its capabilities for both object-oriented and functional programming. It's well-suited for demonstrating SICP concepts, as it blends JavaScript's functional nature with the structure and type safety more commonly associated with OOP languages. Here are TypeScript examples that illustrate each of the SICP concepts.

### 1. Abstraction

TypeScript allows for abstraction through interfaces, classes, and functions, enabling the creation of generic and reusable code structures.

```typescript
interface Shape {
    area(): number;
    perimeter(): number;
}

class Circle implements Shape {
    constructor(private radius: number) {}

    area(): number {
        return Math.PI * this.radius * this.radius;
    }

    perimeter(): number {
        return 2 * Math.PI * this.radius;
    }
}
```

### 2. Recursive Thinking

Recursion is a natural concept in TypeScript, just as it is in JavaScript. A typical example is the recursive calculation of a factorial.

```typescript
function factorial(n: number): number {
    if (n === 0) return 1;
    return n * factorial(n - 1);
}

console.log(factorial(5)); // Output: 120
```

### 3. Procedural and Data Abstraction

TypeScript supports the separation of data and procedures. Classes can be used to encapsulate data along with methods that operate on that data.

```typescript
class BankAccount {
    constructor(private balance: number) {}

    deposit(amount: number): void {
        this.balance += amount;
    }

    withdraw(amount: number): void {
        this.balance -= amount;
    }

    getBalance(): number {
        return this.balance;
    }
}
```

### 4. Functional Programming

TypeScript supports functional programming paradigms, such as higher-order functions, immutability, and lambda expressions.

```typescript
const square = (x: number): number => x * x;

console.log(square(5)); // Output: 25
```

### 5. Metalinguistic Abstraction

Metalinguistic abstraction in TypeScript can be demonstrated through its powerful type system and generics, which can be used to create flexible and reusable code patterns.

```typescript
type Expr = number | [Expr, string, Expr];

function evaluate(expr: Expr): number {
    if (typeof expr === 'number') {
        return expr;
    } else {
        const [left, operator, right] = expr;
        switch (operator) {
            case '+': return evaluate(left) + evaluate(right);
            case '-': return evaluate(left) - evaluate(right);
            // Add other operators as needed
        }
    }
}

console.log(evaluate([5, '+', [2, '-', 3]])); // Output: 4
```

### 6. Modularity, Objects, and State

TypeScript's class system and modules promote modularity and encapsulation, aligning well with OOP principles while also supporting functional approaches.

```typescript
class Counter {
    private count = 0;

    increment(): void {
        this.count++;
    }

    getCount(): number {
        return this.count;
    }
}

const counter = new Counter();
counter.increment();
console.log(counter.getCount()); // Output: 1
```

### 7. Concurrency and Lazy Evaluation

TypeScript leverages JavaScript's event-driven model and Promises for handling concurrency. Lazy evaluation can be achieved through functions or getters.

```typescript
const lazyValue = (): number => {
    console.log("Computed");
    return Math.random();
}

let value: number;
console.log("Value not computed yet");
value = lazyValue(); // Computation happens here
console.log("Computed value: " + value);
```

### 8. Symbolic Computing

While symbolic computing is less common in TypeScript, it can be represented using classes and interfaces to manipulate abstract symbols and expressions.

```typescript
interface SymbolicExpr {
    simplify(): SymbolicExpr;
}

class SymbolicConstant implements SymbolicExpr {
    constructor(private value: number) {}

    simplify(): SymbolicExpr {
        return this;
    }
}

const expr = new SymbolicConstant(5);
console.log(expr.simplify()); // Output: SymbolicConstant { value: 5 }
```

Each TypeScript example demonstrates a concept from SICP, adapted to a language that combines the flexibility of JavaScript with the robustness of static typing. TypeScript's capabilities make it an ideal choice for exploring these concepts in a modern web development context.