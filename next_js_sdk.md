# ▲ Next.js Master SDK

> A reusable Next.js reference for building modern, production-ready full-stack web applications.

---

# 📚 Table of Contents

1. What is Next.js?
2. React vs Next.js
3. Installation
4. Project Structure
5. App Router
6. Pages
7. Layouts
8. Nested Routes
9. Dynamic Routes
10. Catch-all Routes
11. Route Groups
12. Private Routes
13. Linking & Navigation
14. Server Components
15. Client Components
16. `"use client"`
17. Props
18. State
19. Events
20. Forms
21. Server Actions
22. Loading UI
23. Error UI
24. Not Found
25. Metadata
26. SEO
27. Images
28. Fonts
29. Static Assets
30. CSS
31. Tailwind CSS
32. Environment Variables
33. Fetch API
34. Data Fetching
35. Caching
36. Revalidation
37. Dynamic Rendering
38. Route Handlers
39. GET API
40. POST API
41. PUT/PATCH API
42. DELETE API
43. Request & Response
44. Cookies
45. Headers
46. Middleware / Proxy
47. Authentication
48. Authorization
49. JWT
50. Database
51. Prisma
52. PostgreSQL
53. CRUD
54. Server Actions + Database
55. Forms + Validation
56. Zod
57. React Hook Form
58. API Architecture
59. Service Layer
60. Repository Pattern
61. Zustand
62. TanStack Query
63. TypeScript
64. API Types
65. File Upload
66. Pagination
67. Search
68. Debouncing
69. Optimistic UI
70. Streaming
71. Suspense
72. Parallel Routes
73. Intercepting Routes
74. Route Groups
75. `notFound()`
76. `redirect()`
77. `revalidatePath()`
78. `revalidateTag()`
79. Security
80. Performance
81. Testing
82. Docker
83. Deployment
84. Project Structure
85. Full-Stack Architecture
86. Production Checklist
87. Cheat Sheet

---

# 1. What is Next.js?

Next.js is a React framework for building full-stack web applications.

React mainly provides:

```text
UI
Components
State
Client-side logic
```

Next.js adds:

```text
Routing
Server Components
Server Actions
API endpoints
SEO
Caching
Rendering
Image optimization
Font optimization
Authentication architecture
Backend integration
Deployment
```

Basic architecture:

```text
Next.js
│
├── React UI
├── Routing
├── Server Components
├── Client Components
├── API
├── Server Actions
├── Database
└── Deployment
```

---

# 2. React vs Next.js

| React | Next.js |
|---|---|
| UI library | Full-stack React framework |
| Routing separately | Built-in routing |
| API separately | Route Handlers |
| SEO requires setup | Built-in metadata/SSR capabilities |
| Client-focused | Server + Client |
| Backend separate | Backend functionality possible |
| Vite commonly used | Next.js tooling |

Simple:

```text
React
+
Routing
+
Server
+
API
+
SEO
+
Rendering
+
Optimization
=
Next.js
```

---

# 3. Installation

Create project:

```bash
npx create-next-app@latest my-app
```

Typical choices:

```text
TypeScript       → Yes
ESLint           → Yes
Tailwind CSS     → Yes
src/ directory   → Yes
App Router       → Yes
Turbopack        → Yes
Import alias     → Yes
```

Run:

```bash
cd my-app
npm run dev
```

Open:

```text
http://localhost:3000
```

---

# 4. Important Commands

Development:

```bash
npm run dev
```

Production build:

```bash
npm run build
```

Production server:

```bash
npm start
```

Lint:

```bash
npm run lint
```

---

# 5. Project Structure

Basic:

```text
my-app/
│
├── public/
│
├── src/
│   └── app/
│       ├── layout.tsx
│       ├── page.tsx
│       ├── globals.css
│       └── favicon.ico
│
├── package.json
├── tsconfig.json
├── next.config.ts
└── .env.local
```

Production structure:

```text
src/
│
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   │
│   ├── login/
│   │   └── page.tsx
│   │
│   ├── dashboard/
│   │   ├── page.tsx
│   │   ├── loading.tsx
│   │   └── error.tsx
│   │
│   ├── api/
│   │   └── users/
│   │       └── route.ts
│   │
│   └── globals.css
│
├── components/
│   ├── ui/
│   ├── layout/
│   └── forms/
│
├── lib/
│   ├── db.ts
│   ├── auth.ts
│   └── utils.ts
│
├── services/
│
├── repositories/
│
├── actions/
│
├── hooks/
│
├── types/
│
└── config/
```

---

# 6. App Router

Next.js App Router uses the `app` directory.

```text
app/
├── page.tsx
├── about/
│   └── page.tsx
└── contact/
    └── page.tsx
```

Routes:

```text
/
 /about
 /contact
```

---

# 7. Page

`app/page.tsx`

```tsx
export default function Home() {
  return (
    <main>
      <h1>Home Page</h1>
    </main>
  );
}
```

---

# 8. Layout

`app/layout.tsx`

```tsx
import type { Metadata } from "next";

export const metadata: Metadata = {
  title: "My App",
  description: "My Next.js Application",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en">
      <body>
        {children}
      </body>
    </html>
  );
}
```

Layout wraps pages.

```text
Root Layout
     │
     ├── Home
     ├── About
     ├── Login
     └── Dashboard
```

---

# 9. Nested Routes

Structure:

```text
app/
└── dashboard/
    ├── page.tsx
    └── settings/
        └── page.tsx
```

Routes:

```text
/dashboard
/dashboard/settings
```

---

# 10. Dynamic Routes

Structure:

```text
app/
└── users/
    └── [id]/
        └── page.tsx
```

URL:

```text
/users/123
/users/456
```

Page:

