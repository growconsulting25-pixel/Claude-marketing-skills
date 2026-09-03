# SaahVay Redesign Strategy

Phases 1 to 4 of the storefront redesign, plus the brand foundation required before any visual design work begins. Prepared 3 September 2026.

## How to read this document

This is the strategy checkpoint the brief asked for. Nothing here is a visual design or an implementation. It defines what the store must say, who it serves, how a customer moves through it, and what the site map and identity system are. Phases 5 to 9 (wireframes, page designs, Shopify implementation, SEO plan, creative direction) build on the decisions recorded here and should not start until these are approved or corrected.

### Evidence status

The live storefront at saahvay.com could not be opened from the environment this work ran in. The environment's network policy blocks the domain, and it also blocks the Wayback Machine and reader proxies. The Shopify connector available in the session is attached to a different, unrelated store, so it was not used.

Evidence used, in order of reliability:

| Source | What it gives us |
|---|---|
| Search-engine index of saahvay.com | Live title tag, meta description, one best-seller name and price, entry price point |
| Your screenshot of the body-shape navigation | Current five shape labels and their letter codes, current dark-ground nav treatment, current serif typeface style |
| Your written brief | Duplicate product titles, at least one sale price higher than the crossed-out price, a "30-day trial" return claim, a "24/7 support" claim, a "Sexy Stylish Ideas" heading, the current mission and vision copy, and the navigation structure |
| Shopify platform knowledge | What the current theme is likely doing, and what the platform can and cannot do natively |

Findings that come from the first two sources are marked **observed**. Findings that come from your brief are marked **reported** and will be confirmed on the live site. Findings that are inferred from how Shopify stores of this kind typically behave are marked **expected** and are the first things to verify.

To let the next phase inspect the live site directly, allow `saahvay.com`, `www.saahvay.com`, and `cdn.shopify.com` in the Claude Code environment's network policy (Settings, Environments, Network access). The docs page is https://code.claude.com/docs/en/claude-code-on-the-web. Alternatively, export the theme as a zip and the products as CSV from Shopify admin and add both to this repository under `reference/`.

---

## Phase 1: Strategic audit

### 1.1 The one-line diagnosis

The store has a genuinely differentiated idea (shop by body shape) that is currently presented as a sub-menu rather than as the reason the store exists. Everything else on the site, from the title tag to the product names, reads as a general women's clothing store. A customer who lands on the homepage has no reason to believe SaahVay will help her more than any other Shopify store.

### 1.2 Brand positioning weaknesses

**The title tag sells the wrong thing.** *Observed.* Google currently shows the homepage as "SaahVay- Simple, effortless and elegant fashion for women f…". It is truncated mid-word, so it is over the roughly 60-character limit, and the part that survives says "simple, effortless, elegant fashion for women", which is what every competitor says. Body shape, the one thing that is distinctive, is absent.

**The meta description leads with "safe space".** *Observed.* The indexed description opens with "a safe space for trendy, easy to wear and accessible fashion". "Safe space" is a phrase with strong connotations outside fashion, and paired with "trendy" it contradicts the brief's own direction (timeless, not trend-led). Neither "trendy" nor "safe space" should survive the rewrite.

**The mission and vision copy is long, abstract, and interchangeable.** *Reported.* Phrases like "meaningful change in how women feel about themselves" and "empowering women to feel confident" are sincere but could sit on any brand's About page. The concrete, defensible idea buried in the copy is "no endless searching, no overwhelm" and "ready-made combinations". That is the story.

**Body shape is presented as taxonomy, not as help.** *Observed.* The screenshot shows five text links on a dark ground: "The Rectangle Body Shape (H)", "The Apple Body Shape (O)", and so on. The word "Body" repeated five times, plus the definite article, makes the list read like a reference chart. Nothing in the labels tells the customer what she gets by clicking, and there is no route for the customer who does not know her shape.

**Naming risk in the shape labels themselves.** *Observed.* "Apple" and "Pear" are widely used in styling guides but many women find fruit comparisons reductive, and "Inverted Triangle" is technical. The brief is right to keep the five categories (they are the industry standard and are what customers search for), but the display copy should lead with the letter and a positive descriptor, and keep the common name as a secondary label for recognition and SEO. See Phase 2.

### 1.3 Conversion problems

