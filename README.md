<div align="center">

# 🚨 Dorm Evacuation Signage Generator

**Automated A4 Vector Evacuation Plan & Batch Signage Generator for Dormitories and Residential Buildings**

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![SVG](https://img.shields.io/badge/SVG-FFB13B?logo=svg&logoColor=white)](https://www.w3.org/Graphics/SVG/)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Print-Ready](https://img.shields.io/badge/Print--Ready-A4%20Landscape-28a745)](https://github.com/kerwinarlan/dorm-evacuation-signage)

</div>

---

## 📌 Overview

**Dorm Evacuation Signage Generator** is an automated, vector-based architectural mapping engine and A4 print-batch generator designed to produce room-by-room emergency evacuation plans for dormitories, student residences, and multi-story residential buildings.

It parses vector floorplan geometries, calculates localized egress paths for each resident room, and generates print-ready, high-resolution signage cards complete with customized action steps, room callout pins, and clear exit vectors.

---

## 🎯 Why It Exists: Automated Precision vs. Manual Floorplans

In dormitory emergency planning, hand-drawn or generic one-size-fits-all evacuation diagrams fail to communicate immediate directional orientation during a crisis. Generic maps require residents to manually orient themselves on a complex macro plan, leading to panic or wrong turns in smoke-filled corridors.

This system solves the problem by dynamically generating personalized room-level signage where **"YOU ARE HERE"** is pinpointed at the exact room doorway threshold, paired with customized, resident-perspective action steps.

| Problem | Solution | Result |
|---|---|---|
| **Generic Macro Floorplans** | Zonal vector cropping focused on the resident's specific wing | Immediate legibility on A4 printouts |
| **Ambiguous Room Orientation** | Callout pin placed outside the room with thick solid wall emphasis | Zero room number overlap + instant visual focus |
| **Confusing Path Graphics** | Solid continuous route lines with terminal exit arrowheads and multi-floor broken lines | Unambiguous directional flow to safety |
| **Generic Directions** | Room-specific, resident-perspective step-by-step wording | Clear 3-step action guide (e.g. "Exit your room and take the West staircase...") |

---

## 🏗 System Architecture & Pipeline

```
┌──────────────────────────────────────────────┐
│  Vector Floorplan Geometry Data (MODEL)      │
│  - Configurable Room & Corridor Polygons     │
│  - Floor-by-Floor Architectural Layers       │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│  Spatial Pathfinding & Guidance Engine       │
│  - Doorway threshold coordinate calculation  │
│  - Multi-segment egress vectoring            │
│  - Personalized action step generator        │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│  Dynamic SVG & Card Render Engine            │
│  - Thick red box room location emphasis      │
│  - External "YOU ARE HERE" callout badge     │
│  - Stairwell tread step lines                │
│  - Solid upper-floor / Broken ground path    │
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

- **Automated Resident Room Batching**: Instantly generates cards for all resident rooms while excluding administrative or non-occupancy zones from card batching.
- **Thick Solid Room Location Emphasis**: Emphasizes the current resident room with a heavy red border box (`stroke: #dc2626`, `stroke-width: 3.5`) rendered on top of the floorplan so adjacent cells never obscure it.
- **External "YOU ARE HERE" Callout Pin**: Positioned cleanly outside the room cell (above top-row rooms, below bottom-row rooms) with a pointer tail pointing to the outer room border, ensuring 0% text overlap on room numbers.
- **Clean Continuous Route Arrows**: Draws solid black route lines (`stroke: #000000`, `stroke-width: 2.8`) with sharp terminal black arrowheads at exit doors.
- **Multi-Floor Broken Path Representation**: For upper-floor rooms evacuating down stairwells, the upper-floor portion is rendered as a solid line and the ground-floor portion as a broken/dashed line (`stroke-dasharray: 6 5`).
- **Resident-Perspective Action Steps**: Generates direct 3-step instructions tailored to room orientation (e.g., *"Exit your room and take the West hallway staircase..."*, *"Exit your room and proceed down the central circular stairs..."*).
- **Stairwell Tread Detail**: Renders horizontal step lines across wing stairwells and circular stairs for architectural fidelity.
- **Easily Reproducible & Adaptable**: Replace `MODEL` coordinates in `index.html` to deploy for any dormitory or building geometry.

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
├── SAMPA_MASTERPLAN_2026.md             # Dormitory Safety Masterplan
├── TRANSPOSED_GF_MODEL.md               # Ground Floor Vector Geometry Reference
├── TRANSPOSED_2F_MODEL.md               # Second Floor Vector Geometry Reference
├── VISUALIZE_GF.html                    # Ground Floor Vector Visualizer
├── VISUALIZE_2F.html                    # Second Floor Vector Visualizer
└── Sampa-logo.png                       # Dormitory Seal Reference Asset
```

---

## 🚀 How to Use

### 1. View & Print Resident Room Signage (PDF)

1. Open `index.html` in any modern web browser (Chrome, Edge, Safari, Firefox).
2. Click the **🖨 Print Resident Room Signage (PDF)** button at the top right (or press `Ctrl+P` / `Cmd+P`).
3. In the browser print dialog:
   - **Destination**: *Save as PDF*
   - **Paper Size**: *A4*
   - **Layout**: *Landscape*
   - **Margins**: *None* (or *Default / 10mm*)
   - **Background graphics**: *Checked* (enabled)
4. Click **Save** to export a clean PDF containing printable evacuation signage cards for every resident room!

### 2. Adapting for a New Building or Dormitory

1. Open `FLOORPLAN_MAPPER.html` in your browser to interactively plot room coordinates from your floorplan blueprint.
2. Replace the `MODEL` object in `index.html` with your building's polygon coordinates.
3. Open `index.html` to generate batch evacuation signage cards for your building!

---

## 📋 Compliance & Standards Alignment

Designed in alignment with:
- **ISO 7010**: Graphical symbols — Safety colours and safety signs.
- **NFPA 101**: Life Safety Code — Means of Egress signage guidelines.

---

## 📄 License

MIT License. Open-source and free for institutional, residential, and emergency safety deployment.
