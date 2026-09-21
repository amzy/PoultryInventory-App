# OvalOasis Poultry Farm Management App

OvalOasis is a poultry farm management product focused on helping farmers and farm teams keep operational records, understand farm performance, and manage day-to-day poultry business information from one place.

The repository contains the application source, Flutter web application deployment output, Firebase Functions, Android distribution assets, and the canonical marketing website source.

## Product

**Product:** OvalOasis Poultry Farm Management App  
**Repository:** `amzy/PoultryInventory-App`  
**Marketing website:** https://www.ovaloasis.in  
**Web application:** https://app.ovaloasis.in  
**Technology:** Flutter + Firebase  
**Primary positioning:** Smart farming and practical poultry-farm record management.

OvalOasis is designed around a simple product promise:

> **Manage Your Poultry Farm Smarter**

The product experience is intended to make farm records easier to capture, review, and turn into useful operational information without relying on disconnected notebooks, spreadsheets, or repeated manual calculations.

---

## Repository Purpose

This repository is the application and distribution source for OvalOasis.

It includes:

- Flutter application source and platform integrations
- Firebase-backed services and Cloud Functions
- Web application deployment files
- Android APK distribution
- Canonical marketing website source
- GitHub Actions deployment workflows
- Product and operational documentation

### Important source-of-truth rule

The `website/` directory is the canonical marketing website source.

The public website repository, `amzy/PoultryInventory-Website`, is a deployment mirror only. Website changes must be made in this repository first and then synchronized by the deployment workflow.

Do not reconstruct the website from an older ZIP, generated build, or public mirror.

---

# Product Capabilities

OvalOasis is organized around the operational areas needed by a poultry farm.

### Flock and Daily Operations

- Flock configuration
- Bird population tracking
- Daily production and consumption records
- Weight and activity information
- Farm operational records
- Historical record management

### Sales and Lifting

The application distinguishes persisted sale classifications:

- `average_lift`
- `direct_lift`
- `cutting_sale`

Historical Average Lift and Direct Lift records can be edited while preserving their persisted classification.

The application treats persisted sale classification as authoritative rather than repeatedly inferring it from other fields.

### Expenses and Categories

- Expense records
- Main expense categories
- Expense subcategories
- Category administration
- Historical expense management

Default expense categories and subcategories are maintained through the application reference-data system.

### Reports and Farm Insight

The product is designed to turn recorded farm data into useful operational views, including:

- Production trends
- Expense and sales information
- Farm performance indicators
- Historical records
- Business-oriented summaries

### Web/Desktop Administration

The web experience supports administration and larger-screen workflows such as:

- Settings
- Categories management
- Flock configuration
- Reference data
- Operational administration

---

# Architecture

OvalOasis follows a local-first approach for important application data.

### Mobile

Mobile workflows prioritize local cached data so the interface can remain responsive while synchronization happens in the background.

### Web/Desktop

Web and desktop workflows use browser persistence and Firestore-backed data.

### Dashboard rendering

The intended dashboard flow is:

1. Load local/cache data.
2. Render priority cards immediately.
3. Synchronize incremental changes.
4. Update the local cache.
5. Refresh only affected cards.

The architecture intentionally avoids unnecessary full Firestore reads, repeated expensive calculations, and repeated full-history scans.

### Smart synchronization

Expense records use cursor-based synchronization.

The current architecture includes:

- local cache rendering
- delta synchronization
- persistent sync cursor
- Firestore change logging
- callable Cloud Function synchronization
- fallback full snapshots
- transient-failure cache retention
- sync attempt cooldown/coalescing

The expense synchronization callable is deployed in `asia-south1`.

---

# Technology Stack

## Application

- Flutter
- Dart
- Android
- iOS
- Flutter Web

## Backend

- Firebase
- Cloud Firestore
- Firebase Cloud Functions
- Node.js

## Persistence and synchronization

- Local caching
- SharedPreferences
- Firestore
- Cursor-based reference and expense synchronization

## Marketing website

- HTML
- CSS
- JavaScript
- SVG assets
- GitHub Pages/deployment mirror

---

