# 🚀 DAY 1 — TypeScript Foundation (Think Like a Pro)

## 🧠 1. What is TypeScript? (Simple Truth)

👉 TypeScript = **JavaScript + Types**

It helps you catch errors **before running the code**.

### Example (JavaScript ❌)

```js
function add(a, b) {
  return a + b;
}

add(5, "hello"); // 😬 No error, but wrong output
```

### Same in TypeScript ✅

```ts
function add(a: number, b: number) {
  return a + b;
}

add(5, "hello"); // ❌ Error BEFORE running
```

👉 This is called:

> **Static Type Checking**

---

## ⚠️ Why JavaScript Alone is Not Enough

Since you already know JS, understand this deeply:

### Problems in JS:

* No type safety
* Bugs found at runtime (too late)
* Hard to scale large apps
* Poor developer experience

👉 TypeScript fixes all of these.

---

## ⚙️ 2. How TypeScript Works (VERY IMPORTANT)

👉 TypeScript does NOT run in browser/node directly.

Flow:

```
TypeScript (.ts)
   ↓ (compile)
JavaScript (.js)
   ↓
Runs in browser / Node
```

👉 Tool used:

```
tsc (TypeScript Compiler)
```

---

## 🛠️ 3. Setup TypeScript (DO THIS NOW)

### Step 1:

```bash
npm install -g typescript
```

### Step 2:

```bash
tsc --init
```

👉 This creates:

```
tsconfig.json
```

---

## 📄 4. tsconfig.json (Your Control Panel)

You don’t need everything. Just understand THIS:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "strict": true
  }
}
```

### 🔥 Important:

* `target` → JS version output
* `strict` → makes TS powerful (ALWAYS keep true)

---

## ▶️ 5. Your First TypeScript Program

Create file: `index.ts`

```ts
let message: string = "Hello Ayush";
console.log(message);
```

### Compile:

```bash
tsc index.ts
```

👉 It creates:

```
index.js
```

### Run:

```bash
node index.js
```

---

## 🧠 6. Key Concept (Most Important Today)

👉 TypeScript checks **at compile time, not runtime**

| Stage         | Happens when    |
| ------------- | --------------- |
| Type Checking | Before running  |
| Execution     | After compiling |

---

## 🔥 7. Strict Mode (VERY IMPORTANT)

```json
"strict": true
```

👉 Enables:

* strict types
* no implicit any
* safer code

💡 Interview tip:

> “I always enable strict mode because it prevents hidden bugs.”

---

## 🧪 8. Mini Practice (DO THIS)

Create this file:

```ts
let age: number = 20;
let name: string = "Ayush";

function greet(name: string): string {
  return "Hello " + name;
}

console.log(greet(name));
```

👉 Now try breaking it:

```ts
greet(10); // ❌ Should error
```

---

## 🎯 End Goal of Day 1

By now you should:

* Understand WHY TypeScript exists
* Know how TS → JS works
* Be able to compile and run TS code
* Know what `tsconfig` and `strict` do

---



Perfect. Now we enter **real TypeScript territory** — this is where most beginners get confused and interviewers start testing.

---

# 🚀 DAY 2 — Type System Deep Dive (CRITICAL)

👉 Today’s goal:
You should **understand types like a pro**, not just memorize them.

---

# 🧠 1. Basic Types (Quick Recap)

```ts
let age: number = 21;
let name: string = "Ayush";
let isLoggedIn: boolean = true;
```

Simple — but don’t underestimate:
👉 These are the building blocks of everything.

---

# ⚠️ 2. `any` (THE MOST DANGEROUS TYPE)

```ts
let value: any = 10;
value = "hello";
value = true;
```

👉 TypeScript basically says:

> “Do whatever you want, I won’t check.”

### ❌ Problem:

```ts
value.toUpperCase(); // 💥 runtime crash if value is number
```

---

## 🔥 Interview Insight:

> “`any` disables TypeScript completely. It should be avoided unless absolutely necessary.”

---

# 🧠 3. `unknown` (SMART VERSION OF `any`)

```ts
let value: unknown = "hello";
```

👉 You CANNOT directly use it:

```ts
value.toUpperCase(); // ❌ Error
```

### ✅ You must check first:

```ts
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

