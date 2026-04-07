# TAM AI Ad Automation — Complete Setup Guide
### For Community Members | The Agency Mentor

---

> **Before you start:** This guide walks you through setting up two Manus skills that will automate your Meta ad creation from end to end. Read through the whole guide first so you understand what you are building, then follow each step in order. Nothing here requires coding knowledge.

---

## What You Are Building

By the end of this guide, you will have two skills installed in your Manus account:

| Skill | What It Does |
|---|---|
| **Meta Ad Caption Skill** | Learns your unique voice and writes ad captions that sound exactly like you |
| **Meta Ad Creation Skill** | Downloads creatives from Google Drive, writes captions using Skill 1, and publishes ads to Meta — automatically |

Once both are set up, creating a new batch of Meta ads takes less than 2 minutes. You paste a Google Drive folder link into Manus, tell it which campaign to use, and it handles everything else.

---

## What You Need Before You Start

- A **paid Manus subscription** (Pro plan or above). The free tier does not support skill files or background Python execution. Visit [manus.im](https://manus.im) to check your plan.
- Access to your **Meta Business Manager** and **Ads Manager**
- Access to **Google Drive** (the account where your video editor uploads creatives)
- A **Google account** to create a free Cloud project
- Approximately **2 hours** for the full setup

---

## How to Use a Wizard File

Both skills are set up using a "wizard" — a special instruction file that you upload to Manus. Here is how it works every time:

1. Download the wizard file (`.md` file)
2. Open [manus.im](https://manus.im) in your browser
3. Click **New Task** (the pencil or compose icon)
4. Attach the wizard file by clicking the paperclip icon or dragging it into the chat
5. Type exactly: **Run this skill**
6. Press Enter and follow Manus's instructions step by step

> **Important:** Each wizard must be run in its own separate Manus task. Do not mix Part 1 and Part 2 in the same conversation.

---

---

# PART 1: META AD CAPTION SKILL

**Download:** `TAMCommunity-MetaAdCaptionSkillWizard.md`

**Time:** 5–10 minutes

**What this does:** Creates a skill that learns your ad writing style. Every time you create ads in the future, Manus will read this skill first so the captions sound like you — not like a generic AI.

---

## Step 1: Gather Your Top Performing Ad Captions

This is the only thing you need to do in Part 1. Manus handles everything else automatically once you provide your captions.

**What to do:**

1. Open your **Meta Ads Manager** at [adsmanager.facebook.com](https://adsmanager.facebook.com)
2. Go to the **Ads** level (not Campaigns or Ad Sets)
3. Sort by your best performance metric — usually **Cost Per Lead (CPL)** ascending, or **Leads** descending
4. Open your top 3 best-performing ads and copy the **Primary Text** from each one (this is the main caption that appears above the creative)
5. If you have more than 3 ads that have performed well, include all of them — the more context you give Manus, the better it will replicate your voice

**When Manus asks for your captions**, paste all of them into the chat in a single message. You can separate them with a line like `--- Ad 2 ---` between each one.

> **Why this matters:** Manus uses your real captions as a reference to understand your tone, offer, sentence structure, and call to action. It will never copy them word for word — it uses them as a style guide to write new captions that feel authentic to your brand.

**What happens next:** Manus creates two files in your account:
- `/home/ubuntu/skills/meta-ad-scripter/SKILL.md` — the skill instructions
- `/home/ubuntu/skills/meta-ad-scripter/references/ad_script_examples.md` — your captions stored as reference

You will see a confirmation message when the skill is live. Once confirmed, move on to Part 2.

---

---

# PART 2: META AD CREATION SKILL

**Download:** `TAMCommunity-AIAdAutomationSetupWizard.md`

**Time:** 60–90 minutes

**What this does:** Creates the skill that actually builds your ads. It connects to your Meta account and Google Drive, then automates the entire ad creation process.

> **Important:** Complete Part 1 before starting Part 2. The ad creation skill relies on the caption skill existing in your account.

---

## Step 1: Create a Meta Business App

**Why:** Without a Meta Business App, Manus has no official way to communicate with Meta's API. This registers your automation tool with Meta so it has permission to create ads on your behalf.

1. Go to [developers.facebook.com](https://developers.facebook.com) and log in with your Facebook account
2. Click **My Apps** in the top right corner
3. Click **Create App**
4. Fill in the details:
   - **App name:** `TAM Ad Automation`
   - **App contact email:** your email address
   - Click **Next**
5. On the **Use cases** screen, tick:
   - *"Create & manage ads with Marketing API"*
   - *"Create & manage app ads with Meta Ads Manager"*
   - Click **Next**
6. On the **Business** screen, select your Business Portfolio from the dropdown. Click **Next**
7. On the **Requirements** screen, it should say "No requirements identified". Click **Next**
8. On the **Overview** screen, review and click **Create app**

> **Can't create an app?** If Meta shows an error or blocks you, your Business Manager account is likely not verified. Go to **Business Settings → Security Centre** and click **Start Verification** under Business Verification. Complete the verification process (usually requires uploading a business document), then return here and try again.

---

## Step 2: Create a System User and Generate a Token

**Why:** A System User token is permanent and never expires. If you used a personal access token instead, it would expire every 60 days and break your automation. This is the most important step in the entire Meta setup.

**Create the System User:**

1. Go to [business.facebook.com](https://business.facebook.com)
2. Click the **⚙️ gear icon** (Business Settings) in the left sidebar
3. In the left menu under **Users**, click **System Users**
4. Click **Add**
5. Name it: `Manus Automation`
6. Set the role to **Admin**
7. Click **Create System User**

> **Naming issue?** If Meta rejects the name `Manus Automation`, try `TAM API User` or `AI Ad Bot`. The name has no effect on how the skill works — it is just a label.

**Add Assets to the System User:**

8. Click **Add Assets**
9. Select **Apps** from the asset type list
10. Find `TAM Ad Automation` in the list and tick it
11. Set permissions to **Full control**
12. Click **Save changes**
13. Click **Add Assets** again
14. Select **Ad Accounts** from the asset type list
15. Find your ad account and tick it
16. Set permissions to **Manage campaigns**
17. Click **Save changes**

**Generate the Token:**

18. Click **Generate New Token**
19. Select `TAM Ad Automation` from the app dropdown
20. Tick these three permissions:
    - `ads_management`
    - `ads_read`
    - `business_management`
21. Click **Generate Token**
22. **Copy the token immediately** — you will not be able to see it again after you close this window

Your token will look like this (it is much longer than a personal token):

```
EAAMp1fsRFhUBQZCWuMKjc2ujwsUnyqMbh2vnqsTX59U9smuUFTAQr8pmXsYwONq94WR5xIb...
```

> **Critical order:** You MUST add your app and ad account to the System User's assets BEFORE generating the token. If you generate the token first, it will not have the correct permissions and ad creation will fail.

---

## Step 3: Meta Ad Account ID

**Why:** This tells Manus exactly which ad account to publish ads into.

1. In Business Settings, click **Ad Accounts** in the left menu
2. Click on your ad account name
3. Your Ad Account ID is the number shown at the top of the right panel

When pasting into Manus, format it with `act_` at the front:

```
act_1234567890
```

---

## Step 4: Facebook Page ID and Instagram Actor ID

**Why:** Without these, Meta does not know which Facebook Page and Instagram account to attach to the ad. Your ads would fail to publish or show the wrong identity.

**Facebook Page ID:**
1. Business Settings → **Pages** in the left menu
2. Click your Facebook Page
3. The Page ID is shown in the right panel or in the URL

**Instagram Actor ID:**
1. Business Settings → **Instagram Accounts** in the left menu
2. Click your Instagram account
3. The ID is shown in the right panel or in the URL

Paste both into Manus when prompted:

```
Page ID: 106953661965167
Instagram ID: 17841452606507069
```

---

## Step 5: Testing and Performance Campaign IDs

**Why:** Manus does not create new campaigns — it adds new ads into your existing Testing and Performance campaigns. These IDs tell it exactly where to place them.

1. Open [Ads Manager](https://adsmanager.facebook.com)
2. Click on your **Testing** campaign to open it
3. Look at the browser URL — find `selected_campaign_ids=` and copy the number after it
4. Go back and repeat for your **Performance** campaign

```
Testing Campaign: 120231741510640018
Performance Campaign: 120234450912130018
```

---

## Step 6: Default Landing Page URL

**Why:** Every ad needs a destination URL. Setting a default here means you do not have to type it every time you run the skill.

Paste your full booking or landing page URL into Manus when prompted:

```
https://yourwebsite.com/booking
```

> **Tip:** You can always override this when running the skill. Just include "use this landing page: [URL]" in your task message.

---

## Step 7: Create a Google Cloud Project

**Why:** Your video editor uploads ad creatives to Google Drive. For Manus to download those files automatically, it needs a secure, registered credential with Google. Creating a Cloud Project is the first step in getting that credential.

1. Go to [console.cloud.google.com](https://console.cloud.google.com) and log in with your Google account

2. **If you see a "Select a project" screen** (first time user):
   - Click the **Create project** button in the top right of the main content area

3. **If you see a "Welcome" dashboard** (you already have a project loaded from a previous visit):
   - Click the project name button in the top navigation bar (it shows your current project name)
   - A popup appears — click **New Project** in the top right of that popup

4. Fill in the project details:
   - **Project name:** `TAM Manus Bot`
   - **Organisation:** Leave exactly as it is (it will show your domain)
   - **Project ID:** Auto-generated — do not change it
   - Click **Create**

5. Wait for the project to be created. You will land on the Welcome dashboard showing `TAM Manus Bot` in the top navigation bar — this confirms you are in the right project.

---

## Step 8: Enable the Google Drive API, Configure OAuth, and Create Your Client ID

This step has three parts. Do them in order — each one is required before the next.

**Why this whole step matters:** These three parts give Manus the specific, scoped permission to read your Google Drive — nothing else. The Client ID and Client Secret are the keys Manus will use every time it downloads your creatives.

---

### Part A: Enable the Google Drive API

1. On the Welcome dashboard, look for the **Quick access** section. Click the **APIs and services** tile.
   - If you do not see it, click the **≡ hamburger menu** (three horizontal lines) in the top left → hover over **APIs & Services** → click **Library**
2. At the top of the page, click **+ ENABLE APIS AND SERVICES**
3. In the search bar, type `Google Drive API` and press Enter
4. Click the **Google Drive API** result
5. Click the blue **Enable** button

---

### Part B: Configure the OAuth Consent Screen

This is a required step that Google forces before you can create a Client ID. It registers your app with Google so it can request permission from users.

1. In the left sidebar, click **Credentials**
2. You will see a yellow warning banner at the top: *"Remember to configure the OAuth consent screen with information about your application."* Click the **Configure consent screen** button on the right side of that banner
3. You are now in the **Project configuration** wizard. It has 4 steps: App Information → Audience → Contact Information → Finish
4. Under **App Information**:
   - **App name:** `TAM Ad Automation`
   - **User support email:** Select your email from the dropdown
   - Click **Next**
5. On **Audience**: Click **Next**
6. On **Contact Information**: Enter your email address. Click **Next**
7. On **Finish**: Click **Create**
8. You will land on the **OAuth overview** page. A small toast notification at the bottom of the screen will say *"OAuth configuration created."* — this confirms it worked.

---

### Part C: Create the OAuth Client ID

1. On the OAuth overview page, click the **Create OAuth client** button
2. For **Application type**, select **Desktop app** from the dropdown
3. For the name, type: `Manus Desktop Client`
4. Click **Create**

---

> ### 🚨 CRITICAL: DO NOT CLOSE THE POPUP THAT APPEARS
>
> A popup window will appear showing your **Client ID** and **Client Secret**. These are the two most important values in the entire Google setup. **Before you do anything else:**
>
> 1. Open a Notes app (Apple Notes, Notepad, Google Docs — anything)
> 2. Copy the **Client ID** and paste it into your notes
> 3. Copy the **Client Secret** and paste it into your notes
> 4. Label them clearly so you know which is which
>
> **Only then** close the popup and return to Manus.
>
> **If you already closed the popup:** Do not panic. Go to **APIs & Services → Credentials**, find `Manus Desktop Client` in the **OAuth 2.0 Client IDs** section, and click the **pencil (edit) icon** on the right. Your Client ID and Client Secret will be displayed on the right side of the page.

Your **Client ID** ends in `.apps.googleusercontent.com`:

```
632460847530-[YOUR_CLIENT_ID].apps.googleusercontent.com
```

Your **Client Secret** starts with `GOCSPX-`:

```
GOCSPX-[YOUR_CLIENT_SECRET]
```

---

## Step 9: Paste Your Client ID and Client Secret into Manus

After the Google setup, Manus will ask for your Client ID first, then your Client Secret in a follow-up message. Paste each one from your notes when prompted.

Manus will validate each value. If it detects a placeholder or incorrect format, it will ask you to check and re-enter. This is normal — just follow its instructions.

---

## Step 10: Authorise Google Drive Access

**Why:** This is the final connection step. After you click Allow, Google gives Manus a permanent Refresh Token — meaning it can access your Drive any time in the future without you logging in again.

1. Manus will generate a personalised authorisation link in the chat. Click it.
2. A Google login/permission screen will open in your browser. Sign in with the **Google account that holds your ad creatives in Drive** (this may be different from the account you used to create the Cloud project).
3. You will see a screen saying something like: *"TAM Ad Automation wants to access your Google Account — View and download all your Google Drive files"*. Click **Allow**.
4. Google will display a one-time code on the screen. **Copy it immediately.**
5. Paste the code back into the Manus chat.

> **⏱️ This code expires in minutes.** Do not switch apps, leave the page, or delay. Copy the code and paste it into Manus immediately after it appears.

The code will look like this:

```
4/0AeaYSHD8jX9kL_mN2pQ5vR3wT7yU1bC4xZ6vM9nK2lJ5hG8fD1sA4qW7eR0tY3uI6oP
```

---

## 🎉 Step 11: Skill Build — The Finale

Once you paste the authorisation code, Manus silently builds your `create-meta-ads` skill. It writes all your credentials into a Python script and creates the skill files in your Manus account. You will see a confirmation message when it is done.

**Your setup is complete.** Both skills are now live in your Manus account and will appear when you click the **+ skills icon** in any new Manus task.

---

---

# HOW TO USE YOUR SKILLS

## Running the Ad Creation Skill

Start a brand new Manus task and type:

```
Create new Meta ads from this Google Drive folder: [paste your Drive link]. Use the Testing campaign.
```

Manus will:
1. Read your `meta-ad-scripter` skill to understand your voice
2. Download every video and image file from the Drive folder
3. Upload each file to your Meta Media Library
4. Write a unique ad caption for each creative in your style
5. Create a PAUSED ad for each file in your Testing campaign
6. Return a summary table of all ads created

The ads are created as **PAUSED** — they will not go live until you review and activate them in Ads Manager.

## Updating Your Ad Captions Skill

If your offers change, you launch a new product, or you find new captions that perform well, you can update your caption skill at any time. Simply open a new Manus task, attach the `TAMCommunity-MetaAdCaptionSkillWizard.md` file again, and type **"Run this skill"**. Manus will ask for your new captions and update the skill.

## Ad Naming Format

Your ads will be named using this format:

```
#[Number]__[Filename]__[Type]__[Date]
```

For example:

```
#7__TAM-Hook-v3__VIDEO__07-Apr-26
```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| Meta blocks app creation | Verify your Business Manager account (Business Settings → Security Centre → Start Verification) |
| System User name rejected | Try `TAM API User` or `AI Ad Bot` — the name does not affect functionality |
| Token exchange error | You likely pasted a demo or incorrect value. Check that your Client ID ends in `.apps.googleusercontent.com` and your Client Secret starts with `GOCSPX-` |
| Auth code expired | Re-run the authorisation step — Manus will generate a new link |
| Ads not appearing in Ads Manager | Check that your System User has the ad account added as an asset with Manage campaigns permission |
| Skill not appearing in Manus | The skill files may not have been written correctly. Re-run the wizard from Step 1 in a new task |

---

*The Agency Mentor — AI Systems | [theagencymentor.com.au](https://theagencymentor.com.au)*
