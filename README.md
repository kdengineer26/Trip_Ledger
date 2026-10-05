✈️ Trip Ledger - Multi-Vendor Group Travel Coordination, Activity Opt-Ins, Split Ledger & Debt Settlement in INR (₹)

Trip Ledger is a modern, mobile-first group travel management application. It solves the complexity of group trips where different members book different hotels, rentals, flights, and excursions, and only specific members participate in specific activities.

Equipped with an AI Greedy Debt Minimization Engine, Role-Aware Razorpay & UPI Settlements, and a Gemini AI Trip Copilot, Trip Ledger turns chaotic group finances into a clear, transparent, and settled itinerary.


🌟 Key Features
👥 Swipeable Traveler Cards:

Interactive card deck with tactile swipe gestures and haptic feedback.
Instant visibility into each traveler's Paid vs. Share balance and Net Position (+ owed money, - owes money).
Tap any traveler to inspect their personalized activity breakdown and individual itinerary.

🏨 Multi-Vendor Bookings & Custom Opt-In Splits:

Track separate vendor expenses (Hotels, Tempo Travelers, Scuba Diving, Dining, Beach Clubs).
Flexible Split Models:
Equal Split: Even division across selected members.
Room/Bed Share: Weighted split for accommodation configurations.
Activity Opt-In: Only members who joined an activity pay for it.
Automated per-person share calculation and audit tags.

⚡ Greedy Debt Minimization Matrix:

Reduces complex multi-party debts (e.g. 7 different people paying for 12 activities) into the minimum possible number of peer-to-peer transfers.
Eliminates circular payments using net-balance reconciliation.

💳 Role-Aware Razorpay & UPI Payment Flow
Debtors (Who Owe Money):


