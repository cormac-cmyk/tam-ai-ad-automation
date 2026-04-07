# TAM AI Ad Automation — Pre-Call Prep Checklist
### The Agency Mentor | Live Build Session

---

> **Your Setup Call Starts Soon.**
> This isn't a passive webinar — it's a live build session. Every member who comes prepared walks away with a working automation. Every member who doesn't, watches. Complete this checklist before the call.


> **Can't figure something out right now? That's totally fine.** Do what you can before the call. The more you have ready, the more you'll get out of the session — but we'll help you work through anything you're stuck on together.

---

## What We Are Building Together

On the call, Manus will walk you through setting up two skills. By the end, you will paste a Google Drive link and watch ads build themselves.

1. **Meta Ad Caption Skill:** Learns your unique voice from your best-performing ads. Writes captions that sound exactly like you — not a generic AI.
2. **Meta Ad Creation Skill:** Downloads creatives from Google Drive, writes captions using Skill 1, and publishes ads to Meta. Fully automated.

---

## ⚠️ Critical Requirement: Manus Pro Plan

These skills use background Python execution and persistent skill files — features only available on the **Pro plan or above**. If you are on the free tier, upgrade at [manus.im](https://manus.im) before the call. Setup will not work on a free account.

---

## 1. Your Ad Content
*What Manus will use to learn your voice.*

- [ ] **Your Top 3+ Best-Performing Ad Captions**
  Open Meta Ads Manager → Ads level → sort by Cost Per Lead (ascending) or Leads (descending). Copy the Primary Text from your top 3 ads. If you have more winners, grab all of them — the more context, the better your captions will be.
- [ ] **Your Default Landing Page URL**
  The URL where your ads will send traffic — usually your booking page, VSL, or lead form. Have it copied and ready to paste. Example: `https://yourwebsite.com/booking`

---

## 2. Meta / Facebook Setup
*Your ad account access and credentials.*

- [ ] **Meta Business Manager — Verified**
  Go to `business.facebook.com` → Business Settings → Security Centre. If your account shows "Not Verified", click Start Verification and complete it now. An unverified account will block you from creating a Meta Developers app.
- [ ] **Meta Developers Account — Logged In**
  Visit `developers.facebook.com` and confirm you can log in. If you've never been here before, your first visit will ask you to register as a developer — click Get Started and complete the one-time registration.
- [ ] **Meta Ads Manager — Access Confirmed**
  Open `adsmanager.facebook.com` and confirm you can see your active ad account. You will need Admin access — not just Advertiser. If you are an employee or agency, confirm with your account owner that you have Admin permissions.
- [ ] **Your Ad Account ID — Copied**
  Business Settings → Ad Accounts → click your account → copy the ID from the right panel. It is a number like `1234567890`. You will paste it as `act_1234567890`.
- [ ] **Facebook Page ID — Copied**
  Business Settings → Pages → click your Page → copy the Page ID from the right panel. It is a long number like `106953661965167`.
- [ ] **Instagram Account ID — Copied**
  Business Settings → Instagram Accounts → click your account → copy the ID. It is a long number like `17841452606507069`. This is different from your Instagram username.
- [ ] **Testing & Performance Campaign IDs — Copied**
  Open Ads Manager → click into your Testing campaign → look at the URL for `selected_campaign_ids=` and copy that number. Repeat for your Performance campaign. If you don't have these campaigns yet, create them before the call.

---

## 3. Google Setup
*Drive access so Manus can download your creatives.*

- [ ] **Google Account — Logged In**
  Make sure you are logged into the Google account that your video editor uses to upload ad creatives. This is the account you will use to authorise Drive access during the setup.
- [ ] **Google Cloud Console — Can Access**
  Visit `console.cloud.google.com` and confirm you can log in. You don't need to do anything there yet — just confirm access. If you've never been here before, you may be prompted to agree to Google Cloud terms of service.
- [ ] **Google Drive Folder — Ready with Creatives**
  Have at least one Google Drive folder ready with video or image files you want to turn into ads. This is what you will paste the link to when you first run the skill after setup. Your video editor should be uploading files here.

---

## 4. Manus Setup
*Your AI platform where the skills will live.*

- [ ] **Manus Account — Pro Plan or Above**
  Log into `manus.im` and confirm your subscription is Pro or higher. Free accounts cannot run skill files or background Python scripts. If you need to upgrade, do it before the call — setup will not work on a free account.

---

**All boxes ticked?** You are ready to build. Show up to the call and you will walk away with a fully working ad automation — no delays, no admin, just results.
