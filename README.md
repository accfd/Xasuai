# XASUAI — Executive Lunar Landing Site Navigator

> **NASA Space Apps Challenge 2026**
>
> **Challenge:** Lunar Landing Site Navigator  
> **Team:** PILAR KARYA  
> **Project Tagline:** *3 Steps to Easier Lunar Landing*  
> **Target Location:** Mons Mouton Crest, Lunar South Pole (-84.9°S, 33.3°W)  
> **Repository:** https://github.com/accfd/Xasuai  
> **Languages:** English and Bahasa Indonesia

*A formula-based lunar mission planning platform that identifies safer landing opportunities through environmental analysis, terrain assessment, and flight trajectory simulation.*

---

## 1. Project Overview

### The Challenge

Landing a spacecraft near the Moon's South Pole presents several environmental and technical challenges. Low solar elevation angles create extended shadows and extreme temperature variations, while crater rims and elevated terrain can obstruct direct radio communication between a landing site and Earth.

These conditions make landing-site selection, mission scheduling, and spacecraft navigation particularly challenging for future lunar exploration missions.

### Our Solution

**XASUAI (Executive Lunar Landing Site Navigator)** is a web-based lunar mission planning platform designed to support safer landing decisions at Mons Mouton Crest, one of the candidate landing regions in the lunar South Pole.

The platform integrates scientific datasets, mathematical calculations, and interactive visualizations into three interconnected solutions:

**Solution 1 — Landing Window Recommendation**

Identifies suitable launch and landing opportunities by analyzing solar illumination, Earth visibility, and environmental conditions using NASA JPL Horizons ephemeris data and a Multi-Criteria Decision Analysis (MCDA) approach.

**Solution 2 — Terrain Visualization and Topographic Analysis**

Evaluates surface elevation, slope conditions, and communication line-of-sight using NASA Lunar Reconnaissance Orbiter (LRO) Lunar Orbiter Laser Altimeter (LOLA) Digital Elevation Model (DEM) data.

**Solution 3 — Full Mission Simulation and Landing Dynamics**

Simulates the spacecraft journey from Earth departure to lunar touchdown, including translunar injection, orbital descent, and powered landing maneuvers using numerical trajectory calculations.

Together, these three solutions provide an integrated approach to evaluating landing conditions and understanding the challenges of lunar mission planning.

---

## 2. How to Run the Application

Follow these steps to install and run XASUAI locally.

### Prerequisites

- Python 3.10 or later.
- Git.
- A modern web browser.
- Internet connection for accessing external resources when required.

### Step 1 — Clone the Repository

```bash
git clone https://github.com/accfd/Xasuai.git
cd Xasuai
```

### Step 2 — Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**

```bash
venv\Scripts\activate
```

**macOS / Linux:**

