# Build Decisions Spec: Ouroboros Jewellery Online Store

Status: Draft v1
Source: business-context-spec.md, functional-spec.md, features-spec.md, email_templates_prompt.txt
Last updated: 2026-06-12

## 1. Purpose

This spec captures the build decisions required to turn the existing business, functional, and feature specs into an implementable ecommerce website.

It does not replace the existing specs. It resolves or tracks decisions that affect architecture, implementation order, operations, payment, shipping, legal content, product data, testing, and launch readiness.

## 2. Decision Status Legend

- Confirmed: Already decided by the source specs and should be treated as fixed unless the business changes direction.
- Proposed: Recommended default for build planning. Must be accepted or replaced before implementation begins.
- Open: Required decision that is not yet defined.
- Deferred: Not required for the first sellable launch unless the business expands scope.

## 3. Confirmed Source Decisions

The following decisions are already confirmed by the source specs:

- The site is a custom ecommerce platform.
- The store sells Ouroboros-inspired silver and white gold jewellery.
- Product categories are bracelets, necklaces, and rings.
- The business currently sells UK-only.
- Prices are GBP-only.
- Displayed prices include VAT or other applicable taxes.
- UK shipping is free.
- Account creation or sign-in is required before payment and order placement.
- Guest browsing and guest cart building are allowed.
- Guest carts do not silently merge into saved logged-in customer carts.
- Internal product keyword search is out of scope for the current version.
- Infinite scroll is out of scope.
- Raw card details must never be stored by the store.
- Payments are single upfront payments only.
- Instalments and split payments are out of scope.
- A separate admin management interface is not required for the current version.
- Product, inventory, order, refund, fulfilment, enquiry, content, and email preference management are developer/operator managed.
- Stock is reserved when an item is added to cart.
- Wishlist does not reserve stock.
- Overselling is not allowed for stock-tracked items.
- Made-to-order capacity is limited to 1-20 pieces per 3-week period unless product data overrides this later.
- Legal, privacy, cookie, returns, cancellation, VAT, and hallmarking requirements must be reviewed before launch.

## 4. Launch Scope Decision

Status: Proposed

The first sellable launch should prioritize the P0 launch feature set from `features-spec.md`.

P0 launch must include:

- Public storefront pages.
- Product catalogue.
- Category and collection browsing.
- Product detail pages.
- Variant selection, especially UK ring size.
- Cart.
- Stock reservation.
- Account registration, sign-in, sign-out, and password reset.
- UK-only checkout.
- Payment provider integration.
- Order creation.
- Transactional emails.
- Contact form.
- Required legal and policy pages.
- Developer/operator workflows for catalogue, stock, orders, fulfilment, refunds, enquiries, and content.

P1 features may follow after the first sellable launch unless the business requires them for launch:

- Full account dashboard.
- Saved address book.
- Customer order history page.
- Wishlist.
- Newsletter preference centre.
- Cookie preference centre beyond the minimum legally required implementation.

Build implication:

- Authentication is P0 because checkout requires it.
- Full account self-service is P1 unless explicitly promoted to launch scope.
- Address capture and order address snapshots are P0.
- Saved address book management is P1.

Open decision:

- Confirm whether wishlist and full customer account area must be included in the first public launch or can follow immediately after launch.

## 5. Technical Architecture

### 5.1 Application Stack

Status: Proposed

Recommended default:

- TypeScript application.
- Server-rendered storefront for SEO and fast product pages.
- PostgreSQL database.
- ORM or typed query layer with migrations.
- Component-based frontend with a small design system.
- External payment provider checkout or secure provider payment elements.
- External email provider for transactional email.
- Object storage or image service for product imagery.

Open decisions:

- Final frontend framework.
- Final backend framework.
- Final hosting platform.
- Final database host.
- Final image storage or image CDN provider.
- Final email provider.

Build requirement:

- The selected stack must support local, staging, and production environments.
- Secrets must be environment-specific and never committed to source control.
- Migrations must be repeatable and reviewable.
- Product, order, payment, and inventory data must be stored in structured systems of record, not hardcoded in UI files.

### 5.2 Rendering And Routing

Status: Proposed

Recommended default:

- Public product, category, collection, and policy pages should be server-rendered or statically generated where practical.
- Cart, account, checkout, and payment flows should be dynamic and session-aware.
- Product, category, and collection routes should use stable slugs.
- Filtered listing pages should avoid creating uncontrolled duplicate SEO index pages.

Build requirement:

- Product and collection pages must have unique titles, meta descriptions, canonical URL behavior, and structured data where appropriate.

### 5.3 Database And Identifiers

Status: Proposed

Recommended default:

- Use PostgreSQL.
- Use stable internal IDs for database records.
- Use human-readable order numbers for customer communication.
- Store money as integer minor units or fixed precision decimals.
- Store all order snapshots independently from mutable product data.
- Use database transactions for stock reservation, payment confirmation, and order creation logic where consistency matters.

Open decisions:

- Exact ID format.
- Exact order number format.
- Whether prices are stored as pence integers or decimal values.

### 5.4 File And Image Storage

Status: Proposed

Recommended default:

- Product images should be uploaded to a managed object store or image platform.
- The database should store image metadata and URLs.
- Product image records must support alt text, sort order, image type, and primary image flag.

Open decisions:

- Image storage provider.
- Required image aspect ratios.
- Minimum source resolution.
- Maximum upload size.
- Image naming convention.

## 6. Developer And Operator Workflows

Status: Proposed

Because a separate admin management interface is out of scope, the launch build must still define protected operational workflows.

Recommended launch workflow:

- Product and collection data are managed through protected developer/operator scripts, seed files, or protected internal routes.
- Inventory and variant stock can be updated through protected developer/operator scripts or internal screens.
- Order fulfilment status, carrier, tracking number, cancellations, and refunds are updated through protected developer/operator workflows.
- Enquiries can be viewed through the database, protected workflow, or routed support inbox.
- Sensitive changes create audit events.

Build requirement:

- Operational workflows must not require editing customer-facing code paths.
- Operational access must be restricted.
- Manual stock changes, refund actions, order status changes, and customer-data changes must be auditable.

Open decisions:

- Whether launch operations use scripts, protected internal screens, a lightweight CMS, or a combination.
- Who has operator access.
- Whether product imports use CSV, JSON, database UI, or custom forms.
- How support staff view and respond to enquiries.
- How marketing subscriber exports are generated where legally permitted.

## 7. Product Catalogue Decisions

### 7.1 Launch Catalogue

Status: Open

Required before product page implementation is complete:

- Final product list.
- Final collection list.
- SKU naming convention.
- Product names.
- Slugs.
- Categories.
- Materials.
- Purity or fineness.
- Finishes.
- Dimensions.
- Weights.
- Product descriptions.
- Symbolic meanings.
- Care guidance.
- Packaging notes.
- Returns notes.
- Prices in GBP.
- Tax display wording.
- Availability statuses.
- Stock quantities by variant.
- Made-to-order lead times.
- SEO titles and descriptions.
- Product images.
- Product image alt text.

Build requirement:

- No purchasable product should launch without price, material, availability, at least one product image, and stock or made-to-order capacity rules.

### 7.2 Product Variant Rules

Status: Confirmed with open details

Confirmed:

- Rings require UK ring size selection before add to cart.
- Ring stock is tracked by UK ring size.
- Necklaces and bracelets may have size, length, clasp, finish, or other variants if purchase-relevant.

Open decisions:

- Exact UK ring sizes sold at launch.
- Whether rings support half sizes.
- Necklace chain lengths at launch.
- Bracelet sizing scheme.
- Whether any products include engraving, stones, clasp choices, or finish choices.

### 7.3 Product Images

Status: Proposed

Recommended minimum launch image set for each product:

- Main product image.
- Detail image.
- Angle image.
- Scale or worn image where available.
- Packaging image where packaging is a selling point.

Recommended technical default:

- Use consistent aspect ratios for product cards.
- Use high-resolution source images.
- Generate responsive sizes for listing, product detail, cart, and checkout views.
- Use descriptive alt text focused on the actual product.

Open decisions:

- Final photography style.
- Final background and lighting style.
- Minimum resolution.
- Exact product-card aspect ratio.
- Whether packaging images are global or product-specific.

