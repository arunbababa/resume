# CLAUDE.md - AI Assistant Guide for Resume Repository

## Repository Overview

This repository contains a personal resume website for Tanaka Alfredo Hatsuki, written primarily in Japanese. It's a single-page, responsive web application built with Bootstrap that showcases professional experience, education, skills, and interests.

**Repository Type:** Static Website (Personal Resume/Portfolio)
**Primary Language:** Japanese (ja)
**Tech Stack:** HTML5, CSS3, JavaScript (ES6+), Bootstrap 5.2.3

---

## Project Structure

```
/home/user/resume/
├── index.html              # Main HTML file - entire resume content
├── css/
│   └── styles.css         # Custom styles (Bootstrap-based, ~104k tokens)
├── js/
│   └── scripts.js         # Navigation and UI interactions
├── assets/
│   └── img/
│       ├── profile.jpg    # Profile photo
│       ├── favicon.ico    # Site favicon
│       ├── jest.png       # Technology logo
│       ├── playwright.webp # Technology logo
│       └── pytest.png     # Technology logo
└── .git/                  # Git repository metadata
```

### File Descriptions

#### `index.html` (224 lines)
- **Purpose:** Single-page resume with all content
- **Sections:**
  - Navigation sidebar with profile image
  - About (概要) - Name, location, email, social links
  - Experience (経験) - Work history with 4 positions
  - Education (学歴) - Educational background
  - Skills (スキル) - Programming languages, tools, and strengths
  - Interests (趣味) - Hobbies and personal interests
  - Awards (受賞) - Currently commented out (lines 172-217)
- **Dependencies:**
  - Bootstrap 5.2.3 (via CDN)
  - Font Awesome 6.3.0 (via CDN)
  - Google Fonts: Saira Extra Condensed, Muli
- **Key Elements:**
  - Responsive navbar with scroll spy
  - Bootstrap grid system
  - Font Awesome icons for skills and social media

#### `js/scripts.js` (35 lines)
- **Purpose:** UI interactions and navigation behavior
- **Functionality:**
  1. Bootstrap ScrollSpy activation for sidebar navigation
  2. Responsive navbar collapse on menu item click
- **Framework:** Vanilla JavaScript with Bootstrap 5 API
- **License:** MIT (Start Bootstrap - Resume v7.0.6)

#### `css/styles.css` (Very large file - ~104k tokens)
- **Purpose:** Custom styling based on Start Bootstrap Resume theme
- **Note:** File is too large to read in one pass; use offset/limit when editing
- **Framework:** Bootstrap-based with custom overrides

---

## Content Guidelines

### Language Conventions
- **Primary Language:** Japanese (ja)
- **Navigation Labels:** Use Japanese terms:
  - 概要 (About)
  - 経験 (Experience)
  - 学歴 (Education)
  - スキル (Skills)
  - 趣味 (Interests)
  - 受賞 (Awards - when enabled)

### Person Information
- **Name:** Tanaka Alfredo Hatsuki (田中アルフレド初希)
- **Display Name Variants:**
  - Mobile nav: "Tanaka Alfredo Hatsuki"
  - Main heading: "Tanaka" with highlighted "Alfuredo Hatsuki"
- **Contact:** hatuki.1.gzs@gmail.com
- **Location:** 千葉県在住 (Chiba Prefecture)

### Content Sections

#### Experience Section (経験)
Current entries in reverse chronological order:
1. QA Engineer Intern - Works Applications (2023/09-2024/02, paused, 2024/08-present)
   - E2E test automation with Python, Playwright, pytest
   - Focus on test maintainability and Page Object Model (POM)
2. SAP Consultant Training - Wonder Camel (2024/04-2024/05)
3. Cram School Instructor - Takeda Juku (2022/08-2024/02)
4. Administrative Intern - Funai Consulting (2023/05-2023/12)