---

## 🔥 Key Difference

| Feature             | any ❌ | unknown ✅ |
| ------------------- | ----- | --------- |
| Safety              | No    | Yes       |
| Type check required | No    | Yes       |

👉 Golden rule:

> Use `unknown` instead of `any`

---

# 🧠 4. `void` (FUNCTION RETURNS NOTHING)

```ts
function logMessage(msg: string): void {
  console.log(msg);
}
```

👉 Means:

> “This function doesn’t return anything”

---

# 🧠 5. `null` and `undefined`

```ts
let a: null = null;
let b: undefined = undefined;
```

👉 In strict mode:
You must explicitly allow them.

```ts
let name: string | null = null;
```

---

# 💀 6. `never` (VERY IMPORTANT 🔥)

👉 Represents:

> “This will NEVER happen”

### Example 1: Infinite loop

```ts
function infiniteLoop(): never {
  while (true) {}
}
```

### Example 2: Error throwing

```ts
function throwError(msg: string): never {
  throw new Error(msg);
}
```

---

## 🔥 Interview Insight:

Difference between `void` vs `never`

| Type  | Meaning              |
| ----- | -------------------- |
| void  | returns nothing      |
| never | never returns at all |

---

# 🧠 7. Type Inference (SUPER IMPORTANT)

👉 TypeScript is smart:

```ts
let x = 10; // TS automatically: number
```

You don’t always need to write types.

---

## ⚠️ BUT:

```ts
let x; // ❌ becomes 'any'
```

👉 Always initialize variables!

---

# 🧪 8. Real Practice (DO THIS NOW)

```ts
let data: unknown = "Ayush";

if (typeof data === "string") {
  console.log(data.toUpperCase());
}
```

---

### Try breaking:

```ts
let data: any = 10;
console.log(data.toUpperCase()); // 💥 runtime error
```

👉 THIS is why `any` is dangerous.

---

# 🧠 9. Small Mental Model (IMPORTANT)

When writing TypeScript, always think:

👉 “Can this value change type?”

* YES → use `unknown`
* NO → use strict type (`string`, `number`, etc.)
* NOT SURE → avoid `any`

---

# 🎯 End Goal of Day 2

You should now:

* Understand `any vs unknown` deeply
* Know `void`, `never`, `null`, `undefined`
* Understand type safety vs flexibility
* Start thinking like TypeScript

---

Perfect — now we move to **Day 3**, and this is where TypeScript starts becoming **practical + interview-relevant**.

---

# 🚀 DAY 3 — Functions + Type Inference (VERY IMPORTANT)

👉 Today’s focus:

* Writing functions properly in TS
* Understanding **how TS “thinks” automatically**

---

# 🧠 1. Function Basics in TypeScript

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

### Breakdown:

* `a: number` → parameter type
* `: number` → return type

---

## ⚠️ If you don’t define types:

```ts
function add(a, b) {
  return a + b;
}
```

👉 In strict mode:
❌ Error → because params become `any`

---

# 🧠 2. Return Type — Do You Always Need It?

👉 Not always.

```ts
function add(a: number, b: number) {
  return a + b;
}
```

👉 TS automatically infers:

> return type = `number`

---

## 🔥 Interview Insight:

> “I rely on inference for simple functions, but explicitly define return types in complex logic for clarity.”

---

# 🧠 3. Optional Parameters (`?`)

```ts
function greet(name: string, age?: number) {
  return age ? `${name} is ${age}` : `Hello ${name}`;
}
```

👉 `age` may or may not exist

---

## ⚠️ Rule:

Optional parameters must be **at the end**

❌ Wrong:

```ts
function test(a?: number, b: number) {}
```

---

# 🧠 4. Default Parameters

