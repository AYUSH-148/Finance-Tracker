# 💰 PennyWise – AI-Powered Finance Tracker

PennyWise is a full-stack **personal finance intelligence platform** that helps users automate expense tracking, manage budgets, and receive AI-generated financial insights — all in one place.  
It leverages modern web technologies like **Next.js**, **Prisma**, **PostgreSQL**, **Inngest**, **Clerk**, **Arcjet**, and **Gemini API** to deliver a secure, intelligent, and scalable experience.

---

## 🚀 Features

### 🔐 Authentication & Authorization
- Secure sign-in/sign-up using **Clerk** (supports Email + OAuth).
- Role-based route protection using middleware.
- Session handling and user management handled seamlessly by Clerk.

### 📊 Expense Management
- Add, view, and categorize transactions (income & expenses).
- AI-powered **OCR bill scanning** for automatic expense detection and categorization.
- View detailed analytics with expense breakdowns and category-wise summaries.

### 💸 Budget Tracking
- Users can set budgets per account or category.
- Automated **budget alerts** every 6 hours if spending crosses 80% of the limit.
- Alerts are sent via email using `@/actions/send-email`.

### 🔁 Recurring Transactions
- Automatically process recurring income/expense entries daily using **Inngest** background jobs.
- Transaction processing and account balance updates handled inside **Prisma `$transaction`** for atomic consistency.

### 📅 Monthly Financial Reports
- **Scheduled Inngest function** runs on the 1st of every month.
- Aggregates user data and uses **Gemini API** to generate 3 friendly, AI-driven financial insights.
- Sends personalized reports via email.

### 🤖 Bot Protection & Rate Limiting
- Integrated **Arcjet** middleware for:
  - Bot detection & blocking malicious traffic.
  - Rate limiting (e.g., 5 req/hr/user).
  - Shielding against SQL injection & XSS attacks.
- Runs before Clerk auth middleware for optimal security.

### ⚙️ Performance & Caching
- **Next.js caching** with `revalidateTag` and `revalidatePath` for efficient data updates.
- Optional **Redis** caching for frequently accessed summaries.
- Uses **server components** for faster initial page loads.

---

## 🧱 Tech Stack

| Layer | Technology | Purpose |
|-------|-------------|----------|
| **Frontend** | Next.js (App Router), React, Tailwind CSS | UI & server-side rendering |
| **Authentication** | Clerk | Secure user auth & session management |
| **Database** | PostgreSQL | Relational data storage |
| **ORM** | Prisma | Type-safe database access |
| **Async Jobs** | Inngest | Cron jobs, recurring transactions, monthly reports |
| **AI Integration** | Gemini API | Financial insights generation |
| **Security** | Arcjet | Bot protection, rate limiting, threat shield |
| **Email Service** | Resend + React Email | Sending budget alerts and monthly reports |
| **Deployment** | Vercel | Serverless deployment with built-in edge caching |

---

## 🧩 Architecture Overview

