# Functional Spec: Ouroboros Jewellery Online Store

Status: Draft v1
Source: business-context-spec.md
Last updated: 2026-06-04

## 1. Purpose

This functional spec translates the business context for the Ouroboros Jewellery online store into build-ready website requirements.

The site must let UK customers discover premium Ouroboros-inspired jewellery, understand materials and symbolism, choose variants such as ring size, save items, manage an account, contact the brand, and complete a secure GBP checkout for UK delivery.

## 2. Product Scope

### 2.1 In Scope

- UK-only ecommerce storefront
- GBP product pricing
- Product catalogue for bracelets, necklaces, and rings
- Collection browsing
- Product listing pages
- Product detail pages
- Product image galleries
- Variant selection, especially UK ring sizes
- Ring size guide
- Cart
- Wishlist for logged-in customers
- Secure customer accounts
- Saved delivery addresses
- Newsletter opt-in and preference management
- Contact and enquiry forms
- UK checkout
- External payment processing
- Order confirmation
- Transactional emails
- Shipping, returns, packaging, privacy, terms, and contact content pages
- Admin or operational method for product, stock, order, and customer support management

### 2.2 Out Of Scope

- International shipping
- Non-GBP currencies
- Marketplace seller accounts
- Large multi-brand catalogue
- Physical store pickup
- Custom jewellery design studio
- Raw payment card storage
- Public product reviews unless added later
- Loyalty programme unless added later

## 3. Launch Assumptions

These assumptions make the first build functional while leaving commercial decisions configurable.

- Account creation is required to purchase; guest checkout is not allowed.
- Wishlist also requires login.
- Products and inventory are managed through an admin interface or ecommerce platform admin.
- Payments are handled by a trusted external payment provider.
- The store never stores raw payment card details.
- Inventory is checked when adding to cart and again before payment.
- Stock is reduced only after successful payment unless the payment provider or platform supports temporary checkout reservations.
- All prices are shown in GBP.
- VAT registration status is TBD, so the checkout must support configurable tax display.
- UK-only delivery rules must be enforced at checkout.
- Marketing emails require explicit opt-in or another verified lawful basis before launch.
- Compliance copy and legal policies require final legal/business review before launch.

## 4. User Roles

### 4.1 Guest Customer

Can:

- Browse all public pages
- Search, filter, and sort products
- View product detail pages
- View ring size guide
- Add eligible products to cart
- Update cart
- Start the sign-in or account creation step before checkout
- Create an account
- Sign up for newsletter
- Submit contact forms

Cannot:

- Complete checkout, submit payment, or place an order without an account
- Save wishlist items
- View order history
- Save addresses
- Manage newsletter preferences inside an account

### 4.2 Registered Customer

Can do everything a guest customer can do, plus:

- Log in and log out
- Reset password
- View and update account details
- Save delivery addresses
- View order history
- Save, remove, and move wishlist items to cart
- Manage newsletter preferences
- Complete checkout and place orders
- Reuse saved delivery details at checkout
- Persist cart across sessions

### 4.3 Admin User

Can:

- Create, edit, archive, and publish products
- Manage variants and stock
- Manage categories and collections
- Upload and order product images
- View, search, and update orders
- Add dispatch and tracking information
- Handle refunds through the payment provider or ecommerce platform
- View customer enquiries
- Export orders and subscriber lists where permitted
- Manage page content or trigger developer-managed content updates
- Review audit history for sensitive product, stock, and order changes

## 5. Information Architecture

### 5.1 Primary Navigation

- Home
- Shop
- Collections
- Bracelets
- Necklaces
- Rings
- Ring Size Guide
- About
- Contact

### 5.2 Utility Navigation

- Account
- Wishlist
- Cart

### 5.3 Footer Navigation

- Shipping Information
- Returns And Exchanges
- Packaging And Gifting
- Privacy Policy
- Cookie Policy
- Terms And Conditions
- Contact
- Newsletter Signup

## 6. Page Requirements

### 6.1 Home Page

Purpose: Introduce the brand, establish the Ouroboros theme, and route customers into shopping.

Must include:

- Clear brand name
- Refined hero area with jewellery-led visual direction
- Short brand positioning copy
- Featured collections
- Featured products
- Links to bracelets, necklaces, and rings
- Packaging and gifting trust signal
- UK shipping trust signal
- Newsletter signup

Acceptance criteria:

- A customer can reach product listings within one click.
- The site communicates that it sells jewellery, not only symbolic content.
- GBP and UK-only shipping context are discoverable before checkout.

### 6.2 Shop All Page

Purpose: Display all purchasable or previewable products.

Must include:

- Product grid
- Product image
- Product name
- Category
- Collection
- Price in GBP
- Material
- Availability status
- Filter controls
- Sort controls
- Empty state

Required filters:

- Category
- Collection
- Material
- Availability
- Price range
- Ring size when category is rings

Required sort options:

- Availability

Acceptance criteria:

- Sold out and coming soon products are visible but cannot be added directly to cart.
- Filters can be cleared.
- Empty results show useful text and a route back to all products.

### 6.3 Category Pages

Pages:

- Bracelets
- Necklaces
- Rings

Must behave like filtered product listing pages.

Additional ring page requirements:

- Link to ring size guide
- Ring size filter
- Clear message that UK sizing is the default

### 6.4 Collection Pages

Purpose: Group products by symbolic theme, form, or finish.

Must include:

- Collection title
- Collection story or symbolic meaning
- Product grid
- Same product card fields as Shop All
- Optional collection hero image

Acceptance criteria:

- A product can only belong to one collection.
- Collection pages remain functional if a collection has no available products.

### 6.5 Product Detail Page

Purpose: Give the customer enough information to make a confident purchase decision.

Must include:

- Product name
- Product category
- Collection name
- Price in GBP
- Material and purity or fineness
- Availability status
- Product description
- Symbolic inspiration or meaning
- Size and dimensions
- Weight
- Variant selector where applicable
- Quantity selector where applicable
- Add to cart button
- Wishlist button
- Product image gallery
- UK shipping information
- Made-to-order lead time where applicable
- Packaging and gifting information
- Care guidance
- Returns or exchange information
- Hallmarking or material-compliance information where relevant
- Related products or collection link

Image gallery must support:

- Main product image
- Close-up detail image
- Multiple angles where relevant
- Detail views of clasps, chains, bands, stones, engraving, and texture where present

Add to cart rules:

- In stock products can be added to cart.
- Low stock products can be added to cart with honest urgency messaging.
- Sold out products cannot be added to cart.
- Coming soon products cannot be added to cart.
- Made-to-order products can be added to cart only if lead time is shown.
- Rings require a selected ring size before add to cart.

Acceptance criteria:

- The add to cart button is disabled until all required product options are selected.
- The page explains why an item cannot be purchased if it is unavailable.
- A customer can access ring size help from every ring product page.

### 6.6 Ring Size Guide

Purpose: Help customers select the correct UK ring size.

Must include:

- UK ring sizes as the primary format
- Measuring guidance
- Guidance for customers unsure of their size
- Contact link for sizing help
- Disclaimer that the guide is advisory

Acceptance criteria:

- UK sizes are visually dominant.
- Ring product pages link to the guide without leaving the customer stranded.

### 6.7 Cart Page

Purpose: Let customers review and update selected items before checkout.

Must include:

- Product image
- Product name
- Variant details such as ring size
- Price
- Quantity where applicable
- Line total
- Availability messages
- Remove item action
- Subtotal
- Shipping estimate or UK shipping note
- Tax display if applicable
- Checkout button

Cart rules:

- Sold out and coming soon products block checkout.
- If an item becomes unavailable, the cart shows a clear message and disables checkout until resolved.
- Made-to-order items show lead time in cart.
- Quantity cannot exceed available stock unless the product is made to order.
- Cart persists for logged-in users.
- Guest cart persists for the current browser session.
- Guest cart merges with account cart after login, with duplicate lines merged when variant details match.

Acceptance criteria:

- Customers can update or remove items without losing the rest of the cart.
- Checkout total is understandable before payment.
- Non-UK shipping restriction is visible before checkout.

### 6.8 Checkout

Purpose: Securely collect contact, delivery, shipping, and payment details.

Checkout steps:

1. Cart review
2. Sign in or account creation if the customer is not already authenticated
3. Contact details
4. Delivery address
5. Shipping method or shipping confirmation
6. Payment
7. Confirmation

Must collect:

- Email address
- First name
- Last name
- UK delivery address
- Billing address if different
- Phone number if required by carrier or payment provider
- Gift message if enabled
- Marketing opt-in choice

Validation rules:

- Delivery country must be United Kingdom.
- Required address fields must be completed.
- Email must use a valid format.
- Customer must be signed in before payment.
- Ring size and required variants must remain selected.
- Checkout must re-check stock before payment.

