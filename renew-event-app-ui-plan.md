# ReNew — Employee Event & Gamification App
## UI Mockup Planning Document
**Version:** v1.0 | **Date:** April 29, 2026
**Prepared by:** EMB Global — Solution Architecture
**Client:** ReNew Power Pvt. Ltd.
**Build Target:** EMB OS Internal Development Tool

---

## 1. Branding & Design System

### 1.1 Color Tokens

| Token | Name | Hex | Usage |
|---|---|---|---|
| `--renew-dark-green` | Dark Green | `#1B5E20` | Primary buttons, headers, nav bars, active states |
| `--renew-mid-green` | Mid Green | `#2E7D32` | Hover states, card borders, section dividers |
| `--renew-light-green` | Light Green (leaf accent) | `#4CAF50` | Badges, tags, highlights, progress bars, icons |
| `--renew-pale-green` | Pale Green | `#E8F5E9` | Card backgrounds, input field fills, subtle sections |
| `--renew-white` | White | `#FFFFFF` | Main backgrounds, modal surfaces, text on dark |
| `--renew-off-white` | Off White | `#F5F9F5` | Page backgrounds, alternate row fills |
| `--renew-text-dark` | Dark Text | `#1A1A1A` | Primary body text |
| `--renew-text-muted` | Muted Text | `#616161` | Secondary labels, placeholders, captions |
| `--renew-error` | Error Red | `#D32F2F` | Validation errors, alerts |
| `--renew-warning` | Amber | `#F9A825` | Warning states, pending status |

### 1.2 Typography

| Role | Font | Weight | Size (Mobile) | Size (Web) |
|---|---|---|---|---|
| Display / Hero | Inter | 700 | 28px | 40px |
| Section Heading | Inter | 600 | 20px | 28px |
| Card Title | Inter | 600 | 16px | 18px |
| Body | Inter | 400 | 14px | 15px |
| Caption / Label | Inter | 400 | 12px | 13px |
| Button | Inter | 600 | 14px | 14px |

### 1.3 Logo Assets

| Asset | URL |
|---|---|
| SVG Logo (Official) | `https://dg4e57nn4fnta.cloudfront.net/logos/ReNew.svg` |
| PNG/WEBP Fallback | `https://i.postimg.cc/1zY4Wxm7/reneww-png.webp` |

**Logo placement rules:**
- Mobile app: Top-left of nav bar, height 28px
- Web app: Top-left of sidebar/header, height 36px
- Login/splash screen: Centered, height 56px
- Always on white or `--renew-dark-green` background only

### 1.4 Component Defaults

- **Border radius:** 12px (cards), 8px (buttons, inputs), 24px (pills/tags)
- **Shadow:** `0 2px 8px rgba(0,0,0,0.08)` for cards
- **Primary button:** `bg: #1B5E20`, `text: #FFFFFF`, border-radius: 8px
- **Secondary button:** `bg: transparent`, `border: 1.5px solid #1B5E20`, `text: #1B5E20`
- **Input fields:** `bg: #F5F9F5`, `border: 1px solid #C8E6C9`, focus border `#4CAF50`
- **Bottom nav (mobile):** White background, active icon `#1B5E20`, inactive `#9E9E9E`

---

## 2. Platform Overview

### 2.1 Surfaces

| Surface | Target Users | Priority |
|---|---|---|
| **Mobile App (iOS + Android)** | All employees attending events | P0 |
| **Web App (Responsive PWA)** | Laptop/desktop users | P0 |
| **Admin Dashboard (Web)** | Event Admin, Super Admin | P0 |

### 2.2 User Roles

| Role | Access Level | Primary Surface |
|---|---|---|
| **Employee** | Attendee features only | Mobile App (primary), Web App |
| **Event Admin** | Event management + moderation + analytics | Web App (primary), Mobile |
| **Super Admin** | Full platform access including user management | Web App only |

---

## 3. Gap Assumptions (Market-Filled)

The following open items from the discovery document have been filled using patterns from Whova, Hopin, and Slido for mockup purposes. These must be confirmed with Renew before final development.

