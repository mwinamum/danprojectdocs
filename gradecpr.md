# GradeCPR Platform - Product Requirements Document (PRD)

**Domain:** GradeCPR.com  
**Date:** June 6, 2026  
**Version:** 2.1  
**Status:** Finalized

---

## 1. Project Overview

GradeCPR is an academic support platform designed to help students access and understand assignment requirements across **2,195+ documents** from six major universities. The platform provides clear, readable access to course assignment instructions while protecting original content through standard technical measures. Students can review assignment prompts, understand expectations, and reach out for further academic guidance through official contact channels.

**Core Mission:** *Provide transparent access to academic assignment information while maintaining content integrity.*

---

## 2. Technology Stack

| Layer | Technology |
|:---|:---|
| Frontend | .NET Blazor |
| Backend API | .NET Core Web API |
| Database | PostgreSQL |
| Hosting | Azure / AWS / Windows Server |

---

## 3. Information Architecture

The platform follows a simple, three-tier structure:

```
Homepage (University Selection)
       │
       ▼
Course Index Page (Course Codes)
       │
       ▼
Document Page (Assignment Instructions)
```

### 3.1 Level 1: Homepage – University Selection

Students land on the homepage and choose from six universities:

| University | Course Count | Document Count |
|:---|:---:|:---:|
| Capella University | 11 | 104 |
| University of Phoenix (UOP) | 85+ | 776 |
| University of Arizona Global Campus (UAGC) | 40+ | 839 |
| Trident University | 21 | 287 |
| Columbia Southern University | 1 | 27 |
| Southern New Hampshire University (SNHU) | 90+ | 162 |
| **TOTAL** | **255+** | **2,195** |

### 3.2 Level 2: Course Index Page

After selecting a university, students see a clean, searchable list of course codes specific to that institution, each showing how many documents are available.

### 3.3 Level 3: Document Page

The final page displays the actual assignment instructions. This is the primary landing page from search engines, where students read specific assessment requirements.

**URL pattern:** `GradeCPR.com/{university}/{course-code}/{assignment-name}`

---

## 4. Functional Requirements

### 4.1 Content Management System (CMS)

| Requirement | Description |
|:---|:---|
| **Content Format** | All documents stored as HTML text — no PDFs or downloadable files |
| **Content Type** | Assignment instructions and prompts only (no completed answers or solutions) |
| **Dynamic Page Titles** | Each page automatically generates SEO-friendly `<title>` and meta description based on university, course, and assignment |
| **Breadcrumbs** | Automatic navigation trail showing: Home > University > Course > Assignment |
| **University Branding** | Subtle color themes (e.g., UOP red, SNHU blue, Capella maroon) applied per university |
| **Document Counts** | Each course clearly displays number of available documents |
| **Admin Interface** | Password-protected CMS for adding/editing documents and courses |

### 4.2 Content Protection

To protect the original content from unauthorized copying, the platform implements standard browser-based protections:

| Protected Action | Method |
|:---|:---|
| Right-click | Disabled on document pages |
| Text selection | Disabled (cannot highlight text) |
| Copy (Ctrl+C / Cmd+C) | Intercepted and blocked |
| View source (Ctrl+U) | Intercepted |
| Save page (Ctrl+S) | Intercepted |
| Developer Tools (F12) | Console notice displayed |

**Important Note:** These protections apply only to browser-based interactions. Search engines can still fully index all content for SEO purposes. Screen readers and accessibility tools retain full access.

### 4.3 Student Support Channels

Every document page prominently displays contact information for academic guidance:

**Persistent contact bar** (visible on all pages):
- Email: `Contact@GradeCPR.com`
- Phone: `(612) 208-2686`

**Support card on every document page:**
- Heading: "Need Help Understanding This Assignment?"
- Message: "Our academic team can provide guidance and clarification for this specific assignment."
- Email and phone number prominently displayed
- Privacy assurance: "Confidential • Responsive • Supportive"

---

## 5. Database Requirements

The system requires a PostgreSQL database with three core tables:

| Table | Purpose |
|:---|:---|
| **Universities** | Stores university names, URL slugs, brand colors, and document counts |
| **Courses** | Stores course codes (e.g., HCS/380), linked to universities |
| **Documents** | Stores assignment names, HTML content, word counts, and relationships to courses |