```bash
source venv/bin/activate
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4 — Launch XASUAI

Run the primary application launcher:

```bash
python main.py
```

Alternatively, start the web server directly:

```bash
python web/server.py
```

Once the server starts, access the application through:

**http://127.0.0.1:8888**

### Language Settings

XASUAI supports two languages:

- English (EN)
- Bahasa Indonesia (ID)

Use the language selector in the upper-right corner of the navigation bar to switch between languages.

---

## 3. Application Features

XASUAI consists of three main solutions accessible through its web interface.

### 3.1 Solution 1 — Landing Window Recommendation

**Route:** `/rekomendasi`

This module evaluates potential launch and landing schedules by examining the relative positions of the Sun and Earth, solar elevation angles, and terrain obstruction conditions.

**How to use:**

1. Open the **Recommendation** menu.
2. Select the intended mission month and year.
3. Click **Calculate Recommended Schedule**.
4. Observe the sequential telemetry analysis process.
5. Review the recommended launch and landing schedule.
6. Open the saved recommendation results to examine the MCDA comparison between alternative landing locations.

**Key capabilities:**

- Accesses NASA JPL Horizons ephemeris data.
- Evaluates solar elevation and illumination conditions.
- Analyzes potential crater-rim obstructions.
- Identifies suitable mission timing.
- Compares alternative landing locations using MCDA scoring.

**Illustrative calculation result:**

| Parameter | Result |
|---|---|
| Earth Departure | November 11, 2026, 08:00 UTC |
| Lunar Landing | November 15, 2026, 08:00 UTC |
| Estimated Travel Duration | 4 days |
| Solar Illumination | 100% continuous illumination |
| Communication | Direct line-of-sight available |
| Overall Assessment | Optimal and Safe |

### 3.2 Solution 2 — Terrain Visualization and Topographic Analysis

**Route:** `/visualisasi`

This module provides interactive terrain inspection through three visualization modes.

**Mode 1 — 3D Orbital Navigation**

- Displays an interactive 3D representation of the Moon.
- Provides camera altitude and target tracking information.
- Includes the **Fly-To Mons Mouton** feature to navigate toward the selected landing coordinates.
- Visualizes the target location from an orbital perspective.

**Mode 2 — 2D Terrain and Slope Inspection**

Uses NASA LOLA DEM data to display surface elevation and terrain characteristics.

Users can zoom and pan across the terrain map to inspect the proposed landing region.

Key terrain indicators include:

| Parameter | Calculated Value |
|---|---:|
| Surface Slope | 0.08° |
| Peak Elevation | +5,920 m |
| Solar Illumination | 100% |
| Terrain Assessment | GO — SAFE |

The calculated slope is below the 10° safety threshold referenced in the project's evaluation criteria.

**Mode 3 — 3D Topography and Radio Communication Analysis**

- Displays a 3D terrain representation of Mons Mouton Crest.
- Provides selectable visualization layers:
  - MCDA Feasibility Zones.
  - LOLA DEM Elevation.
  - Slope Safety.
- Visualizes the direct communication line between the landing site and Earth.
- Evaluates the available line-of-sight clearance above surrounding terrain.

The calculated communication clearance is approximately **+12.35°** above the highest obstructing terrain boundary.

### 3.3 Solution 3 — Full Mission Simulation and Landing Dynamics

**Route:** `/simulasi`

This module demonstrates the spacecraft's flight sequence from Earth departure to lunar touchdown.

The mission is divided into three major phases:

1. **Trans-Lunar Injection (TLI):** The spacecraft initiates its transfer trajectory from Earth orbit toward the Moon.
2. **Polar Orbit Descent:** The spacecraft approaches the lunar landing region through its planned descent trajectory.
3. **Powered Descent Initiation (PDI):** The spacecraft performs its final braking and landing maneuvers.

**How to use:**

1. Open the **Simulation** menu.
2. Review the three mission phases.
3. Click **Launch Full 3D Mission Simulator**.
4. The simulator opens in a new browser tab through `simulator.html`.
5. Observe the spacecraft's movement and flight instrumentation during the landing sequence.

**Flight instrumentation includes:**

- Vertical velocity (\(V_z\)).
- Horizontal velocity (\(V_x\)).
- Remaining propellant.
- Spacecraft altitude.
- Touchdown safety indicator.

The simulator uses a WebGL-based 3D environment powered by Three.js, with a target vertical touchdown velocity of \(V_z \leq 1.0\text{ m/s}\).

---

## 4. Scientific Data and Methodology

XASUAI incorporates publicly available NASA datasets and mathematical methods to support its landing-site evaluation and mission simulation.

### 4.1 Scientific Data Sources

| Dataset / Resource | Application |
|---|---|
| NASA LRO LOLA DEM | Surface elevation, terrain mapping, and slope analysis |
| NASA JPL Horizons DE441 | Sun and Earth position calculations and mission timing |
| NASA Moon Trek | Geographic inspection and coordinate verification |
| NASA Artemis Landing Regions Study | Background reference for lunar landing-site selection |
| NASA NAIF SPICE Toolkit | Reference for astronomical coordinate systems and transformations |

### 4.2 Mathematical Approaches

**Multi-Criteria Decision Analysis (MCDA)**

Used to evaluate and compare potential landing locations based on multiple environmental and operational criteria.

**Terrain Gradient Analysis**

Uses elevation differences from LOLA DEM data to calculate terrain slopes and assess landing surface conditions.

**Horizon Raymarching**

Analyzes the surrounding terrain horizon to evaluate potential obstructions to direct communication with Earth.

**Orbital Mechanics**

Applies two-body orbital mechanics to estimate translunar injection requirements.

**Runge-Kutta Numerical Integration (RK45)**

Used for numerical trajectory calculations during spacecraft descent and powered landing maneuvers.

### 4.3 Scientific Evaluation Results

| Evaluation Parameter | Method / Data Source | Calculated Result |
|---|---|---:|
| Terrain Elevation | NASA LRO LOLA DEM | +5,920 m |
| Surface Slope | DEM Gradient Analysis | 0.08° |
| Solar and Earth Position | NASA JPL Horizons DE441 | 336-hour analysis |
| Communication Clearance | 360° Horizon Raymarching | +12.35° |
| Translunar Injection | Two-Body Orbital Mechanics | +3.05 km/s |
| Vertical Touchdown Velocity | RK45 Numerical Integration | 0.80 m/s |

These calculations form the basis of XASUAI's environmental assessment and mission simulation.

---

## 5. Technology Stack

XASUAI combines Python-based scientific computation with web technologies for interactive visualization.

| Category | Technologies |
|---|---|
| Programming Language | Python, JavaScript |
| Backend | Tornado |
| Frontend | HTML, CSS, JavaScript |
| 3D Visualization | Three.js, WebGL |
| Desktop Interface | PyQt6 |
| Scientific Computation | NumPy, SciPy |
| Astronomical Data | NASA JPL Horizons |
| Terrain Data | NASA LRO LOLA DEM |
| Numerical Methods | MCDA, RK45, Orbital Mechanics |
| Development Tools | Git, GitHub |

---

## 6. Project Structure

```text
Xasuai/
├── web/
│   ├── index.html
│   ├── simulator.html
│   ├── server.py
│   ├── js/
│   │   └── app.js
│   ├── css/
│   │   └── style.css
│   └── data/
├── src/
│   ├── site_evaluator.py
│   ├── trajectory_calculator.py
│   └── visualizer_ui.py
├── data/
│   ├── quickmap-lroc.png
│   ├── quickmap-lroc.vrt
│   ├── horizons_cache.json
│   ├── moon_1024.jpg
│   └── earth_blue_marble.jpg
├── tests/
│   ├── test_xsasuai_core.py
│   └── test_web_server.py
├── utilities/
├── scripts/
├── solar_earth_horizon_planner.py
├── scan_terrain.py
├── simulate_landing.py
├── horizons_api.py
├── mission_state.py
├── constants.py
├── main.py
├── requirements.txt
└── README.md
```

---

## 7. Additional Application Modes

In addition to the web application, XASUAI provides several execution modes through `main.py`.

| Command | Application Mode | Description |
|---|---|---|
| `python main.py` | Web Console | Launches the web dashboard and Tornado server |
| `python main.py --desktop` | Desktop GUI | Opens the native PyQt6 interface |
| `python main.py --sim` | 3D Flight Simulator | Launches the WebGL landing simulator |
| `python main.py --eval` | CLI Batch Evaluator | Executes MCDA calculations through the terminal |
| `python main.py --help` | Help | Displays available commands and arguments |

---

## 8. NASA Data Sources and References

The project utilizes publicly accessible scientific resources to support its environmental analysis and lunar mission planning.

1. **NASA LRO LOLA DEM**
   - Lunar elevation and topographic data.
   - [NASA LROC QuickMap](https://quickmap.lroc.asu.edu/)
   - [NASA PDS Geosciences Node](https://pds-geosciences.wustl.edu/missions/lro/lola.htm)

2. **NASA JPL Horizons System**
   - Astronomical ephemeris data for Sun and Earth position calculations.
   - [JPL Horizons](https://ssd.jpl.nasa.gov/horizons/)
   - [Horizons API Documentation](https://ssd-api.jpl.nasa.gov/doc/horizons.html)

3. **NASA Moon Trek**
   - Interactive lunar geographic exploration and coordinate inspection.
   - [NASA Moon Trek](https://trek.nasa.gov/moon/)

4. **NASA Artemis Landing Regions Study**
   - Reference for candidate lunar landing regions, including Mons Mouton.
   - [NASA Artemis III Landing Regions Announcement](https://www.nasa.gov/news-release/nasa-provides-update-on-artemis-iii-moon-landing-regions/)

5. **NASA NAIF SPICE Toolkit**
   - Reference for astronomical coordinate systems and space navigation calculations.
   - [NASA NAIF Toolkit](https://naif.jpl.nasa.gov/naif/toolkit.html)

---

## 9. AI Usage Disclosure

XASUAI was developed through the team's original conceptual work, research, and technical implementation.

Artificial intelligence tools were used as development support in selected activities, including:

- Assisting with programming syntax and code development.
- Supporting code refactoring and module organization.
- Assisting in the preparation of the bilingual language system.
- Generating and stylizing selected visual assets and logo elements using Gemini and Canva.

The project's core concept, problem identification, selection of Mons Mouton Crest as the target landing region, mathematical approaches, and integration of the three proposed solutions were developed by the PILAR KARYA team.

AI-generated visual assets are identified as such, and the team acknowledges the use of AI tools in the development process.

---

## 10. Project Impact and Future Potential

XASUAI aims to make lunar landing-site evaluation and mission planning more accessible through an integrated and interactive platform.

Its potential contributions include:

- **Safer Landing Assessment:** Supporting the identification of suitable landing regions through terrain and environmental evaluation.
- **Mission Scheduling:** Helping evaluate launch and landing opportunities based on solar illumination and communication conditions.
- **Scientific Visualization:** Making complex astronomical and topographic information easier to understand through interactive 2D and 3D representations.
- **Mission Simulation:** Demonstrating the relationship between spacecraft trajectory, velocity, and landing conditions.
- **Educational Value:** Providing an interactive learning platform for understanding lunar exploration and astrodynamics.

Future development could incorporate additional landing-site datasets, more comprehensive environmental constraints, and improved spacecraft dynamics models.

---

## 11. Team and Attribution

**Team Name:** PILAR KARYA  
**Competition:** NASA Space Apps Challenge 2026  
**Selected Challenge:** Lunar Landing Site Navigator  
**Local Event:** Purwokerto, Indonesia

**Team Members:**

1. Syaifa Mulyadi, S.T., M.T.
2. Muhammad Alif Abdam
3. Mutiara Ersa Christine Dawolo
4. Fuadi Dhiyaulhaq
5. Arsyad Mulya Rahman
6. Muhammad Nabil Surya Andyka

**Visual Assets:** Selected logos and visual elements were AI-generated and stylized using Gemini and Canva.

**License:** MIT License

---

*Explore. Create. Solve.*

**PILAR KARYA | NASA Space Apps Challenge 2026**
