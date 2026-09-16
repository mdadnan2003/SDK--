# TypeScript Master SDK

> Complete reusable TypeScript reference for frontend, React, Next.js, Node.js, APIs, backend and full-stack development.

---

# 1. TypeScript Setup

Install TypeScript:

```bash
npm install -D typescript
```

Check version:

```bash
npx tsc --version
```

Create config:

```bash
npx tsc --init
```

Compile:

```bash
npx tsc
```

Compile specific file:

```bash
npx tsc app.ts
```

Watch mode:

```bash
npx tsc --watch
```

---

# 2. Basic TypeScript

JavaScript:

```javascript
let name = "Adnan";
```

TypeScript:

```typescript
let name: string = "Adnan";
```

---

# 3. Basic Types

```typescript
let name: string = "Adnan";

let age: number = 22;

let active: boolean = true;

let value: null = null;

let data: undefined = undefined;
```

---

# 4. Type Inference

TypeScript automatically understands:

```typescript
let name = "Adnan";
```

TypeScript infers:

```text
string
```

Example:

```typescript
let age = 22;
```

Inferred:

```text
number
```

You don't always need to explicitly write types.

---

# 5. String

```typescript
let name: string = "Adnan";
```

Template literal:

```typescript
let message = `Hello ${name}`;
```

---

# 6. Number

```typescript
let age: number = 22;

let price: number = 99.99;
```

---

# 7. Boolean

```typescript
let isLoggedIn: boolean = false;
```

---

# 8. Any

```typescript
let value: any = "Hello";

value = 100;
value = true;
```

Avoid unnecessary `any`.

---

# 9. Unknown

```typescript
let value: unknown;

value = "Hello";
value = 100;
```

Before using it:

```typescript
if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

Prefer `unknown` over `any` when the type is genuinely unknown.

---

# 10. Never

Used when a function never successfully returns.

```typescript
function throwError(): never {
    throw new Error("Something went wrong");
}
```

---

# 11. Arrays

```typescript
let numbers: number[] = [
    1,
    2,
    3
];
```

Alternative:

```typescript
let numbers: Array<number> = [
    1,
    2,
    3
];
```

Strings:

```typescript
let names: string[] = [
    "Adnan",
    "Rahul"
];
```

---

# 12. Mixed Array / Union Array

```typescript
let values: (string | number)[] = [
    "Adnan",
    22,
    "IITM"
];
```

---

# 13. Tuple

Fixed number and order of values:

```typescript
let user: [string, number] = [
    "Adnan",
    22
];
```

Access:

```typescript
user[0];
user[1];
```

---

# 14. Optional Tuple

```typescript
let data: [string, number?];

data = ["Adnan"];
data = ["Adnan", 22];
```

---

# 15. Object Type

```typescript
let user: {
    name: string;
    age: number;
} = {
    name: "Adnan",
    age: 22
};
```

---

# 16. Optional Properties

```typescript
let user: {
    name: string;
    age?: number;
} = {
    name: "Adnan"
};
```

---

# 17. Type Alias

```typescript
type User = {
    name: string;
    age: number;
};
```

Use:

```typescript
const user: User = {
    name: "Adnan",
    age: 22
};
```

---

# 18. Interface

```typescript
interface User {
    name: string;
    age: number;
}
```

Use:

```typescript
const user: User = {
    name: "Adnan",
    age: 22
};
```

---

# 19. Interface Optional Property

```typescript
interface User {
    name: string;
    email?: string;
}
```

---

# 20. readonly

```typescript
interface User {
    readonly id: number;
    name: string;
}
```

This cannot be changed:

```typescript
user.id = 10;
```

---

# 21. Function Types

```typescript
function add(
    a: number,
    b: number
): number {

    return a + b;
}
```

---

# 22. Arrow Function

```typescript
const add = (
    a: number,
    b: number
): number => {

    return a + b;
};
```

Short:

```typescript
const add = (
    a: number,
    b: number
): number => a + b;
```

---

# 23. Function Type

```typescript
type AddFunction = (
    a: number,
    b: number
) => number;
```

Use:

```typescript
const add: AddFunction = (
    a,
    b
) => a + b;
```

---

# 24. Optional Function Parameter

```typescript
function greet(
    name?: string
): string {

    return `Hello ${name ?? "User"}`;
}
```

---

# 25. Default Parameter

```typescript
function greet(
    name: string = "User"
): string {

    return `Hello ${name}`;
}
```

---

# 26. Rest Parameters

```typescript
function sum(
    ...numbers: number[]
): number {

    return numbers.reduce(
        (total, n) => total + n,
        0
    );
}
```

---

# 27. Union Types

```typescript
let id: string | number;

id = 10;
id = "abc";
```

---

# 28. Union Function

```typescript
function printId(
    id: string | number
) {

    console.log(id);
}
```

---

# 29. Type Narrowing

```typescript
function printId(
    id: string | number
) {

    if (typeof id === "string") {

        console.log(
            id.toUpperCase()
        );

    } else {

        console.log(
            id.toFixed(2)
        );
    }
}
```

---

# 30. Literal Types

```typescript
let direction:
    "left"
    | "right"
    | "up"
    | "down";
```

Now:

```typescript
direction = "left";
```

Valid.

```typescript
direction = "hello";
```

Invalid.

---

# 31. Literal Object

```typescript
type Status =
    "pending"
    | "success"
    | "failed";
```

---

# 32. Intersection Types

Combine types:

```typescript
type Person = {
    name: string;
};

type Employee = {
    employeeId: number;
};

type EmployeePerson =
    Person & Employee;
```

Use:

```typescript
const employee: EmployeePerson = {
    name: "Adnan",
    employeeId: 101
};
```

---

# 33. Interface extends

```typescript
interface Person {
    name: string;
}

interface Employee extends Person {
    employeeId: number;
}
```

---

# 34. Nested Objects

```typescript
interface User {
    name: string;

    address: {
        city: string;
        state: string;
    };
}
```

---

# 35. Index Signature

Dynamic keys:

```typescript
interface Scores {
    [subject: string]: number;
}
```

Use:

```typescript
const scores: Scores = {
    math: 90,
    physics: 85,
    programming: 95
};
```

---

# 36. Record

```typescript
type Scores =
    Record<string, number>;
```

Example:

```typescript
const scores: Scores = {
    math: 90,
    programming: 95
};
```

---

# 37. Enum

```typescript
enum Role {
    USER,
    ADMIN,
    MANAGER
}
```

Use:

```typescript
const role = Role.ADMIN;
```

String enum:

```typescript
enum Role {
    USER = "user",
    ADMIN = "admin",
    MANAGER = "manager"
}
```

---

# 38. `as const`

```typescript
const roles = [
    "user",
    "admin",
    "manager"
] as const;
```

This creates readonly literal values.

---

# 39. keyof

```typescript
type User = {
    name: string;
    age: number;
    email: string;
};