| Gap | Assumption Applied | Source Reference |
|---|---|---|
| Floor Plan visualisation | Static zoomable PNG/SVG map with room labels and pin markers; no live navigation | Whova app floor plan pattern |
| Expected concurrency | 500 concurrent users per event | Conservative enterprise event benchmark |
| Offline write behaviour | Read-only offline; changes queue locally and sync on reconnect | Standard PWA offline-first pattern |
| Social feed visibility | All employees at the event can see all posts (no segmentation) | Hopin social wall default |
| Post-event data retention | Employee retains connections + agenda history; event feed archived (admin access only) | Whova post-event archive pattern |
| Analytics export format | Excel (.xlsx) export + on-screen dashboard; no BI API in Phase 1 | Standard event analytics default |
| RBAC matrix (admin side) | Event Admin: manage own events only; Super Admin: all events + user management | Standard SaaS admin RBAC pattern |
| Simultaneous events | One active event at a time; archived events visible in history | Phase 1 simplification assumption |
| AI matchmaking input | Name + Department + 3 interest tags + 1 goal statement (collected at first login) | LinkedIn Events / Hopin networking pattern |

---

## 4. Screen Inventory

### 4.1 Mobile App — Complete Screen List

#### AUTH & ONBOARDING (Module 1)

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-01 | Splash Screen | ReNew logo centered on dark green background, auto-redirect to SSO | All |
| M-02 | SSO Login | "Login with ReNew account" button, Okta/Azure AD redirect, no manual login | All |
| M-03 | Profile Setup — Step 1 | Auto-populated name, role, department from HRMS; user reviews and confirms | Employee |
| M-04 | Profile Setup — Step 2 | Select 3 interest tags (Energy, Strategy, Operations, HR, Finance, etc.) | Employee |
| M-05 | Profile Setup — Step 3 | Set 1 networking goal ("Looking to connect with", goal statement) | Employee |
| M-06 | Profile Setup — Complete | Confirmation screen with profile summary, "Enter Event" CTA | Employee |

#### HOME & NAVIGATION

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-07 | Home / Event Dashboard | Event banner, today's agenda preview (next 2 sessions), leaderboard snippet, quick action tiles (Networking, Feed, Q&A) | Employee |
| M-08 | Bottom Navigation Bar | 5 tabs: Home, Agenda, Network, Feed, More | Employee |

#### MODULE 2 — AI NETWORKING

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-09 | Networking Home | AI match cards (3 suggested people), "View All Matches" CTA, Meetings tab, QR scan button | Employee |
| M-10 | AI Match Card Detail | Person profile: name, role, department, shared interests, match reason ("Both interested in Sustainability"), Book Meeting CTA | Employee |
| M-11 | Meeting Scheduler | Available time slots at Networking Hubs, room assignment, confirm booking | Employee |
| M-12 | My Meetings | List of upcoming and past 1:1 meetings with status (Confirmed / Pending / Completed) | Employee |
| M-13 | QR Code Scanner | Camera view with scan overlay, success state showing scanned contact card | Employee |
| M-14 | My Connections | All scanned/connected colleagues, search by name or department | Employee |

#### MODULE 3 — LIVE ENGAGEMENT & GAMIFICATION

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-15 | Live Poll — Active | Poll question with 4 options, progress bar showing time left, tap to vote | Employee |
| M-16 | Live Poll — Results | Animated horizontal bar chart showing live vote percentages, total votes count | Employee |
| M-17 | Q&A — Attendee View | List of submitted questions sorted by upvotes, text input to submit new question, upvote button per question | Employee |
| M-18 | Knowledge Check Quiz | Question card with 4 MCQ options, timer (30 sec), point reward shown on correct answer | Employee |
| M-19 | Quiz Result | Score card, correct/incorrect breakdown, points earned, leaderboard position change | Employee |
| M-20 | Leaderboard | Ranked list with employee avatars, names, departments, point totals; current user row highlighted in light green | Employee |
| M-21 | Points & Badges | My total points, activity log (attended session +50pts, scanned booth +30pts, etc.), earned badges | Employee |

