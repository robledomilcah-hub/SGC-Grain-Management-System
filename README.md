# SGC Grain Management System

A beginner-friendly front-end prototype for the INTE 351 Systems Analysis and Design laboratory activity.

## How to run
1. Download and extract the ZIP file.
2. Open the `SGC_Management_System` folder in Visual Studio Code.
3. Open `index.html` in a browser, or use the VS Code Live Server extension.
4. Use the sidebar to test Dashboard, Record Delivery, Inventory, Buyer Orders, and Reports.

## Demo data
- Farmers: F001 Maria Santos, F002 Juan Dela Cruz, F003 Ana Reyes
- Starting inventory: Rice 2,500 kg; Corn 1,800 kg; Wheat 900 kg

## Main functions
- Save farmer deliveries and automatically increase stock.
- Check stock before confirming buyer orders.
- Reject orders that exceed available stock.
- Automatically deduct stock after a confirmed order.
- Generate and print buyer confirmation receipts.
- View a basic activity report.

## Files
- `index.html` — page structure
- `style.css` — responsive soft pink/lavender design
- `script.js` — prototype logic and browser local storage
- `Discovery_Log.md` — Phase 1 discovery and collaboration log
- `Analytical_Reflection.md` — 300–400 word reflection

## Important limitation
This is a front-end demonstration. It uses browser local storage and does not include a server, shared database, authentication, or SMS integration. Data is saved only in the browser where it was entered.
