# Khmer Invoice App

A React + Vite + Tailwind invoice/expense app for Cambodian small businesses,
with Khmer-first UI, USD/KHR/THB currency support, a 30-day trial, and a
hidden admin approval panel.

## Run it locally

```bash
npm install
npm run dev
```

Then open the local URL it prints (usually http://localhost:5173).

## Deploy to Vercel

**Option A — from the Vercel website (easiest):**
1. Push this folder to a GitHub repo.
2. Go to vercel.com → "Add New Project" → import that repo.
3. Vercel auto-detects Vite. Leave the defaults:
   - Build Command: `npm run build`
   - Output Directory: `dist`
4. Click Deploy.

**Option B — from your terminal:**
```bash
npm install -g vercel
vercel
```
Follow the prompts. Vercel will detect the Vite framework automatically.

## Before you give this app to real vendors — please check these

Open `src/App.jsx` and find this block near the top:

```js
const ADMIN_PIN = "2468";
const SUBSCRIPTION_PRICE_USD = 2;
const SUBSCRIPTION_PAYEE_NAME = "SOK HENG PANG · ABA Bank";
const SUBSCRIPTION_QR_IMAGE = "data:image/jpeg;base64,....";
```

- **Change `ADMIN_PIN`** to something only you know before distributing this app.
- `SUBSCRIPTION_QR_IMAGE` already contains your real ABA QR — that's expected,
  it's what vendors scan to pay their $2/month.

## Important limitation, stated plainly

This app currently saves all data (accounts, invoices, expenses, trial status)
in the browser's **localStorage** — on each person's own device only. There is
no shared server or database yet. That means:

- Each vendor's data stays on their own phone/browser. Clearing browser data,
  using a different browser, or switching devices will lose access to that data.
- The hidden Admin Panel can only see and approve **the device it's opened on**
  — it cannot remotely manage other vendors' phones.

To support many vendors for real (shared accounts, real remote billing,
data backup), the next step is connecting this app to a real backend
(e.g. Supabase or Firebase) — ask Claude to help with that when you're ready.
