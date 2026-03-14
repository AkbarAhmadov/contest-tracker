# ⚡ CF Contest Tracker

A single-file HTML tool that takes a list of Codeforces usernames from a CSV and shows every contest where **none of them got any Accepted submission**.

---

## 📋 What It Does

1. You upload a CSV file containing Codeforces usernames (one per row, first column).
2. The tool fetches all submissions for each user via the Codeforces public API.
3. It collects every contest any of them participated in.
4. It filters out contests where at least one user got an AC.
5. The remaining contests — where **everyone failed to get an AC** — are displayed in a sortable, searchable table.

---

## 🚀 How to Use

1. **Open** `cf-contest-tracker.html` in any modern browser (Chrome, Firefox, Edge).
2. **Upload** your CSV file by dragging and dropping it onto the upload zone, or clicking to browse.
3. Click **▶ Run Analysis**.
4. Wait while the tool fetches data from Codeforces (a progress bar and live log track the process).
5. View the results table once the analysis is complete.

> No server, no installation, no dependencies — everything runs in your browser.

---

## 📁 CSV Format

The first column of each row must be a Codeforces username. Extra columns are ignored. A header row is automatically detected and skipped.

**Examples:**

Simple list:
```
tourist
jiangly
Um_nik
Benq
```

With extra columns (ignored):
```
username,country,rank
tourist,Romania,legendary grandmaster
jiangly,China,legendary grandmaster
```

---

## 📊 Results Table

| Column | Description |
|---|---|
| **Contest ID** | Codeforces contest ID (links to the contest page) |
| **Contest Name** | Full contest name fetched from the CF API |
| **Type** | Contest type (CF, ICPC, etc.) |
| **Participants** | How many users from your list participated |
| **Who Participated** | Clickable username tags linking to each user's CF profile |

- Click any **column header** to sort ascending/descending.
- Use the **search box** to filter by contest name, ID, or username.

---

## 📈 Stats Panel

After the analysis completes, a summary panel shows:

- **Users** — number of usernames processed
- **Zero-AC Contests** — contests where nobody got an AC (the main result)
- **Total Contests** — all contests the users participated in (for context)
- **Failed** — usernames that couldn't be fetched (invalid handle, API error, etc.)

---

## ⚙️ Technical Details

- **API used:** [Codeforces Public API](https://codeforces.com/apiHelp)
  - `user.status` — fetches all submissions for a user
  - `contest.list` — resolves contest names and types
- **Rate limiting:** 300ms delay between user requests to respect Codeforces API limits (~5 req/s).
- **No backend:** Entirely client-side HTML + JavaScript. Nothing is sent anywhere except the Codeforces API.
- **Submissions fetched:** Up to 10,000 most recent submissions per user.

---

## ⚠️ Notes & Limitations

- **Private/deleted contests** may not have their names resolved (shown as `Contest #ID`).
- **Gym contests** are excluded from the contest list lookup.
- Codeforces API may be slow or temporarily unavailable — the log panel will show any errors.
- Users with very large submission histories (10,000+) may have older contests missing from results.
- The tool requires an internet connection to reach the Codeforces API.

---

## 🛠️ No Installation Required

Just open the HTML file in a browser. No Node.js, no Python, no build step.

```
cf-contest-tracker.html   ← open this
README.md                 ← you are here
```
