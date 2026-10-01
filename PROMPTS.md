# Mistvale Tea Co. — AI Prompt Log

This document records the AI-assisted prompts used during the development and refinement
of the Mistvale Tea Co. store.

---

## Prompt 1

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Review the provided Mistvale Tea Co. index.html against the assessment requirements.
> Identify the existing JavaScript issues and business-rule violations, especially around
> cart quantities, product pricing, coupons, shipping, sorting, search/filter interaction,
> sold-out products, checkout data, and persisted cart state. Do not modify anything yet.
> Give me a concise list of the changes that are actually required.

- Outcome: accepted
- Why: Used to identify the concrete functional issues before making changes.

---

## Prompt 2

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Review the existing CSS in the provided Mistvale Tea Co. index.html against the
> assessment and brand requirements. Do not redesign the page unnecessarily. Identify
> only CSS issues that are explicitly required to be fixed. If the existing CSS already
> satisfies the requirements, recommend leaving it unchanged.

- Outcome: accepted
- Why: The existing CSS already covered the required visual system and responsive
  behaviour, so unnecessary CSS changes were avoided.

---

## Prompt 3

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Make only the changes required by the Mistvale assessment. Do not redesign the existing
> UI and do not make unrelated refactors.
>
> Fix the business logic while preserving the existing HTML structure and styling.
>
> Requirements:
> - Always calculate prices from PRODUCTS.
> - Limit each product to a maximum quantity of 5 and never above stock.
> - Prevent sold-out products from being added.
> - Restore persisted carts safely and remove invalid or unavailable products.
> - Implement WELCOME10 correctly: case-insensitive, minimum subtotal ₹399,
>   10% discount on eligible products, maximum discount ₹150, and exclude Gifts.
> - Applying the coupon more than once must not increase the discount.
> - Shipping must be ₹49 unless the free-shipping threshold is reached after discount.
> - Round only the final total.
> - Use Indian currency formatting.
> - Keep sold-out products last in every sort order.
> - Make search, category filtering and sorting work together.
> - Ensure current search text is never lost when filters or sorting change.
> - Preserve the provided API object exactly as supplied.
> - Preserve PRODUCT ids, names and prices.
> - Preserve the checkout form contract.
> - Preserve the existing legal text.
>
> Do not change anything else.

- Outcome: modified
- Why: The generated implementation was reviewed and adjusted to ensure each assessment
  rule was satisfied without changing unrelated parts of the store.

---

## Prompt 4

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Update the cart logic so persisted cart data is validated against PRODUCTS when the page
> loads. Remove products that no longer exist or are sold out, refresh the product name and
> price from PRODUCTS, and clamp each quantity to the smaller of 5 and available stock.
> Keep the existing cart structure and UI unchanged.

- Outcome: accepted
- Why: This fixed persisted-cart edge cases while preserving the existing implementation.

---

## Prompt 5

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Fix all cart price calculations so they always read the current product price from
> PRODUCTS using the product id instead of trusting stored cart prices. Keep the existing
> cart UI and functionality unchanged.

- Outcome: accepted
- Why: This ensures the cart follows the assessment requirement that PRODUCTS is the
  source of truth for prices.

---

## Prompt 6

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Implement the WELCOME10 coupon rules exactly:
>
> - Code is case-insensitive.
> - Cart subtotal must be at least ₹399.
> - Discount is 10% of eligible items.
> - Products in category "Gifts" are excluded.
> - Maximum discount is ₹150.
> - Do not round the discount early.
> - Applying the coupon repeatedly must not increase the discount.
> - Invalid coupon codes must not leave an old discount active.
>
> Preserve the existing coupon UI.

- Outcome: accepted
- Why: The coupon calculation was updated to follow the assessment rules without changing
  the surrounding UI.

---

## Prompt 7

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Fix the shipping and total calculation in the existing cart. Shipping is ₹49 unless the
> amount after discount reaches the existing free-shipping threshold. Calculate the final
> total from subtotal + shipping - discount and round only the final total to the nearest
> rupee. Keep the existing shipping progress UI and use Indian currency formatting.

- Outcome: accepted
- Why: Corrected the cart mathematics while retaining the existing presentation.

---

## Prompt 8

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Fix product sorting so sold-out products always appear after all in-stock products,
> regardless of whether the selected sort is price low-to-high, price high-to-low, or
> name. Then make sure the current search query and category filter continue to work
> correctly with the selected sort.

- Outcome: accepted
- Why: This addressed the interaction between sorting, availability, search and filtering.

---

## Prompt 9

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Fix the search and category-filter interaction in the existing Mistvale store. If a
> search query is currently active, category changes must continue to respect the typed
> search query. Search results must also preserve the active sorting behaviour. Do not
> clear or replace the user's current search text.

- Outcome: accepted
- Why: This fixed the R7 requirement without restructuring the product filtering system.

---

## Prompt 10

- Tool: ChatGPT (GPT-5)
- Type: code
- Prompt:

> Fix the checkout payload so the existing checkout form submits the required contract.
> The items field should contain a JSON array containing only product IDs and quantities,
> for example [{"id":101,"qty":2}], and the coupon field should contain the applied coupon
> code or an empty value. Do not change the form action, method, field names, or checkout UI.

- Outcome: accepted
- Why: The checkout payload was aligned with the assessment contract while keeping the form
  itself unchanged.

---

## Prompt 11

- Tool: ChatGPT (GPT-5)
- Type: SEO
- Prompt:

> Improve the existing Mistvale Tea Co. SEO implementation without changing the visible
> design. Add the required Open Graph metadata and structured data for the organization,
> all provided products, and the FAQ. Use only information already present in the provided
> project files. Do not invent reviews, ratings, awards, company claims, or product facts.

- Outcome: accepted
- Why: Added the required SEO metadata and JSON-LD while keeping the page content and
  product information grounded in the supplied data.

---

## Prompt 12

- Tool: ChatGPT (GPT-5)
- Type: review
- Prompt:

> Perform a final review of the modified Mistvale Tea Co. index.html against the assessment.
> Check that the required business rules are implemented, the API object was not changed,
> product IDs/names/prices were not changed, the checkout contract is preserved, the legal
> text is unchanged, and no unnecessary CSS or UI changes were introduced. Report only
> remaining issues that actually need fixing.

- Outcome: accepted
- Why: Used as the final verification pass before submission.

---

## Prompt 13

- Tool: ChatGPT (GPT-5)
- Type: review
- Prompt:

> The Mistvale store is now working correctly. Do not make additional changes. Prepare
> the required NOTES.md and PROMPTS.md submission documentation based only on the work
> completed in this project.

- Outcome: accepted
- Why: Used to move from implementation to submission preparation without introducing
  unnecessary code changes.