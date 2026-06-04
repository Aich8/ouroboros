# Feature Spec: Ouroboros Jewellery Online Store

Status: Draft v1
Source: business-context-spec.md, functional-spec.md
Last updated: 2026-06-04

## 1. Purpose

This feature spec converts the current business and functional requirements into a build-oriented feature backlog for the Ouroboros Jewellery website.

The goal is a functional UK ecommerce website where customers can browse premium Ouroboros-inspired jewellery, understand each product, choose required variants, add available products to cart, complete a secure GBP checkout for UK delivery, and receive order confirmation.

## 2. Priority Definitions

- P0: Required for a public, sellable launch.
- P1: Required to satisfy the broader current functional spec, but can follow the first sellable launch if needed.
- P2: Optional or later enhancement.

## 3. Resolved Assumptions

The existing specs are mostly consistent, but a few points need explicit build decisions:

- Account creation is required to purchase; guest checkout is not allowed.
- Login is required to complete checkout, purchase, use wishlist, use saved addresses, manage newsletter preferences inside an account, and view order history.
- Products should belong to one primary collection. If the implementation uses `collection_ids`, it must enforce only one active public collection per product unless the business later changes this rule.
- All customer-facing product prices are displayed in GBP.
- UK delivery must be enforced before payment.
- VAT and tax display must be configurable because VAT registration status is not final.
- Payment card details are handled only by an external payment provider. The website must not store raw card details.
- Gift messages, back-in-stock alerts, discount codes, and advanced analytics are not launch blockers unless explicitly enabled by the business.

## 4. Launch Feature Set

The P0 launch is considered functional when these customer journeys work end to end:

1. A customer can browse home, shop, category, collection, and product pages.
2. A customer can inspect product images, price, material, availability, size, weight, care, packaging, shipping, and returns information.
3. A customer can select required variants, especially UK ring size.
4. A customer can add available products to cart.
5. A customer can update cart quantity, remove items, and see subtotal and availability messages.
6. A customer can sign in or create an account, check out with a UK delivery address, and pay securely in GBP.
7. A successful payment creates an order and sends a confirmation email.
8. A failed payment gives a retry path without losing the cart.
9. Sold out and coming soon products cannot be purchased.
10. Made-to-order products show lead time before purchase.
11. Required policy, contact, shipping, returns, privacy, terms, and cookie pages are accessible.
12. Admin or operational users can manage products, images, stock, orders, dispatch status, and customer enquiries.

## 5. Feature Map

| ID | Feature | Priority | Primary Users |
| --- | --- | --- | --- |
| F-001 | Site Navigation And Layout | P0 | Guest, Customer |
| F-002 | Homepage | P0 | Guest, Customer |
| F-003 | Product Catalogue Data | P0 | Admin, Customer |
| F-004 | Product Listing Pages | P0 | Guest, Customer |
| F-005 | Category Pages | P0 | Guest, Customer |
| F-006 | Collection Pages | P0 | Guest, Customer |
| F-007 | Product Detail Pages | P0 | Guest, Customer |
| F-008 | Ring Size Selection And Guide | P0 | Guest, Customer |
| F-009 | Cart | P0 | Guest, Customer |
| F-010 | UK Checkout | P0 | Customer |
| F-011 | Payment And Order Creation | P0 | Customer, Admin |
| F-012 | Transactional Emails | P0 | Guest, Customer, Admin |
| F-013 | Contact And Enquiries | P0 | Guest, Customer, Admin |
| F-014 | Required Content And Policy Pages | P0 | Guest, Customer |
| F-015 | Admin Product And Inventory Operations | P0 | Admin |
| F-016 | Admin Order And Support Operations | P0 | Admin |
| F-017 | Customer Authentication | P0 | Guest, Customer |
| F-018 | Customer Account Area | P1 | Customer |
| F-019 | Wishlist | P1 | Customer |
| F-020 | Newsletter And Marketing Preferences | P1 | Guest, Customer, Admin |
| F-021 | Back-In-Stock And Launch Notifications | P2 | Guest, Customer |
| F-022 | Gift Options | P2 | Guest, Customer |
| F-023 | Discounts And Promotions | P2 | Guest, Customer, Admin |
| F-024 | Analytics And Consent Tracking | P1 | Admin |
| F-025 | SEO | P0 | Customer, Admin |
| F-026 | Accessibility | P0 | Guest, Customer |
| F-027 | Security And Abuse Protection | P0 | All |
| F-028 | Error And Empty States | P0 | Guest, Customer |