#### MODULE 4 — AGENDA & NAVIGATION

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-22 | Master Schedule | Full day view with multi-track timeline, session cards (title, speaker, room, time, track colour), filter by track | Employee |
| M-23 | Session Detail | Session title, speaker name + avatar, room, time, description, Add to My Agenda CTA, Live Poll / Q&A buttons (if session is live) | Employee |
| M-24 | My Agenda | Bookmarked sessions in chronological order, remove from agenda option | Employee |
| M-25 | Floor Plan | Zoomable static venue map, room labels (Hall A, Networking Hub 1, Breakout Room 3), pin icons for key locations | Employee |
| M-26 | Push Notification View | Notification list: session reminders, room changes, admin surprise moments ("🎉 Surprise: Free coffee at Networking Hub!") | Employee |

#### MODULE 5 — SOCIAL FEED & FEEDBACK

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-27 | Social Feed | Vertical card feed of photo posts with captions, upvote count, comment count, report button (3-dot menu) | Employee |
| M-28 | Post Creator | Camera/gallery picker, caption input (max 150 chars), post button | Employee |
| M-29 | Post Detail | Full photo, caption, upvote button, comments thread, report option | Employee |
| M-30 | Session Survey | Auto-triggered modal at session end: 5-star rating + 2 short text questions + submit | Employee |
| M-31 | Post-Event Survey | Full-screen survey form: overall rating, top session, NPS score, open feedback | Employee |

#### MORE / SETTINGS

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| M-32 | More Menu | Links: My Profile, My Connections, Help & Support, About Event, Logout | Employee |
| M-33 | My Profile | View/edit profile, interests, goal statement, photo | Employee |

---

### 4.2 Web App — Complete Screen List

The web app mirrors mobile functionality in a wider layout. Key differences: sidebar navigation instead of bottom nav, two-column layouts for content-heavy screens, agenda in calendar-style view.

#### AUTH & ONBOARDING

| Screen ID | Screen Name | Description |
|---|---|---|
| W-01 | Login Page | Centered card on pale green bg, ReNew logo, "Sign in with ReNew SSO" button |
| W-02 | Profile Setup (3-step wizard) | Same as mobile M-03 to M-06, displayed in a centered 3-step form card |

#### HOME & NAVIGATION

| Screen ID | Screen Name | Description |
|---|---|---|
| W-03 | Main Layout Shell | Left sidebar (240px): logo + nav links. Top bar: event name, notification bell, user avatar. Main content area. |
| W-04 | Home Dashboard | Hero event banner, Today's Schedule (3-column cards), Leaderboard widget (top 5), Live Activity feed widget |

#### MODULE 2 — NETWORKING (Web)

| Screen ID | Screen Name | Description |
|---|---|---|
| W-05 | Networking Home | Left: AI match cards grid (2-column). Right: My Upcoming Meetings panel |
| W-06 | Match Profile Modal | Overlay showing full profile, shared interests, match reason, Book Meeting CTA |
| W-07 | Meeting Scheduler Modal | Time slot picker, hub/room selector, confirm |
| W-08 | My Connections Page | Searchable table/grid of all connections with filter by department |

#### MODULE 3 — LIVE ENGAGEMENT (Web)

| Screen ID | Screen Name | Description |
|---|---|---|
| W-09 | Live Poll Widget | Embedded within session page: question + options + live result bar chart side-by-side |
| W-10 | Q&A Panel | Right-side panel within session page: question list + submit input + upvote |
| W-11 | Knowledge Check Quiz Page | Full-width quiz card, MCQ, timer progress bar at top |
| W-12 | Leaderboard Page | Full ranked table with search, filter by department, user's own rank highlighted |

#### MODULE 4 — AGENDA (Web)

| Screen ID | Screen Name | Description |
|---|---|---|
| W-13 | Full Schedule Page | Multi-track calendar view (columns = tracks, rows = time slots), color-coded by track |
| W-14 | Session Detail Page | Two-column: left = session info + speaker bio, right = live Q&A / poll panel |
| W-15 | My Agenda Page | Personalized timeline view with add/remove session controls |
| W-16 | Floor Plan Page | Large zoomable venue map, room legend sidebar, click room to see scheduled sessions |

#### MODULE 5 — SOCIAL & FEEDBACK (Web)

| Screen ID | Screen Name | Description |
|---|---|---|
| W-17 | Social Feed Page | Masonry photo grid (3 columns), upvote + comment on hover, post button top-right |
| W-18 | Post Detail Modal | Lightbox-style photo view, caption, comments thread |
| W-19 | Session Survey Modal | Auto-triggered on session end, same fields as mobile |
| W-20 | Post-Event Survey Page | Full-page survey form with progress indicator |

