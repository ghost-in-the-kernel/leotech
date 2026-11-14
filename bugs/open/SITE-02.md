<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-02: 1 broken link: the site links to an address that answers an error

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** A visitor who follows one of these links reaches an error instead of the page promised.

**Likely fix:** Point each link at a page that exists, or bring the page back (or redirect its old address to where it went).

**Where:**

- https://leotechnologies.com/leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/: answered 404; linked from /verus-featured-in-sheriff-deputy-magazine/

## Items expected open

- `SITE-02-246d4ad1` /leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/: answers 404 (linked from /verus-featured-in-sheriff-deputy-magazine/) (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
