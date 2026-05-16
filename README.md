# Seasonal Service Requests & Quality of Life in Bloomington, Indiana

> An interactive data visualization exploring how seasonal shifts shape citizen service demands in Bloomington, IN (2020–2025).

**Course:** INFO I 590: Data Visualization (Fall 2025) — Indiana University Bloomington
**Team:** Pixel and Plot

---

## 🔗 Live Visualization

**[View Interactive HTML Visualization](https://drive.google.com/file/d/1JAQD1AQHE8feZa1SyJo55f1kFGCgREvu/view?usp=drive_link)**

> Download the HTML file and open it in a browser for the full interactive experience.

---

## Problem Statement

Bloomington's quality of life is shaped by seasonal forces — winter storms, spring vegetation growth, summer outdoor activity, and fall leaf accumulation all generate distinct waves of citizen service requests. Yet city services traditionally operate reactively, responding to issues after they arise rather than anticipating them. Without a clear picture of *when* and *where* service demands peak, resource allocation remains inefficient and residents' needs go unmet during critical windows.

---

## Project Objective

**Narrative Question:** *"How do seasonal service demands impact the quality of life for Bloomington's residents?"*

To analyze multi-year citizen service request records and identify recurring seasonal patterns across Bloomington neighborhoods — enabling the city to shift from a reactive to a **predictive service model**.

---

## Method Used

### Dataset
- **Source:** [City of Bloomington Open311 Service Request Dataset](https://data.bloomington.in.gov/) (publicly available)
- **Scope:** 2020–2025 (filtered from a full dataset spanning back to 2002)
- **Key fields:** `service_request_id`, `requested_datetime`, `updated_datetime`, `service_name`, `address`, `lat/long`, `status`, `agency_responsible`

### Data Cleaning & Feature Engineering
- Removed duplicate records and filtered out test/system-generated entries
- Handled missing timestamps; used `updated_datetime` as the primary date reference (0 null values)
- Standardized service category labels and created a new `service_category` column (Environmental, Transportation, City Administration, etc.)
- Added a `season` column (Winter, Spring, Summer, Fall) for seasonal trend analysis
- Created `area_category` based on zip code regions: Downtown/IU Campus, Residential, Industrial, Suburban, Rural
- Parsed zip codes from address fields to recover missing location data
- Dropped analytically irrelevant columns (`SLA_Days`, `SLA_Diff_Days`, `Georeference`)
- Reduced event types from raw categories to grouped service categories for readability

### Visualizations (Plotly + Python → HTML export)

Three complementary visualizations tell a layered story:

**1. Sunburst Diagram (Interactive)**
Shows how service request volume is distributed across area categories and service categories, filterable by season. Allows users to drill down from neighborhood → category → service count in a single click.

**2. Sankey (Parallel Categories) Diagram (Interactive)**
Traces how service requests flow from area → service category → service name across seasons. Reveals which neighborhoods drive which complaints and highlights bottlenecks in service delivery.

**3. Heatmap (Static)**
Displays total seasonal service intensity per zip code region. Provides a quick, cognitive-load-light overview before users engage with the interactive charts.

The hybrid static + interactive approach was chosen deliberately: interactive views reward exploration, while the static heatmap gives quick-glance viewers an immediate takeaway.

---

## Results

- Summer and Spring showed the highest volumes of environmental and transportation service requests across most neighborhoods
- Downtown/IU Campus and Residential areas consistently generated the highest request volumes across all seasons
- The Sankey diagram revealed that waste/sanitation and vegetation management dominate summer flows, while winter spikes in road repair and snow removal
- Narrowing to 2020–2025 improved data quality significantly — older records had high rates of missing neighborhood and completion data
- Grouping 50+ service types into categories was essential for Sankey readability without losing analytical depth

---

## Design Decisions

- **Color encoding:** Warmer/saturated tones for area categories; deeper tones for service categories. Green for environmental issues for intuitive mapping. Color-blind-safe palette (avoids red-green combinations)
- **Interactivity:** Season filter applied globally across all three views for consistency
- **Export format:** HTML to preserve interactivity without requiring a live server or dashboard tool

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-blue) ![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Viz-purple) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-green)

`Python` · `Plotly` · `Pandas` · `Jupyter Notebook` · `HTML`

---

## Team

Rujul Jadav · Deeksha Bapura · Rithvik Mysore Suresh · Parvez Shaik · Ishwari Dawkhar

*Team: Pixel and Plot — INFO I 590: Data Visualization, Luddy School of Informatics, Computing, and Engineering, Indiana University Bloomington*
