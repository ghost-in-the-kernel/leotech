<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-29: The site publishes no security.txt, the file that tells security researchers whom to contact

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** Researchers who find a security problem look for /.well-known/security.txt to know whom to tell (RFC 9116); without it they may not report it, or report it publicly.

**Likely fix:** Publish /.well-known/security.txt with a Contact line (an email address or a form) and an Expires line.

**Where:**

- https://leotechnologies.com/.well-known/security.txt: answered 404

## Items expected open

- `SITE-29-8802ab17` security.txt: answers 404 (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