type UserKey = keyof User;
```

Result:

```text
"name" | "age" | "email"
```

---

# 40. typeof

```typescript
const user = {
    name: "Adnan",
    age: 22
};

type User = typeof user;
```

---

# 41. Indexed Access Types

```typescript
type User = {
    name: string;
    age: number;
};

type UserName = User["name"];
```

Result:

```text
string
```

---

# 42. Generic

```typescript
function identity<T>(
    value: T
): T {

    return value;
}
```

Usage:

```typescript
identity<string>("Hello");

identity<number>(100);
```

TypeScript can infer:

```typescript
identity("Hello");

identity(100);
```

---

# 43. Generic Array Function

```typescript
function first<T>(
    items: T[]
): T {

    return items[0];
}
```

---

# 44. Generic Interface

```typescript
interface ApiResponse<T> {
    data: T;
    success: boolean;
}
```

Use:

```typescript
interface User {
    id: number;
    name: string;
}

const response:
    ApiResponse<User> = {

    data: {
        id: 1,
        name: "Adnan"
    },

    success: true
};
```

---

# 45. Multiple Generics

```typescript
function pair<T, U>(
    first: T,
    second: U
): [T, U] {

    return [first, second];
}
```

---

# 46. Generic Constraint

```typescript
function getLength<T extends { length: number }>(
    value: T
): number {

    return value.length;
}
```

Works:

```typescript
getLength("Hello");

getLength([1, 2, 3]);
```

---

# 47. Generic keyof

```typescript
function getProperty<
    T,
    K extends keyof T
>(
    object: T,
    key: K
): T[K] {

    return object[key];
}
```

Use:

```typescript
const user = {
    name: "Adnan",
    age: 22
};

getProperty(user, "name");
```

---

# 48. Classes

```typescript
class User {

    name: string;
    age: number;

    constructor(
        name: string,
        age: number
    ) {

        this.name = name;
        this.age = age;
    }

    greet(): string {

        return `Hello ${this.name}`;
    }
}
```

---

# 49. Access Modifiers

```typescript
class User {

    public name: string;

    private password: string;

    protected role: string;

    constructor(
        name: string,
        password: string,
        role: string
    ) {

        this.name = name;
        this.password = password;
        this.role = role;
    }
}
```

---

# 50. readonly Class Property

```typescript
class User {

    readonly id: number;

    constructor(id: number) {

        this.id = id;
    }
}
```

---

# 51. Parameter Properties

Short class syntax:

```typescript
class User {

    constructor(
        public name: string,
        private age: number
    ) {}
}
```

---

# 52. Inheritance

```typescript
class Animal {

    move(): void {

        console.log("Moving");
    }
}


class Dog extends Animal {

    bark(): void {

        console.log("Bark");
    }
}
```

---

# 53. Abstract Class

```typescript
abstract class Animal {

    abstract speak(): void;

    move(): void {

        console.log("Moving");
    }
}
```

---

# 54. Interface Implementation

```typescript
interface Payment {

    pay(amount: number): void;
}


class StripePayment
    implements Payment {

    pay(amount: number): void {

        console.log(
            `Paid ${amount}`
        );
    }
}
```

---

# 55. Static

```typescript
class MathUtils {

    static add(
        a: number,
        b: number
    ): number {

        return a + b;
    }
}
```

Use:

```typescript
MathUtils.add(10, 20);
```

---

# 56. Getters

```typescript
class User {

    constructor(
        private _name: string
    ) {}

    get name(): string {

        return this._name;
    }
}
```

---

# 57. Setters

```typescript
class User {

    private _age = 0;

    set age(value: number) {

        if (value < 0) {
            throw new Error(
                "Invalid age"
            );
        }

        this._age = value;
    }

    get age(): number {

        return this._age;
    }
}
```

---

# 58. Modules

Export:

```typescript
export function add(
    a: number,
    b: number
): number {

    return a + b;
}
```

Import:

```typescript
import { add } from "./math";
```

---

# 59. Default Export

```typescript
export default class User {

    name: string;

    constructor(name: string) {

        this.name = name;
    }
}
```

Import:

```typescript
import User from "./User";
```

---

# 60. Multiple Imports

```typescript
import {
    add,
    subtract,
    multiply
} from "./math";
```

---

# 61. Type-only Import

```typescript
import type { User } from "./types";
```

---

# 62. Type-only Export

```typescript
export type User = {
    id: number;
    name: string;
};
```

---

# 63. Utility Types

TypeScript provides built-in utility types:

```text
Partial
Required
Readonly
Pick
Omit
Record
Exclude
Extract
NonNullable
ReturnType
Parameters
Awaited
```

---

# 64. Partial

```typescript
interface User {
    name: string;
    age: number;
    email: string;
}

type UpdateUser =
    Partial<User>;
```

Now all properties are optional.

---

# 65. Required

```typescript
type RequiredUser =
    Required<User>;
```

All properties become required.

---

# 66. Readonly

```typescript
type ReadonlyUser =
    Readonly<User>;
```

---

# 67. Pick

Select specific properties:

```typescript
type UserPreview =
    Pick<User, "name" | "email">;
```

---

# 68. Omit

Remove properties:

```typescript
type PublicUser =
    Omit<User, "password">;
```

---

# 69. Record

```typescript
type UserRoles =
    Record<
        "admin" | "user",
        string
    >;
```

---

# 70. Exclude

```typescript
type Status =
    "pending"
    | "success"
    | "failed";

type FailedStatus =
    Exclude<Status, "success">;
```

---

# 71. Extract

```typescript
type Status =
    "pending"
    | "success"
    | "failed";

type Selected =
    Extract<
        Status,
        "success" | "failed"
    >;
```

---

# 72. NonNullable

```typescript
type Value =
    string | null | undefined;

type CleanValue =
    NonNullable<Value>;
```

Result:

```text
string
```

---

# 73. ReturnType

```typescript
function getUser() {

    return {
        id: 1,
        name: "Adnan"
    };
}

type User =
    ReturnType<typeof getUser>;
```

---

# 74. Parameters

```typescript
function add(
    a: number,
    b: number
) {
    return a + b;
}

type AddParams =
    Parameters<typeof add>;
```

Result:

```text
[number, number]
```

---

# 75. Awaited

```typescript
async function getUser() {

    return {
        id: 1,
        name: "Adnan"
    };
}

