# Feature Spec: Ouroboros Jewellery Online Store

Status: Draft v2
Source: business-context-spec.md, functional-spec.md
Last updated: 2026-06-12

## 1. Purpose

This feature spec converts the current business and functional requirements into a prioritized build backlog for the Ouroboros Jewellery website.

The target product is a custom UK ecommerce store where customers can browse premium Ouroboros-inspired silver and white gold jewellery, understand each product, select required variants, build a cart, create an account, pay securely in GBP, and receive clear post-purchase communication.

## 2. Priority Definitions

- P0: Required for a public, sellable launch.
- P1: Required for the broader current product scope, but can follow the first sellable launch if a smaller MVP is needed.
- P2: Optional, later, or dependent on a separate business decision.

## 3. Resolved Build Decisions

- Platform is custom ecommerce, not a marketplace or off-the-shelf admin-first build.
- Product, order, inventory, refund, fulfilment, enquiry, content, and email preference data are developer/operator managed.
- A separate admin management interface is not required for the current version.
- Sales are GBP only.
- Displayed prices include VAT or other applicable taxes.
- UK shipping is free.
- UK shipping includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Channel Islands, Isle of Man, and BFPO addresses.
- Account creation or sign-in is required before payment and order placement.
- Guest browsing and guest cart building are allowed.
- Guest carts do not merge into saved logged-in customer carts.
- Wishlist requires login.
- Internal product search is out of scope.
- Infinite scroll is out of scope.
- Payment is single upfront payment only.
- Instalments and split payments are out of scope.
- Payment providers include Stripe, PayPal, Square, and Airwallex.
- The store must not store raw payment card details.
- Stock is reserved when an item is added to cart.
- Wishlist does not reserve stock.
- Overselling is not allowed for stock-tracked items.
- Made-to-order capacity is 1-20 pieces per 3-week period.

## 4. Launch Feature Set

The P0 launch is considered sellable when these journeys work end to end:

1. A customer can browse home, shop, category, collection, and product pages.
2. A customer can evaluate product imagery, material, symbolic meaning, size, weight, care, packaging, shipping, returns, availability, and GBP price.
3. A customer can select required variants, especially UK ring size.
4. A customer can add available products to cart and reserve stock.
5. A customer can update cart quantity, remove items, and resolve invalid or expired cart items.
6. A customer can create an account or sign in before payment.
7. A customer can check out only with a supported UK delivery address.
8. A customer can pay securely through approved external payment providers.
9. Successful payment creates an order and sends confirmation.
10. Failed payment gives a retry path without losing cart contents.
11. Sold out and coming soon products cannot be purchased.
12. Made-to-order products show lead time and capacity expectations before payment.
13. Required policy, contact, shipping, returns, privacy, cookie, terms, and gifting pages are live.
14. Developer/operator workflows can manage products, images, variants, stock, reservations, orders, tracking, refunds, enquiries, and content.

## 5. Feature Map

| ID | Feature | Priority | Primary Users |
| --- | --- | --- | --- |
| F-001 | Platform, Environments, And Source Of Truth | P0 | Developer/Operator |
| F-002 | Site Navigation And Layout | P0 | Guest, Customer |
| F-003 | Homepage | P0 | Guest, Customer |
| F-004 | Product Catalogue Data | P0 | Developer/Operator, Customer |
| F-005 | Product Browsing, Filtering, And Sorting | P0 | Guest, Customer |
| F-006 | Collection And Category Pages | P0 | Guest, Customer |
| F-007 | Product Detail Pages | P0 | Guest, Customer |
| F-008 | Ring Size Selection And Guide | P0 | Guest, Customer |
| F-009 | Cart And Stock Reservations | P0 | Guest, Customer |
| F-010 | Customer Authentication | P0 | Guest, Customer |
| F-011 | UK Checkout | P0 | Customer |
| F-012 | Payment Provider Integration And Order Creation | P0 | Customer, Developer/Operator |
| F-013 | Shipping, Fulfilment, And Mixed Carts | P0 | Customer, Developer/Operator |
| F-014 | Order Lifecycle | P0 | Customer, Developer/Operator |
| F-015 | Transactional Emails | P0 | Customer, Developer/Operator |
| F-016 | Contact And Enquiries | P0 | Guest, Customer, Developer/Operator |
| F-017 | Required Content And Policy Pages | P0 | Guest, Customer |
| F-018 | Developer/Operator Product And Inventory Operations | P0 | Developer/Operator |
| F-019 | Developer/Operator Order And Support Operations | P0 | Developer/Operator |
| F-020 | Security And Abuse Protection | P0 | All |
| F-021 | Accessibility, SEO, And Performance | P0 | Guest, Customer |
| F-022 | Error And Empty States | P0 | Guest, Customer |
| F-023 | Customer Account Area | P1 | Customer |
| F-024 | Wishlist | P1 | Customer |
| F-025 | Newsletter And Marketing Preferences | P1 | Guest, Customer, Developer/Operator |
| F-026 | Privacy, Cookies, Analytics, And Consent Tracking | P1 | Guest, Customer, Developer/Operator |
| F-027 | Back-In-Stock And Launch Notifications | P2 | Guest, Customer |
| F-028 | Gift Message Options | P2 | Guest, Customer |
| F-029 | Discounts, Gift Cards, Store Credit, And Promotions | P2 | Customer, Developer/Operator |