```tsx
type Props = {
  params: Promise<{
    id: string;
  }>;
};

export default async function UserPage({
  params,
}: Props) {

  const { id } = await params;

  return (
    <h1>User ID: {id}</h1>
  );
}
```

---

# 11. Catch-all Routes

```text
app/
└── docs/
    └── [...slug]/
        └── page.tsx
```

Examples:

```text
/docs/react
/docs/react/hooks
/docs/react/hooks/use-state
```

---

# 12. Optional Catch-all

```text
[[...slug]]
```

Can match:

```text
/docs
/docs/react
/docs/react/hooks
```

---

# 13. Route Groups

Folder:

```text
(auth)
```

Example:

```text
app/
├── (auth)/
│   ├── login/
│   │   └── page.tsx
│   └── register/
│       └── page.tsx
│
└── dashboard/
    └── page.tsx
```

`(auth)` does not appear in URL.

Routes:

```text
/login
/register
/dashboard
```

---

# 14. Private Route Architecture

```text
/dashboard
     │
     ▼
Authentication Check
     │
 ┌───┴────┐
 │        │
YES       NO
 │        │
 ▼        ▼
Dashboard Login
```

Authorization:

```text
Authenticated?
     ↓
Role?
 ├── admin → Admin
 ├── user  → User Dashboard
 └── other → Forbidden
```

---

# 15. Link

Use Next.js `Link`.

```tsx
import Link from "next/link";

<Link href="/dashboard">
  Dashboard
</Link>
```

Dynamic:

```tsx
<Link href={`/users/${user.id}`}>
  View User
</Link>
```

---

# 16. Navigation

Client component:

```tsx
"use client";

import { useRouter } from "next/navigation";

export default function Button() {

  const router = useRouter();

  return (
    <button
      onClick={() => router.push("/dashboard")}
    >
      Dashboard
    </button>
  );
}
```

Other methods:

```tsx
router.push("/dashboard");

router.replace("/login");

router.back();

router.refresh();
```

---

# 17. Server Components

In App Router, components are Server Components by default.

```tsx
export default async function Page() {

  const data = await getData();

  return (
    <div>
      {data.name}
    </div>
  );
}
```

Server Components can:

```text
Fetch server-side data
Access server resources
Query database through server-side code
Keep secrets on server
Reduce client JavaScript
```

---

# 18. Client Components

When you need:

```text
useState
useEffect
useRef
Browser APIs
Click handlers
Interactive UI
```

use:

```tsx
"use client";
```

Example:

```tsx
"use client";

import { useState } from "react";

export default function Counter() {

  const [count, setCount] =
    useState(0);

  return (
    <button
      onClick={() => setCount(count + 1)}
    >
      {count}
    </button>
  );
}
```

---

# 19. Server vs Client

```text
SERVER COMPONENT
       │
       ├── Database
       ├── Secrets
       ├── Server API
       └── Data fetching
       
CLIENT COMPONENT
       │
       ├── State
       ├── Events
       ├── Browser API
       └── Interactive UI
```

Rule:

```text
Use Server Components by default.
Use Client Components when interactivity requires them.
```

---

# 20. Passing Props

Server component:

```tsx
import UserCard from "@/components/UserCard";

export default function Page() {

  const user = {
    name: "Adnan",
    role: "Developer",
  };

  return (
    <UserCard user={user} />
  );
}
```

Component:

```tsx
type Props = {
  user: {
    name: string;
    role: string;
  };
};

export default function UserCard({
  user,
}: Props) {

  return (
    <div>
      <h2>{user.name}</h2>
      <p>{user.role}</p>
    </div>
  );
}
```

---

# 21. Client State

```tsx
"use client";

import { useState } from "react";

export default function Counter() {

  const [count, setCount] =
    useState(0);

  return (
    <>
      <p>{count}</p>

      <button
        onClick={() =>
          setCount(prev => prev + 1)
        }
      >
        +
      </button>
    </>
  );
}
```

---

# 22. Forms

Client-side form:

```tsx
"use client";

import { useState } from "react";

export default function LoginForm() {

  const [email, setEmail] =
    useState("");

  const [password, setPassword] =
    useState("");

  function handleSubmit(
    e: React.FormEvent<HTMLFormElement>
  ) {

    e.preventDefault();

    console.log({
      email,
      password,
    });
  }

  return (
    <form onSubmit={handleSubmit}>

      <input
        type="email"
        value={email}
        onChange={e =>
          setEmail(e.target.value)
        }
      />

      <input
        type="password"
        value={password}
        onChange={e =>
          setPassword(e.target.value)
        }
      />

      <button type="submit">
        Login
      </button>

    </form>
  );
}
```

---

# 23. Server Actions

Server Actions allow server-side functions to be called from application code/forms.

Example:

```tsx
"use server";

export async function createUser(
  formData: FormData
) {

  const name =
    formData.get("name");

  const email =
    formData.get("email");

  console.log(name, email);
}
```

Use:

```tsx
<form action={createUser}>

  <input name="name" />

  <input name="email" />

  <button type="submit">
    Create
  </button>

</form>
```

---

# 24. Server Action with Database

Concept:

```text
Form
 ↓
Server Action
 ↓
Validation
 ↓
Database
 ↓
Revalidate
 ↓
UI
```

Example:

```tsx
"use server";

import { db } from "@/lib/db";

export async function createUser(
  formData: FormData
) {

  const name =
    String(formData.get("name"));

  const email =
    String(formData.get("email"));

  await db.user.create({
    data: {
      name,
      email,
    },
  });
}
```

Always validate untrusted input.

---

# 25. Loading UI

Create:

```text
app/dashboard/loading.tsx
```

