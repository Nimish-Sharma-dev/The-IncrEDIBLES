# The IncrEDIBLES 🌙
### The City's Missing Ledger | The IncrEDIBLES

**Making surplus food visible. Connecting hungry communities. Moving food before it's too late.**


The IncrEDIBLES is a WhatsApp-first food rescue and coordination network that connects restaurants, bakeries, and food businesses with surplus food to registered NGOs and community kitchens through a network of volunteer rescue riders.

It transforms food that would otherwise be discarded at closing time into timely, trackable food deliveries.

**Our goal:** Move safe surplus food from businesses to people who need it within 60 minutes.

---

## 1. The Problem

Cities generate enormous amounts of food waste while thousands of people struggle to access reliable meals.

In Bengaluru, this problem has three largely invisible components:

- **Unrecorded surplus:** Restaurants, bakeries, sweet shops, and caterers discard unsold food every night.
- **Unconnected demand:** Street dwellers, hospital attendants, night-shift workers, and gig workers often lack access to timely food assistance.
- **Missing coordination:** Volunteers and delivery riders could help connect surplus food to recipients, but there is no unified system coordinating them.

The problem is not simply food scarcity. It is a failure of coordination, timing, and safe distribution.

The IncrEDIBLES aims to make these three invisible elements visible through a shared city-level ledger.

## 2. Our Solution

The IncrEDIBLES creates a real-time food rescue network around the two hours before business closing.

It connects three primary stakeholders:

| Stakeholder | Responsibility |
|---|---|
| Food Donors | List available surplus food |
| NGO Receivers | Accept batches and manage distribution |
| Rescue Riders | Collect and transport food |

A WhatsApp-first interface ensures that food donors do not need to install another application or complete complicated registration processes.

### How The IncrEDIBLES Works

1. **List Surplus:** A donor sends a WhatsApp voice note, photo, or quick listing indicating available food.
2. **Extract Information:** The system identifies food items, quantities, and preparation time.
3. **Safety Clock:** A rule-based engine calculates the remaining safe distribution window.
4. **Intelligent Matching:** The system identifies suitable NGOs and available riders based on distance, capacity, dietary requirements, and time remaining.
5. **Rescue Run:** A rider accepts the task and collects the food.
6. **Verified Handover:** Collection and delivery are recorded with timestamps and photo evidence.
7. **City Ledger:** Every listing, successful collection, rejection, and unmet request contributes to a ward-level impact dashboard.

**Target:** Complete the rescue and handover process within 60 minutes of listing.

---

## 3. System Architecture

The IncrEDIBLES follows a modular architecture consisting of five primary layers.

```text
                 FOOD DONORS
              WhatsApp / Voice / Photo
                       |
                       v
             +--------------------+
             |  WhatsApp Bot      |
             |  Listing Interface |
             +--------------------+
                       |
                       v
             +--------------------+
             | Voice & Data       |
             | Extraction Layer   |
             | Speech-to-Text     |
             | Structured JSON    |
             +--------------------+
                       |
                       v
             +--------------------+
             | Food Safety Engine |
             | Category Rules     |
             | Safe-Until Timer    |
             | Expiry Validation  |
             +--------------------+
                       |
                       v
             +--------------------+
             | Matching Engine    |
             | Distance           |
             | Capacity            |
             | Dietary Needs       |
             | Time Remaining      |
             +--------------------+
                       |
              +--------+--------+
              |                 |
              v                 v
        REGISTERED NGO     RESCUE RIDER
              |                 |
              +--------+--------+
                       |
                       v
             +--------------------+
             | Verified Handover  |
             | Photo Evidence     |
             | Timestamp Log      |
             +--------------------+
                       |
                       v
             +--------------------+
             | City Impact Ledger |
             | Ward Heatmap       |
             | Surplus vs Demand  |
             | Rider Coverage     |
             +--------------------+
```

### Core Components

| Component | Purpose |
|---|---|
| WhatsApp Bot | Provides a simple interface for donors and riders |
| Data Extraction | Converts voice notes and photos into structured food listings |
| Food Safety Engine | Validates food categories and distribution deadlines |
| Matching Engine | Ranks NGOs and riders for suitable rescue assignments |
| Rescue Management | Handles acceptance, rejection, expiry, and handover |
| City Ledger | Records surplus, unmet demand, and rescue activity |
| Impact Dashboard | Visualizes food rescue activity across city wards |

---

## 4. Key Features

### 4.1 Zero-Friction Food Listing
- WhatsApp-based interaction.
- Voice-note and photo-based food submissions.
- Support for Kannada, Hindi, and English.
- Quick listing through a closing-time notification.
- No dedicated application or login required for donors.