#### MODULE 6 — ADMIN DASHBOARD (Web Only)

| Screen ID | Screen Name | Description | Role |
|---|---|---|---|
| W-21 | Admin Login | Separate admin portal login (SSO, admin flag check) | Event Admin, Super Admin |
| W-22 | Admin Home | KPI cards: Total Attendees, Active Sessions, Poll Responses, Top Leaderboard Player; live activity feed | Both |
| W-23 | Event Management | Create/edit event: name, date, venue, cover image, tracks, session list | Both |
| W-24 | Session Manager | Add/edit sessions: title, speaker, track, room, time, attach quiz/poll | Event Admin |
| W-25 | Live Session Monitor | Real-time view during a live session: attendance count, poll live results, Q&A queue, moderation controls | Event Admin |
| W-26 | Q&A Moderation Panel | List of submitted questions, approve/hide controls, pin to display | Event Admin |
| W-27 | Social Feed Moderation | All posts with flag status, 1-click remove, reported post queue | Event Admin |
| W-28 | Gamification Config | Set point values per activity (session attendance, booth scan, quiz completion), configure leaderboard visibility | Super Admin |
| W-29 | Attendee Management | Upload CSV / HRMS sync, view all registered employees, manage roles | Super Admin |
| W-30 | Analytics Dashboard | Charts: session attendance over time, engagement heatmap, poll participation rate, networking connections made | Both |
| W-31 | Post-Event Export | Download .xlsx report: networking summary, session rankings, engagement metrics, survey responses | Both |
| W-32 | Audit Log | Timestamped table of all admin actions: who did what, when | Super Admin |

---

## 5. User Flows

### 5.1 Employee — Full Event Day Flow

```
App Launch → Splash (M-01)
  └─ SSO Login (M-02)
       └─ First time? → Profile Setup M-03 → M-04 → M-05 → M-06
       └─ Returning? → Home Dashboard (M-07)

Home Dashboard
  ├─ View Full Schedule → M-22 → Session Detail M-23 → Add to My Agenda
  ├─ Networking → M-09 → View Match M-10 → Book Meeting M-11
  ├─ Live Session →
  │    ├─ Live Poll M-15 → Results M-16
  │    ├─ Q&A M-17
  │    └─ Knowledge Quiz M-18 → Result M-19 → Leaderboard M-20
  ├─ Social Feed → M-27 → Post M-28 / Comment M-29
  └─ Survey (auto-triggered at session end) → M-30
       └─ Post-event → M-31
```

### 5.2 Event Admin — Event Day Flow

```
Admin Login (W-21)
  └─ Admin Home (W-22)
       ├─ Monitor Live Session (W-25)
       │    ├─ Launch / close polls
       │    ├─ Moderate Q&A (W-26)
       │    └─ Trigger push notifications
       ├─ Moderate Social Feed (W-27)
       ├─ View Live Analytics (W-30)
       └─ Export Post-Event Report (W-31)
```

---

## 6. Dummy Data Strategy

All mockup screens must use realistic dummy data. Use the following dataset for consistency across all screens.

### 6.1 Event Details

```
Event Name: ReNew Annual Leaders Connect 2026
Date: May 15–16, 2026
Venue: The Leela Ambience, Gurugram
Total Attendees: 320 employees
Tracks: Strategy & Vision | Operations & Delivery | People & Culture | Technology & Innovation
```

### 6.2 Sample Employees (for attendee lists, networking, leaderboard)

```
1. Arjun Mehta — VP Strategy | Delhi | 1,240 pts
2. Priya Sharma — Senior Manager HR | Mumbai | 1,105 pts
3. Rohan Kapoor — Lead Engineer | Gurugram | 980 pts
4. Neha Joshi — Business Analyst | Hyderabad | 870 pts
5. Amit Verma — Director Operations | Pune | 760 pts
6. Sunita Rao — Product Manager | Bangalore | 710 pts
7. Vikram Singh — Finance Controller | Delhi | 650 pts
8. Pooja Nair — CSR Lead | Chennai | 590 pts
```

### 6.3 Sample Sessions

