# Publish the LE 2 dashboard on GitHub Pages (locked build)

These seven files are safe to put on a **public** GitHub Pages site: every figure, project name
and register line is AES-256 encrypted inside `index.html`, and the page shows a lock screen until
the passphrase is entered. The passphrase is **not** in this folder — Atif holds it.

## One-time setup (about 5 minutes)

1. **Do not reuse the `GECO-Dashboard` repository.** It already holds an *unencrypted* copy of the
   dashboard from the first upload, and a public repository shows its whole history. Delete it
   (repository → Settings → General → scroll to the bottom → *Delete this repository*) or leave it
   private and unused.
2. On GitHub click **New** → name it e.g. `le2-dashboard` → **Public** → *Create repository*.
3. Click **uploading an existing file** and drag in all seven files from this folder
   (`index.html`, `manifest.webmanifest`, `sw.js`, the four `icon-*.png`). *Commit changes*.
4. Repository **Settings** → left sidebar **Pages** (in the *Code, planning, and automation*
   group) → under *Build and deployment*, Source **Deploy from a branch** → Branch **main**,
   folder **/ (root)** → **Save**.
5. Wait one to two minutes, refresh; the address appears at the top:
   `https://<your-username>.github.io/le2-dashboard/`

## On the phone

Open the address in **Samsung Internet, Chrome or Edge** (not inside another app). Enter the
passphrase once and leave *Remember on this device* ticked. Then tap **Add to Home Screen** in the
dashboard header (or the browser menu → *Add page to* / *Add to Home screen* / *Install app*).
The icon is the navy **LE2** tile, named "LE 2"; it opens full-screen and works offline.

## Updating the figures later

Rebuild `index.html` with `build_locked.py` (in `Mobile dashboard\`) and upload it over the old
one; bump `CACHE` in `sw.js` at the same time so installed phones pick up the new build. The
passphrase stays the same unless you choose a new one.

## Changing or revoking access

The only key is the passphrase. To lock everyone out, rebuild with a new passphrase and re-upload;
people who had the old one see the lock screen again. Anyone can download the encrypted file, so
the protection is only as strong as the passphrase — keep the generated one (three blocks of four
characters) and share it person to person, not in the same message as the link.