## 6. Feature Specifications

### F-001 Platform, Environments, And Source Of Truth

Priority: P0

Goal: Establish the custom ecommerce foundation and reliable operational data ownership.

Requirements:

- Build on a custom ecommerce platform.
- Support local, staging, and production environments.
- Define a system of record for products, variants, inventory, reservations, customers, orders, payments, enquiries, marketing consent, and audit events.
- Use developer/operator managed workflows instead of a required separate admin interface for the current version.
- Protect operational workflows behind developer/operator-only access.

Acceptance criteria:

- Local, staging, and production configuration can be separated.
- Product, order, inventory, and customer data have one clear source of truth.
- Operational updates can be performed without editing customer-facing code paths directly.

### F-002 Site Navigation And Layout

Priority: P0

Goal: Provide clear routes into shopping, account, cart, wishlist, brand, support, and policy content.

Requirements:

- Primary navigation includes Home, Shop all, Collections, Bracelets, Necklaces, Rings, Ring size guide, About, and Contact.
- Utility navigation includes Account, Wishlist, and Cart.
- Footer navigation includes Shipping information, Packaging and gifting, Returns and exchanges, Privacy policy, Cookie policy, Terms and conditions, Contact, and newsletter route.
- Header and footer are available across public pages.
- Cart item count is visible when cart contains items.
- Mobile navigation supports all primary and utility routes.

Acceptance criteria:

- A customer can reach product listings within one click from the homepage.
- Policy pages are reachable from the footer.
- Mobile navigation does not hide cart, account, or contact routes.

### F-003 Homepage

Priority: P0

Goal: Introduce the brand and route customers into product discovery.

Requirements:

- Show the Ouroboros Jewellery brand name clearly.
- Use jewellery-led visual direction.
- Include concise positioning around eternity, renewal, transformation, and premium craftsmanship.
- Feature selected collections.
- Feature selected products.
- Link to Bracelets, Necklaces, and Rings.
- Surface UK-only free shipping and gift-appropriate packaging trust signals.
- Include newsletter signup or route where enabled.

Acceptance criteria:

- The page clearly communicates that the site sells jewellery.
- A customer can navigate from the homepage to a product listing.
- UK-only delivery and GBP pricing context are discoverable before checkout.

### F-004 Product Catalogue Data

Priority: P0

Goal: Store structured product data needed for browsing, purchase, inventory, and order snapshots.

Requirements:

- Product records include SKU, slug, category, collection, material, purity or fineness, finish, dimensions, weight, description, symbolic meaning, care guidance, packaging note, returns note, GBP price, VAT/tax display, availability, low-stock threshold, made-to-order lead time, publish state, SEO title, and SEO description.
- Variant records support ring size, chain length, bracelet size, clasp type, engraving, stones, texture, or other purchase-relevant options.
- Ring variants are tracked by UK ring size.
- Product image records support main, detail, scale, worn, angle, and packaging images.
- Product image records include alt text, sort order, and primary image flag.
- Collection records include name, slug, story, symbolic theme, hero image, SEO title, SEO description, sort order, and publish state.

Acceptance criteria:

- Product listing and detail pages render without hardcoded product data.
- Unpublished products do not appear publicly.
- Every purchasable product has price, availability, material, category, collection, and at least one image.

### F-005 Product Browsing, Filtering, And Sorting

Priority: P0

Goal: Let customers browse and narrow the catalogue without internal keyword search.