```
Session 1: "ReNew 2030: Our Path to 50GW" | 09:00–10:00 | Main Auditorium | Track: Strategy & Vision
Session 2: "AI in Renewable Operations" | 10:30–11:30 | Hall B | Track: Technology & Innovation
Session 3: "Building High-Performance Teams" | 11:30–12:30 | Hall C | Track: People & Culture
Session 4: "Townhall: Q&A with Leadership" | 14:00–15:30 | Main Auditorium | All Tracks
Session 5: "Project Delivery Excellence Workshop" | 16:00–17:00 | Breakout Room 1 | Track: Operations & Delivery
```

### 6.4 Sample Live Poll

```
Question: "What do you think is ReNew's biggest opportunity in the next 3 years?"
Option A: Green Hydrogen — 34%
Option B: Offshore Wind — 28%
Option C: Energy Storage — 24%
Option D: Corporate PPAs — 14%
Total votes: 187
```

### 6.5 Sample Q&A Questions

```
Q1: "What is the plan for expanding into Tier-2 cities?" — 42 upvotes
Q2: "How are we addressing grid reliability for RTC projects?" — 38 upvotes
Q3: "What new roles are being created in the tech vertical?" — 29 upvotes
```

### 6.6 Sample Knowledge Quiz

```
Session: "AI in Renewable Operations"
Q: "Which ML model type is most commonly used for solar irradiance forecasting?"
A) Random Forest  B) LSTM  C) SVM  D) K-Means
Correct: B) LSTM
Points on correct answer: +100 pts
```

### 6.7 Sample AI Match

```
You: Arjun Mehta (VP Strategy)
Suggested Match: Sunita Rao (Product Manager, Bangalore)
Match Reason: "Both interested in Technology & Innovation and share a goal of cross-functional collaboration"
Confidence: 92%
```

### 6.8 Sample Social Feed Posts

```
Post 1: Photo of group at networking hub | Caption: "Great conversations at Hub 1! #LeadersConnect" | 24 upvotes
Post 2: Selfie at session | Caption: "Mindblown by the 2030 vision talk 🌱" | 18 upvotes
Post 3: Team photo | Caption: "Delhi team representing! 💚" | 31 upvotes
```

---

## 7. Module-by-Module Build Instructions for EMB OS

### Build Order (Recommended)

| Phase | Modules | Rationale |
|---|---|---|
| Phase 1 | Auth + Onboarding (M-01 to M-06, W-01 to W-02) | Foundation — all other screens depend on login |
| Phase 2 | Home + Agenda (M-07, M-22 to M-25, W-03, W-04, W-13 to W-16) | Core navigation established |
| Phase 3 | Live Engagement + Gamification (M-15 to M-21, W-09 to W-12) | Highest demo impact screens |
| Phase 4 | Networking Engine (M-09 to M-14, W-05 to W-08) | AI feature showcase |
| Phase 5 | Social Feed + Feedback (M-27 to M-31, W-17 to W-20) | Engagement layer |
| Phase 6 | Admin Dashboard (W-21 to W-32) | Final layer — data-heavy |

---

### Module 1 — Auth & Onboarding

**EMB OS Prompt Guidance:**

> Build a mobile splash screen for the ReNew employee event app.
> Logo: `https://dg4e57nn4fnta.cloudfront.net/logos/ReNew.svg` centered, height 56px.
> Background: `#1B5E20` (dark green). Tagline below logo: "Leaders Connect 2026" in white Inter 600 18px.
> Auto-redirects after 2 seconds. Subtle fade-in animation on logo.

> Build a mobile SSO login screen. White background. ReNew logo top-center. Event name "Leaders Connect 2026 | May 15–16, Gurugram" in muted text. Single primary CTA button: "Sign in with ReNew Account" in `#1B5E20`. Small text below: "Secured by ReNew IT — SSO Enabled". Bottom tagline: Powered by EMB OS.

> Build a 3-step profile setup wizard (mobile). Step 1: Show pre-filled name (Arjun Mehta), role (VP Strategy), department (Strategy), and location (Delhi) in read-only fields with light green borders. Step 2: Interest tag selector — grid of pill tags (Energy Transition, AI & Tech, People Strategy, Finance, Operations, CSR, Policy, Innovation) — user selects 3. Selected tags: `bg #1B5E20 text white`. Step 3: Goal input — single text field "What are you looking to achieve at this event?" with placeholder "e.g. Meet peers from Operations team". Progress bar at top shows step 1/2/3 in light green.