## 8. Inventory, Cart, And Reservation Decisions

### 8.1 Cart Reservation Duration

Status: Proposed

Recommended default:

- Reserve stock for 30 minutes after item add or quantity update.
- Release reservations automatically after expiry.
- Revalidate reservations immediately before payment.
- Show a clear cart notice when a reservation expires.

Open decision:

- Confirm exact reservation duration.

### 8.2 Low Stock Threshold

Status: Proposed

Recommended default:

- Use product-specific or variant-specific thresholds.
- If no threshold is set, use 2 units as the default low-stock threshold.
- Avoid aggressive scarcity copy.

Open decision:

- Confirm global default threshold and whether thresholds can vary per variant.

### 8.3 Guest Cart And Logged-In Cart Behavior

Status: Proposed

Recommended default:

- Guest cart is stored against the current session.
- Logged-in saved cart is stored against the customer account.
- Guest cart does not merge into saved account cart.
- If a guest signs in during checkout, the active session cart is used for that checkout.
- Any existing saved account cart remains unchanged unless the customer explicitly replaces it.
- If the customer leaves checkout, the system preserves whichever cart is active for that session without duplicating line items.

Build requirement:

- The UI must explain the active-cart choice if both a session cart and saved account cart exist.

### 8.4 Made-To-Order Capacity

Status: Confirmed with open details

Confirmed:

- Made-to-order capacity is 1-20 pieces per 3-week period.
- Made-to-order products must show lead time and capacity expectations before payment.
- Average made-to-order lead time is 2-10 weeks unless product data overrides it.

Open decisions:

- Whether made-to-order capacity is global, product-specific, or variant-specific.
- Whether capacity resets on a rolling 3-week window or fixed calendar periods.
- Whether customers can buy multiple made-to-order items in one order.

## 9. Account And Authentication Decisions

Status: Proposed

Recommended default:

- Customers register with email and password.
- Email addresses are unique.
- Passwords are hashed with a modern password hashing algorithm.
- Password reset tokens expire.
- Login, registration, and password reset are rate limited.
- Email verification is optional unless required by the selected auth approach or business policy.
- Customer must be signed in before payment.

Open decisions:

- Whether email verification is required before checkout.
- Session lifetime.
- Remember-me behavior.
- Whether multi-factor authentication is offered or required for customers.
- Exact account deletion workflow.

Build requirement:

- Account deletion or deletion request must preserve legal order records as required while removing or anonymising data where appropriate after review.

## 10. Checkout Decisions

### 10.1 Address Validation

Status: Proposed

Recommended default:

- Checkout supports manual UK address entry.
- Postcode format is validated.
- Delivery boundary is validated against the supported UK shipping areas.
- POST TOWN is stored and displayed in uppercase.
- Address lookup is optional and can be added if a provider is selected.

Open decisions:

- Whether to use an address lookup provider.
- How to validate BFPO, Channel Islands, Isle of Man, Highlands and Islands, and Northern Ireland addresses.
- Whether phone number is required for every order or only for selected carrier/payment flows.

### 10.2 Checkout Steps

Status: Confirmed with proposed implementation

Confirmed steps:

1. Cart review.
2. Sign in or account creation before payment.
3. Customer contact details.
4. UK delivery address.
5. Shipping confirmation or method.
6. Billing address if different.
7. Payment.
8. Order confirmation.

Recommended implementation:

- Keep cart review separate from payment.
- Revalidate stock, reservation, made-to-order capacity, selected variants, and price before creating or confirming a payment.
- Preserve cart contents after payment failure.
- Store order address snapshots at order creation.

### 10.3 Abandoned Checkout And Session Expiry

Status: Open

Required decisions:

- How long checkout sessions remain active.
- Whether abandoned checkout emails are enabled.
- Whether abandoned checkout emails require marketing consent.
- Whether incomplete pending-payment orders expire automatically.
- How expired pending-payment orders release stock reservations.

Recommended launch default:

- Do not send abandoned checkout emails at first launch unless consent and email logic are fully reviewed.
- Release stock when the cart reservation expires.

## 11. Payment Decisions

### 11.1 Launch Payment Provider

Status: Open