Requirements:

- Shop All displays a product grid.
- Product cards show image, name, category, collection, material, availability, and GBP price.
- Filters include category, collection, material, availability, price range, and ring size where relevant.
- Filters can be cleared.
- Empty filter results show useful copy and a route back to all products.
- Sorting includes availability at minimum.
- Price and newest sorting are enabled if supporting data exists.
- Sold out and coming soon products can be visible but cannot be added directly to cart.
- Internal product search is not included.
- Infinite scroll is not used.

Acceptance criteria:

- Customers can filter products and clear filters.
- Customers can distinguish purchasable, sold out, coming soon, low-stock, and made-to-order products.
- Empty filtered results do not trap the customer.

### F-006 Collection And Category Pages

Priority: P0

Goal: Provide browsing paths by product type and symbolic collection.

Requirements:

- Category pages exist for Bracelets, Necklaces, and Rings.
- Each category page behaves like a filtered product listing.
- Ring category page includes ring size filtering and a link to the ring size guide.
- Ring category page states that UK sizing is the default.
- Collection pages include title, symbolic story, product grid, and optional hero image.
- Product cards on collection and category pages match Shop All card data.
- Empty collection and category pages remain functional.

Acceptance criteria:

- Category routes only show products from the selected category.
- Collection routes show products from the selected collection.
- Ring customers can reach size guidance from the ring category page.

### F-007 Product Detail Pages

Priority: P0

Goal: Give customers enough information to decide whether to buy.

Requirements:

- Show product name, SKU or reference where appropriate, category, collection, material, purity or fineness, finish, availability, description, symbolic meaning, dimensions, weight, care, packaging, UK-only free shipping, returns, and GBP price.
- Show VAT-inclusive or applicable tax wording.
- Show made-to-order lead time where applicable.
- Show hallmarking or material-compliance information where relevant.
- Include product image gallery with main image and supporting detail views.
- Include variant selector where applicable.
- Include quantity selector where applicable.
- Include Add to Cart action.
- Include Wishlist action or login prompt if wishlist is enabled.

Add to cart rules:

- In stock products can be added to cart.
- Low stock products can be added to cart with honest urgency messaging.
- Sold out products cannot be added to cart.
- Coming soon products cannot be added to cart.
- Made-to-order products can be added only when lead time and capacity expectations are shown.
- Rings require selected UK ring size before add to cart.

Acceptance criteria:

- Add to Cart is disabled until required options are selected.
- Unavailable products explain why purchase is blocked.
- Product details include all purchase-critical material, sizing, care, packaging, shipping, and returns information.

### F-008 Ring Size Selection And Guide

Priority: P0

Goal: Help customers select the correct UK ring size before buying.

Requirements:

- Ring products require size selection before cart add.
- Available ring sizes are displayed in UK format.
- Ring size availability is shown where stock data exists.
- Made-to-order ring handling is shown where relevant.
- Ring size guide uses UK sizes as the primary format.
- Guide includes measuring instructions, advice for unsure customers, support contact link, and advisory disclaimer.
- Ring product pages link to the guide.

Acceptance criteria:

- A ring cannot be added to cart without a selected UK size.
- UK sizing is visually dominant on the guide.
- Customers can reach sizing help from ring product pages.

### F-009 Cart And Stock Reservations

Priority: P0

Goal: Let customers review selected items and reserve available stock before checkout.

Requirements:

- Cart displays product image, product name, selected variant, availability messages, unit price, quantity, line total, subtotal, free UK shipping note, tax wording, remove action, and checkout button.
- Customers can update quantity where quantity is allowed.
- Customers can remove items.
- Quantity cannot exceed available stock or made-to-order capacity.
- Stock is reserved when an item is added to cart.
- Reservation expiry is configurable.
- Expired reservations are released.
- Sold out and coming soon items block checkout.
- Invalid or sold out cart items must be removed or adjusted before payment.
- Price changes update to the current price in cart and payment.
- Made-to-order lead time appears in cart.
- Guest carts do not merge into saved logged-in carts.
- If guest and saved account carts both exist, the active cart behavior must be clear and must not duplicate line items.

Acceptance criteria:

- Customers can update or remove one item without losing the rest of the cart.
- Cart state survives payment failure.
- Cart clearly explains expired, unavailable, or invalid items.
- Stock reservations prevent overselling within the configured reservation window.

### F-010 Customer Authentication

Priority: P0