Payment rules:

- Payment is processed by an external provider.
- Payment errors show a clear retry path.
- Orders are created only when payment succeeds, or are created as pending payment if required by provider flow.
- No raw card details are stored by the store.

Confirmation page must include:

- Order number
- Customer email
- Order summary
- Shipping address
- Shipping method or shipping note
- Total paid in GBP
- Expected dispatch or made-to-order lead time
- Contact support route

Acceptance criteria:

- Guest checkout cannot complete purchase; unauthenticated customers must sign in or create an account before payment.
- A non-UK delivery address cannot complete checkout.
- Payment failure does not lose the cart.
- Successful payment triggers an order confirmation email.

### 6.9 Account Area

Pages:

- Sign in
- Register
- Password reset
- Account overview
- Account details
- Saved addresses
- Order history
- Wishlist
- Newsletter preferences

Account rules:

- Email addresses must be unique.
- Passwords must be securely hashed.
- Password reset links must expire.
- Sensitive account changes require confirmation.
- Customers can log out from all authenticated account areas.
- Customers can request account deletion or data access through a defined support route.

Acceptance criteria:

- Registered customers can view their past orders.
- Saved addresses can be added, edited, and removed.
- Newsletter preference changes are saved and auditable.

### 6.10 Wishlist

Purpose: Let logged-in customers save products for later.

Rules:

- Wishlist requires login.
- Guests clicking wishlist are prompted to sign in or create an account.
- Duplicate wishlist entries are prevented.
- Wishlist displays product image, name, price, availability, and selected variant where relevant.
- Customers can remove items.
- Customers can move available items to cart.
- Sold out and coming soon wishlist items cannot be moved to cart.

Acceptance criteria:

- Wishlist persists across devices for the same account.
- Availability and price shown in wishlist reflect current product data.

### 6.11 Contact Page

Purpose: Give customers a reliable route to support.

Must include:

- Customer service email address
- Contact form
- Enquiry type selector
- Name field
- Email field
- Message field
- Optional order number field
- Privacy note

Enquiry types:

- Product question
- Ring sizing help
- Order status
- Shipping question
- Returns or exchange
- Made-to-order enquiry
- General enquiry

Acceptance criteria:

- Successful submission shows confirmation.
- Submission triggers acknowledgement to customer if email service is configured.
- Admin or support recipient receives enquiry details.

### 6.12 Content Pages

Required pages:

- About The Brand
- Shipping Information
- Packaging And Gifting
- Returns And Exchanges
- Privacy Policy
- Cookie Policy
- Terms And Conditions

Content requirements:

- Copy must be clear, trustworthy, and aligned with refined symbolic positioning.
- Policy pages must be easy to find from footer.
- Legal and policy content must be reviewed before launch.

## 7. Data Model

### 7.1 Product

Fields:

- product_id
- sku
- name
- slug
- category
- collection_ids
- material
- purity_or_fineness
- finish
- description
- symbolic_meaning
- dimensions
- weight
- care_guidance
- packaging_note
- returns_note
- price_gbp
- tax_class
- availability_status
- low_stock_threshold
- made_to_order_lead_time
- is_published
- seo_title
- seo_description
- created_at
- updated_at

### 7.2 Variant

Fields:

- variant_id
- product_id
- variant_sku
- option_type
- option_value
- price_override_gbp
- stock_quantity
- availability_status
- made_to_order_allowed
- lead_time_override
- is_active

Examples:

- Ring size: UK L, UK M, UK N
- Chain length: 16 inch, 18 inch
- Bracelet size: small, medium, large

### 7.3 Product Image

Fields:

- image_id
- product_id
- variant_id optional
- image_url
- alt_text
- image_type
- sort_order
- is_primary

Image types:

- Main
- Detail
- Scale
- Angle
- Packaging

### 7.4 Collection

Fields:

- collection_id
- name
- slug
- description
- symbolic_theme
- hero_image
- seo_title
- seo_description
- sort_order
- is_published

### 7.5 Customer

Fields:

- customer_id
- email
- password_hash
- first_name
- last_name
- phone
- marketing_status
- created_at
- updated_at
- last_login_at

### 7.6 Address

Fields:

- address_id
- customer_id
- first_name
- last_name
- address_line_1
- address_line_2
- town_or_city
- county
- postcode
- country
- phone
- is_default

### 7.7 Cart

Fields:

- cart_id
- customer_id optional
- session_id optional
- status
- created_at
- updated_at
- expires_at

### 7.8 Cart Item

Fields:

- cart_item_id
- cart_id
- product_id
- variant_id optional
- quantity
- price_snapshot_gbp
- added_at

### 7.9 Wishlist Item

Fields:

- wishlist_item_id
- customer_id
- product_id
- variant_id optional
- added_at

### 7.10 Order

Fields:

- order_id
- order_number
- customer_id
- email
- status
- payment_status
- fulfilment_status
- subtotal_gbp
- shipping_gbp
- tax_gbp
- total_gbp
- currency
- shipping_address_snapshot
- billing_address_snapshot
- shipping_method
- tracking_number
- carrier
- gift_message
- marketing_opt_in_at_checkout
- created_at
- updated_at

### 7.11 Order Item

Fields:

- order_item_id
- order_id
- product_id
- variant_id optional
- product_name_snapshot
- variant_label_snapshot
- sku_snapshot
- quantity
- unit_price_gbp
- line_total_gbp
- made_to_order_lead_time_snapshot

### 7.12 Enquiry

Fields:

- enquiry_id
- name
- email
- enquiry_type
- order_number optional
- message
- status
- created_at

### 7.13 Marketing Preference

Fields:

- customer_id or email
- new_item_drops
- collection_launches
- sale_offers
- back_in_stock_updates
- consent_source
- consent_timestamp
- unsubscribe_timestamp
- updated_at

## 8. Availability And Inventory Rules

### 8.1 Availability Statuses

- In stock: purchasable.
- Low stock: purchasable with honest low-stock messaging.
- Sold out: visible but not purchasable.
- Coming soon: visible but not purchasable.
- Made to order: purchasable only with lead time displayed.

### 8.2 Stock Rules

- Variant stock overrides product stock when variants exist.
- Ring stock is tracked by UK ring size.
- Checkout must block purchase if requested quantity exceeds available stock.
- Low stock threshold can be global or product-specific.
- Overselling is not allowed for stock-tracked products.
- Admin stock adjustments should be recorded.

### 8.3 Back-In-Stock

If enabled:

- Sold out products can show back-in-stock signup.
- Coming soon products can show launch notification signup.
- Signup requires email and consent context.

## 9. Order Lifecycle

### 9.1 Order Statuses

Supported statuses:

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

### 9.2 Status Behavior

- Pending payment: order exists but payment has not completed.
- Payment failed: payment attempt failed; customer can retry if cart/order remains valid.
- Paid: payment confirmed.
- Processing: order is being prepared.
- Made to order: item production is required before dispatch.
- Ready to dispatch: order is packed or ready for carrier handoff.
- Dispatched: order has been sent.
- Delivered: delivery confirmation received or manually marked.
- Cancelled: order cancelled before fulfilment or as allowed by policy.
- Refunded: full refund issued.
- Partially refunded: partial refund issued.
- Returned: returned item received or return process completed.

### 9.3 Customer Visibility

Customers can see:

- Order number
- Order date
- Order status
- Items purchased
- Delivery address
- Total paid
- Tracking details when available

## 10. Shipping And Fulfilment

### 10.1 Shipping Boundary

The site ships only within the United Kingdom.

TBD before launch:

- Whether Channel Islands, Isle of Man, BFPO, Highlands and Islands, and remote-area surcharges are supported.

### 10.2 Shipping Display

Shipping information must appear:

- Product detail page
- Cart
- Checkout
- Shipping information page
- Order confirmation email

### 10.3 Fulfilment Rules

- In-stock dispatch time is configurable.
- Made-to-order lead time is product or variant specific.
- Mixed carts containing in-stock and made-to-order items must show whether the order ships together or separately.
- Tracking availability must be shown before checkout if tracked shipping is used.
- Higher value orders may require signature on delivery if enabled.

## 11. Returns, Exchanges, And Cancellations

### 11.1 Policy Requirements

The site must publish clear returns, exchanges, and cancellation information before checkout.

The policy must define:

- Return window
- Exchange window
- Cancellation route
- Refund timing
- Return postage responsibility
- Condition requirements
- Handling of worn, damaged, altered, engraved, personalised, and made-to-order items
- Ring size exchange policy
- Gift return or exchange process

### 11.2 Functional Requirements

- Product pages link to returns or exchange information.
- Checkout links to returns and cancellation policy.
- Order confirmation email includes or links to return and cancellation information.
- Customer support can identify return enquiries by order number.

