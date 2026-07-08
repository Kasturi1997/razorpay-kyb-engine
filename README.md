# Razorpay KYB - Merchant Risk Decisioning Engine

> A production-grade simulation of Razorpay's Know Your Business (KYB) merchant onboarding gate. Built to demonstrate rule-based risk scoring, automated document verification, and regulatory compliance decisioning for payment aggregators.

## 🚀 Live Demo

**[👉 View Live Demo](https://yourusername.github.io/razorpay-kyb-engine/)**

*(Replace with your actual GitHub Pages URL after deployment)*

---

## 📋 What This Project Does

Every merchant who wants to accept payments online must go through **KYB (Know Your Business)** before Razorpay activates their account. This project simulates the exact gate they use to decide:

> **"Auto-approve this merchant, send to manual review, or reject?"**

### Strategic Context
- Razorpay onboarded **14 million+ businesses** as of 2026
- They cannot manually review every merchant
- They use **prohibited-business checks** and **category-based risk rules** (crypto, gambling, certain supplements get flagged)
- This engine mirrors their production KYB decisioning logic

---

## 🏗️ Architecture & Features

### Input Layer (Merchant Application)
| Field | Validation | Purpose |
|-------|-----------|---------|
| Business Legal Name | Required | Entity identification |
| Business Type | Pvt Ltd / LLP / Partnership / Proprietorship | Structural risk assessment |
| GSTIN | 15-char format + GSTN registry check | Tax compliance verification |
| PAN | 10-char format + NSDL validation | Director/business identity |
| MCC Category | 14 real merchant category codes | Prohibited/restricted flagging |
| Annual Turnover | ₹0 - ₹5Cr+ buckets | Financial stability scoring |
| Business Age | <1yr to 10+ yrs | Operational maturity |
| Director KYC | Name, PAN, DOB, Nationality, PEP | Sanctions screening |
| Documents | 4 required uploads | OCR extraction & verification |

### Engine Layer (Risk Scoring)
- **Prohibited MCC Detection**: Auto-rejects Gambling (7995), Crypto (6051)
- **Restricted MCC Flags**: Enhanced DD for Supplements (5122), Tobacco (5993), Securities (6211)
- **GSTIN Verification**: Format validation + simulated GSTN registry lookup
- **PAN Validation**: NSDL format checks
- **Sanctions & PEP Screening**: OFAC/UN watchlist + Politically Exposed Person detection
- **Geographic Risk**: High-risk jurisdiction flagging
- **Document Completeness**: OCR pipeline simulation
- **Business Age Penalty**: New entities (<1yr) score higher risk
- **Turnover Bonus**: High turnover (₹5Cr+) reduces risk score

### Output Layer (Decision Dashboard)
- **Animated Risk Gauge**: 0-100 score with color-coded zones
- **Decision Badge**: AUTO-APPROVED / MANUAL REVIEW / REJECTED
- **Risk Bucket**: LOW / MEDIUM / HIGH / CRITICAL
- **Factor Breakdown**: Per-check pass/warn/fail status with point impact
- **Real-time Engine Logs**: Processing pipeline visualization
- **Processing Metrics**: Verification rate, processing time, assessment ID

---

## 🧪 Synthetic Data Generator

Click **"Generate Synthetic Data"** to auto-fill realistic Indian merchant profiles:
- Valid GSTIN format (state code + PAN + entity code + checksum)
- Valid PAN format (5 letters + 4 digits + 1 letter)
- Realistic business names, directors, banks, websites
- Random risk distribution (70% standard, 30% high-risk)
- Auto-uploads all 4 required documents

---

## 🛠️ Tech Stack

- **Frontend**: Pure HTML5, CSS3, Vanilla JavaScript (zero dependencies)
- **Styling**: CSS Grid, Flexbox, CSS animations, backdrop-filter blur
- **No Build Step**: Single-file architecture, deploy anywhere
- **No External APIs**: All verifications simulated client-side

---

## 📦 Deployment

### GitHub Pages (Recommended)
1. Fork or create a new repo
2. Upload `index.html` to the root
3. Go to **Settings → Pages → Deploy from Branch → main**
4. Visit `https://yourusername.github.io/repo-name/`

### Netlify Drop
1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag & drop `index.html`
3. Get instant live URL

### Vercel
1. Go to [vercel.com](https://vercel.com)
2. Create new project → Upload `index.html`
3. Instant deployment with HTTPS

---

## 🎯 Interview Angle

> *"I built a merchant onboarding risk engine that replicates how payment aggregators balance frictionless signup with regulatory compliance — the same tradeoff Razorpay faces when onboarding millions of SMEs. The system uses rule-based scoring with prohibited/restricted MCC checks, automated GSTIN/PAN verification, sanctions screening, and document OCR — scoring merchants into Low/Medium/High/Critical buckets to decide auto-approval, manual review, or rejection."*

**Key Technical Decisions:**
- **Rule-based over ML**: Deterministic rules for regulatory auditability (compliance teams must explain rejections)
- **Tiered Review**: Low-risk auto-approve frees human reviewers for high-risk cases
- **Synthetic Data**: Enables safe demoing without real PII
- **Single-file**: Zero build step, easy to deploy and share

---

## 📄 License

MIT License — Free to use, modify, and deploy.

---

*Built as a portfolio project to demonstrate fintech risk engineering concepts. Not affiliated with Razorpay.*
