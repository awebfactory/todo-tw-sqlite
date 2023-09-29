# Todo Tailwind Sqlite

> Based on Tutorial [You Tube Web Dev Simplified - Learn Next.js 13 With This One Project](https://youtu.be/NgayZAuTgwM?si=BuQfd5BDetNI7Max)

- See also [tutorial repo](https://github.com/WebDevSimplified/next-13-todo-list)

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
