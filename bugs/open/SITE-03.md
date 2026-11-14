<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-03: 4 of the site's own links redirect before they arrive

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** Every click on one of these links costs an extra round trip before the page starts loading, and search engines see one page at two addresses.

**Likely fix:** Link to each page's final address (with or without its trailing slash, as the server serves it).

**Where:**

- https://leotechnologies.com/dir: 301 to /dir/
- https://leotechnologies.com/verus-ai-new/: 301 to /verus-ai/
- https://leotechnologies.com/news-resources/leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/: 301 to /leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/
- https://leotechnologies.com/verus/: 301 to /verus-ai/

## Items expected open

- `SITE-03-065a542b` /aws-partner: redirects (301) to https://leotechnologies.com/partners/aws-partner/ (since 2026-11-14)
- `SITE-03-26f8b2d7` /verus/: redirects (301) to https://leotechnologies.com/verus-ai/ (since 2026-11-14)
- `SITE-03-2abc9114` /dir: redirects (301) to https://leotechnologies.com/dir/ (since 2026-11-14)
- `SITE-03-a0239013` /news-resources/leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/: redirects (301) to https://leotechnologies.com/leo-technologies-partners-with-deliverfund-to-fight-human-trafficking/ (since 2026-11-14)
- `SITE-03-ee7395be` /verus-ai-new/: redirects (301) to https://leotechnologies.com/verus-ai/ (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