Goal: Provide secure accounts required for purchase.

Requirements:

- Customers can register with unique email and password.
- Customers can log in and log out.
- Customers can request password reset.
- Passwords are securely hashed.
- Password reset links expire.
- Authenticated sessions are protected.
- Customer must be authenticated before payment.
- Sensitive account changes require confirmation.

Acceptance criteria:

- Duplicate customer emails are rejected.
- Customers can recover access through password reset.
- Guests cannot submit payment or place an order.

### F-011 UK Checkout

Priority: P0

Goal: Collect customer, delivery, shipping, billing, and consent details for a UK-only order.

Requirements:

- Checkout steps include cart review, sign-in or account creation, contact details, UK delivery address, shipping confirmation, billing address if different, payment, and confirmation.
- Collect email, name, UK delivery address, billing address if different, phone where required, marketing opt-in choice, and gift message if enabled.
- UK address fields support addressee, organization, unit or flat, building or house number and street, locality, POST TOWN in ALL CAPS, and postcode.
- Delivery must be limited to supported UK addresses.
- Required address and contact fields must be validated.
- Required variants must remain selected.
- Product availability, reservation, capacity, and current price must be rechecked before payment.
- Checkout totals show product price, quantity, selected option, free shipping, tax wording, and total in GBP.

Acceptance criteria:

- Non-UK delivery addresses cannot complete checkout.
- Missing required fields show field-level validation.
- Customer must sign in or create an account before payment.
- Checkout revalidates stock and price before payment.

### F-012 Payment Provider Integration And Order Creation

Priority: P0

Goal: Process payment securely and create accurate order records.

Requirements:

- Support credit card, digital wallet, and bank transfer payment methods.
- Integrate approved external payment providers: Stripe, PayPal, Square, and Airwallex.
- Support single upfront payment only.
- Do not support instalments or split payments.
- Do not store raw payment card data.
- Payment must fail or be prevented when required payment information is missing, funds are unavailable, item stock is invalid, or made-to-order capacity is unavailable.
- Successful payment creates an order unless the provider flow requires pending-payment order creation first.
- Order item records snapshot product name, variant label, SKU, quantity, unit price, line total, and made-to-order lead time.

Acceptance criteria:

- Successful payment creates an order.
- Successful payment triggers order confirmation email.
- Payment failure gives a retry path without losing the cart.
- Order totals match checkout totals.

### F-013 Shipping, Fulfilment, And Mixed Carts

Priority: P0

Goal: Communicate UK-only free tracked shipping and handle in-stock plus made-to-order fulfilment.

Requirements:

- Shipping boundary includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Channel Islands, Isle of Man, and BFPO addresses.
- Shipping is free for UK orders.
- Shipping information appears on product pages, cart, checkout, shipping page, and order confirmation.
- Deliveries use carrier services and tracking.
- Made-to-order items show average lead time of 2-10 weeks unless product data overrides it.
- Mixed carts warn that combined shipping waits until made-to-order items are ready.
- Customer can accept combined shipping or decline it if separate shipping is supported.
- Customer receives notification when made-to-order item is ready to ship.

Acceptance criteria:

- Customers see UK-only free shipping before payment.
- Mixed cart shipping expectations are explicit before payment.
- Tracking information can be communicated after dispatch.

### F-014 Order Lifecycle

Priority: P0

Goal: Track orders from payment through fulfilment, cancellation, return, and refund states.

Supported statuses:

- Pending payment.
- Payment failed.
- Paid.
- Processing.
- Made to order.
- Ready to dispatch.
- Dispatched.
- Delivered.
- Cancelled.
- Refunded.
- Partially refunded.
- Returned.

Requirements:

- Define which actor or process can change each status.
- Define which status changes trigger emails.
- Customer order history shows order number, date, status, items, delivery address, total paid, and tracking details when available.
- Refund, return, and cancellation state changes preserve audit history.

Acceptance criteria:

- Paid orders are visible to the developer/operator workflow.
- Customers can understand the current state of an order.
- Status changes do not break payment, stock, or fulfilment records.

### F-015 Transactional Emails

Priority: P0

Goal: Send operational emails for account, checkout, payment, support, and fulfilment flows.

P0 emails:

- Password reset.
- Order confirmation.
- Payment failed.
- Order dispatched.
- Tracking information.
- Made-to-order ready to ship.
- Contact form acknowledgement if email service is configured.
- Refund issued if refunds are managed through the site or operational workflow.

