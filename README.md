# FinBoard - Finance Dashboard Builder

A modern, customizable finance dashboard application built with Next.js, React, and Zustand. Connect to any financial API and create real-time widgets with drag-and-drop support.

## Deployed App
🔗 Live Demo: [Click Me!](https://v0-finance-dashboard-builder-chi.vercel.app/)

## Features
- Connect to any JSON-based financial API
- Customizable widgets: **Card / Table / Chart**
- **Drag & Drop** widget arrangement
- **Auto-refresh** with configurable intervals
- **Real-time updates** (socket-ready)
- **Dynamic JSON field selector**
- **Light / Dark theme toggle**
- Persistent dashboard using `localStorage`
- **Export / Import** dashboard configuration
- Error & loading states
- Responsive UI

---

## Quick Test APIs

| Purpose | URL |
|--------|-----|
Bitcoin Price | `https://api.coinbase.com/v2/exchange-rates?currency=BTC`
Ethereum Price | `https://api.coinbase.com/v2/exchange-rates?currency=ETH`
AAPL Stock Price | `https://finnhub.io/api/v1/quote?symbol=AAPL&token=demo`

---


## Setup

```bash
git clone https://github.com/TuShArBhArDwA/finance-dashboard-builder
cd finance-dashboard-builder
npm install
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Tech Stack

- **Framework**: Next.js 16 with App Router
- **UI Library**: ShadCN UI + Tailwind CSS v4
- **State Management**: Zustand 5
- **Drag & Drop**: dnd-kit
- **Charts**: Recharts
- **Icons**: Lucide React
- **Styling**: Tailwind CSS v4

---

## Architecture

The application follows a modular architecture using Next.js App Router, Zustand state management, and reusable widget components.  
The dashboard system is built around a real-time widget engine with persistence and drag-and-drop layout handling.

📄 **Detailed Architecture & Project Structure:**  
👉 [View PROJECT_STRUCTURE.md](./PROJECT_STRUCTURE.md)

---

## Contact

**Find me everywhere →** [link.minianon.in/tusharbhardwaj](https://link.minianon.in/tusharbhardwaj)

If my work helps you, you can support it on [GitHub Sponsors](https://github.com/sponsors/minianon) · [Buy me a chai](https://buymeachai.ezee.li/minianon).
