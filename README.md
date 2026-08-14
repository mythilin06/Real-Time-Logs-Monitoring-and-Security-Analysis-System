# Real-Time Log Monitoring & Security Analytics System

A platform for ingesting **any log or security dataset** (Kaggle downloads, CSV, JSON, Parquet, etc.), storing events in **MongoDB**, and running **Python anomaly detection** for suspicious access patterns.

**Stack:** Node.js · MongoDB · Python (Flask + scikit-learn)

**Default ports (unique — safe alongside other projects):** Dashboard **4110** · Python **5110**

See **[PORTS.md](PORTS.md)** for running multiple projects at once.

---

## Features

- **Insert Dataset** — CSV, TSV, JSON, JSONL, TXT, LOG, XML, XLSX, Parquet, Feather, GZ
- **Flexible schema mapping** — `src_ip`, `event_type`, `@timestamp`, etc.
- **Anomaly detection** — failed logins, IP volume spikes, outliers
- **Multi-dataset** — filter analytics per import

---

## Quick Start

### 1. Prerequisites

- Node.js 18+, Python 3.10+, MongoDB

### 2. Install

```powershell
cd "C:\Users\mythi\OneDrive\Desktop\Log Project"
npm run install:all
```

### 3. Check ports (optional)

```powershell
npm run ports
```

### 4. Run (two terminals)

**Terminal 1 — Python:**
```powershell
python python-service/app.py
```

**Terminal 2 — Node:**
```powershell
cd backend
npm run dev
```

### 5. Open

**http://localhost:4110** (or whatever `PORT` is in `.env`)

Upload `sample-data/kaggle-style-security-logs.csv` via **Insert Dataset**.

---

## Multiple projects at once

| Project | PORT | PYTHON_PORT |
|---------|------|-------------|
| **This (log monitoring)** | 4110 | 5110 |
| Fraud / other app | 5000 | 5100 |

Each project needs its own `.env` values. Never reuse the same `PORT` or `PYTHON_PORT` twice.

---

## Kaggle datasets

Search: `security logs`, `authentication logs`, `CICIDS`, `firewall logs`, `honeypot logs`.

Avoid pure **credit-card transaction** datasets (those are for fraud apps, not log monitoring).