**No guided entry point.** *Expected.* The homepage of a standard Shopify theme opens with a hero image and a "Shop now" button that leads to an all-products collection. For SaahVay this sends the customer straight past the only thing that makes the store worth trusting.

**Contradictory sale pricing destroys trust at the product card.** *Reported.* At least one product shows a "sale" price higher than the crossed-out regular price. On Shopify this happens when a supplier import writes the supplier's retail price into `price` and a lower number into `compare_at_price`, or when a bulk price edit updates one field and not the other. Shopify's theme code will happily render the strike-through anyway. This is a data problem, not a design problem, and it must be fixed with an audit across every variant before launch, plus a Liquid guard so the strike-through only renders when `compare_at_price` is greater than `price`.

**Supplier product names.** *Observed.* The indexed best seller is "Button Front Tiered Denim Maxi Skirt". This is a supplier feed title: four descriptors stacked in front of the noun, no brand voice, and identical to the same SKU on dozens of other stores. It also tells the customer nothing about who it flatters. Product naming rules are in section 1.6.

**Duplicate product titles.** *Reported.* Duplicate titles usually mean the same supplier item was imported twice (once per colourway, or once per import run). Each duplicate splits reviews, inventory, and search ranking, and shows the customer two identical cards. These must be merged into single products with colour variants.

**Trust claims the business cannot back.** *Reported.* "24/7 support" and a "30-day trial" for clothing. A trial implies the customer can wear the garment for 30 days and return it, which is almost certainly not the policy. If a claim is later contradicted at checkout or in a support reply, the customer feels misled, and misleading return claims are also a consumer-protection exposure in Canada, the US, and the EU.

**Generic section headings.** *Reported.* "Sexy Stylish Ideas" does not match the audience (busy professionals, mothers, women who want guidance without judgement) and does not describe what the section contains.

### 1.4 UX and mobile problems

**Dark-ground navigation for a light-ground store.** *Observed.* The shape menu sits on near-black with beige text. If the rest of the storefront is white and cream (as the brand palette intends), a black mega-menu is a visual break, and beige-on-black at small text sizes falls below WCAG contrast for body text. Black should be reserved for type and primary buttons, not large surfaces.

**Navigation likely carries duplication.** *Expected.* The brief mentions "excessive navigation duplication". Shopify stores built up over time typically end up with "Shop", "All", "New", and a product-type menu that all lead to overlapping collections. The proposed navigation in Phase 4 collapses this to six items.

**Mobile is likely the desktop stacked.** *Expected.* Standard Shopify themes handle mobile by stacking sections. For a guided store, the mobile experience needs its own decisions: a quiz that works with thumbs, filters in a bottom sheet, a sticky add-to-cart, and a way back to quiz results. These are specified in Phase 3 and detailed in Phase 6.

### 1.5 Content and product-data problems

The problems in this section all come from the same root cause: supplier data is being published to the storefront without a cleaning step.

- Titles are supplier titles. *Observed.*
- Duplicate products exist. *Reported.*
- Price and compare-at price are inconsistent. *Reported.*
- Photography is supplier photography, so it varies in background, lighting, model, and crop from product to product. *Expected.*
- Descriptions are likely supplier descriptions or empty. *Expected.*
- Capitalisation and punctuation vary between products. *Reported.*
- Collections overlap because supplier categories were imported as collections. *Reported.*
- No product carries structured body-shape data. Body-shape collections, if they exist, are likely manual collections or tag-based collections with inconsistent tagging. *Expected.*

The fix is a publishing workflow, defined in section 1.6, not a one-off cleanup.

### 1.6 Product-data rules (for the cleanup and for every future import)

**Workflow.** Imported products land as `draft`. A product moves to `active` only when every field in the checklist below is complete. The checklist lives in a Shopify metafield (`saahvay.publish_ready`, boolean) so it can be filtered in admin and enforced by a bulk-edit view.

**Title format.** `[Style name] [Garment]` in title case, with a maximum of 40 characters. Style names are short, warm, and reusable across a range: *Mira Wrap Dress*, *Ada Wide-Leg Trouser*, *Noor Tiered Midi Skirt*. Supplier descriptors (button-front, tiered, denim) move into the description and the fit notes. Colour is a variant, never part of the title.

**Description structure.** Three short parts, each its own metafield so the product page can lay them out without parsing HTML:

1. *The piece* (two sentences: what it is, what it is for)
2. *Why it works* (one sentence per recommended shape, in the "designed to complement" register)
3. *Fit and fabric* (fabric composition, stretch, length in cm on a named size, model size and height when available, care)