# Repository Structure

Important directories and files:

```text
.
├── lib/                         # Flutter application source
├── functions/                   # Firebase Cloud Functions
├── android/                     # Android platform project
├── ios/                         # iOS platform project
├── web/                         # Flutter Web deployment output
├── website/                     # Canonical OvalOasis marketing website
├── .github/workflows/           # Deployment automation
├── poultry-inventory.apk        # APK distribution artifact
├── source-version.txt           # Release version metadata
├── README.md                    # Repository and product documentation
└── docs/
    ├── BUSINESS_LOGIC.md        # Product/business rules
    ├── UI_GUIDELINES.md         # UI and interaction rules
    └── PROJECT_OPERATIONS.md    # Architecture/deployment/operations
```

---

# Marketing Strategy

## 1. Positioning

OvalOasis should be presented as a **practical poultry farm management system**, not simply as another generic farm-record application.

The marketing message should focus on the operational outcome:

**Less manual record keeping → clearer farm information → better day-to-day decisions.**

Core message:

> **Manage Your Poultry Farm Smarter**

Supporting themes:

- Keep farm records organized.
- Capture daily information quickly.
- Understand expenses and sales.
- Track flock performance.
- Access farm information from the web and mobile experience.
- Turn operational records into useful insight.

Marketing should demonstrate the product rather than relying on unsupported claims.

---

## 2. Target Audience

The product communication should primarily address:

### Poultry Farm Owners

Key concerns:

- Understanding farm performance
- Tracking expenses and sales
- Keeping historical records
- Reducing manual bookkeeping
- Accessing important information quickly

### Farm Managers and Operators

Key concerns:

- Fast daily data entry
- Consistent operational records
- Flock monitoring
- Expense and production tracking
- Easy access to historical information

### Farm Administration Teams

Key concerns:

- Categories and reference data
- Consistent records
- Business reporting
- Web/desktop administration
- Centralized farm information

The repository currently documents these product capabilities, but it does not establish quantified market size, customer counts, or conversion benchmarks. Such claims should not be added unless independently verified.

---

# Marketing Funnel

The intended customer journey should be simple:

```text
Awareness
   ↓
Marketing Website
   ↓
Product Features / Screenshots / Demo
   ↓
Download App
   ↓
First Farm Setup
   ↓
Daily Usage
   ↓
Repeat Usage
   ↓
Product Adoption
```

## Awareness

Use practical poultry-farming problems as the entry point.

Example topics:

- How to organize poultry farm records
- Tracking daily flock information
- Managing poultry farm expenses
- Tracking poultry sales and lifting records
- Moving from notebooks to digital farm records
- Understanding farm performance from daily records

The content should educate first and promote the product second.

## Consideration

The website should show the actual product experience through:

- Product screenshots
- Feature explanations
- Interactive demo
- Clear workflow examples
- Short product demonstrations
- Practical use cases

Avoid vague marketing language when a concrete product workflow can be shown instead.

## Conversion

The primary website CTA should remain clear:

**Download App**

The website should provide a direct, stable APK download path.

Current release asset:

```text
https://github.com/amzy/PoultryInventory-App/releases/download/latest/poultry-inventory.apk
```

The website should not reference an APK filename that is not actually present in the current GitHub release.

## Retention

Retention messaging should focus on recurring farm workflows:

- Daily records
- Expense entry
- Sales/lifting records
- Flock monitoring
- Reports and historical information

The objective is to make OvalOasis part of the farm's normal daily record-keeping routine.

---

# Marketing Website Strategy

The marketing website is intentionally structured around:

- Brand introduction
- Product hero message
- Features
- Screenshots
- Product demo
- Why OvalOasis
- Support
- Download CTA

The current visual direction is:

- green / cream / white
- clean agricultural branding
- modern dashboard presentation
- poultry/farm imagery
- practical product screenshots
- prominent download CTA

The website should remain product-focused and should not introduce fabricated:

- farmer testimonials
- customer counts
- revenue claims
- adoption statistics
- performance guarantees
- unsupported awards or certifications

---

# Content Strategy

A sustainable marketing content plan should use three content groups.