P1 or conditional emails:

- Account verification.
- Order cancelled.
- Return or exchange update.
- Back-in-stock notification.
- Newsletter subscription confirmation if double opt-in is used.

Rules:

- Transactional emails must not include marketing content unless the customer separately opted in.
- Order confirmation includes order number, order summary, total paid in GBP, delivery details, expected dispatch or lead time, and support route.
- Dispatch email includes carrier and tracking number when available.

Acceptance criteria:

- Successful payment sends order confirmation.
- Payment failure sends or displays a clear failure message.
- Dispatch notification can be triggered when tracking is added or order is marked dispatched.

### F-016 Contact And Enquiries

Priority: P0

Goal: Give customers a reliable support route.

Requirements:

- Contact page displays customer service email address.
- Contact form collects name, email, enquiry type, message, and optional order number.
- Enquiry types include Product question, Ring sizing help, Order status, Shipping question, Returns or exchange, Made-to-order enquiry, and General enquiry.
- Contact form includes privacy note.
- Successful submission shows confirmation.
- Developer/operator or support recipient receives enquiry details.

Acceptance criteria:

- Customer can submit a valid enquiry.
- Invalid email or missing required fields are rejected with clear errors.
- Enquiry type is stored or included in support notification.

### F-017 Required Content And Policy Pages

Priority: P0

Goal: Provide trust, legal, operational, and pre-purchase information.

Required pages:

- About the brand.
- Shipping information.
- Packaging and gifting.
- Returns and exchanges.
- Privacy policy.
- Cookie policy.
- Terms and conditions.
- Contact.

Requirements:

- Footer links to required policy pages.
- Product pages expose or link to shipping, packaging, care, and returns information.
- Checkout links to returns, cancellation, terms, privacy, and shipping information.
- Legal business name, business address, and customer service email are included where required.
- Precious metal descriptions are accurate.
- Hallmarking and Online Dealer's Notice requirements are confirmed and implemented where required.
- Legal and policy copy is reviewed before launch.

Acceptance criteria:

- Customers can find shipping, returns, privacy, terms, and contact information before checkout.
- Product material claims are not vague or misleading.
- Required legal pages are not hidden behind account or checkout walls.

### F-018 Developer/Operator Product And Inventory Operations

Priority: P0

Goal: Let the business manage catalogue, images, variants, inventory, availability, and reservations.

Requirements:

- Developer/operator can create, edit, archive, publish, and unpublish products.
- Developer/operator can assign category and collection.
- Developer/operator can set material, dimensions, weight, care, packaging, returns note, symbolic meaning, and SEO fields.
- Developer/operator can upload and reorder product images.
- Developer/operator can create and manage variants.
- Developer/operator can set availability status.
- Developer/operator can set made-to-order lead time and capacity.
- Developer/operator can view stock by product and variant.
- Developer/operator can adjust stock.
- Developer/operator can manage or inspect cart reservations.
- Sensitive stock and reservation changes are recorded in audit history.

Acceptance criteria:

- A complete product can be published through the defined operational method.
- Variant stock can be managed for ring sizes.
- Public availability updates after stock or status changes.

### F-019 Developer/Operator Order And Support Operations

Priority: P0

Goal: Let the business fulfil orders and handle customer support.

Requirements:

- Developer/operator can view orders.
- Developer/operator can search or filter orders by order number, email, status, and date through the defined operational method.
- Developer/operator can update fulfilment status.
- Developer/operator can add carrier and tracking number.
- Developer/operator can mark an order dispatched.
- Developer/operator can trigger dispatch email.
- Developer/operator can handle cancellation and refund actions through approved provider or workflow.
- Developer/operator can view enquiries, filter by enquiry type, and mark them open, pending, or resolved.
- Developer/operator can export orders and marketing subscribers where legally permitted.

Acceptance criteria:

- Paid orders are visible for fulfilment.
- Dispatch tracking can be added and communicated.
- Support enquiries are not lost after submission.

### F-020 Security And Abuse Protection

Priority: P0

Goal: Protect customer data, payment flow, operational tooling, and public forms.

Requirements:

- HTTPS everywhere in production.
- Secure password hashing.
- Secure session cookies.
- Password reset tokens expire.
- Rate limiting for login, register, password reset, checkout, and contact forms.
- CSRF protection where relevant.
- Input validation and output escaping.
- Protection against common injection and cross-site scripting risks.
- Developer/operator-only access controls for operational workflows.
- Audit logging for sensitive operational actions.
- Fraud review flow for suspicious orders.
- No raw payment card storage.

