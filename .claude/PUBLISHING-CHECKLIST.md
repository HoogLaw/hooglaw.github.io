# Monthly Insights Publishing Checklist

Insights posts are written ahead and held. A held post lives in the repo and its URL
is reachable, so `noindex` is what actually keeps it unpublished, not the absence of
a link. Removing the `noindex` is the act of publishing.

## Current queue

| Publish date | File | Headline |
|---|---|---|
| September 1, 2026 | `insights/llc-operating-agreement.html` | What Your LLC Operating Agreement Should and Should Not Do |
| October 1, 2026 | `insights/when-need-lawyer-contract.html` | When Do You Actually Need a Lawyer to Review a Contract? |
| November 1, 2026 | `insights/business-succession.html` | Business Succession: The Thing Most Owners Never Plan For |

## Publish day: four steps

**1. Remove the hold.** Delete both lines from the `<head>`:

```html
<!-- SCHEDULED-NOINDEX: remove this entire comment block on ... -->
<meta name="robots" content="noindex, nofollow">
```

Confirm nothing is left behind:

```bash
grep -n "SCHEDULED-NOINDEX\|noindex" insights/THE-FILE.html
```

**2. Add the sitemap entry.** In `sitemap.xml`, inside the Insights block, with
`lastmod` set to the actual publish date:

```xml
<url>
  <loc>https://www.hooglaw.com/insights/THE-FILE.html</loc>
  <lastmod>YYYY-MM-DD</lastmod>
  <changefreq>yearly</changefreq>
  <priority>0.7</priority>
</url>
```

**3. Add the card to `insights/index.html`.** Copy an existing `article-card` block,
swap the href, tag, title, blurb, and date. If there is no hero image, use the gradient
tile pattern from the SB 26-189 card rather than pointing at a missing file.

**4. Add the line to `llms.txt`** under `## Insights (Articles)`.

Then commit and push. Confirm the live page returns no `noindex`:

```bash
curl -s https://www.hooglaw.com/insights/THE-FILE.html | grep -c noindex
```

That should print `0`.

## Verify before pushing

```bash
python -c "import xml.etree.ElementTree as ET; ET.parse('sitemap.xml'); print('sitemap ok')"
```

```bash
grep -rc "SCHEDULED-NOINDEX" insights/ | grep -v ':0'
```

The second command lists everything still held. It should match the queue table above
minus whatever you just published.

## House drafting standards

No em dashes or en dashes. No banned words (delve, leverage, bolster, foster, harness,
unpack, pivotal, groundbreaking, transformative, robust, seamless, nuanced as empty
praise, multifaceted, holistic, testament as praise, underscore, innovative,
cutting-edge, game-changing, vibrant, realm, figurative landscape). No banned phrases
("In today's world," "it's important to note," "one of the most," "when it comes to,"
"at its core," "at the end of the day," "plays a crucial role," "cannot be overstated,"
"shed light on," "pave the way"). No "It's not just X, it's Y" constructions. No
sign-off tags. No client-volume claims. Every post links to at least one service page.

Quick check:

```bash
grep -c "—\|–" insights/THE-FILE.html
```