**Key capabilities:**
- Fast lookups across 2,195+ documents
- Full-text search across all assignment content
- Efficient pagination and filtering

---

## 6. API Requirements

The backend API must provide the following endpoints:

| Endpoint | Purpose |
|:---|:---|
| `GET /api/universities` | Retrieve list of all universities |
| `GET /api/universities/{slug}/courses` | Retrieve courses for a specific university |
| `GET /api/courses/{slug}/documents` | Retrieve documents for a specific course |
| `GET /api/documents/{slug}` | Retrieve single document content |
| `GET /api/search?q={query}` | Search across all documents |

All API responses should be JSON format with appropriate caching headers for performance.

---

## 7. Performance Requirements

| Metric | Target |
|:---|:---|
| Page load time (LCP) | Under 2.5 seconds |
| Interaction delay (FID) | Under 100 milliseconds |
| Layout stability (CLS) | Under 0.1 |
| API response time | Under 200 milliseconds |

These standards are required to maximize organic search rankings for competitive course terms.

---

## 8. Complete University Course Inventory

### 8.1 Capella University (104 documents)

| Course Code | Document Count |
|:---|:---:|
| COM-FPX 1250 | 7 |
| COM-FPX 3700 | 3 |
| BHA-FPX 4102 | 9 |
| NHS 4000 | 8 |
| NURS-FPX 4010 | 9 |
| NURS-FPX 4020 | 11 |
| NURS-FPX 4030 | 14 |
| NURS-FPX 4040 | 13 |
| NURS-FPX 4050 | 9 |
| NURS-FPX 4060 | 8 |
| NURS-FPX 4900 | 13 |
| **TOTAL** | **104** |

---

### 8.2 University of Phoenix (776 documents)

| Course Code | Docs | Course Code | Docs |
|:---|:---:|:---|:---:|
| ACC 205 | 1 | HIS 210 | 6 |
| ACC 208 | 7 | HIS 301 | 9 |
| BSACB 531 | 8 | HUM 105 | 6 |
| BUS 311 | 13 | HEL 133 | 7 |
| BUS 318 | 6 | HEL 134 | 7 |
| BUS 600 | 15 | SCI 220T | 3 |
| BUS 215 | 6 | SOC 100 | 5 |
| BUS 303 | 10 | SOC 110 | 3 |
| BUS 308 | 10 | SCI 256 | 6 |
| BUS 330 | 8 | CJS 201 | 9 |
| BUS 370 | 14 | CMGTCCB 582 | 5 |
| BUS 372 | 9 | CMGTCCB 583 | 6 |
| BUS 375 | 11 | CMGTCCB 578 | 6 |
| BUS 401 | 17 | CMGTCCB 545 | 6 |
| BUS 402 | 5 | CMGTCCB 558 | 6 |
| BUS 431 | 21 | CMGTCCB 556 | 6 |
| BUS 413 | 5 | CMGTCCB 554 | 6 |
| BUS 450 | 7 | CMGTCCB 559 | 6 |
| BUS 610 | 15 | CMGTCCB 555 | 6 |
| BUS 638 | 2 | CMGTCCB 575 | 6 |
| BUS 670 | 19 | CMGTCCB 576 | 6 |
| CAN 312 | 7 | DATCB 565 | 8 |
| ECE 332 | 10 | MHACB 520 | 7 |
| ECO 204 | 13 | MHACB 515 | 7 |
| ECO 316 | 10 | MHACB 598 | 7 |
| ENG 125 | 7 | MHACB 599 | 7 |
| FIN 301 | 9 | MHACB 516 | 7 |
| FIN 302 | 5 | MHACB 542 | 7 |
| FIN 190 | 2 | MHACB 543 | 7 |
| GEN 499 | 14 | MHACB 560 | 7 |
| HCA 460 | 1 | STHCCB 581 | 5 |
| HCA 421 | 7 | PSY 110 | 6 |
| HCA 460 | 7 | PSYCH 599 | 9 |
| HHS 320 | 7 | SEC 120 | 15 |
| HCS 380 | 5 | SEC 130 | 14 |
| HCS 430 | 7 | SOC 315 | 8 |
| HCS 457 | 7 | YFEB 240T | 5 |
| HCS 483 | 10 | HCS 385 | 10 |
| HCS 490 | 9 | HCS 131T | 5 |
| HIA 608 | 12 | ENG 110 | 5 |
| HIS 206 | 11 | COMM 110 | 10 |
| HCM 400 | 9 | COM 295T | 5 |
| INF 220 | 3 | EPSS 210 | 10 |
| MAT 222 | 5 | ECO 372T | 5 |
| MAT 232 | 11 | ENG 240 | 10 |
| MGT 435 | 1 | ENG 210 | 8 |
| MGT 450 | 10 | ETH 120 | 4 |
| MGT 601 | 3 | ETH 321T | 5 |
| MGT 330 | 8 | FIN 419T | 5 |
| MGT A15 | 1 | CMGT 245 | 5 |
| MGT 135 | 11 | ECH 418 | 6 |
| MGT 490 | 20 | ECH 302 | 9 |
| MGT 601 | 13 | ECH 400 | 10 |
| MHA GIE | 14 | FP 100T | 5 |
| | | HCIS 140T | 12 |
| | | HCS 120T | 13 |
| | | HCS 131T | 8 |
| | | HCS 235T | 8 |
| | | HCS 245T | 13 |
| | | HCS 305 | 10 |
| | | HCS 325 | 10 |
| | | HCS 335 | 9 |
| | | HCS 341 | 10 |
| | | HCS 370 | 10 |
| | | HCS 455 | 7 |
| | | HCS 456 | 9 |
| | | HCS 475 | 8 |
| | | HCS 499 | 10 |
| | | HUM 115 | 7 |
| | | MTH 213 | 4 |
| | | MTH 214 | 6 |
| | | MTH 215T | 5 |
| | | MTH 216T | 5 |
| **TOTAL** | **776** | | |

