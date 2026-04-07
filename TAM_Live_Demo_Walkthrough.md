# TAM Live Demo Walkthrough: AI Ad Automation Setup

This document contains a complete, step-by-step script for demonstrating the `create-meta-ads-community-setup` skill live on a workshop or community call. 

It includes **fictitious but realistic credentials** that you can copy and paste into Manus during the demo to show exactly how the workflow operates without exposing your real tokens.

*(Note: I have verified your real credentials in your existing `create-meta-ads` skill. Your setup is fully complete and working. This document is purely for demonstration purposes.)*

---

## How to run this demo
1. Start a new Manus chat.
2. Upload the `TAMCommunity-AIAdAutomationSetupWizard.md` file (downloaded from the landing page).
3. Say: *"Run this skill"*
4. Follow the script below, copying and pasting the fake credentials when prompted.

---

### Step 1: Meta Developer App
**Manus will say:** "Welcome to the TAM AI Ad Automation setup! First, we need to create a Meta Business App. This acts as the secure bridge between Manus and your Meta Ads account.

Please follow these exact steps (refer to Step 1 on the landing page):
1. Go to developers.facebook.com and log in.
2. Click My Apps in the top right, then click Create App.
3. **App details screen:** Give your app a name (e.g. 'TAM Ad Automation') and enter your contact email. Click Next.
4. **Use cases screen:** Tick the top two options — 'Create & manage ads with Marketing API' AND 'Create & manage app ads with Meta Ads Manager'. Click Next.
5. **Business screen:** Select your Business Portfolio from the list (e.g. your agency name). Click Next.
6. **Requirements screen:** It should say 'No requirements identified'. Click Next.
7. **Overview screen:** Review the summary — you should see your app name, both use cases, and your business. Click Create app.

Once you have created the app, you will land on the App Dashboard. You don't need to paste anything here yet — just reply 'Done' when you have finished this step!"

**What you say on the call:** *"Alright guys, so Manus is walking us through the exact screens inside Meta Developers. Notice it tells you to tick BOTH the top two use cases — 'Create & manage ads with Marketing API' AND 'Create & manage app ads with Meta Ads Manager'. That's the step most people miss. I've already done this, so I'm going to tell it I'm done."*

**What you type into Manus:**
> Done

---

### Step 2: System User Token
**Manus will say:** "Great job! ✅ Now we need to create a System User and generate your permanent access token.

Please follow these steps (refer to Step 2 on the landing page):
1. Go to business.facebook.com → Settings → System Users.
2. Click Add, name it 'Manus Automation', set role to Admin, click Create System User.
3. Click Add Assets → select Apps → find 'TAM Ad Automation' → tick Full control → Save changes. ⚠️ This is the step most people miss.
4. Click Add Assets again → select Ad Accounts → find your ad account → tick Manage campaigns → Save changes.
5. Click Generate New Token → select 'TAM Ad Automation' → tick ads_management, ads_read, business_management → Generate Token.

Copy that token and paste it here."

**What you say on the call:** *"This is the step that trips everyone up. After you create the System User, you have to add your app to its assets FIRST — before you generate the token. If you skip that, the token won't have permission to create ads. Watch me do this now..."*

**What you type into Manus (Copy this fake token):**
> EAAMp1fsRFhUBQZCWuMKjc2ujwsUnyqMbh2vnqsTX59U9smuUFTAQr8pmXsYwONq94WR5xIbDPZAyobHdOjgFEz7iuvFcC7kyXIlbtRNUtqC1LbuHScTk4fFZAuNFdyoWC1EZBv1ZAMTRF7pSc8MWuWoMtjIeuYBAeSU0iPGjDRcBvpkLHNodFiuQZBaot5OWNxOAZDZD

---

### Step 3: Ad Account ID
**Manus will say:** "Token saved securely! Next, I need your Meta Ad Account ID... Please paste your Ad Account ID here (make sure to add `act_` at the front)."

**What you say on the call:** *"It saved the token. Now it needs to know exactly which ad account to put the ads into. I'll grab my Ad Account ID from Business Settings."*

**What you type into Manus (Copy this fake ID):**
> act_4932300966838426

---

### Step 4: Page & Instagram IDs
**Manus will say:** "Ad Account ID saved. Now I need two IDs: your Facebook Page ID and your Instagram Actor ID..."

**What you say on the call:** *"Next, it needs my Facebook Page and Instagram IDs so the ads actually look like they're coming from my agency."*

**What you type into Manus (Copy these fake IDs):**
> Page ID: 106953661965167
> Instagram ID: 17841452606507069

---

### Step 6: Campaign IDs
**Manus will say:** "Page and IG IDs saved. Next, I need the IDs for the specific campaigns where you want me to put the ads. Specifically, I need your Testing Campaign ID and your Performance Campaign ID..."

**What you say on the call:** *"This is the cool part. Manus doesn't create messy new campaigns — it puts the ads directly into my existing Testing and Performance campaigns. I'll give it those IDs now."*