The functional spec lists Stripe, PayPal, Square, and Airwallex as supported providers, but the build needs a launch decision.

Required decision:

- Decide whether launch must integrate all listed providers or one primary provider from the approved list.

Recommended launch default:

- Integrate one primary card and wallet provider first.
- Add additional providers after the first provider is stable.

Open decisions:

- Primary launch provider.
- Secondary provider, if any.
- Whether PayPal is required at launch.
- Whether bank transfer is required at launch.
- Whether Apple Pay and Google Pay are enabled through the selected provider.
- Whether payment methods vary by order value.

### 11.2 Payment Lifecycle

Status: Proposed

Recommended default:

- Create a payment attempt when checkout enters payment.
- Create an order at payment success, unless the provider requires a pending-payment order first.
- Treat provider webhooks as the source of truth for final payment status.
- Use idempotency keys for payment and order creation.
- Do not commit stock until payment is confirmed.
- Do not lose cart contents on payment failure.
- Log payment failures without storing raw card data.

Open decisions:

- Whether pending-payment orders are visible to customers.
- How long pending-payment orders remain valid.
- Which payment failure reasons are shown to customers.
- Exact refund initiation workflow.

### 11.3 Refunds And Cancellations

Status: Proposed

Recommended default:

- Refunds are initiated through the selected payment provider or a protected operator workflow.
- Refund records are stored locally for audit and customer order history.
- Partial refunds must preserve original order totals and item snapshots.
- Cancellation before dispatch releases or restores stock according to order status.

Open decisions:

- Whether refund records are separate database entities at launch.
- Whether refund confirmation emails are triggered automatically or manually.
- Who can approve refunds.

## 12. Shipping And Fulfilment Decisions

### 12.1 Carrier And Service Levels

Status: Open

Required decisions:

- Exact carrier or carriers.
- Exact service names.
- Dispatch working days.
- Daily order cut-off time.
- Standard dispatch time for in-stock products.
- Estimated delivery time after dispatch.
- Whether signature on delivery is required.
- Whether enhanced insured delivery is required for high-value orders.
- Whether different services apply to Channel Islands, Isle of Man, Highlands and Islands, Northern Ireland, or BFPO.

Build requirement:

- Shipping copy must be visible before checkout and repeated during checkout.
- Tracking details must be supported in order records and dispatch emails.

### 12.2 Mixed In-Stock And Made-To-Order Carts

Status: Proposed

Recommended default:

- Default option is combined shipping when a cart contains in-stock and made-to-order items.
- Customer is warned that combined shipping waits until the made-to-order item is ready.
- Separate shipping is only offered if the business confirms it operationally supports split fulfilment.
- If separate shipping is offered, the order must track item-level fulfilment statuses.

Open decision:

- Confirm whether separate shipping is available at launch.

### 12.3 Lost, Delayed, Or Damaged Parcels

Status: Open

Required decisions:

- When an order is considered delayed.
- When an order is considered lost.
- Customer support process for delivery issues.
- Whether replacement, refund, carrier claim, or investigation happens first.
- Damaged parcel evidence requirements.
- Customer communication templates.

## 13. Returns, Exchanges, And Cancellations

Status: Open

Confirmed source rules:

- Maximum return window is 14 days.
- Customer must contact the site before sending an item back.
- Buyer pays return shipment.
- Refunds are issued after return conditions are met.
- Exchanges are not supported except for ring size exchanges.
- Gift orders follow the same return rules as standard orders.
- Customers can cancel standard orders before dispatch.

Required decisions:

- Final legal returns and cancellation wording.
- Whether made-to-order items have extra cancellation or return restrictions.
- Whether personalised, engraved, altered, or resized items have extra restrictions.
- Whether ring size exchanges have a separate time limit.
- Whether ring size exchanges have a fee.
- Whether outgoing shipping cost is ever refunded.
- Return address.
- Return authorisation process.
- Condition inspection process.
- Refund rejection process.

Build requirement:

- The returns policy must be final before launch.
- Product pages and checkout must link to the policy.

## 14. Legal, Tax, Privacy, Cookies, And Compliance

Status: Open

Required before launch:

