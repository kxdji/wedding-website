# 🚀 The Complete PowerShell, Git & Vercel Deployment Master Guide

A comprehensive, beginner-friendly reference covering every command, flag, technical concept, and troubleshooting step learned during the deployment of the **Abram & Danielle Wedding Website**.

---

## 📑 Table of Contents
1. [Understanding the Terminal & PowerShell Navigation](#1-understanding-the-terminal--powershell-navigation)
2. [Git & GitHub Commands: Word-by-Word Breakdown](#2-git--github-commands-word-by-word-breakdown)
3. [How Vercel Works & Why It's Free](#3-how-vercel-works--why-its-free)
4. [Fixing the 404 NOT_FOUND Error (The Root Directory Concept)](#4-fixing-the-404-not_found-error-the-root-directory-concept)
5. [Custom Domains (`bramanddee.com`) Demystified](#5-custom-domains-bramanddeecom-demystified)
6. [Crucial Gotchas & Edge Cases Checklist](#6-crucial-gotchas--edge-cases-checklist)
7. [Day-to-Day Cheatsheet: Making Future Updates](#7-day-to-day-cheatsheet-making-future-updates)

---

## 1. Understanding the Terminal & PowerShell Navigation

### Why PowerShell Opens in `System32`
* When you launch PowerShell normally (or as Administrator), Windows starts in its default system location: `C:\Windows\System32` or your user home directory `C:\Users\Ked`.
* A terminal **does not automatically know** which project you want to work on until you tell it where to navigate.

### How to Navigate in PowerShell
```powershell
cd "c:\Users\Ked\Documents\Projects\wedding website\wedding-website"
```
* **`cd`** stands for **Change Directory**.
* **Quotation Marks (`"..."`)** are **mandatory** whenever any folder in your path has a space (like `"wedding website"`). Without quotes, PowerShell thinks `wedding` and `website` are two separate parameters and throws an error.

### 💡 The File Explorer Address Bar Shortcut
1. Open Windows File Explorer and navigate into your folder.
2. Click directly on the top address bar (or press `Alt + D`).
3. Type `powershell` and hit **Enter**.
4. A terminal window will open with the exact working directory already active.

---

## 2. Git & GitHub Commands: Word-by-Word Breakdown

Here is the exact sequence of commands and what every single word, flag, and symbol means under the hood.

```
┌─────────────┐     git add .     ┌──────────────┐   git commit    ┌────────────────┐   git push    ┌─────────────┐
│ Your Files  │ ────────────────► │ Staging Area │ ──────────────► │ Local Git Repo │ ────────────► │ GitHub Repo │
└─────────────┘                   └──────────────┘                 └────────────────┘               └─────────────┘
```

---

### Command 1: `git init`
```powershell
git init
```
* **`git`**: Calls the Git version control program installed on your machine.
* **`init`**: Short for **initialize**.
* **What it does:** Creates a hidden `.git` folder in your directory. This turns an ordinary Windows folder into a Git repository that tracks changes, history, and revisions.

---

### Command 2: `git add .`
```powershell
git add .
```
* **`add`**: Tells Git to move files from your working directory into the **Staging Area** (a preparation room for what will be saved in the next snapshot).
* **`.` (the dot/period)**: In command-line syntax, a single dot `.` means **"everything in the current directory and all subdirectories"**.
* **What it does:** Stages all new, modified, and deleted files for commit.

---

### Command 3: `git commit -m "Initial commit of wedding website"`
```powershell
git commit -m "Initial commit of wedding website"
```
* **`commit`**: Takes all files currently in the Staging Area and permanently saves a point-in-time snapshot to your local Git history.
* **`-m`**: A flag that stands for **"message"**. It tells Git that the string following in quotes is the description of this commit.
* **`"..."`**: The human-readable message describing what changes were made.

---

### Command 4: `git branch -M main`
```powershell
git branch -M main
```
* **`branch`**: Git's tool for managing different development timelines.
* **`-M`**: Stands for **Move / rename (Force)**.
  * `-m` is lowercase rename.
  * `-M` is uppercase force rename (overwrites any existing branch with that name).
* **`main`**: The standard modern name for your primary code branch (replacing the older default name `master`).

---

### Command 5: `git remote add origin https://github.com/USERNAME/REPO.git`
```powershell
git remote add origin https://github.com/kxdji/wedding-website.git
```
* **`remote`**: Manages connections to repositories located on servers outside your computer.
* **`add`**: Creates a new connection link.
* **`origin`**: The standard industry nickname given to your primary remote repository. (Instead of typing the full 60-character URL every time, you just refer to `origin`).
* **`https://github.com/...`**: The exact web address of your GitHub repository.

---

### Command 6: `git push -u origin main`
```powershell
git push -u origin main
```
* **`push`**: Uploads your local commits and files up to the remote server.
* **`-u`**: Stands for **set upstream tracking**. This tells Git: *"Link my local `main` branch directly to `origin/main`"*.
  * **Why this is awesome:** Because of `-u`, every time you make updates in the future, you only need to type `git push` (no need to type `origin main` again).
* **`origin`**: Where to send the files (the GitHub URL aliased earlier).
* **`main`**: Which branch to push.

---

## 3. How Vercel Works & Why It's Free

### What Vercel Does
* Vercel connects directly to your GitHub repository.
* Every time you run `git push`, Vercel detects the new commit, automatically builds your website, and distributes it across a global **Edge Content Delivery Network (CDN)** in less than 20 seconds.

### Why Is Hosting Free? (The Freemium Model)
1. **Static Files Cost Near $0**: Your wedding site is pure HTML, CSS, and images. Unlike database-heavy dynamic apps, static files are cached globally and require negligible server power.
2. **Developer Acquisition**: Vercel gives individual creators free hobby hosting so developers use and love their tools. When those developers work at companies, their employers pay Vercel thousands of dollars/month for Enterprise plans.
3. **No Catch**: There are no hidden fees, no injected ads, and no expiration date on the free tier.

---

## 4. Fixing the 404 NOT_FOUND Error (The Root Directory Concept)

### Why the Error Happened
When you pushed your whole project workspace to GitHub, the folder structure on GitHub looked like this:
```
wedding-website (GitHub Repository)
├── _raw_assets/
├── markdowns/
└── wedding-website/          <── Actual website files are in here!
    ├── index.html
    ├── Title.png
    └── gallery-1.jpg
```

By default, Vercel looks for `index.html` in the **root folder (`./`)**. Because `index.html` was tucked inside the `wedding-website` subfolder, Vercel couldn't find an entry file and gave a **`404: NOT_FOUND`**.

### The Permanent Fix in Vercel
1. Go to **Vercel Dashboard $\rightarrow$ Project Settings**.
2. In the left menu, click **Build and Deployment**.
3. Under **Root Directory**, click **Edit**, type:
   ```
   wedding-website
   ```
4. Click **Save**.
5. Go to the **Deployments** tab, click the three dots (`...`) on the latest build, and click **Redeploy**.

---

## 5. Custom Domains (`bramanddee.com`) Demystified

### How Buying on Vercel Works
* **Price:** $11.25/year (covers wholesale registry cost + ICANN regulatory fees).
* **Duration:** Registered for 1 full year. You can renew it annually or turn off auto-renewal after the wedding season.
* **Zero Config Benefit:** Buying through Vercel automatically creates and links all DNS A-Records (`76.76.21.21`), CNAME records (`cname.vercel-dns.com`), and generates the free SSL/HTTPS security lock.

---

## 6. Crucial Gotchas & Edge Cases Checklist

| Edge Case | Why It Happens | Action Required |
| :--- | :--- | :--- |
| **📧 ICANN 14-Day Email Verification** | International law requires email verification for new domains. | Check your email within 24–48 hours of purchase and **click the confirmation link** to prevent domain suspension. |
| **📝 Google Apps Script RSVP Permissions** | Browser `no-cors` mode prevents JavaScript from detecting HTTP errors. | In Apps Script: set **Execute as: "Me"** and **Who has access: "Anyone"**. Test a real submission. |
| **⏳ Local ISP DNS Cache Lag** | Philippine ISPs (Globe, PLDT, Smart) cache DNS records locally. | A domain might take 1–6 hours to resolve on mobile data after purchase; this is normal DNS propagation. |
| **📱 Heavy Gallery Images** | 6MB+ camera files can load slowly on mobile data. | Compress large JPGs to ~300KB–500KB so the site opens instantaneously on cellular phones. |
| **💬 Social Media Link Previews** | Chat apps (iMessage, WhatsApp, Messenger) look for OpenGraph tags. | Add `<meta property="og:image">` and `og:description` to display a nice thumbnail when texting the link. |

---

## 7. Day-to-Day Cheatsheet: Making Future Updates

Whenever you make changes to `index.html` or photos in the future, follow this 3-step routine in PowerShell:

```powershell
# 1. Stage all modifications
git add .

# 2. Save your snapshot with a description of what you changed
git commit -m "Updated guest notes and color palette"

# 3. Push live (Vercel updates your live website automatically in ~15 seconds!)
git push
```

---
*Created for Abram & Danielle's Wedding Website Deployment (`bramanddee.com`)*
