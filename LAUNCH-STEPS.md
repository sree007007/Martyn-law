# Launch steps — plain English

No technical knowledge needed. Do these in order. Where a step says **send me**, just
paste the thing into our chat and I'll put it in the right place in the code — you never
need to edit a file yourself.

Rough total of your time: **about 3 hours**, spread over two weeks, plus waiting time
for the bank.

---

## THIS WEEK

### Step 1 — Start the bank account application (do this first, today)
**Why first:** everything else takes minutes. A business bank account takes 2–4 weeks,
and you cannot take card payments without one. If this slips, the whole launch slips.

1. Register the Ltd company first — gov.uk, "set up a limited company", about £50 and
   usually done the same day. It must be in your wife's name as sole director.
2. As soon as you have the company number, apply for the business bank account.
   Tide, Starling and Mettle are quickest for a new small Ltd.
3. While waiting, get professional indemnity insurance quotes (~£300–500/year).
   Search "professional indemnity insurance for consultants". Tell them: we supply
   written emergency-procedure templates to community venues.

**Send me:** the company name, company number and registered office address once you
have them. I'll put them in the footer of all ten pages — there are placeholders
sitting there now saying "to be added".

---

### Step 2 — Buy the domain (15 minutes)
1. Go to a domain registrar. Namecheap or Gandi are fine, or 123-reg if you prefer UK.
2. Search for `venue-ready.co.uk` and buy it. About £10 a year.
3. That's it for now. Don't buy any extras they offer — no hosting, no email package,
   no "site builder", no privacy add-on you have to pay for. You need the domain only.

**Send me:** confirmation that you own it.

---

### Step 3 — Put the site online (20 minutes)
The site is finished and ready. This puts it on the internet for free.

1. Go to **netlify.com** and sign up (free — use the "sign up with GitHub" button, since
   the site already lives on GitHub).
2. Click **Add new site → Import an existing project → GitHub**.
3. Choose the repository called **Martyn-law**.
4. It will ask which branch to deploy. Choose **claude/new-session-684hen**.
   *(Or ask me first and I'll make a tidier branch called `main` for you to pick instead.)*
5. Leave every other setting exactly as it is. Click **Deploy**.
6. Wait about a minute. You'll get a temporary address like `random-name-123.netlify.app`.
   **Open it and have a look — that's your site.**
7. To use your real domain: **Domain settings → Add a domain you already own** → type
   `venue-ready.co.uk` → follow the instructions it gives you. It will tell you to change
   two or three settings at the registrar from Step 2. Copy them across exactly.

From now on, every change I make appears on the live site automatically within a minute.
You never have to upload anything.

**Send me:** the netlify address, so I can check it looks right.

---

## NEXT WEEK

### Step 4 — Set up the email system (45 minutes)
This is what sends people the free letter, the checklist and the annual reminder.
Right now nobody receives anything, because there's nothing connected.

1. Sign up at **mailerlite.com** — the free plan is enough to start.
   *(Use MailerLite, not Formspree. Only MailerLite does the automatic yearly reminder.)*
2. Verify your domain when it asks. It will give you some DNS records — copy them into
   the registrar from Step 2. **Do not skip this.** Without it, church and council spam
   filters will silently bin your emails.
3. Create these five groups (they call them "groups" or "segments"):
   `out-of-scope` · `standard` · `enhanced` · `committee-onepager` · `annual-review`
4. Create a form or use their API, and find the **endpoint URL** — the web address
   MailerLite gives you for receiving sign-ups. It usually looks like
   `https://assets.mailerlite.com/jsonp/...` or similar.
5. Set up the automated emails. The wording for the annual reminder is already written
   for you in `content/annual-review-reminder-email.md` — copy and paste it.

**Send me:** the endpoint URL. I'll connect every sign-up box on the site to it, and the
list will sort itself into those five groups automatically.

---

### Step 5 — Set up card payments (45 minutes)
1. Sign up at **stripe.com** with the company details and the new bank account.
2. Go to **Product catalogue → Add product**. Create three:
   - Document Pack — £149
   - Complete Kit — £199
   - Training Kit — £49
3. For each one, create a **Payment Link** (Stripe has a button for this). You'll get
   three web addresses starting `https://buy.stripe.com/...`
4. In Stripe's settings, turn on **"After payment → show a confirmation page"** and paste
   in a thank-you message telling people the documents are on their way.

**Send me:** the three payment links.

Until you send them, every Buy button opens a pre-written email to you instead — so
nothing is broken in the meantime, and you can already sell by invoice.

---

### Step 6 — I wire it all together (my job, 20 minutes)
Once you've sent me the company details, the email endpoint and the three payment links,
I put them into the site and it goes live automatically. You do nothing.

---

## THE WEEK AFTER

### Step 7 — Test it like a customer (30 minutes)
Don't skip this. Sit down with a cup of tea and do all of it yourself:

1. Open the site on your **phone**, not just the computer.
2. Run the scope check as a small church — 150 people. Ask for the free letter.
   **Does the email actually arrive?** Check the junk folder too.
3. Run it again as a village hall with 250 people. Ask for the starter checklist.
4. Try to buy the Document Pack with a real card, then refund yourself in Stripe.
5. Send the free letter to a friend with a `@btinternet.com` or council email address
   and check it doesn't land in their spam.

**Tell me anything that felt wrong, confusing or slow.** You are the closest thing we
have to a real customer right now.

---

### Step 8 — Soft launch (no advertising)
Give the pack free to three local venues you know. Ask them for one honest sentence
about it afterwards. That's your first testimonial, and it's real.

Only after that, start the gatekeeper emails — your marketing copy pack already has
them written.

---

## Two decisions only you can make

**1. The training video.** The site currently sells the £199 Complete Kit including a
narrated video that hasn't been recorded. Either record it before launch, or tell me and
I'll take it off the site and mark training as "coming later" — it takes me twenty
minutes. Selling something that doesn't exist is the one thing that would undo the whole
honesty position.

**2. "Most venues choose this."** That badge sits on the Complete Kit card. You have no
customers yet, so it isn't true. Tell me and I'll remove it or replace it with something
factual.

---

## What I can do for you, any time — just ask

- Put your company details, payment links and email endpoint into the site
- Remove the training video claims, or the "most venues choose this" badge
- Check the four Word documents line by line against the official guidance
  (**send me the s27 statutory guidance PDF** — this is the biggest open risk)
- Add visitor statistics so you can see how many people run the scope check
- Build the `/webinar` booking page for associations
- Turn the six free printables into PDF files if MailerLite wants files to attach
- Write or rewrite any wording on the site
- Anything that feels wrong when you test it
