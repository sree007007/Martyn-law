# CLAUDE.md — Venue-Ready website

## What this project is
Single-page marketing + conversion site for **Venue-Ready**: a £149 one-off Martyn's Law
(Terrorism (Protection of Premises) Act 2025) readiness pack for UK churches, village halls
and parish-council venues. Sold by a UK Ltd owned by the founder's wife. Launch target:
live before end of August 2026; sales peak Q4 2026 – Q2 2027 (commencement Spring 2027).

`index.html` is the entire site: self-contained HTML/CSS/JS, no build step, no framework.
Keep it that way unless a task truly requires splitting files. It must remain deployable by
drag-and-drop to Netlify.

## THE SPINE: seven legal requirements (standard tier) — everything maps to these
1 Assess scope/tier honestly (capacity incl. staff, busiest realistic occasion) → FREE calculator
2 Name the responsible person (non-delegable) → Document Pack
3 Notify the SIA when the portal opens → Document Pack
4 Have the four procedures: evacuation, invacuation, lockdown, communication → Document Pack
5 Make staff/volunteers AWARE of the procedures (explicit statutory ask) → Complete Kit (training)
6 Review the procedures → FREE annual reminder email
7 Coordinate with other responsible persons / shared premises → Document Pack
NOT required at standard tier: CCTV, barriers, bag searches, security staff, submitted risk
assessment, consultants, course certificates. Never sell or imply otherwise.
Positioning sentence (use everywhere): "Seven legal requirements. One afternoon. Nothing more,
nothing less." Doc 2 (risk assessment) is NOT statutorily required — always framed as the
thinking that makes requirement 4 fit the building, never as a legal duty.

## Audience & voice (do not drift)
- Buyer: churchwardens, PCC secretaries, village-hall trustees, parish clerks. Age 55–75,
  volunteer, time-poor, sceptical of security-industry fear-selling.
- Voice: calm, plain English, sentence case, active verbs. NEVER fear-selling, never
  "guaranteed compliance", never imply Home Office/SIA endorsement (they endorse nobody).
- Honesty is the brand: out-of-scope venues are told the truth and given a free letter.
  Enhanced-tier (800+, non-worship) visitors are referred away from the product. Keep both.
- Accessibility floor: 18px+ body, WCAG AA contrast, visible focus states, works without JS
  for reading (checker may need JS), prefers-reduced-motion respected.

## Brand tokens (already in :root)
- --green #1E3D2F (noticeboard green), --green-deep #152B21, --paper #FAF7F0,
  --brass #B08D3E / #C9A85C, --ink #22271F, --amber #8A5A16, --ok #2F6B3A.
