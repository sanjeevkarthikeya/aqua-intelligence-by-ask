# AQUA INTELLIGENCE — Predictive Water Infrastructure Management Platform

A civic technology platform connecting citizens, residential apartment communities, commercial dining establishments, government administrators, and municipal field workers.

---

## 1. System Overview

AQUA INTELLIGENCE addresses recurring urban waterlogging, drainage blockages, pipeline ruptures, and potable water quality concerns by transforming reactive citizen complaints into structured, predictive civic infrastructure intelligence.

### Key Capabilities
- **Dual Intake Streams:** Individual citizen grievances with geotagging and consolidated community reports from Apartment RWAs and restaurant clusters.
- **Server-Side Gemini AI Integration:**
  - Automated report triage and priority classification.
  - Multi-complaint semantic & geographic cluster analysis to detect underlying arterial pipeline ruptures or blocked trunk drains.
  - Objective civic help walkthrough assistant knowing the user's current page.
- **Privacy-Preserving Public GIS:** Ward-level spatial aggregation of water problems without exposing citizen names, unit numbers, phone numbers, or private pipeline routes.
- **Government Command Center:** Private infrastructure GIS mapping (pipelines, manholes, valves), incident management, work order dispatch, and audit trails.
- **Field Worker Mobile Desk:** Work orders, true sub-surface fault location recording (separate from citizen reported pins), and before/after repair proof.
- **Predictive Risk Engine:** Transparent scoring formulas for recurrence risk and nearby network vulnerability with data-gap indicators.

---

## 2. Environment Variables

Configured in `.env`:
```bash
# Gemini AI API Key for server-side triage, clustering, and chat
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"

# Development / App URL
APP_URL="https://..."
```

---

## 3. Firebase Configuration

Firebase Authentication and Firestore have been provisioned using the native AI Studio Fax RPC:
- **Project ID:** `marklar-toolbox-jf6jr`
- **Database ID:** `ai-studio-3b57d238-38e9-4593-91a0-82b37af075e4`
- **Config file:** `firebase-applet-config.json`
- **Security Rules:** `firestore.rules` deployed with Attribute-Based Access Control (ABAC) and role protection (`government_admin`, `field_worker`, `community_admin`, `citizen`).

### Firestore Collections:
- `users`: User profiles with role protection.
- `communities`: Apartment associations, restaurant clusters, and wards.
- `communityMembers`: Association membership records.
- `reports`: Individual citizen water grievances.
- `communityReports`: Consolidated RWA petitions.
- `incidents`: Master municipal problem entities linking reports and assets.
- `infrastructureAssets`: Pipelines, stormwater box drains, manholes, and valves.
- `clusters`: AI-detected complaint clusters.
- `workOrders`: Municipal field repair dispatch orders.
- `repairs`: Actual fault locations and completion evidence logged by field workers.
- `riskAssessments`: Recurrence risk and nearby geographic risk scores.
- `auditLogs`: Immutable government accountability trail.

---

## 4. Role-Based Navigation & Demo Testing Instructions

A dedicated **Evaluator Role Switcher** is accessible in the top civic bar and on the `/login` page:

1. **Government Administrator (`/admin`):**
   - Click **Admin Console** or switch to `Gov Administrator`.
   - Access the **All Citizen Reports** tab to review Gemini summaries or reject invalid submissions.
   - Access **AI Complaint Clusters** to confirm suggested groupings into master incidents.
   - Access **Infrastructure GIS Map** to inspect pipelines, toggle verification status, or draw new pipeline routes.
   - Access **Predictive Risk Engine** to view transparent factor breakdowns and data gaps.
   - Use the **"Sync Synthetic Data (35+)"** button in the top bar anytime to populate or reset live Firestore with realistic Bengaluru/urban water records.

2. **Field Worker Desk (`/worker`):**
   - Switch to `Field Worker`.
   - View assigned tasks (e.g. Indiranagar or Koramangala work orders).
   - Record the **actual sub-surface fault GPS coordinates** (which differ from the citizen surface pin).
   - Enter remedial actions, before/after photos, and materials used.

3. **Community RWA Admin (`/community` & `/community-report`):**
   - Switch to `Community RWA Admin`.
   - View your association's profile (e.g. Prestige Palms or Palm Meadows).
   - File consolidated community petitions on behalf of hundreds of households.

4. **Citizen / Public (`/` & `/report` & `/track` & `/public-map`):**
   - Lodge individual complaints with photos and GPS pin.
   - Use the interactive public map with generalized ward-level hotspot polygons.
   - Track reports using reference numbers such as `AQ-IND-8401` or `AQ-KOR-1501`.

---

## 5. Water Quality Policy & Limitations

- **Potable Safety Disclaimer:** In strict compliance with public health standards, Gemini AI is prohibited from declaring water safe or unsafe solely based on visual photographs. All water quality grievances trigger formal physical sampling by the State Environmental Water Laboratory.
- **Synthetic Data Notice:** The sample pipelines, manholes, and incidents included for demonstration are realistic but fictional civic scenarios.