### 4.2 Intelligent Food Safety Clock
- Records food preparation time.
- Assigns food categories.
- Calculates a safe-until countdown.
- Rejects expired or unsuitable listings.
- Displays relevant hot-chain and cold-chain handling guidance.
- Maintains a photo-based audit trail.

### 4.3 Intelligent Matching Engine

The matching engine ranks potential receivers and riders using:

- Geographic distance.
- Available collection capacity.
- Dietary requirements.
- Remaining food safety window.

A weighted scoring approach prioritizes the most suitable available match.

### 4.4 Rescue Rider Network
- Riders can mark themselves available for the night.
- One-tap task acceptance or rejection.
- Short-distance pickup and delivery assignments.
- No compulsory participation or speed-based incentives.
- Club-based rescue participation and leaderboards.

### 4.5 City Food Waste Ledger

The city ledger maintains records of:

- Total food surplus listed.
- Food successfully collected.
- Food rejected for safety reasons.
- Unclaimed food batches.
- Unmet food requests.
- Rider availability and coverage.

A ward-level heatmap helps identify areas with surplus food but insufficient rescue coverage.

### 4.6 Offline Accessibility
- Missed-call and SMS-based listing fallback.
- Accessibility for users without smartphones or mobile data.
- Alternative communication channels for the demonstration MVP.

---

## 5. Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Backend | Python, FastAPI | API and application logic |
| Database | PostgreSQL + PostGIS | Structured data and geospatial queries |
| Messaging | WhatsApp Business API / Twilio | Donor and rider communication |
| Fallback Messaging | Telegram / SMS | Alternative communication |
| Voice Processing | Speech-to-Text | Voice-note transcription |
| AI Extraction | LLM APIs | Structured information extraction |
| Frontend | React PWA | Web-based dashboard |
| Mapping | Leaflet + OpenStreetMap | Ward-level visualization |
| Routing | OSRM | Pickup routes and ETA estimation |
| Hosting | Render / Railway | Application deployment |

The architecture is modular. Individual services can be replaced without redesigning the entire system.

---

## 6. Food Safety, Privacy & Responsible Operations

Food rescue must prioritize safety and accountability over delivery speed.

### Food Safety
- Food listings are validated using category-based rules.
- The default safety window in the concept is four hours from preparation, with stricter rules for applicable categories.
- Unsafe or expired listings are rejected.
- Donors receive food-handling guidance.
- Collection and handover records support traceability.

### Compliance
The system is designed around the FSSAI Surplus Food Recovery and Distribution Regulations, 2019.

Food donations are routed through registered surplus food distribution organisations and NGO partners.

Relevant handling guidance includes:
- Hot food: approximately 60°C.
- Cold food: approximately 5°C.

Operational deployment must follow applicable FSSAI requirements and partner procedures.

### Rider Safety
- No speed-based delivery incentives.
- Short-distance rescue assignments.
- Helmet and traffic-safety reminders.
- Riders can decline any task.
- Incident reporting can pause an affected donation batch.

### Privacy
- No unauthorized scraping of personal information.
- Rider location is shared only during an active task.
- Food requesters remain anonymous in the public-facing system.
- Access to operational information is restricted according to user roles.

---

## 7. Expected Impact

### Initial Pilot: One Bengaluru Ward

| Metric | Pilot Target |
|---|---:|
| Food donors | 20 |
| NGO receivers | 10 |
| Participating clubs | 5 |
| Pilot duration | 4 weeks |
| Median matching time | Under 30 minutes |
| Successful collection rate | 60%+ |
| Safety incidents | Zero |

### Projected Food Rescue

Based on the concept's initial planning assumptions:

- 20 participating donors.
- 5 operating nights per week.
- 10 meals per donor per night.

This gives a projected **1,000 meals per week**, or approximately **4,000 meals per month**.

These figures are pilot targets and assumptions, not measured results.

### Impact Indicators
- Number of meals rescued.
- Quantity of food collected.
- Average matching time.
- Successful collection percentage.
- Food rejected for safety reasons.
- Unmet food requests.
- Rider participation and retention.

---

## 8. Business Model

The IncrEDIBLES follows a social-impact-oriented model.

**Free for:**
- NGOs.
- Community kitchens.
- Rescue riders.
- Volunteer clubs.

**Potential revenue streams:**

1. **CSR and ESG Reporting:** Food donors receive verifiable food-rescue and impact reports.
2. **Ward-Level Intelligence:** Aggregated surplus, demand, and rider-coverage insights for civic bodies and NGOs.
3. **Community Infrastructure Planning:** Insights for identifying locations for community fridges and rider pit stops.
4. **Institutional Partnerships:** Partnerships with canteens, hostels, caterers, and larger food businesses.

The objective is to keep food rescue accessible while making city-level impact intelligence sustainable.

---

## 9. Roadmap

