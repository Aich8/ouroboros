# Functional Spec: Ouroboros Jewellery Online Store

Status: Draft v2
Source: business-context-spec.md
Last updated: 2026-06-12

## 1. Purpose

This functional spec converts the approved business context for the Ouroboros Jewellery online store into build-ready system requirements.

The site must let UK customers discover premium Ouroboros-inspired silver and white gold jewellery, understand product meaning and material, choose required variants such as ring size, build a cart, create a secure account, complete a GBP checkout for UK delivery, and receive clear operational communication after purchase.

## 2. Source Of Truth Decisions

The following decisions from the current business context override older spec assumptions:

- The store uses a custom ecommerce platform.
- The store sells only in pound sterling.
- The business is VAT registered, and displayed prices include VAT or other applicable taxes.
- UK shipping is free.
- Shipping is UK-only and includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Channel Islands, Isle of Man, and BFPO addresses.
- Account creation or sign-in is required before payment and order placement.
- Guest browsing and guest cart building are allowed before account creation.
- Guest carts do not merge into saved logged-in customer carts.
- The store does not include an internal product search engine in the current version.
- Product discovery relies on navigation, category pages, collection pages, filtering, and sorting.
- Raw payment card details are never stored by the store.
- Payments are single upfront payments only. Instalments and split payments are not supported.
- Supported payment providers include Stripe, PayPal, Square, and Airwallex.
- Product, inventory, order, refund, fulfilment, enquiry, content, and email preference operations are handled by the developer/operator. A separate admin management interface is not required for the current version.

## 3. Product Scope

### 3.1 In Scope

- UK-only ecommerce storefront
- Custom ecommerce platform
- Local, staging, and production environments
- GBP pricing
- VAT-inclusive price display
- Free UK shipping
- Silver and white gold jewellery
- Bracelets, necklaces, and rings
- Product listing pages
- Product detail pages
- Collection and category browsing
- Collection and category filtering
- Product availability statuses
- Variant selection, especially UK ring sizes
- Ring size guide
- Gift-appropriate jewellery packaging
- Secure customer accounts
- Saved delivery addresses
- Account deletion request or flow
- Shopping cart
- Cart inventory reservations
- Wishlist for logged-in customers
- Email marketing opt-in and preferences
- Contact support forms
- Secure checkout and shipping flow
- Payment provider integrations
- Order confirmation and transactional emails
- Developer/operator management of product, inventory, order, refund, fulfilment, enquiry, and email preference data
- Required legal, policy, privacy, cookie, shipping, returns, and gifting content

### 3.2 Out Of Scope

- International shipping
- Non-GBP currencies
- Internal product search engine
- Infinite scroll
- Dedicated admin management interface unless added later
- Marketplace seller accounts
- Large multi-brand catalogue
- Physical store pickup unless added later
- Custom design studio unless added later
- Instalment payments
- Split payments
- Raw payment card storage

## 4. User Roles

### 4.1 Guest Customer

Can:

- Browse public pages.
- Browse products by shop, category, and collection.
- Filter and sort product listings.
- View product detail pages.
- View ring size guide and policy pages.
- Add eligible products to a guest cart.
- Update or remove guest cart items.
- Start checkout.
- Create an account or sign in before payment.
- Submit contact forms.
- Opt in to newsletter marketing where available.

Cannot:

- Complete payment or place an order without an account.
- Save wishlist items.
- View order history.
- Save delivery addresses.
- Manage account-level newsletter preferences.

### 4.2 Registered Customer

Can do everything a guest customer can do, plus:

- Log in and log out securely.
- Reset forgotten password.
- View and update account details.
- Save and manage delivery addresses.
- View order history.
- Manage wishlist items.
- Manage newsletter preferences.
- Persist cart contents between sessions.
- Complete checkout and place orders.
- Request or complete account deletion with a clear warning.

### 4.3 Developer/Operator

Can manage operational data through developer-managed tools, platform screens, scripts, or protected internal workflows:

- Products and variants.
- Product images and alt text.
- Collections and category assignment.
- Inventory, stock reservations, and made-to-order capacity.
- Orders, order statuses, cancellations, refunds, fulfilment, carrier, and tracking data.
- Customer enquiries.
- Email preferences and subscriber exports where legally permitted.
- Content such as product descriptions, collection copy, homepage content, and operational configuration.
- Audit history for sensitive stock, order, refund, and customer data changes.

## 5. Information Architecture

### 5.1 Primary Navigation

- Home
- Shop all
- Collections
- Bracelets
- Necklaces
- Rings
- Ring size guide
- About
- Contact

### 5.2 Utility Navigation

- Account
- Wishlist
- Cart

### 5.3 Footer Navigation

- Shipping information
- Packaging and gifting
- Returns and exchanges
- Privacy policy
- Cookie policy
- Terms and conditions
- Contact
- Newsletter signup or preferences route

## 6. Page Requirements

### 6.1 Home Page

Purpose: Introduce the Ouroboros Jewellery brand and route customers into product discovery.

Must include:

- Clear brand name.
- Jewellery-led visual direction.
- Concise copy around eternity, renewal, transformation, symbolic meaning, and premium craftsmanship.
- Featured collections.
- Featured products.
- Links to bracelets, necklaces, and rings.
- Gift-appropriate packaging trust signal.
- UK-only free shipping trust signal.
- Newsletter signup or route where marketing signup is enabled.

Acceptance criteria:

- The page clearly communicates that the site sells jewellery.
- A customer can reach product listings within one click.
- UK-only delivery and GBP pricing context are discoverable before checkout.

### 6.2 Shop All Page

Purpose: Display all published products that are purchasable or previewable.

Must include:

- Product grid.
- Product image.
- Product name.
- Category.
- Collection.
- Material.
- Availability status.
- Price in GBP.
- VAT-inclusive price note where appropriate.
- Filter controls.
- Sort controls.
- Empty state when no products match selected filters.

Required filters:

- Category.
- Collection.
- Material.
- Availability.
- Price range.
- Ring size when browsing rings.

Required sort options:

- Availability.
- Price low to high if supported by product data.
- Price high to low if supported by product data.
- Newest if product publish dates are available.

Rules:

- Sold out and coming soon products may be visible but cannot be added directly to cart.
- Infinite scroll must not be used.
- Internal keyword search is not included in the current version.

### 6.3 Category Pages

Pages:

- Bracelets.
- Necklaces.
- Rings.

Rules:

- Category pages behave like filtered product listing pages.
- Necklace pages show necklaces only.
- Ring pages show rings only.
- Bracelet pages show bracelets only.
- Ring pages include ring size filtering and a clear route to the ring size guide.
- Ring pages must state that UK sizing is the default.

### 6.4 Collection Pages

Purpose: Group products by symbolic interpretation, form, or finish.

Must include:

- Collection title.
- Collection story or symbolic meaning.
- Product grid.
- Same product card fields as Shop All.
- Optional collection hero image.

Rules:

- Collections may include themes such as Eternal Return, Renewal, Devourer, Circle of Becoming, Silver Serpent, and White Gold Ouroboros.
- A collection page must remain usable when no products are available.

### 6.5 Product Detail Page

Purpose: Give the customer enough information to make a confident purchase decision.

Must include:

- Product name.
- SKU or product reference where appropriate.
- Product category.
- Collection name.
- Material, including purity or fineness where relevant.
- Finish where relevant.
- Product description.
- Symbolic inspiration or meaning.
- Size information.
- Dimensions where relevant.
- Weight.
- Product image gallery.
- Availability status.
- Price in GBP.
- VAT-inclusive price note or tax wording.
- UK-only free shipping information.
- Packaging and gifting information.
- Care guidance.
- Returns or exchange information.
- Made-to-order lead time where relevant.
- Hallmarking or material-compliance information where relevant.
- Variant selector where relevant.
- Quantity selector where relevant.
- Add to cart action.
- Wishlist action or login prompt where wishlist is enabled.

Product images should support:

- Main product image.
- Close-up detail image.
- Scale or worn image where possible.
- Multiple angles where relevant.
- Clear views of clasps, chains, bands, stones, engraving, or texture if present.