### Educational content

Explain real poultry-farm management problems.

Examples:

- Daily poultry record checklist
- Poultry expense tracking
- Flock record organization
- Poultry sales record management
- Farm performance tracking

### Product education

Show how OvalOasis handles a specific workflow.

Examples:

- Creating a flock
- Recording daily production
- Adding an expense
- Managing categories
- Recording a sale
- Reviewing farm reports

### Proof through product experience

Use actual:

- screenshots
- short demonstrations
- UI walkthroughs
- workflow examples
- product updates

This creates evidence through the product itself instead of depending on unsupported promotional claims.

---

# SEO Direction

The website and content should naturally target phrases related to the product category, such as:

- poultry farm management app
- poultry farm management software
- poultry farm record keeping
- poultry expense management
- poultry flock management
- poultry farm accounting records
- poultry production tracking
- poultry sales management

SEO content should remain useful and specific. Avoid keyword stuffing.

---

# Marketing Measurement

The repository does not currently define validated marketing targets. For future marketing work, useful measurements can include:

### Acquisition

- Website visits
- Search impressions
- Search clicks
- Referral traffic
- Campaign traffic

### Conversion

- Download CTA clicks
- APK downloads
- App installation signals where measurable
- First farm setup completion

### Activation

- First flock created
- First daily record created
- First expense recorded
- First sale recorded

### Retention

- Returning users
- Daily/weekly active farm usage
- Repeated record entry
- Continued use of reports and business workflows

Marketing decisions should be based on measured product usage rather than assumptions.

---

# Release and Deployment

The intended deployment order is:

```text
1. Deploy Flutter Web App
2. If website/ changed → publish marketing website
3. Publish APK
```

The deployment workflow is:

```text
.github/workflows/release-order.yml
```

The APK release uses the stable GitHub release tag:

```text
latest
```

and the asset:

```text
poultry-inventory.apk
```

Website download links must match the actual release asset name.

---

# Development Rules

## Business logic

Business rules belong in the application implementation and should be documented in:

```text
docs/BUSINESS_LOGIC.md
```

Do not duplicate business rules across temporary change-log Markdown files.

## UI

UI conventions and persistent interaction rules belong in:

```text
docs/UI_GUIDELINES.md
```

## Operations

Deployment and source-management rules belong in:

```text
docs/PROJECT_OPERATIONS.md
```

## Website

The canonical website source is:

```text
website/
```

Do not copy website changes backward from the public deployment mirror.

---

# Verification Policy

Do not claim that Flutter analyzer, tests, or production builds succeeded unless they have actually been executed successfully.

For JavaScript changes:

```bash
node --check website/script.js
```

For Firebase Functions:

```bash
node --check functions/index.js
```

For Firebase deployment:

```bash
cd functions
npm install
cd ..
firebase deploy --only functions
```

Reference synchronization functions must use the configured `asia-south1` region.

---

# Documentation Policy

Keep the repository documentation small and authoritative.

Permanent documentation belongs in:

- `README.md`
- `docs/BUSINESS_LOGIC.md`
- `docs/UI_GUIDELINES.md`
- `docs/PROJECT_OPERATIONS.md`

Do not accumulate dated troubleshooting notes, duplicate deployment guides, or temporary fix Markdown files in the repository.

Git commits should provide the historical record of implementation changes.

---

# Product Principles

OvalOasis development should prioritize:

1. Reliable farm records
2. Fast daily workflows
3. Local-first responsiveness
4. Efficient synchronization
5. Clear business information
6. Consistent UI
7. Mobile and web accessibility
8. Data integrity
9. Practical product marketing
10. Evidence-based product communication

The goal is to make the application useful enough that the product experience itself becomes the primary marketing asset.

---

## Related Documentation

- `docs/BUSINESS_LOGIC.md`
- `docs/UI_GUIDELINES.md`
- `docs/PROJECT_OPERATIONS.md`
- `website/WEBSITE_SOURCE_RULE.md`

---

## Brand

**OvalOasis**  
**Smart Farming. Better Tomorrow.**

Marketing website: https://www.ovaloasis.in
