# CLAUDE.md — Venue-Ready website

## What this project is
Single-page marketing + conversion site for **Venue-Ready**: a £149 one-off Martyn's Law
(Terrorism (Protection of Premises) Act 2025) readiness pack for UK churches, village halls
and parish-council venues. Sold by a UK Ltd owned by the founder's wife. Launch target:
live before end of August 2026; sales peak Q4 2026 – Q2 2027 (commencement Spring 2027).

`index.html` is the entire site: self-contained HTML/CSS/JS, no build step, no framework.
Keep it that way unless a task truly requires splitting files. It must remain deployable by
drag-and-drop to Netlify.

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

## Current TODOs (work these, in order)
1. Replace payment placeholders with real Stripe/Gumroad links: KIT_PAYMENT_LINK_HERE (x2),
   PACK_PAYMENT_LINK_HERE (x2), TRAINING_PAYMENT_LINK_HERE (x1). Also LEAD_MAGNET_LINK_HERE
   for the Mis-selling Checklist PDF (host on the email platform).
2. Wire email capture to a real endpoint (Formspree or MailerLite embed). Success state
   inline, no alert(). Add hidden field for verdict type (out-of-scope / standard / enhanced)
   so the list is segmented.
3. Create privacy.html and terms.html (plain-English, UK GDPR; ICO number placeholder) and
   link from footer.
4. Fill footer placeholders: Ltd name, company number, registered office, ICO number —
   ask the owner, never invent.
5. Favicon + og:image (simple brass VR seal on green), meta og/twitter tags.
6. Plausible or GoatCounter analytics snippet (privacy-friendly; no cookie banner needed).
7. Netlify deploy: netlify.toml with security headers; connect domain venue-ready.co.uk.
8. Build the training product page/flow: hosts the narrated video (owner records it from the
   volunteer briefing deck), 10-question quiz, and a printable Briefing Completion Record
   (name / venue / date / score) — this is the £49/£199 fulfilment.
9. Design the Mis-selling Checklist one-page PDF from the #honest section content.
10. Later: /webinar page for association bookings; printable one-page PDF of the scope result.

## Do NOT
- Add a subscription tier, urgency countdown timers, exit popups, or testimonials that
  don't exist yet. Empty-state honesty over fake social proof.
- Invent legal claims, statistics, or endorsements. If a legal fact is needed, mark
  `<!-- VERIFY -->` and list it for the owner instead of guessing.