- Legal business name.
- Trading name if different.
- Business trading or registered address.
- Customer service email address.
- VAT number if required to display.
- Final VAT/tax wording.
- Terms and conditions.
- Privacy policy.
- Cookie policy.
- Returns and cancellation policy.
- Standard cancellation form where required.
- Data retention periods.
- Third-party processor list.
- Cookie categories.
- Analytics consent behavior.
- Marketing consent behavior.
- Data access and deletion request process.
- Precious metal hallmarking approach.
- Online Dealer's Notice or equivalent hallmarking content where required.

Special build note:

- The shipping boundary includes Channel Islands, Isle of Man, BFPO, and UK regions. Tax, address validation, shipping service availability, and policy wording for these destinations must be confirmed before checkout implementation is final.

Open decisions:

- Analytics provider.
- Advertising pixels or remarketing tools.
- Cookie consent provider or custom implementation.
- Whether non-essential cookies are disabled until consent.
- Data retention periods for customers, orders, enquiries, wishlist, carts, abandoned checkout, payment attempts, and marketing records.

## 15. Email Decisions

### 15.1 Transactional Email Provider

Status: Open

Required decisions:

- Transactional email provider.
- Sending domain.
- From name.
- From email address.
- Reply-to email address.
- Support inbox.
- Email logging and retry behavior.

Recommended default:

- Use a dedicated transactional email provider.
- Keep transactional and marketing email streams separate.
- Store email send events for order-critical messages.

### 15.2 Email Templates

Status: Proposed

Source template list:

- Account verification if required.
- Password reset.
- Order confirmation.
- Payment failed.
- Order dispatched.
- Tracking information.
- Made-to-order ready to ship.
- Order cancelled.
- Refund issued.
- Return or exchange update.
- Back-in-stock notification if enabled.
- Contact form acknowledgement.
- Newsletter subscription confirmation if double opt-in is used.

Build requirement:

- Transactional emails must not include marketing content unless the customer has separately opted in.
- Order confirmation must include order number, order summary, total paid in GBP, delivery details, expected dispatch or lead time, and support route.
- Dispatch email must include carrier and tracking number when available.

Open decisions:

- Exact final copy for each P0 email.
- Which order status changes trigger emails.
- Whether payment failed is an email, on-page message, or both.
- Whether contact form acknowledgement is enabled at launch.
- Whether made-to-order ready-to-ship email is automatic or manual.

## 16. Content And Merchandising Decisions

Status: Open

Required decisions:

- Homepage merchandising order.
- Featured collections.
- Featured products.
- Final collection names.
- Final collection stories.
- About page copy.
- Ring size guide content.
- Packaging and gifting copy.
- Shipping page copy.
- Returns and exchanges page copy.
- Care guidance copy.
- Product copy owner.
- Product copy approval process.
- SEO title and meta description owner.

Build requirement:

- The site should avoid mass-market, overly gothic, or costume-like presentation.
- Product information must remain easy to scan.
- UK-only delivery and GBP pricing must be discoverable before checkout.

## 17. Design System Decisions

Status: Proposed

Recommended default:

- Build a restrained premium interface that supports product evaluation.
- Use mobile-first responsive layout.
- Use clear product imagery as the main visual driver.
- Use consistent product-card sizing.
- Use accessible focus states.
- Avoid misleading scarcity patterns.
- Avoid decorative complexity that makes product details harder to scan.

Open decisions:

- Logo assets.
- Typefaces.
- Colour palette.
- Icon set.
- Product-card layout.
- Form field style.
- Button hierarchy.
- Checkout layout.
- Empty-state visual treatment.

Build requirement:

- The selected design must meet baseline accessibility requirements before launch.

## 18. Accessibility, SEO, And Performance Decisions

### 18.1 Accessibility

Status: Proposed

Recommended target:

- Build against WCAG 2.2 AA expectations where practical.

Build requirement:

- Keyboard users must be able to navigate menus, product options, cart, account, and checkout.
- Form labels and errors must be programmatically connected.
- Product option controls must work with screen readers.
- Focus states must be visible.
- Colour must not be the only way to communicate important information.

Open decisions:

- Formal accessibility target.
- Whether external accessibility testing is required before launch.

### 18.2 SEO

Status: Proposed

