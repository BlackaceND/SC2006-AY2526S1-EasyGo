#  EasyGo

Welcome to the official repository for NTU SC2006 / SC2002 Software Engineering group project **_EasyGo_**.



**EasyGo** is a **smart transport and convenience planner** that helps users find the **most optimal route based on overall comfort over just speed**.  
By integrating **real-time public transport, bus wait timings, carpark... data**, EasyGo computes a personalized **Convenience Score** that balances time, cost, walking distance, and live conditions.  
Built with **Next.js + TypeScript**, with **scalability, modularity, and strong software engineering practices**  in mind.

---




<details>
<summary>🧩 Diagrams</summary>
<br>

1. [System Architecture Diagram](link_here)
2. [Use Case Diagram](link_here)
3. [Class Diagram](link_here)
4. [Sequence Diagram](link_here)
5. [Data Flow Diagram](link_here)

</details>

---

## ⚙️ Setup Instructions

### 🖥️ Running the Website

1. Navigate to the `/EasyGo` directory.
   ```bash
   npm install
   npm run dev
   ```
2. The website will be running on:  
   👉 [http://localhost:3000](http://localhost:3000)

### 🌍 Environment Variables

Create a `.env.local` file in the root directory and populate the fields with your own keys:

```bash
NEXT_PUBLIC_ONEMAP_API_KEY=
NEXT_PUBLIC_LTA_DATAMALL_KEY=
NEXT_PUBLIC_NEA_WEATHER_URL=
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=
```
API keys are provided in .env local for convenience. In real production this should not be the case. These tokens will be revoked in the future.


---

## 🧭 Project Overview

**Goal:**  
To develop a web application that consolidates multiple transport and environmental data sources to compute a **“Convenience Score”**, helping users select routes that best fit their preferences and live conditions.

## 🚀 Features

| Category | Description |
|-----------|--------------|
| **Authentication** | Supports **Driving**, **Public Transport**, and **Walking** via the OneMap Routing API. |
| **Convenience Scoring System** | Calculates a **customized score** based on weighted user preferences (time, walking distance, fare cost, carpark availability, etc.). |
| **Real-Time Data Integration** | Uses **OneMap**, **LTA DataMall**, and **NEA Weather** APIs for live conditions. |
| **Interactive Map Visualization** | Visualized using **Leaflet.js** with custom popups, carpark overlays, and selectable route layers. |
| **Route Generation** | Generate routes which is retrieved from oneMap API |
| **Route Specfic Information Display** | Displays information specfic to route (traffic incident / weather). |
| **Save Route / Locations** | Saves locations for easy access |
## 🧠 App Design

### **Overview**
EasyGo adopts a **Layered / MVC Architecture**, separating the application into distinct layers for maintainability and scalability.

```
Frontend (View)
  ├── React Components (Sidebar for Location Search, Save Routes, Login Page)
  │     ...etc
Controllers (Logic Layer)
  ├── ItineraryController
  ├── ScoreCalculator 
  ├── AuthController
  │     ...etc
Data Layer (Model)
  ├── BaseItinerary
  ├── RouteLeg
  ├── Various API Response Classes
        ...etc
```



---

### **Frontend**
- Built with **Next.js + TypeScript + TailwindCSS + ShadCN + MUI**
- Pages under `/app/` serve as entry routes
- `/components/` contains reusable UI elements (Map, RouteCards, Charts)
- `/controllers/` manages API orchestration and data logic
- `/api/` provides backend logic (serverless API routes)

### **Backend / API Layer**
- Next.js API routes serve as the backend
- Integrates external APIs (OneMap, LTA, NEA)
- Controllers abstract logic and serve the frontend (facade pattern)

---

## 🧩 Design Patterns

| Pattern | Purpose | Implementation |
|----------|----------|----------------|
| **Strategy Pattern** | Allows flexible scoring algorithms | `ScoreCalculator` dynamically switches between time-based, cost-based, or hybrid weighting |
| **Factory Pattern** | Centralizes object creation and selects the correct scoring strategy based on itinerary type | ConvenienceScoreFactory.create() instantiates a ConvenienceScore with the appropriate scoring strategy (e.g., WalkingScoring, PublicScoring, DrivingScoring) |
| **Observer Pattern** | Automatic UI update on data change | React state/hooks trigger re-renders when filters or data update |


---

## 🧱 SOLID Principles

1. **Single Responsibility Principle (SRP)**  
   Each controller or service handles one concern (e.g., routing, weather, scoring).
2. **Open–Closed Principle (OCP)**  
   Easily extendable for new route types or scoring strategies without modifying existing code.
4. **Interface Segregation Principle (ISP)**  
   Each data type (Route, Carpark, Weather) uses its own lightweight interface.
5. **Dependency Inversion Principle (DIP)**  
   Controllers depend on abstractions (interfaces), not concrete service implementations.

---

## 🧰 Tech Stack

**Frontend:**
- Next.js (React + TypeScript)
- Tailwind CSS
- Leaflet.js
- MUI 

**Backend / API:**
- Next.js API Routes
- Node.js
- Supabase (Database)

**External APIs:**
- OneMap Routing API
- LTA DataMall (Carpark availability)
- NEA Weather API
- data.gov.sg

**Tools:**
- GitHub for version control and collaboration


---

## 🧠 Software Engineering Practices

| Practice | Description |
|-----------|-------------|
| **TypeScript** | Ensures strong typing, avoids ```any``` except in well-justified fallback cases |
| **Code Consistency** | ESLint + Prettier  |
| **Reusable Components** | Modular UI components and hooks for map and routing. |
| **Interface-Driven Design** | Interfaces defines contracts between modules. |

---


## 📋 Future Enhancements

- [ ] MRT incident alert integration  
- [ ] Predictive congestion scoring  
- [ ] Accessibility improvements  
- [ ] Enhanced map interactivity
- [ ] Accept Cycle type alongside Walking
- [ ] Optimise Carpark route generation


---

## 🌍 External APIs

1. **OneMap API**
   - Routing & geocoding endpoints  
   - [https://www.onemap.gov.sg/docs/](https://www.onemap.gov.sg/docs/)
2. **LTA DataMall**
   - Carpark availability  
   - [https://datamall.lta.gov.sg/](https://datamall.lta.gov.sg/)
3. **NEA Weather API**
   - 24-hour weather forecast  
   - [https://data.gov.sg](https://data.gov.sg)

---

## 🧩 Acknowledgements

- **OneMap**, **LTA DataMall**, and **data.gov** for external APIs  


---