Pay via UPI App: Direct deep-link (upi://pay) launching Google Pay, PhonePe, Paytm, or BHIM with prefilled payee UPI ID and amount.
Razorpay Checkout: Integrated gateway with UPI QR codes, VPA intent, and card/netbanking methods (method: ['upi', 'card', 'netbanking', 'wallet']).
Cash / Offline: Mark manual settlements.
Creditors (Who Paid Upfront & Are Owed Money):
Never shown confusing payment buttons.
Remind via UPI: Copies pre-formatted payment request with exact amount and UPI ID for WhatsApp/SMS.
Mark as Received: Reconciles and settles debt upon receiving funds.
Perspective Switcher: Switch viewpoints to view the ledger from any traveler's perspective.

🤖 Gemini AI GroupTrip Copilot
Powered by @google/genai (Gemini 2.5 Flash).
Generates smart expense audits, spending warnings, itinerary recommendations, and packing advice tailored to your group's destination.

📊 Real-Time Analytics & Budget Tracking
Live visual breakdown of expenses by category (Accommodation, Transport, Food, Activities).
Dynamic progress against the target trip budget in INR (₹).

🛠️ Tech Stack
Frontend: React 19, TypeScript, Tailwind CSS v4, Motion (Framer Motion), Recharts, Canvas-Confetti, Lucide React
Backend / API: Express 4.x, Node.js (Full-stack with Vite middleware integration)
AI / LLM: @google/genai (Google Gemini API)
Payments: Razorpay Node SDK & Razorpay Checkout.js with custom UPI blocks
Build Tool: Vite 8, TSX

🚀 Getting Started (Local Setup)

Prerequisites
Ensure you have Node.js 18.0.0 or higher (Node.js 20+ LTS recommended) installed on your system.
code
Bash
node -v
npm -v
Step 1: Clone or Extract the Project
If you downloaded the ZIP file:
Extract the folder.
In VS Code, open the folder that directly contains package.json (File > Open Folder...).
Step 2: Install Dependencies
Open your terminal in VS Code (Ctrl + </kbd> or <kbd>Cmd</kbd> + <kbd>) and run:
code
Bash
npm install
Note: If your local npm encounters peer-dependency version strictness, run:
code
Bash
npm install --legacy-peer-deps
Step 3: Configure Environment Variables
Create your local .env file by copying the provided example:
macOS / Linux / Git Bash:
code
Bash
cp .env.example .env
Windows Command Prompt / PowerShell:
code
Powershell
copy .env.example .env
Open .env and fill in your keys (optional for basic testing, required for live AI and live Razorpay payments):
code
Env

# Gemini API Key (for the AI Copilot Assistant)
GEMINI_API_KEY="your_gemini_api_key_here"

# Razorpay API Credentials (for real payments; works in test mode with mock keys)
RAZORPAY_KEY_ID="rzp_test_YOUR_KEY_ID"
RAZORPAY_KEY_SECRET="YOUR_RAZORPAY_SECRET"

# App Port (defaults to 3000)
PORT=3000
Step 4: Run the Development Server
Start the full-stack server (Express backend + Vite frontend):
code
Bash
npm run dev
Open your browser and navigate to:
👉 http://localhost:3000
📁 Project Structure
code
Text
├── src/
│   ├── components/            # UI components
│   │   ├── Header.tsx         # Trip stats, budget badge, action buttons
│   │   ├── SwipeableCardDeck.tsx # Mobile-first draggable traveler cards
│   │   ├── SettlementModal.tsx# Minimal debt matrix, role-aware Razorpay & UPI
│   │   ├── TravelerDetailModal.tsx # Traveler's personal itinerary breakdown
│   │   ├── AddBookingModal.tsx# Vendor expense logging & opt-in assignment
│   │   ├── AddTravelerModal.tsx # Add new members with UPI ID handles
│   │   ├── AiAssistantModal.tsx # Gemini AI GroupTrip copilot dialog
│   │   ├── BudgetModal.tsx    # Interactive budget goal editor
│   │   └── StatisticsView.tsx # Expense analytics & category charts
│   ├── services/
│   │   ├── razorpayService.ts # Razorpay order creation, UPI blocks & verification
│   │   └── geminiService.ts   # Gemini AI prompt orchestration & audits
│   ├── lib/
│   │   └── supabaseAdapter.ts # LocalStorage / Supabase-ready persistence layer
│   ├── data/
│   │   └── mockData.ts        # Seed data (Goa Coastal Expedition 2026)
│   ├── utils/
│   │   ├── currency.ts        # Indian Rupee (₹ INR) formatting helpers
│   │   ├── debtOptimizer.ts   # Greedy Debt Minimization algorithm
│   │   └── haptics.ts         # Mobile vibration & tactile feedback helpers
│   ├── types/
│   │   └── index.ts           # TypeScript interfaces (Trip, Participant, Booking, Debt)
│   ├── App.tsx                # Main application state and tab navigation
│   ├── index.css              # Tailwind CSS styles and theme variables
│   └── main.tsx               # React DOM entry point
├── server.ts                  # Express server with Razorpay APIs & Vite dev middleware
├── vite.config.ts             # Vite configuration with Tailwind CSS plugin & optimizeDeps
├── package.json               # Dependencies and scripts
└── .env.example               # Example environment variables


📜 Available NPM Scripts
Script	Command	Description
dev	npm run dev	Runs the full-stack server with live reloading on port 3000
build	npm run build	Compiles TypeScript and creates optimized production assets in dist/
start	npm run start	Starts the production Express server with pre-built assets
lint	npm run lint	Runs tsc --noEmit to validate all TypeScript types and syntax
clean	npm run clean	Removes build artifacts (dist and server.js)

🔧 Troubleshooting
1. Failed to resolve import "react-is" from "node_modules/.vite/deps/recharts.js"
If Recharts throws a react-is error during Vite pre-bundling:
code
Bash
npm install react-is --legacy-peer-deps
npm run dev -- --force

2. Port 3000 is already in use (EADDRINUSE)
Another process is using port 3000. Stop the running process or change the port:
code
Bash
PORT=3001 npm run dev
3. Windows PowerShell Execution of scripts is disabled
If PowerShell blocks running npm or tsx:
code
Powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
Or switch your VS Code terminal to Command Prompt (cmd) or Git Bash.


📄 License
This project is licensed under the MIT License. Feel free to customize and adapt it for your group adventures!