Recommended default:

- Use SEO-friendly slugs.
- Generate sitemap.
- Configure robots rules.
- Add canonical URLs for filtered pages where needed.
- Add product structured data where appropriate.
- Add unique metadata for product and collection pages.

Open decisions:

- SEO owner.
- Whether filtered listing pages are indexable.
- Final metadata generation rules.

### 18.3 Performance

Status: Proposed

Recommended default:

- Optimize all product images.
- Use responsive image sizes.
- Lazy-load below-the-fold imagery.
- Keep checkout scripts minimal.
- Delay non-essential third-party scripts until consent where required.

Open decisions:

- Performance budget.
- Target Lighthouse thresholds.
- Maximum acceptable checkout load time on mobile connection.

## 19. Security And Abuse Prevention Decisions

Status: Proposed

Required controls:

- HTTPS in production.
- Secure password hashing.
- Secure password reset tokens.
- Secure session cookies.
- CSRF protection where relevant.
- Input validation.
- Output escaping.
- Rate limiting on login, registration, password reset, contact forms, and checkout attempts.
- Protected developer/operator workflows.
- Audit logging for sensitive operational actions.
- No raw card storage.

Open decisions:

- Rate limit thresholds.
- Session expiry duration.
- Fraud review criteria.
- Whether high-value orders require manual review.
- Whether operator access requires multi-factor authentication.
- Backup and restore procedure.
- Incident response owner.

## 20. Analytics And Event Tracking

Status: Open

Potential events:

- Product viewed.
- Collection viewed.
- Category viewed.
- Filter applied.
- Sort changed.
- Add to cart.
- Remove from cart.
- Cart quantity changed.
- Checkout started.
- Payment succeeded.
- Payment failed.
- Newsletter signup.
- Contact form submitted.

Required decisions:

- Analytics provider.
- Whether advertising pixels are used.
- Which events are consent-dependent.
- Whether server-side tracking is used.
- How analytics events avoid storing unnecessary personal data.

Build requirement:

- Privacy and cookie policy content must match the implemented tracking.

## 21. QA, Testing, And Launch Checks

Status: Proposed

Required test coverage before launch:

- Product listing rendering.
- Product detail rendering.
- Variant selection.
- Ring size required before add to cart.
- Cart add, update, remove, and empty states.
- Stock reservation creation and expiry.
- Stock revalidation before payment.
- Guest cart to signed-in checkout behavior.
- Non-UK address rejection.
- Payment success.
- Payment failure.
- Payment webhook idempotency.
- Order creation.
- Confirmation email.
- Dispatch email or dispatch workflow.
- Contact form validation and delivery.
- Product not found.
- Collection not found.
- Empty filters.
- Cart reservation expired.
- Sold out and coming soon purchase blocking.
- Made-to-order capacity blocking.
- Basic keyboard navigation.
- Critical responsive layouts.

Open decisions:

- Browser support matrix.
- Device test matrix.
- Payment provider test cards and scenarios.
- Whether automated end-to-end tests are required before launch.
- Who signs off launch readiness.

## 22. Deployment And Operations

Status: Open

Required decisions:

- Hosting platform.
- Database hosting.
- Object storage or image provider.
- Email provider.
- Payment provider accounts.
- Domain registrar and DNS owner.
- SSL/TLS management.
- Error monitoring.
- Uptime monitoring.
- Logging provider.
- Backup schedule.
- Restore testing schedule.
- Deployment approval process.
- Rollback process.

Recommended default:

- Separate local, staging, and production environments.
- Staging should use test payment keys and non-production email behavior.
- Production secrets should only exist in production secret storage.
- Database migrations should run through a controlled deployment process.

## 23. Decision Register

The following decisions should be confirmed before build work starts or before the relevant feature is implemented.

