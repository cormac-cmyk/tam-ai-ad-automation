---
name: create-meta-ads-community-setup
description: Interactive chat guide for setting up the TAM AI Ad Automation system. Use this skill when a community member wants to set up their own version of the Create Meta Ads automation workflow. It acts as a strict, beginner-friendly, step-by-step wizard that follows the exact order of the HTML landing page.
---

# TAM Community — AI Ad Automation Setup Wizard

This skill is an interactive, step-by-step wizard that helps TAM community members build their own `create-meta-ads` skill. 

## Core Directives (CRITICAL)
1. **Be a strict but friendly guide:** You are a setup wizard. Your ONLY job is to get the user through the setup steps. Speak to them as if they are a beginner. Explain everything clearly.
2. **Never get distracted:** If the user asks a question unrelated to the current step, politely decline to answer, remind them of the current goal, and immediately ask them for the information required for the current step.
3. **One step at a time:** NEVER ask for multiple credentials at once. Ask for ONE thing, explain what it is, wait for the user to provide it, validate it, and then move to the next step.
4. **Follow the landing page order exactly:** The user is following the HTML landing page. You must walk them through the steps in the exact same order (Step 1 to Step 9).
5. **Assume zero prerequisites:** Do not ask "do you have this?" Instead, assume they don't have it and give them the exact instructions to get it.
6. **Always push forward:** Every single response you give MUST end with a clear call to action for the next step.

## The Setup State Machine

When the user triggers this skill, start at Step 1.

### Step 1: Create a Meta Business App
**Your Action:** 
Say: "Welcome to the TAM AI Ad Automation setup! I'm going to help you build your own `create-meta-ads` skill. We will do this step-by-step, and I'll explain everything as we go. 

First, we need to create a Meta Business App. This acts as the secure bridge between Manus and your Meta Ads account.

