# TAM Live Demo Walkthrough: AI Ad Automation Setup

This document contains a complete, step-by-step script for demonstrating the `create-meta-ads-community-setup` skill live on a workshop or community call. 

It includes **fictitious but realistic credentials** that you can copy and paste into Manus during the demo to show exactly how the workflow operates without exposing your real tokens.

*(Note: I have verified your real credentials in your existing `create-meta-ads` skill. Your setup is fully complete and working. This document is purely for demonstration purposes.)*

---

## How to run this demo
This setup is a two-part process. You will run two separate skills in order.

### Part 1: The Meta Ad Caption Skill
1. Start a new Manus chat.
2. Upload the `TAMCommunity-MetaAdCaptionSkillWizard.md` file.
3. Say: *"Run this skill"*
4. Follow the script below for Part 1.

### Part 2: The Meta Ad Creation Skill
1. In the same chat (or a new one), upload the `TAMCommunity-AIAdAutomationSetupWizard.md` file.
2. Say: *"Run this skill"*
3. Follow the script below for Part 2.

---

## Part 1: The Meta Ad Caption Skill

### Step 1: Your Top 3 Ad Captions
**Manus:** "Welcome to the TAM AI Ad Automation setup! We are going to start by building your Meta Ad Caption Skill. Please find your top 3 best-performing ad captions from past campaigns. Copy and paste all three of them into the chat here."

**What you say on the call:** *"This is where Manus learns my exact tone of voice. I'm going to paste in three of my best-performing ad captions so it knows exactly how I write, what emojis I use, and how I structure my offers."*

**What you type into Manus (Copy the entire block below):**
```text
CAPTION 1:
We help Agency Owners create a 7-Figure Lifestyle Agency! 🚀
We mentor Aussie & NZ Agency Owners every week using our proven methods of scaling agencies legitimately.
Our method to grow agencies is called a "Client Acquisition & Retention System" which broken down is:
✅ Paid Media Funnel
✅ 2 Call Sales Process
✅ Streamlined Operation
If any of what you've just heard sounds like something that might help you... Hit 'Learn More' below & we'll explain how we help Agency Owners grow.

CAPTION 2:
Looking to grow your agency? Ready to reach the 7+ figure a year mark? 🚀
We mentor Aussie & NZ Agency Owners every week using our proven method of scaling agencies legitimately.
This method is called: "CARS"
CARS is made up of 3 key foundations to building a 7 figure agency. These are:
✅ Paid Media Funnel
✅ 2 Call Sales Process
✅ Streamlined Operation
If any of what you've just heard sounds like something that might help you... Hit 'Learn More' below & we'll explain how we help Agency Owners grow.

CAPTION 3:
LIVE Workshop – “Team Building!” – March 18th, 9am AEST! 💥
Join me on our LIVE workshop to learn how to:
✅ Build Out Pod Structures
✅ Build Your 6 Month Organisational Chart
✅ Set Clear Profit Margin Targets
✅ Measure Utilisation & Capacity Rates
BONUS Content:
🎉 Worksheets to map out organisation chart
🎉 Utilisation Rate Tracking Spreadsheet
🎉 48-hour access to the live workshop recording
First 50 tickets are only $100! After that, they’re $150.
Click the link below to grab your seat!
```

**Manus:** "Skill Created Successfully! Your `meta-ad-scripter` skill is now live. Now that your caption writer is ready, we can move on to the main event: automating your ad uploads. Please download the Meta Ad Creation Skill Wizard document..."

**What you say on the call:** *"And just like that, the first skill is built. Manus now knows exactly how to write ads in my voice. Now we move to Part 2, which is setting up the actual ad creation automation."*

---

## Part 2: The Meta Ad Creation Skill

### Step 1: Create a Meta Business App
**Manus:** "Welcome to the TAM AI Ad Automation setup! I see you have already created your `meta-ad-scripter` skill. Now we are going to build your `create-meta-ads` skill. First, we need to create a Meta Business App..."

**What you say on the call:** *"First, we create a Meta Business App. This is the secure bridge between Manus and your ad account. If Meta blocks you from creating one, it usually means your Business Manager isn't verified yet — you can fix that in Business Settings under Security Centre."*

### Step 2: System User Token
**Manus:** "Great job! ✅ Now we need to create a System User and generate your permanent access token. Please follow these steps..."

**What you say on the call:** *"This is the step that trips everyone up. First, if Meta rejects the name 'Manus Automation', just try a different name like 'TAM API User'. Second, after you create the System User, you have to add your app to its assets FIRST — before you generate the token. If you skip that, the token won't have permission to create ads. Watch me do this now..."*

**What you type into Manus (Copy the block below):**
```text
EAAMp1fsRFhUBQZCWuMKjc2ujwsUnyqMbh2vnqsTX59U9smuUFTAQr8pmXsYwONq94WR5xIbDPZAyobHdOjgFEz7iuvFcC7kyXIlbtRNUtqC1LbuHScTk4fFZAuNFdyoWC1EZBv1ZAMTRF7pSc8MWuWoMtjIeuYBAeSU0iPGjDRcBvpkLHNodFiuQZBaot5OWNxOAZDZD
```

