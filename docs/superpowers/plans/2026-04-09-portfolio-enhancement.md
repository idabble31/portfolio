# Portfolio Enhancement Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Enhance the single-file portfolio with a resume download button, full-width project cards, FAST-LIVO SLAM work in the Freelance experience card, Widya Load Scanner product context, and a new PicoBot project card.

**Architecture:** All changes are in `index.html`. No build system or frameworks. CSS lives in a `<style>` block in `<head>`. A renamed copy of the CV PDF (`resume.pdf`) is added to the portfolio directory alongside `index.html`.

**Tech Stack:** HTML5, CSS3 (custom properties, flexbox)

---

### Task 1: Add resume PDF and Download Resume button

**Files:**
- Add: `Downloads/portfolio/resume.pdf`
- Modify: `Downloads/portfolio/index.html` (`.hero-links` div, around line 267)

- [ ] **Step 1: Copy CV PDF to portfolio folder**

```bash
cp "C:/Users/HP/Documents/CV Rafly Daffaldi 2025.pdf" "C:/Users/HP/Downloads/portfolio/resume.pdf"
```

- [ ] **Step 2: Add Download Resume button to hero**

In `index.html`, find the `.hero-links` div (around line 267). Replace:
```html
        <div class="hero-links">
          <a href="mailto:rafly.daffaldi@gmail.com" class="btn btn-primary">Get in Touch</a>
          <a href="https://github.com/idabble31" target="_blank" class="btn btn-ghost">GitHub</a>
          <a href="https://www.linkedin.com/in/rdaffaldi" target="_blank" class="btn btn-ghost">LinkedIn</a>
        </div>
```
With:
```html
        <div class="hero-links">
          <a href="mailto:rafly.daffaldi@gmail.com" class="btn btn-primary">Get in Touch</a>
          <a href="resume.pdf" download class="btn btn-ghost">Download Resume</a>
          <a href="https://github.com/idabble31" target="_blank" class="btn btn-ghost">GitHub</a>
          <a href="https://www.linkedin.com/in/rdaffaldi" target="_blank" class="btn btn-ghost">LinkedIn</a>
        </div>
```

- [ ] **Step 3: Verify in browser**

Open `index.html`. Hero should show four buttons. Clicking "Download Resume" prompts a PDF download (not an in-browser open).

- [ ] **Step 4: Commit**

```bash
cd "C:/Users/HP/Downloads/portfolio"
git add index.html resume.pdf
git commit -m "feat: add resume download button to hero"
```

---

### Task 2: Change project cards to full-width layout

**Files:**
- Modify: `Downloads/portfolio/index.html` (`.projects-grid` CSS rule, around line 143)

- [ ] **Step 1: Update `.projects-grid` CSS**

Find:
```css
    .projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 1.2rem; }
```
Replace with:
```css
    .projects-grid { display: flex; flex-direction: column; gap: 1.2rem; }
```

- [ ] **Step 2: Verify in browser**

Projects section should show cards stacked full-width (matching the experience cards), not in a 3-column grid.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: change project cards to full-width single-column layout"
```

---

### Task 3: Add product context to Widya Robotics card

**Files:**
- Modify: `Downloads/portfolio/index.html` (CSS block + Widya experience card, around lines 138 and 305)

- [ ] **Step 1: Add `.card-product` CSS rule**

In the `<style>` block, after the `.card-company` rule (around line 138), add:
```css
    .card-product { font-size: 0.85rem; color: var(--muted); margin-bottom: 0.8rem; }
    .card-product a { color: var(--accent); }
```

- [ ] **Step 2: Add product blurb to Widya card**

Find:
```html
          <div class="card-company">Widya Robotics — Sleman, D.I. Yogyakarta</div>
```
Replace with:
```html
          <div class="card-company">Widya Robotics — Sleman, D.I. Yogyakarta</div>
          <p class="card-product"><strong>Product:</strong> <a href="https://widya.ai/load-scanner/" target="_blank">Widya Load Scanner</a> — LiDAR-based truck volume measurement system deployed across 13 provinces in Indonesia for mining, construction, and logistics.</p>
```

- [ ] **Step 3: Replace verbose media comment with clean placeholder**

Find the entire `<!--` comment block that starts with `═══ HOW TO ADD MEDIA TO THIS CARD ═══` inside the Widya card (between the closing `</ul>` and closing `</div>`) and replace it with:
```html
          <!-- VIDEO: Paste your embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 4: Verify in browser**

