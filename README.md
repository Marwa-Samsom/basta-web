<p align="center">
  <img src="docs/screenshots/banner.png" alt="Basta — a multi-vendor marketplace, built from scratch" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React_19-149ECA?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/TanStack_Query-FF4154?style=flat-square&logo=reactquery&logoColor=white" alt="TanStack Query">
  <img src="https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white" alt="NestJS">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Meilisearch-FF5CAA?style=flat-square&logo=meilisearch&logoColor=white" alt="Meilisearch">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" alt="Playwright">
</p>

A full multi-vendor marketplace built from scratch: a customer storefront, an independent dashboard for every vendor, and a central admin panel with a commission and settlement engine.

> [!NOTE]
> **Personal project** by Marwa Samsoum — designed, planned and built end to end.
> **This repository holds the web frontend.** The backend (API, database and business logic) lives in a private repository — available on request.
> **Status:** feature-complete and fully tested locally; not deployed yet.

## Highlights

- **86 screens** across the storefront, the vendor dashboard and the admin panel.
- **Multi-vendor cart** — one customer order is split automatically into a sub-order per vendor, each with its own shipping and status.
- **Reliable money handling** (backend)
  - All amounts are stored as integers (no floating-point rounding errors).
  - The commission rate is snapshotted on each order at purchase time (vendor rate → global rate), so later changes never rewrite the past.
  - An append-only ledger: entries are never edited or deleted; corrections are new entries.
- **Vendor data isolation** enforced in the API, not just hidden in the UI.
- **Bilingual Arabic / English** — built right-to-left first; every page, notification and email follows the user's language.
- **Arabic-aware search** (Meilisearch) that ignores hamza forms, ta marbuta / ha, alif maqsura / ya, diacritics and Arabic-Indic digits.
- **Light and dark themes**, multi-currency prices, and an installable PWA.

## Screenshots

<table>
  <tr>
    <td width="50%"><img src="docs/screenshots/cart.png" alt="Multi-vendor cart"><br><b>Multi-vendor cart</b> — one order, two shops, each with its own shipping and total.</td>
    <td width="50%"><img src="docs/screenshots/product.png" alt="Product page"><br><b>Product page</b> — shopper's currency, live stock and a direct line to the shop.</td>
  </tr>
  <tr>
    <td width="50%"><img src="docs/screenshots/home-ar.png" alt="Storefront in Arabic"><br><b>Arabic first</b> — built right-to-left from day one.</td>
    <td width="50%"><img src="docs/screenshots/home-en.png" alt="Storefront in English"><br><b>Fully bilingual</b> — one click and everything follows the language.</td>
  </tr>
</table>

## Tech stack

| Layer | Tools |
|---|---|
| **Frontend (this repo)** | Next.js 16 (App Router), React 19, TypeScript, TanStack Query, Zustand, Sentry |
| Backend *(private)* | NestJS, TypeScript, 19 domain modules (catalog, cart, checkout, orders, finance, payments, shipping, …) |
| Data *(private)* | PostgreSQL, Prisma |
| Search *(private)* | Meilisearch |
| Background jobs *(private)* | In-process schedulers over PostgreSQL (stock-reservation expiry, payment reconciliation, notification delivery) |
| Testing | Vitest (API, unit + integration), Playwright (end-to-end) |

## Quality

- **546 documented test cases**, tracked in a QA workbook.
- **~90 API test files** (unit + integration, on a dedicated test database) and **110+ end-to-end test files**.

## Planning

Before writing any code, I planned the project as if it were a real client engagement: a technical and financial proposal (scope, screens, timeline and a cost estimate — a planning exercise for my own project, not a client contract), a 12-phase execution plan with a testable exit gate per phase, architecture decision records, a data model and order/payment state machines. These live in the private repository — available on request.

## Running the frontend

Requires Node.js 22+ and a running Basta API (private).

```bash
cp .env.example .env.local   # set NEXT_PUBLIC_API_URL to the API address
npm install
npm run dev                  # http://localhost:3000
```

---

<p align="center"><b>Marwa Samsoum</b> · Full-Stack Developer · open to Full-Stack roles, remote or in the region</p>