## 12. Packaging And Gifting

### 12.1 Product Page Requirements

Product pages must state that jewellery arrives in gift-appropriate packaging.

### 12.2 Checkout Requirements

If gift options are enabled:

- Customer can mark order as gift.
- Customer can enter gift message.
- Gift message has a character limit.
- Pricing is excluded from physical parcel when order is marked as gift.

### 12.3 Operational Requirements

- Packaging must protect bracelets, necklaces, and rings.
- Packaging should include care card or care guidance where appropriate.
- Material or product information card should be included where appropriate.

## 13. Email Requirements

### 13.1 Transactional Emails

Required:

- Password reset
- Order confirmation
- Payment failed
- Order dispatched
- Refund issued
- Contact form acknowledgement

Optional:

- Account verification
- Order cancelled
- Return or exchange update
- Back-in-stock notification
- Newsletter subscription confirmation

### 13.2 Marketing Emails

Preference categories:

- New item drops
- Collection launches
- Sale offers
- Back-in-stock updates

Rules:

- Newsletter signup is optional.
- Marketing consent must be explicit or legally reviewed if relying on another basis.
- Customers can unsubscribe.
- Customers can update preferences.
- Transactional emails must not include marketing content unless customer has separately opted in.

## 14. Admin Functional Requirements

### 14.1 Product Management

Admin can:

- Create product
- Edit product
- Archive product
- Publish or unpublish product
- Assign category
- Assign collection
- Set material, dimensions, weight, care, and symbolic meaning
- Add SEO fields
- Upload images
- Reorder images
- Manage variants
- Set availability status
- Set made-to-order lead time

### 14.2 Inventory Management

Admin can:

- View stock by product and variant
- Adjust stock
- Set low-stock thresholds
- Mark sold out
- Mark coming soon
- Enable or disable made-to-order status

### 14.3 Order Management

Admin can:

- View orders
- Search by order number, email, status, and date
- Update fulfilment status
- Add tracking number
- Mark dispatched
- Trigger dispatch email
- Handle cancellation and refund actions through approved payment/provider workflow

### 14.4 Support Management

Admin or support user can:

- View enquiries
- Filter by enquiry type
- Mark enquiries open, pending, or resolved
- Reference order number when supplied

## 15. Search, Filtering, And Sorting

### 15.1 Search

Searchable fields:

- Product name
- Collection
- Category


### 15.2 Filters

Required filters:

- Category
- Collection
- Material
- Availability
- Price
- Ring size where relevant

Optional filters:

- Finish
- Gift suitability
- Made to order

### 15.3 Empty States

When no results match:

- Show a clear empty message.
- Offer to clear filters.
- Link back to Shop All.

## 16. UX And Design Requirements

### 16.1 Visual Direction

The interface should feel:

- Refined
- Mysterious
- Elegant
- Trustworthy
- Premium
- Wearable rather than costume-like

Avoid:

- Overly gothic styling
- Mass-market discount aesthetic
- Decorative clutter that obscures product information
- Misleading scarcity messaging

### 16.2 Usability Requirements

- Product information must be easy to scan.
- Purchase actions must be visually clear.
- Unavailable states must be explained.
- Mobile layout must support browsing, cart, and checkout comfortably.
- Forms must show clear field labels and validation errors.
- Customers must never be surprised by UK-only shipping at payment time.

## 17. Accessibility Requirements

Minimum requirements:

- Keyboard navigable menus, forms, product options, cart, and checkout
- Visible focus states
- Sufficient text contrast
- Alt text for product images
- Form labels connected to inputs
- Error messages connected to fields
- Ring size and variant controls usable by screen readers
- Buttons and links named clearly
- No critical information conveyed by color alone

## 18. SEO Requirements

Must include:

- SEO-friendly URLs
- Unique page titles
- Unique meta descriptions for product and collection pages
- Product structured data where appropriate
- Sitemap
- Robots rules
- Canonical URLs for filtered listing pages where needed
- Descriptive image alt text

URL examples:

- /shop
- /collections/eternal-return
- /bracelets
- /necklaces
- /rings
- /products/silver-serpent-ring
- /ring-size-guide

## 19. Performance Requirements

Minimum requirements:

- Optimised product images
- Lazy loading for below-the-fold imagery
- Responsive image sizes
- Fast product listing interactions
- Checkout pages load reliably on mobile connections
- No unnecessary third-party scripts before consent where consent is required

## 20. Security Requirements