```ts
function greet(name: string, age: number = 18) {
  return `${name} is ${age}`;
}
```

👉 If no value → uses default

---

# 🧠 5. Function Type (IMPORTANT 🔥)

You can define function types separately:

```ts
type AddFunction = (a: number, b: number) => number;

const add: AddFunction = (a, b) => a + b;
```

---

## 🔥 Why important?

Used in:

* Callbacks
* React props
* APIs

---

# 🧠 6. Arrow Functions in TypeScript

```ts
const multiply = (a: number, b: number): number => {
  return a * b;
};
```

👉 Same as normal functions, just syntax change

---

# 🧠 7. Type Inference (THE GAME CHANGER)

👉 TypeScript is smart:

```ts
const x = 10; // inferred as number
const name = "Ayush"; // inferred as string
```

---

## 🔥 In functions:

```ts
const greet = (name: string) => {
  return "Hello " + name;
};
```

👉 TS infers return type = `string`

---

# ⚠️ Dangerous Case

```ts
let x;
x = 10;
x = "hello";
```

👉 Type becomes `any` ❌

---

# 🧠 8. Callback Functions (VERY IMPORTANT)

```ts
function processUser(callback: (name: string) => void) {
  callback("Ayush");
}
```

Usage:

```ts
processUser((name) => {
  console.log(name);
});
```

---

## 🔥 Real-world use:

* Event handlers
* API calls
* React props

---

# 🧪 9. Practice (DO THIS)

### Task 1:

```ts
function calculate(a: number, b: number, op: string): number {
  if (op === "add") return a + b;
  if (op === "sub") return a - b;
  return 0;
}
```

---

### Task 2 (Callback):

```ts
function greetUser(callback: (msg: string) => void) {
  callback("Hello Ayush");
}
```

---

# 🧠 10. Real Thinking Shift (IMPORTANT)

When writing functions, always think:

👉 What goes in? → parameter types
👉 What comes out? → return type

---

# 🎯 End Goal of Day 3

You should now:

* Write fully typed functions
* Understand optional/default params
* Use function types
* Understand inference deeply

---

Great — now we hit **Day 4**, and this is where things start becoming **real-world useful (React + Backend + APIs)**.

Take this seriously — this topic is asked in **almost every interview**.

---

# 🚀 DAY 4 — Objects + `type` vs `interface` (🔥 VERY IMPORTANT)

---

# 🧠 1. Why We Need Object Types

In JS:

```js
const user = {
  name: "Ayush",
  age: 21
};
```

👉 No safety. You can mess it up anytime.

---

## ✅ In TypeScript:

```ts
const user: { name: string; age: number } = {
  name: "Ayush",
  age: 21
};
```

👉 Now TypeScript protects you.

---

# 🧠 2. Cleaner Way — Type Alias

```ts
type User = {
  name: string;
  age: number;
};
```

Use it:

```ts
const user: User = {
  name: "Ayush",
  age: 21
};
```

---

# 🧠 3. Interface (Same Purpose… but different behavior)

```ts
interface User {
  name: string;
  age: number;
}
```

Use it the same way:

```ts
const user: User = {
  name: "Ayush",
  age: 21
};
```

---

# ⚔️ 4. `type` vs `interface` (INTERVIEW FAVORITE 🔥)

## 🟢 Similarities:

* Both define object shapes
* Both are used everywhere

---

## 🔴 Differences:

### 1. Extension

👉 Interface:

```ts
interface User {
  name: string;
}

interface Admin extends User {
  role: string;
}
```

👉 Type:

```ts
type User = {
  name: string;
};

type Admin = User & {
  role: string;
};
```

---

### 2. Flexibility

👉 Type can do more:

```ts
type Status = "success" | "error"; // union
```

👉 Interface cannot do this ❌

---

