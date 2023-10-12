# Todo Tailwind Sqlite

> Based on Tutorial [You Tube Web Dev Simplified - Learn Next.js 13 With This One Project](https://youtu.be/NgayZAuTgwM?si=BuQfd5BDetNI7Max)

- See also [tutorial repo](https://github.com/WebDevSimplified/next-13-todo-list)

## Development in order of commits

```bash
047819a Initial commit from Create Next App
b916871 build: prepare app with database migration based on Todo model
860ac76 build: complete preparation app with database migration based on Todo model
b376e1a build: scaffold some pages
2bd86ad build: scaffold page navigation
a4aa77d chore: configure env file in setup
a9fd892 build: scaffold server component data fetching and creation
75dbd68 build(todo items): scaffold TodoItem component
2b5b2e7 style(TodoItem): checked state
8c6123c build(new page): scaffold New page
6809190 build(new page): scaffold server actions on New page
f732d8d style: server action form on New page
a47816d feat(Todos): implement create new todo (test in db)
aac8cba build: scaffold update checked value todo on Home page
9ddd764 feat: complete server action update to db checked value todo on Home page
fb8bf0b docs: indicate completed server actions to end tutorial
2324a73 (HEAD -> main, origin/main) fix: render new todo items in the client
```

## Note on Prisma Studio

- [Prisma Studio](https://www.prisma.io/studio)

> Available on all major platforms
>
> Run it from the command line with `npx prisma studio`

(cuz that way you always run the latest version and you don't have to be always updating all the time)

## Setup

```bash
git clone git@github.com:WebDevSimplified/next-13-todo-list.git
npx create-next-app@latest todo-tw-sqlite
cd todo-tw-sqlite/
npm i prisma -D
npx prisma init --datasource-provider sqlite
```

- prisma tells us to put `.env` in `,gitignore`
  - Copy `.env.example` to `.env` and modify as per requirements

```bash
npx prisma migrate dev --name init
victor@victorpc:todo-tw-sqlite$ tree prisma
prisma
├── dev.db
├── dev.db-journal
├── migrations
│   ├── 20230929130025_init
│   │   └── migration.sql
│   └── migration_lock.toml
└── schema.prisma
```

- We need to put the database in `.gitignore`

- [Best practice for instantiating PrismaClient with Next.js](https://www.prisma.io/docs/guides/other/troubleshooting-orm/help-articles/nextjs-prisma-client-dev-practices#solution)
  - See `src/db.ts`

## Tutorial completed

```bash
commit 9ddd764f098e35e6c95ef4f1012bad44008986d2 (HEAD -> main, origin/main)
Author: victorkane <victorkane@gmail.com>
Date:   Fri Sep 29 18:35:58 2023 -0300

    feat: complete server action update to db checked value todo on Home page

 src/app/page.tsx | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)
```

## Fix for new todo to appear immediately on TODO listing page

- fix in commit: `2324a73 (HEAD -> main, origin/main) fix: render new todo items in the client`

```bash
victor@victorpc:todo-tw-sqlite$ git diff fb8bf0b 2324a73
diff --git a/src/app/page.tsx b/src/app/page.tsx
index 2f3fb36..87b2100 100644
--- a/src/app/page.tsx
+++ b/src/app/page.tsx
@@ -2,6 +2,8 @@ import { prisma } from "@/db"
 import Link from "next/link"
 import { TodoItem } from "@/components/TodoItem"

+export const revalidate = 0
+
 function getTodos() {
   return prisma.todo.findMany()
 }
```

---

Original
This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