Acceptance criteria:

- Guest users cannot access customer-only or operational routes.
- Public forms reject invalid input and limit abuse.
- Payment processing uses provider-secure flows.

### F-021 Accessibility, SEO, And Performance

Priority: P0

Goal: Make the store usable, discoverable, and fast enough for launch.

Requirements:

- Mobile-first responsive design.
- Keyboard navigable menus, forms, product options, cart, and checkout.
- Visible focus states.
- Sufficient text contrast.
- Product image alt text.
- Form labels connected to inputs.
- Error messages connected to fields.
- Ring size and variant controls usable by screen readers.
- SEO-friendly URLs.
- Unique page titles and meta descriptions.
- Product structured data where appropriate.
- Sitemap and robots rules.
- Optimised responsive images.
- Lazy loading for below-the-fold imagery.
- Checkout loads reliably on mobile connections.
- Non-essential scripts wait for consent where required.

Acceptance criteria:

- A keyboard user can add a product to cart and reach checkout.
- Product and collection pages have indexable metadata.
- Product imagery does not make listing and checkout pages unacceptably slow.

### F-022 Error And Empty States

Priority: P0

Goal: Keep customers oriented when something is unavailable, invalid, empty, or broken.

Required states:

- Product not found.
- Collection not found.
- No products in category.
- No products match filters.
- Cart empty.
- Wishlist empty if wishlist is enabled.
- Account order history empty.
- Product sold out.
- Product coming soon.
- Variant unavailable.
- Cart reservation expired.
- Made-to-order capacity unavailable.
- Checkout address invalid.
- Checkout non-UK address rejected.
- Checkout required account missing.
- Payment failed.
- Contact form failed.
- Newsletter signup failed if newsletter is enabled.
- Server error.
- Maintenance mode if needed.

Acceptance criteria:

- Each state explains what happened.
- Each state offers the next useful action.
- Failed payment and failed forms do not erase recoverable customer input.

### F-023 Customer Account Area

Priority: P1

Goal: Let registered customers manage details, addresses, orders, wishlist, and preferences.

Requirements:

- Account overview.
- Account details.
- Saved delivery addresses.
- Order history.
- Wishlist route.
- Newsletter preferences.
- Account deletion request or confirmation flow.
- Customers can add, edit, remove, and set default delivery addresses.
- Customers can view order number, date, status, items, delivery address, total paid, and tracking details when available.
- Account deletion warns that saved addresses, wishlist items, saved cart contents, and account preferences will be lost.

Acceptance criteria:

- Registered customers can view past orders.
- Saved addresses can be reused at checkout.
- Account pages are inaccessible to guests.

### F-024 Wishlist

Priority: P1

Goal: Let logged-in customers save products for later.

Requirements:

- Wishlist requires login.
- Guests clicking wishlist are prompted to sign in or create an account.
- Duplicate wishlist entries are prevented.
- Wishlist displays product image, name, selected variant where relevant, price in GBP, and availability.
- Customers can remove wishlist items.
- Customers can move available wishlist items to cart.
- Sold out and coming soon wishlist items cannot be moved to cart.
- Wishlist availability and price reflect current product data.
- Wishlist does not reserve stock.

Acceptance criteria:

- Wishlist persists across devices for the same account.
- Duplicate saves do not create duplicate rows.
- Moving wishlist item to cart follows product option, stock, and reservation rules.

### F-025 Newsletter And Marketing Preferences

Priority: P1

Goal: Collect and manage lawful marketing consent.

Requirements:

- Newsletter signup is optional.
- Marketing categories include new item drops, collection launches, sale offers, and back-in-stock updates.
- Marketing emails are sent only to customers who opted in or where another lawful basis has been legally approved.
- Customers can unsubscribe.
- Registered customers can update newsletter preferences.
- Consent source and timestamp are stored.
- Transactional emails remain separate from marketing emails.

Acceptance criteria:

- Customer can complete checkout without opting into marketing.
- Consent is auditable.
- Unsubscribe prevents future marketing for the unsubscribed category or address.

### F-026 Privacy, Cookies, Analytics, And Consent Tracking

Priority: P1

Goal: Implement privacy and tracking behavior that matches legal content and consent choices.

