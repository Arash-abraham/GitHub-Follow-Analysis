<div align="center">
  <img src="icons/icon128.png" width="96" height="96" alt="GitHub Follow Analysis Icon">
  <h1>GitHub Follow Analysis</h1>
  <p><strong>Browser Extension (Manifest V3) to analyze GitHub followers &amp; following, detect one-way connections, filter &amp; sort profiles, and bulk follow or unfollow.</strong></p>

  <p>
    🌐 <strong>Language:</strong> <strong>English</strong> &nbsp;|&nbsp; <a href="./README.fa.md"><strong>فارسی (Persian)</strong></a>
  </p>
</div>

 **راهنمای فارسی:** می‌توانید مستندات کامل و آموزش گام‌به‌گام نصب و استفاده به زبان فارسی را [**اینجا بخوانید (README.fa.md)**](./README.fa.md).

---

## Overview

**GitHub Follow Analysis** is a lightweight, dependency-free browser extension for **Chrome, Edge, Brave, Opera, Vivaldi, and Firefox** that lets you inspect the relationship between any GitHub account's **Following** and **Followers** lists directly inside GitHub—or in a dedicated full-page dashboard.

In seconds, it compares every page of `following` and `followers`, fetches rich profile cards in batches, and organizes accounts into three actionable views:

1. **Not following back** — Accounts the user follows that do **not** follow them back (one-way following).
2. **Not followed back** — Accounts that follow the user whom the user does **not** follow back (one-way followers).
3. **Mutuals** — Accounts with a mutual follow connection (profiles are lazy-loaded only when opened to save API quota).

---

## Key Features

- **4 Convenient Ways to Launch**
  - **GitHub Profile Button:** Adds a native **"Follow Analysis"** button directly on GitHub user profile sidebars.
  - **Toolbar Popup:** Detect the current GitHub user automatically, switch to your own `@username` in one click, or enter any GitHub username.
  - **Right-Click Context Menu:** Right-click any GitHub page or link to a `@username` and choose **"Analyze GitHub Follows"**.
  - **Standalone Full-Tab Dashboard:** Run analyses from anywhere—even when you don't have `github.com` open.
- **Rich Profile Cards** — Displays avatar, `@username`, `Org` badge for organizations, display name, bio, public repository count, followers, following, location, and company.
- **Advanced Filter & Sort Drawer**
  - Sort by **Username (A→Z / Z→A)**, **Followers (High/Low)**, **Following (High/Low)**, or **Public Repos (High/Low)**.
  - Filter by **Account Type**: *All Accounts*, *Users Only (Hide Organizations)*, or *Organizations Only* — critical because GitHub Organizations cannot follow users back!
  - Filter by **Min / Max Followers**, **Min Public Repos**, and profile completeness (**Has Bio**, **Has Location**, **Has Company**).
  - Instant keyword search across username, name, bio, company, and location.
- **Single & Bulk Follow / Unfollow**
  - Follow or unfollow individual accounts in one click or run bulk actions on selected accounts with live progress and a **Stop** button to pause safely at any time.
- **Popup-Blocker-Free Multi-Tab Opener**
  - Uses the browser extension Tabs API to open selected profiles cleanly in background tabs—never blocked by site popup blockers.
- **CSV Export**
  - Export selected or filtered accounts (including bio, stats, company, location, and profile URL) to `.csv` in one click.
- **Live Rate Limit & Token Verification**
  - Real-time GitHub API remaining quota indicator and automatic scope verification (`user:follow`).
- **100% Local & Private**
  - Zero external servers, zero analytics, zero tracking. Your Personal Access Token stays exclusively in `chrome.storage.local` and is sent only to `https://api.github.com`.

---

## Installation

### Google Chrome / Microsoft Edge / Brave / Opera / Vivaldi

1. **Download or clone this repository** to your computer:
   ```bash
   git clone https://github.com/Arash-abraham/GitHub-Follow-Analysis.git
   ```
   *(Or click **Code → Download ZIP** on GitHub and extract the ZIP archive.)*
2. Open your browser's extensions page:
   - **Chrome:** `chrome://extensions`
   - **Edge:** `edge://extensions`
   - **Brave:** `brave://extensions`
   - **Opera:** `opera://extensions`
3. Enable **Developer mode** (toggle in the top-right corner).
4. Click **Load unpacked** and select the `GitHub-Follow-Analysis` folder (the folder containing `manifest.json`).
5. *(Optional)* Click the puzzle-piece Extensions icon in your browser toolbar and **pin** **GitHub Follow Analysis** for quick access.

### Mozilla Firefox (128+)

1. Clone or download and unzip this repository.
2. Open `about:debugging#/runtime/this-firefox` in Firefox.
3. Click **Load Temporary Add-on...** and select the `manifest.json` file inside the `GitHub-Follow-Analysis` directory.

---

## Setting Up a GitHub Personal Access Token (Recommended)

> **Can I use the extension without a token?**  
> **Yes!** Read-only analysis works without a token, but GitHub limits unauthenticated requests to **60 requests per hour** and disables **Follow / Unfollow** actions. Adding a Personal Access Token raises your limit to **5,000 requests per hour** and unlocks one-click Follow & Unfollow.

### Step 1: Create a Token on GitHub