```tsx
export default function Loading() {

  return (
    <div>
      Loading dashboard...
    </div>
  );
}
```

Next.js can display this while the route's content is loading.

---

# 26. Error UI

`error.tsx` is a Client Component.

```tsx
"use client";

export default function ErrorPage({
  reset,
}: {
  error: Error & {
    digest?: string;
  };
  reset: () => void;
}) {

  return (
    <div>

      <h2>
        Something went wrong.
      </h2>

      <button onClick={() => reset()}>
        Try again
      </button>

    </div>
  );
}
```

---

# 27. Not Found

`not-found.tsx`

```tsx
export default function NotFound() {

  return (
    <div>
      <h1>404</h1>
      <p>Page not found.</p>
    </div>
  );
}
```

Programmatically:

```tsx
import { notFound } from "next/navigation";

if (!user) {
  notFound();
}
```

---

# 28. redirect()

```tsx
import { redirect } from "next/navigation";

if (!user) {
  redirect("/login");
}
```

Useful for:

```text
Authentication
Authorization
After form submission
Conditional routing
```

---

# 29. Metadata

Static metadata:

```tsx
import type { Metadata } from "next";

export const metadata: Metadata = {

  title: "Home",
  description:
    "Welcome to my website",

};
```

---

# 30. Dynamic Metadata

```tsx
import type {
  Metadata
} from "next";

export async function generateMetadata(
  { params }: {
    params: Promise<{ id: string }>
  }
): Promise<Metadata> {

  const { id } = await params;

  return {
    title: `User ${id}`,
  };
}
```

---

# 31. SEO

Important:

```text
title
description
canonical URL
Open Graph
Twitter metadata
robots
sitemap
structured data
```

Example:

```tsx
export const metadata = {
  title: "My Website",
  description:
    "A modern web application",
};
```

---

# 32. Open Graph

```tsx
export const metadata = {

  title: "My App",

  openGraph: {
    title: "My App",
    description: "My website",
    images: ["/og-image.png"],
  },

};
```

---

# 33. Next Image

```tsx
import Image from "next/image";

<Image
  src="/profile.jpg"
  alt="Profile"
  width={500}
  height={500}
/>
```

Remote image:

```tsx
<Image
  src="https://example.com/image.jpg"
  alt="Example"
  width={500}
  height={500}
/>
```

Remote domains must be configured appropriately.

---

# 34. Image Fill

```tsx
<div className="relative h-64">

  <Image
    src="/hero.jpg"
    alt="Hero"
    fill
    className="object-cover"
  />

</div>
```

---

# 35. Fonts

Using `next/font`:

```tsx
import {
  Geist
} from "next/font/google";

const geist = Geist({
  subsets: ["latin"],
});
```

Apply:

```tsx
<body className={geist.className}>
  {children}
</body>
```

---

# 36. Static Assets

Put static files inside:

```text
public/
```

Example:

```text
public/
├── logo.png
├── hero.jpg
└── favicon.ico
```

Use:

```tsx
<img src="/logo.png" alt="Logo" />
```

For optimized images, prefer:

```tsx
<Image
  src="/logo.png"
  alt="Logo"
  width={200}
  height={80}
/>
```

---

# 37. CSS

Global:

```text
app/globals.css
```

CSS Module:

```text
Button.module.css
```

Use:

```tsx
import styles from "./Button.module.css";

<button className={styles.button}>
  Click
</button>
```

---

# 38. Tailwind CSS

Example:

```tsx
<div className="rounded-xl border p-6 shadow">
  <h2 className="text-2xl font-bold">
    Dashboard
  </h2>
</div>
```

Responsive:

```tsx
<div className="
  p-4
  md:p-8
  lg:p-12
">
```

---

# 39. Environment Variables

`.env.local`

```env
DATABASE_URL="postgresql://..."
API_URL="https://api.example.com"
```

Server:

```tsx
const url =
  process.env.DATABASE_URL;
```

Client-exposed variables:

```env
NEXT_PUBLIC_API_URL="..."
```

Important:

```text
NEXT_PUBLIC_*
```

variables can be exposed to browser code.

Never put private secrets in them.

---

# 40. Fetch API

Server Component:

```tsx
const response =
  await fetch(
    "https://api.example.com/users"
  );

const users =
  await response.json();
```

---

# 41. Data Fetching

Server:

```tsx
export default async function Users() {

  const response =
    await fetch(
      "https://api.example.com/users"
    );

  const users =
    await response.json();

  return (
    <div>
      {users.map((user: any) => (
        <p key={user.id}>
          {user.name}
        </p>
      ))}
    </div>
  );
}
```

Prefer proper TypeScript types instead of `any`.

---

# 42. Caching Concept

Next.js can cache and reuse data depending on the API and configuration.

Concept:

```text
Request
 ↓
Cache
 ↓
Existing data?
 ├── YES → Return cached data
 └── NO  → Fetch
```

For data that must always be fresh, use an appropriate dynamic/no-store strategy.

---

# 43. Revalidation

Time-based revalidation:

```tsx
const response = await fetch(
  "https://api.example.com/posts",
  {
    next: {
      revalidate: 60,
    },
  }
);
```

Meaning:

```text
Data can be revalidated approximately every 60 seconds.
```

---

# 44. No-Store Fetch

For always-fresh data:

```tsx
const response = await fetch(
  "https://api.example.com/orders",
  {
    cache: "no-store",
  }
);
```

Use only when the data actually needs request-time freshness.

---

# 45. Route Handlers

Create:

```text
app/api/users/route.ts
```

This gives:

```text
/api/users
```

---

# 46. GET API

```tsx
import { NextResponse } from "next/server";

export async function GET() {

  const users = [
    {
      id: 1,
      name: "Adnan",
    },
  ];

  return NextResponse.json(users);
}
```