Add to cart rules:

- In stock products can be added to cart.
- Low stock products can be added to cart with honest urgency messaging.
- Sold out products cannot be added to cart.
- Coming soon products cannot be added to cart.
- Made-to-order products can be added to cart only when lead time and production expectations are clearly shown.
- Rings require a selected UK ring size before add to cart.
- Quantity cannot exceed available stock or made-to-order capacity.

### 6.6 Ring Size Guide

Purpose: Help customers choose a UK ring size before purchase.

Must include:

- UK ring sizes as the primary format.
- Optional international comparison sizes, with UK sizing still dominant.
- Measuring guidance.
- Guidance for customers unsure of their size.
- Contact route for ring sizing help.
- Advisory disclaimer.

Rules:

- Ring products must include size selection before purchase.
- Ring product pages must link to the guide.
- Available ring sizes and stock by size should be shown where possible.
- Made-to-order handling must be shown where relevant.

### 6.7 Cart Page

Purpose: Let customers review, update, and validate selected items before checkout.

Must include:

- Product image.
- Product name.
- Selected variant details such as ring size.
- Availability messages.
- Unit price in GBP.
- Quantity where applicable.
- Line total.
- Remove action.
- Subtotal.
- Free UK shipping note.
- Tax wording showing prices include VAT or applicable taxes.
- Checkout button.

Cart rules:

- Guests can build a cart before account creation.
- Logged-in customer carts persist between sessions.
- Guest carts do not merge into saved logged-in carts.
- If a guest signs in with an active session cart, the active cart may be used for the current checkout, but it must not silently merge into any existing saved account cart.
- If both a guest session cart and saved account cart exist, the customer must get a clear choice or the system must define one active cart without duplicating line items.
- Stock is reserved when an item is added to cart.
- Cart reservation duration must be configured before build.
- Quantity is limited by available stock.
- Sold out and coming soon items block checkout.
- If a cart item becomes sold out or invalid, the cart shows a clear notice and prevents payment until the item is removed or adjusted.
- If product price changes, the current price is reflected in cart and payment.
- Made-to-order products show lead time in cart.
- Mixed carts containing in-stock and made-to-order items trigger the combined shipping choice described in fulfilment rules.

### 6.8 Wishlist

Purpose: Let logged-in customers save products for later.

Rules:

- Wishlist requires login.
- Guests attempting to save a wishlist item are prompted to sign in or create an account.
- Duplicate wishlist items are prevented.
- Wishlist items are saved to the customer account and appear across devices after login.
- Wishlist displays product image, name, selected variant where relevant, price in GBP, and availability.
- Customers can remove wishlist items.
- Customers can move available wishlist items to cart.
- Sold out and coming soon wishlist items cannot be moved to cart.
- Wishlist does not reserve stock.
- If product price changes, the current price is reflected in the wishlist.

### 6.9 Account Area

Pages:

- Register.
- Sign in.
- Password reset.
- Account overview.
- Account details.
- Saved delivery addresses.
- Order history.
- Wishlist.
- Newsletter preferences.
- Account deletion confirmation or request route.

Account rules:

- Customers register with email and password.
- Email addresses must be unique.
- Passwords must be securely hashed.
- Authentication sessions must be protected.
- Password reset links or tokens must expire.
- Customers can log out securely.
- Sensitive account actions require confirmation.
- Saved addresses require validation.
- Account deletion must warn that saved addresses, wishlist items, saved cart contents, and account preferences will be lost.
- Customer data must be handled in line with UK data protection expectations.

### 6.10 Checkout

Purpose: Securely collect account, contact, delivery, shipping, billing, and payment details.

Checkout steps:

1. Cart review.
2. Sign in or account creation before payment.
3. Customer contact details.
4. UK delivery address.
5. Shipping confirmation or method.
6. Billing address if different.
7. Payment.
8. Order confirmation.

Must collect:

- Email address.
- First name.
- Last name.
- UK shipping address.
- Billing address if different.
- Phone number where required by carrier or payment provider.
- Marketing opt-in choice.
- Gift message if enabled.