## 6. Feature Specifications

### F-001 Site Navigation And Layout

Priority: P0

Goal: Provide clear routes into shopping, account, cart, wishlist, brand, and policy content.

Requirements:

- Primary navigation includes Home, Shop, Collections, Bracelets, Necklaces, Rings, Ring Size Guide, About, and Contact.
- Utility navigation includes Account, Wishlist, and Cart.
- Footer navigation includes Shipping Information, Returns And Exchanges, Packaging And Gifting, Privacy Policy, Cookie Policy, Terms And Conditions, Contact, and Newsletter Signup.
- Header and footer are available across public pages.
- Cart item count is visible when cart contains items.
- Mobile navigation supports all primary and utility routes.

Acceptance criteria:

- A customer can reach product listings within one click from the homepage.
- Policy pages are reachable from the footer.
- Mobile users can navigate to shop, cart, account, contact, and policy pages without layout overlap.

### F-002 Homepage

Priority: P0

Goal: Introduce the brand and route customers into product discovery.

Requirements:

- Show the Ouroboros Jewellery brand name clearly.
- Use jewellery-led visual direction.
- Include concise brand positioning copy around eternity, renewal, transformation, and premium craft.
- Feature selected collections.
- Feature selected products.
- Link to Bracelets, Necklaces, and Rings.
- Surface UK shipping and gift packaging trust signals.
- Include newsletter signup or route to newsletter signup.

Acceptance criteria:

- The page clearly communicates that the site sells jewellery.
- A customer can navigate from the homepage to a product listing.
- GBP pricing or UK-only delivery context is discoverable before checkout.

### F-003 Product Catalogue Data

Priority: P0

Goal: Store the structured product data needed for browsing, purchase, inventory, and order snapshots.

Requirements:

- Product records include SKU, name, slug, category, collection, material, finish, description, symbolic meaning, dimensions, weight, care guidance, packaging note, returns note, price in GBP, tax class, availability status, low-stock threshold, made-to-order lead time, publish status, SEO title, and SEO description.
- Variant records support ring size, chain length, bracelet size, or other product options.
- Variant stock overrides product stock when variants exist.
- Ring stock is tracked by UK ring size.
- Product image records support main, detail, scale, angle, and packaging images.
- Product image records include alt text, sort order, and primary image flag.
- Collection records include name, slug, description, symbolic theme, hero image, SEO title, SEO description, sort order, and publish status.

Acceptance criteria:

- Product listing and detail pages can render without hardcoded product information.
- Unpublished products do not appear publicly.
- Every purchasable product has price, availability, category, collection, material, and at least one image.

### F-004 Product Listing Pages

Priority: P0

Goal: Let customers browse and evaluate available, sold out, and coming soon products.

Requirements:

- Shop All displays a product grid.
- Each product card shows image, name, category, collection, price in GBP, material, and availability status.
- Product listing supports filters for category, collection, material, availability, price range, and ring size where relevant.
- Product listing supports sorting by availability at minimum.
- Filters can be cleared.
- Empty results show useful copy and a route back to Shop All.
- Sold out and coming soon products are visible but cannot be added directly to cart.

Acceptance criteria:

- Customers can filter products and clear filters.
- Customers can distinguish purchasable, sold out, coming soon, low-stock, and made-to-order products.
- Empty results do not trap the customer.

### F-005 Category Pages

Priority: P0

Goal: Provide category-specific browsing for bracelets, necklaces, and rings.

Requirements:

- Category pages exist for Bracelets, Necklaces, and Rings.
- Each category page behaves like a filtered product listing page.
- Ring category page includes a link to the Ring Size Guide.
- Ring category page includes a ring size filter.
- Ring category page states that UK sizing is the default.

Acceptance criteria:

- Category routes only show products from the selected category.
- Ring customers can reach size guidance from the category page.
- Product cards retain price, material, collection, and availability information.

### F-006 Collection Pages

Priority: P0

Goal: Group products by symbolic theme, form, or finish.

Requirements:

- Collection pages include collection title, symbolic story, product grid, and optional hero image.
- Product cards match Shop All card data.
- A product belongs to one public collection.
- Empty collection pages remain functional.

Acceptance criteria:

- Customers can browse products by collection.
- A collection with no available products displays a useful empty state.
- Collection content explains the symbolic theme without blocking product browsing.

### F-007 Product Detail Pages

Priority: P0

Goal: Give customers enough information to decide whether to buy.

Requirements:

- Show product name, category, collection, price in GBP, material, purity or fineness, availability, description, symbolic inspiration, size, dimensions, weight, care guidance, packaging information, UK shipping information, returns information, and related products or collection link.
- Show made-to-order lead time where applicable.
- Show hallmarking or material-compliance information where relevant.
- Include product image gallery with main image and supporting detail views.
- Include variant selector where applicable.
- Include quantity selector where applicable.
- Include Add to Cart button.
- Include Wishlist button or wishlist sign-in prompt if wishlist is enabled.

Add to cart rules:

- In stock products can be added to cart.
- Low stock products can be added to cart with honest urgency messaging.
- Sold out products cannot be added to cart.
- Coming soon products cannot be added to cart.
- Made-to-order products can be added to cart only when lead time is shown.
- Rings require selected UK ring size before add to cart.

Acceptance criteria:

- Add to Cart is disabled until required options are selected.
- Unavailable products explain why purchase is blocked.
- Ring products link to size help.
- Product details include enough material, sizing, care, packaging, shipping, and returns information to support an online purchase.

### F-008 Ring Size Selection And Guide

Priority: P0

Goal: Help customers select the correct UK ring size before buying.

Requirements:

- Ring products require size selection before cart add.
- Available ring sizes are displayed in UK format.
- Ring size availability is shown where stock data exists.
- Ring size guide uses UK sizes as the primary format.
- Guide includes measuring instructions, advice for unsure customers, support contact link, and advisory disclaimer.
- Ring product pages link to the guide.

Acceptance criteria:

- A ring cannot be added to cart without a selected UK size.
- UK sizing is visually dominant on the guide.
- Customers can return from size guidance to shopping without becoming stranded.

### F-009 Cart

Priority: P0

Goal: Let customers review, update, and validate selected items before checkout.

Requirements:

- Cart displays product image, product name, selected variant details, price, quantity, line total, availability messages, subtotal, shipping note or estimate, tax display if applicable, remove action, and checkout button.
- Customers can update quantity where quantity is allowed.
- Customers can remove items.
- Quantity cannot exceed available stock unless the product is made to order.
- Sold out and coming soon items block checkout.
- If an item becomes unavailable, checkout is disabled until the item is removed or adjusted.
- Made-to-order lead time appears in cart.
- Guest cart persists for the current browser session.
- Logged-in cart persists across sessions when account features are enabled.
- Guest cart merges into account cart after login when account features are enabled.

Acceptance criteria:

- Customers can update or remove one item without losing the rest of the cart.
- Checkout total is understandable before payment.
- Non-UK shipping restriction is visible before checkout.
- Cart state survives payment failure.

### F-010 UK Checkout

Priority: P0

Goal: Collect contact, delivery, shipping, and payment details for a UK-only order.

Requirements:

- Checkout steps include cart review, contact details, delivery address, shipping method or shipping confirmation, payment, and confirmation.
- Collect email, first name, last name, UK delivery address, billing address if different, phone number if required, gift message if enabled, and marketing opt-in choice.
- Delivery country must be United Kingdom.
- Required address fields must be completed.
- Email must use a valid format.
- Customer must be signed in before payment.
- Required variants must remain selected.
- Stock must be rechecked before payment.
- Checkout totals show product price, quantity, shipping, tax where applicable, and total in GBP.

Acceptance criteria:

- A non-UK delivery address cannot complete checkout.
- Missing required fields show field-level validation.
- Checkout revalidates stock before payment.
- Customers must sign in or create an account before payment; guest checkout cannot complete purchase.

### F-011 Payment And Order Creation

Priority: P0

Goal: Process payment securely and create accurate order records.

Requirements:

- Payment is processed through an external trusted payment provider.
- Website does not store raw payment card data.
- Payment errors show a clear retry path.
- Orders are created after successful payment, unless the selected provider requires pending-payment order creation.
- Successful orders include order number, customer email, order summary, shipping address, shipping method or note, total paid in GBP, dispatch expectation, and support route.
- Order item records snapshot product name, variant label, SKU, quantity, unit price, line total, and made-to-order lead time.
- Stock is reduced only after successful payment unless provider-supported temporary reservation is configured.

Acceptance criteria:

- Successful payment creates an order.
- Successful payment triggers order confirmation email.
- Payment failure does not lose the cart.
- Order totals match checkout totals.

### F-012 Transactional Emails

Priority: P0

Goal: Send operational emails required for account, checkout, payment, support, and fulfilment flows.

P0 required emails:

- Order confirmation
- Payment failed
- Order dispatched
- Password reset
- Contact form acknowledgement if email service is configured
- Refund issued if refunds are managed through the site or platform

P1 or optional emails:

- Account verification
- Order cancelled
- Return or exchange update
- Back-in-stock notification
- Newsletter subscription confirmation

Rules:

- Transactional emails must not include marketing content unless the customer has separately opted in.
- Order confirmation includes order number, order summary, total paid in GBP, delivery details, expected dispatch or lead time, and support route.
- Dispatch email includes tracking number and carrier when available.

Acceptance criteria:

- Successful payment sends order confirmation.
- Payment failure sends or displays a clear failure message.
- Dispatch notification can be triggered when tracking is added or order is marked dispatched.

### F-013 Contact And Enquiries

Priority: P0

Goal: Give customers a reliable support route.

Requirements:

- Contact page displays customer service email address.
- Contact form collects name, email, enquiry type, message, and optional order number.
- Enquiry types include Product question, Ring sizing help, Order status, Shipping question, Returns or exchange, Made-to-order enquiry, and General enquiry.
- Contact form includes privacy note.
- Successful submission shows confirmation.
- Admin or support recipient receives enquiry details.

Acceptance criteria:

- Customer can submit a valid enquiry.
- Invalid email or missing required fields are rejected with clear errors.
- Enquiry type is stored or included in support notification.

### F-014 Required Content And Policy Pages

Priority: P0

Goal: Provide trust, operational, legal, and pre-purchase information.

Required pages:

- About The Brand
- Shipping Information
- Packaging And Gifting
- Returns And Exchanges
- Privacy Policy
- Cookie Policy
- Terms And Conditions
- Contact

Requirements:

- Footer links to required policy pages.
- Product pages link or expose shipping, packaging, care, and returns information.
- Checkout links to returns, cancellation, terms, privacy, and shipping information.
- Legal and policy copy must be reviewed before launch.
- Precious metal material descriptions must be accurate.
- Hallmarking and Dealer's Notice requirements must be confirmed and implemented where required.

Acceptance criteria:

- Customers can find shipping, returns, privacy, terms, and contact information before checkout.
- Product material claims are not vague or misleading.
- Required legal pages are not hidden behind account or checkout walls.

### F-015 Admin Product And Inventory Operations

Priority: P0

Goal: Give the business an operational way to manage products, images, variants, and stock.

Requirements:

- Admin can create, edit, archive, publish, and unpublish products.
- Admin can assign category and collection.
- Admin can set material, dimensions, weight, care, packaging, returns note, symbolic meaning, and SEO fields.
- Admin can upload and reorder product images.
- Admin can create and manage variants.
- Admin can set availability status.
- Admin can set made-to-order lead time.
- Admin can view stock by product and variant.
- Admin can adjust stock.
- Admin can set low-stock thresholds.
- Sensitive stock changes are recorded in audit history.

Acceptance criteria:

- Admin can publish a complete product without developer intervention, or there is a documented operational method if using a managed platform.
- Variant stock can be managed for ring sizes.
- Public product availability updates after admin stock or status changes.

