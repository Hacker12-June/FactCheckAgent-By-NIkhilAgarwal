# 🔍 FactCheck Agent

An automated, client-side, AI-driven **Truth Layer for PDF Verification** developed by Nikhil Agarwal. This tool extracts statistical, financial, and numerical claims directly from standard PDF documents and live-verifies them against the web to combat misinformation and validate datasets.

![JavaScript](https://img.shields.io/badge/Language-JavaScript%20%2F%20HTML5%20%2F%20CSS3-yellow?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![API](https://img.shields.io/badge/Live%20Search-DuckDuckGo%20HTML-blue?style=for-the-badge)

---

## 🌟 Key Features

- **Local PDF Parsing**: Extracts text securely on the client side using `PDF.js` without uploading records to any external cloud storage.
- **Statistical Claim Extraction**: Employs advanced Regular Expression (RegEx) matching patterns to extract:
  - Percentages (`%`, `percent`)
  - Currency figures (`$`, `€`, `£` in millions, billions, etc.)
  - Growth or decline trends (`increased`, `plunged`, `surged by`)
  - Dated statistics and year-bound historical figures
  - Market valuations and corporate financial statistics
- **Live Web Verification**: Connects dynamically with DuckDuckGo's live HTML search framework to gather current cross-reference resources (no proprietary API keys required).
- **Automated Accuracy Verdicts**: Uses weighted heuristics to crosscheck statistical metrics against live snippets, categorizing assertions into four clear verification tiers:
  - ✅ **Verified** (Within an expected numeric tolerance threshold)
  - 🟧 **Inaccurate** (Values differ from live cross-references)
  - ❌ **False** (Direct contradiction or heavily disproven values)
  - ⬜ **Unverified** (Insufficient online citations found to confirm)
- **Deep Insight Diagnostics**: Computes confidence ratings and highlights mismatched values while surfacing links directly to web sources.

---

## 🛠️ Configuration Architecture

The verification mechanics run on a modular ruleset defined in the global `CONFIG` state:

| Parameter | Default Value | Description |
| :--- | :--- | :--- |
| `maxClaimsToVerify` | `20` | Maximum number of statements checked per document. |
| `searchDelayMs` | `800` | Rate-limiting safety interval to prevent web search throttling. |
| `numericalTolerance` | `0.18` | Defines the acceptable threshold variance ($\pm18\%$) for a "Verified" state. |
| `outdatedYearThreshold`| `2023` | Statements quoting years prior to this threshold get flagged for outdated validation. |

---

## 🚀 Quick Start / Installation

Because this application runs entirely inside an architectural sandbox on the browser client, it has zero hard backend operational system requirements. 

### Option 1: Standalone Browser Launch
1. Clone this repository locally:
   ```bash
   git clone [https://github.com/your-username/FactCheck-Agent.git](https://github.com/your-username/FactCheck-Agent.git)