#### Education Section (学歴)
1. Open University of Japan - Currently enrolled
2. Tokyo City University - Engineering (withdrawn)

#### Skills Section (スキル)
- **Technologies:** Git, HTML5, CSS3, JavaScript, React, PHP, Python
- **Testing Tools:** Playwright, Jest, pytest (with logo images)
- **Strengths:**
  - Test automation and maintainability
  - E2E testing with Playwright & pytest
  - Unit testing with Jest
  - CI/CD experience with GitLab & GitHub

---

## Development Workflows

### Git Workflow

#### Branching Strategy
- **Main Branch:** Not explicitly set, but standard practice suggests `main` or `master`
- **Feature Branches:** Use pattern `claude/[feature-name]-[session-id]`
  - Example: `claude/add-claude-documentation-SGhDM`
  - **CRITICAL:** Branch names MUST start with `claude/` and end with matching session ID
  - Failure to follow this pattern will result in 403 errors on push

#### Git Commands
```bash
# Always use -u flag for first push to new branch
git push -u origin <branch-name>

# Fetch specific branches
git fetch origin <branch-name>

# Pull from specific branch
git pull origin <branch-name>
```

#### Retry Logic for Network Operations
- **Push/Pull/Fetch:** Retry up to 4 times on network failures
- **Backoff Strategy:** Exponential (2s, 4s, 8s, 16s)

#### Recent Commit History
```
1bc788b Update index.html
c882595 Merge pull request #1 from arunbababa/replace
e366ae8 名前や写真、文章の差し替え (Name, photo, text replacement)
83e1b4f first commit
```

### Making Changes

#### HTML Modifications (index.html)
1. **Read First:** Always read `index.html` before editing
2. **Preserve Structure:**
   - Keep Bootstrap classes intact
   - Maintain responsive grid layout (`d-flex`, `flex-column`, `flex-md-row`)
   - Preserve Font Awesome icon syntax
3. **Section Updates:**
   - Each section has class `resume-section` with unique ID
   - Use `<hr class="m-0" />` between sections
   - Keep date ranges in `<span class="text-primary">` tags
4. **Commented Code:**
   - Awards section (lines 172-217) is intentionally commented
   - Comment notes preservation of future features

#### JavaScript Modifications (scripts.js)
1. **Minimal Changes:** This file is stable and rarely needs updates
2. **Bootstrap Dependencies:** Changes may break ScrollSpy or navbar behavior
3. **Event Listeners:** All code runs after DOMContentLoaded

#### CSS Modifications (styles.css)
1. **Large File Warning:** Use `offset` and `limit` parameters with Read tool
2. **Bootstrap Override:** Custom styles override Bootstrap defaults
3. **Responsive Design:** Maintains mobile-first approach

#### Asset Updates
1. **Profile Image:** Replace `assets/img/profile.jpg` (used in sidebar)
2. **Technology Logos:** PNG/WebP format in `assets/img/`
   - `jest.png` (width: 130px, height: 60px)
   - `playwright.webp` (width: 130px, height: 90px)
   - `pytest.png` (width: 130px, height: 70px)
3. **Favicon:** `assets/img/favicon.ico`

---

## Common Tasks for AI Assistants

### Adding New Experience Entry
1. Read `index.html` to understand current structure
2. Locate the Experience section (`<section class="resume-section" id="experience">`)
3. Add new entry at the top (reverse chronological order)
4. Follow this structure:
```html
<div class="d-flex flex-column flex-md-row justify-content-between mb-5">
    <div class="flex-grow-1">
        <h3 class="mb-0">[Job Title in Japanese]</h3>
        <div class="subheading mb-3">[Company Name]</div>
        <p>[Description in Japanese]</p>
    </div>
    <div class="flex-shrink-0"><span class="text-primary">[Date Range]</span></div>
</div>
```

### Adding New Skills
1. **Technology Icons:** Add Font Awesome icon in skills list
   - Format: `<li class="list-inline-item"><i class="fab fa-[tech-name]"></i></li>`