Must include:

- HTTPS everywhere in production
- Secure password hashing
- Secure session cookies
- Password reset tokens with expiry
- Rate limiting for login, register, reset password, checkout, and contact forms
- CSRF protection where relevant
- Input validation and output escaping
- Admin-only access controls
- Audit logging for sensitive admin actions
- No raw payment card storage

## 21. Privacy, Cookies, And Analytics

### 21.1 Privacy

The site must publish a privacy policy explaining:

- What customer data is collected
- Why it is collected
- How long it is retained
- Which third-party processors are used
- How customers can request access, correction, or deletion
- How marketing preferences are managed

### 21.2 Cookies

The site must distinguish:

- Strictly necessary cookies
- Analytics cookies
- Marketing cookies

Cookie consent must be implemented for non-essential cookies where required.

### 21.3 Analytics

Analytics events should include:

- Product viewed
- Collection viewed
- Search performed
- Filter applied
- Add to cart
- Remove from cart
- Checkout started
- Payment succeeded
- Payment failed
- Newsletter signup
- Contact form submitted

Analytics implementation must respect cookie and consent settings.

## 22. Legal And Compliance Implementation Notes

The site must include enough pre-purchase information for online selling, including business identity, contact details, goods description, price, payment methods, delivery arrangements, delivery costs, cancellation information, and contract confirmation.

Precious metal products must include accurate material descriptions. Hallmarking requirements and the online Dealer's Notice must be checked and implemented where required for silver and white gold products.

Marketing and cookie behavior must be reviewed against current UK data protection, PECR, and ICO guidance before launch.

Compliance reference links checked while drafting:

- GOV.UK distance selling: https://www.gov.uk/online-and-distance-selling-for-businesses/distance-selling
- GOV.UK returns and refunds: https://www.gov.uk/accepting-returns-and-giving-refunds
- GOV.UK hallmarking summary: https://www.gov.uk/government/publications/hallmarking-guidance-notes/hallmarking-is-the-law-guidance-summary
- GOV.UK hallmarking compliance: https://www.gov.uk/guidance/hallmarking-how-businesses-can-comply-with-the-law
- ICO electronic marketing guidance: https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guide-to-pecr/electronic-and-telephone-marketing/

## 23. Error And Empty States

Required states:

- Product not found
- Collection not found
- No products in category
- No search results
- Cart empty
- Wishlist empty
- Account order history empty
- Product sold out
- Product coming soon
- Variant unavailable
- Checkout address invalid
- Checkout non-UK address rejected
- Payment failed
- Contact form failed
- Newsletter signup failed
- Server error
- Maintenance mode if needed

Each state must explain what happened and offer the next useful action.

## 24. Acceptance Criteria

The site is functionally complete when:

- Customers can browse home, shop, category, collection, and product pages.
- Product pages show material, price, availability, size, weight, images, care, packaging, shipping, and returns information.
- Rings require UK ring size selection before purchase.
- Cart supports add, remove, quantity update, selected variants, subtotal, and availability changes.
- Sold out and coming soon products cannot be purchased.
- Made-to-order products show lead time before checkout.
- Registered customers can use account, saved addresses, order history, wishlist, and newsletter preferences.
- Guests can browse and build a cart, but must sign in or create an account before checkout payment or purchase.
- Checkout blocks non-UK delivery addresses.
- Checkout shows product price, shipping, tax where applicable, and total in GBP.
- Successful payment creates an order and sends confirmation email.
- Payment failure gives a clear retry path without losing cart.
- Contact form routes enquiries with the correct enquiry type.
- Marketing signup is optional and consent is stored.
- Required policy pages are accessible from footer.
- Admin or platform operations can manage products, images, variants, stock, orders, tracking, refunds, and enquiries.
- Mobile, accessibility, security, and performance requirements are met at launch baseline.

## 25. Open Decisions

The following decisions still need business confirmation:

- Ecommerce platform or custom build
- Payment provider
- Accepted payment methods
- VAT registration and tax display
- Shipping carrier
- Shipping cost and free shipping threshold
- Supported UK territories and remote areas
- Dispatch timelines
- Made-to-order lead times
- Return and exchange policy specifics
- Gift message support
- Discount code support
- Back-in-stock notification support
- Analytics and advertising tools
- Cookie consent provider or implementation
- Legal business name, address, and customer service contact
- Final hallmarking and Dealer's Notice implementation
- Whether wishlist and full account features are launch-critical or phase-two