The Widya card should show the product line in muted text with a blue "Widya Load Scanner" link, sitting between the company name and bullet points.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: add Widya Load Scanner product context to experience card"
```

---

### Task 4: Add FAST-LIVO bullet and video placeholder to Freelance ROS Developer card

**Files:**
- Modify: `Downloads/portfolio/index.html` (Freelance ROS Developer card, around lines 348–364)

- [ ] **Step 1: Add FAST-LIVO bullet point**

Find the `<ul>` inside the Freelance ROS Developer card:
```html
          <ul>
            <li>Implemented a multi-agent R3Live++ configuration for synchronized SLAM across multiple sensors.</li>
            <li>Developed a robust backend data saver for high-throughput sensor serialization and data integrity.</li>
          </ul>
```
Replace with:
```html
          <ul>
            <li>Implemented a multi-agent R3Live++ configuration for synchronized SLAM across multiple sensors.</li>
            <li>Developed a robust backend data saver for high-throughput sensor serialization and data integrity.</li>
            <li>Implementing a full SLAM pipeline using the FAST-LIVO2 algorithm — covering LiDAR-camera-IMU sensor calibration, core SLAM mechanism, and a live monitoring dashboard.</li>
          </ul>
```

- [ ] **Step 2: Replace verbose media comment with clean placeholder**

Find the entire `<!--` comment block starting with `═══ HOW TO ADD MEDIA TO THIS CARD ═══` inside the Freelance card and replace with:
```html
          <!-- VIDEO: Paste your FAST-LIVO screen recording embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 3: Verify in browser**

The Freelance ROS Developer card should now show three bullet points, with the FAST-LIVO entry as the third.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add FAST-LIVO SLAM bullet and video slot to freelance experience card"
```

---

### Task 5: Add PicoBot Rehabilitation Robot project card

**Files:**
- Modify: `Downloads/portfolio/index.html` (projects section `.projects-grid`, around line 427)

- [ ] **Step 1: Add PicoBot card as first card in the projects grid**

Find the opening of the projects grid content — the first `<div class="project-card">` (the Logistic Robot Fleet card). Insert the PicoBot card immediately before it:
```html
        <div class="project-card">
          <div class="proj-icon">🦿</div>
          <h3>PicoBot Rehabilitation Robot</h3>
          <div class="proj-date">Aug 2023 – Sep 2024 · Embedded Systems Engineer</div>
          <p>A rehabilitation robot designed to help post-stroke patients regain lower-limb mobility by guiding feet through controlled, natural walking movements. Uses a BLDC motor near the ankle for foot actuation. Patients connect via Bluetooth to a custom mobile app to select training modes (basic, walking, or advanced) tailored to their recovery stage.</p>
          <!-- IMAGE: Place your photo file in the portfolio folder, then uncomment below -->
          <!-- <div class="media"><img src="picobot.jpg" alt="PicoBot Rehabilitation Robot" /></div> -->
          <!-- VIDEO: Paste your embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
        </div>

```

- [ ] **Step 2: Verify in browser**

Projects section should now show four full-width cards in this order: PicoBot, Logistic Robot Fleet, Autonomous Tractor, IoT Homecare Monitor.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add PicoBot rehabilitation robot project card"
```

---

### Task 6: Simplify remaining verbose media comments

**Files:**
- Modify: `Downloads/portfolio/index.html` (R&D Engineer card, Motion Engineer card, Logistic Robot Fleet card, IoT Homecare Monitor card)

The Autonomous Tractor card already has a live YouTube embed — leave it unchanged.

- [ ] **Step 1: Replace comment in R&D Engineer (PT. Summit Vision Nusantara) card**

Find the `═══ HOW TO ADD MEDIA TO THIS CARD ═══` comment block in the R&D Engineer card and replace with:
```html
          <!-- VIDEO: Paste your YouTube or Google Drive embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 2: Replace comment in Motion Engineer (Summit Features Sdn Bhd) card**

Find the `═══ HOW TO ADD MEDIA TO THIS CARD ═══` comment block in the Motion Engineer card and replace with:
```html
          <!-- VIDEO: Paste your YouTube or Google Drive embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 3: Replace comment in Logistic Robot Fleet card**

Find the `═══ HOW TO ADD MEDIA TO THIS PROJECT ════════════════════════════` comment block in the Logistic Robot Fleet card and replace with:
```html
          <!-- VIDEO: Paste your YouTube or Google Drive embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 4: Replace comment in IoT Homecare Monitor card**

Find the `═══ HOW TO ADD MEDIA TO THIS PROJECT ════════════════════════════` comment block in the IoT Homecare Monitor card and replace with:
```html
          <!-- VIDEO: Paste your YouTube or Google Drive embed below when ready -->
          <!-- YouTube:      <div class="media-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe></div> -->
          <!-- Google Drive: <div class="media-video"><iframe src="https://drive.google.com/file/d/FILE_ID/preview" allowfullscreen></iframe></div> -->
```

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "chore: simplify media placeholder comments"
```