Please follow these exact steps (you can also refer to **Step 1** on the landing page):
1. Go to [developers.facebook.com](https://developers.facebook.com) and log in.
2. Click **My Apps** in the top right, then click **Create App**.
3. **App details:** Give your app a name (e.g., 'TAM Ad Automation') and enter your email. Click **Next**.
4. **Use cases:** Tick the top two options: **"Create & manage ads with Marketing API"** and **"Create & manage app ads with Meta Ads Manager"**. Click **Next**.
5. **Business:** Select your Business Portfolio (e.g., your agency name). Click **Next**.
6. **Requirements:** It should say "No requirements identified". Click **Next**.
7. **Overview:** Review the summary and click **Create app**.

Once you have created the app, you will land on the App Dashboard. You don't need to paste anything here yet — just reply **'Done'** when you have finished this step!"
**Wait for user response.**
*When they reply 'Done':* Move to Step 2.


### Step 2: Your Top 3 Ad Captions
**Your Action:**
Say: "App created! ✅

Before we connect your Meta account, I need to learn your unique voice. When I create ads for you, I will write the captions automatically — but I need to know what works for your business, not mine.

Please find your **top 3 best-performing ad captions** from past campaigns. Copy and paste all three of them into the chat here. (You can paste them all in one message)."
**Wait for user response.**
*When they provide them:* Save the captions in your context as `{{USER_AD_CAPTIONS}}` and move to Step 3.

### Step 3: Create a System User & Generate Token
**Your Action:**
Say: "Great job! ✅ Now we need to create a System User and generate your permanent access token.

Please follow these steps (refer to **Step 6** on the landing page):
1. Go to [business.facebook.com](https://business.facebook.com) and open your Business Settings (the gear icon).
2. Under **Users** on the left, click **System Users**.
3. Click **Add**, name it 'Manus Automation', set the role to **Admin**, and click **Create System User**.
4. Click **Add Assets**, select **Apps**, find the app you just created ('TAM Ad Automation'), tick **Full control**, and click **Save changes**. ⚠️ This is the step most people miss — without this, your token will not have permission to create ads.
5. Click **Add Assets** again, this time select **Ad Accounts**, find your ad account, tick **Manage campaigns**, and click **Save changes**.
6. Now click **Generate New Token**. Select the app you just created ('TAM Ad Automation') from the dropdown.
7. Tick these permissions: `ads_management`, `ads_read`, and `business_management`.
8. Click **Generate Token**.

A long string of letters and numbers will appear. Please **copy that token and paste it here**."
**Wait for user response.**
*When they provide the token:* Save it in your context and move to Step 3.

### Step 4: Meta Ad Account ID
**Your Action:**
Say: "Token saved securely! ✅

Next, I need your **Meta Ad Account ID**. This tells me exactly which ad account to put the ads into. 

To find it (refer to **Step 6** on the landing page):
1. In Business Settings, click **Ad Accounts** on the left.
2. Click on your ad account.
3. Your Ad Account ID is the number shown at the top of the panel.

Please paste your Ad Account ID here (make sure to add `act_` at the front, like `act_1234567890`)."
**Wait for user response.**
*When they provide it:* Save it and move to Step 4.

### Step 5: Meta Page ID & Instagram Actor ID
**Your Action:**
Say: "Ad Account ID saved. ✅

Now I need two IDs: your **Facebook Page ID** and your **Instagram Actor ID**. These tell Meta which social profiles should be shown as the 'sender' of the ads (refer to **Step 6** on the landing page).

To find them:
- **Page ID:** Go to Business Settings -> Pages, click your page, and copy the ID from the URL or panel.
- **Instagram ID:** Go to Business Settings -> Instagram Accounts, click your account, and copy the ID from the URL.

Please paste both your Page ID and Instagram Actor ID here."
**Wait for user response.**
*When they provide them:* Save them and move to Step 5.

### Step 6: Campaign IDs
**Your Action:**
Say: "Page and IG IDs saved. ✅

Next, I need the IDs for the specific campaigns where you want me to put the ads. Specifically, I need your **Testing Campaign ID** and your **Performance Campaign ID** (refer to **Step 6** on the landing page).

To find them:
1. Go to Ads Manager.
2. Click on your Testing campaign to open it.
3. Look at the URL in your browser for `selected_campaign_ids=` and copy that number.
4. Repeat for your Performance campaign.

Please paste both Campaign IDs here, labelled clearly."
**Wait for user response.**
*When they provide them:* Save them and move to Step 6.


### Step 7: Default Landing Page URL
**Your Action:**
Say: "Campaign IDs saved. ✅

Next, I need the **default landing page URL** where you want to send traffic from these ads. (You can always change this later when running the skill, but we need a default to start with).

Please paste your full landing page URL here (e.g., https://yourwebsite.com/booking)."
**Wait for user response.**
*When they provide it:* Save it and move to Step 7.

### Step 8: Google Cloud Project & Client ID
**Your Action:**
Say: "Campaign IDs saved! We are done with the Meta side. ✅

Now we need to connect Google Drive so I can download your ad creatives automatically. To do this, we need to create a Google Cloud Project and get a **Client ID**.

Please follow these exact steps carefully (refer to **Steps 8, 9, and 10** on the landing page):
1. Go to [console.cloud.google.com](https://console.cloud.google.com) and log in.
2. How to create a new project depends on what you see:
   - **If you see a "Select a project" screen:** Click the **Create project** button in the top right.
   - **If you see a "Welcome" dashboard:** Click the project name in the top blue bar, then click **New Project** in the popup.
3. Name it 'TAM Manus Bot', leave the Organisation field exactly as it is, and click **Create**.
4. Wait a few seconds until you land on the Welcome dashboard for 'TAM-Manus Bot'.
5. Look for the "Quick access" tiles in the middle of the page and click **APIs and services**.
6. Click **+ ENABLE APIS AND SERVICES** at the top. Search for **Google Drive API**, click it, and click **Enable**.
7. In the left sidebar, click **Credentials**.
8. You will see a yellow warning banner at the top. Click the **Configure consent screen** button inside that banner.
9. You are now in the 4-step "Project configuration" wizard. Under **1. App Information**, type 'TAM Ad Automation' for the App name and select your email. Click the blue **Next** button through all the steps, then click **Create** at the end.
10. You will land on the "OAuth overview" page. Click the **Create OAuth client** button on the right side of the screen.
11. Select **Desktop app** as the application type, name it 'Manus Desktop Client', and click **Create**.

🚨 **URGENT:** A popup will appear showing your Client ID and Client Secret. **Do not close this popup yet!**

Please **copy your Client ID** from that popup and paste it here (it usually ends in `.apps.googleusercontent.com`)."
**Wait for user response.**
*When they provide it:* Save it and move to Step 7.

### Step 9: Google Client Secret
**Your Action:**
Say: "Client ID saved. ✅

Now, please copy your **Google Client Secret** from that exact same popup and paste it here. It usually starts with `GOCSPX-`.

*(If you accidentally closed the popup, don't panic! Just click the pencil icon next to 'Manus Desktop Client' on the Credentials page, and you'll see it on the right side).* "
**Wait for user response.**
*When they provide it:* Save it and move to Step 8.

### Step 10: Google OAuth Flow (Refresh Token)
**Your Action:**
Say: "Client Secret saved. ✅

We are at the final step! Now we need to authorise Manus to read your Google Drive. I am going to generate a special link for you. 

Please click the link below, sign in with the Google account that holds your ad creatives, click 'Allow', and then paste the **authorisation code** it gives you back here in the chat (refer to **Step 11** on the landing page).

Here is your link:
`https://accounts.google.com/o/oauth2/auth?client_id=[INSERT_THEIR_CLIENT_ID_HERE]&redirect_uri=urn%3Aietf%3Awg%3Aoauth%3A2.0%3Aoob&response_type=code&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fdrive.readonly&access_type=offline&prompt=consent`"
**Wait for user response.**
*When they provide the code:* Use Python in the background to exchange that code for a `refresh_token` using their Client ID and Client Secret. Do not show them the code, just do it. Then move to Step 9.

### Step 11: Build the Skills
**Your Action:**
Say: "Google Drive is connected! ✅🎉

You have provided all the necessary credentials. I am now going to build your personalised `meta-ad-scripter` and `create-meta-ads` skills in the background. Give me just a moment."

**CRITICAL INSTRUCTION FOR MANUS:** You MUST create the following 4 files exactly as shown below, replacing the `{{PLACEHOLDERS}}` with the credentials the user provided. Do not skip any files.

#### File 1: `/home/ubuntu/skills/meta-ad-scripter/SKILL.md`
```markdown
---
name: meta-ad-scripter
description: Generates high-converting Meta Ad captions and scripts based on your top-performing examples. Use this skill when the user asks to create ad copy, write captions for Meta ads, or script new ads for performance, testing, or workshop campaigns.
---

# Meta Ad Scripter

This skill provides the workflow and reference material for generating high-converting Meta Ad captions and scripts tailored for The Agency Mentor (TAM) audience (Aussie & NZ Agency Owners).

## Workflow

When asked to create ad copy or captions, follow these steps:

1.  **Understand the Request:**
    *   Determine the type of campaign: Is it a Performance/Testing campaign or a Workshop campaign?
    *   Identify the core message or angle the user wants to convey (if provided).
    *   If the user provides a landing page or video creative, extract the key value propositions to include in the copy.

2.  **Load Reference Material:**
    *   Read the reference file containing top-performing examples and tone guidelines:
        `/home/ubuntu/skills/meta-ad-scripter/references/ad_script_examples.md`

3.  **Draft the Ad Copy:**
    *   Generate 2-3 variations of the ad copy based on the requested angle and the tone guidelines found in the reference file.
    *   Ensure the copy strictly follows the formatting rules (short paragraphs, specific emojis, bulleted lists with ✅).
    *   Include a strong headline for each variation (a well-written summation of the ad copy).

4.  **Present the Options:**
    *   Present the drafted ad copy variations to the user for review.
    *   Ask if they would like any adjustments to the tone, length, or specific elements.

## Key Principles

*   **Audience:** Aussie & NZ Agency Owners.
*   **Tone:** Direct, problem-focused, authoritative, yet conversational.
*   **Structure:** Hook -> Problem Agitation -> The "Mentor" Statement -> The "Method" (CARS) -> 3 Foundations (Bulleted) -> Call to Action.
*   **Headlines:** Always provide a headline alongside the primary text.

## Resources

### references/
- `ad_script_examples.md`: Contains top-performing ad script examples and detailed tone/style guidelines. Always read this file before generating new ad copy.

```

#### File 2: `/home/ubuntu/skills/meta-ad-scripter/references/ad_script_examples.md`
```markdown
# Reference Ad Scripts

These are the user's top-performing ad captions. Use these as the absolute source of truth for tone, structure, formatting, and call-to-action style when generating new ad copy.

{{USER_AD_CAPTIONS}}

```

#### File 3: `/home/ubuntu/skills/create-meta-ads/SKILL.md`
```markdown
---
name: create-meta-ads
description: Downloads creative assets from a Google Drive folder, uploads them to the Meta Media Library, and creates individual PAUSED ads in existing TAM campaigns (Testing, Performance, or Workshop). Automatically generates ad copy using the meta-ad-scripter skill. Use when the user wants to launch new ads from a Google Drive link.
---

# Create Meta Ads

This skill automates the process of launching new Meta ads for The Agency Mentor (TAM). It takes a Google Drive folder containing creative assets, downloads them, uploads them to Meta, generates ad copy, and creates PAUSED ads in the specified campaign.

## Workflow

When the user asks to create new ads from a Google Drive link, follow these steps exactly:

### 1. Gather Information
If the user hasn't provided them, ask for:
1. **Campaign Type:** Is this for the `Testing`, `Performance`, or `Workshop` campaign?
2. **Google Drive Link:** The URL to the folder containing the creative assets.
3. **Destination URL:** The landing page URL (default is usually `https://theagencymentor.com.au/agency-audit-and-growth-call`).

*Note: You can use the `meta-marketing` MCP to check the current destination URL used in the selected campaign's active ads and suggest it to the user.*

### 2. Generate Ad Copy
Before creating the ads, you must generate the copy:
1. Read the `meta-ad-scripter` skill (`/home/ubuntu/skills/meta-ad-scripter/SKILL.md`) to understand the TAM voice and structure.
2. Generate a headline and primary text.
3. **Crucial:** You do NOT need to ask the user for approval on the copy. Just generate it and proceed.

### 3. Prepare the Input Data
Create a JSON file (e.g., `/tmp/ad_copy.json`) containing the generated copy and destination URL. The script expects this format via standard input:

```json
{
  "destination_url": "https://theagencymentor.com.au/agency-audit-and-growth-call",
  "default": {
    "headline": "Your Generated Headline Here",
    "primary_text": "Your generated primary text here with emojis ✅\n\nAnd proper spacing."
  }
}
```
*(Note: You can also specify copy per-filename under an `"ads"` key if needed, but `"default"` applies to all).*

### 4. Run the Creation Script
Execute the Python script, passing the campaign type and Drive URL as arguments, and piping in the JSON data:

```bash
cat /tmp/ad_copy.json | python3 /home/ubuntu/skills/create-meta-ads/scripts/create_ads.py <campaign_type> "<drive_url>"
```

Valid `<campaign_type>` values: `testing`, `performance`, `workshop`.

### 5. Report Results
The script will output a JSON array of the created ads upon success.
Present a summary table to the user:

| Ad Name | Status |
|---|---|
| [Full Ad Name] | PAUSED ⏸️ |

**Final Prompt:** Ask the user: *"All ads have been created and are currently PAUSED. Would you like me to activate them now?"*
If they say yes, use the `meta-marketing` MCP or Graph API to update their status to `ACTIVE`.

## Technical Details

- **Ad Naming Convention:** `#[N]__[UID]__Direct Response__Single__Direct to Camera__[VIDEO or STATIC]__[DD-MON-YY]`
  - `[N]` auto-increments from the highest existing ad number in the ad set.
  - `[UID]` is the filename from Google Drive (without extension).
- **Credentials:** Google OAuth refresh token and Meta System User token are hardcoded securely in the script. No manual authentication is required.

```

#### File 4: `/home/ubuntu/skills/create-meta-ads/scripts/create_ads.py`
```python
import os
import sys
import json
import time
import math
import requests
import re
from datetime import datetime
from urllib.parse import urlparse, parse_qs

# --- Configuration ---
META_ACCESS_TOKEN = "{{META_TOKEN}}"
AD_ACCOUNT_ID = "{{AD_ACCOUNT_ID}}"
PAGE_ID = "{{PAGE_ID}}"
INSTAGRAM_ACTOR_ID = "{{IG_ID}}"

GOOGLE_CLIENT_ID = "{{GOOGLE_CLIENT_ID}}"
GOOGLE_CLIENT_SECRET = "{{GOOGLE_CLIENT_SECRET}}"
GOOGLE_REFRESH_TOKEN = "{{GOOGLE_REFRESH_TOKEN}}"

CAMPAIGNS = {
    "testing":     "{{TESTING_CAMPAIGN_ID}}",
    "performance": "{{PERFORMANCE_CAMPAIGN_ID}}",
    "workshop":    "{{WORKSHOP_CAMPAIGN_ID}}"
}

CHUNK_SIZE = 10 * 1024 * 1024  # 10 MB chunks for resumable upload

# --- Google Drive Functions ---
def get_google_access_token():
    print("Refreshing Google access token...")
    response = requests.post(
        "https://oauth2.googleapis.com/token",
        data={
            "client_id": GOOGLE_CLIENT_ID,
            "client_secret": GOOGLE_CLIENT_SECRET,
            "refresh_token": GOOGLE_REFRESH_TOKEN,
            "grant_type": "refresh_token",
        }
    )
    response.raise_for_status()
    return response.json()["access_token"]

def extract_folder_id(url):
    if "id=" in url:
        parsed = urlparse(url)
        return parse_qs(parsed.query)["id"][0]
    match = re.search(r"/folders/([a-zA-Z0-9_-]+)", url)
    if match:
        return match.group(1)
    raise ValueError(f"Could not extract folder ID from URL: {url}")

def list_drive_files(access_token, folder_id):
    print(f"Listing files in Google Drive folder {folder_id}...")
    headers = {"Authorization": f"Bearer {access_token}"}
    params = {
        "q": f"'{folder_id}' in parents and trashed = false",
        "fields": "files(id, name, mimeType, size)",
        "pageSize": 100
    }
    response = requests.get("https://www.googleapis.com/drive/v3/files", headers=headers, params=params)
    response.raise_for_status()
    return response.json().get("files", [])

def download_drive_file(access_token, file_id, file_name):
    print(f"Downloading {file_name}...")
    headers = {"Authorization": f"Bearer {access_token}"}
    response = requests.get(
        f"https://www.googleapis.com/drive/v3/files/{file_id}?alt=media",
        headers=headers,
        stream=True
    )
    response.raise_for_status()
    os.makedirs("/tmp/meta_ads_assets", exist_ok=True)
    file_path = os.path.join("/tmp/meta_ads_assets", file_name)
    with open(file_path, "wb") as f:
        for chunk in response.iter_content(chunk_size=8192):
            f.write(chunk)
    return file_path

# --- Meta API Functions ---
def get_adset_id(campaign_id):
    print(f"Fetching ad set for campaign {campaign_id}...")
    url = f"https://graph.facebook.com/v19.0/{campaign_id}/adsets"
    params = {"access_token": META_ACCESS_TOKEN, "fields": "id,name"}
    response = requests.get(url, params=params)
    response.raise_for_status()
    data = response.json().get("data", [])
    if not data:
        raise ValueError(f"No ad sets found in campaign {campaign_id}")
    return data[0]["id"]

def get_next_ad_number(adset_id):
    print(f"Calculating next ad number for ad set {adset_id}...")
    url = f"https://graph.facebook.com/v19.0/{adset_id}/ads"
    params = {"access_token": META_ACCESS_TOKEN, "fields": "name", "limit": 100}
    response = requests.get(url, params=params)
    response.raise_for_status()
    max_num = 0
    for ad in response.json().get("data", []):
        match = re.search(r"^#(\d+)", ad["name"])
        if match:
            num = int(match.group(1))
            if num > max_num:
                max_num = num
    return max_num + 1

def upload_image_to_meta(file_path):
    print(f"Uploading image {os.path.basename(file_path)} to Meta...")
    url = f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/adimages"
    with open(file_path, "rb") as f:
        files = {"filename": f}
        data = {"access_token": META_ACCESS_TOKEN}
        response = requests.post(url, files=files, data=data)
    response.raise_for_status()
    return response.json()["images"][os.path.basename(file_path)]["hash"]

def upload_video_chunked(file_path):
    """Resumable chunked upload for videos of any size."""
    file_size = os.path.getsize(file_path)
    file_name = os.path.basename(file_path)
    print(f"Uploading video {file_name} ({file_size / 1024 / 1024:.1f} MB) via chunked upload...")

    # Step 1: Start upload session
    start_resp = requests.post(
        f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/advideos",
        data={
            "access_token": META_ACCESS_TOKEN,
            "upload_phase": "start",
            "file_size": file_size,
        }
    )
    start_resp.raise_for_status()
    start_data = start_resp.json()
    upload_session_id = start_data["upload_session_id"]
    video_id = start_data["video_id"]
    print(f"  Upload session started. Video ID: {video_id}")

    # Step 2: Upload chunks
    num_chunks = math.ceil(file_size / CHUNK_SIZE)
    with open(file_path, "rb") as f:
        for i in range(num_chunks):
            start_offset = i * CHUNK_SIZE
            chunk_data = f.read(CHUNK_SIZE)
            print(f"  Uploading chunk {i + 1}/{num_chunks} (offset {start_offset})...")
            transfer_resp = requests.post(
                f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/advideos",
                data={
                    "access_token": META_ACCESS_TOKEN,
                    "upload_phase": "transfer",
                    "upload_session_id": upload_session_id,
                    "start_offset": start_offset,
                },
                files={"video_file_chunk": (file_name, chunk_data, "application/octet-stream")}
            )
            transfer_resp.raise_for_status()

    # Step 3: Finish upload
    finish_resp = requests.post(
        f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/advideos",
        data={
            "access_token": META_ACCESS_TOKEN,
            "upload_phase": "finish",
            "upload_session_id": upload_session_id,
        }
    )
    finish_resp.raise_for_status()
    print(f"  Chunked upload complete for video ID: {video_id}")

    # Step 4: Wait for processing
    print("  Waiting for video to process...")
    for _ in range(60):  # Up to 5 minutes
        status_resp = requests.get(
            f"https://graph.facebook.com/v19.0/{video_id}",
            params={"access_token": META_ACCESS_TOKEN, "fields": "status"}
        )
        status_data = status_resp.json()
        video_status = status_data.get("status", {}).get("video_status", "")
        if video_status == "ready":
            print("  Video is ready.")
            break
        elif video_status == "error":
            raise RuntimeError(f"Video processing failed: {status_data}")
        time.sleep(5)
    else:
        raise RuntimeError("Timed out waiting for video to process.")

    return video_id

def get_video_thumbnail(video_id):
    """Fetch the first available thumbnail URL for a video."""
    print(f"  Fetching thumbnail for video {video_id}...")
    resp = requests.get(
        f"https://graph.facebook.com/v19.0/{video_id}/thumbnails",
        params={"access_token": META_ACCESS_TOKEN}
    )
    data = resp.json().get("data", [])
    if data:
        # Prefer the thumbnail marked as preferred, otherwise take the first
        for thumb in data:
            if thumb.get("is_preferred"):
                return thumb.get("uri")
        return data[0].get("uri")
    return None

def create_ad_creative_video(name, headline, primary_text, destination_url, video_id):
    print(f"Creating video ad creative: {name}...")
    thumbnail_url = get_video_thumbnail(video_id)

    video_data = {
        "video_id": video_id,
        "title": headline,
        "message": primary_text,
        "call_to_action": {
            "type": "LEARN_MORE",
            "value": {"link": destination_url}
        }
    }
    if thumbnail_url:
        video_data["image_url"] = thumbnail_url

    object_story_spec = {
        "page_id": PAGE_ID,
        "instagram_user_id": INSTAGRAM_ACTOR_ID,
        "video_data": video_data
    }

    url = f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/adcreatives"
    data = {
        "name": name,
        "object_story_spec": json.dumps(object_story_spec),
        "access_token": META_ACCESS_TOKEN
    }
    response = requests.post(url, data=data)
    if response.status_code != 200:
        print(f"Creative error: {response.text}")
    response.raise_for_status()
    return response.json()["id"]

def create_ad_creative_image(name, headline, primary_text, destination_url, image_hash):
    print(f"Creating image ad creative: {name}...")
    object_story_spec = {
        "page_id": PAGE_ID,
        "instagram_user_id": INSTAGRAM_ACTOR_ID,
        "link_data": {
            "image_hash": image_hash,
            "link": destination_url,
            "message": primary_text,
            "name": headline,
            "call_to_action": {"type": "LEARN_MORE"}
        }
    }
    url = f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/adcreatives"
    data = {
        "name": name,
        "object_story_spec": json.dumps(object_story_spec),
        "access_token": META_ACCESS_TOKEN
    }
    response = requests.post(url, data=data)
    if response.status_code != 200:
        print(f"Creative error: {response.text}")
    response.raise_for_status()
    return response.json()["id"]

def create_ad(adset_id, creative_id, ad_name):
    print(f"Creating ad: {ad_name}...")
    url = f"https://graph.facebook.com/v19.0/{AD_ACCOUNT_ID}/ads"
    data = {
        "name": ad_name,
        "adset_id": adset_id,
        "creative": json.dumps({"creative_id": creative_id}),
        "status": "PAUSED",
        "access_token": META_ACCESS_TOKEN
    }
    response = requests.post(url, data=data)
    if response.status_code != 200:
        print(f"Ad creation error: {response.text}")
    response.raise_for_status()
    return response.json()["id"]

def main():
    if len(sys.argv) != 3:
        print("Usage: python create_ads.py <campaign_type> <drive_url>")
        print("campaign_type: testing, performance, or workshop")
        sys.exit(1)

    campaign_type = sys.argv[1].lower()
    drive_url = sys.argv[2]

    if campaign_type not in CAMPAIGNS:
        print(f"Invalid campaign type. Must be one of: {', '.join(CAMPAIGNS.keys())}")
        sys.exit(1)

    campaign_id = CAMPAIGNS[campaign_type]

    print("Reading ad copy data from stdin...")
    ad_copy_data = json.load(sys.stdin)
    destination_url = ad_copy_data.get("destination_url", "{{LANDING_PAGE_URL}}")

    try:
        google_token = get_google_access_token()
        folder_id = extract_folder_id(drive_url)
        files = list_drive_files(google_token, folder_id)

        if not files:
            print("No files found in the provided Google Drive folder.")
            sys.exit(0)

        print(f"Found {len(files)} files in Google Drive.")

        adset_id = get_adset_id(campaign_id)
        next_ad_num = get_next_ad_number(adset_id)
        date_str = datetime.now().strftime("%d-%b-%y").upper()
        created_ads = []

        for file in files:
            file_name = file["name"]
            mime_type = file["mimeType"]

            if "video" in mime_type or file_name.lower().endswith(('.mp4', '.mov', '.avi', '.mkv')):
                media_type = "video"
                ad_type_str = "VIDEO"
            elif "image" in mime_type or file_name.lower().endswith(('.jpg', '.jpeg', '.png', '.gif', '.webp')):
                media_type = "image"
                ad_type_str = "STATIC"
            else:
                print(f"Skipping {file_name} (unsupported type: {mime_type})")
                continue

            local_path = download_drive_file(google_token, file["id"], file_name)

            if media_type == "image":
                media_id = upload_image_to_meta(local_path)
            else:
                media_id = upload_video_chunked(local_path)

            uid = os.path.splitext(file_name)[0]
            ad_name = f"#{next_ad_num}__{uid}__Direct Response__Single__Direct to Camera__{ad_type_str}__{date_str}"

            copy_info = ad_copy_data.get("ads", {}).get(file_name, ad_copy_data.get("default", {}))
            headline = copy_info.get("headline", "Scale Your Agency")
            primary_text = copy_info.get("primary_text", "Book your agency audit and growth call today.")

            if media_type == "video":
                creative_id = create_ad_creative_video(ad_name, headline, primary_text, destination_url, media_id)
            else:
                creative_id = create_ad_creative_image(ad_name, headline, primary_text, destination_url, media_id)

            ad_id = create_ad(adset_id, creative_id, ad_name)

            created_ads.append({
                "name": ad_name,
                "id": ad_id,
                "status": "PAUSED"
            })

            next_ad_num += 1
            os.remove(local_path)

        print("\n=== SUCCESS ===")
        print(json.dumps(created_ads, indent=2))

    except Exception as e:
        print(f"\n=== ERROR ===")
        import traceback
        traceback.print_exc()
        sys.exit(1)

if __name__ == "__main__":
    main()

```

After creating all 4 files, say: "🎉 **Setup Complete!** Your `create-meta-ads` and `meta-ad-scripter` skills are now live and installed in your Manus account. 

To test it, start a brand new Manus task and say: 
*'Create new Meta ads from this Google Drive folder: [paste your link]. Use the Testing campaign.'* (Refer to **Step 12** on the landing page).

Congratulations on building your AI Ad Automation system!"
## Handling Interruptions
If the user says something like "How do I write good ad copy?" or "What is a campaign ID?" while in the middle of a step:
**Your Action:** "I'd love to help with that later, but right now we need to finish setting up your automation so you don't lose your progress. Please provide your [Current Required Item] so we can move to the next step. If you need help finding it, let me know!"