---

# 47. POST API

```tsx
import { NextRequest, NextResponse }
  from "next/server";

export async function POST(
  request: NextRequest
) {

  const body =
    await request.json();

  return NextResponse.json(
    {
      message: "User created",
      user: body,
    },
    {
      status: 201,
    }
  );
}
```

---

# 48. PUT API

```tsx
export async function PUT(
  request: Request
) {

  const body =
    await request.json();

  return Response.json({
    message: "User updated",
    data: body,
  });
}
```

---

# 49. DELETE API

```tsx
export async function DELETE(
  request: Request
) {

  return Response.json({
    message: "User deleted",
  });
}
```

---

# 50. Dynamic API Route

Structure:

```text
app/
└── api/
    └── users/
        └── [id]/
            └── route.ts
```

Example:

```tsx
type Props = {
  params: Promise<{
    id: string;
  }>;
};

export async function GET(
  request: Request,
  { params }: Props
) {

  const { id } = await params;

  return Response.json({
    id,
  });
}
```

URL:

```text
/api/users/123
```

---

# 51. Request Headers

```tsx
export async function GET(
  request: Request
) {

  const auth =
    request.headers.get(
      "authorization"
    );

  return Response.json({
    authenticated: Boolean(auth),
  });
}
```

---

# 52. Cookies

Read:

```tsx
import { cookies } from "next/headers";

const cookieStore =
  await cookies();

const token =
  cookieStore.get("token");
```

Set cookies where supported in server-side contexts:

```tsx
const cookieStore =
  await cookies();

cookieStore.set(
  "session",
  sessionId,
  {
    httpOnly: true,
    secure: true,
    sameSite: "lax",
    path: "/",
  }
);
```

---

# 53. Authentication

Recommended high-level architecture:

```text
Login
 ↓
Validate credentials
 ↓
Create server-side session
 ↓
Secure HttpOnly cookie
 ↓
Request
 ↓
Verify session
 ↓
Authenticated User
```

Avoid exposing sensitive session credentials to client JavaScript unnecessarily.

---

# 54. Authorization

Authentication:

```text
Who are you?
```

Authorization:

```text
What are you allowed to do?
```

Example:

```tsx
if (user.role !== "admin") {
  return <Forbidden />;
}
```

Better enforce authorization on the server, not only by hiding UI.

---

# 55. JWT

Typical concept:

```text
Login
 ↓
Verify credentials
 ↓
Create JWT
 ↓
Secure storage / cookie
 ↓
Request
 ↓
Verify JWT
 ↓
User
```

JWT payload example:

```json
{
  "sub": "123",
  "role": "admin"
}
```

Never put passwords or sensitive secrets inside JWT payloads.

---

# 56. Database

Common choices:

```text
PostgreSQL
MySQL
MongoDB
SQLite
```

For your stack:

```text
Next.js
   ↓
Prisma / Drizzle
   ↓
PostgreSQL
```

---

# 57. Prisma

Install:

```bash
npm install prisma @prisma/client
```

Initialize:

```bash
npx prisma init
```

---

# 58. Prisma Schema

`prisma/schema.prisma`

```prisma
model User {

  id        Int      @id @default(autoincrement())

  name      String

  email     String   @unique

  createdAt DateTime @default(now())

}
```

---

# 59. Prisma Client

`src/lib/db.ts`

```tsx
import {
  PrismaClient
} from "@prisma/client";

const globalForPrisma =
  globalThis as unknown as {
    prisma: PrismaClient | undefined;
  };

export const db =
  globalForPrisma.prisma ??
  new PrismaClient();

if (process.env.NODE_ENV !== "production") {
  globalForPrisma.prisma = db;
}
```

---

# 60. Prisma Create

```tsx
const user =
  await db.user.create({

    data: {
      name: "Adnan",
      email: "adnan@example.com",
    },

  });
```

---

# 61. Prisma Read

```tsx
const users =
  await db.user.findMany();
```

Single:

```tsx
const user =
  await db.user.findUnique({
    where: {
      id: 1,
    },
  });
```

---

# 62. Prisma Update

```tsx
await db.user.update({

  where: {
    id: 1,
  },

  data: {
    name: "New Name",
  },

});
```

---

# 63. Prisma Delete

```tsx
await db.user.delete({

  where: {
    id: 1,
  },

});
```

---

# 64. CRUD Architecture

```text
Frontend UI
    ↓
Server Action / Route Handler
    ↓
Validation
    ↓
Service
    ↓
Repository
    ↓
Prisma
    ↓
PostgreSQL
```

---

# 65. Service Layer

```tsx
export async function getUsers() {

  return db.user.findMany({
    orderBy: {
      createdAt: "desc",
    },
  });

}
```

Page:

```tsx
const users =
  await getUsers();
```

---

# 66. Repository Layer

```tsx
export async function findUsers() {

  return db.user.findMany();

}

export async function findUserById(
  id: number
) {

  return db.user.findUnique({
    where: {
      id,
    },
  });

}
```

Repository handles database access.

Service handles business logic.

---

# 67. Zod

Install:

```bash
npm install zod
```

Schema:

```tsx
import { z } from "zod";

const userSchema = z.object({

  name:
    z.string().min(2),

  email:
    z.email(),

});
```

Validate:

```tsx
const result =
  userSchema.safeParse(data);

if (!result.success) {

  console.log(
    result.error.issues
  );

}
```

---

# 68. Server Action + Zod

