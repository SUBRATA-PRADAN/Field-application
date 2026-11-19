# PRADAN Field Application

A lightweight, mobile-first web app that gives PRADAN field teams **one-tap access** to the Survey123 and AppSheet data-collection tools, and to the dashboards, reports and story maps built by the GIS & MEL team.

It is a single static web page. There is no backend, no database and no build step, so it is easy to host and easy to update.

**Live link:** https://SUBRATA-PRADAN.github.io/Field-application/

---

## What it does

The app has two tabs and an **EN / हिं** language switch in the header.

### 1. Field Forms (for field surveyors)

- **AppSheet:** Agriculture, Livestock and Fishery modules. Each opens the AppSheet app directly on the phone.
- **Survey123:**
  - Shows the surveys currently available: Onboarding, Training, NRM Structure, Livelihood (Direct Action Team), Livelihood (Partnership) and Asset Listing.
  - The **Open Survey123** button opens the Survey123 app through the organisation portal. If the app is not installed, the user is sent to the Play Store (Android) or App Store (iOS).
  - A collapsible step-by-step guide explains first-time setup: log in with ArcGIS Enterprise, open the profile, choose *Download Survey*, download the survey needed, then fill and sync.

### 2. Data & Reports (for supervisors and MIS use)

These links open in the browser, in a new tab.

- **All-in-One Dashboard:** PRADAN MIS Dashboard
- **AppSheet:** browser versions of the modules and the Livestock dashboard
- **Survey123:** data-download dashboards for each survey
- **Dashboards:** Kotak, One Map Rajasthan, Lasadiya and SRDC GPDP (FY 2024-25)
- **Award-Winning Story Maps:** four ArcGIS StoryMaps

Some links need a login. This is shown under the link name:

| Link | Login needed |
|---|---|
| Kotak Dashboard | ArcGIS Online |
| One Map Rajasthan | ArcGIS Enterprise |

### Other features

- Hindi and English for all labels, and the chosen language is remembered
- The last opened tab is remembered
- A copy-link button on every row, to share links over WhatsApp
- Can be added to the phone home screen and opens like an app

---

## Files in this repo

All files must stay together in the **root** of the repo (not inside a sub-folder).

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML, CSS, JavaScript). All logos are embedded in this file. |
| `manifest.json` | Home-screen app name, colours and icons |
| `favicon.ico`, `favicon-16x16.png`, `favicon-32x32.png` | Browser tab icons |
| `apple-touch-icon.png` | Home-screen icon on iPhone |
| `icon-192.png`, `icon-512.png` | Home-screen icons on Android |

---

## Deploying with GitHub Pages

1. Create a **public** repository and upload all the files above to its root.
2. Go to **Settings → Pages**.
3. Under *Branch*, select `main` and the `/ (root)` folder, then click **Save**.
4. After 1–2 minutes the live link appears at the top of the Pages screen. Share this single link.

Any later change committed to `index.html` goes live at the same link in about 1–2 minutes. Users only need to refresh the page.

---

## How to add or change a link

Open `index.html` on GitHub, click the pencil (✏️) icon and press `Ctrl+F` to find the list below. Add one line at the end of the list, just before the closing `];`. Then click **Commit changes**.

| Where it appears | Search for | Icon to use |
|---|---|---|
| Data & Reports → Dashboards | `dashboardsData` | `chart` |
| Data & Reports → Story Maps | `storymapsData` | `map` |
| Data & Reports → AppSheet | `appsheetData` | none |
| Data & Reports → Survey123 | `survey123Data` | none |
| Data & Reports → All-in-One Dashboard | `allInOneDashboard` | uses a logo image |
| Field Forms → Survey123 names | `survey123Forms` | `flag`, `book`, `tree`, `clipboard`, `list` |

**Example: adding a dashboard**

```js
{ nameEn:'Dashboard Name', nameHi:'हिंदी नाम', url:'https://example.com/dashboard', icon:'chart' },
```

**Example: with a note under the name (such as a login requirement or year)**

```js
{ nameEn:'Dashboard Name', nameHi:'हिंदी नाम', url:'https://example.com/dashboard', icon:'chart', subEn:'Needs an ArcGIS Online login', subHi:'इसके लिए ArcGIS Online का लॉगिन चाहिए' },
```

**Rules to avoid breaking the page**

- Every line ends with a comma `,`
- All text is inside single quotes `' '`. If a name contains an apostrophe, write `\'` (for example `Women\'s`)
- Do not delete or edit the surrounding lines or the closing `];`
- Always add both `nameEn` and `nameHi`

If the page goes blank after an edit, the usual cause is a missing comma or quote. Undo the last commit from the repo history and try again.

---

## Adding the app to the phone home screen

- **Android (Chrome):** open the live link, tap the ⋮ menu and choose **Add to Home screen** (or **Install app**).
- **iPhone (Safari):** open the live link, tap **Share** and choose **Add to Home Screen**.

---

## Notes

- **Do not put passwords or private data in this repo.** The repo is public and stores only links. Users sign in on the destination site or app.
- **Survey123 opening:** the app uses the `arcgis-survey123://` link together with the organisation portal address. Users must have the ArcGIS Survey123 app installed and signed in once with the login shared for their team.
- **Portal:** https://gisinnovations.pradan.in/portal/

## Tech

Plain HTML, CSS and JavaScript in a single file. There is no framework, no build tooling and no server.

## Maintained by

GIS & MEL Innovations, Jaipur