### Phase 1 — Functional MVP
- WhatsApp donor listing.
- Structured food information extraction.
- Food safety countdown.
- NGO and rider matching.
- Rider task acceptance.
- Collection and delivery tracking.

### Phase 2 — City-Level Intelligence
- Ward-level surplus and demand heatmaps.
- Unmet food request tracking.
- Rider coverage analytics.
- NGO performance and impact reporting.
- Multilingual improvements.

### Phase 3 — Community Expansion
- Rider Pit Stops.
- SMS-based food discovery.
- Club-based ward adoption.
- Monthly Rescue Run events.
- Expansion to hostels, canteens, and wedding caterers.

---

## 10. Project Structure

The following is a suggested repository structure for the modular implementation.

```text
The-IncrEDIBLES/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── api/
│   │   ├── models/
│   │   ├── schemas/
│   │   ├── services/
│   │   │   ├── food_extraction.py
│   │   │   ├── safety_engine.py
│   │   │   ├── matching_engine.py
│   │   │   └── notification_service.py
│   │   ├── database/
│   │   └── utils/
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── App.jsx
│   └── package.json
│
├── bot/
│   ├── handlers/
│   ├── integrations/
│   └── webhook.py
│
├── docs/
│   └── architecture/
│
├── tests/
│
├── .env.example
├── .gitignore
└── README.md
```

*Note: This is a proposed project structure. Adjust it to match the actual repository implementation.*

---

## 11. Getting Started

### Prerequisites

- Python 3.10+
- Node.js and npm
- PostgreSQL with PostGIS
- Git
- WhatsApp Business API or Twilio credentials (for live messaging integration)

### Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd The-IncrEDIBLES
```

### Backend Setup

```bash
cd backend

python -m venv venv
```

Activate the virtual environment:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Configure the environment variables using the provided `.env.example` file.

Start the backend:

```bash
uvicorn app.main:app --reload
```

### Frontend Setup

```bash
cd frontend

npm install
npm run dev
```

The application will run at the local development URL provided by Vite.

*Setup commands may require adjustment depending on the final repository structure and implementation.*

---

## 12. Environment Variables

Create a `.env` file using `.env.example`.

Example configuration:

```env
# Application
APP_ENV=development
APP_SECRET_KEY=your_secret_key

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/the_incredibles

# Messaging
WHATSAPP_API_TOKEN=
WHATSAPP_PHONE_NUMBER_ID=
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=

# AI / Voice Processing
LLM_API_KEY=
SPEECH_TO_TEXT_API_KEY=

# Mapping
OSRM_BASE_URL=
```

Never commit API keys, credentials, or production secrets to GitHub.

---

## 13. Testing & Validation

The MVP should validate the following scenarios:

| Test Case | Expected Behaviour |
|---|---|
| Valid food listing | Batch successfully created |
| Missing preparation time | Listing requests additional information |
| Unsafe food category | Batch rejected with a reason |
| Expired food batch | Listing automatically becomes unavailable |
| No available NGO | Batch remains unclaimed and escalates |
| No available rider | Matching process continues or escalates |
| Duplicate task acceptance | Only one rider successfully claims the task |
| Successful handover | Collection and delivery records updated |
| Rider rejection | Task becomes available to another rider |
| Incident reported | Affected batch is paused for review |

---

## 14. Open-Source Resources & References

The project is built around publicly available technologies and resources.

### Core Technologies
- [Python](https://www.python.org/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [PostGIS](https://postgis.net/)
- [React](https://react.dev/)
- [Leaflet](https://leafletjs.com/)
- [OpenStreetMap](https://www.openstreetmap.org/)
- [OSRM](https://project-osrm.org/)
- [Twilio](https://www.twilio.com/docs/whatsapp)

### Food Safety & Research
- [FSSAI](https://www.fssai.gov.in/)
- [FSSAI Food Safety Regulations](https://www.fssai.gov.in/)
- [UNEP Food Waste Index](https://www.unep.org/resources/publication/food-waste-index-report-2024)
- [FAO](https://www.fao.org/)

All libraries, APIs, datasets, and AI tools used in the final implementation should be explicitly declared with their licenses and attribution requirements.

---

## 15. Team

**Team Name: The IncrEDIBLES**

| Member | Responsibility |
|---|---|
| Vansh Baranwal | Product & Pitch Lead |
| Omkar DK | Backend, Data & Matching Engine |
| D Venkat Abhishek | Frontend & WhatsApp Bot |
| Nimish Sharma | Field Research, Club & NGO Outreach |

---

## 16. Why The IncrEDIBLES?

A city does not lack food, people willing to help, or people who need a meal.

It lacks the coordination that connects them at the right moment.

The IncrEDIBLES builds that missing connection.

**We don't just track food waste. We make sure food reaches someone before it becomes waste.**

---