```tsx
"use server";

import { z } from "zod";

const schema = z.object({

  name:
    z.string().min(2),

  email:
    z.email(),

});

export async function createUser(
  formData: FormData
) {

  const result =
    schema.safeParse({

      name:
        formData.get("name"),

      email:
        formData.get("email"),

    });

  if (!result.success) {

    return {
      success: false,
      errors: result.error.flatten(),
    };

  }

  // Database operation here

  return {
    success: true,
  };
}
```

---

# 69. React Hook Form

Install:

```bash
npm install react-hook-form
```

Example:

```tsx
"use client";

import {
  useForm
} from "react-hook-form";

type FormData = {
  name: string;
  email: string;
};

export default function UserForm() {

  const {
    register,
    handleSubmit,
  } = useForm<FormData>();

  function onSubmit(data: FormData) {
    console.log(data);
  }

  return (
    <form
      onSubmit={handleSubmit(onSubmit)}
    >

      <input
        {...register("name")}
      />

      <input
        {...register("email")}
      />

      <button type="submit">
        Save
      </button>

    </form>
  );
}
```

---

# 70. File Upload

Client:

```tsx
const formData =
  new FormData();

formData.append(
  "file",
  file
);

await fetch(
  "/api/upload",
  {
    method: "POST",
    body: formData,
  }
);
```

Server:

```tsx
export async function POST(
  request: Request
) {

  const formData =
    await request.formData();

  const file =
    formData.get("file");

  return Response.json({
    received: Boolean(file),
  });
}
```

For production, consider object storage such as S3-compatible storage rather than storing large files directly in your application server.

---

# 71. Pagination

URL:

```text
/users?page=2
```

Read search params:

```tsx
type Props = {
  searchParams: Promise<{
    page?: string;
  }>;
};

export default async function Users({
  searchParams,
}: Props) {

  const params =
    await searchParams;

  const page =
    Number(params.page ?? "1");

  return <div>Page {page}</div>;
}
```

---

# 72. Database Pagination

```tsx
const limit = 10;

const page = 2;

const users =
  await db.user.findMany({

    skip:
      (page - 1) * limit,

    take:
      limit,

  });
```

---

# 73. Search

URL:

```text
/products?q=laptop
```

```tsx
type Props = {
  searchParams: Promise<{
    q?: string;
  }>;
};

export default async function Products({
  searchParams,
}: Props) {

  const { q } =
    await searchParams;

  return (
    <h1>
      Searching for: {q}
    </h1>
  );
}
```

---

# 74. Debouncing

Client-side:

```tsx
"use client";

useEffect(() => {

  const timer =
    setTimeout(() => {

      searchProducts(query);

    }, 500);

  return () =>
    clearTimeout(timer);

}, [query]);
```

For large applications, consider server-side search plus a data-fetching/cache strategy.

---

# 75. Optimistic UI

Concept:

```text
User action
 ↓
Update UI immediately
 ↓
Server request
 ↓
Success → keep UI
Error → rollback
```

Useful for:

```text
Like
Follow
Toggle
Delete
Todo completion
```

---

# 76. Suspense

```tsx
import { Suspense } from "react";

<Suspense
  fallback={<Loading />}
>
  <UserList />
</Suspense>
```

Useful for streaming parts of UI independently.

---

# 77. Streaming

Concept:

```text
Server starts rendering
       ↓
Fast content sent
       ↓
Slow content loads
       ↓
Slow section streams later
```

Example:

```tsx
<Suspense fallback={<Loading />}>
  <SlowComponent />
</Suspense>
```

---

# 78. Parallel Routes

Advanced routing feature.

Concept:

```text
Dashboard
├── Main
├── Notifications
└── Sidebar
```

Useful for complex dashboards where multiple route segments need independent rendering/navigation.

---

# 79. Intercepting Routes

Useful for:

```text
Open product as modal
Open image as modal
Preserve current page behind modal
```

Example concept:

```text
Products
   ↓
Click Product
   ↓
Product Modal
```

while direct navigation can still show the full product page.

---

# 80. revalidatePath()

After changing data:

```tsx
import {
  revalidatePath
} from "next/cache";

revalidatePath("/users");
```

Useful when a mutation should cause a path to be regenerated/refreshed according to the configured caching model.

---

# 81. revalidateTag()

Tag related data:

```tsx
const response = await fetch(
  "https://api.example.com/users",
  {
    next: {
      tags: ["users"],
    },
  }
);
```

Later:

```tsx
import {
  revalidateTag
} from "next/cache";
```

Use tag-based invalidation when you want to refresh related cached data.

---

# 82. API Architecture

Recommended:

```text
app/
│
├── api/
│   ├── auth/
│   ├── users/
│   ├── products/
│   └── orders/
│
├── actions/
│
├── services/
│
├── repositories/
│
└── lib/
```

---

# 83. Server Action vs Route Handler

Use Server Actions when:

```text
Form mutation
Internal application mutation
Server-side action
```

Use Route Handlers when:

```text
REST API
External clients
Webhook
Mobile application
Third-party integration
API endpoint
```

---

# 84. Webhook

Example:

```text
Payment Provider
       ↓
POST /api/webhook
       ↓
Verify signature
       ↓
Process event
       ↓
Update database
```

Never trust webhook payloads without verification.

---

# 85. TypeScript API Type

```tsx
type User = {

  id: number;

  name: string;

  email: string;

};
```

API response:

```tsx
type ApiResponse<T> = {

  success: boolean;

  data: T;

  message?: string;

};
```

---

# 86. Generic API

```tsx
type UserResponse =
  ApiResponse<User>;
```

List:

```tsx
type UsersResponse =
  ApiResponse<User[]>;
```

---

# 87. Zustand

Install:

```bash
npm install zustand
```

Store:

```tsx
import { create } from "zustand";

type Store = {

  count: number;

  increment: () => void;

};

export const useStore =
  create<Store>((set) => ({

    count: 0,

    increment: () =>
      set((state) => ({
        count:
          state.count + 1,
      })),

  }));
```

