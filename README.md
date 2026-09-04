# CryptoWithFinowingsAI — Frontend

Next.js 16 app: AI chat, portfolio tracking, aur ek crypto trading terminal
(live Delta Exchange candles, EMA overlays, AI coin screener, backtesting aur
strategies).

Backend alag repo mein hai — [cryptowithfinoai](https://github.com/faiyaz950/cryptowithfinoai)
(FastAPI + Flask, ek hi service).

## Pages

| Route | Kya hai |
|---|---|
| `/` | AI chat — multi-model (Gemini / OpenAI / Claude / Groq), streaming |
| `/trade` | Crypto terminal — Markets, Screener, Backtest, Strategies |
| `/trade/strategies/[id]` | Har strategy ka apna run page — live signal + backtest |
| `/portfolio` | Holdings, P&L, allocation charts, file import |

## Local par chalao

```bash
npm install
cp .env.example .env.local
npm run dev            # http://127.0.0.1:3003
```

Backend bhi chalna chahiye, warna charts aur chat dono khaali rahenge.
Uske repo mein instructions hain; default `http://127.0.0.1:8000` par chalta hai.

## Environment variables

| Var | Kya hai |
|---|---|
| `NEXT_PUBLIC_BACKEND_URL` | Backend ka origin, bina trailing slash |
| `NEXT_PUBLIC_API_URL` | Wahi backend (AI chat routes) |
| `NEXT_PUBLIC_CRYPTO_API_URL` | Wahi backend + `/api` (trading routes) |
| `BACKEND_URL` | Server-side rewrite ke liye; browser ko expose nahi hota |

Teeno `NEXT_PUBLIC_*` ek hi backend ko point karte hain — alag services nahi
hain. Alag naam isliye hain kyunki pehle do backends the; code abhi bhi dono
padhta hai, isliye dono set karna zaroori hai.

## Deploy — Vercel

| Setting | Value |
|---|---|
| Framework Preset | Next.js (auto-detect) |
| Root Directory | **khaali chhod dein** — ye repo hi app hai |
| Build Command | default (`next build`) |

Vercel project banane ke baad Settings → Environment Variables mein wo chaar vars
daalein, sab mein deployed backend ka URL (jaise
`https://cryptowithfinoai-backend.onrender.com`).

Phir **backend** ke `FRONTEND_URL` mein is Vercel app ka URL daalna na bhoolein —
wo CORS allow-list mein jaata hai. Bina uske browser se har API call block hogi,
chahe backend bilkul theek chal raha ho.

## Note

Ye software analysis aur backtesting ke liye hai, investment advice ke liye nahi.
