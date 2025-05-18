# What is the use of the keyof keyword in TypeScript?
The keyof keyword creates a union of the keys in a given object type. This allows developers to reference the property names of an object as a type. This is particularly useful for type-safe access to object properties.

Example:
``` typescript
type User = {
  id: number;
  name: string;
  age: number;
};

type UserKeys = keyof User;

function getProperty(obj: User, key: UserKeys) {
  return obj[key];
}

const user: User = { id: 1, name: "Shahi", age: 25 };
const name = getProperty(user, "name");
```
In this example, keyof User creates a union type "id" | "name" | "age", making the getProperty function type-safe by ensuring only valid keys are used.

# Explain the difference between any, unknown, and never types in TypeScript.
Any allows any value to be assigned without type checking. It disables TypeScript's type checking, making it risky.
Unknown is similar to any but requires type checking before usage, providing more safety.
Never represents values that never occur, such as functions that throw errors or have infinite loops.

Example:

``` typescript

let anything: any = "hello";
let uncertain: unknown = "world";
let impossible: never;

console.log(anything.toUpperCase());

if (typeof uncertain === "string") {
  console.log(uncertain.toUpperCase());
}

function throwError(message: string): never {
  throw new Error(message);
} 
```
Using unknown instead of any enforces safer code practices by requiring explicit checks before usage.