Use in Client Component:

```tsx
"use client";

const count =
  useStore(state => state.count);
```

---

# 88. TanStack Query

Install:

```bash
npm install @tanstack/react-query
```

Useful for client-side server state:

```text
Fetching
Caching
Refetching
Mutations
Loading
Errors
```

Example:

```tsx
const {
  data,
  isPending,
  error,
} = useQuery({
  queryKey: ["users"],
  queryFn: getUsers,
});
```

---

# 89. Authentication Architecture

```text
                  LOGIN
                    │
                    ▼
              Login Form
                    │
                    ▼
              Server Action
                    │
                    ▼
              Validate Input
                    │
                    ▼
             Verify Password
                    │
                    ▼
              Create Session
                    │
                    ▼
           HttpOnly Secure Cookie
                    │
                    ▼
               Dashboard
                    │
                    ▼
          Server Auth Check
                    │
             ┌──────┴──────┐
             │             │
           Valid         Invalid
             │             │
             ▼             ▼
         Dashboard       Login
```

---

# 90. Password Hashing

Never store:

```text
plain password
```

Use a password hashing algorithm/library designed for password storage.

Concept:

```text
Password
   ↓
Hash
   ↓
Database
```

Login:

```text
Password
   ↓
Verify against hash
   ↓
Success / Failure
```

---

# 91. Security Checklist

```text
□ Validate all user input
□ Authorize on server
□ Hash passwords
□ Use HTTPS
□ Use secure cookies
□ Use HttpOnly cookies for sessions where appropriate
□ Configure SameSite correctly
□ Protect CSRF where applicable
□ Validate webhook signatures
□ Do not expose secrets
□ Do not trust client roles
□ Rate-limit sensitive endpoints
□ Sanitize untrusted HTML
□ Restrict file uploads
□ Validate file type and size
□ Use secure headers
□ Keep dependencies updated
```

---

# 92. Client vs Server Secret

Never:

```tsx
"use client";

const secret =
  process.env.DATABASE_PASSWORD;
```

Server-only:

```tsx
const secret =
  process.env.DATABASE_PASSWORD;
```

Keep database credentials and private API keys on the server.

---

# 93. Performance

Important techniques:

```text
Server Components
Code Splitting
Lazy Loading
Image Optimization
Font Optimization
Caching
Revalidation
Streaming
Suspense
Database indexing
Pagination
Avoid unnecessary client JS
```

---

# 94. Avoid Excessive "use client"

Bad architecture:

```text
Every component
      ↓
"use client"
```

Better:

```text
Server Page
   │
   ├── Server UI
   │
   └── Small Client Component
            │
            ├── State
            └── Events
```

Keep the client boundary as small as practical.

---

# 95. Database Performance

Use:

```text
Indexes
Pagination
Selective fields
Efficient queries
Connection pooling
Transactions
```

Avoid:

```text
Fetch thousands of rows
 ↓
Send everything to browser
 ↓
Filter in JavaScript
```

Prefer server/database filtering.

---

# 96. Error Handling

API:

```tsx
try {

  const user =
    await db.user.findUnique({
      where: { id },
    });

  if (!user) {
    return Response.json(
      {
        message: "User not found",
      },
      {
        status: 404,
      }
    );
  }

  return Response.json(user);

} catch {

  return Response.json(
    {
      message: "Internal server error",
    },
    {
      status: 500,
    }
  );

}
```

Do not leak sensitive internal errors to users.

---

# 97. Status Codes

```text
200 → OK
201 → Created
204 → No Content

400 → Bad Request
401 → Unauthenticated
403 → Forbidden
404 → Not Found
409 → Conflict
422 → Validation Error
429 → Too Many Requests

500 → Internal Server Error
```

---

# 98. Reusable UI

Create:

```text
components/ui/
│
├── Button.tsx
├── Input.tsx
├── Card.tsx
├── Modal.tsx
├── Badge.tsx
├── Table.tsx
├── Pagination.tsx
├── Spinner.tsx
└── Toast.tsx
```

---

# 99. Button

```tsx
type Props = {
  children: React.ReactNode;
  onClick?: () => void;
  type?: "button" | "submit" | "reset";
};

export default function Button({
  children,
  onClick,
  type = "button",
}: Props) {

  return (
    <button
      type={type}
      onClick={onClick}
      className="rounded-lg px-4 py-2"
    >
      {children}
    </button>
  );
}
```

---

# 100. Card

```tsx
type Props = {
  title: string;
  children: React.ReactNode;
};

export default function Card({
  title,
  children,
}: Props) {

  return (
    <div className="rounded-xl border p-6">

      <h2 className="text-xl font-bold">
        {title}
      </h2>

      <div className="mt-4">
        {children}
      </div>

    </div>
  );
}
```

---

# 101. Navbar Architecture

```text
Navbar
│
├── Logo
├── Navigation
├── Search
├── Notification
├── User Menu
└── Mobile Menu
```

Keep interactive pieces as Client Components where required.

---

# 102. Dashboard Architecture

```text
Dashboard
│
├── Sidebar
│
├── Navbar
│
└── Main
    │
    ├── Stats
    ├── Charts
    ├── Tables
    └── Recent Activity
```

---

# 103. Admin Architecture

```text
/admin
│
├── dashboard
├── users
├── products
├── orders
├── reports
└── settings
```

Authorization should be checked server-side for each protected operation.

---

# 104. Feature-Based Architecture

Large application:

```text
src/
│
├── app/
│
├── components/
│
├── features/
│   ├── auth/
│   ├── users/
│   ├── products/
│   └── orders/
│
├── actions/
├── services/
├── repositories/
├── lib/
├── hooks/
├── types/
└── config/
```

