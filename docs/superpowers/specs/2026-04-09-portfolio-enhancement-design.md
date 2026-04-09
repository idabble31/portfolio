# Portfolio Enhancement Design
**Date:** 2026-04-09
**File:** `index.html` (single-file portfolio at `Downloads/portfolio/`)

---

## Overview

Enhance the existing personal portfolio with media embeds (YouTube / Google Drive), a new FAST-LIVO SLAM project card, product context for the Widya Robotics experience, and a Resume download button. The single-file architecture is preserved.

---

## 1. Resume Download Button

**Where:** Hero section, added to the existing `.hero-links` button row alongside "Get in Touch", "GitHub", and "LinkedIn".

**Implementation:**
- New `<a class="btn btn-ghost">` element linking to `CV Rafly Daffaldi 2025.pdf`
- PDF file placed in the same directory as `index.html`
- `download` attribute on the anchor so browsers trigger a download rather than opening inline

---

## 2. Project Cards — Layout Change

**Current:** `projects-grid` uses `repeat(auto-fill, minmax(260px, 1fr))` — compact 3-column grid.

**New:** Single-column layout (full-width cards), matching the style of the existing experience `.card` elements. Each card has the structure:
1. Icon + title + date (top)
2. Description text
3. Video embed (`.media-video` iframe for YouTube/Google Drive, or `.media` for local files)

**CSS change:** `.projects-grid` → `display: flex; flex-direction: column; gap: 1.2rem;`
**Card CSS:** `.project-card` gets `flex-direction: column` (already is), no other structural changes needed — the card naturally expands to full width.

---

## 3. New Project Card — FAST-LIVO SLAM Pipeline

**Position:** First card in the projects section (most recent work first).

**Content:**
- Icon: 🗺️
- Title: FAST-LIVO SLAM Pipeline
- Date: Jan 2026 – Present
- Role line: Remote ROS Developer · Upwork
- Description: Full SLAM pipeline implementation using the FAST-LIVO2 algorithm — covering sensor calibration (LiDAR-camera-IMU), the core SLAM mechanism, and a live monitoring dashboard.
- Media: Screen recording video (user to provide YouTube or Google Drive link)

---

## 4. Widya Robotics Experience Card Enhancement

**Add product context** immediately below the `.card-company` line:

> **Product:** [Widya Load Scanner](https://widya.ai/load-scanner/) — LiDAR-based truck volume measurement system deployed across 13 provinces in Indonesia for mining, construction, and logistics.

**Add video embed** below the bullet list (user to provide YouTube or Google Drive link).

---

## 5. Remaining Media Slots

The following existing cards have media comment placeholders. They will remain as comments until the user provides links:
- Freelance ROS Developer (Upwork) card
- R&D Engineer — PT. Summit Vision Nusantara card
- Motion Engineer — Summit Features Sdn Bhd card
- Logistic Robot Fleet project card
- Autonomous Tractor project card (already has a YouTube embed: `g1iaPkFP0VY`)
- IoT Homecare Monitor project card

---

## Out of Scope

- No new sections or nav items
- No changes to Skills, About, or Footer sections
- No backend, build tools, or frameworks — pure HTML/CSS
- No PDF viewer embed (download button only)