type User =
    Awaited<
        ReturnType<typeof getUser>
    >;
```

---

# 76. Conditional Types

```typescript
type IsString<T> =
    T extends string
        ? true
        : false;
```

Example:

```typescript
type A = IsString<string>;
```

Result:

```text
true
```

---

# 77. Mapped Types

```typescript
type Optional<T> = {
    [K in keyof T]?: T[K];
};
```

Equivalent idea to:

```typescript
Partial<T>
```

---

# 78. Template Literal Types

```typescript
type EventName =
    `on${string}`;
```

Valid:

```typescript
const event: EventName = "onClick";
```

---

# 79. Type Guards

```typescript
function isString(
    value: unknown
): value is string {

    return typeof value === "string";
}
```

Use:

```typescript
if (isString(value)) {

    value.toUpperCase();
}
```

---

# 80. `in` Narrowing

```typescript
type Admin = {
    role: "admin";
    permissions: string[];
};

type User = {
    role: "user";
    name: string;
};

function handle(
    account: Admin | User
) {

    if ("permissions" in account) {

        console.log(
            account.permissions
        );
    }
}
```

---

# 81. Discriminated Union

```typescript
type Result =
    | {
        status: "success";
        data: string;
    }
    | {
        status: "error";
        message: string;
    };
```

Use:

```typescript
function handle(
    result: Result
) {

    if (result.status === "success") {

        console.log(result.data);

    } else {

        console.log(result.message);
    }
}
```

---

# 82. Nullish Coalescing

```typescript
const name =
    user.name ?? "Guest";
```

Difference:

```text
?? → only null / undefined

|| → any falsy value
```

---

# 83. Optional Chaining

```typescript
const city =
    user.address?.city;
```

Function:

```typescript
user.getAddress?.();
```

---

# 84. Non-null Assertion

```typescript
const element =
    document.querySelector("#app")!;
```

Use carefully.

---

# 85. Type Assertion

```typescript
const value =
    input.value as string;
```

Alternative:

```typescript
const value =
    <string>input.value;
```

Prefer `as` in modern TS/JSX code.

---

# 86. DOM

Get element:

```typescript
const button =
    document.querySelector(
        "#submit"
    );
```

Typed:

```typescript
const button =
    document.querySelector<HTMLButtonElement>(
        "#submit"
    );
```

---

# 87. Event Listener

```typescript
button?.addEventListener(
    "click",
    (event) => {

        console.log(event);
    }
);
```

---

# 88. Input Element

```typescript
const input =
    document.querySelector<HTMLInputElement>(
        "#email"
    );

console.log(
    input?.value
);
```

---

# 89. Form

```typescript
const form =
    document.querySelector<HTMLFormElement>(
        "#form"
    );

form?.addEventListener(
    "submit",
    (event) => {

        event.preventDefault();

        const formData =
            new FormData(form);

        console.log(
            formData.get("email")
        );
    }
);
```

---

# 90. Fetch API

```typescript
const response =
    await fetch("/api/users");

const data =
    await response.json();
```

---

# 91. Typed API Response

```typescript
interface User {
    id: number;
    name: string;
}

const response =
    await fetch("/api/users");

const users =
    await response.json() as User[];
```

Remember:

> Type assertions do not validate runtime data.

---

# 92. Generic API Function

```typescript
async function fetchApi<T>(
    url: string
): Promise<T> {

    const response =
        await fetch(url);

    if (!response.ok) {

        throw new Error(
            `HTTP ${response.status}`
        );
    }

    return response.json();
}
```

Use:

```typescript
const users =
    await fetchApi<User[]>(
        "/api/users"
    );
```

---

# 93. POST Request

```typescript
const response =
    await fetch("/api/users", {

        method: "POST",

        headers: {
            "Content-Type":
                "application/json"
        },

        body: JSON.stringify({
            name: "Adnan",
            email: "adnan@example.com"
        })
    });
```

---

# 94. API Error Handling

```typescript
try {

    const response =
        await fetch("/api/users");

    if (!response.ok) {

        throw new Error(
            `Request failed: ${response.status}`
        );
    }

    const data =
        await response.json();

} catch (error) {

    console.error(error);
}
```

---

# 95. Async Function

```typescript
async function getUsers() {

    const response =
        await fetch("/api/users");

    return response.json();
}
```

---

# 96. Promise

```typescript
const promise:
    Promise<string> =
    Promise.resolve("Hello");
```

---

# 97. Promise Type

```typescript
function getUser():
    Promise<User> {

    return fetchApi<User>(
        "/api/user"
    );
}
```

---

# 98. Promise.all

```typescript
const [
    users,
    products
] = await Promise.all([

    fetchApi<User[]>(
        "/api/users"
    ),

    fetchApi<Product[]>(
        "/api/products"
    )
]);
```

---

# 99. Promise.allSettled

```typescript
const results =
    await Promise.allSettled([
        fetch("/api/users"),
        fetch("/api/products")
    ]);
```

Useful when one failure should not reject the entire group.

---

# 100. Error Type

Modern TypeScript:

```typescript
try {

    // code

} catch (error: unknown) {

    if (error instanceof Error) {

        console.log(
            error.message
        );
    }
}
```

---

# 101. Custom Error

```typescript
class ApiError extends Error {

    status: number;

    constructor(
        message: string,
        status: number
    ) {

        super(message);

        this.name = "ApiError";
        this.status = status;
    }
}
```

---

# 102. JSON Parsing

```typescript
const data:
    unknown =
    JSON.parse(text);
```

Validate before trusting external data.

---

# 103. Zod

Install:

```bash
npm install zod
```

Schema:

```typescript
import { z } from "zod";

const UserSchema = z.object({

    name: z.string(),

    age: z.number().int().min(18),

    email: z.string().email()
});
```

---

# 104. Zod Parse

```typescript
const user =
    UserSchema.parse(data);
```

Safe parse:

```typescript
const result =
    UserSchema.safeParse(data);

if (result.success) {

    console.log(
        result.data
    );

} else {

    console.log(
        result.error
    );
}
```

---

# 105. Infer Type from Zod

```typescript
type User =
    z.infer<typeof UserSchema>;
```

One source of truth:

```text
Zod Schema
     ↓
Runtime Validation
     +
TypeScript Type
```

---

# 106. React + TypeScript

Create project:

```bash
npm create vite@latest my-app
```

Select:

```text
React
TypeScript
```

---

# 107. React Props

```tsx
interface UserCardProps {
    name: string;
    age: number;
}