UK address fields:

- Addressee line, meaning recipient name.
- Organization or department, if applicable.
- Unit, apartment, or flat number, if applicable.
- Building or house number and street.
- Locality or dependent locality, if applicable.
- POST TOWN or city, stored and displayed in ALL CAPS.
- Postcode, such as EH14 5AN.

Validation rules:

- Customer must be signed in before payment.
- Delivery address must be within the UK shipping boundary.
- Non-UK addresses must prevent checkout completion and explain the UK-only shipping rule.
- Required address fields must be completed.
- Email must use a valid format.
- Required variants, including ring size, must remain selected.
- Checkout must revalidate product availability, stock reservation, price, and made-to-order capacity before payment.
- Payment must be prevented if any required payment information is missing.

Checkout totals must show:

- Product price.
- Quantity.
- Ring size or selected option.
- Free shipping cost.
- Taxes where applicable.
- Total order cost in GBP.

### 6.11 Payment And Order Creation

Purpose: Process payments securely and create accurate order records.

Payment requirements:

- Supported payment methods include credit card, digital wallet, and bank transfer.
- Supported providers include Stripe, PayPal, Square, and Airwallex.
- Payment is made as a single upfront payment.
- Instalments and split payments are not supported.
- The store must not store raw payment card details.
- Payment errors must show a clear retry path.

Payment must fail or be prevented when:

- Required payment information has not been provided.
- The payment method does not hold the required funds.
- The item is not in stock or the required reservation is invalid.
- The requested made-to-order capacity is no longer available.

Order rules:

- Successful payment creates an order unless provider flow requires a pending-payment order first.
- Order item records snapshot product name, SKU, variant label, quantity, unit price, line total, and made-to-order lead time.
- Stock is committed after successful payment from the reserved cart stock.
- Payment failure must not lose cart contents.
- Confirmation page and email must include order number, customer email, order summary, shipping address, shipping note or method, total paid in GBP, expected dispatch or made-to-order lead time, and support route.

### 6.12 Shipping And Fulfilment

Shipping boundary:

- England.
- Scotland.
- Wales.
- Northern Ireland.
- Highlands and Islands.
- Channel Islands.
- Isle of Man.
- BFPO addresses.

Shipping requirements:

- Shipping is free for UK orders.
- Shipping information must be visible before checkout and repeated during checkout.
- All deliveries should use carrier services.
- All deliveries should be tracked.
- Tracked delivery availability must be communicated.
- Enhanced carrier service should be used for security.
- Made-to-order products show an average lead time of 2-10 weeks unless overridden by product data.

Shipping details must include:

- UK-only shipping notice.
- Estimated dispatch time.
- Estimated delivery time.
- Free shipping notice.
- Made-to-order lead times where relevant.
- Delivery restrictions.
- Tracked delivery information.
- Carrier service information where available.

Mixed cart rules:

- If a cart contains both in-stock and made-to-order items, checkout must warn that combined shipping waits until the made-to-order item is ready.
- If the customer accepts combined shipping, the order ships together when the made-to-order item is ready.
- If the customer accepts combined shipping, the customer receives an email notification when the made-to-order item is ready to ship.
- If the customer declines combined shipping, eligible in-stock items may ship separately.
- If the customer declines combined shipping, the customer still receives a notification when the made-to-order item is ready.

### 6.13 Order Lifecycle

Supported order statuses:

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

Customer-visible order data:

- Order number.
- Order date.
- Order status.
- Items purchased.
- Delivery address.
- Total paid.
- Tracking details when available.

Operational requirements:

- The implementation must define who or what can change each status.
- Status changes that trigger emails must be defined.
- Customer-visible statuses must be clear and non-technical.
- Refund, cancellation, return, and partial refund states must preserve payment and stock audit history.

### 6.14 Returns, Exchanges, And Cancellations

Return policy requirements:

- Maximum return window is 14 days.
- Customer must contact the site and communicate the return request before sending the item back.
- Buyer pays for return shipment.
- Refunds are issued after return conditions are met.
- Refund timing is usually 5-14 business days and depends on the original payment method.

