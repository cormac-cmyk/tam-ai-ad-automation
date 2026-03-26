---
name: create-meta-ads-community-setup
description: Community setup guide for building the TAM AI Ad Automation system. Use this skill when a community member wants to set up their own version of the Create Meta Ads automation workflow. Walks through account setup, credential collection, skill installation, and first test run step by step.
---

# TAM Community — AI Ad Automation Setup Guide

This skill walks you through setting up your own automated Meta Ads creation system from scratch. By the end, you will be able to give Manus a Google Drive folder link and have it automatically create fully-named, copy-written, PAUSED ads inside your Meta campaigns.

---

## What You Are Building

You are building a system where:
1. You drop creative assets (videos or images) into a Google Drive folder
2. You tell Manus which campaign to use and what the destination URL is
3. Manus downloads every file, uploads them to Meta, writes ad copy, and creates one PAUSED ad per asset
4. You choose whether to activate the ads

---

## Tech Stack Required

Before starting, confirm you have access to all of the following:

| Tool | Purpose | Link |
|---|---|---|
| **Manus AI** | The AI agent that runs your skills | manus.im |
| **Google Drive** | Where you store creative assets | drive.google.com |
| **Google Cloud Console** | Where you create your OAuth app | console.cloud.google.com |
| **Meta Business Manager** | Where your ad account and campaigns live | business.facebook.com |
| **Meta Developers** | Where you create your app and system user token | developers.facebook.com |

---

## Day 1 — Account Setup

Work through each of these steps. Do not proceed to Day 2 until all required steps are complete.

### Step 1.1 — Google Cloud Setup
1. Go to **console.cloud.google.com**
2. Create a new project (e.g. `Manus-Ads-Bot`)
3. Navigate to **APIs & Services → Library**
4. Search for **Google Drive API** and click **Enable**
5. Go to **APIs & Services → Credentials → Create Credentials → OAuth Client ID**
6. Select **Desktop App** as the application type
7. Save your **Client ID** and **Client Secret** securely — you will need these in Day 2

> **Important:** Google no longer shows Client Secrets after creation. If yours is hidden, click **+ Add Secret** to generate a new one. It is only shown once — copy it immediately.

### Step 1.2 — Meta Developer Setup
1. Go to **developers.facebook.com → My Apps → Create App**
2. Choose **Business** as the app type
3. Connect the app to your Business Manager
4. Add the **Marketing API** product to the app
5. Go to **Business Manager → Business Settings → Users → System Users → Add**
6. Give the system user **Admin** role
7. Click **Generate Token**, select your app, and enable these permissions:
   - `ads_management`
   - `ads_read`
   - `business_management`
8. Copy the token immediately — it is not shown again

### Step 1.3 — Gather Your IDs
Collect the following before Day 2:
- **Ad Account ID** — found in Business Settings → Ad Accounts (format: `act_XXXXXXXXXX`)
- **Campaign IDs** — click into each campaign in Ads Manager; the ID is in the URL
- You need IDs for: Testing campaign, Performance campaign, Workshop campaign

---

## Day 2 — Credential Setup with Manus

### Step 2.1 — Start a Manus session
Open a new task in Manus and say:

> "I want to build a Create Meta Ads skill. Help me set it up. I have my Google Client ID, Client Secret, Meta System User token, and Campaign IDs ready."

### Step 2.2 — Google OAuth Flow
Manus will:
1. Ask for your **Client ID** and **Client Secret**
2. Generate a one-time authorisation URL
3. Ask you to visit it in your browser and approve Google Drive access
4. Ask you to paste back the authorisation code
5. Exchange it for a **refresh token** and store it permanently

You only do this once. After this, Manus can access Google Drive without any login.

### Step 2.3 — Meta Token Setup
Provide Manus with:
- Your **Meta System User token**
- Your **Ad Account ID** (format: `act_XXXXXXXXXX`)
- Your **Campaign IDs** for Testing, Performance, and Workshop

Manus will automatically pull your **Page ID** and **Instagram Actor ID** from your existing ads — you do not need to find these manually.

### Step 2.4 — Verification
Manus will run a verification script to confirm it can:
- List files in a Google Drive folder
- See your Meta campaigns and ad sets

If either fails, Manus will tell you exactly what is wrong and how to fix it.

---

## Day 3 — Build and Test

### Step 3.1 — Install the Skills
Make sure both of these skills are installed in Manus:
1. **meta-ad-scripter** — generates ad copy (headlines and primary text)
2. **create-meta-ads** — the main automation skill (this is what Manus builds for you in Day 2)

### Step 3.2 — First Test Run
Prepare a Google Drive folder with 1–2 test assets (video or image). Then say to Manus:

> "Create new Meta ads for the Testing campaign. Here is the Google Drive folder: [your link]. The destination URL is [your landing page URL]."

Manus will:
1. Download all files from the folder
2. Generate a headline and primary text for each ad using the Ad Scripter skill
3. Upload each file to the Meta Media Library (using chunked upload for large videos)
4. Create one PAUSED ad per asset with the naming format:
   `#N__UID__Direct Response__Single__Direct to Camera__VIDEO or STATIC__DD-MON-YY`
5. Show you a summary table of all created ads
6. Ask if you want to activate them

### Step 3.3 — Verify in Meta Ads Manager
Go to your Testing campaign in Meta Ads Manager. Confirm:
- The ad appears with the correct naming convention
- The creative (video or image) is attached
- The ad copy (headline and primary text) is present
- The destination URL is correct
- The ad status is **PAUSED**

### Step 3.4 — Full Production Run
Once your test passes, run it with a full folder of assets. The system scales to any number of files — 7 videos creates 7 ads, each with unique copy, all in one command.

---

## Ad Naming Convention Reference

Every ad created by this system follows this format:

```
#[N]__[UID]__Direct Response__Single__Direct to Camera__[TYPE]__[DATE]
```

| Part | Meaning |
|---|---|
| `#N` | Auto-incrementing number from the highest existing ad in the ad set |
| `UID` | The filename from Google Drive (without extension) |
| `Direct Response` | The offer type — always Direct Response |
| `Single` | The ad format — always Single |
| `Direct to Camera` | The creative style |
| `VIDEO` or `STATIC` | Detected automatically from the file type |
| `DATE` | The date the ad was created (e.g. `26-MAR-26`) |

---

## Troubleshooting

**Google Drive download fails:**
Check that your OAuth app has the Google Drive API enabled and that the folder is shared with your Google account.

**Meta upload fails with size error:**
The script uses chunked upload (10 MB per chunk) which handles files of any size. If it still fails, check that your system user token has not expired.

**Wrong page or Instagram ID:**
Manus pulls these automatically from your existing ads. If it gets the wrong ones, ask Manus to re-fetch them by looking at a specific ad you know is correct.

**Ad copy sounds generic:**
The Meta Ad Scripter skill uses a Google Doc of top-performing examples. Ask Manus to update the scripter skill with more examples from your best-performing ads.

---

## What's Next

Once this system is running, you can extend it by:
- Building a **Meta Ad Scripter** skill customised for your specific offer and audience
- Creating a **Workshop Campaign** version with different copy angles
- Adding a **Slack or email notification** when new ads are created
- Scheduling weekly ad launches from a recurring Google Drive folder
