# Understanding Union and Intersection Types in TypeScript

TypeScript provides powerful tools to compose types — two of the most common are **union** (`|`) and **intersection** (`&`) types. Let’s explore what they do and how to use them with real-world examples.

---

## Union Types (`|`)

A **union type** allows a variable to be **one of several types**. This is great when a value might come in different forms.

### Example: Handling API Response

```ts
type Success = {
  status: "success";
  data: string;
};

type Error = {
  status: "error";
  message: string;
};

type ApiResponse = Success | Error;

function handleResponse(res: ApiResponse) {
  if (res.status === "success") {
    console.log("Data:", res.data);
  } else {
    console.error(" Error:", res.message);
  }
}
```

## Intersection Types (`&`)

An **intersection type** in TypeScript lets you combine multiple types into a single one. The resulting type has **all the properties** of the types being combined.

### What It Means

Think of it as saying:  
**“This value must satisfy both Type A and Type B.”**

---

### Example: Admin User

```ts
type User = {
  name: string;
  email: string;
};

type Admin = {
  role: "admin";
  permissions: string[];
};

// Intersection type: must include all properties from both User and Admin
type AdminUser = User & Admin;

const admin: AdminUser = {
  name: "Alice",
  email: "alice@example.com",
  role: "admin",
  permissions: ["read", "write", "delete"],
};
```

### 🛠 When to Use

Use intersection types when:

You want to combine features or traits.

An object must fulfill multiple roles or categories.

You’re extending multiple reusable types.

# What is Type Inference in TypeScript? And Why It Matters

TypeScript is well known for its static typing — but did you know you don’t always have to explicitly write types? That’s where **type inference** comes in.

---

## What is Type Inference?

**Type inference** is the process where TypeScript automatically determines the type of a variable, parameter, or return value **based on its initial value or usage** — without you explicitly specifying it.

### Example:

```ts
let name = "Alice"; // TypeScript infers: string
let count = 42; // TypeScript infers: number

function greet(user: string) {
  return `Hello, ${user}`;
}

const message = greet("Bob"); // TypeScript infers: string
```

### Why is Type Inference Helpful?

- **Less Code, Same Safety**  
  You write fewer type annotations but still get the benefits of type checking.

- **Improved Readability**  
  Cleaner and more concise code makes it easier to maintain and understand.

- **Smart Autocompletion**  
  TypeScript knows the types, so editors like VSCode can offer intelligent suggestions and documentation.

- **Faster Development**  
  TypeScript catches mistakes early — even when types aren’t explicitly written.

**TypeScript’s type inference makes your code smart, safe, and clean — helping you enjoy the benefits of types without the overhead of writing them everywhere.**
