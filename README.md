What is this?
BracketMaker lets you build tournament brackets in seconds — single or double elimination, up to 64 teams. Click to advance winners, drag to rearrange matchups, track scores, and share the entire bracket as a single URL. Everything runs in the browser with zero setup.
Built for esports organizers, sports clubs, office pools, or anyone who needs to run a bracket fast without setting up an account or paying for software.

Features
🎮 Single & Double EliminationFull losers bracket with correct drop-down logic👆 Click to advanceClick a team name to declare the winner — they propagate automatically🖱️ Drag & dropSwap teams or entire match cards within a round🔢 Score trackingEnter scores per match — saved in the bracket state↺ UndoUp to 40 steps of history🔗 Shareable URLFull bracket state encoded in the URL hash — just paste and share📥 Download offlineOne-click download of a standalone BracketMaker.html❓ Interactive guideStep-by-step spotlight tour covering every feature✈️ Works offlineZero CDN requests, zero npm packages, zero build tools

Quick Start
Option A — Just use the file

Download BracketMaker.html from Releases
Double-click it — opens in any browser
Done. No install, no internet needed.

Option B — GitHub Pages (hosted)

Fork or clone this repo
Go to Settings → Pages → Source → main branch / root
Your bracket is live at https://<username>.github.io/<repo>/

Option C — Run locally
bashgit clone https://github.com/yourusername/bracketmaker.git
cd bracketmaker
# Open index.html in your browser — or serve it:
npx serve .

How to Use
1. Setup
Fill in the form on the right side of the screen:

Tournament Name — shown in the header and in exports (optional)
Format — Single Elimination (one loss = out) or Double Elimination (losers get a second chance)
Seeding — keep teams in the order you entered them, or randomize the draw
Teams — one name per line, up to 64. Duplicates are removed. Byes are inserted automatically if needed.

Click Create Bracket when ready.
2. Making Predictions
What you want to doHowAdvance a winnerClick the team's name inside a match cardEnter a match scoreClick the small number box on the right of a team rowSwap two teamsDrag one team slot onto anotherSwap two matchupsDrag an entire match card onto another in the same roundPlace a team (mobile)Tap a team in the sidebar (it turns gold), then tap a bracket slot
3. Toolbar Buttons
ButtonWhat it does? GuideOpens the interactive step-by-step spotlight tour✎ EditReturns to the setup screen without losing your bracket↺ UndoReverses your last action (up to 40 steps)⟳ ResetClears all winners and scores — asks for confirmation first⤢ FitScales the bracket to fit your current window↓ ExportDownloads a snapshot of the current bracket as a standalone HTML file⤤ ShareCopies a URL with the full bracket state encoded — anyone who opens it sees your exact bracket
4. Download Offline App
On the setup screen, click ↓ Download Offline App to get a single BracketMaker.html file you can use anywhere — no internet, no browser extensions, no accounts.

Project Structure
bracketmaker/
├── index.html            # App shell — markup only
├── BracketMaker.html     # Single-file offline build (all CSS + JS inlined)
├── css/
│   ├── base.css          # Design tokens, reset, buttons, forms, toasts, modal
│   ├── layout.css        # Topbar, setup screen, sidebar, canvas
│   ├── bracket.css       # Match cards, participants, champion display
│   └── guide.css         # Guided tour overlay, spotlight, tooltip
├── js/
│   ├── utils.js          # Shared helpers ($, mk, toast, confirm, drag utils)
│   ├── bracket.js        # All bracket logic and rendering (IIFE)
│   ├── guide.js          # Spotlight tour system (IIFE)
│   ├── download.js       # Offline bundle generator
│   └── main.js           # Event wiring and app bootstrap
├── README.md
└── LICENSE
The multi-file structure is for development. The BracketMaker.html file is the production build — all CSS and JS inlined into one file, safe to use from file:// without a server.

Browser Support
Works in any modern browser — no transpilation or polyfills needed:
BrowserMinimum versionChrome / Edge60+Firefox60+Safari12+Opera47+

Double Elimination — How it Works
When a team loses in the Winners Bracket, they drop to the corresponding round of the Losers Bracket automatically. The round mapping is:

WB Round 1 losers → LB Round 1
WB Round 2 losers → LB Round 3
WB Round N losers → LB Round (2N − 1)

The winner of the Losers Bracket meets the Winners Bracket champion in the Grand Finals.

FAQ
Does it work without internet?
Yes. Download BracketMaker.html and open it anywhere. It loads no external resources.
Is there a limit on teams?
64 teams maximum. Byes are inserted automatically if the count isn't a power of 2 (e.g. 6 teams → 8-slot bracket with 2 byes).
Are brackets saved automatically?
Not to disk — but the Share button encodes the entire bracket into the URL. Bookmark or copy that URL to come back to it later.
Can I use this for commercial events?
Yes — it's MIT licensed. Use it however you want.

License
MIT — see LICENSE for the full text.
Copyright © 2026 Julleven Mendoza