---

### Step 3: Ad Account ID
**Manus:** "Token saved securely! Next, I need your Meta Ad Account ID... Please paste your Ad Account ID here (make sure to add `act_` at the front)."

**What you say on the call:** *"It saved the token. Now it needs to know exactly which ad account to put the ads into. I'll grab my Ad Account ID from Business Settings."*

**What you type into Manus (Copy the block below):**
```text
act_4932300966838426
```

---

### Step 4: Page & Instagram IDs
**Manus:** "Ad Account ID saved. Now I need two IDs: your Facebook Page ID and your Instagram Actor ID..."

**What you say on the call:** *"Next, it needs my Facebook Page and Instagram IDs so the ads actually look like they're coming from my agency."*

**What you type into Manus (Copy the block below):**
```text
Page ID: 106953661965167
Instagram ID: 17841452606507069
```

---

### Step 5: Campaign IDs
**Manus:** "Page and IG IDs saved. Next, I need the IDs for the specific campaigns where you want me to put the ads. Specifically, I need your Testing Campaign ID and your Performance Campaign ID..."

**What you say on the call:** *"This is the cool part. Manus doesn't create messy new campaigns — it puts the ads directly into my existing Testing and Performance campaigns. I'll give it those IDs now."*

**What you type into Manus (Copy the block below):**
```text
Testing Campaign: 120231741510640018
Performance Campaign: 120231741510640019
```

---

### Step 6: Default Landing Page URL
**Manus:** "Campaign IDs saved. ✅ Next, I need the default landing page URL where you want to send traffic from these ads."

**What you say on the call:** *"Now it just needs the default link where I want to send people when they click the ad. I'll give it my audit call booking page."*

**What you type into Manus (Copy the block below):**
```text
https://theagencymentor.com.au/agency-audit-and-growth-call
```

---

### Step 7: Google Cloud Project
**Manus:** "Landing page saved! We are done with the Meta side. Now we need to connect Google Drive so I can download your ad creatives. Let's start by creating a Google Cloud Project..."

**What you say on the call:** *"Okay so Meta is fully done. Now we're setting up the Google side. The reason we need this is simple — your video editor uploads files to Google Drive, and Manus needs a secure way to access that folder. Google requires you to create a 'project' first — think of it like registering your automation with Google. I've already done this, so I'll say done."*

**What you type into Manus (Copy the block below):**
```text
Done
```

---

### Step 8: Enable Drive API, OAuth Consent Screen & Create Client ID
**Manus:** "Project created! Now we need to do three things inside Google Cloud: Enable the Drive API, Configure OAuth Consent Screen, and Create OAuth Client ID. Paste your Client ID here when ready."

**What you say on the call:** *"This is the most detailed part of the Google setup. Three things happen here — we turn on Drive access, we configure the consent screen (which is basically telling Google what this app is called), and then we create the actual credential. The popup at the end is critical — I tell my community to copy both values into a Notes app immediately before closing it. I've already done all of this, so here's my Client ID."*

**What you type into Manus (Copy the block below):**
```text
632460847530-DEMO-bvjv0jtd2kek110dtjdasajdr2lr38gi.apps.googleusercontent.com
```
*(This is a fictitious Client ID for demo purposes only — not a real credential.)*

---

### Step 9: Google Client Secret
**Manus:** "Client ID saved. Now paste your Google Client Secret (this is the second value from that popup)."

**What you say on the call:** *"And the Client Secret — this is the second value from that popup. If anyone missed it, I remind them to click the pencil icon next to 'Manus Desktop Client' on the Credentials page to get it back."*

**What you type into Manus (Copy the block below):**
```text
GOCSPX-DEMO-oZPq-pOizYpdet6o8zXnfgEPRV-N
```
*(This is a fictitious Client Secret for demo purposes only — not a real credential.)*

---

### Step 10: Google OAuth Authorisation
**Manus:** "Client Secret saved. Final step! I am generating a special authorisation link for you. Click it, log in with your Google account, and paste the code you receive back here."

**What you say on the call:** *"This is the final step. Manus generates a custom one-time login link. I click it, Google asks me to confirm I want to give this app access to my Drive, and then it gives me a code. I paste that code back here and we're done."*

**What you type into Manus (Copy the block below):**
```text
4/0AeaYSHD8jX9kL_mN2pQ5vR3wT7yU1bC4xZ6vM9nK2lJ5hG8fD1sA4qW7eR0tY3uI6oP
```

---

### The Finale
**Manus:** "Google Drive is connected! You have provided all the necessary credentials. I am now going to build your personalised `create-meta-ads` skill in the background..."

**What you say on the call:** *"And that's it! Manus takes all those credentials, writes the Python code in the background, and builds my custom automation skill. I never had to touch a single line of code."*
