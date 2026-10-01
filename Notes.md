# Mistvale Tea Co. — Assessment Notes

## 1. What I changed

I started from the provided Mistvale Tea Co. store and focused on fixing the existing functionality while keeping the original design and structure intact.

### Bugs and business rules fixed

- Product prices are calculated from the `PRODUCTS` data rather than relying on values stored in the cart or displayed text.
- Cart quantities are limited to a maximum of 5 per product and cannot exceed available stock.
- Invalid, unavailable, or sold-out products are removed/normalised when restoring a persisted cart.
- Sold-out products cannot be added to the cart.
- The `WELCOME10` coupon:
  - is case-insensitive
  - requires a minimum subtotal of ₹399
  - gives 10% off eligible products
  - excludes products in the `Gifts` category
  - is capped at ₹150
  - does not produce an additional effect when applied repeatedly
- Shipping is calculated as ₹49 unless the free-shipping threshold is reached after applying the discount.
- Only the final order total is rounded to the nearest rupee.
- Currency values use the ₹ symbol and Indian number formatting.
- Search, category filtering and sorting now work together without losing the current search query.
- Sold-out products remain at the end of sorted product lists.
- Checkout submits product IDs and quantities in the required JSON format.
- Added Open Graph metadata for SEO/social sharing.
- Added JSON-LD structured data for the organization, products and FAQ.
- Kept the provided API unchanged.
- Kept the product IDs, names and prices unchanged.
- Kept the checkout contract unchanged.
- Kept the approved legal footer text unchanged.

The existing CSS/design was intentionally left unchanged because the requested approach was to make only the necessary fixes rather than redesign working parts of the page.

---

## 2. What the AI got wrong

AI-generated changes were treated as suggestions rather than automatically accepted.

During implementation, I checked the generated logic against the assessment rules, especially:

- Product prices must come from `PRODUCTS`.
- Gift products must not receive the welcome discount.
- The coupon must have the ₹399 minimum subtotal and ₹150 maximum discount.
- Cart quantities must respect both the 5-unit limit and stock.
- Sold-out products must remain last when sorting.
- Search results must remain consistent with the currently typed search query.
- The checkout payload must contain product IDs and quantities rather than relying on presentation data.

I also avoided changing the provided API, product data, checkout contract, legal text, or the existing CSS unnecessarily.

---

## 3. Images

The store uses the provided/created Mistvale image assets in the `images/` directory.

The required image set consists of:

- Mistvale Tea Co. logo
- Hero/banner image
- Assam Breakfast Black Tea
- Darjeeling First Flush
- Kashmiri Kahwa
- Masala Chai Blend
- Nilgiri Green Tea
- Chamomile & Tulsi
- Hibiscus Rose Infusion
- Tea Lover's Sampler Gift Box

Images were used as web assets rather than embedding them directly into the HTML.

---

## 4. How I tested it

I tested the store through normal shopper flows, including:

- Product browsing
- Category filtering
- Search
- Sorting
- Quick view
- Adding products to the cart
- Increasing/decreasing quantities
- Removing products
- Cart persistence
- Sold-out product behaviour
- Coupon application
- Coupon eligibility
- Coupon cap
- Free shipping calculation
- Checkout payload
- Delivery/pincode check
- FAQ and other page interactions
- Responsive layout

I also checked the JavaScript syntax after the final changes using Node.js.

The final JavaScript syntax check passed.

The assessment specifically requires responsive behaviour, accessibility, SEO and interaction testing, so these areas were considered during the final review.

---

## 5. Questions for the team

No blocking questions remain.

One implementation decision that required clarification from the supplied page was the free-shipping threshold. The existing store announcement states that free shipping applies above ₹499, so the implementation keeps the existing ₹499 threshold rather than inventing a new value.

---

## 6. Time spent

Approximately 4 hours including:

- understanding the existing implementation
- reviewing the assessment requirements
- debugging the store
- implementing the required fixes
- reviewing the result
- testing the main shopper flows
- preparing the submission documentation

---

## 7. Extra features I added

No major bonus features were added.

I prioritised fixing the required assessment functionality and preserving the existing design rather than adding features that could introduce unnecessary risk.

SEO improvements were added as part of the required technical work:

- Open Graph metadata
- Organization structured data
- Product structured data
- FAQ structured data

---

## 8. With more time I would…

With additional time I would:

- perform a more extensive accessibility audit with a screen reader
- run a Lighthouse audit and address any remaining performance/accessibility opportunities
- test additional real-device viewport sizes
- optimise and verify all image file sizes and formats
- perform additional edge-case testing around rapid interactions and persisted cart state
- further review structured data against the final rendered content

The priority would remain stability and correctness rather than adding unnecessary features.