---

### Module 2 — AI Networking Engine

**EMB OS Prompt Guidance:**

> Build a mobile networking home screen. Top section: "Your AI Matches" heading with a subtitle "Based on your interests and goals". Show 3 horizontal swipeable match cards. Each card: person avatar (initials circle in light green), name, role, department, 2 shared interest tags as pills, a match confidence badge ("92% Match" in dark green), and a "Book Meeting" button. Below cards: "My Meetings" tab showing 2 upcoming meetings in a list with time, room, and person name.

> Build a mobile meeting scheduler screen. Title: "Book a Meeting". Show available time slots for May 15 in a vertical list: 10:30 AM / 11:00 AM / 12:00 PM / 2:00 PM — each as a selectable card. Below: room picker dropdown showing Networking Hub 1, Hub 2, Hub 3. Confirm button in dark green at bottom. Selected slot highlighted with light green background and dark green border.

> Build a mobile QR code scanner screen. Full-screen camera view with a square scan overlay (corners in light green). Instruction text: "Point at a colleague's QR code to connect". Success state: green checkmark animation, show contact card (name, role, dept, avatar) with "Connection Saved!" message.

---

### Module 3 — Live Engagement & Gamification

**EMB OS Prompt Guidance:**

> Build a mobile live poll screen. Full-width card with dark green header bar showing "LIVE POLL" badge. Question: "What do you think is ReNew's biggest opportunity in the next 3 years?" Four option buttons: A) Green Hydrogen B) Offshore Wind C) Energy Storage D) Corporate PPAs. Timer progress bar at top counting down from 60 seconds in light green. After vote: animate to results view showing horizontal bars with percentages (34%, 28%, 24%, 14%). Total vote count shown: "187 responses".

> Build a mobile Q&A screen for an active session. Title bar: "Townhall Q&A — Live". Show list of 3 questions sorted by upvotes. Each question card: question text, upvote icon + count (42, 38, 29), "Top Question" badge on the first item in light green. Bottom: text input "Ask a question..." with send button in dark green. Questions animate to reorder as upvotes change.

> Build a mobile leaderboard screen. Title: "Leaders Connect Leaderboard". Top 3 shown in podium style (gold/silver/bronze): 1st Arjun Mehta 1240pts, 2nd Priya Sharma 1105pts, 3rd Rohan Kapoor 980pts. Below: ranked list for positions 4–8 with avatar, name, department, points. Current user's row highlighted in `#E8F5E9` with dark green left border. Filter by department pill at top.

> Build a mobile gamification points screen. Header: "Your Points: 870 pts" with a circular progress indicator. Below: activity log list showing: "Attended Strategy Session +50pts", "Scanned Booth at Expo +30pts", "Completed AI Quiz +100pts", "Connected with 3 people +45pts". Earned badges section below: icon badges for "Early Bird", "Quiz Champion", "Networker" — greyed out unearned badges shown with lock icon.

---

### Module 4 — Agenda & Navigation

**EMB OS Prompt Guidance:**

> Build a mobile master schedule screen. Day selector tabs at top (Day 1 — May 15 | Day 2 — May 16). Below: vertical timeline with session cards. Each card shows: time, session title, speaker name, room, track colour pill (Strategy=dark green, Tech=teal, People=purple, Ops=orange). Bookmarked sessions show a filled bookmark icon in light green. Filter chips at top: All | Strategy | Tech | People | Ops.

> Build a mobile session detail screen. Hero area: track colour band at top. Session title large. Speaker avatar + name + title. Time and room with icons. Short description (2-3 lines). "Add to My Agenda" button (outlined when not added, filled dark green when added). If session is live: two action buttons appear — "Join Live Poll" and "Ask a Question" — both in light green.

> Build a mobile floor plan screen. Title: "Venue Map — The Leela Ambience". Full-width zoomable static map image (use a clean generic conference venue floor plan as placeholder). Overlay pins: Main Auditorium (red), Hall B, Hall C (blue), Networking Hub 1, Hub 2, Hub 3 (green), Breakout Room 1 (orange), Registration Desk (yellow). Tap a pin to show a tooltip: room name + current/next session. Legend at bottom showing pin color codes.

---