### F-016 Admin Order And Support Operations

Priority: P0

Goal: Let the business fulfil orders and handle customer support.

Requirements:

- Admin can view orders.
- Admin can search orders by order number, email, status, and date.
- Admin can update fulfilment status.
- Admin can add carrier and tracking number.
- Admin can mark an order dispatched.
- Admin can trigger dispatch email.
- Admin can handle cancellation and refund actions through approved provider or platform workflow.
- Admin or support user can view enquiries, filter by enquiry type, and mark them open, pending, or resolved.

Acceptance criteria:

- Paid orders are visible to admin.
- Dispatch tracking can be added and communicated.
- Support enquiries are not lost after submission.

### F-017 Customer Authentication

Priority: P0

Goal: Provide secure customer accounts for purchasing, saved data, and authenticated features.

Requirements:

- Customers can register with unique email and password.
- Customers can log in and log out.
- Customers can request password reset.
- Passwords are securely hashed.
- Password reset links expire.
- Authenticated sessions are protected with secure cookies.
- Sensitive account changes require confirmation.

Acceptance criteria:

- Duplicate customer emails are rejected.
- Customers can recover access through password reset.
- Logout is available from authenticated account areas.

### F-018 Customer Account Area

Priority: P1

Goal: Let registered customers manage their details and purchase history.

Pages:

- Account overview
- Account details
- Saved addresses
- Order history
- Wishlist
- Newsletter preferences

Requirements:

- Customers can view and update account details.
- Customers can add, edit, remove, and set default delivery addresses.
- Customers can view order history.
- Customers can view order number, date, status, items, delivery address, total paid, and tracking details when available.
- Customers can request account deletion or data access through a defined support route.

Acceptance criteria:

- Registered customers can view past orders.
- Saved addresses can be reused at checkout.
- Account pages are inaccessible to guests.

### F-019 Wishlist

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

Acceptance criteria:

- Wishlist persists across devices for the same account.
- Duplicate saves do not create duplicate rows.
- Moving a wishlist item to cart follows the same variant and stock rules as product detail pages.

### F-020 Newsletter And Marketing Preferences

Priority: P1

Goal: Collect and manage lawful marketing consent.

Requirements:

- Newsletter signup is optional.
- Marketing opt-in is explicit unless another lawful basis is legally approved.
- Marketing categories include new item drops, collection launches, sale offers, and back-in-stock updates.
- Customers can unsubscribe.
- Registered customers can update newsletter preferences.
- Consent source and timestamp are stored.
- Transactional emails remain separate from marketing emails.

Acceptance criteria:

- A customer can complete checkout without opting into marketing.
- Consent is auditable.
- Unsubscribe prevents future marketing emails for the unsubscribed category or address.

### F-021 Back-In-Stock And Launch Notifications

Priority: P2

Goal: Let customers register interest in unavailable products.

Requirements:

- Sold out products can show back-in-stock signup if enabled.
- Coming soon products can show launch notification signup if enabled.
- Signup collects email and consent context.
- Notification emails are sent only to eligible subscribers.

Acceptance criteria:

- Signup is unavailable or hidden when the feature is disabled.
- Back-in-stock subscribers are associated with the relevant product or variant.

### F-022 Gift Options

Priority: P2

Goal: Support gifting beyond default gift-appropriate packaging.

Requirements:

- Product pages state that jewellery arrives in gift-appropriate packaging.
- Checkout can allow customer to mark order as gift if enabled.
- Checkout can collect gift message if enabled.
- Gift message has a configurable character limit.
- Pricing is excluded from physical parcel when order is marked as gift.

Acceptance criteria:

- Gift message appears in order details for fulfilment.
- Gift state is visible before final payment.

### F-023 Discounts And Promotions

Priority: P2

Goal: Support promotional pricing only if the business decides it is in scope.

Requirements:

- Discount code support is disabled unless configured.
- If enabled, discount rules must define eligibility, expiry, usage limits, product restrictions, and tax treatment.
- Checkout must show discount amount and updated total in GBP.

Acceptance criteria:

- Invalid codes show clear errors.
- Discounts do not reduce order total below valid minimums.
- Refund behavior for discounted orders is defined before launch.

### F-024 Analytics And Consent Tracking

Priority: P1

Goal: Measure ecommerce behavior while respecting cookie and consent rules.

Requirements:

- Analytics implementation respects cookie consent.
- Non-essential analytics and marketing cookies require consent where required.
- Cookie preferences can be changed after initial consent.
- Suggested events include product viewed, collection viewed, search performed, filter applied, add to cart, remove from cart, checkout started, payment succeeded, payment failed, newsletter signup, and contact form submitted.

Acceptance criteria:

- Strictly necessary cookies are separated from analytics and marketing cookies.
- Events that depend on consent are not sent before consent.
- Cookie policy reflects implemented tracking tools.

### F-025 SEO

Priority: P0

Goal: Make product and collection pages discoverable and technically sound.

Requirements:

- Public pages use SEO-friendly URLs.
- Product and collection pages have unique page titles and meta descriptions.
- Product structured data is implemented where appropriate.
- Sitemap is generated.
- Robots rules are configured.
- Canonical URLs are used for filtered listing pages where needed.
- Product images use descriptive alt text.

Acceptance criteria:

- Product URLs follow `/products/product-slug`.
- Collection URLs follow `/collections/collection-slug`.
- Hidden, unpublished, or admin pages are not indexed.

### F-026 Accessibility

Priority: P0

Goal: Make the store usable with keyboard, screen readers, and accessible form interactions.

Requirements:

- Menus, forms, product options, cart, and checkout are keyboard navigable.
- Focus states are visible.
- Text contrast is sufficient.
- Product images have alt text.
- Form labels are connected to inputs.
- Error messages are connected to fields.
- Ring size and variant controls are screen-reader usable.
- Buttons and links have clear names.
- No critical information is conveyed by color alone.

Acceptance criteria:

- A keyboard user can add a product to cart and reach checkout.
- Form validation errors identify the affected fields.
- Availability status is available as text, not only color.

### F-027 Security And Abuse Protection

Priority: P0

Goal: Protect customer data, payment flow, admin functions, and public forms.

Requirements:

- Production uses HTTPS everywhere.
- Passwords are securely hashed.
- Session cookies are secure.
- Password reset tokens expire.
- Login, register, password reset, checkout, and contact forms are rate-limited.
- CSRF protection is implemented where relevant.
- Inputs are validated and output is escaped.
- Admin routes require admin-only access.
- Sensitive admin product, stock, and order changes are audit logged.
- Raw payment card details are never stored.

Acceptance criteria:

- Guest users cannot access admin or customer-only pages.
- Public forms reject invalid input and limit abuse.
- Payment processing uses the provider's secure flow.

### F-028 Error And Empty States

Priority: P0

Goal: Keep customers oriented when something is unavailable, invalid, empty, or broken.

Required states:

- Product not found
- Collection not found
- No products in category
- No search results
- Cart empty
- Wishlist empty if wishlist is enabled
- Account order history empty
- Product sold out
- Product coming soon
- Variant unavailable
- Checkout address invalid
- Checkout non-UK address rejected
- Payment failed
- Contact form failed
- Newsletter signup failed if newsletter is enabled
- Server error
- Maintenance mode if needed

Acceptance criteria:

- Each state explains what happened.
- Each state offers the next useful action.
- Failed payment and failed form submissions do not erase recoverable customer input.

## 7. Data Entities Required For Build

Minimum P0 entities:

- Customer
- Product
- Variant
- Product Image
- Collection
- Cart
- Cart Item
- Order
- Order Item
- Enquiry

P1 entities:

- Address
- Wishlist Item
- Marketing Preference

Operational or provider-backed entities:

- Payment Attempt
- Stock Adjustment
- Admin Audit Event
- Email Event
- Cookie Consent Record

## 8. Key Business Rules

### 8.1 Availability

- In stock: purchasable.
- Low stock: purchasable with honest low-stock messaging.
- Sold out: visible but not purchasable.
- Coming soon: visible but not purchasable.
- Made to order: purchasable only with lead time displayed.