| ID | Decision | Status | Recommended Default | Needed Before |
| --- | --- | --- | --- | --- |
| BD-001 | First launch includes only P0 or also P1 account/wishlist features | Open | P0 first, P1 immediately after | Sprint planning |
| BD-002 | Frontend and backend stack | Open | TypeScript, server-rendered storefront, PostgreSQL | Project setup |
| BD-003 | Hosting platform | Open | Managed app hosting with staging and production | Project setup |
| BD-004 | Database host | Open | Managed PostgreSQL | Project setup |
| BD-005 | Product image storage provider | Open | Managed object/image storage | Product build |
| BD-006 | Operational workflow method | Open | Protected scripts or internal screens | Catalogue/order build |
| BD-007 | Launch payment provider | Open | One primary provider first | Checkout build |
| BD-008 | PayPal at launch | Open | Defer unless required | Checkout build |
| BD-009 | Bank transfer at launch | Open | Defer unless required | Checkout build |
| BD-010 | Wallet payments | Open | Enable through selected provider if simple | Checkout build |
| BD-011 | Cart reservation duration | Open | 30 minutes | Cart build |
| BD-012 | Low-stock threshold | Open | 2 units default, override per variant | Catalogue build |
| BD-013 | Guest cart vs saved cart behavior | Proposed | Use active session cart for checkout, no merge | Auth/cart build |
| BD-014 | Address lookup provider | Open | Manual entry first | Checkout build |
| BD-015 | Carrier and service levels | Open | Tracked, insured service | Shipping build |
| BD-016 | Dispatch days and cut-off time | Open | Business-defined | Shipping page and checkout |
| BD-017 | Signature requirement | Open | Required for high-value orders if supported | Shipping build |
| BD-018 | Separate shipping for mixed carts | Open | Combined shipping only unless approved | Checkout build |
| BD-019 | Lost/delayed/damaged parcel policy | Open | Define in shipping/support policy | Policy pages |
| BD-020 | Made-to-order return restrictions | Open | Legal review required | Returns policy |
| BD-021 | Ring size exchange rules | Open | Define time limit and fee before launch | Returns policy |
| BD-022 | Legal business details | Open | Business-supplied | Policy pages |
| BD-023 | VAT/tax edge cases by destination | Open | Legal/accounting review required | Checkout build |
| BD-024 | Hallmarking and Online Dealer's Notice | Open | Legal/compliance review required | Product/legal pages |
| BD-025 | Analytics provider | Open | None until chosen | Cookie/privacy build |
| BD-026 | Cookie consent approach | Open | Block non-essential scripts until consent | Cookie/privacy build |
| BD-027 | Data retention periods | Open | Legal/privacy review required | Account/privacy build |
| BD-028 | Transactional email provider | Open | Dedicated provider | Email build |
| BD-029 | Final transactional email copy | Open | Use existing templates as draft | Email build |
| BD-030 | Product launch catalogue | Open | Business-supplied data set | Product build |
| BD-031 | Product image requirements | Open | Consistent product-card ratio and high-res sources | Design/product build |
| BD-032 | Homepage merchandising order | Open | Featured collections and products | Homepage build |
| BD-033 | Browser/device support matrix | Open | Modern evergreen browsers, mobile-first | QA planning |
| BD-034 | Accessibility target | Open | WCAG 2.2 AA where practical | Design and QA |
| BD-035 | Performance budget | Open | Define before production hardening | QA planning |
| BD-036 | Backup and restore procedure | Open | Daily backups and tested restore | Production launch |
| BD-037 | Error monitoring and alerting | Open | Add before production launch | Production launch |
| BD-038 | Fraud review rules | Open | Manual review for suspicious or high-value orders | Checkout/order build |

## 24. Build Readiness Checklist

The build is ready to begin when these items are accepted:

- P0 vs P1 launch scope is confirmed.
- Technical stack is selected.
- Hosting, database, image storage, email, and payment providers are selected.
- Operational workflow method is selected.
- Payment lifecycle and webhook strategy are confirmed.
- Cart reservation duration is confirmed.
- Shipping carrier and service rules are confirmed.
- Returns, cancellation, and ring exchange rules are confirmed.
- Legal business details are supplied.
- VAT/tax destination edge cases are reviewed.
- Hallmarking approach is confirmed.
- Analytics and cookie consent approach is confirmed.
- Data retention periods are defined.
- Product launch catalogue data is available.
- Product image standards are confirmed.
- Browser/device QA matrix is agreed.

The site is ready for public launch only when the source specs' launch acceptance criteria and this spec's open P0 decisions are satisfied.
