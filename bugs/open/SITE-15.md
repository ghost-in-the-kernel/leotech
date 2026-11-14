<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-15: 3 pages have no main heading

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** Screen reader users jump to the h1 to learn what a page is, and search engines read it as the page's subject; none, or several competing, says neither.

**Likely fix:** Give each page one h1 naming what it shows; the site's name in the header is not it.

**Where:**

- https://leotechnologies.com/dir/: no h1 with words shown
- https://leotechnologies.com/dir-cpo-6149/: no h1 with words shown
- https://leotechnologies.com/partners/aws-partner/: no h1 with words shown

## Items expected open

- `SITE-15-a19bb9f5` /dir-cpo-6149/: has no main heading (h1) with words (since 2026-11-14)
- `SITE-15-d36c51a4` /partners/aws-partner/: has no main heading (h1) with words (since 2026-11-14)
- `SITE-15-f314781b` /dir/: has no main heading (h1) with words (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