### 3. Declaration Merging (🔥 tricky concept)

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}
```

👉 Automatically becomes:

```ts
{
  name: string;
  age: number;
}
```

👉 Type DOES NOT allow this ❌

---

# 🧠 5. When to Use What (IMPORTANT)

👉 My recommendation (and industry trend):

* Use `interface` → for objects (especially React props)
* Use `type` → for everything else (unions, complex types)

---

## 🔥 Interview Answer (MEMORIZE THIS)

> “I prefer `interface` for object structures due to extendability and readability, and `type` when I need unions or advanced compositions.”

---

# 🧠 6. Optional Properties

```ts
type User = {
  name: string;
  age?: number;
};
```

👉 `age` is optional

---

# 🧠 7. Readonly Properties

```ts
type User = {
  readonly id: number;
  name: string;
};
```

```ts
user.id = 5; // ❌ Error
```

---

# 🧠 8. Nested Objects (REAL WORLD)

```ts
type User = {
  name: string;
  address: {
    city: string;
    pincode: number;
  };
};
```

---

# 🧠 9. Using in Functions

```ts
type User = {
  name: string;
  age: number;
};

function greet(user: User): string {
  return `Hello ${user.name}`;
}
```

---

# 🧪 10. Practice (DO THIS)

### Task 1:

```ts
type Product = {
  id: number;
  name: string;
  price: number;
};
```

---

### Task 2:

```ts
interface Order {
  product: string;
  quantity: number;
}
```

---

### Task 3 (Important):

Create:

* one extended interface
* one intersection type

---

# 💥 Real World Connection (IMPORTANT FOR YOU)

👉 This is used in:

* React props
* API responses
* Database models
* Backend DTOs

---

# 🧠 Final Mental Model

👉 Think:

> “I am defining the SHAPE of data”

---

# 🎯 End Goal of Day 4

You should:

* Define objects properly
* Understand `type vs interface`
* Know when to use each
* Handle nested + optional data

---


Great — now we hit **Day 4**, and this is where things start becoming **real-world useful (React + Backend + APIs)**.

Take this seriously — this topic is asked in **almost every interview**.

---

# 🚀 DAY 4 — Objects + `type` vs `interface` (🔥 VERY IMPORTANT)

---

# 🧠 1. Why We Need Object Types

In JS:

```js
const user = {
  name: "Ayush",
  age: 21
};
```

👉 No safety. You can mess it up anytime.

---

## ✅ In TypeScript:

```ts
const user: { name: string; age: number } = {
  name: "Ayush",
  age: 21
};
```

👉 Now TypeScript protects you.

---

# 🧠 2. Cleaner Way — Type Alias

```ts
type User = {
  name: string;
  age: number;
};
```

Use it:

```ts
const user: User = {
  name: "Ayush",
  age: 21
};
```

---

# 🧠 3. Interface (Same Purpose… but different behavior)

```ts
interface User {
  name: string;
  age: number;
}
```

Use it the same way:

```ts
const user: User = {
  name: "Ayush",
  age: 21
};
```

---

# ⚔️ 4. `type` vs `interface` (INTERVIEW FAVORITE 🔥)

## 🟢 Similarities:

* Both define object shapes
* Both are used everywhere

---

## 🔴 Differences:

### 1. Extension

👉 Interface:

```ts
interface User {
  name: string;
}

interface Admin extends User {
  role: string;
}
```

👉 Type:

```ts
type User = {
  name: string;
};

type Admin = User & {
  role: string;
};
```

---

### 2. Flexibility

👉 Type can do more:

```ts
type Status = "success" | "error"; // union
```

👉 Interface cannot do this ❌

---

### 3. Declaration Merging (🔥 tricky concept)

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}
```

👉 Automatically becomes:

```ts
{
  name: string;
  age: number;
}
```

👉 Type DOES NOT allow this ❌

---

# 🧠 5. When to Use What (IMPORTANT)

👉 My recommendation (and industry trend):

* Use `interface` → for objects (especially React props)
* Use `type` → for everything else (unions, complex types)

---

## 🔥 Interview Answer (MEMORIZE THIS)