**Pricing rule.** `compare_at_price` is either empty or strictly greater than `price`. A scheduled check (Shopify Flow, or a small script using the Admin API) flags any variant that breaks the rule.

**Photography rule.** One consistent product-on-model shot set per product: front, back, detail, and a movement shot. Same background family (white or cream), same crop (3:4). Supplier lifestyle imagery is not used on cards. Until reshoots happen, supplier images are cropped to 3:4 and background-normalised so cards at least align.

**Body-shape data.** Two metafields on every product:

- `saahvay.shapes_primary` (list of single letters from H, O, V, X, A): the shapes the piece is selected for
- `saahvay.shapes_secondary` (list): shapes it also works well for

Plus a text metafield `saahvay.why_it_works` used by the product page fit module. A product can and usually should carry more than one shape. Products that suit all five are tagged with all five, not left empty.

**Tags.** Tags are for filtering only, and use a namespaced format so imports cannot collide with them: `shape:H`, `occasion:work`, `fit:relaxed`, `length:midi`, `sleeve:long`. Supplier tags are stripped on import.

### 1.7 SEO issues

- Truncated, non-distinctive title tag on the homepage. *Observed.*
- Meta description that leads with "safe space" and "trendy". *Observed.*
- Duplicate products mean duplicate pages competing for the same query. *Reported.*
- Supplier titles are identical to titles on other stores, so product pages have no differentiated text to rank on. *Observed.*
- Body-shape pages are the store's best organic opportunity ("best dresses for pear shape" and similar queries have real volume and low commercial competition), and they are currently menu links rather than content pages. *Observed.*
- The store does not visibly have a journal or blog, so there is nothing to build topic clusters from. *Expected.*
- Schema is likely whatever the theme emits (Product and Organization at best). *Expected.*

### 1.8 Trust issues

Covered above: contradictory pricing, unverifiable support and trial claims, and supplier imagery. Two additions:

- The brand has no visible founder, no visible policy detail, and no visible location. A guided-shopping brand needs a person or at least a point of view behind it.
- Reviews: if there are none yet, the redesign must not fake them or show empty review modules. A single honest line ("New to SaahVay? Our returns policy is here") outperforms an empty star rating.

### 1.9 Opportunities worth keeping

- The five-shape system with letter codes. It is correct, standard, and searchable.
- The existing mission's concrete ideas: ready-made combinations, no endless searching, built for busy lives.
- The black, white, and warm beige identity. It is already right for the positioning; it needs to be applied with discipline.
- Shopify itself, with its checkout, product import apps, and collections. Nothing in this plan requires leaving it.
- Entry pricing around 42 to 48 USD. *Observed.* It is accessible enough to make guided shopping a low-risk first purchase.

---

## Phase 2: Brand foundation

### 2.1 Brand essence

**Fashion chosen for your shape, so you can stop guessing.**

### 2.2 Target customer

Women in their late twenties to late fifties who buy clothes online, dislike the process, and have been burned by it. She is a professional, a business owner, a mother, or all three. She is not looking for trends and she is not looking for a bargain hunt. She wants to open a site, understand quickly what will work on her, buy it, and have it arrive looking the way it looked on screen. She wants advice from someone who has thought about bodies like hers, and she does not want to be labelled or lectured.

Two secondary audiences the store should not design against but should not exclude: younger women learning what suits them for the first time, and gift-givers who know the recipient's shape.

### 2.3 The customer problem

She cannot tell from a product photo whether a piece will flatter her. So she either buys and returns, buys and keeps something she does not wear, or gives up. Online stores answer this with size charts, which solve a different problem (will it fit) and not hers (will it look right).

### 2.4 Unique value proposition

SaahVay selects every piece and every outfit for specific body shapes, tells you which ones and why, and lets you shop your shape from the first click. Standard sizes still apply; shape is the layer on top that other stores do not offer.

### 2.5 Positioning statement

For women who want to look good without spending hours shopping or gambling on returns, SaahVay is the online fashion store that curates clothing and complete outfits by body shape. Unlike general fashion stores that leave you to guess, SaahVay tells you which pieces are selected for your shape and why, so you can buy with confidence in minutes.

### 2.6 Brand promise

Every piece on SaahVay tells you who it is chosen for. We will never sell you something without saying which shapes it is selected to complement.

