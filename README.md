# Migraine Log

A one-tap migraine tracker for your phone. Tap the button, the migraine is recorded.
Everything else — which painkiller, what might have set it off — is optional and can be
filled in later, or never.

It's a single static page: no accounts, no server, no build step. Entries are stored in
your browser's local storage and never leave the device.

## Setting it up

1. **Turn on GitHub Pages** — repo *Settings → Pages → Build and deployment*, source
   *Deploy from a branch*, branch `main` (or whichever branch holds this), folder `/ (root)`.
   Give it a minute, then it's live at `https://<your-username>.github.io/tracker/`.

   > Pages only serves **private** repos on a paid GitHub plan. On the free plan the repo
   > has to be public — which is fine here: the code contains no personal data, and your
   > migraine entries never go near the repo. They stay in your phone's browser storage.
   > If you'd rather keep it private, any static host works instead (Netlify, Cloudflare
   > Pages, Vercel) — point it at this repo, no build command, publish directory `/`.
2. **Open that URL on your phone.**
3. **Add it to your home screen** so it opens like an app and works offline:
   - iOS Safari: Share → *Add to Home Screen*
   - Android Chrome: ⋮ menu → *Add to Home screen* / *Install app*

## Using it

- **Tap the big button.** That's the whole required interaction — it records the current
  time immediately. If it was a mis-tap, *Undo* is right there.
- **Optional details.** The new entry opens with three medication chips (Acetaminophen,
  Ibuprofen, Nothing) and a free-text note. Tap a selected chip again to clear it.
- **Wrong time?** If you're logging after the fact, edit the *When* field on the entry —
  the list re-sorts itself.
- **Later edits.** Tap any past entry to expand and change it, or delete it.

The line under the title shows when the last one was and how many you've had in the last
30 days.

## Getting your data out

`Export CSV` for spreadsheets or a doctor's appointment, `Export JSON` for a full backup,
`Copy JSON` when you'd rather paste it somewhere. `Import JSON` merges a backup back in —
it skips entries already present, so re-importing the same file is harmless, and it's also
how you move history to a new phone.

Worth exporting occasionally: clearing your browser data would otherwise take the log with it.

## Offline

A service worker caches the page, so it loads and records entries with no connection —
which matters, since a migraine starting is not the moment to argue with a bad signal.
When you do change the code, bump `CACHE` in `sw.js` so installed copies pick up the update.

## Files

| File | |
|---|---|
| `index.html` | The whole app — markup, styles and logic |
| `sw.js` | Service worker for offline use |
| `manifest.webmanifest` | Makes it installable as an app |
| `icons/` | Home-screen icons |
