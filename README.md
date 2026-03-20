🥛 Milk Tracker — Buyer & Seller Apps
A complete browser-based milk tracking system with two separate apps that sync with each other in real-time via a shared localStorage bridge.
📁 Files
File
Description
milk-buyer.html
Buyer dashboard — manage multiple sellers, log entries, track payments
milk-seller.html
Seller portal — profile page, log deliveries, track received payments
milk-tracker.html
Standalone single-user milk tracker (original version)
milk-integration.html
Full data flow documentation between buyer & seller apps
🚀 Getting Started
No installation or server needed. All files are plain HTML — just open in any modern browser.
Option 1 — Open directly
Double-click any .html file to open it in your browser.
Option 2 — Use GitHub Pages
Go to your repo → Settings → Pages
Set Source to main branch → / (root)
Access your apps at:
https://<your-username>.github.io/<repo-name>/milk-buyer.html
https://<your-username>.github.io/<repo-name>/milk-seller.html
⚠️ Important: Both apps must be open in the same browser on the same device for the localStorage sync to work.
🛒 Milk Buyer App
Features:
Add multiple milk sellers with name, unique ID, phone & avatar color
Log morning ☀️ and evening 🌙 milk quantity per seller daily
Set global price (₹) and unit (Litre or Kg)
View per-seller stats: morning qty, evening qty, monthly total, bill
Payment tracker per seller — record payments, view balance due
Aggregated dashboard stats across all sellers
Live sync button to push/pull data from seller apps
🥛 Milk Seller App
Features:
Profile hero banner at top showing seller name & ID
First-time setup modal (name + Seller ID must match buyer's registration)
Auto-syncs price & unit from buyer app every 5 seconds
Log morning/evening deliveries independently
Track payments received
Sync status indicator — shows "✓ Buyer connected" when ID matches
🔗 Integration Data Flow
Both apps communicate via a shared localStorage key called milkSharedData.
Buyer App  ──writes──▶  milkSharedData  ◀──reads/writes──  Seller App
How to connect them:
Open milk-buyer.html — set price & unit, click "Add New Seller", enter ID e.g. SEL-001
Open milk-seller.html in another tab — enter same Seller ID SEL-001 in setup
Seller app shows "✓ Buyer connected · ID matched"
Both apps now share entries and payments via the integration layer
localStorage Keys
Key
App
Purpose
buyerSellers
Buyer
List of registered sellers
buyerEntries
Buyer
Milk entries keyed by seller ID
buyerPayments
Buyer
Payments keyed by seller ID
sellerProfile
Seller
Seller's name, ID, phone
sellerEntries
Seller
Seller's own delivery log
sellerPayments
Seller
Seller's received payments
milkSharedData
Both
Integration bridge — syncs between apps
📊 Data Schema
// Milk Entry
{
  "id": 1700000000000,
  "date": "2025-03-18",
  "qty": 1.5,
  "session": "morning",
  "price": 60,
  "unit": "L"
}

// Payment
{
  "id": 1700000000001,
  "date": "2025-03-18",
  "amount": 500,
  "note": "UPI"
}
🛠 Tech Stack
Pure HTML, CSS, JavaScript — zero dependencies
Google Fonts (Sora, Nunito, JetBrains Mono, Playfair Display, DM Mono)
localStorage for data persistence and cross-app sync
No backend, no build step, no npm
📸 Features Summary
Feature
Buyer
Seller
Morning & Evening entries
✅
✅
Litre & Kg units
✅
✅
Payment tracking
✅
✅
Multiple sellers
✅
—
Profile display (name + ID)
—
✅
Cross-app sync
✅
✅
Monthly stats
✅
✅
Balance due tracking
✅
✅
