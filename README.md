Quokka support for `import 'server-only'`
========================================

# Repro

!!! Run Quokka on `scratch.ts`

Get:

> This module cannot be imported from a Client Component module. It should only be used from a Server Component.

# Additional Info

'server-only' is a "marker" package used in NextJS to fail if some module gets imported from anything other than a React Server Component.

https://nextjs.org/docs/app/building-your-application/rendering/composition-patterns#keeping-server-only-code-out-of-the-client-environment

The code for the 'server-only' package is https://www.npmjs.com/package/server-only?activeTab=code

It seems to take advantage of https://nodejs.org/api/packages.html#conditional-exports

I cannot get this to work with Quokka. I tried passing the `-C react-server` to Quokka (node flag defined https://nodejs.org/api/cli.html#-c-condition---conditionscondition) but to no avail.

# This Repo Setup

1. npx create-next-app@latest
   * use default settings
2. Add 'server-only' dept
3. Create dummy `./lib/config.ts` that imports 'server-only'
4. Create `scratch.ts` to demo

---

# NextJS boilerplate below

----

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

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

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