Requirements:

- Privacy policy explains collected data, purpose, retention, processors, access/deletion requests, and marketing preferences.
- Cookie policy distinguishes strictly necessary, analytics, and marketing cookies.
- Non-essential cookies require consent where applicable.
- Cookie preferences can be changed after initial consent where required.
- Analytics tools and advertising pixels are explicitly configured before use.
- Suggested events include product viewed, collection viewed, filter applied, add to cart, remove from cart, checkout started, payment succeeded, payment failed, newsletter signup, and contact form submitted.

Acceptance criteria:

- Strictly necessary cookies are separated from analytics and marketing cookies.
- Consent-dependent events are not sent before consent.
- Cookie and privacy pages match the implemented tools.

### F-027 Back-In-Stock And Launch Notifications

Priority: P2

Goal: Let customers register interest in unavailable products if enabled.

Requirements:

- Sold out products can show back-in-stock signup if enabled.
- Coming soon products can show launch notification signup if enabled.
- Signup collects email and consent context.
- Notification emails are sent only to eligible subscribers.
- Subscribers are associated with the relevant product or variant.

Acceptance criteria:

- Signup is hidden or unavailable when the feature is disabled.
- Notification consent is stored.
- Product or variant association is preserved.

### F-028 Gift Message Options

Priority: P2

Goal: Support gifting beyond default gift-appropriate packaging.

Requirements:

- Product pages state that jewellery arrives in gift-appropriate packaging.
- Checkout can allow customer to mark an order as a gift if enabled.
- Checkout can collect gift message if enabled.
- Gift message has a configurable character limit.
- Pricing is excluded from the physical parcel when order is marked as a gift.

Acceptance criteria:

- Gift message appears in order details for fulfilment.
- Gift state is visible before final payment.
- Gift orders follow the same returns and exchange rules as standard orders.

### F-029 Discounts, Gift Cards, Store Credit, And Promotions

Priority: P2

Goal: Support commercial promotion tools only if the business decides they are in scope.

Requirements:

- Discount codes, sale prices, bundles, gift cards, and store credit are disabled unless explicitly enabled.
- If enabled, discount rules define eligibility, expiry, usage limits, product restrictions, tax treatment, and refund behavior.
- Checkout shows discount amount and updated total in GBP.

Acceptance criteria:

- Invalid codes show clear errors.
- Promotions do not reduce order total below valid minimums.
- Refund and partial refund behavior is defined before launch.

## 7. Data Entities Required For Build

P0 entities:

- Product.
- Variant.
- Product image.
- Collection.
- Customer.
- Cart.
- Cart item.
- Stock reservation.
- Order.
- Order item.
- Payment attempt.
- Enquiry.
- Audit event.

P1 entities:

- Address.
- Wishlist item.
- Marketing preference.
- Cookie consent record.
- Email event.

Conditional entities:

- Back-in-stock subscription.
- Gift message.
- Discount or promotion rule.
- Refund record.
- Return or exchange request.

## 8. Key Business Rules

### 8.1 Availability

- In stock is purchasable.
- Low stock is purchasable with honest urgency messaging.
- Sold out is visible but not purchasable.
- Coming soon is visible but not purchasable.
- Made to order is purchasable only with lead time and capacity expectations displayed.

### 8.2 Inventory And Reservations

- Variant stock overrides product stock when variants exist.
- Rings are stocked by UK ring size.
- Stock is reserved when an item is added to cart.
- Reservation duration must be configured.
- Wishlist does not reserve stock.
- Checkout blocks purchase if requested quantity exceeds available stock.
- Overselling is not allowed for stock-tracked products.
- Made-to-order capacity is 1-20 pieces per 3-week period.
- Payment revalidates stock, reservation, price, and capacity.
- Stock and reservation adjustments are auditable.

### 8.3 UK Shipping

- Delivery country must be within the supported UK shipping boundary.
- UK-only free shipping notice appears before checkout and during checkout.
- All deliveries use tracked carrier services.
- Made-to-order and mixed-cart shipping expectations must be shown before payment.

### 8.4 Orders

- Payment success creates or confirms an order.
- Payment failure does not lose cart contents.
- Order records snapshot product, variant, price, customer, delivery, billing, shipping, and lead-time details.
- Customer-visible order statuses must be understandable.
- Refunds, cancellations, returns, and partial refunds must be auditable.

### 8.5 Marketing Consent

