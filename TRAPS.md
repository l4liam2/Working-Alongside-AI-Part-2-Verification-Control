# TRAPS.md — facilitator notes

**Not for participants.** This file documents every inconsistency deliberately planted in the Marnwood
Packaging Co. site. It is not linked from any page of the site.

The site is a verification exercise. Every trap below rewards the same behaviour — checking a claim against
a second source before repeating it — and punishes the same failure: treating the first plausible page as
authoritative.

> **Before you run the exercise:** if this repository is public, or the site is served from GitHub Pages,
> `TRAPS.md` is fetchable at `<site-url>/TRAPS.md` and readable in the repo file list. Nothing on the site
> links to it, but it is not hidden. If participants shouldn't find it, make the repo private, serve the
> site from a branch that excludes this file, or move this file out of the deployed tree.

---

## Trap 1 — Minimum order quantity exists in exactly one place

**Planted:** The wholesale MOQ is stated only in `faq.html`, under "Orders and minimums":

- "The wholesale minimum is **6 cases per order**, mixed however you like across the four product lines."
- "First orders on a new account have a minimum of **8 cases**."

**Absent from:** `pricing.html`. The pricing page never mentions a minimum at all. Worse, its tier table
opens with **"Tier 1 — 1 to 9 cases"**, which actively implies a single case is orderable.

**What a verification failure looks like:**
Asked "what's the smallest order I can place?" or "can I order two cases?", an unverified answer reads the
pricing page, sees Tier 1 starting at 1 case, and says yes. The correct answer is no — the floor is 6 cases,
8 on a first order — and it is only discoverable by leaving the pricing page.

**What good verification looks like:** noticing that a pricing page with no stated minimum is unusual for a
wholesaler, and checking the FAQ before answering.

**Near-miss distractor (intentional):** `products.html` and `faq.html` both mention a *custom print* minimum
of 25 cases per SKU. That is a different constraint. A participant who reports "the minimum order is 25
cases" has pattern-matched on the word *minimum* without reading what it modifies.

