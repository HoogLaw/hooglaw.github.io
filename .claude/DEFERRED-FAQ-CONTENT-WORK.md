# Deferred: FAQ schema with thin on-page support

Identified August 3, 2026. Not urgent, not blocking, but real.

## The situation

Nineteen pre-existing pages carry `FAQPage` schema. Google's structured data
guidance requires the question and answer text to be visible on the page. More
practically, an answer that lives only in JSON-LD does almost nothing for AI
assistants, which read the rendered page.

Measured by substance rather than string match (what share of an answer's content
words appear anywhere in the page's own prose):

| Group | Pairs | Well covered | Partial | **Thin** |
|---|---|---|---|---|
| 7 Insights articles | 26 | 3 | 13 | **10** |
| 11 practice pages | 55 | 1 | 24 | **30** |
| **Total** | **81** | **4** | **37** | **40** |

"Thin" means under 45% of the answer's substance appears on the page at all. The
schema is telling Google something the page does not say.

The AI compliance pages are not part of this. All 51 pairs there are covered in
prose, zero thin, and they also carry visible FAQ blocks.

## Worst offenders

Four thin pairs each: `commercial-contracts-attorney-longmont`,
`power-of-attorney-longmont`, `trust-attorney-longmont`.
Three thin each: `healthcare-directive-longmont`, `llc-formation-attorney-longmont`,
`outside-general-counsel-longmont`, `probate-attorney-longmont`,
`estate-planning-act-of-love`, `llc-death`.

## The decision Michael made

Weave the unanswered questions into the existing page content **organically**,
rather than bolting FAQ blocks onto every page. The questions are real search
queries, so the content is worth having. It just needs to read as part of the page,
not as an appendix.

Do not simply strip the schema. That is the fast fix and it throws away the signal.

## How to redo the measurement

```bash
python .claude/_faq_coverage.py
```

Prints per-page counts of covered, partial, and thin. Re-run after any content pass
to see the thin count fall.

## Related, already done

- Homepage and `faq.html` no longer carry an "FAQ" item in the primary nav. All 45
  pages now share one nav: About, Practice Areas, AI Compliance, Michael Hoog,
  Insights, From the Bench, Contact Us. `faq.html` stays live, indexed, and linked
  from footers.