---

### 8.3 University of Arizona Global Campus (839 documents)

| Course Code | Docs | Course Code | Docs |
|:---|:---:|:---|:---:|
| MHA 618 | 4 | RES 345 | 16 |
| MHA 624 | 1 | RES 431 | 14 |
| MHA 601 | 3 | RES 497 | 15 |
| MHA 605 | 19 | RES 7115 | 3 |
| MHA 616 | 11 | RES 7400 | 8 |
| MHA 618 | 18 | SCI 207 | 24 |
| MHA 620 | 17 | SOC 205 | 13 |
| MHA 622 | 7 | SOC 301 | 5 |
| MHA 624 | 13 | SOC 308 | 7 |
| MHA 626 | 15 | EXP 105 | 2 |
| MHA 628 | 12 | INF 103 | 3 |
| MHA 630 | 13 | INF 336 | 4 |
| MHA 690 | 21 | OMM 615 | 10 |
| OMM 622 | 10 | OBG 7102 | 17 |
| OBG 8510 | 6 | OBG 8511 | 10 |
| PHI 280 | 11 | PHI 445 | 7 |
| PHM 300 | 11 | PHM 337 | 12 |
| PSY 325 | 8 | RES 327 | 12 |
| **TOTAL** | **839** | | |

---

### 8.4 Trident University (287 documents)

| Course Code | Document Count |
|:---|:---:|
| MGT 516 | 13 |
| ITM 517 | 10 |
| MGT 509 | 11 |
| BUS 502 | 12 |
| ITM 525 | 23 |
| MGT 599 | 17 |
| MKT 501 | 17 |
| LOG 503 | 17 |
| ACC 501 | 13 |
| FIN 501 | 13 |
| BUS 520 | 22 |
| LOG 501 | 12 |
| BUS 500 | 15 |
| MGT 501 | 9 |
| ETH 501 | 12 |
| BUS 590 | 12 |
| BUS 580 | 10 |
| HAM 520 | 13 |
| HAM 522 | 13 |
| HAM 509 | 13 |
| **TOTAL** | **287** |

---

### 8.5 Southern New Hampshire University (162 documents)