function UserCard({
    name,
    age
}: UserCardProps) {

    return (
        <div>
            <h2>{name}</h2>
            <p>{age}</p>
        </div>
    );
}
```

---

# 108. React useState

```tsx
import {
    useState
} from "react";

const [count, setCount] =
    useState<number>(0);
```

Type inference usually works:

```tsx
const [count, setCount] =
    useState(0);
```

---

# 109. React State Object

```tsx
interface User {
    name: string;
    age: number;
}

const [user, setUser] =
    useState<User | null>(null);
```

---

# 110. React Event

Input:

```tsx
function handleChange(
    event:
        React.ChangeEvent<HTMLInputElement>
) {

    console.log(
        event.target.value
    );
}
```

Button:

```tsx
function handleClick(
    event:
        React.MouseEvent<HTMLButtonElement>
) {

    console.log("Clicked");
}
```

---

# 111. React Form

```tsx
function Form() {

    const [email, setEmail] =
        useState("");

    function submit(
        event:
            React.FormEvent<HTMLFormElement>
    ) {

        event.preventDefault();

        console.log(email);
    }

    return (
        <form onSubmit={submit}>

            <input
                value={email}
                onChange={(e) =>
                    setEmail(
                        e.target.value
                    )
                }
            />

            <button>
                Submit
            </button>

        </form>
    );
}
```

---

# 112. React useEffect

```tsx
import {
    useEffect
} from "react";

useEffect(() => {

    console.log("Mounted");

}, []);
```

---

# 113. React API Fetch

```tsx
useEffect(() => {

    async function loadUsers() {

        const users =
            await fetchApi<User[]>(
                "/api/users"
            );

        setUsers(users);
    }

    loadUsers();

}, []);
```

---

# 114. React useRef

```tsx
const inputRef =
    useRef<HTMLInputElement>(null);
```

Use:

```tsx
inputRef.current?.focus();
```

---

# 115. React Context

```tsx
interface AuthContextType {

    user: User | null;

    login: (
        user: User
    ) => void;

    logout: () => void;
}
```

Create:

```tsx
const AuthContext =
    createContext<
        AuthContextType | undefined
    >(undefined);
```

---

# 116. Custom Hook

```tsx
function useAuth() {

    const context =
        useContext(AuthContext);

    if (!context) {

        throw new Error(
            "useAuth must be used inside AuthProvider"
        );
    }

    return context;
}
```

---

# 117. React Component Children

```tsx
interface CardProps {

    children:
        React.ReactNode;
}

function Card({
    children
}: CardProps) {

    return (
        <div className="card">
            {children}
        </div>
    );
}
```

---

# 118. React Component Type

Prefer:

```tsx
function Button(
    props: ButtonProps
) {
    ...
}
```

rather than unnecessarily using:

```tsx
React.FC
```

---

# 119. Node.js + TypeScript

Install:

```bash
npm install -D typescript tsx @types/node
```

Example:

```typescript
console.log(
    "Node + TypeScript"
);
```

Run:

```bash
npx tsx src/index.ts
```

---

# 120. Express + TypeScript

Install:

```bash
npm install express
npm install -D @types/express
```

Basic:

```typescript
import express from "express";

const app =
    express();

app.use(
    express.json()
);

app.get(
    "/",
    (req, res) => {

        res.json({
            message: "Hello"
        });
    }
);

app.listen(
    3000,
    () => {

        console.log(
            "Server running"
        );
    }
);
```

---

# 121. Express Route Types

```typescript
import {
    Request,
    Response
} from "express";

app.get(
    "/users",
    (
        req: Request,
        res: Response
    ) => {

        res.json([]);
    }
);
```

---

# 122. Express Request Body

```typescript
interface CreateUserBody {

    name: string;

    email: string;
}

app.post(
    "/users",
    (
        req: Request<
            {},
            {},
            CreateUserBody
        >,
        res: Response
    ) => {

        const {
            name,
            email
        } = req.body;

        res.json({
            name,
            email
        });
    }
);
```

---

# 123. Environment Variables

Node.js:

```typescript
const port =
    process.env.PORT ?? "3000";
```

Use `.env` with a suitable package such as `dotenv`:

```bash
npm install dotenv
```

```typescript
import "dotenv/config";

const databaseUrl =
    process.env.DATABASE_URL;
```

---

# 124. TypeScript Configuration

Important `tsconfig.json` options:

```json
{
    "compilerOptions": {

        "target": "ES2022",

        "module": "NodeNext",

        "moduleResolution": "NodeNext",

        "strict": true,

        "esModuleInterop": true,

        "skipLibCheck": true,

        "noUncheckedIndexedAccess": true,

        "exactOptionalPropertyTypes": true,

        "outDir": "./dist"
    }
}
```

---

# 125. Strict Mode

Enable:

```json
{
    "compilerOptions": {
        "strict": true
    }
}
```

This enables stronger type checking.

---

# 126. TypeScript + PostgreSQL

Install:

```bash
npm install pg
npm install -D @types/pg
```

Connection:

```typescript
import {
    Pool
} from "pg";

const pool =
    new Pool({
        connectionString:
            process.env.DATABASE_URL
    });
```

---

# 127. PostgreSQL Query

```typescript
const result =
    await pool.query(
        "SELECT * FROM users"
    );

console.log(
    result.rows
);
```

---

# 128. Parameterized PostgreSQL Query

Never:

```typescript
const query =
    `SELECT * FROM users
     WHERE email = '${email}'`;
```

Use:

```typescript
const result =
    await pool.query(
        `
        SELECT *
        FROM users
        WHERE email = $1
        `,
        [email]
    );
```

---

# 129. SQL Insert

```typescript
const result =
    await pool.query(
        `
        INSERT INTO users
        (name, email)
        VALUES ($1, $2)
        RETURNING *
        `,
        [
            name,
            email
        ]
    );
```

---

# 130. Prisma

Install:

```bash
npm install prisma
npm install @prisma/client
```

Initialize:

```bash
npx prisma init
```

Schema:

```prisma
model User {

    id Int @id @default(autoincrement())

    name String

    email String @unique
}
```

Generate:

```bash
npx prisma generate
```

---

# 131. Prisma Client

```typescript
import {
    PrismaClient
} from "@prisma/client";

const prisma =
    new PrismaClient();
```

Find:

```typescript
const users =
    await prisma.user.findMany();
```

Create:

```typescript
const user =
    await prisma.user.create({

        data: {
            name: "Adnan",
            email: "adnan@example.com"
        }
    });
