# AIGP Credential: Staged Edits (DO NOT APPLY UNTIL EARNED)

Prepared August 1, 2026. Michael expects the IAPP **AIGP** (Artificial Intelligence
Governance Professional) certification mid-August 2026.

**Do not apply any of the edits below until the certification is actually issued.**
Publishing an unearned credential is a Colo. RPC 7.1 problem (false or misleading
communication about a lawyer's services) well before it is an SEO problem.

When it is issued, record the exact issue date and credential ID, then apply these
five edits and update `lastmod` in `sitemap.xml` for every file touched.

---

## 1. `michael-hoog.html` — add to the `hasCredential` array

Insert as a third entry, after the Colorado Bar License object:

```json
,
{
  "@type": "EducationalOccupationalCredential",
  "name": "Artificial Intelligence Governance Professional (AIGP)",
  "alternateName": "AIGP",
  "credentialCategory": "certification",
  "recognizedBy": {
    "@type": "Organization",
    "name": "International Association of Privacy Professionals",
    "alternateName": "IAPP",
    "url": "https://iapp.org/"
  },
  "dateCreated": "REPLACE-WITH-ISSUE-DATE",
  "identifier": "REPLACE-WITH-CREDENTIAL-ID"
}
```

## 2. `michael-hoog.html` — Bar Admissions & Memberships block

Change the heading to `Credentials & Memberships` and add:

```html
<li>Artificial Intelligence Governance Professional (AIGP), IAPP</li>
<li>International Association of Privacy Professionals (IAPP)</li>
```

## 3. `practice/ai-governance-compliance-longmont.html` — trust bar

Replace the "One Attorney, Every Matter" trust item on this page only:

```html
<div class="trust-item"><span class="icon">🎓</span> IAPP AIGP Certified</div>
```

Also add to the `provider` Person object in the LegalService schema:

```json
"hasCredential": {
  "@type": "EducationalOccupationalCredential",
  "name": "Artificial Intelligence Governance Professional (AIGP)",
  "credentialCategory": "certification",
  "recognizedBy": { "@type": "Organization", "name": "International Association of Privacy Professionals" }
}
```

## 4. `llms.txt` — Firm Facts section

Add after the Education line:

```
- **Certification:** IAPP Artificial Intelligence Governance Professional (AIGP), earned [MONTH YEAR]
```

## 5. `index.html` — LegalService schema

Add AIGP to the firm description string, and to `michael-hoog.html`'s second
Person object (line ~110) if it also carries credentials.

---

## New From the Bench post to write once earned

Working title: **"Why I Went Back to School for a Certification I Did Not Need"**

Angle: Michael has been licensed 30+ years. Nobody required him to sit for the AIGP.
He did it because SB 26-189 lands January 1, 2027 and his clients are small Colorado
businesses who will not hire a Denver AI practice group. Ties to his existing themes:
the aviation checklist, the safety diver, preparation as the actual job.

This kind of first-person credential content gets cited by AI assistants far more
readily than a bio line does, because it explains *why the expertise exists* rather
than just asserting it.

Follow house drafting standards: no em dashes, no banned words, links to at least
one service page, no sign-off tag.