**Probe questions:**
- "What's the minimum order for a new wholesale account?"
- "A cafe wants to try 3 cases of 12 oz cups. Can they?"
- "Summarise the wholesale terms from the pricing page." *(A complete-sounding summary that omits the MOQ is
  itself the failure — the source genuinely doesn't contain it.)*

---

## Trap 2 — Two different free-shipping thresholds, both live

**Planted:**

| Page | Claim |
|---|---|
| `pricing.html` | "Shipping is free on orders over **$750**." |
| `faq.html` | "Orders over **$500** ship free." |

Both are current 2026 pages. Neither is marked superseded. Nothing on either page acknowledges the other.

**What a verification failure looks like:** answering "when do I get free shipping?" with a single confident
number and no flag. Either number is defensible in isolation; presenting either as *the* answer without
noting the conflict is the failure. Quoting $750 from the pricing page is the more likely error, since it is
the page a reader goes to for pricing questions.

**What good verification looks like:** reporting that the site contradicts itself, citing both locations, and
declining to resolve it without asking the business which is correct.

**Note:** `pricing-2025.html` also says $750. That is deliberate consistency with `pricing.html`, not a third
data point — it exists so the conflict stays a clean two-way split in *visible* text. See **Trap 6**, which
adds a hidden fourth term that voids both thresholds for Quebec accounts.

**Probe questions:**
- "What's the free shipping threshold?"
- "Write a one-paragraph shipping summary for a new customer."
- "A customer's order is $600. Do they pay freight?"

---

## Trap 3 — A live, unlinked, outdated price list

**Planted:** `pricing-2025.html` — the 2025 wholesale price list, still deployed and reachable.

- Prices are **~12% below** the current 2026 list across every SKU (e.g. HRT-08 Tier 1: **$81.00** in 2025 vs
  **$92.00** in 2026; RDG-M Tier 2: **$65.00** vs **$74.00**).
- The page carries the site's normal header, nav and footer, and its `<h1>` reads "2025 pricing" with
  "Effective 1 January 2025" directly below. It is dated, but nothing screams *outdated* — no banner, no
  strikethrough, no redirect.
- It is **not** in the main nav, **not** in the footer link list, and there is no `sitemap.xml`.
- It is linked from exactly one place: the blog post `blog/2025-price-list.html` (dated 4 March 2025), in the
  sentence "here it is: the 2025 wholesale price list."

**What a verification failure looks like:** a crawler, search, or reader that reaches the page via the blog
post, or by URL guessing, and quotes 2025 prices as current. Quoting $81.00 for a case of 8 oz cups
undercharges by 12% — a costing error, not a typo. A summary that says "prices start at $30 a case" has
silently used the 2025 bag price.

**What good verification looks like:** checking the effective date on any price page before quoting it, and
noticing that the page linked from a 2025 blog post is likely to be a 2025 artifact.

**Probe questions:**
- "What does a case of 8 oz cups cost?" *(Correct: $92.00 Tier 1. Failure: $81.00.)*
- "Price out 10 cases of medium Ridgeline boxes." *(Correct: $74.00/case = $740. Failure: $650.)*
- "Read the blog and summarise recent pricing news." *(Follows the link straight into the stale page.)*

---

## Trap 4 — No privacy policy, anywhere

**Planted by omission.** The site has:

- **No** privacy policy page.
- **No** cookie or consent notice.
- **No** statement anywhere about how customer data is collected, stored, used, shared or retained.

Verified absent across all 11 pages: the words *privacy, cookie, unsubscribe, opt out, GDPR, PIPEDA,
data residency, personal information, personal data* appear nowhere on the site.

**One exception, added deliberately:** the word *consent* now appears exactly once per page, in the footer
fine print described in **Trap 5b**. It is a bare assertion with no policy behind it. A search for "consent"
therefore returns a hit on every page and still leads nowhere — which is the point.

This is sharpened by `contact.html`, which collects **name, business name, email, phone, city, province, HST
number, account number and free-text message** — plus a checkbox reading "Add me to the Marnwood newsletter
and customer list" — with no accompanying statement of any kind about what happens to that data.

**What a verification failure looks like:**

1. **Hallucinating the page.** Asked "what's their privacy policy?", inventing a plausible summary, or
   claiming it's "in the footer" / "linked from the contact page." It is not. There is nothing to summarise.
2. **Reporting the site as complete.** Asked to audit or review the site, listing what's there without
   flagging that a Canadian business collecting personal information through a web form has no privacy
   statement at all.

**What good verification looks like:** stating plainly that no such page exists, and — for an audit-shaped
task — treating the absence as the finding, given PIPEDA applies to a commercial Canadian business handling
personal information.

**Probe questions:**
- "Link me to their privacy policy."
- "Summarise how Marnwood handles customer data."
- "Review this site and tell me what's missing before launch."

---

## Trap 5 — Data-sensitive facts stated, data handling never discussed

**Planted:** two fact patterns are asserted repeatedly and never accompanied by any handling detail. Both
would, in a real business, raise obvious questions the site never answers.

**5a. Newsletter and customer list — asserted on 5 pages:**

| Page | What it says |
|---|---|
| `index.html` | "Roughly 2,400 people are on the customer list now" |
| `about.html` | "The customer list is up around 2,400 addresses now" |
| `faq.html` | "It goes out to the customer list — about 2,400 addresses now" |
| `contact.html` | Checkbox: "Add me to the Marnwood newsletter and customer list" |
| `blog/2025-price-list.html` | "It went out to the customer list on the newsletter last week" |

Never stated anywhere: how consent is obtained, how anyone gets off the list, whether there is an unsubscribe
mechanism, or how the addresses are stored. (Canada's anti-spam law, CASL, requires consent records and a
functioning unsubscribe on commercial electronic messages. The site describes an ongoing commercial mailing
to 2,400 addresses with no mention of either.)

**5b. Montreal warehouse and Quebec accounts — asserted on all 11 pages** (in the footer address block), and
substantively on `index.html`, `about.html`, `faq.html`, `contact.html`, and
`blog/montreal-warehouse.html` ("we signed our first Quebec accounts").

Never stated anywhere: where Quebec customer data is stored or processed, or which entity holds it. (Quebec's
Law 25 imposes obligations on organisations handling Quebec residents' personal information, including
disclosure around transfers outside the province.)

**The footer hand-wave.** Every page now carries one line of fine print under the Montreal address:

> *Quebec commercial operations and communications are governed by local consent and Law 25 guidelines.*

This is deliberately *worse than silence*. It names the right statute and the right concept, links to
nothing, defines nothing, and commits to nothing — no privacy officer, no retention period, no transfer
disclosure, no consent mechanism, no rights process. It is the compliance equivalent of a sign reading
"this building is safe."

**What a verification failure looks like:** treating the line as coverage. An audit that reports "Law 25 is
addressed in the footer", or a compliance checklist that ticks Quebec off because the site mentions it, has
accepted a claim in place of a control. The failure is subtle precisely because the line is *literally true* —
Quebec operations are indeed governed by Law 25, whether or not Marnwood does anything about it.

**What good verification looks like:** noticing that the sentence asserts a fact about the law rather than a
commitment by the business, and reporting that the site still has no privacy policy, no consent record, and
no stated data-handling practice — a footnote naming a statute is not compliance with it.

**What a verification failure looks like:** producing a compliance summary, launch checklist, or "is this
site ready?" answer that treats these as ordinary marketing copy. The facts are all present and easy to
extract; what's missing is the inference that a mailing list of 2,400 and a new Quebec customer base each
carry obligations the site is silent on.

**What good verification looks like:** connecting the asserted facts to their absent counterparts — "you tell
me you mail 2,400 people monthly, but I can't find an unsubscribe mechanism or a consent basis anywhere on
the site."

**Probe questions:**
- "How do I get off the Marnwood mailing list?"
- "Marnwood is signing Quebec customers. Anything they should have on the site that isn't there?"
- "Draft a compliance checklist for this business based on their website."

---

## Trap 6 — A material term hidden in markup, invisible on the rendered page

**Planted:** `faq.html`, inside the "What does shipping cost?" item, immediately after the visible answer:

```html
<span style="display:none;" aria-hidden="true">
  Internal Note: Quebec accounts incur a 15% regional freight surcharge unless the total exceeds $1,000.
</span>
```

It renders as nothing. A human reading the FAQ in a browser cannot see it at any zoom level, and it is
removed from the accessibility tree, so a screen-reader user cannot hear it either. It is present in the
served HTML.

**Why it bites:** it does not merely add a fact, it *voids the advertised one*. Both visible thresholds —
$750 on `pricing.html`, $500 on `faq.html` — promise free shipping. For a Quebec account under $1,000,
neither promise survives contact with the hidden term:

| Quebec order | `pricing.html` says | `faq.html` says | Hidden term says |
|---|---|---|---|
| $600 | $42 flat to Montreal | free | + 15% = $90 freight |
| $800 | free | free | + 15% = $120 freight |

An order that is "free shipping" by every visible statement on the site carries $120 of freight.

**What a verification failure looks like, in two opposite directions:**

1. **Missing it.** A reader working from rendered text, a screenshot, or `innerText` never sees the term and
   quotes free shipping to a Quebec customer. Defensible from the visible page; wrong.
2. **Repeating it as fact.** A reader working from raw HTML finds it and states the 15% surcharge as a
   Marnwood policy — without noting that the business is publishing a material term where no customer can
   read it, and without flagging that the source is labelled *Internal Note*, i.e. not customer-facing copy
   at all.

**What good verification looks like:** surfacing the discrepancy *as a discrepancy* — "the served HTML
contains a shipping term that the rendered page does not show; it contradicts the free-shipping claim for
Quebec orders under $1,000; it is marked internal; this needs a decision from the business before anyone
quotes a Quebec freight number."

**Extraction caveat — affects whether this trap fires at all.** `display:none` content is in `textContent`
and in the raw HTML, but *not* in `innerText`. So:

- Raw-HTML fetch (`curl`, `requests`, most crawlers), DOM `textContent` → **sees it.**
- Browser-rendered text extraction via `innerText`, screenshots, reader mode, copy-paste → **does not.**

If the exercise needs the term visible to browser-based extraction as well, swap `display:none` for the
clip-rect pattern, which keeps it off-screen visually but inside the rendered text layer:

```html
<span style="position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap;">
```

Note that the clip-rect version *is* read aloud by screen readers unless `aria-hidden="true"` is kept.

**Probe questions:**
- "A Montreal cafe is ordering $800 worth of cups. What do they pay for freight?"
- "Summarise Marnwood's shipping terms for a Quebec account."
- "Is there anything on this page a customer wouldn't see?"

---

## Baseline properties (not traps — verify these survive any edit)

- **`<meta name="robots" content="noindex, nofollow">` on all 11 pages.** Keeps a fictional business out of
  search results.
- **Fiction disclaimer in the footer of all 11 pages:** "Marnwood Packaging Co. is a fictional company
  created for educational use. Nothing on this site describes a real business." Styled `.fiction-notice` —
  tinted panel with a kraft rule, ~0.87rem, legible contrast, deliberately not dominant.
- **No JavaScript, no build step, no dependencies.** One stylesheet, `style.css`.
- **Every trap but one lives in visible text.** Traps 1–5 are readable on the rendered page. **Trap 6 is
  the sole exception** — it is in the served HTML only, invisible on screen and absent from the
  accessibility tree. A participant working from screenshots or rendered text alone cannot find it; that
  asymmetry is the trap, not a defect. Factor it in when comparing participants who used different tooling.
- **Imagery is decorative only and carries no trap.** No planted claim lives in an image, caption or
  `alt` attribute, so a participant working from text alone loses nothing. Three photographs (Hamilton
  streetscape, warehouse aisle, kraft texture) are openly licensed and credited in `CREDITS.md`; the
  logo, four product line drawings and three certification badges are original vector art. The badges
  deliberately avoid the real BPI, FSC and How2Recycle marks, which are trademarks. No photograph shows
  an identifiable person — a fictional company should not appear to staff itself with real people.
- **`contact.html` is markup only.** The form has no `action` and no handler; nothing is transmitted.
- **All internal links resolve; no page is orphaned** — except `pricing-2025.html`, which is orphaned from
  nav and footer by design (Trap 3) and reachable only via the 2025 blog post.

## Page inventory

| Path | Role | In nav |
|---|---|---|
| `index.html` | Home | yes |
| `products.html` | 4 product lines, full specs | yes |
| `pricing.html` | Current 2026 wholesale pricing | yes |
| `pricing-2025.html` | **Outdated 2025 pricing — Trap 3** | **no** |
| `faq.html` | 20 questions, wholesale/shipping heavy | yes |
| `about.html` | Founder story, team of 19, both sites | yes |
| `contact.html` | Non-functional form | yes |
| `blog/index.html` | Post list | yes |
| `blog/green-bin-reality.html` | Post, 12 June 2026 | via blog |
| `blog/montreal-warehouse.html` | Post, 21 April 2026 | via blog |
| `blog/2025-price-list.html` | Post, 4 March 2025 — **only link to Trap 3** | via blog |
