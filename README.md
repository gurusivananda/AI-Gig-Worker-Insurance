# 🚀 GigShield — AI-Powered Parametric Income Insurance for India's Gig Economy

> **Guidewire DEVTrails 2026 | University Hackathon**
> Phase 1: Ideation & Foundation

---

## 📌 Table of Contents

1. [Executive Summary](#executive-summary)
2. [Chosen Persona](#chosen-persona)
3. [Problem Deep Dive](#problem-deep-dive)
4. [Persona-Based Scenarios & Workflow](#persona-based-scenarios--workflow)
5. [Weekly Premium Model](#weekly-premium-model)
6. [Parametric Triggers](#parametric-triggers)
7. [Platform Choice: Web vs Mobile](#platform-choice-web-vs-mobile)
8. [AI/ML Integration Plan](#aiml-integration-plan)
9. [Fraud Detection Architecture](#fraud-detection-architecture)
10. [Tech Stack](#tech-stack)
11. [System Architecture](#system-architecture)
12. [Development Plan (6-Week Roadmap)](#development-plan-6-week-roadmap)
13. [Business Viability](#business-viability)
14. [Team](#team)

---

## Executive Summary

**GigShield** is an AI-powered parametric income insurance platform built exclusively for **Food Delivery Partners** on platforms like Zomato and Swiggy. When an external disruption — extreme rain, heat wave, local curfew, or severe pollution — prevents a delivery partner from working, GigShield automatically detects the event, validates the claim, and instantly transfers lost wages to the worker's UPI account — **with zero manual intervention**.

> We are not selling insurance. We are selling peace of mind for ₹49/week.

**Coverage Scope:** Income loss due to external, environmental and social disruptions **only**.
**Strictly Excluded:** Health, life, accident, vehicle repair payouts.

---

## Chosen Persona

### 🛵 Food Delivery Partner (Zomato / Swiggy)

| Attribute | Detail |
|-----------|--------|
| **Platforms** | Zomato, Swiggy |
| **Work Pattern** | 8–12 hours/day, 6–7 days/week |
| **Avg. Weekly Earnings** | ₹3,000 – ₹6,000 |
| **Key Risk** | Outdoor exposure to weather, traffic disruptions, zone-level curfews |
| **Payment Preference** | UPI / Direct Bank Transfer |
| **Digital Literacy** | Moderate; comfortable with mobile apps |
| **Language** | Hindi, Telugu, Tamil, Kannada (regional-first UX) |

**Why Food Delivery?**
- Largest gig worker segment in India (~5 million+ active partners)
- Highest outdoor exposure — directly impacted by rain, heat, pollution, and civic disruptions
- Earnings are extremely volatile and tied to order volume, which collapses during disruptions
- Weekly payout cycle aligns perfectly with weekly premium model

---

## Problem Deep Dive

Food delivery partners in India face an invisible financial crisis:

- A heavy rainfall event (≥ 20mm/hour) can halt deliveries for an entire day, wiping out ₹600–₹1,000 in daily earnings
- Severe pollution days (AQI > 400) in cities like Delhi force platforms to reduce active orders
- Unexpected local curfews or bandhs freeze entire zones without warning
- **There is currently no financial product that protects these workers against income loss from such events**

Traditional insurance products fail this segment because:
1. Monthly premiums are unaffordable and misaligned with weekly earnings
2. Claims require documentation, paperwork, and waiting periods
3. Products cover health/vehicle — not income disruption from weather

---

## Persona-Based Scenarios & Workflow

### Scenario 1: Heavy Rain Event — Ravi (Swiggy Partner, Hyderabad)

> *Ravi works 10 hours a day and earns ~₹700/day. On a Tuesday afternoon, the IMD issues a red alert for heavy rainfall in his zone. Swiggy reduces active delivery slots by 60%. Ravi can only complete 3 deliveries instead of his usual 18.*

**GigShield Flow:**
1. **Real-time Weather API** detects rainfall ≥ 25mm/hour in Ravi's registered zone
2. System cross-references Ravi's active policy — confirms he's covered for the current week
3. AI engine validates the disruption is genuine (not a duplicate, not in excluded zone)
4. Parametric trigger fires automatically — no claim submission needed
5. Ravi receives a UPI notification: *"GigShield payout of ₹420 credited for disruption on 14 March"*
6. Fraud check runs in background — GPS activity cross-validated with weather data

---

### Scenario 2: Civic Curfew — Meena (Zomato Partner, Bengaluru)

> *A sudden political protest leads to Section 144 being imposed in Meena's delivery zone from 2 PM to 8 PM. She loses 6 hours of potential earnings (~₹360).*

**GigShield Flow:**
1. **Civic Alert API / News API** detects Section 144 in Koramangala zone
2. System identifies all active policy holders in the affected pin codes
3. Disruption validated against government notice timestamp
4. Automated payout calculated based on average hourly earning profile
5. Transfer initiated via mock UPI gateway

---

### Scenario 3: Extreme Heat — Arjun (Amazon Flex Partner, Delhi)

> *IMD issues an orange alert for heat wave (45°C+). The DDMA advises against outdoor work. Arjun cannot safely complete deliveries for 5 hours.*

**GigShield Flow:**
1. Temperature API detects heat index > 43°C sustained for > 3 hours
2. Corroborated with DDMA advisory scraper
3. Payout for lost income hours calculated and triggered

---

### Application Workflow (End-to-End)

```
┌─────────────────────────────────────────────────────────────────────┐
│                        WORKER ONBOARDING                            │
│  Sign Up → KYC (Aadhaar/DL) → Link Platform Account → Zone Setup   │
└───────────────────────────┬─────────────────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────────────────┐
│                      RISK PROFILING (AI)                            │
│  Zone Risk Score + Historical Disruption Data + Earnings Pattern    │
└───────────────────────────┬─────────────────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────────────────┐
│                    POLICY SELECTION & PAYMENT                       │
│  Choose Weekly Plan (Basic / Standard / Premium) → Pay ₹29-₹79/wk  │
└───────────────────────────┬─────────────────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────────────────┐
│                   REAL-TIME DISRUPTION MONITORING                   │
│  Weather APIs + Civic APIs + AQI APIs → Zone-level event detection  │
└───────────────────────────┬─────────────────────────────────────────┘
                            │
          ┌─────────────────▼──────────────────┐
          │   Disruption Threshold Breached?    │
          └──────┬──────────────────────┬───────┘
                 │ YES                  │ NO
    ┌────────────▼──────────┐     ┌─────▼────────────────┐
    │  Fraud Validation AI  │     │  Continue Monitoring  │
    └────────────┬──────────┘     └──────────────────────┘
                 │
    ┌────────────▼──────────┐
    │  Auto Claim Generated  │
    │  Payout Calculated     │
    └────────────┬──────────┘
                 │
    ┌────────────▼──────────┐
    │  UPI Payout Initiated  │
    │  Worker Notified       │
    └───────────────────────┘
```

---

## Weekly Premium Model

### Why Weekly?

Gig workers are paid weekly by platforms (Zomato pays every Monday; Swiggy settles weekly). A weekly insurance premium fits naturally into this cycle — the worker simply allocates a fraction of their weekly settlement to protection.

### Premium Tiers

| Plan | Weekly Premium | Coverage per Disruption Day | Max Weekly Payout | Triggers Covered |
|------|---------------|----------------------------|-------------------|-----------------|
| **Basic** | ₹29 | ₹200 | ₹600 (3 days) | Rain, Flood |
| **Standard** | ₹49 | ₹350 | ₹1,050 (3 days) | Rain, Flood, Heat, AQI |
| **Premium** | ₹79 | ₹500 | ₹2,000 (4 days) | All triggers incl. Curfew, Strike |

### Dynamic Pricing Logic (AI-Adjusted Weekly)

The base premium is dynamically adjusted each week using the following formula:

```
Weekly Premium = Base Rate × Zone Risk Multiplier × Season Factor × Claim History Factor

Where:
  Base Rate          = Plan base (₹29 / ₹49 / ₹79)
  Zone Risk Mult.    = 0.8 (low risk zone) to 1.3 (flood-prone / high AQI zone)
  Season Factor      = 1.0 (normal) to 1.4 (monsoon season, Jun–Sep)
  Claim History      = 0.9 (no claims in past 4 weeks) to 1.1 (frequent claimant)
```

**Example:** A Standard plan worker in a flood-prone Hyderabad zone during monsoon:
`₹49 × 1.3 × 1.3 × 1.0 = ₹82.81/week`

Workers with clean claim histories are **rewarded with lower premiums**, incentivizing honest reporting.

### Payout Calculation

```
Daily Payout = (Worker's Avg Daily Earnings) × Coverage Ratio × Disruption Hours Factor

Where:
  Avg Daily Earnings  = Derived from onboarding + platform data (mocked)
  Coverage Ratio      = 70% (Basic) / 80% (Standard) / 90% (Premium)
  Disruption Hours    = Verified hours of disruption in worker's zone
```

---

## Parametric Triggers

Unlike traditional insurance (claim → investigate → approve → pay), **parametric insurance pays automatically when a pre-defined objective threshold is crossed**. No subjectivity. No paperwork.

### Trigger Definitions

| Trigger ID | Event | Threshold | Data Source | Payout |
|------------|-------|-----------|-------------|--------|
| **T-01** | Heavy Rainfall | ≥ 20mm/hr sustained for ≥ 2 hours | OpenWeatherMap API | Per hour lost |
| **T-02** | Extreme Heat | Temperature ≥ 43°C + Heat Index advisory | IMD / WeatherAPI | Per hour lost |
| **T-03** | Severe Air Pollution | AQI ≥ 400 (Severe+) for ≥ 4 hours | CPCB AQI API / OpenAQ | Flat daily rate |
| **T-04** | Flooding / Waterlogging | IMD Red Alert + zone-level flood report | IMD API + mock civic feed | Per day |
| **T-05** | Civic Disruption | Curfew / Section 144 in worker's zone | Mock civic alert API / news scraper | Per hour |

### Trigger Validation Chain

```
Raw API Signal
    │
    ▼
Threshold Check (Is the value above trigger threshold?)
    │
    ▼
Duration Check (Has it persisted for minimum time?)
    │
    ▼
Zone Match (Is worker's registered zone affected?)
    │
    ▼
Policy Active Check (Is the worker's weekly policy valid?)
    │
    ▼
Fraud Score Check (Is worker's fraud score below limit?)
    │
    ▼
AUTO-TRIGGER PAYOUT ✅
```

---

## Platform Choice: Web vs Mobile

### Decision: **Progressive Web App (PWA) — Mobile-First Web**

| Factor | Rationale |
|--------|-----------|
| **Target users are mobile-first** | Delivery partners use Android phones almost exclusively |
| **No app store dependency** | PWA can be installed from browser — no Google Play approval required |
| **Low-bandwidth optimized** | PWA works offline and on 2G/3G networks common in Tier 2/3 cities |
| **Admin dashboard on Web** | Insurance admin/insurer dashboard is desktop-web for rich analytics |
| **Faster iteration** | Single codebase for both mobile and web |

The **worker-facing interface** is a mobile-first PWA (React + Tailwind).
The **admin/insurer dashboard** is a full desktop web application.

**Regional Language Support:** Hindi, Telugu, Kannada, Tamil via i18n (react-i18next)

---

## AI/ML Integration Plan

### 1. Dynamic Premium Calculation (ML Model)

**Approach:** Gradient Boosted Decision Tree (XGBoost) trained on:
- Historical weather data for Indian cities (IMD historical data)
- Zone-level flood/disruption frequency
- Claim payout frequency per zone per season

**Output:** Zone Risk Score (0.8 – 1.3 multiplier) recalculated weekly

**Tool:** Python (scikit-learn / XGBoost) → served via FastAPI endpoint

---

### 2. Risk Profiling at Onboarding

**Approach:** Rule-based + lightweight ML scoring at worker registration

**Features Used:**
- City / Zone (flood risk, heat risk, AQI history)
- Platform (Zomato / Swiggy — order density differences)
- Avg. daily hours worked (self-reported, validated against platform mock data)
- Historical disruption frequency for their pin code

**Output:** Initial Risk Tier (Low / Medium / High) → determines base premium bracket

---

### 3. Intelligent Fraud Detection (Anomaly Detection)

**Approach:** Isolation Forest + Rule-based checks

**What it detects:**
- GPS location mismatch: worker's GPS during claimed disruption period shows movement inconsistent with being grounded
- Claim timing anomaly: claim filed before trigger event timestamp
- Duplicate claim: same worker, same zone, same event filing twice
- Coordinated fraud: unusual cluster of claims from same zone outside actual weather event

**Tool:** Python (scikit-learn Isolation Forest) → integrated into claim validation pipeline

---

### 4. Predictive Disruption Forecasting (Admin Dashboard)

**Approach:** Time-series forecasting using Prophet (Facebook) or SARIMA

**Use Case:** Insurer dashboard predicts next week's likely disruption events and expected payout liability, enabling reserve management

**Input:** 3-year historical weather + disruption data for top 10 cities
**Output:** Weekly disruption probability per city, expected claims volume

---

## Fraud Detection Architecture

```
                    CLAIM INITIATED (Auto-triggered)
                              │
              ┌───────────────▼───────────────────┐
              │         FRAUD SCORE ENGINE         │
              │                                    │
              │  ① GPS Activity Validator          │
              │     - Was worker stationary?       │
              │     - Location in affected zone?   │
              │                                    │
              │  ② Temporal Validator              │
              │     - Claim time vs event time     │
              │     - Policy active at event time? │
              │                                    │
              │  ③ Anomaly Score (ML)              │
              │     - Compare vs peer workers      │
              │     - Isolation Forest score       │
              │                                    │
              │  ④ Historical Check                │
              │     - Previous claim patterns      │
              │     - Duplicate claim detection    │
              └───────────────┬───────────────────┘
                              │
              ┌───────────────▼───────────────────┐
              │         FRAUD SCORE RESULT         │
              │                                    │
              │  Score < 0.3  → AUTO APPROVE ✅    │
              │  Score 0.3-0.7→ MANUAL REVIEW ⚠️   │
              │  Score > 0.7  → AUTO REJECT ❌     │
              └───────────────────────────────────┘
```

Specific fraud vectors addressed for food delivery:
- **GPS Spoofing:** Delivery partner claims to be in flooded zone but GPS mock shows movement patterns indicating active deliveries
- **Weather Shopping:** Worker registers in high-risk zone just before a storm (addressed via 48-hour policy lock-in after registration)
- **Syndicate Claims:** ML clusters detect if 50+ workers from same zone all claim on a non-event day

---

## Tech Stack

### Frontend (Worker PWA)
| Layer | Technology |
|-------|-----------|
| Framework | React 18 + Vite |
| Styling | Tailwind CSS |
| State Management | Zustand |
| Offline Support | Workbox (Service Workers) |
| Internationalization | react-i18next |
| Charts | Recharts |

### Backend (API Server)
| Layer | Technology |
|-------|-----------|
| Runtime | Node.js + Express.js |
| Language | TypeScript |
| Database | PostgreSQL (Supabase) |
| Auth | Supabase Auth (OTP-based for gig workers) |
| Caching | Redis |
| Task Queue | Bull (Redis-based) for async claim processing |

### AI/ML Services
| Module | Technology |
|--------|-----------|
| Premium Calculation | Python + XGBoost → FastAPI microservice |
| Fraud Detection | Python + scikit-learn (Isolation Forest) → FastAPI |
| Forecasting | Python + Prophet → FastAPI |
| Deployment | Docker containers |

### External Integrations (Free/Mock)
| Service | API / Mock |
|---------|-----------|
| Weather | OpenWeatherMap Free Tier |
| AQI | OpenAQ API (free) |
| Civic Alerts | Mock REST API (custom) |
| Payments | Razorpay Test Mode / UPI Simulator |
| Platform Data | Mock API (simulated Zomato/Swiggy earnings data) |

### Infrastructure
| Layer | Technology |
|-------|-----------|
| Hosting | Vercel (Frontend) + Railway (Backend) |
| CI/CD | GitHub Actions |
| Monitoring | Sentry (error tracking) |
| API Docs | Swagger / OpenAPI |

---

## System Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                           GIGSHIELD PLATFORM                            │
│                                                                         │
│  ┌──────────────────┐         ┌──────────────────────────────────────┐  │
│  │  Worker PWA       │         │        Admin Dashboard (Web)         │  │
│  │  (React + TWind)  │         │        (React + Recharts)            │  │
│  └────────┬─────────┘         └─────────────────┬────────────────────┘  │
│           │                                     │                       │
│  ┌────────▼─────────────────────────────────────▼────────────────────┐  │
│  │                     API Gateway (Express.js)                       │  │
│  │   /auth  /policy  /claims  /payouts  /dashboard  /triggers        │  │
│  └────┬──────────┬───────────────┬──────────────┬────────────────────┘  │
│       │          │               │              │                       │
│  ┌────▼───┐ ┌────▼─────┐ ┌──────▼───┐ ┌────────▼──────┐               │
│  │  Auth  │ │  Policy  │ │  Claims  │ │   Payout      │               │
│  │Service │ │  Engine  │ │  Engine  │ │   Service     │               │
│  └────────┘ └──────────┘ └──────┬───┘ └───────────────┘               │
│                                 │                                       │
│  ┌──────────────────────────────▼──────────────────────────────────┐   │
│  │                      ML Microservices (FastAPI)                   │   │
│  │   ┌─────────────┐  ┌──────────────┐  ┌────────────────────┐    │   │
│  │   │  Premium    │  │   Fraud      │  │  Disruption        │    │   │
│  │   │  Calculator │  │   Detector   │  │  Forecaster        │    │   │
│  │   └─────────────┘  └──────────────┘  └────────────────────┘    │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                    External API Integrations                      │  │
│  │   OpenWeatherMap │ OpenAQ │ Mock Civic API │ Razorpay Test Mode  │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│                                                                         │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                  Database Layer (PostgreSQL / Supabase)           │  │
│  │   Workers │ Policies │ Claims │ Payouts │ DisruptionEvents       │  │
│  └──────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Development Plan (6-Week Roadmap)

### ✅ Phase 1 (Weeks 1–2): Ideation & Foundation [March 4–20]
- [x] Define persona, use cases, and scenarios
- [x] Design weekly premium model and parametric trigger framework
- [x] Choose tech stack and architecture
- [x] Set up GitHub repository
- [x] Create README (this document)
- [x] Build minimal UI wireframes (Figma)
- [x] Set up project scaffolding (React PWA + Express boilerplate)
- [x] Record 2-minute strategy video

**Deliverables:** README.md + GitHub Repo + 2-min video

---

### 🔨 Phase 2 (Weeks 3–4): Automation & Protection [March 21–April 4]
- [ ] Worker registration + OTP Auth (Supabase)
- [ ] KYC mock flow (Aadhaar simulation)
- [ ] Policy creation UI + weekly pricing selection
- [ ] Dynamic premium calculator (ML model v1)
- [ ] Integrate OpenWeatherMap + OpenAQ APIs
- [ ] Build 3–5 automated parametric triggers
- [ ] Auto claim generation when trigger fires
- [ ] Mock UPI payout integration (Razorpay test mode)
- [ ] Basic fraud detection rules (v1)
- [ ] Worker dashboard: active policy, coverage status

**Deliverables:** Executable source code + 2-min demo video

---

### 🚀 Phase 3 (Weeks 5–6): Scale & Optimise [April 5–17]
- [ ] Advanced fraud detection (ML Isolation Forest)
- [ ] GPS activity validation for claims
- [ ] Admin/Insurer dashboard with analytics
- [ ] Predictive disruption forecasting (Prophet model)
- [ ] Instant payout simulation (end-to-end flow demo)
- [ ] Regional language support (Hindi + Telugu)
- [ ] Performance optimization + PWA offline support
- [ ] Final pitch deck (PDF)
- [ ] 5-minute demo video with simulated disruption event

**Deliverables:** Final working platform + 5-min demo + Pitch deck PDF

---

## Business Viability

### Market Size
- ~10 million active gig delivery workers in India (2025)
- Targeting food delivery segment: ~4–5 million workers
- Even 1% penetration = 40,000–50,000 active policies

### Unit Economics (Standard Plan ₹49/week)

| Metric | Value |
|--------|-------|
| Weekly Premium | ₹49 |
| Annual Premium per Worker | ₹2,548 |
| Expected Claim Rate | ~35% weeks (monsoon + disruptions) |
| Avg Claim Payout per Trigger | ₹350 |
| Loss Ratio Target | < 65% |
| Platform Fee (Zomato/Swiggy API integration) | 10% |

**Revenue at 50,000 workers:** ₹49 × 50,000 × 52 weeks = **₹12.7 Cr/year**

### Why This Works

1. **Zero claims processing cost** — parametric model eliminates human adjuster cost
2. **Anti-selection managed** via 48-hour lock-in + zone-based pricing
3. **Distribution via platforms** — Zomato/Swiggy can bundle GigShield as a partner benefit, reducing CAC to near-zero
4. **Regulatory fit** — IRDAI's sandbox framework for parametric insurance (Bima Sugam ecosystem) supports this model

---

## Team

| Member | Role |
|--------|------|
| [Team Member 1] | Full Stack Developer |
| [Team Member 2] | ML/AI Engineer |
| [Team Member 3] | UI/UX + Frontend |
| [Team Member 4] | Backend + DevOps |

---

## Repository Structure

```
gigshield/
├── README.md                  ← This file
├── frontend/                  ← React PWA (Worker Interface)
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── store/
│   │   └── i18n/
│   └── package.json
├── backend/                   ← Express.js API Server
│   ├── src/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── models/
│   │   └── triggers/
│   └── package.json
├── ml-services/               ← Python ML Microservices
│   ├── premium_calculator/
│   ├── fraud_detector/
│   └── forecaster/
├── mock-apis/                 ← Mock civic & platform APIs
├── docs/                      ← Architecture diagrams, wireframes
└── docker-compose.yml
```

---

## Links

- 📁 **GitHub Repository:** [Link to be added]
- 🎥 **Phase 1 Demo Video:** [Link to be added]

---

> *GigShield — Built for the workers who keep India running. 🛵*