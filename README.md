# QuizForge PH

A free, DepEd-aligned flashcard quiz and mastery app. It is one static file (`index.html`), so it runs on GitHub Pages with no server, build step or database.

## 1. Publish on GitHub Pages
1. Sign in at github.com and click **New repository**. Name it (for example `quizforge`), choose **Public**, and click **Create repository**.
2. Click **Add file → Upload files** and drag in `index.html`, `README.md` and `.nojekyll` (the empty file that skips Jekyll). Click **Commit changes** to the `main` branch.
3. Open **Settings → Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, **Branch** to `main`, folder to `/ (root)`, then **Save**.
4. After about a minute your app is live at `https://<username>.github.io/<repo-name>/`.

## 2. Optional: Gemini AI card extraction
1. Open Google AI Studio and create a free API key.
2. In the app, open **Settings**, paste the key under **Gemini API key**, and **Save**. The key stays in your browser.
Without a key, the built-in offline parser still reads `Term - Definition`, `Term: Definition`, `**Term**: Definition`, tab-separated lines, "X is defined as Y" sentences, and `Learning Competency:` lines.

## 3. Optional: Google Drive Picker (OAuth)
1. In Google Cloud Console, create a project and enable the **Google Drive API** and **Google Picker API**.
2. Configure the **OAuth consent screen**, then create an **OAuth client ID** of type **Web application**.
3. Under **Authorized JavaScript origins**, add `https://<username>.github.io` (no repo name, no trailing slash). In the app, **Settings → Copy Origin URL for Google Cloud OAuth** copies the exact value.
4. Create an **API key** and restrict it to the HTTP referrer `https://<username>.github.io/*`.
5. In **Settings**, paste the Client ID, API key and App ID (your project number), then **Save**. Use **Pick a file from Google Drive** on the Import screen.

## 4. Using the app
- **Import:** paste notes, link a public Google Sheet/Doc, YouTube or article, or drop CSV, XLSX, JSON, TXT, MD, RTF, DOCX, PDF, PPTX and image files. Facebook and some sites block automatic reading, so paste the text instead.
- **Study Studio:** edit cards, set Quarter, Learning Competency and Cognitive Process, export JSON/CSV, or copy a **Share quiz link** (the deck is compressed into the URL, so very large decks need the JSON file instead).
- **Quiz:** Multiple Choice, Written (Apple Pencil Scribble and S Pen friendly), True/False, Matching. Choose **Formative** (hints and feedback) or **Summative** (no hints).
- **Grades:** the result shows raw score, percentage score and the transmuted grade from the DepEd Order No. 8, s. 2015 table (60.00–61.59% = 75, 100% = 100, 0–3.99% = 60) with its descriptor. A grade below 75 requires the Mastery &amp; Remediation Round.
- **Mastery:** each card moves Unseen → Learning → Familiar → Mastered. Mastered means answered correctly in at least two different formats; a miss sends the card back to Learning. Repeat the round until every card is Mastered.
- **Report:** **Export Item Analysis CSV** gives per-item attempts, difficulty index and mastery state.

## 5. Saving and sharing a deck
All of these are in the **Study Studio** screen:
- **Export JSON:** a full backup you can reload later (Import → drop the file).
- **Export CSV:** a spreadsheet file for Excel or Google Sheets; also reloadable.
- **Share quiz link:** copies (or shares) a link that carries the deck. Big decks are split into several links; each link adds its cards to the classmate's deck.
- **Copy as text:** copies `Term - Definition` lines to paste into chats, documents or Import.
- **Copy for Google Sheets:** copies tab-separated cells; open a Sheet, click A1 and paste.
- **Save to Google Sheets:** creates a Sheet in your Drive (needs the Google Client ID from step 3). Set its sharing to "Anyone with the link", then classmates paste the link into Import.
- **Print:** prints the deck as a table (or save it as PDF).

## Privacy
Decks, settings and keys are stored only in your browser (`localStorage`). Nothing is sent anywhere except the services you choose to use (Gemini, Google Drive, link fetching).
