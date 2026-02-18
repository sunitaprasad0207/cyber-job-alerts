# 🔐 Daily Cybersecurity Job Alert Automation
### For: Sunita A. Prasad | sunitaprasad0207@gmail.com

Automatically fetches **fresh Cybersecurity / IT Audit / GRC jobs in Bangalore** every morning and sends a beautiful HTML email digest to your Gmail — powered by **GitHub Actions (free)**.

---

## 📧 What You Get Every Morning (8:00 AM IST)

- 🏙️ **Bangalore Full-Time / Hybrid jobs** (IT Auditor, GRC Analyst, ISO 27001, CISA roles)
- 💼 **Freelance / Remote jobs** (Upwork, Remotive, global platforms)
- 💡 **Career tip of the day**
- 🔗 **Quick-apply links** to LinkedIn, Naukri, Glassdoor, Upwork
- 📊 **Daily job count** — only NEW jobs (no duplicates!)

---

## 🚀 SETUP GUIDE (One-Time, ~15 minutes)

### STEP 1 — Create GitHub Repository

1. Go to **https://github.com/new**
2. Name it: `cyber-job-alerts`
3. Set to **Private** (recommended)
4. Click **"Create repository"**

---

### STEP 2 — Upload These Files

Upload ALL files from this folder to your new GitHub repo:
```
cyber-job-alerts/
├── .github/
│   └── workflows/
│       └── daily_job_alert.yml    ← GitHub Actions trigger
├── scripts/
│   └── job_scraper.py             ← Main script
├── seen_jobs.json                 ← Tracks seen jobs (auto-updated)
├── requirements.txt
└── README.md
```

**How to upload:**
- In your GitHub repo, click **"uploading an existing file"**
- Drag and drop all files (maintain folder structure)
- Click **"Commit changes"**

---

### STEP 3 — Set Up Gmail App Password

> ⚠️ You CANNOT use your regular Gmail password. You need a special "App Password".

1. Go to your Google Account: **https://myaccount.google.com**
2. Click **Security** → **2-Step Verification** (enable it if not done)
3. Go back to Security → scroll down → click **"App passwords"**
4. Select app: **"Mail"** → Select device: **"Other"** → type `JobAlertBot`
5. Click **Generate** → Copy the **16-character password** (e.g., `abcd efgh ijkl mnop`)
6. Save it — you'll need it in Step 4!

---

### STEP 4 — Add GitHub Secrets

1. In your GitHub repo → click **Settings** tab
2. Left sidebar → **Secrets and variables** → **Actions**
3. Click **"New repository secret"** and add these 3 secrets:

| Secret Name | Value |
|---|---|
| `GMAIL_USER` | `sunitaprasad0207@gmail.com` |
| `GMAIL_APP_PASSWORD` | The 16-char app password from Step 3 |
| `JSEARCH_API_KEY` | Your RapidAPI key (see Step 5) |

---

### STEP 5 — Get Free JSearch API Key (for LinkedIn/Indeed jobs)

1. Go to **https://rapidapi.com/letscrape-6bRB4HnG79u/api/jsearch**
2. Click **"Subscribe to Test"** → Choose **FREE plan** (200 requests/month)
3. Copy your **RapidAPI Key** from the dashboard
4. Add it as `JSEARCH_API_KEY` secret in GitHub (Step 4)

> 💡 Free tier = 200 calls/month = ~6 calls/day = enough for daily alerts!

---

### STEP 6 — Test It Manually

1. In your GitHub repo → click **Actions** tab
2. Click **"🔐 Daily Cybersecurity Job Alert"** in the left panel
3. Click **"Run workflow"** → **"Run workflow"** button
4. Wait ~60 seconds → check your Gmail inbox!

---

### STEP 7 — It Runs Automatically!

After setup, the workflow runs **every day at 8:00 AM IST** automatically.

You can verify it's running: **Actions tab** → see green ✅ checkmarks daily.

---

## 📋 Job Sources

| Source | Type | Jobs |
|---|---|---|
| JSearch API (LinkedIn/Indeed) | Full-time Bangalore | IT Audit, GRC, CISA, ISO 27001 |
| Remotive API | Remote/Freelance | Cybersecurity, ISO 27001, SOC 2 |
| Arbeitnow API | Remote/Global | Security, Compliance, Risk |

---

## 🔧 Customization

To change search keywords, edit `scripts/job_scraper.py`:

```python
SEARCH_QUERIES = [
    {"keywords": "Cybersecurity Internal Auditor", "location": "Bangalore, India"},
    {"keywords": "IT Internal Auditor",            "location": "Bangalore, India"},
    # Add more queries here...
]
```

To change email time, edit `.github/workflows/daily_job_alert.yml`:
```yaml
- cron: "30 2 * * *"   # 2:30 AM UTC = 8:00 AM IST
# Change to: "0 1 * * *" for 6:30 AM IST
```

---

## ✅ Troubleshooting

| Issue | Fix |
|---|---|
| No email received | Check GitHub Actions logs for errors |
| "Authentication failed" | Regenerate Gmail App Password |
| No jobs found | JSearch API key may be expired — renew on RapidAPI |
| Duplicate jobs | Delete `seen_jobs.json` and recommit |

---

## 🔒 Security Notes

- Your Gmail password is **never stored in code** — only in GitHub Secrets (encrypted)
- The repo can be **private** so no one sees your data
- `seen_jobs.json` only stores hashed job IDs — no personal data

---

*Built for Sunita A. Prasad | Cybersecurity Internal Auditor | Bangalore*
*LinkedIn: linkedin.com/in/suunita-a-prasad-943bb328*
