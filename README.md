# daikibo-factory-downtime-analysis
Tableau analysis of Daikibo factory telemetry data from the Deloitte Data Analytics Job Simulation, focusing on machine downtime by factory and device type.
# Deloitte Data Analytics Job Simulation – Daikibo Telemetry

This repository contains my work for the **Deloitte Data Analytics Job Simulation (Forage)**, focused on analyzing Daikibo's factory telemetry data and visualizing machine downtime using Tableau.[file:61]

## Project Overview

Daikibo is a manufacturing client experiencing issues with machine reliability and production downtime.[file:61]  
The goal of this task was to use telemetry data to:

- Quantify downtime across factories.
- Identify which device types contribute most to downtime.
- Build clear visuals that could support data‑driven decisions.

## Data

- Source: `daikibo-telemetry-data.json` (provided in the simulation).
- Content: Telemetry messages with fields such as:
  - `Factory`
  - `Device Type`
  - `Status` (healthy / unhealthy)
  - `Timestamp`
  - Temperature and location details (area, city, country, section).[file:61]

Each telemetry message represents a 10‑minute interval.

## Analysis Steps

1. Imported the JSON telemetry data into Tableau and enabled all schema levels for analysis.[file:61]
2. Created a calculated measure **`Unhealthy`**:

   ```tableau
   IF [Status] = 'unhealthy' THEN 10 ELSE 0 END
   ```

   This assigns **10 minutes of potential downtime** to each unhealthy status message.[file:61]

3. Built a bar chart **“Down Time per Factory”** using:
   - Columns: `Factory`
   - Rows: `SUM(Unhealthy)`[file:61]

4. Built a second bar chart **“Down Time per Device Type”** using:
   - Columns: `Device Type`
   - Rows: `SUM(Unhealthy)`[file:61]

5. Created a **dashboard** combining both charts and set the factory chart to **“Use as Filter”**, so selecting a factory filters the device‑type downtime view.[file:61]

## Files in this Repository

- `README.md` – Project description and documentation.
- `screenshots/` – Dashboard screenshots (e.g., factory with highest downtime).
- `tableau/` – Exported Tableau workbook (`.twb` / `.twbx`) with all sheets and dashboard.
- `notes/` (optional) – Any personal notes or additional analysis.

> Note: The original raw JSON file from the simulation may not be publicly shareable, so this repo focuses on my Tableau workbook, screenshots, and documentation.

## Key Learnings

- Connecting and modeling **JSON** data in Tableau.[file:61]
- Creating **calculated fields** to convert status logs into measurable downtime.[file:61]
- Designing **interactive dashboards** that let users filter by factory and drill into device‑level performance.[file:61]

## Acknowledgements

This work is based on the **Deloitte Data Analytics Job Simulation** hosted on **Forage**.  
All client names and datasets (e.g., Daikibo) are part of the simulation material.
