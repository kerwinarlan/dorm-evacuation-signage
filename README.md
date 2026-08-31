<div align="center">

# 🚨 Sampaguita Residence Hall Evacuation Signage Generator

**Automated A4 Vector Evacuation Plan & Batch Signage Generator for Resident Rooms (AY 2026-2027)**

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![SVG](https://img.shields.io/badge/SVG-FFB13B?logo=svg&logoColor=white)](https://www.w3.org/Graphics/SVG/)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Print-Ready](https://img.shields.io/badge/Print--Ready-A4%20Landscape-28a745)](https://github.com/kerwinarlan/sampaguita-evacuation-signage)
[![UP Diliman](https://img.shields.io/badge/UP%20Diliman-Sampaguita%20Residence%20Hall-7b1113)](https://upd.edu.ph)

</div>

---

## 📌 Overview

**Sampaguita Evacuation Signage Generator** is an automated, vector-based architectural mapping engine and A4 print-batch generator built specifically for **Sampaguita Residence Hall at UP Diliman (AY 2026-2027)**.

It dynamically parses architectural floorplan coordinates for Ground Floor (GF) and Second Floor (2F) resident wings, computes localized egress paths, and generates high-resolution, print-ready emergency evacuation signage cards for **every individual resident room** (Corridors A, B, C, and D).

---

## 🎯 Why It Exists: Automated Precision vs. Manual Floorplans

In dormitory emergency planning, hand-drawn or generic one-size-fits-all evacuation diagrams fail to communicate immediate directional orientation during a crisis. Generic maps require residents to manually orient themselves on a complex macro plan, leading to panic or wrong turns in smoke-filled corridors.

This system solves the problem by dynamically generating personalized room-level signage where **"YOU ARE HERE"** is pinpointed at the exact room doorway threshold, paired with customized, student-perspective action steps.

| Problem | Solution | Result |
|---|---|---|
| **Generic Macro Floorplans** | Zonal vector cropping focused on the resident's specific wing | Immediate legibility on A4 printouts |
| **Ambiguous Room Orientation** | Callout pin placed outside the room with thick solid wall emphasis | Zero room number overlap + instant visual focus |
| **Confusing Path Graphics** | Solid continuous route lines with terminal exit arrowheads and 2F/GF broken lines | Unambiguous directional flow to safety |
| **Generic Directions** | Room-specific, student-perspective step-by-step wording | Clear 3-step action guide (e.g. "Exit your room and take the West staircase...") |

---

## 🏗 System Architecture & Pipeline

```
┌──────────────────────────────────────────────┐
│  Vector Floorplan Geometry Data (MODEL)      │
│  - Ground Floor (GF): Corridors A & D        │
│  - Second Floor (2F): Corridors B & C        │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│  Spatial Pathfinding & Guidance Engine       │
│  - Doorway threshold coordinate calculation  │
│  - Multi-segment egress vectoring            │
│  - Personalized student action step generator│
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│  Dynamic SVG & Card Render Engine            │
│  - Thick red box room location emphasis      │
│  - External "YOU ARE HERE" callout badge     │
│  - Stairwell tread step lines                │
│  - Solid 2F / Broken GF path line styles     │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│  A4 Landscape Print Batch Page Container     │
│  - PDF export via window.print()             │
│  - Instant batch generation for resident rooms│
└──────────────────────────────────────────────┘
```

---

## ✨ Key Features

- **Automated Resident Room Batching**: Instantly generates cards for all non-vacant resident rooms (`A1–A17`, `B1–B20`, `C1–C20`, `D1–D17`) while excluding administrative zones from card batching.
- **Thick Solid Room Location Emphasis**: Emphasizes the current resident room with a heavy red border box (`stroke: #dc2626`, `stroke-width: 3.5`) rendered on top of the floorplan so adjacent cells never obscure it.
- **External "YOU ARE HERE" Callout Pin**: Positioned cleanly outside the room cell (above top-row rooms, below bottom-row rooms) with a pointer tail pointing to the outer room border, ensuring 0% text overlap on room numbers.
- **Clean Continuous Route Arrows**: Draws solid black route lines (`stroke: #000000`, `stroke-width: 2.8`) with sharp terminal black arrowheads at exit doors.
- **2F-to-GF Broken Path Representation**: For 2F rooms evacuating down stairwells, the 2F portion is rendered as a solid line and the GF lobby portion as a broken/dashed line (`stroke-dasharray: 6 5`).
- **Student-Perspective Action Steps**: Generates direct 3-step instructions tailored to room orientation (e.g., *"Exit your room and take the West hallway staircase..."*, *"Exit your room and proceed down the central circular stairs..."*).
- **Stairwell Tread Detail**: Renders horizontal step lines across Boys Stairwell, Girls Stairwell, and Circular Stairs for architectural fidelity.

---

## 📂 Repository Structure

```
.
├── index.html                           # Main Print-Batch Generator & PDF Signage Application
├── SAMPAGUITA_MODEL_V2_PRINT_BATCH.html # Primary A4 Landscape Batch Generator
├── EVACUATION_SIGNAGE_PIPELINE.html     # Interactive Egress Simulator & Pathfinding Pipeline
├── SAMPAGUITA_MODEL_V1.html             # Single Card Signage Model (V1)
├── SAMPAGUITA_FLOORPLANS.html           # Full Floorplan Visualizer (GF & 2F)
├── FLOORPLAN_MAPPER.html               # Interactive Coordinate Mapper & Zone Plotter
├── FLOORPLAN_COORDINATES_TEMPLATE.md    # Coordinate Mapping Reference Guide
├── SAMPA_MASTERPLAN_2026.md             # Sampaguita Residence Hall Safety Masterplan
├── TRANSPOSED_GF_MODEL.md               # Ground Floor Vector Geometry Reference
├── TRANSPOSED_2F_MODEL.md               # Second Floor Vector Geometry Reference
├── VISUALIZE_GF.html                    # Ground Floor Vector Visualizer
├── VISUALIZE_2F.html                    # Second Floor Vector Visualizer
├── Sampa-logo.png                       # Sampaguita Residence Hall Official Seal
└── Sampaguita Floor Plans.pdf           # Original Architectural Blueprint Reference
```

---

## 🚀 How to Use

### 1. View & Print Resident Room Signage (PDF)

1. Open `index.html` or `SAMPAGUITA_MODEL_V2_PRINT_BATCH.html` in any web browser (Chrome, Edge, Safari, Firefox).
2. Click the **🖨 Print Resident Room Signage (PDF)** button at the top right (or press `Ctrl+P` / `Cmd+P`).
3. In the browser print dialog:
   - **Destination**: *Save as PDF*
   - **Paper Size**: *A4*
   - **Layout**: *Landscape*
   - **Margins**: *None* (or *Default / 10mm*)
   - **Background graphics**: *Checked* (enabled)
4. Click **Save** to export a clean PDF containing printable evacuation signage cards for every resident room!

### 2. Interactive Coordinate Mapping & Editing

- Open `FLOORPLAN_MAPPER.html` to plot new room coordinates or adjust architectural boundaries.
- Open `EVACUATION_SIGNAGE_PIPELINE.html` to run interactive pathfinding simulations across corridors.

---

## 📋 Compliance & Standards Alignment

Designed in alignment with:
- **ISO 7010**: Graphical symbols — Safety colours and safety signs.
- **NFPA 101**: Life Safety Code — Means of Egress signage guidelines.
- **UP Diliman Dormitory Safety Policy**: Resident room emergency signage guidelines (AY 2026-2027).

---

## 📄 License

Developed for **Sampaguita Residence Hall, University of the Philippines Diliman**. Distributed for educational, institutional, and emergency safety deployment.