---

# 105. Complete Full-Stack Architecture

```text
                        USER
                          │
                          ▼
                    Next.js App
                          │
             ┌────────────┴────────────┐
             │                         │
         Server UI                Client UI
             │                         │
             │                    Interactions
             │                         │
             └────────────┬────────────┘
                          │
              Server Actions / APIs
                          │
                    Validation
                          │
                      Services
                          │
                    Repositories
                          │
                     Prisma/ORM
                          │
                     PostgreSQL
```

---

# 106. Next.js + Flask

Possible architecture:

```text
Next.js
    ↓
Frontend / SSR
    ↓
Flask REST API
    ↓
SQLAlchemy
    ↓
PostgreSQL
```

Next.js:

```tsx
const response =
  await fetch(
    `${process.env.API_URL}/users`
  );
```

Flask:

```python
@app.get("/users")
def users():
    return jsonify(...)
```

---

# 107. Next.js + FastAPI

```text
Next.js
    ↓
Server Component / Route Handler
    ↓
FastAPI
    ↓
Pydantic
    ↓
SQLAlchemy
    ↓
PostgreSQL
```

---

# 108. Next.js Full-Stack

Alternative:

```text
Next.js
   │
   ├── UI
   ├── Server Components
   ├── Server Actions
   ├── Route Handlers
   ├── Auth
   ├── Prisma
   └── PostgreSQL
```

This can eliminate the need for a separate Flask/FastAPI backend for many web applications.

---

# 109. When to Use Separate Backend

Separate backend can make sense when:

```text
Mobile app
Multiple frontend clients
Public API
Microservices
Heavy Python workloads
ML/AI services
Existing backend
Complex backend infrastructure
```

Architecture:

```text
Next.js
   │
   ├── Web
   │
   ▼
API Gateway / Backend
   │
   ├── Auth
   ├── Business Logic
   ├── AI Service
   └── Database
```

---

# 110. Next.js + AI Architecture

For an AI application:

```text
Next.js
   │
   ├── UI
   ├── Chat Interface
   └── API / Server Action
          │
          ▼
       AI Service
          │
     ┌────┴────┐
     │         │
    LLM      RAG
     │         │
     └────┬────┘
          │
       Database
          │
      PostgreSQL
```

Python AI service:

```text
Next.js
   ↓
FastAPI
   ↓
LangChain / PyTorch
   ↓
PostgreSQL / Vector DB
```

---

# 111. Testing

Useful tools:

```text
Vitest
Jest
React Testing Library
Playwright
```

Test:

```text
Components
Server logic
API endpoints
Forms
Authentication
Critical user flows
```

---

# 112. E2E Testing Concept

```text
Open website
 ↓
Login
 ↓
Dashboard
 ↓
Create user
 ↓
Verify user
 ↓
Logout
```

This is an end-to-end test.

---

# 113. Docker

Production concept:

```text
Next.js Source
      ↓
npm install
      ↓
npm run build
      ↓
Next.js Production Server
      ↓
Docker Container
      ↓
Cloud
```

Example Dockerfile pattern:

```dockerfile
FROM node:alpine AS deps

WORKDIR /app

COPY package*.json ./

RUN npm ci


FROM node:alpine AS builder

WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules

COPY . .

RUN npm run build


FROM node:alpine AS runner

WORKDIR /app

ENV NODE_ENV=production

COPY --from=builder /app/package.json ./
COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/node_modules ./node_modules

EXPOSE 3000

CMD ["npm", "start"]
```

---

# 114. Deployment

Common options:

```text
Vercel
Netlify
AWS
Google Cloud
Azure
Docker VPS
Cloudflare
```

Production:

```bash
npm run build
npm start
```

---

# 115. CI/CD

Typical:

```text
GitHub
   ↓
Push
   ↓
CI
   ├── Install
   ├── Lint
   ├── Test
   └── Build
   ↓
Deploy
```

---

# 116. Git Workflow

```bash
git checkout -b feature/dashboard

git add .

git commit -m "Add dashboard"

git push origin feature/dashboard
```

Merge:

```bash
git checkout main

git pull origin main

git merge feature/dashboard

git push origin main
```

---

# 117. Production Environment

Development:

```text
localhost
```

Production:

```text
yourdomain.com
```

Keep separate:

```text
.env.local
.env.production
```

Never commit secrets.

---

# 118. Recommended Project Structure

For a serious SaaS:

```text
src/
│
├── app/
│   ├── (marketing)/
│   │   ├── page.tsx
│   │   ├── pricing/
│   │   └── about/
│   │
│   ├── (auth)/
│   │   ├── login/
│   │   └── register/
│   │
│   ├── dashboard/
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   ├── users/
│   │   └── settings/
│   │
│   ├── api/
│   │   ├── auth/
│   │   ├── users/
│   │   └── webhooks/
│   │
│   ├── layout.tsx
│   ├── page.tsx
│   ├── loading.tsx
│   ├── error.tsx
│   └── not-found.tsx
│
├── components/
│   ├── ui/
│   ├── layout/
│   └── forms/
│
├── features/
│   ├── auth/
│   ├── users/
│   ├── products/
│   └── orders/
│
├── actions/
├── services/
├── repositories/
├── hooks/
├── lib/
├── types/
├── config/
└── styles/
```

---

# 119. Request Flow

Example:

```text
User clicks "Create User"
          ↓
Form
          ↓
Server Action
          ↓
Zod Validation
          ↓
Authorization
          ↓
Service
          ↓
Repository
          ↓
Prisma
          ↓
PostgreSQL
          ↓
Success
          ↓
revalidatePath()
          ↓
Updated UI
```