### 2.7 Messaging pillars

1. **Chosen for your shape.** Every product carries its shape recommendations and a one-line reason. This is the claim the store is built on.
2. **Outfits, not just items.** Complete combinations remove the hardest part of shopping, which is deciding what goes with what.
3. **Minutes, not hours.** The quiz, the shape pages, and the filters exist so she can finish quickly.
4. **Honest fit.** Real measurements, real model sizes, plain language about fabric and stretch, and a returns policy stated the way it actually works.
5. **Guidance without judgement.** Shape is a starting point, not a verdict. Copy never calls anything a flaw, a problem area, or something to hide.

### 2.8 Tone of voice

Warm, direct, and competent. Like a stylist friend who is short on time and respects yours.

- Short sentences. One idea each.
- Second person, present tense. "This dress is selected for H and A shapes because the tie waist adds definition."
- Recommend, never guarantee. Use *selected for*, *designed to complement*, *often works well for*. Never *will flatter*, *guaranteed to fit*, *perfect for*.
- Never use *flatter your flaws*, *hide*, *slimming*, *problem area*, *balance out*. Describe what a cut does, not what it corrects.
- No exclamation marks in product or navigation copy. They are allowed once in an order confirmation.
- No "empowerment", "journey", "elevate", "curated" (the word, not the practice), "safe space", "trendy", "sexy".

**Microcopy style.** Buttons say what happens: *Find my shape*, *Shop shape H*, *Add the full look*, *Save my result*. Labels are nouns. Errors say what to do next: "Choose a size to continue." Empty states are honest: "No reviews yet. Be the first, or read the fit notes below."

### 2.9 Shape names in customer-facing copy

Keep the five industry names for recognition and search, but lead with the letter and a positive descriptor. Display format:

| Letter | Display name | Secondary label | One-line descriptor |
|---|---|---|---|
| H | Shape H | Rectangle | Shoulders, waist, and hips in a straight line. Pieces that add shape at the waist. |
| O | Shape O | Apple | Fullness through the middle, with great legs and shoulders. Pieces that flow from the shoulder or bust. |
| V | Shape V | Inverted Triangle | Strong shoulders, narrower hips. Pieces that add volume and detail below the waist. |
| X | Shape X | Hourglass | Bust and hips in proportion with a defined waist. Pieces that follow the waist rather than hide it. |
| A | Shape A | Pear | Hips wider than shoulders. Pieces that bring attention up and skim below. |

Rules: the letter is always shown, the common name is always shown at least once per page for search intent, and the descriptor never mentions a flaw.

### 2.10 Tagline options