### 8.2 Inventory

- Variant stock overrides product stock when variants exist.
- Rings are stocked by UK ring size.
- Checkout blocks purchase if requested quantity exceeds available stock.
- Overselling is not allowed for stock-tracked products.
- Stock is reduced after successful payment unless temporary reservation is deliberately implemented.
- Admin stock adjustments should be auditable.

### 8.3 UK Shipping

- Delivery country must be United Kingdom.
- UK-only shipping notice appears before checkout and during checkout.
- The business must confirm whether Channel Islands, Isle of Man, BFPO, Highlands and Islands, and remote-area surcharges are supported.
- Made-to-order and mixed-cart shipping expectations must be shown before payment.

### 8.4 Orders

Supported order statuses:

- Pending payment
- Payment failed
- Paid
- Processing
- Made to order
- Ready to dispatch
- Dispatched
- Delivered
- Cancelled
- Refunded
- Partially refunded
- Returned

Customer-visible order data:

- Order number
- Order date
- Order status
- Items purchased
- Delivery address
- Total paid
- Tracking details when available

### 8.5 Marketing Consent

- Newsletter signup is optional.
- Marketing consent must be explicit unless legally approved otherwise.
- Consent source and timestamp must be stored.
- Customers can unsubscribe or update preferences.
- Transactional emails must remain separate from marketing emails.

## 9. Page Inventory

P0 public pages:

- Home
- Shop All
- Bracelets
- Necklaces
- Rings
- Collections index or route
- Individual collection page
- Product detail page
- Ring Size Guide
- About The Brand
- Contact
- Cart
- Checkout
- Order Confirmation
- Sign In
- Register
- Password Reset
- Shipping Information
- Packaging And Gifting
- Returns And Exchanges
- Privacy Policy
- Cookie Policy
- Terms And Conditions

P1 account pages:

- Account Overview
- Account Details
- Saved Addresses
- Order History
- Wishlist
- Newsletter Preferences

Operational pages or platform screens:

- Product management
- Variant and stock management
- Collection management
- Image management
- Order management
- Enquiry management
- Customer or subscriber export where permitted

## 10. Non-Functional Requirements

### 10.1 UX And Design

- The interface should feel refined, mysterious, elegant, trustworthy, premium, and wearable.
- Avoid overly gothic styling, mass-market discount patterns, decorative clutter, and misleading scarcity.
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
- Hallmarking requirements and Dealer's Notice implementation must be confirmed before selling applicable silver or white gold products.
- Data processing, cookies, marketing consent, and retention must be reviewed against UK expectations before launch.

## 11. Open Decisions Before Build

These decisions affect implementation and should be resolved before development starts or before the relevant feature is built:

- Ecommerce platform, custom build, or hybrid approach.
- Payment provider and accepted payment methods.
- VAT registration and tax display.
- Shipping carrier, shipping cost, free shipping threshold, dispatch timelines, and supported UK territories.
- Which account-area features beyond required sign-in and registration are P0 or P1 for the first launch.
- Whether gift message support is enabled at launch.
- Whether back-in-stock notifications are enabled at launch.
- Whether discount codes or sale pricing are in scope.
- Cookie consent provider or custom implementation.
- Analytics and advertising tools.
- Legal business name, address, customer service email, and final policy copy.
- Final hallmarking and online Dealer's Notice approach.

## 12. Functional Launch Acceptance

The website is functionally launch-ready when:

- Public browsing works for home, shop, category, collection, and product pages.
- Product detail pages show complete purchase-critical information.
- Ring products require UK ring size selection.
- Cart supports add, remove, quantity update, variant display, subtotal, and availability validation.
- Customers must sign in or create an account before payment; guest checkout is blocked.
- Checkout accepts only UK delivery addresses.
- Payment succeeds through an external provider.
- Successful payment creates an order and sends confirmation.
- Payment failure does not lose cart contents.
- Required policy pages are live and linked from the footer.
- Contact enquiries reach the business.
- Admin or operational users can manage products, inventory, orders, dispatch, refunds, and enquiries.
- Baseline accessibility, security, SEO, privacy, and performance requirements are met.