- Newsletter signup is optional.
- Consent source and timestamp must be stored.
- Customers can unsubscribe or update preferences.
- Transactional emails must remain separate from marketing emails.

## 9. Page Inventory

P0 public and checkout pages:

- Home.
- Shop all.
- Bracelets.
- Necklaces.
- Rings.
- Collections index or route.
- Individual collection page.
- Product detail page.
- Ring size guide.
- About the brand.
- Contact.
- Cart.
- Checkout.
- Order confirmation.
- Sign in.
- Register.
- Password reset.
- Shipping information.
- Packaging and gifting.
- Returns and exchanges.
- Privacy policy.
- Cookie policy.
- Terms and conditions.

P1 customer pages:

- Account overview.
- Account details.
- Saved addresses.
- Order history.
- Wishlist.
- Newsletter preferences.
- Account deletion request or confirmation.

Operational workflows or protected screens:

- Product management.
- Variant and stock management.
- Cart reservation review.
- Collection management.
- Image management.
- Order management.
- Refund and cancellation handling.
- Fulfilment and tracking management.
- Enquiry management.
- Marketing subscriber export where permitted.
- Audit history review.

## 10. Non-Functional Requirements

### 10.1 UX And Design

- The interface should feel refined, mysterious, elegant, trustworthy, premium, and wearable.
- Avoid overly gothic styling, mass-market discount patterns, costume-like presentation, decorative clutter, and misleading scarcity.
- Product information must be easy to scan.
- Purchase actions must be clear.
- Unavailable states must be explained.
- Mobile browsing, cart, and checkout must be comfortable.
- Customers must not discover UK-only shipping for the first time at payment.

### 10.2 Performance

- Product images are optimized.
- Below-the-fold images are lazy loaded.
- Responsive image sizes are used.
- Product listing filters and sorting feel fast.
- Checkout loads reliably on mobile connections.
- Non-essential third-party scripts wait for consent where required.

### 10.3 Compliance

- Legal, privacy, cookie, returns, cancellation, and terms content require final business or legal review before launch.
- Precious metal descriptions must be accurate.
- Hallmarking requirements and Online Dealer's Notice implementation must be confirmed before selling applicable silver or white gold products.
- Data processing, cookies, marketing consent, and retention must be reviewed against current UK expectations before launch.

## 11. Open Decisions Before Build

These decisions affect implementation and should be resolved before the related feature is built:

- Exact carrier options.
- Dispatch working days and cut-off times.
- Standard dispatch time for in-stock products.
- Lost, delayed, and damaged parcel handling.
- Whether signature on delivery is required for high-value orders.
- Exact cart reservation duration.
- Low stock thresholds.
- Whether back-in-stock and coming-soon signups are enabled at launch.
- Whether Apple Pay, Google Pay, or other wallet options are enabled through selected providers.
- How abandoned checkout and session expiry behave.
- Which order status changes trigger emails.
- Whether personalised, engraved, altered, or made-to-order items have extra return restrictions.
- Whether ring size exchanges have a separate time limit or fee.
- Required image aspect ratios and minimum resolutions.
- Photography style and minimum image set per product.
- Final product copy ownership and approval process.
- Homepage merchandising order.
- Analytics tools and advertising pixels.
- Cookie consent implementation.
- Data retention periods.
- Legal business name, address, and customer service email.
- Final hallmarking and Online Dealer's Notice approach.

## 12. Functional Launch Acceptance

The website is functionally launch-ready when:

- Public browsing works for home, shop, category, collection, and product pages.
- Product detail pages show complete purchase-critical information.
- Ring products require UK ring size selection.
- Cart supports add, remove, quantity update, variant display, subtotal, availability validation, and stock reservations.
- Guest carts do not silently merge into logged-in carts.
- Customers must sign in or create an account before payment.
- Checkout accepts only supported UK delivery addresses.
- Checkout shows free UK shipping, VAT-inclusive or applicable tax wording, and total in GBP.
- Payment succeeds through approved external provider flows.
- Successful payment creates an order and sends confirmation.
- Payment failure does not lose cart contents.
- Made-to-order and mixed-cart fulfilment expectations are shown before payment.
- Required policy pages are live and linked from the footer.
- Contact enquiries reach the business.
- Developer/operator workflows can manage products, inventory, reservations, orders, dispatch, refunds, enquiries, and content.
- Baseline accessibility, security, SEO, privacy, and performance requirements are met.