### Module 5 — Social Feed & Feedback

**EMB OS Prompt Guidance:**

> Build a mobile social feed screen. Title: "Event Feed". Top: "Share a moment 📸" post-creator bar (tapping opens M-28). Feed: vertical scroll of post cards. Each card: user avatar + name + time ago. Photo (16:9 ratio placeholder). Caption text. Row: upvote icon + count, comment icon + count, 3-dot menu (Report). Use dummy posts: "Great conversations at Hub 1! #LeadersConnect — 24 upvotes", "Mindblown by the 2030 vision talk 🌱 — 18 upvotes", "Delhi team representing! 💚 — 31 upvotes".

> Build a mobile session survey modal. Triggered at end of session. Overlay modal (bottom sheet). Title: "How was this session?" Session name below. 5-star rating row. Two short text inputs: "What was the key takeaway?" and "Any suggestions for the speaker?". Submit button in dark green. Skip link in muted text.

---

### Module 6 — Admin Dashboard

**EMB OS Prompt Guidance:**

> Build a web admin dashboard home screen. Left sidebar 240px: ReNew logo top, nav links (Home, Events, Sessions, Attendees, Analytics, Feed Moderation, Audit Log). Top bar: "Leaders Connect 2026 — LIVE" status badge in light green, notification bell, admin avatar. Main content: 4 KPI cards (Total Registered: 320, Currently Active: 247, Poll Responses Today: 183, Top Scorer: Arjun Mehta 1240pts). Below: Live Activity Feed showing real-time events ("Priya Sharma joined Hall B", "42 votes on current poll", "New Q&A question upvoted 38 times").

> Build a web live session monitor screen. Title: "Session Monitor — AI in Renewable Operations (LIVE)". Split layout: Left 60% — attendance counter (live updating), poll launch controls (create poll button, active poll results live bar chart). Right 40% — Q&A moderation panel: list of questions with Approve / Hide / Pin controls. Bottom bar: "Send Push Notification" input for admin surprise moments.

> Build a web analytics dashboard page. Title: "Post-Event Analytics". KPI row: Total Connections Made: 412, Avg Session Attendance: 78%, Poll Participation Rate: 63%, NPS Score: 72. Below: 3 charts side-by-side — Session Attendance Bar Chart (5 sessions, attendance numbers), Engagement Heatmap (time of day vs activity intensity, green gradient), Networking Connections by Department (horizontal bar chart). Bottom: "Download Full Report (.xlsx)" button.

---

## 8. Screen Priority Matrix

| Priority | Screens | Reason |
|---|---|---|
| **P0 — Must Have for Demo** | M-01, M-02, M-07, M-15, M-16, M-17, M-20, M-22, M-23, M-27, W-04, W-22, W-25, W-30 | Core demo narrative — login → agenda → live session → gamification → admin view |
| **P1 — High Value** | M-09, M-10, M-11, M-18, M-19, M-21, M-25, M-28, W-05, W-13, W-27, W-31 | Differentiating features — AI networking, quiz, floor plan, moderation |
| **P2 — Complete Coverage** | All remaining screens | Full scope coverage for handoff |

---

## 9. Notes for EMB OS Build

1. **All screens are HTML mockups** with dummy data hardcoded — no API calls needed at this stage.
2. **Mobile screens** should be built at 390px width (iPhone 14 standard) inside a phone frame wrapper.
3. **Web screens** should be built at 1440px width full layout.
4. **Animations to include:** poll bar chart animated fill, leaderboard live update pulse, point counter increment, QR scan success animation.
5. **Interactive states to show:** button hover, active tab selection, bookmark toggle, poll option selected state, tag pill selected/unselected.
6. **Do not build:** SSO actual authentication, real-time WebSocket data, actual QR camera access — all dummy/simulated.
7. **Logo must appear** on every screen either in nav bar or splash.
8. **Consistent bottom nav** on all mobile screens: Home | Agenda | Network | Feed | More — with active state shown for the current screen.
9. **Admin dashboard** must use sidebar nav, not bottom nav.
10. **Color consistency:** Never use a green outside the defined palette. All greens must be from the 5 defined tokens.

---

*Document prepared by EMB Global Solution Architecture Team*
*For internal use — ReNew Leaders Connect 2026 App Mockup Sprint*
