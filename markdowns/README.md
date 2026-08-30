# Abram & Danielle — Wedding Website

A clean, modern, and responsive wedding website for Abram & Danielle (January 7, 2027 · The Abba's Orchard, Cagayan de Oro City).

---

## 📁 Project Structure

```text
wedding-website/
├── index.html                  # Main website markup & script logic
├── css/
│   ├── variables.css           # Design tokens, color schemes & global variables
│   ├── reset.css               # CSS reset & base typography settings
│   ├── layout.css              # Containers, grid system & global section structures
│   ├── components.css          # Nav, cards, buttons, modals & reusable components
│   ├── sections.css            # Section-specific styles (Hero, Story, RSVP, Gallery, etc.)
│   └── style.css               # Central stylesheet importing all modular CSS files
└── images/
    ├── Title.png               # Monogram / Hero title graphic
    ├── Home (1).png            # Story photo 1 (Proposal photo)
    ├── Home (2).png            # Story photo 2 (Proposal photo)
    ├── Home (3).png            # Story photo 3 (Proposal photo)
    ├── gcash-qr.png            # Gifts contribution QR code
    ├── gallery-1.jpg           # Gallery photo 1
    ├── gallery-2.jpg           # Gallery photo 2
    ├── gallery-3.jpg           # Gallery photo 3
    ├── gallery-4.jpg           # Gallery photo 4
    ├── gallery-5.jpg           # Gallery photo 5
    ├── gallery-6.jpg           # Gallery photo 6
    ├── gallery-7.jpg           # Gallery photo 7
    ├── gallery-8.jpg           # Gallery photo 8
    ├── gallery-9.jpg           # Gallery photo 9
    ├── gallery-10.jpg          # Gallery photo 10
    ├── gallery-11.jpg          # Gallery photo 11
    ├── gallery-12.jpg          # Gallery photo 12
    └── gallery-13.jpg          # Gallery photo 13
```

---
## 🚀 Deployment to GitHub & Vercel

### Step 1: Upload to GitHub
1. Create a new repository on [GitHub](https://github.com/new) (e.g. `abram-dee-wedding`).
2. Open terminal in the `wedding-website` folder and run:
   ```bash
   git init
   git add .
   git commit -m "Initial commit of wedding website"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/abram-dee-wedding.git
   git push -u origin main
   ```

### Step 2: Deploy on Vercel
1. Go to [Vercel](https://vercel.com/) and click **"Add New..." > "Project"**.
2. Connect your GitHub account and select the `abram-dee-wedding` repository.
3. Keep default settings (Framework Preset: **Other**, Root Directory: `./`).
4. Click **Deploy**.
5. In ~15 seconds, your wedding website is live with an SSL HTTPS link!

---

## 📝 RSVP & Google Sheets Integration
RSVP submissions are posted automatically to your Google Apps Script Web App endpoint.
The spreadsheet columns collected:
- `Timestamp`
- `Name`
- `Attending` (*Joyfully Accepts* / *Regretfully Declines*)
- `Guests` (Total count)
- `Additional_Guests` (Formatted breakdown of names & dietary requirements)
- `Allergies`
- `Song_Note`
