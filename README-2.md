# Boyd House Shared-Living Survey

A two-person survey to react to Rex's first floor plans for 1017 (RLJ Design A1.0, client review 9/24/26), and to capture how we plan to live together so the design reflects it. 83 questions in 16 short sections, about 25 minutes.

## What's in here

| File | What it does |
|---|---|
| `index.html` | The survey. Saves progress on your device as you go. |
| `compare.html` | Load both answer files and see matches, gaps, and what to talk through before sending feedback to Rex. |
| `config.js` | Where the Google Sheet link goes (one line). |
| `plan-first-floor.png`, `plan-basement.png` | Rex's floor plans, shown inside the survey. |
| `google-apps-script.gs` | Goes into the "Boyd Brother Survey" sheet, not GitHub. |

## Put it on GitHub Pages

1. On GitHub, click **New repository**. Name it something like `house-survey`.
2. Click **Add file → Upload files**, drag in `index.html`, `compare.html`, `config.js`, both `plan-*.png` files, and this README, then **Commit changes**.
3. Go to **Settings → Pages**. Set Source to **Deploy from a branch**, Branch **main**, folder **/ (root)**, then **Save**.
4. Wait a minute or two. Your link will be `https://<your-username>.github.io/house-survey/`.
5. Send that link to your brother.

## Connect the Google Sheet

Do this once, before either of you starts the survey.

1. Open the **Boyd Brother Survey** sheet.
2. **Extensions → Apps Script.** Delete what's in the editor and paste in all of `google-apps-script.gs`.
3. On the `ACCESS_KEY` line, replace `CHANGE-ME` with a passcode you'll share only with your brother. Click **Save**.
4. **Deploy → New deployment.** Click the gear icon and choose **Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy**. Google will ask you to authorize — choose your account, then **Advanced → Go to (project) → Allow**. This is Google's standard warning for personal scripts.
6. Copy the **Web app URL** (ends in `/exec`).
7. In your GitHub repo, open `config.js`, click the pencil to edit, paste the URL between the quotes, and **Commit changes**.

The sheet gets two tabs on the first submission:
- **Responses:** one row per question, one column per person, so your answers sit side by side.
- **Raw:** the full data the compare page reads.

If you change the script later, use **Deploy → Manage deployments → Edit → New version**. That keeps the same URL.

## How the two of you use it

1. Each person fills it out on their own — no peeking — and taps **Submit**. Answers go straight to the sheet.
2. Once you've both submitted, open `.../house-survey/compare.html`, enter the passcode, and tap **Load answers**.
3. Filter to **Gaps** and **To discuss**. That's the agenda for your sit-down. Once you've agreed, use **Print / save as PDF** and the "Feedback for Rex" answers to write up one consolidated response for him.

If you resubmit, the compare page uses each person's latest submission, and the Responses tab gets a new column. If the sheet ever isn't reachable, **Download my answers** on the last screen still works, and the compare page can load those files instead.

## Editing questions

Questions live in the `SECTIONS` list in `index.html`. Types:

- `radio` — pick one (add `other:true` for a write-in)
- `checkbox` — pick any (add `max:2` to cap it)
- `scale` — 1–5 importance
- `grid` — rate several `rows` 1–5
- `rank` — put `options` in order
- `pair` — forced A/B choice
- `text`, `textarea` — open answers

Add `note:'...'` to show plan context under a question. Keep each `id` unique, and don't change questions after either of you has started, or the compare page won't line up.

## Privacy

GitHub Pages sites are public, so anyone with the link can see the questions and the floor plan images. The images are cropped to the drawings only — no address, title block, or architect's seal. Answers are never stored on GitHub. They go to your Google Sheet, which stays private to you. The compare page can only read them with the passcode, and the passcode lives in the Apps Script, not in the public GitHub files. Search engines are told not to index the pages.