> “I prefer `interface` for object structures due to extendability and readability, and `type` when I need unions or advanced compositions.”

---

# 🧠 6. Optional Properties

```ts
type User = {
  name: string;
  age?: number;
};
```

👉 `age` is optional

---

# 🧠 7. Readonly Properties

```ts
type User = {
  readonly id: number;
  name: string;
};
```

```ts
user.id = 5; // ❌ Error
```

---

# 🧠 8. Nested Objects (REAL WORLD)

```ts
type User = {
  name: string;
  address: {
    city: string;
    pincode: number;
  };
};
```

---

# 🧠 9. Using in Functions

```ts
type User = {
  name: string;
  age: number;
};

function greet(user: User): string {
  return `Hello ${user.name}`;
}
```

---

# 🧪 10. Practice (DO THIS)

### Task 1:

```ts
type Product = {
  id: number;
  name: string;
  price: number;
};
```

---

### Task 2:

```ts
interface Order {
  product: string;
  quantity: number;
}
```

---

### Task 3 (Important):

Create:

* one extended interface
* one intersection type

---

# 💥 Real World Connection (IMPORTANT FOR YOU)

👉 This is used in:

* React props
* API responses
* Database models
* Backend DTOs

---

# 🧠 Final Mental Model

👉 Think:

> “I am defining the SHAPE of data”

---

# 🎯 End Goal of Day 4

You should:

* Define objects properly
* Understand `type vs interface`
* Know when to use each
* Handle nested + optional data

---

Perfect — now we enter one of the **MOST IMPORTANT topics in TypeScript**.

If you master this → you’ll start thinking like a **senior dev**.

---

# 🚀 DAY 6 — Union (`|`) & Intersection (`&`) Types

---

# 🧠 1. Union Types (`|`) — “OR”

👉 Means:

> Value can be **one of multiple types**

---

## ✅ Example:

```ts
let id: string | number;

id = 101;      // ✅
id = "A101";   // ✅
id = true;     // ❌
```

---

## 🧠 Real-Life Thinking

👉 Like saying:

> “ID can be number OR string”

---

# 🧠 2. Problem with Union (IMPORTANT)

```ts
function printId(id: string | number) {
  console.log(id.toUpperCase()); // ❌ Error
}
```

👉 Why error?

Because:

* number doesn’t have `toUpperCase()`

---

# 🔥 Solution → Narrowing (Preview of Day 7)

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // ✅
  }
}
```

---

# 🧠 3. Union with Objects (VERY IMPORTANT)

```ts
type User = {
  name: string;
};

type Admin = {
  role: string;
};

let person: User | Admin;
```

---

## ⚠️ Problem:

```ts
person.name; // ❌ Not safe
```

👉 Because TS doesn’t know which type it is

---

# 🧠 4. Discriminated Union (🔥 ADVANCED + INTERVIEW FAVORITE)

```ts
type User = {
  type: "user";
  name: string;
};

type Admin = {
  type: "admin";
  role: string;
};

function handle(person: User | Admin) {
  if (person.type === "user") {
    console.log(person.name);
  } else {
    console.log(person.role);
  }
}
```

👉 This is used in:

* APIs
* Redux
* complex apps

---

# 🧠 5. Intersection Types (`&`) — “AND”

👉 Means:

> Combine multiple types into one

---

## ✅ Example:

```ts
type User = {
  name: string;
};

type Admin = {
  role: string;
};

type AdminUser = User & Admin;
```

---

## Use:

```ts
let person: AdminUser = {
  name: "Ayush",
  role: "admin"
};
```

---

## 🧠 Real Thinking

👉 “This object must have ALL properties”

---

# ⚠️ 6. Conflict Case

```ts
type A = { name: string };
type B = { name: number };

