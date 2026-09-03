# SaahVay: Product Marketing Context

Read by every marketing skill before it does anything. Keep this file current. Source of truth for strategy is `docs/strategy/saahvay-redesign-strategy.md`.

## Product

SaahVay (saahvay.com) is a Shopify store selling women's clothing and complete outfit combinations, selected and labelled by body shape. Five shapes are used: H (Rectangle), O (Apple), V (Inverted Triangle), X (Hourglass), A (Pear). Body shape is a guidance layer; standard clothing sizes still apply on every product. Products are sourced from suppliers and brokers and imported into Shopify, then cleaned and tagged before publication.

Entry pricing is roughly 42 to 48 USD (observed from the search index, September 2026). Currency and shipping markets: to be confirmed. The business is operated by Grow Consulting (admin@growconsulting.ca).

## Customer

Women, late twenties to late fifties, who shop online, dislike it, and have had disappointing purchases. Professionals, business owners, mothers, women with active lives. They want to look good without spending hours, want guidance on what suits them, and do not want to feel judged or labelled.

## Problem

She cannot tell from a product photo whether a piece will flatter her, so she buys and returns, buys and never wears, or gives up. Size charts answer "will it fit", not "will it look right on me".

## Positioning

For women who want to look good without spending hours shopping or gambling on returns, SaahVay is the online fashion store that curates clothing and complete outfits by body shape. Unlike general fashion stores that leave you to guess, SaahVay tells you which pieces are selected for your shape and why.

Brand essence: fashion chosen for your shape, so you can stop guessing.
Recommended tagline: Chosen for your shape.

## Messaging pillars

1. Chosen for your shape (every product names its shapes and why)
2. Outfits, not just items
3. Minutes, not hours
4. Honest fit (real measurements, model sizes, plain returns policy)
5. Guidance without judgement

## Voice

Warm, direct, competent. Short sentences, second person, present tense. Recommend, never guarantee: "selected for", "designed to complement", "often works well for". Never: flatter your flaws, hide, slimming, problem area, empowerment, journey, elevate, safe space, trendy, sexy. No exclamation marks in product or navigation copy. No unverifiable claims (no "24/7 support", no "30-day trial" unless literally true).

## Shape display names

Lead with the letter and a positive descriptor; keep the common name as a secondary label for recognition and search.

| Letter | Display | Secondary |
|---|---|---|
| H | Shape H | Rectangle |
| O | Shape O | Apple |
| V | Shape V | Inverted Triangle |
| X | Shape X | Hourglass |
| A | Shape A | Pear |

## Visual identity

Black (`#141414`), white, cream (`#F7F3EC`), warm beige (`#D9C8AD`, to be re-sampled from the logo file). Headings in Cormorant Garamond, everything else in DM Sans. No gradients, no gold, no bright accents, no large black surfaces except the footer. Photography: real, diverse women, editorial, consistent 3:4 crops.

## Competitors and alternatives

General women's fashion Shopify stores and marketplaces (no shape guidance), styling-guide content sites (guidance but no shop), and personal stylist services (guidance but expensive and slow). SaahVay sits between the last two: guidance built into a store.

## Key pages and funnel

Homepage → shape selection or 60-second quiz → result page (email capture after value) → shape collection or outfit → product page with fit module → cart drawer → Shopify checkout → post-purchase "how did it fit" email.

## Data model (Shopify)

Product metafields: `saahvay.shapes_primary` (list of letters), `saahvay.shapes_secondary` (list), `saahvay.why_it_works` (text), `saahvay.fit_notes`, `saahvay.publish_ready` (boolean). Tags are namespaced for filtering: `shape:H`, `occasion:work`, `fit:relaxed`, `length:midi`. Compare-at price must be empty or greater than price.

## Open items

Logo file and brand reference not yet in the repository. Live site not yet inspected directly (network policy). Real shipping, returns, and support terms to be confirmed. Outfit mechanism (Shopify Bundles vs cart API) to be decided.