---

# 120. Complete Authentication Flow

```text
REGISTER
   ↓
Form
   ↓
Validation
   ↓
Check existing email
   ↓
Hash password
   ↓
Database
   ↓
Create session
   ↓
Secure cookie
   ↓
Dashboard


LOGIN
   ↓
Form
   ↓
Validation
   ↓
Find user
   ↓
Verify password
   ↓
Create session
   ↓
Secure cookie
   ↓
Dashboard


LOGOUT
   ↓
Delete/invalidate session
   ↓
Clear cookie
   ↓
Login
```

---

# 121. Complete E-Commerce Flow

```text
User
 │
 ▼
Product Page
 │
 ▼
Add to Cart
 │
 ▼
Cart State
 │
 ▼
Checkout
 │
 ▼
Server Action / API
 │
 ▼
Validate
 │
 ▼
Payment Provider
 │
 ▼
Webhook
 │
 ▼
Verify Payment
 │
 ▼
PostgreSQL
 │
 ▼
Order Created
 │
 ▼
Confirmation
```

---

# 122. Complete SaaS Flow

```text
Landing Page
     ↓
Register
     ↓
Login
     ↓
Authentication
     ↓
Dashboard
     ↓
Organization
     ↓
Projects
     ↓
Members
     ↓
Subscription
     ↓
Billing
     ↓
Analytics
```

---

# 123. Next.js Mental Model

Think:

```text
URL
 ↓
Route
 ↓
Page
 ↓
Layout
 ↓
Server Component
 ↓
Data
 ↓
Client Component
 ↓
Interaction
 ↓
Server Action / API
 ↓
Database
 ↓
Revalidation
 ↓
Updated UI
```

---

# 124. React vs Next.js Mental Model

React:

```text
Component
 ↓
State
 ↓
UI
```

Next.js:

```text
Route
 ↓
Server
 ↓
Data
 ↓
UI
 ↓
Client Interaction
 ↓
Server Mutation
 ↓
Database
 ↓
Revalidation
```

---

# 125. Next.js Golden Rules

```text
1. Server Components by default.
2. Use "use client" only where needed.
3. Keep secrets on the server.
4. Validate every untrusted input.
5. Authorize on the server.
6. Use Server Actions for appropriate internal mutations.
7. Use Route Handlers for APIs/webhooks.
8. Use proper database indexes.
9. Paginate large datasets.
10. Don't send unnecessary data to the client.
11. Use Next Image for application images.
12. Use metadata for SEO.
13. Handle loading/error/empty states.
14. Use caching deliberately.
15. Revalidate data after mutations when needed.
16. Keep business logic outside UI components.
17. Separate database access from business logic in larger apps.
18. Test critical flows.
19. Keep environment secrets out of Git.
20. Build and test production builds before deployment.
```

---

# 126. Next.js Cheat Sheet

## Create App

```bash
npx create-next-app@latest my-app
```

## Development

```bash
npm run dev
```

## Build

```bash
npm run build
```

## Production

```bash
npm start
```

## Page

```text
app/page.tsx
```

## Layout

```text
app/layout.tsx
```

## Dynamic Route

```text
app/users/[id]/page.tsx
```

## API

```text
app/api/users/route.ts
```

## Client Component

```tsx
"use client";
```

## Navigation

```tsx
import Link from "next/link";
```

## Router

```tsx
import { useRouter } from "next/navigation";
```

## Redirect

```tsx
redirect("/login");
```

## 404

```tsx
notFound();
```

## Metadata

```tsx
export const metadata = {};
```

## Image

```tsx
import Image from "next/image";
```

## Server Action

```tsx
"use server";
```

## Database

```tsx
await db.user.findMany();
```

## Revalidation

```tsx
revalidatePath("/dashboard");
```

---

# 127. Master Next.js Stack

```text
                    NEXT.JS
                       │
       ┌───────────────┼────────────────┐
       │               │                │
    App Router      React             Server
       │               │                │
       │          Components       Server Actions
       │               │                │
       ├───────────────┼────────────────┤
       │               │
    Routing         Client
       │           Components
       │               │
       └───────┬───────┘
               │
            API Layer
               │
       ┌───────┴────────┐
       │                │
 Route Handlers     External API
       │                │
       └───────┬────────┘
               │
          Business Logic
               │
            Services
               │
          Repositories
               │
            Prisma
               │
          PostgreSQL
```

---

# 128. Full Production Architecture

```text
                       INTERNET
                           │
                           ▼
                    Next.js Application
                           │
             ┌─────────────┼─────────────┐
             │             │             │
          Pages         Server         Client
             │         Components     Components
             │             │             │
             └─────────────┼─────────────┘
                           │
                  Server Actions / API
                           │
                     Authentication
                           │
                       Validation
                           │
                      Business Logic
                           │
              ┌────────────┴────────────┐
              │                         │
          PostgreSQL                External APIs
              │                         │
              ├── Users                 ├── Payment
              ├── Products              ├── Email
              ├── Orders                ├── AI
              └── Sessions              └── Storage
```

---

# 🚀 Next.js Project Formula

```text
1. Plan routes
       ↓
2. Design layouts
       ↓
3. Build Server Components
       ↓
4. Add Client Components only where needed
       ↓
5. Design database
       ↓
6. Create services/repositories
       ↓
7. Add Server Actions / APIs
       ↓
8. Add validation
       ↓
9. Add authentication
       ↓
10. Add authorization
       ↓
11. Add loading/error/empty states
       ↓
12. Add caching/revalidation
       ↓
13. Add SEO
       ↓
14. Add tests
       ↓
15. Security review
       ↓
16. Production build
       ↓
17. Deploy
```

# END