```

---

# 132. Prisma Update

```typescript
await prisma.user.update({

    where: {
        id: 1
    },

    data: {
        name: "New Name"
    }
});
```

---

# 133. Prisma Delete

```typescript
await prisma.user.delete({

    where: {
        id: 1
    }
});
```

---

# 134. Prisma Transaction

```typescript
await prisma.$transaction([

    prisma.user.update({
        where: { id: 1 },
        data: { name: "A" }
    }),

    prisma.user.update({
        where: { id: 2 },
        data: { name: "B" }
    })

]);
```

---

# 135. Axios

Install:

```bash
npm install axios
```

GET:

```typescript
import axios from "axios";

const response =
    await axios.get<User[]>(
        "/api/users"
    );

console.log(
    response.data
);
```

POST:

```typescript
await axios.post(
    "/api/users",
    {
        name: "Adnan"
    }
);
```

---

# 136. API Client

```typescript
import axios from "axios";

export const api =
    axios.create({

        baseURL:
            "http://localhost:8000/api",

        headers: {
            "Content-Type":
                "application/json"
        }
    });
```

Use:

```typescript
const response =
    await api.get<User[]>(
        "/users"
    );
```

---

# 137. Authentication Token

```typescript
api.defaults.headers.common[
    "Authorization"
] = `Bearer ${token}`;
```

For browser apps, carefully choose token storage based on your threat model; HttpOnly secure cookies are often preferable for session-style authentication.

---

# 138. Next.js + TypeScript

Create:

```bash
npx create-next-app@latest
```

Select:

```text
TypeScript
```

Page:

```tsx
export default function Home() {

    return (
        <main>
            <h1>
                Hello
            </h1>
        </main>
    );
}
```

---

# 139. Next.js API Route

App Router:

```text
app/
└── api/
    └── users/
        └── route.ts
```

```typescript
import {
    NextResponse
} from "next/server";

export async function GET() {

    return NextResponse.json({
        users: []
    });
}
```

---

# 140. Next.js POST

```typescript
export async function POST(
    request: Request
) {

    const body =
        await request.json();

    return NextResponse.json(
        body,
        {
            status: 201
        }
    );
}
```

---

# 141. TypeScript Project Structure

```text
src/
│
├── components/
│
├── pages/
│
├── hooks/
│
├── services/
│
├── types/
│
├── utils/
│
├── lib/
│
├── api/
│
└── main.ts
```

---

# 142. Backend TypeScript Structure

```text
src/
│
├── controllers/
│
├── routes/
│
├── services/
│
├── repositories/
│
├── models/
│
├── schemas/
│
├── middleware/
│
├── utils/
│
├── config/
│
└── server.ts
```

---

# 143. Recommended Full-Stack Architecture

```text
React / Next.js
       ↓
API Client
       ↓
FastAPI / Node / Express
       ↓
Validation
       ↓
Service Layer
       ↓
Repository / ORM
       ↓
PostgreSQL
```

---

# 144. API Types

```typescript
interface User {

    id: number;

    name: string;

    email: string;
}

interface CreateUserRequest {

    name: string;

    email: string;
}

interface UpdateUserRequest {

    name?: string;

    email?: string;
}

interface ApiResponse<T> {

    success: boolean;

    data: T;

    message?: string;
}
```

---

# 145. Generic API Response

```typescript
type UserResponse =
    ApiResponse<User>;

type UsersResponse =
    ApiResponse<User[]>;
```

---

# 146. Pagination Type

```typescript
interface Pagination {

    page: number;

    limit: number;

    total: number;

    totalPages: number;
}

interface PaginatedResponse<T> {

    data: T[];

    pagination: Pagination;
}
```

Use:

```typescript
type UsersResponse =
    PaginatedResponse<User>;
```

---

# 147. Repository Pattern

```typescript
interface UserRepository {

    findById(
        id: number
    ): Promise<User | null>;

    findAll():
        Promise<User[]>;

    create(
        data: CreateUserRequest
    ): Promise<User>;
}
```

---

# 148. Service Layer

```typescript
class UserService {

    constructor(
        private repository:
            UserRepository
    ) {}

    async getUser(
        id: number
    ): Promise<User> {

        const user =
            await this.repository
                .findById(id);

        if (!user) {

            throw new Error(
                "User not found"
            );
        }

        return user;
    }
}
```

---

# 149. Dependency Injection

```typescript
const repository:
    UserRepository =
    new PostgresUserRepository();

const userService =
    new UserService(
        repository
    );
```

---

# 150. Type-safe Config

```typescript
interface Config {

    port: number;

    databaseUrl: string;

    jwtSecret: string;
}

const config: Config = {

    port: Number(
        process.env.PORT ?? 3000
    ),

    databaseUrl:
        process.env.DATABASE_URL!,

    jwtSecret:
        process.env.JWT_SECRET!
};
```

For production, validate environment variables at startup instead of relying only on `!`.

---

# 151. JWT

Install:

```bash
npm install jsonwebtoken
npm install -D @types/jsonwebtoken
```

Create:

```typescript
import jwt from "jsonwebtoken";

const token =
    jwt.sign(
        {
            userId: 1
        },
        process.env.JWT_SECRET!,
        {
            expiresIn: "15m"
        }
    );
```

Verify:

```typescript
const payload =
    jwt.verify(
        token,
        process.env.JWT_SECRET!
    );
```

---

# 152. Password Hashing

Use a dedicated password hashing library such as:

```text
Argon2
bcrypt
```

Example with bcrypt:

```bash
npm install bcrypt
npm install -D @types/bcrypt
```

Hash:

```typescript
import bcrypt from "bcrypt";

const hash =
    await bcrypt.hash(
        password,
        12
    );
```

Verify:

```typescript
const valid =
    await bcrypt.compare(
        password,
        hash
    );
```

---

# 153. CORS

Express:

```bash
npm install cors
npm install -D @types/cors
```

```typescript
import cors from "cors";

app.use(
    cors({
        origin:
            "http://localhost:5173"
    })
);
```

Production me allowed origins explicitly configure karo.

---

# 154. Middleware

```typescript
import {
    Request,
    Response,
    NextFunction
} from "express";

function logger(
    req: Request,
    res: Response,
    next: NextFunction
) {

    console.log(
        req.method,
        req.path
    );

    next();
}
```

Use:

```typescript
app.use(logger);
```

---

# 155. Authentication Middleware

```typescript
function authMiddleware(
    req: Request,
    res: Response,
    next: NextFunction
) {

    const auth =
        req.headers.authorization;

    if (!auth) {

        return res
            .status(401)
            .json({
                message:
                    "Unauthorized"
            });
    }

    next();
}
```

---

# 156. Role Based Access

```typescript
type Role =
    "user"
    | "admin"
    | "manager";
