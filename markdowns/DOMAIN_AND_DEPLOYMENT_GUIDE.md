# 🌐 Deployment & Custom Domain Guide (`bramanddee.com`)

This guide explains how to deploy the **Abram & Danielle Wedding Website** to **Vercel** for free and link your custom domain (`bramanddee.com`).

---

## 📌 Core Concept: Domain vs. Web Hosting

* **Web Hosting (Vercel)**: The free server where your website's files (`index.html`, photos, styles) live.
* **Domain Name (`bramanddee.com`)**: The custom web address your guests will type in their browser.

> **Key Advantage:** Hosting on Vercel is **100% Free** forever for static sites. You only pay for the custom domain name (~$10–$14/year).

---

## 🗺️ Recommended Workflow Overview

```
1. Deploy to Vercel  ──►  2. Test Vercel Link  ──►  3. Buy Domain  ──►  4. Connect DNS  ──►  5. Live at bramanddee.com!
```

---

## 🚀 Phase 1: Deploy to Vercel First

Deploying first lets you test all site pages, images, and RSVP submissions on a temporary URL (`abram-dee-wedding.vercel.app`) before buying the domain.

### Step 1: Push Code to GitHub
1. Open terminal inside the `wedding-website` directory:
   ```bash
   cd "wedding-website"
   ```
2. Initialize Git and commit your files:
   ```bash
   git init
   git add .
   git commit -m "Initial commit of wedding website"
   ```
3. Create a new repository on [GitHub](https://github.com/new) named `abram-dee-wedding`.
4. Link and push to GitHub:
   ```bash
   git branch -M main
   git remote add origin https://github.com/YOUR_GITHUB_USERNAME/abram-dee-wedding.git
   git push -u origin main
   ```

### Step 2: Deploy Project on Vercel
1. Log into [Vercel.com](https://vercel.com/) (Sign up with your GitHub account).
2. Click **"Add New..." > "Project"**.
3. Select your `abram-dee-wedding` repository.
4. Keep default settings:
   * **Framework Preset**: Other
   * **Root Directory**: `./`
5. Click **Deploy**.
6. Within 15 seconds, your site will be live at `https://abram-dee-wedding.vercel.app`. Test the site and RSVP form to verify everything works!

---

## 🛒 Phase 2: Purchase the Custom Domain

Choose a domain registrar to purchase `bramanddee.com`.

### Recommended Registrars:
* **Porkbun** *(Recommended: Lowest renewal rates & free WHOIS privacy)*
* **Cloudflare Registrar** *(At-cost pricing with top security)*
* **Namecheap** *(Popular, includes free privacy protection)*

> **Tip:** Make sure to enable **WHOIS Privacy Protection** (usually free) during checkout so your personal registration details remain hidden.

---

## 🔗 Phase 3: Add Custom Domain in Vercel

Once `bramanddee.com` is purchased:

1. Log into your [Vercel Dashboard](https://vercel.com/dashboard).
2. Click on your `abram-dee-wedding` project.
3. Go to **Settings** $\rightarrow$ **Domains**.
4. Enter `bramanddee.com` and click **Add**.
5. Vercel will ask how you want to redirect:
   * Select **Redirect `bramanddee.com` to `www.bramanddee.com`** (or vice versa, depending on preference).
6. Vercel will display the exact **DNS Records** you need to add to your registrar.

---

## ⚙️ Phase 4: Configure DNS at Your Registrar

Log into the registrar where you bought `bramanddee.com` (e.g. Porkbun / Namecheap / Cloudflare) and open **DNS Management** or **Manage DNS**.

Add the following two records:

| Type | Host / Name | Value / Target | Description |
| :--- | :--- | :--- | :--- |
| **A Record** | `@` (or leave blank) | `76.76.21.21` | Points main domain `bramanddee.com` to Vercel |
| **CNAME Record** | `www` | `cname.vercel-dns.com` | Points `www.bramanddee.com` to Vercel |

*(Note: Vercel will confirm these exact values in your project settings screen).*

---

## 🔒 Phase 5: Verification & SSL Setup

1. Return to **Vercel Settings > Domains**.
2. Vercel will automatically verify the DNS records (usually takes **2 to 15 minutes**).
3. Once verified, Vercel automatically issues a free **SSL/TLS Certificate** for HTTPS security.
4. Visit `https://bramanddee.com` and `https://www.bramanddee.com` to celebrate! 🎉