#### Option A — Personal Access Token (Classic) *(Simplest)*
1. Go to [**GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**](https://github.com/settings/tokens/new?description=GitHub%20Follow%20Analysis&scopes=user:follow).
2. Enter a note (e.g. `GitHub Follow Analysis`) and choose an expiration period.
3. Check **only** the **`user:follow`** scope *(no `repo` or admin permissions are needed!)*.
4. Click **Generate token** and copy the generated `ghp_...` token.

#### Option B — Fine-Grained Personal Access Token
1. Go to [**GitHub → Settings → Developer settings → Fine-grained tokens**](https://github.com/settings/personal-access-tokens/new).
2. Under **Permissions → Account permissions**, set **Followers** to **Read and write**.
3. Generate the token and copy the `github_pat_...` value.

### Step 2: Save Your Token in the Extension

You can save your token from **any** of three places:
- **Toolbar Popup:** Click the extension icon → paste your token in the **GitHub API & Token** card → click **Save & Verify**.
- **In-Page Modal:** Click **Set Token** in the top-right header of the Follow Analysis modal → paste token → click **Save Token**.
- **Settings Page:** Right-click the extension icon → **Options** (or click the gear icon in the popup) → paste token → click **Save & Verify Token**.

---

## How to Use

### 1. Launch an Analysis

- **From any GitHub Profile Page:**  
  Visit `https://github.com/<username>` (for example, your own profile) and click the **Follow Analysis** button right below the `followers · following` counter in the left sidebar.
- **From the Extension Toolbar Popup:**  
  Click the **GitHub Follow Analysis** icon in your browser toolbar. If you're on a GitHub page, the username is auto-detected; otherwise type any GitHub username (or click your `@username` quick chip) and click **Analyze on GitHub Page** or **Open in Full Tab**.
- **From the Right-Click Context Menu:**  
  On `github.com`, right-click anywhere on a profile page—or right-click any link pointing to a GitHub user—and select **Analyze GitHub Follows**.

### 2. Search, Filter & Sort Accounts

- **Search Bar:** Filter instantly by username, display name, bio, company, or location.
- **Filter & Sort Button (Sliders Icon):** Click the sliders button next to the search box to open the filter drawer:
  - **Hide Organizations:** Set **Account Type** to **Users Only (Hide Orgs)** in the *Not following back* tab so you don't accidentally unfollow GitHub Organizations (organizations cannot follow users back).
  - **Sort:** Order accounts by follower count, following count, public repositories, or alphabetically.
  - **Numeric & Profile Filters:** Narrow by minimum/maximum followers, minimum public repos, or require bio/location/company.

### 3. Follow, Unfollow, Open Tabs, or Export

- **Single Action:** Click **Unfollow** or **Follow** on any user card.
- **Bulk Selection:** Click cards (or checkboxes) to select individual accounts, or click **Select All** to select every account matching your active search/filter.
- **Bulk Unfollow / Follow:** Click **Unfollow N** or **Follow N** in the bottom footer and confirm. Progress updates live, and you can click **Stop** at any moment to halt remaining requests.
- **Open Selected Tabs:** Click **Open N Tab(s)** to open all selected GitHub profiles in background tabs for manual review.
- **Export to CSV:** Click **CSV** in the toolbar to download a spreadsheet of your selected (or currently visible) accounts.

---

## Extension Settings

Open **Extension Settings** via the gear icon in the popup (or browser extension Options) to customize:

| Setting | Default | Description |
| :--- | :---: | :--- |
| **Show "Follow Analysis" button on GitHub profiles** | `Enabled` | Injects a quick-launch button in GitHub profile sidebars. |
| **Profile Batch Size** | `10` | Number of user profiles fetched concurrently per batch (`1–50`). |
| **Batch Delay (ms)** | `200 ms` | Pause between consecutive profile batches. |
| **Bulk Follow / Unfollow Delay (ms)** | `300 ms` | Pause between sequential follow/unfollow requests to respect GitHub secondary rate limits. |
| **Open Selected Tabs Delay (ms)** | `180 ms` | Pause between opening selected profile tabs in the background. |

---

## Project Structure

```text
GitHub-Follow-Analysis/
├── manifest.json              # Manifest V3 configuration
├── background/
│   └── service-worker.js      # GitHub API client, token validator, context menu & tab opener
├── shared/
│   └── analyzer-ui.js         # Shared Follow Analysis modal & dashboard UI engine
├── content/
│   ├── content.css            # Scoped modal, filter drawer & profile button styles
│   └── content.js             # GitHub SPA observer, sidebar button & message handler
├── popup/
│   ├── popup.html             # Toolbar popup markup
│   ├── popup.css              # Toolbar popup styles
│   └── popup.js               # Username detection, token verification & rate limit bar
├── dashboard/
│   ├── dashboard.html         # Full-page standalone analyzer view
│   ├── dashboard.css          # Standalone layout styles
│   └── dashboard.js           # Standalone analyzer bootstrap
├── options/
│   ├── options.html           # Extension settings & PAT guide
│   ├── options.css            # Settings page styles
│   └── options.js             # Settings persistence & token validation
├── icons/                     # Extension icons (SVG + 16/32/48/128 PNG)
├── README.md                  # English documentation (main)
├── README.fa.md               # Persian (فارسی) documentation
└── LICENSE                    # MIT License
```

---

## Privacy & Security

- **No hardcoded credentials** and **no third-party servers**.
- Your GitHub Personal Access Token is stored locally inside your browser (`chrome.storage.local`) and is never exposed to page scripts on websites.
- Network requests are strictly restricted to `https://api.github.com/*`.

---

## License

Released under the [MIT License](./LICENSE).