type C = A & B; // ❌ impossible
```

👉 TS will break because:

* name cannot be both string AND number

---

# 🧠 7. Union vs Intersection (CRYSTAL CLEAR)

| Feature | Union (`|`) | Intersection (`&`) |
|--------|------------|-------------------|
| Meaning | OR | AND |
| Data | one type | combined type |
| Use case | flexible input | strict combined object |

---

# 🧪 8. Practice (DO THIS)

### Task 1:

```ts
let value: string | number;
```

---

### Task 2:

```ts
type A = { name: string };
type B = { age: number };

type C = A & B;
```

---

### Task 3 (IMPORTANT):

Create:

* `Student`
* `Teacher`

Then:

* union → person can be either
* intersection → person is both

---

# 💥 Real World Connection (FOR YOU)

👉 React:

```ts
type ButtonProps = {
  variant: "primary" | "secondary";
};
```

---

👉 API:

```ts
type Response = "success" | "error";
```

---

👉 Backend:

```ts
type UserWithToken = User & {
  token: string;
};
```

---

# 🧠 Final Mental Model

👉 Always ask:

* “Is it ONE of many?” → `|`
* “Does it NEED ALL?” → `&`

---

# 🎯 End Goal of Day 6

You should:

* Understand union deeply
* Understand intersection deeply
* Handle object unions
* Know real-world usage

---



Perfect — now we enter one of the **MOST IMPORTANT topics in TypeScript**.

If you master this → you’ll start thinking like a **senior dev**.

---

# 🚀 DAY 6 — Union (`|`) & Intersection (`&`) Types

---

# 🧠 1. Union Types (`|`) — “OR”

👉 Means:

> Value can be **one of multiple types**

---

## ✅ Example:

```ts
let id: string | number;

id = 101;      // ✅
id = "A101";   // ✅
id = true;     // ❌
```

---

## 🧠 Real-Life Thinking

👉 Like saying:

> “ID can be number OR string”

---

# 🧠 2. Problem with Union (IMPORTANT)

```ts
function printId(id: string | number) {
  console.log(id.toUpperCase()); // ❌ Error
}
```

👉 Why error?

Because:

* number doesn’t have `toUpperCase()`

---

# 🔥 Solution → Narrowing (Preview of Day 7)

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // ✅
  }
}
```

---

# 🧠 3. Union with Objects (VERY IMPORTANT)

```ts
type User = {
  name: string;
};

type Admin = {
  role: string;
};

let person: User | Admin;
```

---

## ⚠️ Problem:

```ts
person.name; // ❌ Not safe
```

👉 Because TS doesn’t know which type it is

---

# 🧠 4. Discriminated Union (🔥 ADVANCED + INTERVIEW FAVORITE)

```ts
type User = {
  type: "user";
  name: string;
};

type Admin = {
  type: "admin";
  role: string;
};

function handle(person: User | Admin) {
  if (person.type === "user") {
    console.log(person.name);
  } else {
    console.log(person.role);
  }
}
```

👉 This is used in:

* APIs
* Redux
* complex apps

---

# 🧠 5. Intersection Types (`&`) — “AND”

👉 Means:

> Combine multiple types into one

---

## ✅ Example:

```ts
type User = {
  name: string;
};

type Admin = {
  role: string;
};

type AdminUser = User & Admin;
```

---

## Use:

```ts
let person: AdminUser = {
  name: "Ayush",
  role: "admin"
};
```

---

## 🧠 Real Thinking

👉 “This object must have ALL properties”

---

# ⚠️ 6. Conflict Case

```ts
type A = { name: string };
type B = { name: number };

type C = A & B; // ❌ impossible
```

👉 TS will break because:

* name cannot be both string AND number

---

# 🧠 7. Union vs Intersection (CRYSTAL CLEAR)

| Feature | Union (`|`) | Intersection (`&`) |
|--------|------------|-------------------|
| Meaning | OR | AND |
| Data | one type | combined type |
| Use case | flexible input | strict combined object |

---

# 🧪 8. Practice (DO THIS)

### Task 1:

```ts
let value: string | number;
```

---

### Task 2:

```ts
type A = { name: string };
type B = { age: number };

type C = A & B;
```

---

### Task 3 (IMPORTANT):