```

```typescript
function requireRole(
    ...allowedRoles: Role[]
) {

    return (
        req: Request,
        res: Response,
        next: NextFunction
    ) => {

        const role =
            req.user?.role;

        if (
            !role ||
            !allowedRoles.includes(role)
        ) {

            return res
                .status(403)
                .json({
                    message:
                        "Forbidden"
                });
        }

        next();
    };
}
```

---

# 157. Extending Express Request

Create:

```text
src/types/express.d.ts
```

```typescript
declare global {

    namespace Express {

        interface Request {

            user?: {
                id: number;
                role: Role;
            };
        }
    }
}

export {};
```

---

# 158. Testing with Vitest

Install:

```bash
npm install -D vitest
```

Test:

```typescript
import {
    describe,
    it,
    expect
} from "vitest";

describe("add", () => {

    it("adds numbers", () => {

        expect(
            2 + 3
        ).toBe(5);
    });
});
```

Run:

```bash
npx vitest
```

---

# 159. Jest

Install:

```bash
npm install -D jest ts-jest @types/jest
```

Example:

```typescript
test(
    "addition",
    () => {

        expect(
            2 + 3
        ).toBe(5);
    }
);
```

---

# 160. ESLint

Install:

```bash
npm install -D eslint
```

Use ESLint to find:

```text
bugs
bad patterns
unused code
style problems
```

---

# 161. Prettier

Install:

```bash
npm install -D prettier
```

Format:

```bash
npx prettier
    --write .
```

---

# 162. Package Scripts

`package.json`

```json
{
    "scripts": {

        "dev": "tsx watch src/index.ts",

        "build": "tsc",

        "start": "node dist/index.js",

        "test": "vitest",

        "lint": "eslint .",

        "format": "prettier --write ."
    }
}
```

---

# 163. npm Commands

Install dependencies:

```bash
npm install
```

Install package:

```bash
npm install axios
```

Development dependency:

```bash
npm install -D typescript
```

Remove:

```bash
npm uninstall axios
```

Update:

```bash
npm update
```

---

# 164. package.json

Example:

```json
{
    "name": "my-app",
    "version": "1.0.0",
    "private": true,
    "scripts": {
        "dev": "tsx watch src/index.ts",
        "build": "tsc",
        "start": "node dist/index.js"
    }
}
```

---

# 165. Build

```bash
npx tsc
```

Output:

```text
src/
   index.ts

dist/
   index.js
```

---

# 166. Source Maps

Useful during debugging:

```json
{
    "compilerOptions": {
        "sourceMap": true
    }
}
```

---

# 167. Declaration Files

Generate:

```json
{
    "compilerOptions": {
        "declaration": true
    }
}
```

Output:

```text
index.d.ts
```

Useful for libraries.

---

# 168. `.d.ts` Files

Example:

```typescript
declare module "some-library" {

    export function hello(
        name: string
    ): string;
}
```

---

# 169. Ambient Types

```typescript
declare const API_URL: string;
```

This tells TypeScript that the value exists elsewhere.

---

# 170. `unknown` vs `any`

```text
any
 ↓
Type checking disabled

unknown
 ↓
Must narrow before use
```

Prefer:

```typescript
unknown
```

for untrusted/external values.

---

# 171. `interface` vs `type`

Interface:

```typescript
interface User {
    name: string;
}
```

Type:

```typescript
type User = {
    name: string;
};
```

Both are useful.

Use `type` frequently for:

```text
Union
Intersection
Mapped types
Conditional types
Aliases
```

Use `interface` naturally for:

```text
Object contracts
Class implementation
Extending object shapes
```

---

# 172. TypeScript + React Folder Structure

```text
src/
│
├── components/
│   ├── Navbar.tsx
│   ├── Card.tsx
│   └── Button.tsx
│
├── pages/
│
├── hooks/
│
├── services/
│   └── api.ts
│
├── types/
│   ├── user.ts
│   └── api.ts
│
├── utils/
│
├── context/
│
└── App.tsx
```

---

# 173. TypeScript + FastAPI

Frontend:

```typescript
interface User {

    id: number;

    name: string;

    email: string;
}
```

FastAPI:

```python
class User(BaseModel):

    id: int

    name: str

    email: str
```

Flow:

```text
React / TypeScript
       ↓
fetch()
       ↓
FastAPI
       ↓
Pydantic
       ↓
PostgreSQL
```

---

# 174. API Client Pattern

```typescript
export async function
getUsers(): Promise<User[]> {

    return fetchApi<User[]>(
        "/api/users"
    );
}
```

Component:

```tsx
const users =
    await getUsers();
```

Keep API logic outside UI components when practical.

---

# 175. Loading / Error / Data State

```typescript
type State<T> =
    | {
        status: "loading";
    }
    | {
        status: "success";
        data: T;
    }
    | {
        status: "error";
        error: string;
    };
```

This is better than multiple loosely-related booleans.

---

# 176. Generic State

```typescript
const state:
    State<User[]> = {
    status: "loading"
};
```

---

# 177. Debounce

```typescript
function debounce<
    T extends (...args: any[]) => void
>(
    fn: T,
    delay: number
) {

    let timer:
        ReturnType<typeof setTimeout>;

    return (
        ...args: Parameters<T>
    ) => {

        clearTimeout(timer);

        timer = setTimeout(
            () => fn(...args),
            delay
        );
    };
}
```

---

# 178. Local Storage

Store:

```typescript
localStorage.setItem(
    "name",
    "Adnan"
);
```

Get:

```typescript
const name =
    localStorage.getItem(
        "name"
    );
```

Remove:

```typescript
localStorage.removeItem(
    "name"
);
```

Do not put highly sensitive secrets into browser-accessible storage without considering XSS risk.

---

# 179. Session Storage

```typescript
sessionStorage.setItem(
    "token",
    token
);
```

Get:

```typescript
sessionStorage.getItem(
    "token"
);
```

---

# 180. URLSearchParams

```typescript
const params =
    new URLSearchParams({

        search: "python",

        page: "1"
    });

const url =
    `/api/users?${params}`;
```

---

# 181. FormData

```typescript
const formData =
    new FormData();

formData.append(
    "name",
    "Adnan"
);

formData.append(
    "file",
    file
);
```

Send:

```typescript
await fetch(
    "/api/upload",
    {
        method: "POST",
        body: formData
    }
);
```

Do not manually set `Content-Type` for browser `FormData`; the browser adds the multipart boundary.

---

# 182. File Input

```typescript
const input =
    document.querySelector<HTMLInputElement>(
        "#file"
    );

const file =
    input?.files?.[0];