Return condition requirements:

- Item must be unworn and unused.
- Item must show no signs of wear, body oils, makeup, perfume residue, scratching, or damage.
- Item must be unaltered.
- Item must not have been resized, engraved, or modified by a third-party jeweller after purchase.
- Original diamonds, gemstones, pearls, and other stones must be securely in place and unaltered.
- Original packaging must be returned, including branded jewellery boxes, pouches, presentation materials, and protective outer boxes.
- Certificates and tags must be returned, including GIA, IGI, or diamond grading certificates where relevant.
- Product and security tags must remain fully intact and attached.

Exchange and cancellation rules:

- Products cannot be exchanged except for ring size exchanges.
- Gift orders follow the same return rules as standard orders.
- Gift orders cannot be exchanged except where a ring size exchange is allowed.
- Customers can cancel standard orders before dispatch.
- Customers can cancel made-to-order items after production has started as long as the order has not dispatched.

Open return policy details:

- Whether personalised, engraved, altered, or made-to-order items have restrictions beyond the standard condition requirements.
- Whether ring size exchanges have a separate time limit or fee.

### 6.15 Packaging And Gifting

Packaging requirements:

- Protective jewellery box, pouch, or branded presentation packaging.
- Packaging suitable for bracelets, necklaces, and rings.
- Clean premium presentation aligned with the Ouroboros theme.
- Secure outer shipping packaging.
- Care card or care guidance where appropriate.
- Material or product information card where appropriate.
- Clear checkout indication if gift packaging is included or optional.

Gift requirements:

- Product pages must mention gift-appropriate packaging.
- Checkout should make gift message or gift packaging options easy to select if supported.
- Pricing must not be displayed inside the physical parcel when the order is marked as a gift.
- Gift orders follow the same returns and exchange rules defined above.

### 6.16 Email Requirements

Transactional email templates:

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

Rules:

- Transactional emails must not include marketing content unless the customer has separately opted in.
- Order confirmation must include order number, order summary, total paid in GBP, delivery details, expected dispatch or lead time, and support route.
- Dispatch email must include carrier and tracking number when available.

Marketing preference categories:

- New item drops.
- Collection launches.
- Sale offers.
- Back-in-stock updates where relevant.

Marketing rules:

- Newsletter signup is optional.
- Marketing emails are sent only to customers who opted in or where another lawful basis has been legally approved.
- Customers can unsubscribe.
- Customers can update preferences.
- Consent source and timestamp must be stored.

### 6.17 Contact And Enquiries

Contact options may include:

- Contact form.
- Customer service email address.
- Order enquiry form.
- Product question form.

Contact forms must collect:

- Customer name.
- Email address.
- Enquiry type.
- Message.
- Order number if relevant.

Enquiry types:

- Product question.
- Ring sizing help.
- Order status.
- Shipping question.
- Returns or exchange.
- Made-to-order enquiry.
- General enquiry.

Rules:

- Required fields must be validated.
- Successful submission must show confirmation.
- Customer acknowledgement email should be sent if email service is configured.
- Developer/operator or support recipient must receive the enquiry details.

### 6.18 Content And Policy Pages

Required pages:

- Home.
- Shop all.
- Collections.
- Bracelets.
- Necklaces.
- Rings.
- Product detail page.
- Ring size guide.
- About the brand.
- Contact.
- Shipping information.
- Packaging and gifting information.
- Returns and exchanges.
- Privacy policy.
- Cookie policy.
- Terms and conditions.
- Account.
- Cart.
- Checkout.

Content requirements:

- Product and policy content must support buyer trust and reduce purchase hesitation.
- Shipping, returns, privacy, terms, contact, and gifting information must be accessible before checkout.
- Legal and policy content must be reviewed before launch.
- Product copy should be refined, trustworthy, symbolic, and premium without feeling mass-market, overly gothic, or costume-like.

## 7. Data Model

### 7.1 Product

Fields:

- product_id.
- sku.
- name.
- slug.
- category.
- collection_id.
- material.
- purity_or_fineness.
- finish.
- description.
- symbolic_meaning.
- dimensions.
- weight.
- care_guidance.
- packaging_note.
- returns_note.
- price_gbp.
- tax_included.
- tax_class.
- availability_status.
- low_stock_threshold.
- made_to_order_lead_time.
- seo_title.
- seo_description.
- is_published.
- created_at.
- updated_at.

### 7.2 Variant

Fields:

- variant_id.
- product_id.
- variant_sku.
- option_type.
- option_value.
- price_override_gbp.
- stock_quantity.
- reserved_quantity.
- availability_status.
- made_to_order_allowed.
- made_to_order_capacity_limit.
- lead_time_override.
- is_active.

Examples:

- Ring size: UK L, UK M, UK N.
- Chain length: 16 inch, 18 inch.
- Bracelet size: small, medium, large.

### 7.3 Product Image

Fields:

- image_id.
- product_id.
- variant_id optional.
- image_url.
- alt_text.
- image_type.
- sort_order.
- is_primary.

Image types:

- Main.
- Detail.
- Scale.
- Worn.
- Angle.
- Packaging.

### 7.4 Collection

Fields:

- collection_id.
- name.
- slug.
- description.
- symbolic_theme.
- hero_image.
- seo_title.
- seo_description.
- sort_order.
- is_published.

### 7.5 Customer

Fields:

- customer_id.
- email.
- password_hash.
- first_name.
- last_name.
- phone.
- marketing_status.
- created_at.
- updated_at.
- last_login_at.
- deletion_requested_at.
- deleted_at.

### 7.6 Address

Fields:

- address_id.
- customer_id.
- addressee.
- organization.
- unit_or_flat.
- street_address.
- locality.
- post_town.
- postcode.
- country.
- phone.
- is_default.

Rules:

- post_town must be stored and displayed in ALL CAPS.
- country must be within the supported UK shipping boundary for delivery addresses.

### 7.7 Cart

Fields:

- cart_id.
- customer_id optional.
- session_id optional.
- status.
- active_context.
- reservation_expires_at.
- created_at.
- updated_at.
- expires_at.

### 7.8 Cart Item

Fields:

- cart_item_id.
- cart_id.
- product_id.
- variant_id optional.
- quantity.
- reserved_quantity.
- current_price_gbp.
- added_at.
- updated_at.

### 7.9 Wishlist Item

Fields:

- wishlist_item_id.
- customer_id.
- product_id.
- variant_id optional.
- added_at.

### 7.10 Order

Fields:

- order_id.
- order_number.
- customer_id.
- email.
- status.
- payment_status.
- fulfilment_status.
- subtotal_gbp.
- shipping_gbp.
- tax_gbp.
- total_gbp.
- currency.
- shipping_address_snapshot.
- billing_address_snapshot.
- shipping_method.
- combined_shipping_choice.
- tracking_number.
- carrier.
- gift_message.
- marketing_opt_in_at_checkout.
- created_at.
- updated_at.

### 7.11 Order Item

Fields:

- order_item_id.
- order_id.
- product_id.
- variant_id optional.
- product_name_snapshot.
- variant_label_snapshot.
- sku_snapshot.
- quantity.
- unit_price_gbp.
- line_total_gbp.
- made_to_order_lead_time_snapshot.
- fulfilment_status.

### 7.12 Payment Attempt

Fields:

- payment_attempt_id.
- order_id optional.
- cart_id.
- provider.
- provider_reference.
- payment_method_type.
- status.
- amount_gbp.
- failure_reason.
- created_at.
- updated_at.

### 7.13 Stock Reservation

Fields:

- stock_reservation_id.
- cart_id.
- cart_item_id.
- product_id.
- variant_id optional.
- quantity.
- status.
- reserved_at.
- expires_at.
- released_at.
- committed_at.

### 7.14 Enquiry

Fields:

- enquiry_id.
- name.
- email.
- enquiry_type.
- order_number optional.
- message.
- status.
- created_at.
- updated_at.

### 7.15 Marketing Preference

