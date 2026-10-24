![PROTO / 1D — bespoke brushed-metal project artwork](./assets/readme-metal-hero.svg)

# PROTO / 1D

**An API-driven device-operations interface for fleet overview, status review, and operator commands.**

Proto / 1D is a React/TypeScript frontend organised around a dashboard and device-detail workflow. The dashboard requests summary statistics, charts, device records, and activity from an API through `src/lib/api.ts` and `src/hooks/useDevices.ts`. The client can attach bearer and tenant headers from browser storage and expects backend routes for device lists, detail, statistics, commands, and token refresh.

## Request path

```text
Protected dashboard / device page
             │
             ▼
React Query hooks
             │
             ▼
Axios API client (VITE_API_URL or /api)
             │
             ├──► Device inventory and detail
             ├──► Dashboard statistics
             └──► Device command endpoint
                       │
                       ▼
             Backend + device integration
```

## What is in this repository

- **Dashboard:** Summary cards, chart panels, device table, and activity feed.
- **Device detail:** A route for inspecting one device and presenting available actions.
- **Operator interface:** Sidebar, navigation, notifications, and command controls.
- **Account screens:** Login, registration, password reset, and protected dashboard routes.
- **API boundary:** Query/mutation hooks talk to an expected backend rather than embedding an assumed device service in the UI.

## Stack

React · TypeScript · Vite · React Router · TanStack Query · Axios · Framer Motion · Recharts

## Run locally

**Requirements:** Node.js and npm.

```bash
git clone https://github.com/Kishordiu/proto-1domarbabu.git
cd proto-1domarbabu
npm ci
```

Set `VITE_API_URL` to the backend base URL in a local `.env` file when the API is hosted separately. Without a matching API, dashboard queries and commands will not return operational data.

```bash
npm run dev
npm run lint
npm test
npm run build
```

## API and security boundary

This repository is the frontend. Sending a command request from the browser is not evidence that a physical device performed it. The backend must validate the token, user role, tenant boundary, target-device permission, command type, and replay/idempotency behaviour. Do not rely on localStorage-stored tokens or a client-supplied tenant header as a security boundary without server-side validation.

---

<p align="center"><sub>DIU FOUNDRY · DEVICE OPERATIONS / INTERFACE PROTOTYPING</sub></p>
