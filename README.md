<div align="center">

<img src="assets/banner.jpg" alt="khanfarhana.info — web development case study" width="100%">

<br>

# khanfarhana.info

**A custom WordPress theme and content platform for Khan Farhana —<br>youth development leader, SDG champion and LinkedIn creator.**

<br>

[![Live Site](https://img.shields.io/badge/Live_Site-khanfarhana.info-26bde2?style=for-the-badge&logo=googlechrome&logoColor=white)](https://khanfarhana.info)
[![Status](https://img.shields.io/badge/Status-In_Production-4c9f38?style=for-the-badge)](https://khanfarhana.info)
[![Version](https://img.shields.io/badge/Theme-v1.5.50-19486a?style=for-the-badge)](#-release-history)

![WordPress](https://img.shields.io/badge/WordPress_6.x-21759B?style=flat-square&logo=wordpress&logoColor=white)
![PHP](https://img.shields.io/badge/PHP_7.4+-777BB4?style=flat-square&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Google Fonts](https://img.shields.io/badge/Google_Fonts-4285F4?style=flat-square&logo=googlefonts&logoColor=white)

<br>

[Overview](#-project-overview) &nbsp;·&nbsp;
[Case Study](#-case-study) &nbsp;·&nbsp;
[How It Works](#-how-the-website-works) &nbsp;·&nbsp;
[Features](#-key-features) &nbsp;·&nbsp;
[Screenshots](#-screenshots) &nbsp;·&nbsp;
[Tech Stack](#-tech-stack) &nbsp;·&nbsp;
[Process](#-development-process) &nbsp;·&nbsp;
[Results](#-results)

</div>

<br>

> [!NOTE]
> This is a **portfolio presentation repository**. It documents the design, architecture and outcomes of the project. The production source code is private and is not included here.

<br>

## <img src="assets/icons/panels-top-left.svg" width="22" align="top"> Project Overview

| | |
|---|---|
| **Client** | Khan Farhana — Head of Programmes, Partnerships & Youth Engagement, Dotlines Social Enterprise; Founder, Farhana's Brainstation |
| **Project type** | Personal brand website, content hub and lightweight CMS |
| **My role** | Sole developer — UX/UI design, front-end, back-end, admin tooling, deployment and maintenance |
| **Platform** | WordPress with a fully custom theme built from scratch (no page builder, no premium theme) |
| **Timeline** | Initial build and launch June 2026, ongoing iteration through v1.5.x |
| **Live URL** | [khanfarhana.info](https://khanfarhana.info) |
| **Developed by** | Abdullah Al Fahim — Utopia Softtech Inc. |

Khan Farhana is a development professional with 8+ years of work across Bangladesh, Timor-Leste and Botswana, including UNDP Timor-Leste, and a LinkedIn community of 400K+ people. Her online presence was spread across LinkedIn posts, newsletters, press coverage, award announcements and community programmes. There was no single place that told the whole story or gave organisations an easy way to collaborate with her.

The goal was a site that works as a **credible professional profile**, a **content hub** for everything she publishes, and a **conversion tool** for partnerships, speaking and services — all of it editable by a non-technical team without touching code.

<br>

## <img src="assets/icons/target.svg" width="22" align="top"> Case Study

### The challenge

<table>
<tr>
<td width="50%" valign="top">

**Business problems**

- Achievements, press coverage and awards were scattered across LinkedIn and partner sites
- No clear funnel for organisations wanting to hire, partner or sponsor
- Her community initiative, Farhana's Brainstation, had no home of its own
- Campaigns and fellowships needed sign-up forms on short notice

</td>
<td width="50%" valign="top">

**Technical constraints**

- Content updated often by non-developers
- Most visitors arrive from LinkedIn on mobile
- Bangla and English content side by side
- Must run on standard shared WordPress hosting with no paid plugins

</td>
</tr>
</table>

### The approach

1. **Content audit first.** Every piece of existing content (roles, awards, seminars, media features, testimonials, newsletters, projects) was inventoried and grouped. Each group became either a custom post type or a structured settings screen.
2. **Design around credibility.** The visual language borrows the 17 UN Sustainable Development Goal colours, tying her SDG work to the brand. A serif display face (Fraunces) paired with Plus Jakarta Sans gives an editorial, trustworthy tone; Tiro Bangla handles Bengali text.
3. **A homepage that tells a story.** The homepage is a scroll narrative: who she is, a decade of milestones, career journey, measurable impact, services, projects, SDG goals, seminars, awards, media, community, newsletters, testimonials, partners and a gallery — ending in a contact form.
4. **Admin-first CMS.** Instead of asking the client to learn a page builder, every section has its own purpose-built editor screen in the WordPress dashboard.
5. **No framework overhead.** Plain PHP templates, one hand-written stylesheet and one vanilla JavaScript file. No jQuery dependency on the front end, no build step required on the server.

### The solution

A bespoke WordPress theme with:

- **10 page templates** and **6 custom post types**
- **35+ custom admin screens** grouped into Homepage, Insights, Farhana's Brainstation, Campaign and Resume menus
- **6 public AJAX endpoints** for contact, newsletter, service requests, campaign sign-ups and community blog submissions
- A **form builder** for campaign registration pages
- A **community blog submission** flow with moderation
- **Maintenance mode**, a branded **login page** and a scheduled **ad/announcement popup**, all controlled from the dashboard

<br>

## <img src="assets/icons/workflow.svg" width="22" align="top"> How the Website Works

### Architecture

```mermaid
flowchart LR
    V([Visitor]) -->|HTTPS| WP[WordPress]
    WP --> T[Theme templates]
    T --> CPT[(Post types)]
    T --> OPT[(Section data)]
    T --> FE[CSS + JS]
    FE -->|AJAX| AX[Form handlers]
    AX --> MAIL[Email alerts]
    AX --> MOD[Review queue]
    ED([Editor]) --> ADM[Admin screens]
    ADM --> CPT
    ADM --> OPT
```

### Content model

Content lives in two places, chosen by how it behaves:

| Kind of content | Stored as | Examples |
|---|---|---|
| Repeating, linkable items | Custom post types with meta boxes | Featured stories, media coverage, awards, projects, testimonials, LinkedIn posts |
| One-off page sections | Structured JSON in WordPress options | Hero, about, timeline, impact counters, partners, gallery, footer, resume entries |
| Community articles | Standard posts, created as `pending` | Guest blog submissions awaiting review |

Each custom post type carries its own fields — source, display date, external URL, SDG number and card accent colour — so cards across the site render consistently and can link to an SDG.

### Request lifecycle

1. A visitor opens a page. WordPress resolves it to one of the theme's templates (`front-page`, `page-resume`, `page-services`, `page-fbs`, and so on).
2. The template pulls section data from options and queries the relevant custom post types.
3. Assets load once: a single stylesheet, a single script, Google Fonts and Material Icons. Page-specific libraries (for example the international phone input on the campaign page, or PDF.js for the CV viewer) load only where they are needed.
4. Interactions run in vanilla JavaScript: dropdown navigation with hover intent and keyboard support, drag-to-scroll card rows, arrow/dot carousels, popups, a PDF viewer and form submission.
5. Forms post to `admin-ajax.php`. Each handler verifies a nonce, sanitises every field, validates uploads (image MIME types, 5 MB cap) and then emails the team or stores a pending post.

### Editor workflow

```mermaid
flowchart LR
    A[Log in] --> B[Open section editor]
    B --> C[Edit fields and media]
    C --> D[Save and validate]
    D --> E[Live on site]
```

<br>

## <img src="assets/icons/sparkles.svg" width="22" align="top"> Key Features

<table>
<tr>
<td width="50%" valign="top">

#### <img src="assets/icons/user-round.svg" width="18" align="top"> Personal brand
- Storytelling homepage with 17 sections
- Sticky right column with LinkedIn profile card, services and a fellowship call to action
- Interactive decade timeline and career journey
- Animated impact counters
- Resume page with tabs and an in-browser CV viewer (PDF.js)

</td>
<td width="50%" valign="top">

#### <img src="assets/icons/file-text.svg" width="18" align="top"> Content hub
- Archives for blog, featured stories and media coverage
- Awards, projects and seminars with "see more" popups
- LinkedIn newsletter showcase
- Recommendation wall of testimonials
- SDG goal grid with per-goal project popups

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### <img src="assets/icons/mail.svg" width="18" align="top"> Conversion
- Contact form with purpose selector (speaking, collaboration, partnership, sponsorship)
- Services page with per-service request forms
- Newsletter subscription
- Campaign pages built from a drag-and-configure form builder
- "Collaborate" calls to action throughout

</td>
<td width="50%" valign="top">

#### <img src="assets/icons/settings-2.svg" width="18" align="top"> Admin and operations
- Dedicated editor for every homepage section
- Resume editor with tabs, media library and colour pickers
- Farhana's Brainstation sub-site editor (hero, mission, team, projects, gallery, YouTube)
- Site-wide maintenance mode with admin bypass
- Scheduled announcement popup and branded login screen

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### <img src="assets/icons/book-open-check.svg" width="18" align="top"> Community
- Farhana's Brainstation section with Leadership Fellowship and Opportunities Hub
- Public "Write a Blog" form with featured image upload
- Submissions saved as pending for editorial review

</td>
<td width="50%" valign="top">

#### <img src="assets/icons/smartphone.svg" width="18" align="top"> Experience details
- Fully responsive, mobile-first navigation
- Keyboard-accessible menus (Enter, Space, Escape)
- Arrow-key navigation for horizontal card rows
- Copy-link and share buttons on articles
- A small birthday easter egg with confetti, once a year

</td>
</tr>
</table>

<br>

## <img src="assets/icons/images.svg" width="22" align="top"> Screenshots

### Homepage

<img src="screenshots/desktop/home.jpg" alt="Homepage hero" width="100%">

<details>
<summary><b>View the full homepage (long screenshot)</b></summary>
<br>
<img src="screenshots/desktop/home-full.jpg" alt="Full homepage" width="100%">
</details>

### Homepage sections

<table>
<tr>
<td width="50%"><img src="screenshots/desktop/home-about.jpg" alt="About section"><br><sub><b>About</b> — profile and story</sub></td>
<td width="50%"><img src="screenshots/desktop/home-timeline.jpg" alt="Timeline section"><br><sub><b>A Decade of Impact</b> — milestone carousel</sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/home-impact.jpg" alt="Impact counters"><br><sub><b>Impact That Speaks</b> — key numbers</sub></td>
<td><img src="screenshots/desktop/home-sdgs.jpg" alt="SDG goals"><br><sub><b>Goals She Champions</b> — SDG grid</sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/home-projects.jpg" alt="Projects"><br><sub><b>Projects</b> — horizontal card row</sub></td>
<td><img src="screenshots/desktop/home-awards.jpg" alt="Awards"><br><sub><b>Awards and Certifications</b></sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/home-blog.jpg" alt="Blog"><br><sub><b>From the Newsletter</b> — latest posts</sub></td>
<td><img src="screenshots/desktop/home-newsletters.jpg" alt="LinkedIn newsletters"><br><sub><b>LinkedIn Newsletters</b></sub></td>
</tr>
</table>

### Inner pages

<table>
<tr>
<td width="50%"><img src="screenshots/desktop/resume.jpg" alt="Resume"><br><sub><b>Resume</b> — career, seminars, awards, CV viewer</sub></td>
<td width="50%"><img src="screenshots/desktop/services.jpg" alt="Services"><br><sub><b>Services</b> — offers with request forms</sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/brainstation.jpg" alt="Farhana's Brainstation"><br><sub><b>Farhana's Brainstation</b> — community sub-site</sub></td>
<td><img src="screenshots/desktop/fellowship.jpg" alt="Leadership Fellowship"><br><sub><b>Leadership Fellowship</b></sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/media-coverage.jpg" alt="Media coverage"><br><sub><b>Media Coverage</b> archive</sub></td>
<td><img src="screenshots/desktop/featured-stories.jpg" alt="Featured stories"><br><sub><b>Featured Stories</b> archive</sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/blog.jpg" alt="Blog"><br><sub><b>Blog</b> archive</sub></td>
<td><img src="screenshots/desktop/write-blog.jpg" alt="Write a blog"><br><sub><b>Write a Blog</b> — community submissions</sub></td>
</tr>
<tr>
<td><img src="screenshots/desktop/recommendation-wall.jpg" alt="Recommendation wall"><br><sub><b>Recommendation Wall</b></sub></td>
<td><img src="screenshots/desktop/opportunities.jpg" alt="Opportunities hub"><br><sub><b>Opportunities Hub</b></sub></td>
</tr>
</table>

### Mobile

<table>
<tr>
<td width="25%"><img src="screenshots/mobile/home.jpg" alt="Mobile homepage"><br><sub>Home</sub></td>
<td width="25%"><img src="screenshots/mobile/home-about.jpg" alt="Mobile about"><br><sub>About</sub></td>
<td width="25%"><img src="screenshots/mobile/resume.jpg" alt="Mobile resume"><br><sub>Resume</sub></td>
<td width="25%"><img src="screenshots/mobile/services.jpg" alt="Mobile services"><br><sub>Services</sub></td>
</tr>
<tr>
<td><img src="screenshots/mobile/brainstation.jpg" alt="Mobile Brainstation"><br><sub>Brainstation</sub></td>
<td><img src="screenshots/mobile/blog.jpg" alt="Mobile blog"><br><sub>Blog</sub></td>
<td><img src="screenshots/mobile/media-coverage.jpg" alt="Mobile media"><br><sub>Media</sub></td>
<td><img src="screenshots/mobile/write-blog.jpg" alt="Mobile write a blog"><br><sub>Write a Blog</sub></td>
</tr>
</table>

More full-page captures are in the [gallery](GALLERY.md).

<br>

## <img src="assets/icons/palette.svg" width="22" align="top"> Design System

| Token | Value | Use |
|---|---|---|
| Display type | Fraunces (serif, with italics) | Headlines and names |
| Body type | Plus Jakarta Sans | Interface and body copy |
| Bengali type | Tiro Bangla | Bangla content |
| Icons | Material Icons Round | Interface icons |
| Primary accent | `#26bde2` | Links, highlights, buttons |
| Deep navy | `#19486a` | Gradients, footer, dark surfaces |
| SDG palette | 17 official SDG colours as CSS variables (`--sdg-1` to `--sdg-17`) | Card accents, dividers, SDG badges |

The 17-colour SDG strip appears as a divider under heroes and in the footer, a constant visual reminder of the client's focus on the Global Goals.

<br>

## <img src="assets/icons/layers.svg" width="22" align="top"> Tech Stack

| Layer | Technology |
|---|---|
| CMS | WordPress 6.x |
| Theme | Custom, built from scratch — PHP templates, template parts, modular `inc/` includes |
| Styling | Hand-written CSS with custom properties, 80+ responsive breakpoint rules |
| Scripting | Vanilla JavaScript (ES6), `ResizeObserver`, `IntersectionObserver` |
| Data | Custom post types, post meta, JSON in the options table |
| Forms | WordPress AJAX API, nonces, `wp_mail`, `media_handle_upload` |
| Third-party | PDF.js (CV viewer), intl-tel-input (phone fields), Elfsight (social widgets), WonderPush (web push) |
| Fonts and icons | Google Fonts, Material Icons Round |
| Tooling | Git and GitHub, Visual Studio |

### Codebase at a glance

| Metric | Count |
|---|---|
| Lines of PHP, CSS and JS | ~30,000 |
| Page templates | 10 |
| Single-post templates | 6 |
| Custom post types | 6 |
| Modular include files | 30+ |
| Custom admin screens | 35+ |
| Public AJAX endpoints | 6 |

<br>

## <img src="assets/icons/shield-check.svg" width="22" align="top"> Security and Quality

- **Nonce verification** on every form submission and admin save
- **Input sanitisation and output escaping** using WordPress core functions
- **Upload validation** — image MIME whitelist (JPEG, PNG, GIF, WebP) and a 5 MB size limit
- **Moderation by default** — community blog posts are saved as `pending`, never published directly
- **Capability checks** — editors can manage content, only administrators can change site-wide settings
- **Maintenance gate** that never blocks wp-admin, AJAX, REST or cron, so the team can keep working while the site is offline

<br>

## <img src="assets/icons/gauge.svg" width="22" align="top"> Performance and Accessibility

- One stylesheet and one script for the whole theme, loaded in the footer where possible
- Conditional loading of heavy libraries (PDF.js, intl-tel-input) only on the pages that use them
- Lazy-loaded images in archives and card rows
- No page builder and no jQuery on the front end
- Semantic HTML, keyboard-operable dropdowns and popups (Escape to close), visible focus states
- `ResizeObserver` keeps carousel arrows accurate as content changes

<br>

## <img src="assets/icons/git-branch.svg" width="22" align="top"> Development Process

```mermaid
timeline
    title Project timeline (2026)
    May    : Discovery and content audit
           : Information architecture
    June   : Design system and homepage build
           : Custom post types and admin editors
           : Launch on khanfarhana.info
    July   : Resume editor and documentation
    Ongoing : Brainstation sub-site, campaign form builder
            : Community blog submissions, continuous refinements
```

1. **Discovery** — worked with the client to collect her LinkedIn content, press and awards, and defined the audiences: organisations, media and young people.
2. **Information architecture** — mapped navigation into About, Services, Farhana's Brainstation, Courses, Newsletter and Insights.
3. **Design** — built the SDG-based palette and typography, then designed the homepage as a single narrative.
4. **Build** — templates first, then custom post types, then one admin editor per section so content could be loaded while development continued.
5. **Content load and QA** — tested on real phones and desktop browsers, checked forms end to end and verified email delivery.
6. **Launch and iteration** — released early and shipped improvements in small versions (v1.1 to v1.5.x) based on client feedback.

<br>

## <img src="assets/icons/lightbulb.svg" width="22" align="top"> Challenges and Solutions

| Challenge | Solution |
|---|---|
| The client team needed to update almost every section without a developer | Wrote a dedicated admin screen for each section with media pickers, colour pickers and repeatable rows, storing data as structured JSON |
| Long homepage risked feeling heavy on mobile | Horizontal, drag-to-scroll card rows with arrows and dots keep each section compact; a sticky side column on desktop collapses on mobile |
| Campaigns change often and each needs different form fields | Built a campaign form builder in the dashboard so new registration forms can be configured without code |
| Visitors wanted to read the CV without downloading it | Embedded PDF.js to render the CV page by page in a modal with a page indicator |
| Open submission forms attract spam and unsafe uploads | Nonces, strict sanitisation, MIME and size checks, and a pending-review workflow |
| Mixed Bangla and English content | Added Tiro Bangla to the type stack so both scripts render cleanly together |

<br>

## <img src="assets/icons/circle-check.svg" width="22" align="top"> Results

- **One home for a 400K+ community** — profile, programmes, press, awards and writing now live under a single domain
- **Clear routes to collaboration** — contact, services and campaign forms replace ad-hoc LinkedIn messages
- **Self-managed content** — the client team updates the site through purpose-built editors with no developer involvement
- **Room to grow** — Farhana's Brainstation, the Leadership Fellowship and the Opportunities Hub were added after launch without restructuring the theme
- **Continuous delivery** — iterated from v1.0 to v1.5.50 in small, frequent releases

<br>

## <img src="assets/icons/milestone.svg" width="22" align="top"> Release History

| Version | Highlights |
|---|---|
| v1.0 | Launch: storytelling homepage, custom post types, AJAX contact form, custom login page |
| v1.1 | 404 page, privacy policy, media and cover story archive, testimonial system, Collaborate CTA, Resume Editor |
| v1.5.x | Section-by-section homepage editors, services and service requests, Farhana's Brainstation sub-site, campaign form builder, community blog submissions, maintenance mode, announcement popup and ongoing refinements |

<br>

## <img src="assets/icons/accessibility.svg" width="22" align="top"> What I Learned

- A CMS is only as good as its editing experience. Building purpose-made editor screens took longer than adding a page builder, but the client now updates the site confidently.
- Splitting a large `functions.php` into focused `inc/` modules made it practical to ship small, frequent releases.
- Designing the homepage as a story, rather than a list of sections, made it far easier to decide what belonged on it.

<br>

## <img src="assets/icons/external-link.svg" width="22" align="top"> Links

- **Live website:** [khanfarhana.info](https://khanfarhana.info)
- **Developer:** [Abdullah Al Fahim on LinkedIn](https://linkedin.com/in/abdullahalfahim) · [GitHub](https://github.com/abdullah-al-faahim)

<br>

---

<div align="center">
<sub>
Designed and developed by <b>Abdullah Al Fahim</b> — Utopia Softtech Inc.<br>
All screenshots, names, photographs and content belong to Khan Farhana and are shown with permission for portfolio purposes only.<br>
Icons by <a href="https://lucide.dev">Lucide</a> (ISC License). Badges by <a href="https://shields.io">Shields.io</a> with <a href="https://simpleicons.org">Simple Icons</a>.
</sub>
</div>
