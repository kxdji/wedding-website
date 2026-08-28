# Abram & Danielle Wedding Website — Beginner's Guide

Congratulations on your upcoming wedding! This guide explains how to manage, edit, collect RSVPs, and deploy your wedding website with zero prior coding experience required.

---

## 📁 Project Files Overview

All your project files are located in your workspace directory:
- **`index.html`**: The main wedding website file containing structure, styling, interactive gallery lightbox, and multi-guest RSVP form logic.
- **`Title.png`**: Couple monogram / calligraphy title in the Hero header.
- **`Home (1).png`, `Home (2).png`, `Home (3).png`**: Proposal photos for the **Our Story** section.
- **`gallery-1.jpg` ... `gallery-6.jpg`**: Photos for the **Gallery** section.
- **`gcash-qr.png`**: Payment/Gift QR code image for **A Note on Gifts**.
- **`wedding-qr.png`**: High-resolution printable QR code pointing to your live Vercel website.

---

## 📊 Step 1: Setting Up Google Sheets for RSVP Form Responses

To receive guest RSVPs (including multiple named guests and dietary restrictions) directly into a Google Sheet:

1. **Create a Google Sheet**:
   - Go to [Google Sheets](https://sheets.google.com) and create a new blank spreadsheet titled `Abram & Danielle Wedding RSVPs`.
   - In Row 1, add these exact column headers:
     `Timestamp` | `Name` | `Attending` | `Guests` | `Additional_Guests` | `Allergies` | `Song_Note`

2. **Open Google Apps Script**:
   - In your Google Sheet, click **Extensions** > **Apps Script**.
   - Delete any code in the editor and paste the following code:

```javascript
function doPost(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    var name = e.parameter.Name || '';
    var attending = e.parameter.Attending || '';
    var guests = e.parameter.Guests || '';
    var additionalGuests = e.parameter.Additional_Guests || '';
    var allergies = e.parameter.Allergies || '';
    var songNote = e.parameter.Song_Note || '';
    var timestamp = new Date();

    sheet.appendRow([timestamp, name, attending, guests, additionalGuests, allergies, songNote]);

    return ContentService.createTextOutput(JSON.stringify({ "result": "success" }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (err) {
    return ContentService.createTextOutput(JSON.stringify({ "result": "error", "error": err.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

3. **Deploy as Web App**:
   - Click the blue **Deploy** button (top right) > **New deployment**.
   - Click the gear icon ⚙️ next to "Select type" and choose **Web app**.
   - Description: `Wedding RSVP Web App`
   - Execute as: **Me** (`your-email@gmail.com`)
   - Who has access: **Anyone** *(Crucial so guests can submit without signing in)*
   - Click **Deploy**, authorize permissions when prompted, and **copy your Web App URL**.

4. **Paste Web App URL into `index.html`**:
   - Open `index.html`.
   - Near line 620, locate:
     ```javascript
     const GOOGLE_WEB_APP_URL = '...';
     ```
   - Paste your copied Google Web App URL!

---

## 🚀 Step 2: Free Deployment on Vercel

Vercel provides free, reliable hosting with instant global performance.

### Option A: Via Vercel Website (Drag & Drop / GitHub) - Recommended
1. Create a free account at [Vercel.com](https://vercel.com).
2. Click **Add New...** > **Project**.
3. If using GitHub, upload your `wedding-website` folder to a GitHub repository and import it into Vercel.
4. Set Project Name to `abram-and-danielle` (or your preferred name).
5. Click **Deploy**! Your site will be live at `https://abram-and-danielle.vercel.app`.

### Option B: Via Terminal / Vercel CLI
If you have Vercel CLI installed:
1. Open PowerShell / Command Prompt in your project folder `wedding-website`.
2. Run command: `vercel`
3. Follow the prompts to publish directly!

---

## 📱 Step 3: Permanent QR Code & Error Prevention

> [!IMPORTANT]
> **Why your printed QR Code will NEVER break**:
> Your printable QR code (`wedding-qr.png`) points to your fixed Vercel domain URL (`https://abram-and-danielle.vercel.app`).
> If you ever make typo fixes, update photos, or change bank account numbers in `index.html`, simply push the updated `index.html` to Vercel. Vercel automatically updates the live website under the exact same URL instantly. **You never need to re-print your physical QR codes!**

---

## ✏️ Step 4: How to Edit Details in `index.html`

- **Dee's Contact Info**: Search for `otrp@gmail.com` or `09773544809` in `index.html` to update contact details.
- **Bank Account Details**: Search for `bank-info` in `index.html` to update your account numbers or names.
- **Photos**: Drop replacement photos with names `Home (1).png` to `Home (3).png`, `gallery-1.jpg` through `gallery-6.jpg`, `Title.png`, and `gcash-qr.png`.
