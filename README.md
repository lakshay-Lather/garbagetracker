# Smart Garbage Tracker (Next.js + Tailwind + MongoDB)

Full-stack garbage truck tracking and complaint management platform with:

- Login / Signup
- Role support: admin, user, driver
- Role-based dashboard
- Admin panel
- Users page
- Drivers page
- Complaint form
- User complaint history tracking
- Home / About / Contact pages
- Live truck location tracking using Google Maps API
- Admin complaint status management
- Driver route assignment and progress updates

## Tech Stack

- Next.js (App Router)
- Tailwind CSS
- MongoDB + Mongoose
- JWT auth with HTTP-only cookies
- Google Maps JavaScript API

## Setup

1. Install dependencies:

```bash
npm install
```

2. Create environment file:

```bash
cp .env.example .env.local
```

3. Fill values in `.env.local`:

- `MONGODB_URI`
- `MONGODB_DB_NAME` (e.g. `garbage_tracker`)
- `JWT_SECRET`
- `ADMIN_INVITE_CODE` (required only to create admin accounts from signup)
- `NEXT_PUBLIC_GOOGLE_MAPS_API_KEY`
- `NEXT_PUBLIC_APP_URL`

4. Run development server:

```bash
npm run dev
```

Open `http://localhost:3000`.

## Troubleshooting Auth + MongoDB

- If signup/login works but data is not visible in MongoDB Atlas, verify `MONGODB_DB_NAME` matches the database you are checking.
- Admin signup requires the exact `ADMIN_INVITE_CODE`; otherwise signup returns `Invalid admin invite code`.
- After changing `.env.local`, restart the dev server.

## Troubleshooting HMR WebSocket (LAN IP)

If you open the app using a LAN URL like `http://192.168.1.37:3000` and see:

`WebSocket connection to ... /_next/webpack-hmr ... cannot parse response`

then:

- Make sure dev server is started with `npm run dev` (this project binds to `0.0.0.0`).
- Ensure `next.config.ts` includes your LAN IP in `allowedDevOrigins`.
- Restart the dev server after any `next.config.ts` changes.

## Production Build

```bash
npm run build
npm start
```

## Free Deployment (Recommended)

Deploy on Vercel:

1. Push this project to GitHub
2. Import repository in Vercel
3. Add the same environment variables in Vercel project settings
4. Deploy