2. **Custom Logos:** Add image tag with consistent sizing
   - Format: `<li class="list-inline-item"><img src="assets/img/[logo].png" alt="[description]" width="130" height="[appropriate]"></li>`
3. **Strengths:** Add list item under 強み (Strengths)
   - Format: `<li><span class="fa-li"><i class="fas fa-check"></i></span>[Skill description in Japanese]</li>`

### Enabling Awards Section
1. Uncomment lines 172-217 in `index.html`
2. Update award entries with actual achievements
3. Keep the trophy icon structure: `<span class="fa-li"><i class="fas fa-trophy text-warning"></i></span>`
4. Add corresponding navigation link in navbar if desired

### Updating Contact Information
1. **Email:** Line 47 in `index.html`
2. **Location:** Line 46 in `index.html`
3. **Social Links:** Lines 51-54 (currently placeholder `#!`)
   - Replace `href="#!"` with actual profile URLs

### Translation Considerations
- All visible text should be in Japanese
- Comments can be in Japanese or English
- Maintain professional tone appropriate for a resume
- Technical terms (e.g., "React", "Python") remain in English

---

## Testing and Validation

### Browser Testing
- **Primary Framework:** Bootstrap 5.2.3 (tested across modern browsers)
- **Responsive Breakpoints:** Bootstrap's default (sm, md, lg, xl, xxl)
- **Test Points:**
  1. Mobile navbar toggle functionality
  2. Scroll spy navigation highlighting
  3. Profile image circular crop
  4. Social icon hover states

### File Validation
1. **HTML:** W3C HTML5 validation
2. **Accessibility:** Ensure `alt` tags on images
3. **Links:** Verify all `href` attributes (many are placeholders `#!`)

---

## Dependencies and External Resources

### CDN Resources
1. **Bootstrap 5.2.3**
   - Bundle JS: `https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js`
   - CSS: Bundled in `css/styles.css`

2. **Font Awesome 6.3.0**
   - JS: `https://use.fontawesome.com/releases/v6.3.0/js/all.js`
   - Used for: Social icons, skill icons, list decorations

3. **Google Fonts**
   - Saira Extra Condensed (weights: 500, 700)
   - Muli (weights: 400, 400i, 800, 800i)

### Licenses
- **Template:** Start Bootstrap - Resume v7.0.6
- **License:** MIT
- **Copyright:** 2013-2023 Start Bootstrap
- **Source:** https://startbootstrap.com/theme/resume

---

## Best Practices for AI Assistants

### Before Making Changes
1. **Always read the file first** - Never propose changes to unread code
2. **Understand context** - Review surrounding sections to maintain consistency
3. **Preserve formatting** - Keep indentation and spacing consistent
4. **Check dependencies** - Ensure Bootstrap classes and Font Awesome icons are valid

### Code Modifications
1. **Minimal changes** - Only modify what's requested
2. **No over-engineering** - Don't add unrequested features
3. **Preserve structure** - Maintain Bootstrap grid and component patterns
4. **Test compatibility** - Ensure changes work with Bootstrap 5.2.3

### Japanese Content
1. **Maintain language** - All user-facing text in Japanese
2. **Professional tone** - Formal resume language
3. **Technical accuracy** - Verify technical terms are correctly represented
4. **Date formats** - Follow existing pattern: `YYYY/MM - YYYY/MM`

### Git Operations
1. **Branch naming** - Follow `claude/[name]-[session-id]` pattern
2. **Commit messages** - Clear, descriptive, can be in English or Japanese
3. **Push strategy** - Use `-u` flag for new branches
4. **Network resilience** - Implement retry logic with exponential backoff

### File Operations
1. **Large files** - Use offset/limit for `styles.css` (104k+ tokens)
2. **Image updates** - Maintain consistent dimensions for logos
3. **Asset paths** - Always use relative paths from repository root
4. **Backup awareness** - Understand that edits are immediate and permanent

