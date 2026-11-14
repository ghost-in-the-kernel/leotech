<!-- Filed by Suite Builder: a system bug. To close it yourself, move this file to bugs/closed/. -->
# SITE-24: 4 security headers no page sends

Filed from the crawl of 2026-11-14, by Suite Builder: a finding about the site, not the suite (KNOWN-ISSUES.md has it in full).

**What it blocks:** No test of the regular run trips on it: the audit tests re-check each item.

**Why it matters:** Each header closes off one way the site could be misused (a downgrade to http, a script slipped in, the site framed in another to trick a click). A missing one is a weaker defence, not a sign the site has been attacked; security reviews ask for them, and each costs a line of server configuration.

**Likely fix:** Add the missing headers in the web server or the CDN (one setting each), starting with Strict-Transport-Security.

**Where:**

- https://leotechnologies.com/: no page of the site sends Strict-Transport-Security (without it, browsers are not told to keep to https)
- https://leotechnologies.com/: no page of the site sends Content-Security-Policy (without it, nothing limits which scripts a page may run)
- https://leotechnologies.com/: no page of the site sends X-Frame-Options or frame-ancestors (without it, another site can frame the page to trick a click)
- https://leotechnologies.com/: no page of the site sends X-Content-Type-Options: nosniff (without it, a browser may guess a file's type from its content)

## Items expected open

- `SITE-24-2f369778` x-content-type-options: no page sends it (since 2026-11-14)
- `SITE-24-7ea5b451` x-frame-options: no page sends it (since 2026-11-14)
- `SITE-24-cad315d8` content-security-policy: no page sends it (since 2026-11-14)
- `SITE-24-e6114362` strict-transport-security: no page sends it (since 2026-11-14)

Each item closes by `node menu/audit.mjs accept <id>` after an audit run saw it fixed, or by a rebuild from a crawl that no longer finds it; this file goes with its last item. `node menu/audit.mjs dismiss <id> --why "..."` marks one a false finding or an accepted risk.

**How it closes:** a rebuild from a new crawl that no longer finds it removes this file (one line goes to
bugs/FIXED.md), and its tests count again. To close it yourself (it will not be fixed, or another ticket tracks
it), move this file to bugs/closed/: its tests count again. A rebuild that still finds it files it again,
so it is looked at again.