Create:

* `Student`
* `Teacher`

Then:

* union → person can be either
* intersection → person is both

---

# 💥 Real World Connection (FOR YOU)

👉 React:

```ts
type ButtonProps = {
  variant: "primary" | "secondary";
};
```

---

👉 API:

```ts
type Response = "success" | "error";
```

---

👉 Backend:

```ts
type UserWithToken = User & {
  token: string;
};
```

---

# 🧠 Final Mental Model

👉 Always ask:

* “Is it ONE of many?” → `|`
* “Does it NEED ALL?” → `&`

---

# 🎯 End Goal of Day 6

You should:

* Understand union deeply
* Understand intersection deeply
* Handle object unions
* Know real-world usage

---



# 🚀 DAY 7 — Generics (MOST POWERFUL FEATURE)

---

# 🧠 1. Problem First (Why Generics Exist)

### ❌ Without Generics:

```ts
function identity(value: any): any {
  return value;
}
```

👉 Problem:

* You lose type safety
* TS becomes useless again

---

## ⚠️ Example:

```ts
let result = identity("Ayush");
result.toUpperCase(); // ❓ TS doesn't know it's string
```

---

# 🧠 2. Solution — GENERICS

👉 Generics = **Type as a variable**

```ts
function identity<T>(value: T): T {
  return value;
}
```

---

## ✅ Now:

```ts
let result = identity("Ayush");
result.toUpperCase(); // ✅ TS knows it's string
```

---

## 🔥 What is `<T>`?

👉 It’s a placeholder for a type

You can think:

> “I don’t know the type yet, but I’ll figure it out later”

---

# 🧠 3. Real-Life Analogy

👉 Think of a box:

* Normal function → fixed box (only apples)
* Generic → flexible box (apple, banana, anything)

---

# 🧠 4. Multiple Generics

```ts
function pair<T, U>(a: T, b: U): [T, U] {
  return [a, b];
}
```

Use:

```ts
pair<string, number>("Ayush", 21);
```

---

# 🧠 5. Generics with Arrays

```ts
function getFirst<T>(arr: T[]): T {
  return arr[0];
}
```

---

## Use:

```ts
getFirst([1, 2, 3]);        // number
getFirst(["a", "b"]);       // string
```

---

# 🧠 6. Generics with Type Alias

```ts
type ApiResponse<T> = {
  data: T;
  success: boolean;
};
```

---

## Use:

```ts
type User = { name: string };

let res: ApiResponse<User> = {
  data: { name: "Ayush" },
  success: true
};
```

---

## 🔥 Real-world usage:

👉 This is EXACTLY how APIs are typed

---

# 🧠 7. Generics with Interfaces

```ts
interface Box<T> {
  value: T;
}
```

---

# 🧠 8. Constraints (🔥 VERY IMPORTANT)

👉 Restrict what T can be

```ts
function getLength<T extends { length: number }>(item: T) {
  return item.length;
}
```

---

## Use:

```ts
getLength("hello"); // ✅
getLength([1, 2]);  // ✅
getLength(10);      // ❌ no length
```

---

# 🧠 9. `keyof` with Generics (🔥🔥🔥 INTERVIEW FAVORITE)

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}
```

---

## Use:

```ts
const user = { name: "Ayush", age: 21 };

