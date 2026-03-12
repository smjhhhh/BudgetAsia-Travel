# BudgetAsia Travel - Complete Operation Guide

**Version:** 1.0
**Last Updated:** February 2026
**Audience:** Developers, Content Managers, Instructors

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Getting Started](#getting-started)
3. [File Structure & Navigation](#file-structure--navigation)
4. [Development Environment Setup](#development-environment-setup)
5. [Working with the Codebase](#working-with-the-codebase)
6. [Content Management](#content-management)
7. [Git Workflow](#git-workflow)
8. [Testing & Debugging](#testing--debugging)
9. [Deployment](#deployment)
10. [Troubleshooting](#troubleshooting)
11. [Best Practices](#best-practices)

---

## Project Overview

### What is BudgetAsia Travel?

BudgetAsia Travel is a responsive web application showcasing affordable travel experiences across four Asian cities:
- **Bangkok** - Markets, temples, and street food
- **Tokyo** - Tradition meets modern technology
- **Seoul** - K-culture and vibrant neighborhoods
- **Hong Kong** - Cinematic city with music heritage

### Core Features

- **8 HTML Pages** - Landing page, 4 destination guides, booking form, packages, reviews
- **3-Day Itineraries** - Detailed daily schedules with landmarks and food recommendations
- **Interactive Booking Form** - Capture travel requests with dynamic receipt generation
- **Responsive Design** - Works on mobile, tablet, and desktop devices
- **Hong Kong Special Feature** - Album wall with BGM player celebrating cinema culture
- **Professional Git Workflow** - Version control with feature branches and PR reviews

### Technology Stack

| Technology | Purpose | Version |
|-----------|---------|---------|
| HTML5 | Semantic markup | Latest |
| Tailwind CSS | Responsive design | v3 (CDN) |
| JavaScript | Interactivity | ES6+ |
| Git | Version control | 2.x+ |
| Unsplash API | Images | Free |

---

## Getting Started

### Prerequisites

**Required:**
- Code editor (VS Code, Sublime Text, etc.)
- Web browser (Chrome, Firefox, Safari, Edge)
- Git installed
- GitHub account (for version control)

**Optional:**
- Node.js/npm (for local development servers)
- Web server (Python `http.server` or `npx http-server`)

### Quick Start (5 minutes)

**Step 1: Clone the Repository**
```bash
git clone https://github.com/[username]/BudgetAsia-Travel.git
cd BudgetAsia-Travel
```

**Step 2: Open in Browser**

**Option A: Direct File Opening**
```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

**Option B: Local Server (Recommended)**
```bash
# Using Python 3
python -m http.server 8000

# Or using Node.js
npx http-server

# Then visit http://localhost:8000
```

**Step 3: Navigate the Site**
1. Start at `index.html`
2. Click "Explore Destinations" → `packages.html`
3. Click a city in dropdown → destination page
4. Click "Book Your Trip" → `booking.html`

---

## File Structure & Navigation

### Directory Layout

```
BudgetAsia-Travel/
│
├── HTML Pages (8 files)
│   ├── index.html              [LANDING PAGE]
│   ├── bangkok.html            [DESTINATION GUIDE]
│   ├── tokyo.html              [DESTINATION GUIDE]
│   ├── seoul.html              [DESTINATION GUIDE]
│   ├── hongkong.html           [DESTINATION GUIDE + SPECIAL FEATURE]
│   ├── booking.html            [BOOKING FORM]
│   ├── packages.html           [PACKAGE SHOWCASE]
│   └── reviews.html            [CUSTOMER TESTIMONIALS]
│
├── assets/                     [LOCAL IMAGE FILES]
│   ├── andylau.jpg            [Hong Kong album covers]
│   ├── leslie.jpg
│   ├── tonyleung.jpg
│   ├── chowyunfat.jpg
│   ├── aaronkwok.jpg
│   ├── jackycheung.jpg
│   ├── leonlai.jpg
│   ├── danielwu.jpg
│   ├── stephenchow.jpg
│   ├── nicholastse.jpg
│   └── langzixin.mp3           [BGM audio file]
│
├── Documentation
│   ├── TECHNICAL_REPORT.md     [THIS DOCUMENT]
│   ├── OPERATION_GUIDE.md      [PROJECT OVERVIEW]
│   └── README.md               [GitHub repository file]
│
└── Version Control
    └── .git/                   [Git repository]
```

### Page Hierarchy

```
index.html (Landing)
├── Header Navigation (Global)
│   ├── Logo/Home
│   ├── Destinations Dropdown
│   │   ├── bangkok.html
│   │   ├── tokyo.html
│   │   ├── seoul.html
│   │   └── hongkong.html
│   ├── Packages → packages.html
│   ├── Reviews → reviews.html
│   └── Book Now → booking.html
│
└── Hero Section
    ├── CTA Buttons
    │   ├── "Explore Destinations" → packages.html
    │   └── "Book Your Trip" → booking.html
    │
    └── Featured Destinations Grid
        ├── Bangkok Card → bangkok.html
        ├── Tokyo Card → tokyo.html
        ├── Seoul Card → seoul.html
        └── [Hong Kong mentioned but can be accessed via dropdown]
```

---

## Development Environment Setup

### Setting Up VS Code

**Step 1: Install Extensions**
```
- ES7+ React/Redux/React-Native snippets
- HTML CSS Support
- Live Server (optional)
- Prettier Code Formatter
```

**Step 2: Configure Workspace**

Create `.vscode/settings.json`:
```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "html.validate.styles": true,
  "html.validate.scripts": true
}
```

**Step 3: Use Live Server**
1. Right-click `index.html`
2. Select "Open with Live Server"
3. Browser opens at `http://127.0.0.1:5500`

### Setting Up Git

**Initial Configuration**
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify
git config --global user.name
git config --global user.email
```

**SSH Setup (Recommended)**
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Add to SSH agent
ssh-add ~/.ssh/id_ed25519

# Copy public key and add to GitHub Settings
cat ~/.ssh/id_ed25519.pub
```

---

## Working with the Codebase

### Understanding Page Structure

Every destination page follows the same pattern:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Meta tags -->
  <!-- Tailwind CDN -->
</head>
<body>
  <!-- Background -->
  <!-- Navigation Header (Global) -->
  <header>
    <nav><!-- Common to all pages --></nav>
  </header>

  <!-- Main Content -->
  <main>
    <!-- 1. Hero Section -->
    <section class="...hero..."></section>

    <!-- 2. About Section -->
    <section class="container">
      <h2>Why [City]?</h2>
      <p>Description...</p>
    </section>

    <!-- 3. Attractions Grid -->
    <section class="container">
      <h2>Top Attractions</h2>
      <div class="grid grid-cols-3 gap-8">
        <article>...</article> × 3
      </div>
    </section>

    <!-- 4. Food Section -->
    <section class="container">
      <h2>Must-Try Cuisine</h2>
      <div class="grid grid-cols-4 gap-6">
        <article>...</article> × 4
      </div>
    </section>

    <!-- 5. 3-Day Itinerary -->
    <section class="container bg-[color]-50/30">
      <h2>3-Day [City] Itinerary</h2>
      <article><!-- Day 1 --></article>
      <article><!-- Day 2 --></article>
      <article><!-- Day 3 --></article>
      <div><!-- Budget Summary --></div>
    </section>

    <!-- 6. Travel Tips -->
    <section class="bg-[color]-50/50">
      <h2>Travel Tips</h2>
      <div class="grid grid-cols-2 gap-8">
        <div><!-- Tip 1 --></div>
        <div><!-- Tip 2 --></div>
        <div><!-- Tip 3 --></div>
        <div><!-- Tip 4 --></div>
      </div>
    </section>
  </main>

  <!-- Footer (Global) -->
  <footer>
    <!-- About, Links, Student Info, Copyright -->
  </footer>
</body>
</html>
```

### Editing Content

#### Adding a New Attraction

**Location:** `bangkok.html:122-176` (same pattern for all cities)

**Procedure:**

1. **Find the Attractions Grid**
```html
<section class="container mx-auto px-8 py-24">
  <h2 class="text-3xl font-light text-zinc-900 mb-16">Top Attractions</h2>
  <div class="grid grid-cols-3 gap-8">
    <!-- Attractions go here -->
  </div>
</section>
```

2. **Add a New Article**
```html
<!-- New Attraction -->
<article class="group">
  <div class="bg-amber-100 h-64 mb-4 overflow-hidden">
    <img src="https://images.unsplash.com/photo-[NEW_ID]?w=600&h=400&fit=crop"
         alt="Attraction Name"
         class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
  </div>
  <h3 class="text-xl font-light text-zinc-900 mb-2">Attraction Name</h3>
  <p class="text-sm text-zinc-600 leading-relaxed">
    Description of the attraction goes here.
  </p>
</article>
```

3. **Find an Image on Unsplash**
   - Visit unsplash.com
   - Search for "attraction name"
   - Copy the photo ID from URL: `unsplash.com/photos/[PHOTO_ID]`
   - Replace `[NEW_ID]` with the photo ID

4. **Save and Test**
   - File → Save
   - Reload browser (Cmd+R / Ctrl+R)

#### Adding a Food Item

**Location:** Bangkok food section (Lines 179-243)

**Steps:**
1. Copy an existing food card
2. Update `src="..."` with new Unsplash image
3. Update `alt="..."` with food name
4. Change `<h3>` to new food name
5. Update description in `<p>`
6. Save and test

**Note:** Food grid is 4 columns (not 3 like attractions)
```html
<div class="grid grid-cols-4 gap-6">
  <!-- 4 food items -->
</div>
```

#### Updating Itinerary Content

**Location:** All destination pages (Lines ~246-430)

**Day Structure:**
```html
<article class="bg-white border border-[color]-200 p-8 mb-8">
  <!-- Header with day number -->
  <div class="flex items-center gap-3 mb-6 pb-4 border-b">
    <div class="bg-[color]-700 text-white w-12 h-12 rounded-full flex items-center justify-center">
      1
    </div>
    <div>
      <h3 class="text-2xl font-light text-zinc-900">Day 1: [Title]</h3>
      <p class="text-sm text-zinc-500">[Subtitle]</p>
    </div>
  </div>

  <!-- Landmarks (Green) -->
  <div class="mb-6">
    <h4 class="text-sm font-medium text-emerald-700 uppercase tracking-wider mb-4 flex items-center gap-2">
      <svg class="w-5 h-5"><!-- Icon --></svg>
      Landmarks
    </h4>
    <ul class="space-y-3 ml-7">
      <li class="flex items-start gap-3">
        <span class="text-emerald-700 font-medium text-sm">Morning:</span>
        <div>
          <p class="text-zinc-900 font-medium">[Activity Name]</p>
          <p class="text-sm text-zinc-600">[Description]</p>
        </div>
      </li>
      <!-- Afternoon and Evening -->
    </ul>
  </div>

  <!-- Food (Orange) -->
  <div>
    <h4 class="text-sm font-medium text-orange-700 uppercase tracking-wider mb-4">Food</h4>
    <ul class="space-y-2 ml-7">
      <li class="flex items-start gap-3">
        <span class="text-orange-700 font-medium text-sm">Breakfast:</span>
        <p class="text-zinc-700">[Food name] (~$X)</p>
      </li>
      <!-- Lunch and Dinner -->
    </ul>
  </div>
</article>
```

**Key Fields to Update:**
- Day number (circle badge): `<div class="bg-[color]-700">1</div>`
- Day title: `<h3>Day 1: [TITLE]</h3>`
- Day subtitle: `<p class="text-sm text-zinc-500">[SUBTITLE]</p>`
- Morning/Afternoon/Evening activities
- Breakfast/Lunch/Dinner items with prices

#### Updating Budget Summary

**Location:** End of itinerary section

**Current Format:**
```html
<div class="bg-emerald-50 border-l-4 border-emerald-700 p-6 mt-8">
  <h4>3-Day Budget Estimate</h4>
  <div class="grid grid-cols-2 md:grid-cols-4 gap-4 text-sm">
    <div>
      <p class="text-emerald-700 font-medium">Accommodation</p>
      <p class="text-emerald-900">~$X/night</p>
    </div>
    <div>
      <p class="text-emerald-700 font-medium">Food</p>
      <p class="text-emerald-900">~$Y/day</p>
    </div>
    <div>
      <p class="text-emerald-700 font-medium">Transportation</p>
      <p class="text-emerald-900">~$Z/day</p>
    </div>
    <div>
      <p class="text-emerald-700 font-medium">Attractions</p>
      <p class="text-emerald-900">~$W total</p>
    </div>
  </div>
  <p class="text-xs text-emerald-800 mt-4">
    <strong>Total 3-Day Budget:</strong> Approximately $[AMOUNT] USD per person
  </p>
  <p class="text-xs text-emerald-700 mt-2 italic">💡 Tip: ...</p>
</div>
```

---

## Content Management

### Managing Images

#### Image Sources

**External (Unsplash):**
- Free high-quality photography
- No attribution required
- URL format: `https://images.unsplash.com/photo-[ID]?w=600&h=400&fit=crop`

**Local (/assets/):**
- Hong Kong album covers (for album wall feature)
- Audio files (BGM)
- Should be committed to Git

#### Adding Images from Unsplash

**Step 1: Search for Image**
1. Visit unsplash.com
2. Search for destination/food name
3. Click image to open detail page

**Step 2: Extract Photo ID**
- URL format: `unsplash.com/photos/[PHOTO_ID]-[user-name]`
- Example: `unsplash.com/photos/mAQZ4L-KX3w-grand-palace` → ID is `mAQZ4L-KX3w`

**Step 3: Create Unsplash URL**
```
https://images.unsplash.com/photo-[PHOTO_ID]?w=600&h=400&fit=crop
```

**Step 4: Use in HTML**
```html
<img src="https://images.unsplash.com/photo-[ID]?w=600&h=400&fit=crop"
     alt="Descriptive alt text"
     class="w-full h-full object-cover">
```

#### Image Size Guidelines

| Context | Width | Height | Use |
|---------|-------|--------|-----|
| Full-page background | 1920 | 1080 | Hero sections |
| Attraction cards | 600 | 400 | Top Attractions grid |
| Food cards | 400 | 300 | Food section grid |
| Album wall | 300 | 300 | Hong Kong album grid |

#### Handling Missing Images

If an image fails to load:
1. Check URL is correct
2. Verify internet connection
3. Try different Unsplash photo ID
4. Check file exists in `/assets/` for local images

### Managing Text Content

#### Color Coding per City

Each city has a distinct color scheme:

| City | Primary | Secondary | Uses |
|------|---------|-----------|------|
| Bangkok | `amber-700` / `amber` | `orange` | Itinerary accents, food icons |
| Tokyo | `pink-600` / `pink` | `rose` | Modern, vibrant theme |
| Seoul | `blue-700` / `blue` | `indigo` | Cool, trendy aesthetic |
| Hong Kong | `purple-700` / `purple` | `pink` | Cinematic, sophisticated |

**Color Implementation:**
```html
<!-- Bangkok day card -->
<div class="bg-amber-700">Day 1</div>

<!-- Tokyo section -->
<div class="bg-pink-50/30">3-Day Itinerary</div>

<!-- Seoul button -->
<button class="bg-blue-700 hover:bg-blue-800">Book</button>

<!-- Hong Kong accent -->
<h2 class="text-purple-900">Hong Kong</h2>
```

#### Updating Booking Form

**File:** `booking.html:98-171`

**Current Fields:**
```html
<!-- Name Input -->
<input type="text" id="user-name" required placeholder="John Doe">

<!-- Travelers Select -->
<select id="travelers" required>
  <option value="">Select...</option>
  <option value="1">1 Person</option>
  <option value="2">2 People</option>
  <option value="3">3 People</option>
  <option value="4">4 People</option>
  <option value="5+">5+ People</option>
</select>

<!-- Departure Date -->
<input type="date" id="departure-date" required>

<!-- Package Type -->
<select id="package-select" required>
  <option value="">Select package...</option>
  <option value="Budget Explorer ($599)">Budget Explorer ($599)</option>
  <option value="Cultural Immersion ($899)">Cultural Immersion ($899)</option>
  <option value="Luxury Comfort ($1,499)">Luxury Comfort ($1,499)</option>
</select>
```

**To Add a New Field:**
1. Copy an existing `<div>` with form field
2. Update `<label for="...">`
3. Update `<input>` or `<select>` attributes
4. Update form handler in JavaScript (lines 249-274)

#### Updating Packages Page

**File:** `packages.html`

**Package Card Template:**
```html
<article class="border border-gray-200 p-6 text-center">
  <h3 class="text-2xl font-light text-zinc-900 mb-2">[Package Name]</h3>
  <p class="text-3xl font-bold text-emerald-700 mb-6">$[PRICE]</p>
  <ul class="space-y-2 mb-6 text-left">
    <li class="text-sm text-zinc-700">✓ [Feature 1]</li>
    <li class="text-sm text-zinc-700">✓ [Feature 2]</li>
    <li class="text-sm text-zinc-700">✓ [Feature 3]</li>
    <!-- Add more features as needed -->
  </ul>
  <button class="bg-emerald-700 text-white px-6 py-2 text-sm font-medium hover:bg-emerald-800">
    Select Package
  </button>
</article>
```

---

## Git Workflow

### Daily Development Workflow

**Step 1: Check Status**
```bash
git status
```

**Output indicates:**
- Untracked files (new files)
- Modified files (changed files)
- Staged files (ready to commit)

**Step 2: Make Changes**
Edit files in your editor. Save frequently.

**Step 3: Stage Changes**
```bash
# Stage specific file
git add path/to/file.html

# Stage all changes
git add .

# Review staged changes
git diff --staged
```

**Step 4: Commit Changes**
```bash
# Commit with message
git commit -m "Brief description of changes"

# Example commits:
git commit -m "feat: add Bangkok attractions section"
git commit -m "style: update Tokyo itinerary colors"
git commit -m "fix: resolve broken navigation link"
```

**Step 5: Push to GitHub**
```bash
git push origin main
```

**Step 6: Create Pull Request (Optional)**
```bash
gh pr create --title "Feature title" --body "Description..."
```

### Commit Message Guidelines

**Format:**
```
<type>: <subject>

<optional body>
```

**Type Keywords:**
- `feat:` - New feature
- `fix:` - Bug fix
- `style:` - CSS/image updates
- `refactor:` - Code reorganization
- `docs:` - Documentation updates
- `chore:` - Build/maintenance tasks

**Examples:**
```bash
git commit -m "feat: add 3-day Seoul itinerary"
git commit -m "style: replace gradient backgrounds with real images"
git commit -m "fix: correct broken Bangkok page link"
git commit -m "refactor: simplify booking form validation"
git commit -m "docs: update README with deployment instructions"
```

### Creating Feature Branches

**Procedure:**

```bash
# Create and switch to feature branch
git checkout -b feature/description

# Example names:
git checkout -b feature/add-hongkong-page
git checkout -b feature/improve-responsive-design
git checkout -b feature/booking-form-validation

# Make changes...
git add .
git commit -m "feat: ..."

# Push feature branch
git push origin feature/description

# Create Pull Request
gh pr create --title "Feature title" --body "Description"

# Merge after review
gh pr merge [PR_NUMBER]

# Switch back to main
git checkout main

# Pull latest changes
git pull origin main

# Delete feature branch locally
git branch -d feature/description
```

### Viewing History

```bash
# View recent commits
git log --oneline -10

# View changes in specific file
git log --oneline -- path/to/file.html

# View detailed changes
git show [COMMIT_HASH]

# Compare branches
git diff main feature/branch-name
```

---

## Testing & Debugging

### Browser Testing Checklist

#### Desktop Testing (Chrome/Firefox)
- [ ] All links work correctly
- [ ] Navigation dropdown opens on hover
- [ ] Forms submit without errors
- [ ] Images load correctly
- [ ] Colors render properly
- [ ] No console errors (F12 → Console)

#### Tablet Testing (iPad 768px)
- [ ] Navigation is readable
- [ ] Grid layouts responsive
- [ ] Text is not truncated
- [ ] Buttons are clickable (not too small)
- [ ] Images scale appropriately

#### Mobile Testing (iPhone 375px)
- [ ] Full-width layout works
- [ ] Navigation is accessible (menu)
- [ ] Grid is single column
- [ ] Font sizes are readable
- [ ] Buttons are touch-friendly

### Using Browser DevTools

**Opening DevTools:**
```
Windows/Linux: F12 or Ctrl+Shift+I
macOS: Cmd+Option+I
```

**Key Panels:**
1. **Elements** - Inspect HTML structure
2. **Console** - View errors and warnings
3. **Network** - Check image/resource loading
4. **Device Toolbar** - Test responsive design

**Testing Responsive Design:**
1. Open DevTools (F12)
2. Click Device Toolbar icon (mobile icon in top-left)
3. Select device (iPhone, iPad, etc.)
4. Resize and test layout

**Finding HTML Issues:**
1. Right-click element
2. Select "Inspect"
3. View HTML in Elements panel
4. Check for missing alt text, broken attributes

### Common Issues & Fixes

| Issue | Cause | Fix |
|-------|-------|-----|
| Images not loading | Wrong URL or file missing | Check Unsplash photo ID or `/assets/` path |
| Layout broken | CSS class typo | Check Tailwind class name (e.g., `grid-cols-3`) |
| Form not submitting | Missing `required` attribute | Verify HTML attribute syntax |
| Styling not applying | CDN not loaded | Check Tailwind CDN script in `<head>` |
| BGM not playing | Audio file missing | Add `langzixin.mp3` to `/assets/` folder |
| Navigation dropdown not working | CSS issue | Check `group` and `group-hover:` classes |

---

## Deployment

### Pre-Deployment Checklist

**Content Verification:**
- [ ] All 8 pages exist and link correctly
- [ ] Images load without errors
- [ ] Booking form works end-to-end
- [ ] No broken links (check navigation)
- [ ] All text is properly formatted
- [ ] Color schemes are consistent

**Technical Verification:**
- [ ] No console errors (F12 → Console)
- [ ] Responsive design works (test on mobile)
- [ ] Git history is clean and committed
- [ ] No sensitive data in code
- [ ] All assets are included (`/assets/` folder)

**Performance Check:**
- [ ] Images are optimized (use Unsplash query params)
- [ ] No duplicate code
- [ ] Tailwind is minified (CDN)
- [ ] No unused CSS files

### Hosting Options

#### Option 1: GitHub Pages (Free)

**Steps:**
1. Push to GitHub: `git push origin main`
2. Go to repository Settings
3. Scroll to "Pages" section
4. Select "main" branch as source
5. Wait 1-2 minutes for deployment

**Access:**
```
https://[username].github.io/BudgetAsia-Travel/
```

⚠️ **Note:** As per requirements, GitHub Pages was **NOT** enabled for this project.

#### Option 2: Netlify (Free)

**Steps:**
1. Visit netlify.com
2. Click "Deploy" → "Import existing project"
3. Connect GitHub account
4. Select `BudgetAsia-Travel` repository
5. Configure build (leave defaults)
6. Click "Deploy site"

**Access:**
```
https://[your-site].netlify.app/
```

#### Option 3: Vercel (Free)

**Steps:**
1. Visit vercel.com
2. Click "Import Project"
3. Connect GitHub account
4. Select `BudgetAsia-Travel`
5. Click "Import"
6. Click "Deploy"

**Access:**
```
https://[your-site].vercel.app/
```

### Local Testing Before Deployment

**Start Local Server:**
```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server

# Live Server (VS Code)
Right-click index.html → Open with Live Server
```

**Test in Browser:**
1. Visit http://localhost:8000
2. Click through all pages
3. Test form submission
4. Check mobile view (DevTools)
5. Verify all images load

---

## Troubleshooting

### Issue: Images Not Loading

**Symptoms:**
- Broken image placeholders
- Unsplash images showing blank

**Diagnosis:**
```
1. F12 → Network tab
2. Filter by "img"
3. Check status codes (200 = OK, 404 = Not Found)
4. Check console for error messages
```

**Solutions:**
```bash
# For Unsplash images
# Problem: Wrong photo ID
# Solution: Copy correct ID from unsplash.com/photos/[ID]

# For local images
# Problem: Wrong path (e.g., assets/image.jpg vs ./assets/image.jpg)
# Solution: Use relative path from HTML file location
```

### Issue: Form Not Submitting

**Symptoms:**
- Form submission doesn't show receipt
- Page reloads instead of showing confirmation

**Diagnosis:**
```html
<!-- Check JavaScript is included -->
<script>
  console.log("Form script loaded");
</script>

<!-- Check form element exists -->
<form id="trip-form">
```

**Solutions:**
1. Verify form has `id="trip-form"`
2. Check all inputs have correct `id` attributes:
   - `id="user-name"`
   - `id="travelers"`
   - `id="departure-date"`
   - `id="package-select"`
3. Check JavaScript (F12 → Console for errors)

### Issue: Styling Looks Wrong

**Symptoms:**
- Colors incorrect
- Layout broken
- Spacing off

**Diagnosis:**
```
1. F12 → Elements tab
2. Right-click element
3. Inspect and check CSS classes
4. Verify Tailwind classes are valid
```

**Solutions:**
```bash
# Check Tailwind CDN is loaded
# In <head>, verify:
<script src="https://cdn.tailwindcss.com"></script>

# Check class names are correct
# Common errors:
- grid-cols-3 (correct) vs grid-cols-three (wrong)
- bg-amber-100 (correct) vs bg-amber (wrong)
- hover:scale-105 (correct) vs hover:scale105 (wrong)
```

### Issue: Git Commands Not Working

**Symptoms:**
- Command not found errors
- Permission denied messages

**Solutions:**
```bash
# Verify Git is installed
git --version

# Check Git config
git config --list

# If user not set
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# If pushing fails, check SSH key
ssh-add -l
```

---

## Best Practices

### Code Style Guidelines

**HTML:**
```html
✅ GOOD - Semantic, readable
<section class="container mx-auto px-8 py-24">
  <article class="group">
    <img alt="Descriptive text">
  </article>
</section>

❌ BAD - Divitis, missing alt text
<div class="container">
  <div class="article">
    <img>
  </div>
</div>
```

**CSS (Tailwind):**
```html
✅ GOOD - Organized, readable
<div class="flex items-center gap-3 mb-6 pb-4 border-b border-gray-200">

❌ BAD - Unsorted, hard to read
<div class="mb-6 pb-4 gap-3 flex border-b border-gray-200 items-center">
```

**JavaScript:**
```javascript
✅ GOOD - Clear intent
myForm.addEventListener('submit', function(event) {
  event.preventDefault();
  const nameValue = document.getElementById('user-name').value;
});

❌ BAD - Unclear
form.onsubmit = function() {
  let n = document.getElementById('user-name').value;
};
```

### Git Commit Best Practices

✅ **DO:**
- Write descriptive commit messages
- Commit related changes together
- Use present tense ("add feature" not "added feature")
- Reference issues/PRs when relevant

❌ **DON'T:**
- Make huge monolithic commits
- Use vague messages ("fix stuff")
- Commit directly to main (use feature branches)
- Push sensitive data (API keys, passwords)

### Content Management Best Practices

✅ **DO:**
- Keep alt text descriptive and concise
- Use consistent formatting across pages
- Test changes before committing
- Update documentation when adding features

❌ **DON'T:**
- Leave placeholder text
- Use "image" or "photo" as alt text
- Mix color schemes inconsistently
- Skip testing on mobile

### Performance Best Practices

✅ **DO:**
- Use Unsplash URL parameters: `?w=600&h=400&fit=crop`
- Optimize alt text (good for SEO)
- Use semantic HTML (better SEO)
- Minimize CSS files (Tailwind minified)

❌ **DON'T:**
- Upload full-resolution images
- Use generic alt text
- Nest too many divs
- Add unnecessary JavaScript

---

## Quick Reference

### Useful Commands

```bash
# Git commands
git status                    # Check what changed
git add .                     # Stage all changes
git commit -m "message"       # Commit with message
git push origin main          # Push to GitHub
git pull origin main          # Pull latest changes
git log --oneline -10         # View recent commits

# Local server
python -m http.server 8000    # Start Python server
npx http-server              # Start Node.js server

# Browser DevTools
F12                          # Open DevTools
Cmd+Shift+I (macOS)          # DevTools alternate
Ctrl+Shift+I (Windows)       # DevTools alternate
```

### File Paths to Remember

```
/index.html                  # Landing page
/bangkok.html                # Bangkok guide
/tokyo.html                  # Tokyo guide
/seoul.html                  # Seoul guide
/hongkong.html               # Hong Kong guide (special)
/booking.html                # Booking form
/packages.html               # Package listings
/reviews.html                # Customer reviews
/assets/                     # Images and audio
```

### Key IDs & Classes

```html
<!-- Form IDs (booking.html) -->
id="trip-form"              <!-- Main form -->
id="user-name"              <!-- Name input -->
id="travelers"              <!-- Travelers dropdown -->
id="departure-date"         <!-- Date input -->
id="package-select"         <!-- Package dropdown -->
id="receipt-container"      <!-- Receipt display -->

<!-- Hong Kong BGM -->
id="bgm-toggle"            <!-- BGM button -->
id="hk-audio"              <!-- Audio element -->
id="record-icon"           <!-- Spinning vinyl icon -->
```

### Color Classes by City

```html
<!-- Bangkok: Amber -->
<div class="bg-amber-700">
<div class="text-amber-700">
<div class="border-amber-200">

<!-- Tokyo: Pink -->
<div class="bg-pink-600">
<div class="text-pink-300">

<!-- Seoul: Blue -->
<div class="bg-blue-700">
<div class="border-blue-200">

<!-- Hong Kong: Purple -->
<div class="bg-purple-700">
<div class="text-purple-700">
```

---

## Support & Resources

### Documentation
- **Tailwind CSS:** https://tailwindcss.com/docs
- **HTML5 Spec:** https://developer.mozilla.org/en-US/docs/Web/HTML
- **JavaScript Guide:** https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
- **Git Documentation:** https://git-scm.com/doc

### Learning Resources
- **Responsive Design:** https://web.dev/responsive-web-design-basics/
- **Semantic HTML:** https://www.w3.org/WAI/fundamentals/html5/
- **CSS Flexbox:** https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- **CSS Grid:** https://css-tricks.com/snippets/css/complete-guide-grid/

### Tools
- **VS Code:** https://code.visualstudio.com/
- **Unsplash API:** https://unsplash.com/developers
- **GitHub CLI:** https://cli.github.com/
- **Netlify:** https://www.netlify.com/

---

## Document Information

| Property | Value |
|----------|-------|
| **Document Type** | Operation Guide |
| **Version** | 1.0 |
| **Last Updated** | February 2026 |
| **Author** | Mingjie Shen |
| **Course** | Web Design (Milestone 3) |
| **Institution** | Northeastern University |
| **Status** | Complete ✅ |

---

## Document Revision History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Feb 2026 | Initial complete guide with all sections |

---

**Thank you for using BudgetAsia Travel! Happy developing! 🌏**
