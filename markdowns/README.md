## Project Structure

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

---
## Update 

1. git checkout -b feature-name (Make your new branch)
2. Do your coding...
3. git add . && git commit -m "Add new feature"
4. git checkout main
5. git merge feature-name
6. git push origin main

---

## RSVP & Google Sheets Integration
RSVP submissions are posted automatically to your Google Apps Script Web App endpoint.
The spreadsheet columns collected:
- `Timestamp`
- `Name`
- `Attending` (*Joyfully Accepts* / *Regretfully Declines*)
- `Guests` (Total count)
- `Additional_Guests` (Formatted breakdown of names & dietary requirements)
- `Allergies`
- `Song_Note`
