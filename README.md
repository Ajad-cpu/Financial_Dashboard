# Financial Dashboard (React + Vite + MUI)

A responsive financial dashboard UI built with React (Vite) and Material UI.

## Quick start

Prerequisites:
- Node.js 20+ (recommended, matches Vercel defaults)
- npm (or pnpm/yarn)

Install and run:
```bash
npm install
npm run dev
```

Build and preview:
```bash
npm run build
npm run preview
```

Lint:
```bash
npm run lint
```

## Features

### Dashboard overview
- **Summary cards**: Total Balance, Income, Expenses
- **Charts**: Balance Trend (line), Spending Breakdown (pie)
- **Insights**: Highest spending category, month-over-month change, net cashflow

### Transactions (filters + export)
- Search by category/type/date/amount
- Filter by type and category
- Sort by date or amount
- Date range + amount range filtering with validation feedback
- Export filtered results as **CSV** or **JSON**

### RBAC (role-based behavior)
Use the Role selector in the top bar:
- **Viewer**: can view, filter, and export transactions
- **Admin**: can additionally **add**, **edit**, and **delete** transactions

Admin-only interactions:
- Add transaction form
- Inline row editing
- Inline delete with confirm/cancel
- Keyboard shortcuts: **Ctrl/⌘ + Enter** to save/add, **Esc** to cancel editing

### Theme
- Light/Dark mode toggle (persists in localStorage)

## Navigation / routes

- `/` — Dashboard
- `/api` — API Actions (buttons that call separate mock endpoints)

## State management approach

State is handled via a small Context + `useReducer` setup in `src/state/AppState.jsx`:
- `state`: role, theme mode, loading/error, transactions, and UI filters
- `actions`: role changes, toggling theme, CRUD for transactions, filter updates

Persisted state:
- Role, theme, filters, and transactions are stored in `localStorage` to keep UI consistent across refreshes.

Data source:
- Transactions are loaded from a mock API (`src/api/mockApi.js`) on first run.

## Project structure

- `src/App.jsx`: dashboard composition and derived metrics
- `src/components/*`: UI building blocks (cards, top bar, transactions table)
- `src/state/AppState.jsx`: app state container + persistence
- `src/api/mockApi.js`: mock data fetch
- `src/utils/*`: formatting + export helpers

## Notes / edge cases

- Filters validate date and amount ranges and show inline helper messages.
- Empty states are handled for charts and the transactions table.