**What you type into Manus (Copy these fake IDs):**
> Testing Campaign: 120231741510640018
> Performance Campaign: 120231741510640019

---


### Step 7: Default Landing Page URL
**Manus:** "Campaign IDs saved. ✅ Next, I need the default landing page URL where you want to send traffic from these ads."

**You:**
1. Copy your landing page URL (e.g., `https://theagencymentor.com.au/agency-audit-and-growth-call`).
2. Paste it into the chat.

### Step 8: Google Cloud Project
**Manus will say:** "Campaign IDs saved! We are done with the Meta side. Now we need to connect Google Drive so I can download your ad creatives.

This is why we need Google: your video editor saves files to a Google Drive folder. Instead of you manually downloading and uploading each file to Meta, Manus does it automatically. To make that work, we need to give Manus a secure key to access your Drive.

Let's start by creating a Google Cloud Project (refer to Step 8 on the landing page):
1. Go to console.cloud.google.com and log in with the Google account that owns your Drive.
2. How to create a new project depends on what you see:
   - If you see a "Select a project" screen: Click the 'Create project' button in the top right.
   - If you see a "Welcome" dashboard: Click the project name in the top blue bar, then click 'New Project' in the popup.
3. Name it 'TAM Manus Bot'. Leave the Organisation field exactly as it is.
4. Click Create.
5. Wait a few seconds, then confirm you are on the Welcome dashboard for 'TAM-Manus Bot'.

Reply 'Done' when your project is created."

**What you say on the call:** *"Okay so Meta is fully done. Now we're setting up the Google side. The reason we need this is simple — your video editor uploads files to Google Drive, and Manus needs a secure way to access that folder. Google requires you to create a 'project' first — think of it like registering your automation with Google. I've already done this, so I'll say done."*

**What you type into Manus:**
> Done

---

### Step 7: Enable Drive API, OAuth Consent Screen & Create Client ID
**Manus will say:** "Project created! Now we need to do three things inside Google Cloud:

**Part A — Enable the Drive API** (refer to Step 8 on the landing page):
1. On your project's Welcome dashboard, click the 'APIs and services' tile.
2. Click '+ ENABLE APIS AND SERVICES' at the top.
3. Search for 'Google Drive API', click it, then click Enable.

**Part B — Configure OAuth Consent Screen** (refer to Step 8 on the landing page):
1. In the left sidebar, click 'Credentials'.
2. Click the 'Configure consent screen' button inside the yellow warning banner.
3. In the 4-step wizard: App name is 'TAM Ad Automation', select your email. Click Next through all steps, then click Create at the end.

**Part C — Create OAuth Client ID**:
1. You will land on the OAuth overview page. Click 'Create OAuth client'.
2. Application type: Desktop app. Name: 'Manus Desktop Client'. Click Create.
3. 🚨 A popup will appear — DO NOT CLOSE IT. Copy both the Client ID and Client Secret into a Notes app right now.

Paste your Client ID here when ready."

**What you say on the call:** *"This is the most detailed part of the Google setup. Three things happen here — we turn on Drive access, we configure the consent screen (which is basically telling Google what this app is called), and then we create the actual credential. The popup at the end is critical — I tell my community to copy both values into a Notes app immediately before closing it. I've already done all of this, so here's my Client ID."*

**What you type into Manus (Copy this fake Client ID):**
> 632460847530-DEMO-bvjv0jtd2kek110dtjdasajdr2lr38gi.apps.googleusercontent.com

*(This is a fictitious Client ID for demo purposes only — not a real credential.)*

---

### Step 9: Google Client Secret & OAuth Flow
**Manus will say:** "Client ID saved. Now paste your Google Client Secret (this is the second value from that popup)."

**What you say on the call:** *"And the Client Secret — this is the second value from that popup. If anyone missed it, I remind them to click the pencil icon next to 'Manus Desktop Client' on the Credentials page to get it back."*

**What you type into Manus (Copy this fake Secret):**
> GOCSPX-DEMO-oZPq-pOizYpdet6o8zXnfgEPRV-N

*(This is a fictitious Client Secret for demo purposes only — not a real credential.)*

---

### Step 9: Google OAuth Authorisation
**Manus will say:** "Client Secret saved. Final step! I am generating a special authorisation link for you. Click it, log in with your Google account, and paste the code you receive back here."

**What you say on the call:** *"This is the final step. Manus generates a custom one-time login link. I click it, Google asks me to confirm I want to give this app access to my Drive, and then it gives me a code. I paste that code back here and we're done."*

**What you type into Manus (Copy this fake Auth Code):**
> 4/0AeaYSHD8jX9kL_mN2pQ5vR3wT7yU1bC4xZ6vM9nK2lJ5hG8fD1sA4qW7eR0tY3uI6oP

---

### The Finale
**Manus will say:** "Google Drive is connected! You have provided all the necessary credentials. I am now going to build your personalised `create-meta-ads` skill in the background..."

**What you say on the call:** *"And that's it! Manus takes all those credentials, writes the Python code in the background, and builds my custom automation skill. I never had to touch a single line of code."*