```

---

# 183. Drag and Drop Types

```typescript
function handleDrop(
    event: DragEvent
) {

    event.preventDefault();

    const files =
        event.dataTransfer?.files;
}
```

---

# 184. WebSocket

Browser:

```typescript
const socket =
    new WebSocket(
        "ws://localhost:8000/ws"
    );

socket.onopen = () => {

    socket.send(
        JSON.stringify({
            message: "Hello"
        })
    );
};

socket.onmessage = (
    event
) => {

    console.log(
        event.data
    );
};
```

---

# 185. Date

```typescript
const now =
    new Date();
```

ISO:

```typescript
now.toISOString();
```

---

# 186. Date Formatting

```typescript
const date =
    new Date();

const formatted =
    new Intl.DateTimeFormat(
        "en-IN"
    ).format(date);
```

---

# 187. Number Formatting

```typescript
const price =
    new Intl.NumberFormat(
        "en-IN",
        {
            style: "currency",
            currency: "INR"
        }
    ).format(50000);
```

---

# 188. Map

```typescript
const users =
    new Map<number, User>();

users.set(
    1,
    {
        id: 1,
        name: "Adnan"
    }
);
```

Get:

```typescript
users.get(1);
```

---

# 189. Set

```typescript
const ids =
    new Set<number>();

ids.add(1);
ids.add(2);
ids.add(2);
```

Duplicates are automatically removed.

---

# 190. WeakMap / WeakSet

Useful for certain object-keyed metadata and memory-sensitive patterns:

```typescript
const map =
    new WeakMap<object, string>();
```

---

# 191. Iteration

```typescript
for (
    const user of users
) {

    console.log(
        user.name
    );
}
```

---

# 192. Object Destructuring

```typescript
const user = {
    name: "Adnan",
    age: 22
};

const {
    name,
    age
} = user;
```

---

# 193. Array Destructuring

```typescript
const numbers = [
    10,
    20
];

const [
    first,
    second
] = numbers;
```

---

# 194. Spread

```typescript
const user2 = {
    ...user,
    age: 23
};
```

Array:

```typescript
const all = [
    ...a,
    ...b
];
```

---

# 195. Rest

```typescript
const [
    first,
    ...rest
] = numbers;
```

---

# 196. Null Handling

Bad:

```typescript
const name =
    user.name;
```

if `user` can be null.

Better:

```typescript
const name =
    user?.name;
```

or:

```typescript
const name =
    user?.name ?? "Guest";
```

---

# 197. Type-safe Array Find

```typescript
const user =
    users.find(
        user => user.id === 1
    );
```

Result:

```text
User | undefined
```

Handle it:

```typescript
if (!user) {
    throw new Error(
        "User not found"
    );
}
```

---

# 198. Array Methods

```typescript
map()
filter()
reduce()
find()
findIndex()
some()
every()
includes()
sort()
slice()
splice()
flat()
flatMap()
```

---

# 199. Map

```typescript
const names =
    users.map(
        user => user.name
    );
```

---

# 200. Filter

```typescript
const adults =
    users.filter(
        user => user.age >= 18
    );
```

---

# 201. Reduce

```typescript
const total =
    numbers.reduce(
        (sum, number) =>
            sum + number,
        0
    );
```

---

# 202. Object.keys

```typescript
const keys =
    Object.keys(user);
```

---

# 203. Object.values

```typescript
const values =
    Object.values(user);
```

---

# 204. Object.entries

```typescript
const entries =
    Object.entries(user);
```

---

# 205. Type-safe Object Helper

```typescript
function keysOf<T extends object>(
    object: T
): Array<keyof T> {

    return Object.keys(
        object
    ) as Array<keyof T>;
}
```

---

# 206. Immutability

Avoid:

```typescript
user.name = "New";
```

when you want immutable state.

Use:

```typescript
const updatedUser = {
    ...user,
    name: "New"
};
```

React state:

```tsx
setUser(
    previous => ({
        ...previous,
        name: "New"
    })
);
```

---

# 207. Generic CRUD Service

```typescript
interface Repository<T, ID> {

    findById(
        id: ID
    ): Promise<T | null>;

    findAll():
        Promise<T[]>;

    create(
        data: Omit<T, "id">
    ): Promise<T>;

    update(
        id: ID,
        data: Partial<T>
    ): Promise<T>;

    delete(
        id: ID
    ): Promise<void>;
}
```

---

# 208. Generic API Client

```typescript
class ApiClient {

    constructor(
        private baseUrl: string
    ) {}

    async get<T>(
        path: string
    ): Promise<T> {

        const response =
            await fetch(
                `${this.baseUrl}${path}`
            );

        if (!response.ok) {

            throw new Error(
                `HTTP ${response.status}`
            );
        }

        return response.json();
    }
}
```

Use:

```typescript
const api =
    new ApiClient(
        "http://localhost:8000"
    );

const users =
    await api.get<User[]>(
        "/users"
    );
```

---

# 209. Error Result Pattern

```typescript
type Result<T> =
    | {
        success: true;
        data: T;
    }
    | {
        success: false;
        error: string;
    };
```

Function:

```typescript
async function getUser(
    id: number
): Promise<Result<User>> {

    try {

        const user =
            await fetchApi<User>(
                `/api/users/${id}`
            );

        return {
            success: true,
            data: user
        };

    } catch (error) {

        return {
            success: false,
            error: "Failed to fetch user"
        };
    }
}
```

---

# 210. Environment-based API URL

```typescript
const API_URL =
    import.meta.env.VITE_API_URL;
```

Vite `.env`:

```env
VITE_API_URL=http://localhost:8000
```

Never expose private secrets in frontend environment variables.

---

# 211. Vite TypeScript

```bash
npm create vite@latest
```

Select:

```text
TypeScript
```

Run:

```bash
npm run dev
```

Build:

```bash
npm run build
```

Preview:

```bash
npm run preview
```

---

# 212. TypeScript + Tailwind

Install Tailwind according to the current Tailwind/Vite setup.

Typical component:

```tsx
function Button() {

    return (
        <button
            className="
                px-4
                py-2
                rounded-lg
            "
        >
            Click
        </button>
    );
}
```

---

# 213. TypeScript + React Component Pattern

```tsx
interface ButtonProps {

    children:
        React.ReactNode;

    onClick?: () => void;

    disabled?: boolean;
}

export function Button({
    children,
    onClick,
    disabled = false
}: ButtonProps) {

    return (
        <button
            onClick={onClick}
            disabled={disabled}
        >
            {children}
        </button>
    );
}
```

---

# 214. Reusable API Types

```typescript
export interface ApiError {

