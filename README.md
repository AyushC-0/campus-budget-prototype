# Campus Budget — HCI prototype package

**Live Demo (GitHub Pages):** [https://ayushc-0.github.io/campus-budget-prototype/](https://ayushc-0.github.io/campus-budget-prototype/)  
**Mockup Sheet:** [https://ayushc-0.github.io/campus-budget-prototype/budget-mockups.html](https://ayushc-0.github.io/campus-budget-prototype/budget-mockups.html)

Two self-contained HTML files. No install, no build, no internet needed
(fonts fall back to system fonts when offline). Double-click to open in a browser.

-------------------------------------------------------------------------------
1. budget-app.html — the working prototype
-------------------------------------------------------------------------------
Native iPhone 17 screen: 1206 x 2622 px (402 x 874 pt, UI scaled x3 so text
stays sharp). The phone scales to fit any window. On a real phone the frame
drops away and the app fills the screen.

What the participant sees: a blank background and the phone. Nothing else.

Live behaviour
  - real typing, real validation, review screen shows what was entered
  - submitting runs a send animation, then the request moves on its own:
      ~9s  Admin Office opens it
      ~18s it reaches the Bangalore Branch
  - Withdraw is live only while the request is unopened; after that it becomes
    "Ask for a change", with the reason stated
  - an approved budget shows "Mark event as done"; tapping it moves the
    request into Bills under "Bill due" and takes you straight there
  - bill upload lists only approved requests, flags an amount that does not
    match the approval, and stays locked until the photo is added and the
    amount check is ticked
  - Help tab: stage glossary, bill rules, and demo controls
    (force the next send to fail, reset the data)

Silent session logging
  Recording starts on page load. Captured automatically:
    session start/end, screen changes, every tap with its label, field entries
    (including typed values), file attachments, checkbox toggles, and
    validation failures — each with milliseconds into the session and an
    ISO timestamp.
  Entries persist in the browser's local storage and are tagged with a
  session ID, so separate participants stay separable.

  To see or export the log:
      Ctrl/Cmd + Shift + L      or      triple-click the background
  The panel gives a live view, counts, an optional participant label, and
  JSON / CSV / Clear buttons. The CSV carries a BOM so Excel opens it cleanly.

  CSV columns:
      n, session, participant, kind, detail, extra, screen, msIntoSession, time

  Habits worth keeping:
    - set the participant label BEFORE the session starts (it is stamped on
      entries as they are written)
    - export after each participant
    - the log lives in one browser, so run all sessions on the same machine

-------------------------------------------------------------------------------
2. budget-mockups.html — the mockup sheet
-------------------------------------------------------------------------------
All 19 screen states in device frames at 1x, grouped by flow:
  Main surfaces · Making a request · Tracking and outcomes · Claiming the money
Each frame is captioned with the design decision it demonstrates.

Generated from the prototype's own view code, so the mockups and the working
app can never drift apart. Screenshot this for the Behance case study and the
slide deck.

-------------------------------------------------------------------------------
Design fixes carried in from the UT-2 heuristic review
-------------------------------------------------------------------------------
  - one status vocabulary (Draft / Not sent / In review / Returned / Approved),
    glossed on the Help screen
  - filled progress dots only ever mean finished
  - the withdraw rule is stated, then actually enforced
  - a failed send is clearly separated from a rejection
  - the bill check gates the upload instead of failing after it
  - added the missing Requests list and the Approved state
  - rejection reasons match the rules the app enforces