| Course Code | Course Code | Course Code |
|:---|:---|:---|
| OL 40235 | COM 30179 | MGT 30160 |
| OL 30158 | COM 30093 | MGT 30149 |
| IT 30232 | COM 30107 | MGT 30147 |
| HIM 30227 | COM 30108 | MGT 20066 |
| FIN 30219 | COM 30124 | MGT 20127 |
| INT 20075 | COM 30115 | MGT 30153 |
| INT 20151 | COM 30117 | MGT 30159 |
| ACC 20132 | COM 30122 | MGT 30152 |
| ACC 30134 | COM 30104 | MGT 30157 |
| ACC 20133 | COM 30102 | PHE 40211 |
| POL 10067 | COM 30121 | PHE 20247 |
| HAM 20143 | COM 30092 | PHE 30225 |
| MGT 30160 | COM 30180 | IHP 30241 |
| MGT 30160 | COM 30184 | IHP 40243 |
| MGT 20125 | COM 30105 | IHP 20239 |
| MGT 20136 | COM 20098 | HCM 30217 |
| MGT 20137 | COM 20111 | HCM 40216 |
| MGT 20135 | COM 20125 | HCM 40215 |
| MGT 30148 | COM 20091 | HCM 30229 |
| BUS 20068 | COM 20103 | HCM 30236 |
| BUS 30163 | COM 20099 | HCM 30230 |
| BUS 20161 | COM 30181 | HCM 30234 |
| BUS 20068 | COM 20113 | HCM 30288 |
| BUS 20069 | COM 30185 | HCM 30286 |
| MKT 20081 | COM 2023 | HCM 40283 |
| MKT 20080 | COM 20097 | HCM 40282 |
| MKT 20079 | COM 30096 | HCM 40281 |
| QSO 30167 | COM 30116 | HCM 30207 |
| QSO 20166 | COM 30094 | HCM 30210 |
| QSO 30164 | COM 30106 | HCM 30208 |
| QSO 30165 | COM 30109 | HCM 30206 |
| QSO 30169 | COM 30155 | |
| PHE 30241 | COM 30183 | |
| PHE 20247 | COM 30182 | |
| PHE 30225 | COM 20120 | |
| PHE 20245 | COM 20112 | |
| PHE 20247 | COM 20110 | |
| PHE 40209 | MGT 30155 | |
| **TOTAL** | **162** | |

---

### 8.6 Columbia Southern University (27 documents)

| Course Code | Document Count |
|:---|:---:|
| [Course code to be confirmed] | 27 |
| **TOTAL** | **27** |

---

## 9. SEO & Discovery Requirements

| Requirement | Description |
|:---|:---|
| **XML Sitemap** | Auto-generated sitemap containing all 2,195+ document URLs |
| **robots.txt** | Configured to allow full search engine crawling |
| **Meta Tags** | Unique title, description, and keywords per document |
| **Structured Data** | Schema.org markup for educational content |
| **Breadcrumbs** | JSON-LD structured breadcrumb navigation |
| **Mobile Responsive** | Fully functional on all device sizes |
| **Core Web Vitals** | Optimized for Google's ranking metrics |

---

## 10. Future Phases (Post-Launch)

| Phase | Feature |
|:---|:---|
| Phase 2 | Email capture forms integrated with marketing automation (Mailchimp/Klaviyo) |
| Phase 3 | Student accounts to save and track documents |
| Phase 4 | Subscription paywalls for premium library access |
| Phase 5 | Real-time chat support for immediate assistance |

---

## 11. Launch Checklist

- [ ] Database created and populated with all 2,195+ documents
- [ ] API endpoints built and tested
- [ ] Blazor frontend connected to API
- [ ] Content protection implemented across all document pages
- [ ] Mobile responsive design verified on iOS and Android
- [ ] Google Search Console configured
- [ ] XML sitemap generated and submitted
- [ ] Contact@GradeCPR.com email active
- [ ] Phone support line (612) 208-2686 verified
- [ ] Production hosting environment provisioned

---

## 12. Risk Mitigation

| Risk | Mitigation Strategy |
|:---|:---|
| **Accessibility concerns** | Screen readers maintain full access to all content |
| **Legal compliance** | Publishing only assignment prompts (fair use), never completed answers |
| **Support volume** | Auto-response system for common inquiries |
| **Technical bypass** | Standard protections cover 95% of users; advanced bypass is acceptable |
| **SEO impact of copy protection** | Protections are client-side only; search engines receive full indexable content |

---

## 13. Success Metrics

| Metric | Target |
|:---|:---|
| Monthly organic visitors | 10,000+ within 3 months |
| Email inquiries | 50+ per week |
| Bounce rate | Under 40% |
| Average time on page | 2+ minutes |
| Search ranking for target course codes | Top 5 positions |

---

**Document Approved for Development**

*GradeCPR — Supporting academic success with integrity.*