    message: string;

    code?: string;

    details?: unknown;
}
```

---

# 215. HTTP Status Codes

```text
200 → OK
201 → Created
204 → No Content

400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found
409 → Conflict
422 → Unprocessable Content
429 → Too Many Requests

500 → Internal Server Error
502 → Bad Gateway
503 → Service Unavailable
```

---

# 216. Full-Stack Request Flow

```text
React
  ↓
TypeScript
  ↓
API Client
  ↓
HTTP
  ↓
FastAPI / Express
  ↓
Validation
  ↓
Service
  ↓
Repository
  ↓
PostgreSQL
  ↓
Response
  ↓
TypeScript
  ↓
React UI
```

---

# 217. Recommended Libraries

## Core

```text
typescript
tsx
```

## Frontend

```text
react
next
vite
```

## API

```text
axios
```

## Validation

```text
zod
```

## Backend

```text
express
fastify
nestjs
```

## Database

```text
pg
prisma
drizzle-orm
typeorm
```

## Authentication

```text
jose
jsonwebtoken
argon2
bcrypt
```

## Testing

```text
vitest
jest
playwright
```

## Code Quality

```text
eslint
prettier
typescript
```

---

# 218. TypeScript vs JavaScript

```text
JavaScript

Runtime language
Dynamic typing


TypeScript

JavaScript + Static Type System
Compile-time checking
Better tooling
Better refactoring
Better large-project maintainability
```

---

# 219. TypeScript Mental Model

```text
.ts
 ↓
TypeScript Compiler
 ↓
JavaScript
 ↓
Browser / Node.js
```

Important:

```text
TypeScript types
        ↓
mostly removed during compilation
        ↓
JavaScript runtime
```

Therefore:

```text
TypeScript type checking
≠
Runtime validation
```

For external data use:

```text
Zod / other runtime validator
```

---

# 220. TypeScript Learning Roadmap

```text
LEVEL 1
│
├── JavaScript basics
├── Variables
├── Functions
├── Arrays
├── Objects
└── ES6+
        ↓
LEVEL 2
│
├── Basic Types
├── Type Inference
├── Union
├── Interface
├── Type Alias
├── Optional
└── readonly
        ↓
LEVEL 3
│
├── Generics
├── keyof
├── typeof
├── Utility Types
├── Conditional Types
├── Mapped Types
└── Type Guards
        ↓
LEVEL 4
│
├── Async/Await
├── Fetch
├── API Types
├── Error Handling
└── Runtime Validation
        ↓
LEVEL 5
│
├── React + TypeScript
├── Hooks
├── Props
├── Forms
├── Context
└── Custom Hooks
        ↓
LEVEL 6
│
├── Node.js
├── Express
├── PostgreSQL
├── Prisma / Drizzle
├── Authentication
└── REST APIs
        ↓
LEVEL 7
│
├── Next.js
├── Testing
├── Docker
├── CI/CD
├── Security
└── Production Architecture
```

---

# 221. Real-world Full-Stack TypeScript Stack

```text
                    TypeScript
                        │
          ┌─────────────┴─────────────┐
          │                           │
       Frontend                    Backend
          │                           │
       React                       Node.js
          │                           │
       Next.js                    Express
          │                           │
       Tailwind                  Validation
          │                           │
       API Client                Prisma/Drizzle
          │                           │
          └─────────────┬─────────────┘
                        │
                    PostgreSQL
                        │
                      Redis
                        │
                     Docker
```

---

# 222. Recommended Production Structure

```text
project/
│
├── src/
│   │
│   ├── config/
│   │
│   ├── controllers/
│   │
│   ├── routes/
│   │
│   ├── services/
│   │
│   ├── repositories/
│   │
│   ├── schemas/
│   │
│   ├── models/
│   │
│   ├── middleware/
│   │
│   ├── types/
│   │
│   ├── utils/
│   │
│   └── server.ts
│
├── tests/
│
├── prisma/
│
├── .env
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

---

# 223. Security Checklist

```text
✓ Never trust client-side types
✓ Validate API input at runtime
✓ Use Zod/Pydantic/server-side validation
✓ Parameterize SQL queries
✓ Hash passwords with Argon2/bcrypt
✓ Use HTTPS
✓ Don't expose secrets to frontend
✓ Configure CORS explicitly
✓ Validate JWT claims
✓ Use token/session expiration
✓ Add rate limiting
✓ Validate file uploads
✓ Limit request body size
✓ Avoid eval()
✓ Avoid unsafe HTML injection
✓ Keep dependencies updated
✓ Use npm audit/dependency auditing
✓ Don't log passwords/tokens
✓ Use secure cookies when appropriate
```

---

# 224. Golden Rules

```text
1. Let TypeScript infer simple types.

2. Avoid unnecessary `any`.

3. Prefer `unknown` for unknown external values.

4. Use interfaces/types for clear contracts.

5. Use unions for controlled states.

6. Use generics for reusable type-safe code.

7. Use utility types instead of duplicating types.

8. Use runtime validation for API input.

9. Don't assume JSON matches your TypeScript type.

10. Keep API types separate from UI types when useful.

11. Keep business logic outside React components.

12. Keep database logic outside route handlers.

13. Use parameterized SQL.

14. Validate environment variables at startup.

15. Handle null and undefined explicitly.

16. Use strict TypeScript configuration.

17. Test important business logic.

18. Keep frontend and backend contracts synchronized.

19. Don't expose private environment variables to browsers.

20. TypeScript improves developer safety;
    it does not replace runtime security.
```

---

# 225. Quick Cheat Sheet

```text
string
number
boolean

string[]
number[]

type
interface

|
&

keyof
typeof

Partial
Required
Readonly
Pick
Omit
Record
Exclude
Extract
NonNullable
ReturnType
Parameters
Awaited

<T>

Promise<T>

async / await

unknown
never

as

?. 
??

fetch()

FormData

React.ReactNode

React.ChangeEvent
React.MouseEvent
React.FormEvent

Request
Response
NextFunction

z.object()
z.infer<>

Promise.all()

Map
Set
```

---

# 226. Master Architecture

```text
                         TYPESCRIPT
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
       Frontend            Backend              Data
          │                   │                   │
       React               Node.js             Zod
       Next.js             Express             Prisma
       Vite                Fastify             PostgreSQL
          │                   │                   │
          └───────────────────┼───────────────────┘
                              │
                            APIs
                              │
                         Authentication
                              │
                         Business Logic
                              │
                            Database
                              │
                     Redis / Background Jobs
                              │
                            Docker
                              │
                           CI / CD
```

---

# END — TypeScript Master SDK