getProperty(user, "name"); // ✅
getProperty(user, "email"); // ❌
```

---

# 💥 WHY THIS IS POWERFUL

👉 Prevents accessing wrong keys
👉 Used heavily in:

* React
* APIs
* Libraries

---

# 🧪 10. Practice (DO THIS)

### Task 1:

```ts
function identity<T>(value: T): T {
  return value;
}
```

---

### Task 2:

```ts
function getLast<T>(arr: T[]): T {
  return arr[arr.length - 1];
}
```

---

### Task 3 (IMPORTANT):

```ts
type Response<T> = {
  data: T;
  error: string | null;
};
```

---

# 💥 Real World (FOR YOU)

👉 React:

```ts
const [data, setData] = useState<User | null>(null);
```

---

👉 Backend:

```ts
type ApiResponse<T> = {
  data: T;
  status: number;
};
```

---

# 🧠 Final Mental Model

👉 Generics =

> “Write once, use for any type safely”

---

# 🎯 End Goal of Day 7

You should:

* Understand why `any` is bad → generics fix it
* Use generic functions
* Use generic types
* Understand constraints + keyof

---


---

# 🚀 DAY 8 — Utility Types (🔥 INTERVIEW GOLD)

---

# 🧠 First — Why Utility Types Exist?

👉 Problem:

```ts
type User = {
  name: string;
  age: number;
  email: string;
};
```

Now imagine:

* Sometimes you need only `name`
* Sometimes partial update
* Sometimes remove fields

👉 Without utility types → repetitive code 😵

---

# 🧠 Solution:

👉 TypeScript gives **built-in helpers** = Utility Types

---

# 🔥 1. `Partial<T>` — Make Everything Optional

```ts
type User = {
  name: string;
  age: number;
};
```

```ts
type PartialUser = Partial<User>;
```

👉 Becomes:

```ts
{
  name?: string;
  age?: number;
}
```

---

## ✅ Real Use Case:

```ts
function updateUser(user: Partial<User>) {
  // update only some fields
}
```

---

# 🔥 2. `Required<T>` — Make Everything Mandatory

```ts
type User = {
  name?: string;
  age?: number;
};
```

```ts
type FullUser = Required<User>;
```

👉 Now all fields are required

---

# 🔥 3. `Pick<T, K>` — Select Specific Fields

```ts
type User = {
  name: string;
  age: number;
  email: string;
};
```

```ts
type UserPreview = Pick<User, "name" | "email">;
```

👉 Result:

```ts
{
  name: string;
  email: string;
}
```

---

## 🧠 Real Use:

👉 API response optimization

---

# 🔥 4. `Omit<T, K>` — Remove Fields

```ts
type UserWithoutEmail = Omit<User, "email">;
```

👉 Result:

```ts
{
  name: string;
  age: number;
}
```

---

# 🔥 5. `Record<K, T>` — Create Object Type

```ts
type Roles = "admin" | "user";

type RolePermissions = Record<Roles, string[]>;
```

👉 Result:

```ts
{
  admin: string[];
  user: string[];
}
```

---

## 🧠 Real Use:

```ts
const permissions: RolePermissions = {
  admin: ["read", "write"],
  user: ["read"]
};
```

---

# 🔥 6. `Readonly<T>` — Immutable Object

```ts
type User = {
  name: string;
};
```

```ts
type ReadonlyUser = Readonly<User>;
```

```ts
user.name = "Rahul"; // ❌ Error
```

---

# ⚡ Quick Summary Table

| Utility  | Purpose       |
| -------- | ------------- |
| Partial  | optional      |
| Required | mandatory     |
| Pick     | select fields |
| Omit     | remove fields |
| Record   | create object |
| Readonly | immutable     |

---

# 🧪 Practice (DO THIS)

### Task 1:

```ts
type Product = {
  id: number;
  name: string;
  price: number;
};
```

👉 Create:

* Partial<Product>
* Pick name only
* Omit price

---

### Task 2:

```ts
type Roles = "admin" | "user";
```

👉 Create:

* Record for permissions

---

# 💥 Real World (FOR YOU)

👉 Backend API:

```ts
type ApiResponse<T> = {
  data: T;
  error?: string;
};
```

---

👉 React form update:

```ts
function updateForm(data: Partial<FormData>) {}
```

---

# 🔥 Interview Answer (IMPORTANT)

> “Utility types help avoid repetition and make types reusable and maintainable.”

---

# 🧠 Final Mental Model

👉 Instead of writing new types every time:

> “Transform existing types smartly”

---

# 🎯 End Goal of Day 8

You should:

* Use all major utility types
* Understand when to use each
* Write cleaner types

---



