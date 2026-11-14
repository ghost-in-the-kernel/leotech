<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-21: The site's own scripts throw 1 error on 41 pages

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** An error nothing catches stops the script that threw it: whatever it was doing (a form's checks, a cart, tracking) is left undone. Visitors never report it; it is seen only in the browser's console.

**Likely fix:** Open the page with the browser's developer tools, read the console, and fix each error where its stack points.

**Where:**

- https://leotechnologies.com/privacy-policy/: Cannot read properties of null (reading 'querySelector'), on every page but /, /about/

## Items expected open

- `SITE-21-73f63229` `Cannot read properties of null (reading 'querySelector')`: is thrown by the site's own scripts (on 41 pages) (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