1. **Chosen for your shape.** (Recommended. Short, ownable, and it doubles as a product-card label.)
2. Style that knows your shape.
3. Shop your shape, not the guesswork.
4. Fashion selected for your shape, your life, and your confidence. (The brief's own line. Works as a sub-headline; too long as a tagline.)

### 2.11 Visual identity direction

Elevated contemporary fashion publication meets a personal stylist meets a fast Shopify store. Black type on white and cream, warm beige as the brand surface, editorial photography of real women, generous but disciplined whitespace, and one restrained accent moment per screen. No gradients, no gold, no large black surfaces.

The full color and typography system is in section 5.

---

## Phase 3: Customer journey and funnel

Each step names its purpose, its primary call to action, and what it hands to the next step.

| Step | Purpose | Primary CTA | Hands off |
|---|---|---|---|
| 1. Traffic source | Paid social, organic search on shape queries, email, referrals. Ad and search copy always name the shape or the quiz, never generic fashion. | Find your shape | Landing on homepage or directly on a shape page or the quiz |
| 2. Homepage | Make the promise in five seconds: chosen for your shape. Offer two doors: pick a shape, or take the quiz. Keep a plain "Shop" route for customers who want to browse. | Find my fit | Shape selection, quiz start, or Shop |
| 3a. Shape selection | Five cards. She recognises herself or she does not. | Shop shape X | Shape page |
| 3b. Fit quiz | Six visual questions, about 60 seconds, no measurements required. Progress bar, back button, keyboard accessible. | Show my result | Result page with shape and confidence note |
| 4. Personalised result | Name the shape positively, explain in three lines, show three styling principles, then products and one complete outfit for the shape. Offer to save or email the result. Email capture happens here, after value. | Shop my shape | Shape collection, outfit, or product |
| 5. Shape page or outfit page | Shop with the shape filter pre-applied. Contextual copy above the grid, kept to three lines with a "Read the full guide" link. Outfits appear as a row above single items. | Add to bag / Add the full look | Product page or cart |
| 6. Product page | Reduce fit anxiety: images, shape module ("Selected for H, A, X. Why: …"), size selector with size guide, fit notes with model size, fabric, shipping and returns, reviews, the outfit this piece belongs to. Sticky add-to-cart on mobile. | Add to bag | Cart drawer |
| 7. Cart drawer | Confirm, show the outfit's missing pieces if she added only one, show the shipping threshold if there is one, no upsell noise. | Checkout | Shopify checkout |
| 8. Shopify checkout | Untouched. Shopify Payments, Shop Pay, and any existing gateways stay as they are. | Pay | Order confirmation |
| 9. Post-purchase | Confirmation email with fit notes for the pieces bought. Delivery email. Two weeks later, a "how did it fit" email that feeds reviews and refines the shape data. Saved quiz result in the account. | Tell us how it fit | Reviews, repeat purchase |

**The critical hand-off** is step 4 to step 5: the result page must pass the shape into the collection as a real filter (`/collections/shape-a` or `/collections/dresses?filter.p.m.saahvay.shapes_primary=A`) so that browsing stays personalised without the customer re-selecting anything. The quiz result is stored in `localStorage` and, when she is logged in, in a customer metafield so it follows her across devices.

**Two exits that must always be available.** "I'd rather just browse" from the quiz, and "Change my shape" from any shape-filtered page. A customer who feels trapped in a category leaves.

---

## Phase 4: Sitemap

Shopify's URL structure is fixed (`/collections/`, `/products/`, `/pages/`, `/blogs/`), so the sitemap is expressed in those terms.

### Primary navigation (six items)

| Label | Destination | Notes |
|---|---|---|
| New Arrivals | `/collections/new-arrivals` | Automated collection, published within last 30 days |
| Shop | Mega menu of category collections | Dresses, Tops, Trousers, Skirts, Outerwear, Sets |
| Shop by Shape | `/pages/shop-by-shape` | Five cards plus quiz entry |
| Outfits | `/collections/outfits` | Complete looks |
| Find Your Fit | `/pages/fit-quiz` | The quiz |
| Our Story | `/pages/our-story` | |

Utility icons: search, account, country and currency, bag. On mobile, Shop by Shape and Find Your Fit collapse into a single "Your Shape" entry that opens the five cards with the quiz link beneath.

### Full site map

```
/                                     Homepage
/pages/shop-by-shape                  Shape chooser (five cards + quiz link)
/collections/shape-h                  Shape H (Rectangle) page: guide + products + outfits
/collections/shape-o                  Shape O (Apple)
/collections/shape-v                  Shape V (Inverted Triangle)
/collections/shape-x                  Shape X (Hourglass)
/collections/shape-a                  Shape A (Pear)
/pages/fit-quiz                       Fit quiz
/pages/fit-quiz/result?shape=A        Quiz result (one page template, shape from query)
/collections/outfits                  All complete looks
/products/[outfit-handle]             An outfit (a bundle product with component metafields)
/collections/new-arrivals
/collections/all                      Shop all
/collections/dresses
/collections/tops
/collections/trousers
/collections/skirts
/collections/outerwear
/collections/sets                     Two-piece and co-ord sets (single SKUs, distinct from outfits)
/collections/[occasion]               Work, Weekend, Occasion (automated by occasion tag)
/products/[handle]                    Product page
/pages/our-story                      Brand story
/blogs/style-journal                  Style Journal (content clusters)
/blogs/style-journal/[article]
/pages/fit-and-sizing                 Size guide, how to measure, shape vs size explainer
/pages/faq
/pages/shipping
/pages/returns
/pages/contact
/account                              Shopify account (saved shape shown here)
/cart                                 Cart page (drawer is the primary interface)
/search
/policies/*                           Shopify policy pages
```

### Shape pages are collections, not pages

Each shape page is a Shopify collection (automated: product metafield `shapes_primary` contains the letter) with the guide content stored in collection metafields and rendered above and below the grid. This keeps products filterable and lets Shopify's own Search & Discovery filters work, while giving the page enough unique copy to rank.

### Initial Style Journal clusters

Eight articles to launch with, each a real guide and not a template with the shape name swapped:

1. How to identify your body shape at home (no measuring tape required)
2. Body shape vs clothing size: why both matter and how they differ
3. What to wear for a pear (A) shape: cuts, lengths, and what to skip
4. Best dresses for an apple (O) shape
5. Dressing a rectangle (H) shape: creating a waist without a belt
6. A five-piece work capsule for busy women, by shape
7. Why the same dress looks different on different shapes (with photos of real customers, once permission exists)
8. How to shop for clothes online without the return cycle

---

## Phase 5 preview: Brand foundation deliverables requested before design

The brief asks for six things before any page is designed. They are here so that the design phases can start immediately once the strategy is approved.

### 5.1 Color palette

The logo file and brand reference were not attached to the session, so the values below are derived from the only brand material available: the screenshot of the current navigation (beige type on near-black). They are calibrated, not measured. Once the logo file is added to the repository, the beige and black values will be sampled from it and corrected here; the structure of the palette will not change.

| Token | Hex | Role |
|---|---|---|
| Ink | `#141414` | Headings, navigation, primary buttons, prices. Near-black rather than pure black so it sits warmly against cream. |
| Charcoal | `#3B3835` | Body text and secondary copy. Warm-biased so it reads as part of the beige family. |
| White | `#FFFFFF` | Product cards, product page ground, forms. |
| Cream | `#F7F3EC` | Page background for editorial sections, quiz, result page. Separates sections without borders. |
| Beige | `#D9C8AD` | The brand surface: shape cards, secondary buttons, shape labels on cards, dividers, the announcement bar. |
| Beige deep | `#B49E7E` | Borders on beige surfaces, uppercase labels, focus rings, the one accent line a screen is allowed. |
| Stone | `#8C8479` | Placeholder text, disabled states, captions. |
| Success | `#2F6B4F` | In-stock and confirmation states only. |
| Alert | `#A33A2A` | Errors and low stock only. Never for sale pricing. |

Sale pricing uses Ink for the sale price and Stone for the struck price. No red.

Contrast checks: Ink on White 16.4:1, Ink on Cream 14.6:1, Ink on Beige 10.3:1, Charcoal on Cream 9.9:1, Beige deep on White 2.9:1 (labels 14px and above must be uppercase with letter-spacing, and it is never used for running text), White on Ink 16.4:1.

### 5.2 Logo typeface

The screenshot's navigation is set in an old-style serif with moderate contrast and a slightly condensed lower case, in the Garamond family. Whether the logotype itself uses the same face cannot be confirmed without the file. Closest Google Fonts matches, in order:

1. **Cormorant Garamond** (weights 500 and 600): the closest in character for display sizes. Too light below 20px.
2. **EB Garamond**: the closest for text sizes and the safest single choice if the logo turns out to be a regular Garamond.

If the logo file shows a Didone (high-contrast, hairline serifs), the match becomes **Playfair Display** for headings, and this section will be updated.

### 5.3 Recommended pairing

- **Headings:** Cormorant Garamond, weight 600 for H1 and H2, 500 for H3. `text-wrap: balance`. Letter-spacing 0 at display sizes, -0.01em above 48px.
- **Body, navigation, filters, buttons, prices, and all ecommerce information:** DM Sans, weights 400 and 500. `font-variant-numeric: tabular-nums` on prices and sizes.
- **Fallback stacks:** `"Cormorant Garamond", Garamond, "Times New Roman", serif` and `"DM Sans", "Helvetica Neue", Arial, sans-serif`.

Both are open-licensed, load from Google Fonts with `display=swap`, and together add about 90 KB with subsetting to Latin.

### 5.4 Type scale

| Role | Desktop | Mobile | Face and weight | Line height |
|---|---|---|---|---|
| Display (hero H1) | 56px | 36px | Cormorant 600 | 1.05 |
| H1 (page title) | 44px | 32px | Cormorant 600 | 1.1 |
| H2 (section) | 34px | 26px | Cormorant 600 | 1.15 |
| H3 (card title, module) | 24px | 20px | Cormorant 500 | 1.2 |
| Body large | 18px | 17px | DM Sans 400 | 1.55 |
| Body | 16px | 16px | DM Sans 400 | 1.55 |
| Small (fit notes, captions) | 14px | 14px | DM Sans 400 | 1.5 |
| Label (uppercase) | 12px | 12px | DM Sans 500, 0.08em tracking | 1.3 |
| Price | 16px | 16px | DM Sans 500, tabular | 1.3 |
| Button | 15px | 15px | DM Sans 500, 0.02em tracking | 1 |

Body text never sets below 16px on mobile. Running text is capped at 65 characters per line.

### 5.5 Buttons, cards, borders, icons, spacing

**Buttons.** Height 48px (44px minimum tap target satisfied), horizontal padding 24px, radius 2px. Primary: Ink fill, White text; hover darkens to `#000000`; focus ring 2px Beige deep offset 2px. Secondary: Beige fill, Ink text; hover to Beige deep. Tertiary: text link in Ink with a 1px underline in Beige deep, underline thickens on hover. Disabled: Cream fill, Stone text. Sticky mobile add-to-cart is a full-width Primary.

**Cards.** No shadow. White ground on Cream sections, Cream ground on White sections. Radius 2px. Image ratio 3:4, `object-fit: cover`. A shape label row sits under the title: up to three letter chips (H, A, X) in Beige with Ink text, 12px label style, plus "+2" when more apply. Hover: image swaps to the second photo and the quick-view control fades in at the bottom of the image. Wishlist is a 20px outline heart at top right of the image, filled in Ink when saved.

**Shape cards.** Beige ground, 4:5 image, letter set large in Cormorant 600 at 64px in Ink, the display name beneath, the descriptor in Charcoal at 14px, and a Primary button "Shop shape H". Cards are equal height in a five-column row on desktop, a horizontally scrolling row of 1.3 visible cards on mobile with snap points.

**Borders and dividers.** 1px Beige on White and Cream grounds; 1px Beige deep on Beige grounds. Section dividers are whitespace, not lines, except between product-page accordions.

**Icons.** Outline, 1.5px stroke, 20px in navigation and 24px in the mobile bar, Ink. One family throughout (Lucide meets the spec and is MIT). No filled icons except the saved-wishlist heart and the active state of the mobile tab bar.

**Spacing.** 8px base. Scale: 4, 8, 12, 16, 24, 32, 48, 64, 96, 128. Section padding 96px desktop, 48px mobile. Grid gutter 24px desktop, 16px mobile. Container max-width 1280px with 48px side padding on desktop, 16px on mobile. Product grid: 4 columns desktop, 2 columns mobile.

**Radius.** 2px on buttons, inputs, cards, and chips. 999px on the progress indicator and letter chips only.

**Motion.** 160ms ease-out for hover states, 240ms for drawers and the quick view, 320ms for the quiz step transition. All motion disabled under `prefers-reduced-motion`. No scroll-triggered entrance animations.

### 5.6 Balancing black, white, and beige

The rule is 70 / 25 / 5 by area on any screen: 70 percent white or cream ground, 25 percent beige surfaces, 5 percent ink (type, buttons, the logo). Black is never a background larger than a button, except the footer, which is Ink with Cream type and is the only large dark surface on the site.

Screen-by-screen:

- **Homepage.** White hero with the image carrying the warmth. Cream band for the shape cards, which are Beige. White for products. Cream for the how-it-works and story sections. Ink footer.
- **Shape page.** Cream header band with the guide copy; White product grid; Beige outfit row between them.
- **Quiz.** Cream ground throughout; answer tiles are White with a Beige deep border when selected; progress bar is Beige with Ink fill.
- **Result page.** Beige hero panel with the letter and name; White below.
- **Product page.** White throughout; the fit module is a Beige panel; accordions are separated by 1px Beige rules.
- **Cart drawer.** White with a Cream footer holding the checkout button.
- **Announcement bar.** Beige with Ink text, one message.

---

## Decisions needed before Phase 5

1. Approve or amend the shape display names in section 2.9.
2. Choose the tagline (section 2.10 recommends "Chosen for your shape").
3. Add the logo file (SVG or high-resolution PNG) and the brand reference image to `reference/brand/` in this repository so the palette and logotype match can be measured rather than estimated.
4. Allow saahvay.com and cdn.shopify.com in the environment network policy, or add a theme export and product CSV under `reference/`, so the audit's expected and reported items can be confirmed on the live store.
5. Confirm the real shipping, returns, and support terms so trust copy can be written accurately.
6. Confirm whether outfits will be sold as Shopify bundles (native Bundles app) or as linked products added together via the cart API. Phase 7 depends on this.
