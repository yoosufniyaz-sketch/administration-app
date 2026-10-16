# Administration

An all-in-one, open-source admin web app for small organisations: stock and inventory, assets, vehicles and fuel, petty cash, handovers, key registry, cleaning checklists, staff directory, leave plans, tasks, travel, utilities and department documents (EXCO papers, memos, TORs and more).

It's a single `index.html` file. There's no build step and no server code, and it installs on phones and desktops as an app (PWA).

**Live demo:** `https://<your-github-username>.github.io/<repo-name>/?demo`
The demo loads sample data that stays in your own browser. Use **Reset** in the demo banner to start over.

## Features

- **Stock**: items, stock levels per location, stock in/out, transfers, reorder alerts, reports
- **Assets**: register, transfers between locations, asset report, QR codes
- **Fleet**: vehicles, statutory documents and expiry alerts, fuel requisitions and logs, servicing, vehicle log
- **Petty cash**: requests, cash counts, statements and replenishment forms (PDF, Word, Excel)
- **Documents**: EXCO papers, memos, TORs, SOPs, staff request forms, handovers (PDF and Word)
- **People**: staff directory, business cards and ID cards (PDF), leave plan, tasks, weekly reports
- **Facilities**: key registry, cleaning checklists, utilities, admin complaints
- Light and dark themes, works offline, CSV/PDF/Word/Excel export

## Two ways to run it

### 1. Local mode (no setup)
Open `index.html` in a browser, or host the folder anywhere. Everything is saved in that browser's local storage, so it doesn't sync between devices.

### 2. Shared cloud mode (Firebase, free tier)
Use this so a whole team can share one database with sign-in.

1. Create a project at <https://console.firebase.google.com>.
2. Turn on **Authentication → Email/Password**.
3. Create a **Firestore Database** and paste in the rules from [`firestore.rules`](firestore.rules). They're a starting point, so tighten them for production.
4. Under **Project settings → Your apps**, add a Web app and copy its `firebaseConfig` object.
5. In the app, click **Enable cloud sync** and paste the config. The first person to sign up becomes the admin.

To build the config in for your organisation, set `DEFAULT_FIREBASE_CONFIG` in `index.html`. Firebase web keys aren't secret, but your Firestore rules must stop anyone who isn't signed in from reading data.

### Optional settings in `index.html`
| Setting | What it does |
|---|---|
| `REQUIRED_EMAIL_DOMAIN` | Only allow sign-ups from e.g. `yourcompany.com` (empty = any email) |
| `DEFAULT_LOCATIONS` | Starting list of sites (you can also edit these in the app) |
| `EXCO_FOOT`, handover letterhead text | Your organisation's address on generated documents |
| `BC_FRONT_SVG`, `BC_BACK_SVG`, `ID_SVG` | Business card and ID card artwork |
| Low-stock email | Set up in the app with a free [EmailJS](https://www.emailjs.com) account |

## Deploy on GitHub Pages
1. Fork or upload this repository.
2. Go to **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, then pick `main` and `/ (root)`.
3. Your app will be at `https://<username>.github.io/<repo>/`. Add `?demo` to the address for the demo.

## Contributing
Issues and pull requests are welcome. Please keep the app a single self-contained `index.html`, and test in local mode and with `?demo` before you open a PR.

## License
[MIT](LICENSE) © 2026 Yoosuf Niyaz

Bundled PDF fonts: Poppins, Carlito and Liberation Sans, all under the SIL Open Font License.
