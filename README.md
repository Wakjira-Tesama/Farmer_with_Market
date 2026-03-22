# AgriBridge (Farmer_with_Market)

Smart, mobile-first platform that connects smallholder farmers to practical knowledge and verified markets.

```
	 _
 _( )_                     .-""-.
(_   _)                   / .--. \
	| |                    / /    \ \
	| |       .-""-.       | |    | |
	| |      / .--. \      | |    | |
	| |     / /    \ \     | |    | |
	| |     | |    | |     | |    | |
	|_|     \ \    / /      \ \__/ /
	 ( )     \ '--' /        '----'
		\ \     '-..-'        / .--. \
		 \ \                / /    \ \
			\ \              | |    | |
			 \ \             | |    | |
				\ \            | |    | |
				 \ \            \ \__/ /
					\ \            '----'
					 \ \      Farmer with Market
						\ \
						 \ \
							\_\

	 Fruit Basket          Livestock
			.-""-.               /\_/\
		 / .--. \             ( o.o )
		/ /    \ \             > ^ <
		| |    | |             /| |\
		\ \    / /            /_| |_\
		 \ '--' /            /__|__\
			'-..-'
```

## Table of Contents

- [About](#about)
- [Animation](#animation)
- [Project Description](#project-description)
- [Problem Statement](#problem-statement)
- [Before and After](#before-and-after)
- [Objectives and Goals](#objectives-and-goals)
- [Target Users](#target-users)
- [Key Features](#key-features)
- [Low-Literacy Access](#low-literacy-access)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Detailed Architecture](#detailed-architecture)
- [Design Architecture](#design-architecture)
- [Farmer-System Relationship](#farmer-system-relationship)
- [Farmer-Market Connection](#farmer-market-connection)
- [Core Modules](#core-modules)
- [Use Cases](#use-cases)
- [Sequence Flows](#sequence-flows)
- [Data Model](#data-model)
- [Design](#design)
- [Getting Started](#getting-started)
- [Non-Functional Requirements](#non-functional-requirements)
- [Scope and Roadmap](#scope-and-roadmap)
- [Expected Impact](#expected-impact)
- [Alignment with Global Goals](#alignment-with-global-goals)
- [Contributing](#contributing)
- [License](#license)

## About

AgriBridge is a smart, mobile-based platform designed to support smallholder farmers by providing easy-to-understand agricultural information and direct access to markets. The platform delivers guidance on crops, livestock, soil conditions, and climate using audio and video in local languages, making it accessible to farmers with low literacy levels.

AgriBridge also connects farmers with agricultural experts and verified buyers, enabling fair, efficient product sales. This bridges the gap between knowledge, production, and market access.

![AgriBridge Experience Overview](assets/farmer-market-overview.png)

## Animation

![AgriBridge animated overview](assets/agri-bridge-overview.gif)

## Project Description

AgriBridge combines farmer profiles, advisory services, and market tools into one mobile-first experience. Farmers can learn with audio and video, ask experts for guidance, and list produce for verified buyers. The platform emphasizes low data usage, offline-friendly access, and trusted transactions to improve yields, reduce risk, and increase income.

## Problem Statement

Farmers in rural areas face major challenges:

- Lack of reliable agricultural information (soil, crops, climate)
- Poor awareness of crop suitability
- Limited access to modern farming practices
- Weak connections to trusted markets
- Exploitation by illegal traders and intermediaries
- Low income despite high effort

These issues lead to crop failure, financial loss, and food insecurity.

## Before and After

How the farmer experience changes after using AgriBridge.

```mermaid
flowchart LR
	subgraph Before[Before AgriBridge]
		B1[Low access to reliable info]
		B2[Unsuitable crop choices]
		B3[Weak market connections]
		B4[Exploitative intermediaries]
		B5[Low income and high risk]
	end

	subgraph After[After AgriBridge]
		A1[Localized audio/video guidance]
		A2[Crop and soil recommendations]
		A3[Direct verified buyers]
		A4[Transparent pricing]
		A5[Higher income and resilience]
	end

	B1 --> A1
	B2 --> A2
	B3 --> A3
	B4 --> A4
	B5 --> A5
```

## Objectives and Goals

**General objective**: Empower farmers with accessible knowledge and direct market connections to improve productivity and income.

**Specific objectives**:

- Provide simple, localized agricultural education
- Enable data-driven farming decisions
- Connect farmers to verified markets and buyers
- Reduce exploitation by intermediaries
- Improve product quality and income levels

**Goals**:

| Horizon                 | Goals                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------ |
| Short-Term (4-6 months) | Pilot with 500-1,000 farmers, run training sessions, test AI recommendations and market features |
| Long-Term               | Scale to 4,000,000+ farmers, expand languages, build nationwide farmer-market ecosystem          |

## Target Users

- Smallholder farmers in rural areas
- Low-literacy farmers
- Farmers lacking access to experts and markets

## Key Features

- Mobile-friendly platform (low data usage)
- Audio-based learning for accessibility
- Video tutorials for practical guidance
- Climate and weather updates
- Crop and soil recommendations
- Direct access to agricultural experts
- Market connection system
- Product listing and promotion tools

![AgriBridge Platform Features](assets/agribridge-features.png)

## Low-Literacy Access

How the platform supports farmers who cannot read or write through audio and video guidance.

```mermaid
flowchart LR
	F[Farmer]
	APP[Mobile App]
	IVR[Voice/IVR and Audio]
	VIDEO[Video Lessons]
	AI[AI Helper]
	NOTIFY[Alerts and Reminders]

	F -->|Tap icons / voice input| APP
	APP --> IVR
	APP --> VIDEO
	APP --> AI
	AI -->|Localized guidance| IVR
	AI -->|Localized guidance| VIDEO
	NOTIFY -->|Voice or audio alerts| F
	APP -->|Play audio/video| F
```

## Tech Stack

This section will be finalized once the implementation stack is confirmed. Proposed placeholders:

| Layer      | Candidate Options                            |
| ---------- | -------------------------------------------- |
| Mobile App | Flutter or React Native                      |
| Web        | React or Vue                                 |
| Backend    | Node.js (Express) or Django                  |
| Database   | PostgreSQL                                   |
| Storage    | S3-compatible object storage                 |
| AI/ML      | Python services (recommendations, NLP/voice) |
| Messaging  | Firebase, Twilio, or local SMS gateways      |

## System Architecture

AgriBridge combines mobile and web clients with a scalable backend and AI services.

```mermaid
flowchart LR
	subgraph Clients
		A[Farmer Mobile App]
		B[Buyer Web Portal]
		C[Expert/Admin Web Console]
	end

	subgraph Platform
		API[API Gateway]
		AUTH[Auth and Identity]
		CONTENT[Content Service]
		ADVISORY[Expert Advisory]
		MARKET[Market Service]
		NOTIFY[Notification Service]
		AI[AI Recommendation Engine]
	end

	subgraph Data
		DB[(Relational DB)]
		STORE[(Object Storage)]
		CACHE[(Cache)]
	end

	A --> API
	B --> API
	C --> API
	API --> AUTH
	API --> CONTENT
	API --> ADVISORY
	API --> MARKET
	API --> NOTIFY
	API --> AI
	AUTH --> DB
	CONTENT --> STORE
	CONTENT --> DB
	ADVISORY --> DB
	MARKET --> DB
	AI --> DB
	NOTIFY --> DB
	AI --> CACHE
```

## Detailed Architecture

Deeper view of services, integrations, and data flows.

```mermaid
flowchart TB
	subgraph Client Layer
		M[Farmer Mobile App]
		W[Buyer Web]
		X[Expert/Admin Web]
	end

	subgraph Edge Layer
		GW[API Gateway]
		AUTH[Auth and Identity]
	end

	subgraph Domain Services
		PROFILE[Farmer Profile Service]
		CONTENT[Content Service]
		ADVISORY[Advisory Service]
		MARKET[Market Service]
		PRICING[Pricing and Offers]
		NOTIFY[Notification Service]
		MEDIA[Media Processing]
		AI[AI Recommendations]
	end

	subgraph Data Layer
		DB[(Relational DB)]
		SEARCH[(Search Index)]
		STORE[(Object Storage)]
		CACHE[(Cache)]
	end

	subgraph External Integrations
		WX[Weather Provider]
		PAY[Payments]
		SMS[SMS/Push Gateway]
		MAP[Maps/Geo]
	end

	M --> GW
	W --> GW
	X --> GW
	GW --> AUTH
	GW --> PROFILE
	GW --> CONTENT
	GW --> ADVISORY
	GW --> MARKET
	GW --> NOTIFY
	GW --> AI
	CONTENT --> STORE
	CONTENT --> MEDIA
	PROFILE --> DB
	ADVISORY --> DB
	MARKET --> DB
	PRICING --> DB
	MARKET --> SEARCH
	AI --> CACHE
	AI --> DB
	NOTIFY --> SMS
	NOTIFY --> WX
	MARKET --> PAY
	PROFILE --> MAP
```

## Design Architecture

User experience flow and system responsibilities at each step.

```mermaid
sequenceDiagram
	participant Farmer
	participant App
	participant Gateway
	participant Services
	participant Data
	participant Market

	Farmer->>App: Open app and select task
	App->>Gateway: Request feature entry
	Gateway->>Services: Route to relevant module
	Services->>Data: Fetch/update records
	Services->>Market: Match listing with buyers
	Market-->>Services: Orders and offers
	Services-->>Gateway: Response payload
	Gateway-->>App: Render audio/video/text
	App-->>Farmer: Action confirmation
```

## Farmer-System Relationship

How a farmer interacts with the platform and how the system responds.

```mermaid
flowchart LR
	F[Farmer]
	APP[Mobile App]
	SYS[AgriBridge Services]
	EXP[Expert Network]
	BUY[Verified Buyers]
	DATA[(Data and Content)]

	F -->|Register profile| APP
	F -->|Ask question| APP
	F -->|List produce| APP
	F -->|Consume lessons| APP
	APP --> SYS
	SYS --> DATA
	SYS --> EXP
	SYS --> BUY
	EXP -->|Advice and diagnosis| SYS
	BUY -->|Orders and offers| SYS
	SYS -->|Alerts, tips, prices| APP
	APP -->|Audio, video, text| F
```

## Farmer-Market Connection

How farmers connect to buyers through the market service.

```mermaid
flowchart LR
	F[Farmer]
	APP[Mobile App]
	MARKET[Market Service]
	VERIFY[Buyer Verification]
	BUY[Verified Buyer]
	PAY[Payment and Settlement]
	LOG[Delivery and Logistics]

	F -->|Create listing| APP
	APP -->|Submit listing| MARKET
	MARKET -->|Verify buyer| VERIFY
	BUY -->|Place order| MARKET
	MARKET -->|Confirm order| APP
	MARKET --> PAY
	MARKET --> LOG
	LOG -->|Pickup and delivery| F
```

## Core Modules

| Module                 | Purpose                               | Key Outputs              |
| ---------------------- | ------------------------------------- | ------------------------ |
| Content and Learning   | Audio/video guides in local languages | Lessons, tips, tutorials |
| Farmer Profile         | Store farmer, farm, and location data | Profiles, preferences    |
| Market Connection      | Link farmers to verified buyers       | Listings, offers, orders |
| Expert Advisory        | Connect farmers to agronomists        | Advice, diagnostics      |
| Notification and Alert | Weather, tips, market price alerts    | SMS, push, voice         |

## Use Cases

```mermaid
flowchart TB
	F[Farmer]
	E[Expert]
	B[Buyer]
	A[Admin]

	UC1((Register and Setup Profile))
	UC2((Consume Audio/Video Lessons))
	UC3((Request Expert Advice))
	UC4((Receive Weather Alerts))
	UC5((List Produce for Sale))
	UC6((Buy Produce))
	UC7((Verify Buyers and Content))

	F --- UC1
	F --- UC2
	F --- UC3
	F --- UC4
	F --- UC5
	B --- UC6
	E --- UC3
	A --- UC7
```

### Primary Use Case Table

| Actor  | Goal                      | Outcome                        |
| ------ | ------------------------- | ------------------------------ |
| Farmer | Learn best practices      | Improved farming decisions     |
| Farmer | Sell produce fairly       | Better prices and faster sales |
| Expert | Provide guidance          | Reduced crop risk              |
| Buyer  | Source verified produce   | Trusted supply chain           |
| Admin  | Maintain platform quality | Reliable, safe ecosystem       |

## Sequence Flows

### Sequence 1: Farmer Requests Advice

```mermaid
sequenceDiagram
	participant Farmer
	participant App
	participant API
	participant Advisory
	participant Expert

	Farmer->>App: Submit issue with photo/voice
	App->>API: Create advisory request
	API->>Advisory: Queue request
	Advisory->>Expert: Assign based on crop/location
	Expert->>Advisory: Provide guidance
	Advisory->>API: Respond with recommendations
	API->>App: Deliver response
	App->>Farmer: Show audio/text guidance
```

### Sequence 2: Farmer Lists Produce, Buyer Purchases

```mermaid
sequenceDiagram
	participant Farmer
	participant App
	participant API
	participant Market
	participant Buyer

	Farmer->>App: Create listing
	App->>API: Submit listing
	API->>Market: Store listing
	Buyer->>API: Browse listings
	API->>Market: Fetch listings
	Market->>API: Return matches
	API->>Buyer: Show listings
	Buyer->>API: Place order
	API->>Market: Create order
	Market->>Farmer: Notify sale
```

## Data Model

High-level entities and relationships:

```mermaid
erDiagram
	FARMER ||--o{ FARM : owns
	FARMER ||--o{ LISTING : creates
	FARMER ||--o{ ADVISORY_REQUEST : submits
	EXPERT ||--o{ ADVISORY_RESPONSE : writes
	BUYER ||--o{ ORDER : places
	LISTING ||--o{ ORDER : fulfills
	CONTENT ||--o{ CONTENT_MEDIA : includes

	FARMER {
		string id
		string name
		string phone
		string language
	}
	FARM {
		string id
		string location
		string soilType
	}
	LISTING {
		string id
		string cropType
		number quantity
		number price
	}
	ORDER {
		string id
		string status
		number total
	}
	ADVISORY_REQUEST {
		string id
		string issue
		string status
	}
	ADVISORY_RESPONSE {
		string id
		string recommendation
	}
	CONTENT {
		string id
		string title
		string category
	}
	CONTENT_MEDIA {
		string id
		string type
		string url
	}
```

## Design

### Experience Principles

- Audio-first and low-literacy friendly
- Minimal steps per task
- Works in low connectivity
- Trust and safety focused

### UI Design Outline

```mermaid
flowchart TD
	H[Home]
	H --> L[Learn]
	H --> M[Market]
	H --> A[Ask Expert]
	H --> P[Profile]
	L --> L1[Audio Lessons]
	L --> L2[Video Tutorials]
	M --> M1[List Produce]
	M --> M2[Buyer Offers]
	A --> A1[Submit Issue]
	A --> A2[Advice History]
```

### Design System Tokens (Example)

| Token   | Value   | Usage               |
| ------- | ------- | ------------------- |
| Primary | #2E7D32 | Actions, highlights |
| Accent  | #F4A000 | Alerts, pricing     |
| Neutral | #2D2D2D | Text                |
| Surface | #F7F5EF | Background          |
| Success | #2E8B57 | Positive feedback   |

## Getting Started

These commands are placeholders until the stack is finalized.

### Prerequisites

- Node.js 18+ and npm (or pnpm/yarn)
- Python 3.10+ (for AI services)
- PostgreSQL 14+

### Setup

```bash
# clone the repo
git clone https://github.com/Wakjira-Tesama/Farmer_with_Market.git
cd Farmer_with_Market

# install dependencies (example for a Node backend)
npm install
```

### Run (Example)

```bash
# start backend
npm run dev

# start web app (if in a separate folder)
cd web
npm install
npm run dev
```

## Non-Functional Requirements

| Quality      | Requirement                                |
| ------------ | ------------------------------------------ |
| Scalability  | Support 4M+ users via cloud infrastructure |
| Usability    | Simple, audio-first interface              |
| Reliability  | Stable and accurate system performance     |
| Availability | Works in low-connectivity environments     |
| Security     | Protect user data and transactions         |

## Scope and Roadmap

| Phase       | Scope                                    |
| ----------- | ---------------------------------------- |
| Short-Term  | Pilot in one community or region         |
| Medium-Term | Expand to multiple regions and languages |
| Long-Term   | Nationwide scale to millions of farmers  |

## Expected Impact

- Improved farmer decision-making
- Reduced crop losses
- Increased income and productivity
- Stronger farmer-market connections
- Enhanced food security

## Alignment with Global Goals

- Zero Hunger
- No Poverty

## Contributing

Contributions are welcome. Please open an issue to discuss major changes and submit a pull request for review.

## License

License is not yet specified. Add a LICENSE file and update this section when decided.

<!-- update 2026-03-22T13:27:24 -->

<!-- update 2026-03-22T17:56:12 -->

<!-- update 2026-03-22T09:55:55 -->

<!-- update 2026-03-22T09:02:09 -->