Fields:

- customer_id or email.
- new_item_drops.
- collection_launches.
- sale_offers.
- back_in_stock_updates.
- consent_source.
- consent_timestamp.
- unsubscribe_timestamp.
- updated_at.

### 7.16 Audit Event

Fields:

- audit_event_id.
- actor_id.
- actor_type.
- entity_type.
- entity_id.
- action.
- before_snapshot.
- after_snapshot.
- created_at.

## 8. Availability And Inventory Rules

Availability statuses:

- In stock: product can be added to cart and purchased.
- Low stock: product can be purchased but should show honest urgency.
- Sold out: product cannot be purchased.
- Coming soon: product cannot be purchased yet, but customers may sign up for updates if enabled.
- Made to order: product can be purchased if lead time, capacity, and production expectations are clearly shown.

Inventory rules:

- Availability is shown on listing pages and product detail pages.
- Inventory is tracked at variant level where variants affect purchase decisions.
- Rings are tracked by UK ring size.
- Necklaces and bracelets are tracked by length or size if those options exist.
- Stock is reserved when an item is added to cart.
- Wishlist items do not reserve stock.
- Cart quantity is limited by available stock.
- Overselling is not allowed for stock-tracked items.
- Made-to-order products have production capacity limits.
- Made-to-order capacity is 1-20 pieces per 3-week period.
- Payment must be prevented if the item is not in stock at the point of payment.
- Low stock thresholds may be fixed globally or product-specific.
- Manual stock adjustments must be auditable.

Open inventory decisions:

- Exact cart reservation duration.
- Exact low-stock thresholds.
- Whether coming soon and sold out products support notification signups at launch.
- Operational method for manual stock adjustment.

## 9. Search, Filtering, Sorting, And Navigation

Search:

- Internal product search is out of scope for the current version.

Filtering requirements:

- Collection filter includes each collection name and shows only products in the selected collection.
- Category filter includes Necklaces, Rings, and Bracelets.
- Material filter supports silver and white gold.
- Availability filter supports all defined availability statuses.
- Ring size filter appears where relevant.
- Filters make it clear when no products match the selected option.
- Filters can be cleared.

Sorting requirements:

- Availability sort is required.
- Price and newest sorting are supported if the required product data exists.
- Infinite scroll is not used.

Navigation requirements:

- Breadcrumb behavior must be defined before build.
- Empty states must route customers back to relevant browsing pages.

## 10. Legal, Privacy, Cookies, Analytics, And Compliance

Launch legal content must include or confirm:

- Legal business name.
- Business trading address or registered address.
- Customer service email address.
- Terms and conditions.
- Privacy policy.
- Cookie policy.
- Returns and cancellation policy.
- Standard cancellation form where required.
- Clear material descriptions for silver and white gold products.
- Hallmarking information for precious metal items where legally required.
- Online Dealer's Notice or equivalent hallmark explanation.
- Marketing consent records and unsubscribe controls.
- Data retention rules for customer, order, enquiry, wishlist, abandoned cart, and marketing data.

Privacy and tracking requirements:

- Define which analytics tools are used.
- Define which advertising pixels or remarketing tools are used, if any.
- Separate strictly necessary cookies from analytics and marketing cookies.
- Require consent for non-essential cookies where applicable.
- Allow cookie preferences to be changed after initial consent where required.
- Define third-party processors handling customer data.
- Define how customers request account deletion or data access.

Compliance note:

- UK ecommerce, data protection, PECR, cookie, returns, cancellation, and precious metal hallmarking requirements must be checked against current UK guidance before launch.

## 11. Accessibility, SEO, And Performance

Accessibility requirements:

- Mobile-first responsive design.
- Keyboard navigation for menus, forms, product options, cart, and checkout.
- Screen reader friendly forms and product options.
- Accessible contrast and focus states.
- Accessible error messages connected to fields.
- Product image alt text.
- No critical information conveyed by color alone.

SEO requirements:

- SEO-friendly product, category, and collection URLs.
- Unique page titles.
- Unique meta descriptions for product and collection pages.
- Product structured data where appropriate.
- Descriptive image alt text.
- Sitemap.
- Robots rules.
- Canonical URLs for filtered listing pages where needed.
- 404 page.

Performance requirements:

- Optimised product images.
- Responsive image sizes.
- Lazy loading for below-the-fold imagery.
- Fast listing filter interactions.
- Checkout loads reliably on mobile connections.
- Non-essential third-party scripts wait for consent where consent is required.
- 500 and maintenance pages exist where relevant.

## 12. Security And Abuse Prevention

Security requirements:

- HTTPS everywhere in production.
- Secure password hashing.
- Secure password reset tokens.
- Secure session cookies.
- Secure session expiry behavior.
- Rate limiting for login, registration, password reset, contact forms, and checkout attempts.
- CSRF protection where relevant.
- Input validation and output escaping.
- Protection against common injection and cross-site scripting risks.
- Developer/operator-only access controls for operational tooling.
- Audit logging for sensitive operational actions.
- Fraud review flow for suspicious orders.
- No raw payment card storage.

## 13. Error And Empty States

Required states:

- Product not found.
- Collection not found.
- No products in category.
- No products match selected filters.
- Cart empty.
- Wishlist empty.
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
- Newsletter signup failed.
- Server error.
- Maintenance mode if needed.

Each state must explain what happened and offer the next useful action.

## 14. Operational Workflows

The current version does not require a separate admin management interface, but it must define reliable developer/operator workflows for:

- Creating and editing products.
- Publishing and archiving products.
- Uploading and reordering product images.
- Managing collections.
- Managing inventory by variant.
- Managing cart reservations and reservation expiry.
- Viewing, searching, and updating orders.
- Issuing refunds.
- Adding tracking numbers.
- Exporting orders.
- Viewing customer enquiries.
- Replying to contact form submissions.
- Exporting marketing subscribers where legally permitted.
- Managing homepage and collection page content.
- Reviewing audit history for stock and order changes.

## 15. Launch Acceptance Criteria

The website is functionally launch-ready when:

- Customers can browse home, shop, category, collection, and product pages.
- Product pages show material, price, availability, size, weight, images, care, packaging, shipping, returns, and symbolic meaning.
- Rings require UK ring size selection before purchase.
- Ring size guidance is easy to access from ring product pages.
- Cart supports add, remove, quantity update, selected variants, subtotal, availability changes, and stock reservations.
- Guest carts do not silently merge into logged-in carts.
- Wishlist and account behavior follow login requirements.
- Sold out and coming soon products cannot be purchased.
- Made-to-order products show lead time and capacity expectations before checkout.
- Customers must sign in or create an account before payment.
- Checkout blocks non-UK delivery addresses.
- Checkout shows product price, free shipping, tax wording, and total in GBP.
- Payments are handled securely through approved payment providers.
- Successful payment creates an order and sends confirmation email.
- Payment failure gives a clear retry path without losing cart contents.
- Mixed in-stock and made-to-order carts communicate shipping choices.
- Contact forms route enquiries with the correct enquiry type.
- Marketing signup is optional and consent is stored.
- Required policy pages are accessible from the footer.
- Developer/operator workflows can manage products, images, variants, stock, reservations, orders, tracking, refunds, enquiries, and content.
- Baseline accessibility, security, privacy, SEO, and performance requirements are met.

## 16. Open Decisions Before Build

The following decisions still need confirmation before the related implementation work begins:

- Exact carrier options.
- Dispatch working days and cut-off times.
- Standard dispatch time for in-stock products.
- Lost parcel, delayed parcel, and damaged parcel handling.
- Whether signature on delivery is required for higher value orders.
- Exact cart reservation duration.
- Low stock thresholds.
- Whether back-in-stock and coming-soon signups are enabled at launch.
- Whether Apple Pay, Google Pay, or other wallet options are enabled through the selected providers.
- How abandoned checkout and session expiry behave.
- Exact order confirmation page and confirmation email copy.
- Who can change each order status and which status changes trigger emails.
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
- Final hallmarking and Online Dealer's Notice implementation.