---

## Security and Privacy Considerations

### Personal Information
- Email address is public in the repository
- Social media links are currently placeholders
- Profile photo is version-controlled
- No sensitive credentials or private data detected

### External Resources
- All CDN resources use HTTPS
- Font Awesome uses `crossorigin="anonymous"`
- No tracking scripts or analytics detected
- No form submissions or data collection

---

## Future Enhancements (Commented/Planned)

### Awards Section
- **Status:** Commented out (lines 172-217)
- **Purpose:** Showcase certifications, awards, achievements
- **Note:** "受賞欄は現状書くことないが、今後使う可能性はあるのでコメントアウト"
  - Translation: "There's nothing to write in the awards section currently, but there's a possibility of using it in the future, so it's commented out"

### Potential Improvements (Not Implemented)
- Multi-language support (Japanese/English toggle)
- Dark mode theme
- Print-friendly CSS
- PDF export functionality
- Dynamic content loading
- Blog or portfolio project section

---

## Troubleshooting Common Issues

### Navigation Not Working
- **Cause:** ScrollSpy not initializing or navbar IDs mismatch
- **Fix:** Verify `#sideNav` exists and section IDs match nav links

### Responsive Layout Broken
- **Cause:** Bootstrap classes removed or modified
- **Fix:** Restore original Bootstrap utility classes (`d-flex`, `flex-column`, etc.)

### Images Not Loading
- **Cause:** Incorrect relative paths or missing files
- **Fix:** Ensure paths start with `assets/img/` and files exist

### Japanese Text Not Displaying
- **Cause:** Character encoding issue
- **Fix:** Verify `<meta charset="utf-8" />` is present in `<head>`

### Push Fails with 403
- **Cause:** Branch name doesn't follow required pattern
- **Fix:** Rename branch to start with `claude/` and end with session ID

---

## Contact and Ownership

**Repository Owner:** arunbababa (GitHub username)
**Subject:** Tanaka Alfredo Hatsuki
**Email:** hatuki.1.gzs@gmail.com
**Purpose:** Personal resume website

---

## Quick Reference Commands

```bash
# View project structure
ls -la

# Start local server (if needed)
python -m http.server 8000
# Or
npx serve

# Check git status
git status

# Create and switch to new feature branch
git checkout -b claude/[feature-name]-[session-id]

# Stage all changes
git add .

# Commit with descriptive message
git commit -m "Description of changes"

# Push to remote (first time)
git push -u origin claude/[feature-name]-[session-id]

# View recent commits
git log --oneline -10

# View file at specific line range
head -n 50 index.html
tail -n 20 index.html
```

---

## Version Information

- **Last Updated:** 2026-01-08
- **Current Branch:** `claude/add-claude-documentation-SGhDM`
- **Git Status:** Clean working directory
- **Bootstrap Version:** 5.2.3
- **Font Awesome Version:** 6.3.0
- **Template Version:** Start Bootstrap Resume v7.0.6

---

## Summary for AI Assistants

This is a **personal resume website** built with **Bootstrap 5** and **vanilla JavaScript**. The site is **single-page**, **responsive**, and written in **Japanese**. When assisting with this repository:

1. **Always read before editing** - Especially `index.html` and `js/scripts.js`
2. **Use offset/limit for CSS** - The `styles.css` file is very large
3. **Maintain Japanese language** - All content is in Japanese
4. **Preserve Bootstrap structure** - Don't break responsive classes
5. **Follow git branch naming** - Must start with `claude/` and end with session ID
6. **Keep changes minimal** - Only modify what's requested
7. **Test responsively** - Changes should work on mobile and desktop
8. **Respect commented code** - Awards section is intentionally disabled

The codebase is **simple, stable, and well-structured**. Most changes will involve updating content in `index.html` rather than modifying functionality.
