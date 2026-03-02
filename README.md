# DemandNest — B2B Creator Marketplace

A full-stack B2B marketplace platform that connects **brands** with **content creators** for collaborative campaigns, content production, and partnerships. Built with Next.js 15 and React 19.

---

## Overview

DemandNest is a two-sided marketplace with distinct experiences for two user types:

- **Creators** — discover brand campaigns, create content with built-in tools, manage their portfolio, schedule posts, and get paid
- **Brands** — post campaigns, manage products, discover and hire creators, review submitted content, and track performance

---

## Features

### Authentication & Onboarding
- Email/password registration and login
- Google OAuth and LinkedIn OAuth
- Email verification flow
- Multi-step profile setup (avatar, bio, social links, tags, category)

### Creator Experience
- **Dashboard** — portfolio sections: services, partnerships, featured work, testimonials, and stats
- **Campaign Discovery** — browse and filter brand campaigns by category, budget, and engagement
- **Post Maker** — rich text editor with formatting toolbar, draft saving, multi-platform targeting, and image uploads
- **Carousel Maker** — design image carousels using pre-built templates
- **Content Calendar** — schedule and manage posts via FullCalendar
- **Storefront** — public-facing creator profile page
- **Inbox** — real-time messaging with brands via Socket.io

### Brand Experience
- **Dashboard** — campaign management, product catalog, and partnership tracking
- **Campaign Management** — create, edit, and monitor campaigns with submission tracking
- **Creator Discovery** — search and filter creators by tags, location, and category
- **Brand Discovery** — browse other brands by industry and location
- **Product Management** — add/edit products with multi-image and resource uploads
- **Creator Payments** — pay creators directly via Razorpay integration
- **Analytics** — performance charts and engagement tracking

### Real-Time Features
- Live messaging (Socket.io)
- Real-time notifications
- Unread message counter in navigation

---

## Tech Stack

| Category | Technology |
|---|---|
| Framework | Next.js 15 (App Router) |
| Language | TypeScript 5.8 |
| UI Library | React 19 |
| Component Library | Ant Design 5 |
| Styling | Tailwind CSS 3 |
| Forms | React Hook Form + Zod |
| HTTP Client | Axios (with interceptors) |
| Real-Time | Socket.io Client |
| Charts | Recharts |
| Calendar | FullCalendar, Schedule-X |
| Animation | Framer Motion |
| File Uploads | React Dropzone |
| Auth | Google OAuth (@react-oauth/google), LinkedIn OAuth |
| Payments | Razorpay |
| Icons | Lucide React, Heroicons, React Icons |
| Notifications | Sonner |
| Date Handling | Day.js, Moment.js |

---

## Project Structure

```
src/
├── app/                            # Next.js App Router
│   ├── (auth routes)               # login, signup, verify-email, forgot-password
│   ├── auth/                       # OAuth callbacks (Google, LinkedIn)
│   ├── profile-setup/              # Onboarding flow
│   ├── dashboard/                  # Main protected dashboard
│   │   ├── campaigns/              # Campaign listing & details
│   │   ├── post-maker/             # Post creation tool
│   │   ├── carousel-maker/         # Carousel design tool
│   │   ├── calendar/               # Content scheduling
│   │   ├── inbox/                  # Real-time messaging
│   │   ├── brands/                 # Brand discovery
│   │   ├── creators/               # Creator discovery
│   │   ├── store-front/            # User public profile
│   │   ├── user-preview/[id]       # Creator profile view
│   │   ├── brand-preview/[id]      # Brand profile view
│   │   └── pay-creator/[id]        # Payment page
│   └── brand-dashboard/            # Brand-specific routes
├── components/
│   ├── Auth/                       # Login & signup forms
│   ├── Dashboard/                  # Creator & brand dashboards, editor, modals
│   ├── PostMaker/                  # Post editor components
│   ├── BrandTables/                # Data tables for brand views
│   ├── Charts/                     # Bar chart components
│   └── ui/                         # Shared UI primitives
├── utils/
│   ├── axiosInstance.js            # Axios with auth interceptors
│   ├── catchErrors.js              # Error handling
│   └── withAuth.tsx                # Auth guard HOC
└── lib/
    └── utils.ts                    # Class name utility
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/omar-dakalbab/b2bcreatormarketplace.git
cd b2bcreatormarketplace

# Install dependencies
npm install
```

### Environment Variables

Create a `.env.local` file in the root:

```env
NEXT_PUBLIC_SERVER_URL=your_api_base_url
NEXT_PUBLIC_GOOGLE_CLIENT_ID=your_google_client_id
NEXT_PUBLIC_LINKEDIN_CLIENT_ID=your_linkedin_client_id
NEXT_PUBLIC_DOMAIN=your_frontend_domain
NEXT_PUBLIC_RAZORPAY_KEY_ID=your_razorpay_key
```

### Running the App

```bash
# Development
npm run dev

# Production build
npm run build
npm start
```

---

## Architecture Notes

- **Routing** — Next.js App Router with file-based pages and dynamic segments (`[id]`)
- **Auth flow** — JWT tokens stored in localStorage, injected into every request via Axios interceptors; auto-logout on 401
- **Role-based UI** — dashboard page conditionally renders `<CreatorDashboard>` or `<BrandDashboard>` based on `userType` from localStorage
- **Protected routes** — `withAuth` HOC wraps all dashboard pages
- **Real-time** — Socket.io connects on dashboard mount for live notifications and messages

---

## License

This project is licensed under the MIT License.