- Display type: Young Serif. Body: Atkinson Hyperlegible (chosen for low-vision legibility —
  keep it; it's part of the story). No purple gradients, no dark "tactical" security look.
- Signature element: the oak-framed "Scope Board" checker. It stays the hero interaction.

## Legal lines that must never be removed
- Footer disclaimer: independent guidance, not legal advice, not endorsed by Home Office or
  SIA, responsible person retains all duties, official guidance free on GOV.UK/ProtectUK.
- FAQ answers stating: documentation not statutorily required at standard tier; no equipment
  needed at standard tier; places of worship remain standard tier regardless of capacity.

## Scope checker logic (source of truth)
- Not open to public → likely out of scope.
- Peak headcount (incl. staff/volunteers, busiest reasonable occasion) < 200 → out of scope
  (offer free confirmation letter, capture email).
- 200–799, OR any headcount if type = place of worship → STANDARD TIER → sell pack.
- 800+ and not worship → ENHANCED TIER → honest referral away + reading-list capture.

## Product ladder & pricing (fixed unless owner says otherwise)
£49 Training Kit (video + quiz + Briefing Completion Records) · £149 Document Pack ·
£199 Complete Kit (HERO — documents + training) · £1,295 Organisation Licence (unlimited
member use of Complete Kit, incl. webinar). Member rates via associations: £119 pack /
£169 kit. Never sell or imply a "compliance certificate" — Briefing Completion Records only.
Free lead magnets: scope calculator, out-of-scope letter, Mis-selling Checklist.

## Files in this repo
`index.html` (the site) · `privacy.html` · `terms.html` · `training.html` (£49/£199
fulfilment: video, quiz, Briefing Completion Record) · `netlify.toml` · `favicon.svg` ·
`og-image.png` (+ `og-image.html` source) · `content/annual-review-reminder-email.md`
(copy for the MailerLite automation).

**The six free printables** — each one is what a capture on the site promises, and each is
also linked directly so nobody has to hand over an email to get something we called free:

| Page | The list it serves | Prints as |
|---|---|---|
| `out-of-scope-letter.html` | `out-of-scope` | 1 side of A4 |
| `starter-checklist.html` | `standard` | 1 sheet, both sides |
| `enhanced-tier-reading-list.html` | `enhanced` | 1 sheet, both sides |
| `committee-one-pager.html` | `committee-onepager` | 1 side of A4 |
| `review-sheet.html` | `annual-review` | 1 sheet, both sides |
| `checklist.html` | mis-selling checklist (`LEAD_MAGNET_URL`) | 1 side of A4 |

If you change one of these, check its print pagination — the page counts above are the spec,
not an accident, and several are tuned to the millimetre.

## Current TODOs

### Blocked on the owner — nothing else can close these
1. **Payment links.** Fill `PACK_PAYMENT_URL`, `KIT_PAYMENT_URL`, `TRAINING_PAYMENT_URL` in
   the CONFIG block at the bottom of `index.html`. While any is empty that button falls back
   to a pre-written email, so no click is ever dead — but nobody can pay by card until these
   are real Stripe/Gumroad URLs.
2. **`FORM_ENDPOINT`.** Same CONFIG block. MailerLite (free tier does automations; Formspree
   does not) plus SPF/DKIM/DMARC, or church and council spam filters will eat everything.
   Every capture posts `email`, `list` and `verdict` so the list segments itself.
3. **Company placeholders** in the footer of every page: Ltd name, company number,
   registered office, ICO number. Ask the owner — never invent these.
4. **VAT position** — `[VAT position confirmed at launch]` in the #buying section.
5. **Phone number and hours** — `[phone number] — [days and hours]` in the #buying section.
6. **Record the training video** (optional now), then set `VIDEO_EMBED_URL` in
   `training.html`. The video box stays hidden until that URL is real, so the page never
   promises a video that isn't there. Requirement 5 is already met by the 15 briefing
   slides on that page — the video is an upgrade, no longer a blocker.

### Done (do not redo)
- Config-first wiring of every payment/download button, with email fallbacks.
- Email capture wired to `FORM_ENDPOINT` with inline success state, no `alert()`, and
  hidden `list` + `verdict` fields for segmentation.
- `privacy.html`, `terms.html`, linked from the footer. Terms match the site's 30-day
  refund promise and invoice/BACS route — **if one changes, change the other.**
- Favicon, og-image, full OG/Twitter meta.
- `netlify.toml`: security headers + pretty-URL rewrites.
- `training.html` — now carries the full 15-slide volunteer briefing (present full screen,
  print as a handout, readable with JS off), the 10-question quiz and the Completion Record.
- Annual review reminder (requirement 6): capture in #minimum, printable sheet, and the
  yearly email drafted in `content/annual-review-reminder-email.md`.
- All five promised lead magnets now exist as pages (see the table above). Every capture
  carries a hidden `list` field, and every verdict offers the same material as a direct
  print link — the free thing stays free whether or not an email is given.

### Still to build
7. Privacy-friendly analytics (Plausible or GoatCounter). No cookie banner needed — and
   the privacy notice currently says we run no tracking cookies, so keep it that way.
8. Export the six printables to hosted PDFs if MailerLite needs files to attach. Each page
   prints correctly already — "Print / save as PDF" on the page is the export.
9. Later: `/webinar` page for association bookings; printable one-page PDF of the scope result.

### Two things flagged to the owner, not yet actioned
- **"MOST VENUES CHOOSE THIS"** on the Complete Kit card (`.price.feat::before`) is social
  proof we have not earned — there are no customers yet. Flagged; the owner decides.
- ~~The Complete Kit described an unrecorded video as available.~~ **Resolved:** the
  briefing now exists as 15 presentable/printable slides in `training.html`, taken from the
  Volunteer Briefing Deck, and all site copy describes the briefing rather than a video.

### Legal facts awaiting verification
Marked `<!-- VERIFY -->` in `enhanced-tier-reading-list.html`: the enhanced-tier penalty
ceiling (£18m / 5% of qualifying worldwide revenue), the qualifying-worldwide-revenue
definition from the Commencement No.2 Regulations, and the expected timing of SIA
enforcement guidance and the notification portal. Check GOV.UK before that page goes live.

### Keep the spine intact
Keep the `#minimum` section as the site's spine — if products change, update the seven-row
mapping first, then everything else. The verdict copy, the pricing cards and the FAQ all
lean on it.

## Do NOT
- Add a subscription tier, urgency countdown timers, exit popups, or testimonials that
  don't exist yet. Empty-state honesty over fake social proof.
- Invent legal claims, statistics, or endorsements. If a legal fact is needed, mark
  `<!-- VERIFY -->` and list it for the owner instead of guessing.
