# Business Context Spec: Ouroboros Jewellery Online Store

## 1. Business Overview

The business is a personal brand online jewellery store selling high quality silver and white gold jewellery inspired by the Ouroboros. The Ouroboros is an ancient symbol showing a serpent or dragon swallowing its own tail. For this brand, it represents eternity, cyclic renewal, transformation, and the balance between creation and destruction.

The store focuses on a small number of carefully presented collections rather than a large catalogue. Each product should feel intentional, symbolic, premium, and easy to evaluate before purchase.

The store currently ships only within the United Kingdom and sells exclusively in pound sterling.

## 2. Brand Positioning

The brand should appeal to customers who are drawn to symbolic jewellery, ancient motifs, mythology, transformation, renewal, and meaningful personal objects.

The visual and written tone should feel refined, mysterious, elegant, and trustworthy. The site should avoid feeling mass-market, overly gothic, or costume-like. It should present the jewellery as wearable premium pieces with symbolic depth.

Core brand ideas:

- Eternity and continuity
- Cyclic renewal
- Transformation and rebirth
- Balance of creation and destruction
- Personal symbolism
- Premium craftsmanship
- Quiet luxury with mythic influence

## 3. Target Customers

Primary customers are UK-based buyers interested in meaningful, symbolic, and premium jewellery. They may be purchasing for themselves or as a gift.

Likely customer motivations:

- They want jewellery with deeper meaning.
- They are interested in ancient symbols, mythology, alchemy, spirituality, or transformation.
- They prefer silver or white gold pieces over yellow gold.
- They want a distinctive piece that is elegant enough for regular wear.
- They need clear product information before buying online.
- They value secure checkout, transparent shipping, and reliable communication.

## 4. Product Range

The store sells three main product categories:

- Bracelets
- Necklaces
- Rings

Products are made from silver and white gold. Each item belongs to a limited set of Ouroboros-inspired collections.

Product collections may be organized by symbolic interpretation, form, or finish. Example collection themes:

- Eternal Return
- Renewal
- Devourer
- Circle of Becoming
- Silver Serpent
- White Gold Ouroboros

## 5. Product Detail Requirements

Each product page must give buyers enough information to make a confident purchase decision.

Every product should display:

- Product name
- SKU or product reference where appropriate
- Product category
- Collection name
- Material used, such as sterling silver or white gold
- Clear product description
- Symbolic inspiration or meaning
- Size information
- Weight
- High quality product images
- Availability status
- Price in GBP
- Confirmation that displayed prices include VAT or other applicable taxes
- UK shipping information, including free shipping
- Packaging and gifting information
- Care guidance
- Returns or exchange information where relevant

Product availability statuses:

- In stock
- Low stock
- Sold out
- Coming soon
- Made to order

Product images should include:

- Main product image
- Close-up detail image
- Scale or worn image where possible
- Multiple angles where relevant
- Clear view of clasps, chains, bands, stones, engraving, or texture if present

## 6. Ring Sizing Requirements

Ring products must include a size selection option before purchase.

Ring product pages should include:

- Available ring sizes
- Current stock by size where possible
- Made-to-order handling where relevant
- Ring size guidance chart
- Clear guidance for customers who are unsure of their size

The ring size guide should be easy to access from ring product pages and should include UK ring sizing as the primary format. If international sizes are shown, UK sizing should still remain the default because the store currently serves UK customers.

## 7. Account Requirements

Customers should be able to create a secure account.

Account features:

- Register with email and password
- Log in and log out securely
- Reset forgotten password
- View and update account details
- Save delivery addresses
- View order history
- Manage wishlist items
- Manage newsletter preferences
- Save cart contents between sessions
- Delete account, with a clear warning that saved account information will be lost

Security expectations:

- Passwords must be securely hashed.
- Authentication sessions must be protected.
- Sensitive account actions should require confirmation.
- Customer data must be handled in line with UK data protection expectations.

## 8. Shopping Cart Requirements

Customers should be able to add available products to a shopping cart.

Cart features:

- Add item to cart
- Remove item from cart
- Update quantity where applicable
- Add multiple quantities of the same item where stock allows
- Show selected ring size where applicable
- Show product availability changes
- Show item price in GBP
- Show subtotal
- Show shipping estimate or shipping note
- Persist cart for logged-in users
- Allow guest browsing and cart building before account creation

The cart should prevent checkout for sold out and coming soon products. Made-to-order products should clearly communicate lead times before checkout.

Cart quantities must be limited to the amount available in stock. If a cart item becomes sold out, the cart should show a sold out notice and prevent the customer from proceeding to payment until the sold out item is removed. If a product price changes, the current price should be reflected in the cart and during payment.

If a cart contains both in-stock items and made-to-order items, the customer must be warned that shipping the order together means waiting until the made-to-order item is crafted and ready. If the customer accepts combined shipping, they should receive an email notification when the made-to-order item is ready to ship. If the customer declines combined shipping, eligible in-stock items may be shipped separately, and the customer should still receive a notification when the made-to-order item is ready.

## 9. Wishlist Requirements

Customers should be able to save items to a wishlist when logged in.

Wishlist features:

- Add product to wishlist
- Remove product from wishlist
- View saved products in account area
- Show saved wishlist items across devices when the customer logs in
- Prevent duplicate wishlist items
- Move wishlist item to cart when available
- Show availability status
- Show price in GBP

If a customer is not logged in, they should be prompted to create an account or sign in before saving wishlist items.

Wishlist items do not reserve stock. If a product price changes, the current price should be reflected in the wishlist.

## 10. Email Marketing Requirements

Customers should be able to opt in to email updates.

Email preferences:

- New item drops
- Collection launches
- Sale offers
- Back-in-stock updates where relevant

Newsletter signup must be optional. Customers should be able to unsubscribe or update preferences. Marketing emails should only be sent to customers who have opted in.

## 11. Contact Requirements

The site should make it easy for customers to contact the brand when needed.

Contact options may include:

- Contact form
- Customer service email address
- Order enquiry form
- Product question form

Contact forms should collect:

- Customer name
- Email address
- Enquiry type
- Message
- Order number, if relevant

Common enquiry types:

- Product question
- Ring sizing help
- Order status
- Shipping question
- Returns or exchange
- Made-to-order enquiry
- General enquiry

## 12. Checkout And Payment Requirements

The checkout flow should be simple, secure, and clear.

Checkout should include:

- Cart review
- Account sign-in or account creation before payment
- Customer contact details
- UK shipping address
- Shipping method or shipping confirmation
- Payment step
- Order confirmation
- Confirmation email

Account creation is required to purchase. Guest checkout must not allow payment or order placement without a customer account.

Payment requirements:

- Prices displayed in pound sterling
- Displayed prices include VAT or other applicable taxes
- Free shipping shown clearly before payment
- Secure payment processing through trusted payment providers
- Supported payment methods include credit card, digital wallet, and bank transfer
- Payment is made as a single upfront payment only, with no instalments or split payments
- Payment providers will include Stripe, PayPal, Square, and Airwallex
- No raw payment card details stored by the store
- Clear payment confirmation and error handling

Payment must fail or be prevented when:

- All required payment information has not been provided.
- The payment method used does not hold the required amount of currency or available funds.
- The item is not in stock.

Billing address may differ from delivery address.

UK address collection and validation should support:

- Addressee line, meaning the recipient's name
- Organization or department, if applicable
- Unit, apartment, or flat number, if applicable
- Building or house number and street
- Locality or dependent locality, if applicable
- POST TOWN or city, which must be stored and displayed in ALL CAPS
- Postcode, such as EH14 5AN

The checkout should clearly show:

- Product price
- Quantity
- Ring size or product option
- Shipping cost, shown as free where applicable
- Taxes where applicable
- Total order cost in GBP

## 13. Shipping Context

The store currently ships inside the UK only. UK-only shipping includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Channel Islands, Isle of Man, and BFPO addresses.

Shipping information should be visible before checkout and repeated during checkout.

Shipping details should include:

- UK-only shipping notice
- Estimated dispatch time
- Estimated delivery time
- Free shipping notice
- Made-to-order lead times where relevant
- Delivery restrictions
- Tracked delivery availability
- Carrier service delivery for enhanced security

If a customer enters a non-UK shipping address, checkout should prevent completion and explain that the store currently ships only within the UK.

All deliveries should be shipped through carrier services and tracked.

## 14. Packaging And Gifting Requirements

Jewellery packaging should be appropriate for gifting and should support the nature of the brand.

Packaging should feel refined, secure, and presentation-ready. Customers should be confident that an item can be sent as a gift without needing additional wrapping.

Packaging requirements:

- Protective jewellery box, pouch, or branded presentation packaging
- Packaging suitable for bracelets, necklaces, and rings
- Clean and premium presentation aligned with the Ouroboros theme
- Secure outer shipping packaging to protect the item in transit
- Care card or care guidance included where appropriate
- Material or product information card where appropriate
- Option to add a gift message if supported
- Clear indication during checkout if gift packaging is included or optional

Gift-related expectations:

- Product pages should mention that the item arrives in gift-appropriate packaging.
- Checkout should make any gift message or gift packaging option easy to select.
- Pricing should not be displayed inside the physical parcel when the order is marked as a gift.
- Packaging should protect delicate jewellery while still feeling suitable for special occasions.
- Gift orders follow the same return rules as standard orders and cannot be exchanged, except where a ring size exchange is allowed.

## 15. Inventory And Availability Rules

Availability should be shown clearly on product listing pages and product detail pages.

Availability behavior:

- In stock: product can be added to cart and purchased.
- Low stock: product can be purchased but should show urgency honestly.
- Sold out: product cannot be purchased.
- Coming soon: product cannot be purchased yet, but customers may be able to sign up for updates.
- Made to order: product can be purchased if lead time and production expectations are clearly shown.

Inventory should account for product variants, especially ring sizes.

Made-to-order products should show an average lead time of 2-10 weeks.

## 16. Content Requirements

The site should include enough information to support buyer trust and reduce purchase hesitation.

Recommended pages:

- Home
- Shop all
- Collections
- Bracelets
- Necklaces
- Rings
- Product detail page
- Ring size guide
- About the brand
- Contact
- Shipping information
- Packaging and gifting information
- Returns and exchanges
- Privacy policy
- Terms and conditions
- Account
- Cart
- Checkout

## 17. Trust And Compliance Context

The store should communicate trust clearly because it sells high value personal items online.

Trust signals:

- Clear product images
- Gift-appropriate jewellery packaging
- Accurate material information
- Transparent pricing in GBP
- Clear UK shipping policy
- Secure account creation
- Secure checkout
- Clear returns and exchanges information
- Contact options
- Privacy and marketing consent controls

Operational expectations:

- Handle customer data responsibly.
- Collect marketing consent explicitly.
- Use secure payment processing.
- Avoid misleading availability or scarcity messaging.
- Make UK-only shipping clear before checkout.

## 18. User Experience Goals

The customer experience should be simple, polished, and easy to navigate.

Primary user goals:

- Discover Ouroboros-inspired jewellery
- Understand the meaning and material of each piece
- View clear product images
- Choose the correct ring size
- Understand how the jewellery is packaged for gifting
- Save items to wishlist
- Add items to cart
- Create a secure account before purchasing
- Opt in to email updates if interested
- Contact the brand when needed
- Complete a secure UK checkout in GBP

The site should prioritize clarity over decoration. The Ouroboros theme should be visible through product imagery, collection names, copy, and refined design choices, while product information and checkout usability remain easy to scan.

## 19. Business Success Criteria

The store succeeds if customers can confidently understand the products, trust the brand, and complete a purchase without confusion.

Key success criteria:

- Customers understand the Ouroboros theme and brand meaning.
- Product pages provide all information needed for purchase decisions.
- Customers understand that jewellery packaging is suitable for gifting.
- Ring customers can choose a size with guidance.
- Customers can create secure accounts before purchasing.
- Wishlist and cart behavior is reliable.
- Email opt-in is clear and optional.
- UK-only shipping is clearly communicated.
- Checkout is secure, simple, and priced in GBP.
- Customers can contact the brand for support.

## 20. Current Scope

In scope:

- UK-only ecommerce store
- Custom ecommerce platform
- Local, staging, and production environments
- GBP pricing
- VAT-registered pricing with displayed prices including VAT or other applicable taxes
- Free UK shipping
- Silver and white gold jewellery
- Bracelets, necklaces, and rings
- Product listings and product detail pages
- Collection and category filtering
- Product availability statuses
- Ring sizing and size guide
- Gift-appropriate jewellery packaging
- Secure customer accounts
- Shopping cart
- Wishlist
- Email marketing opt-in
- Contact support
- Secure checkout and shipping flow
- Developer-managed product, order, and operational data

Out of scope for the current version:

- International shipping
- Non-GBP currencies
- Internal product search engine
- Infinite scroll
- Admin management interface unless added later
- Marketplace seller accounts
- Large multi-brand catalogue
- Physical store pickup unless added later
- Custom design studio unless added later

## 21. Grey Zones To Resolve Before Build

The spec defines the brand, core ecommerce journey, product requirements, account expectations, wishlist, cart, and UK checkout well. The areas below are not yet fully defined and should be clarified before implementation so the site can be built consistently and operated after launch.

### 21.1 Platform And Source Of Truth

The store will use a custom ecommerce platform.

Operational ownership:

- Product, inventory, order, refund, customer enquiry, and email preference management will be handled by the developer/operator.
- A separate admin management interface is not required for the current version.
- Content such as product descriptions, collection pages, and operational configuration can be managed by the developer/operator rather than through a customer-facing admin system.
- The project requires local, staging, and production environments.

The implementation should still define a reliable system of record for products, inventory, customers, orders, payments, and marketing consent.

### 21.2 Product And Variant Data Model

The product requirements are clear at page level, but the structured product data model needs more detail.

Each product should define:

- Product ID and SKU
- Variant SKU where relevant
- URL slug
- Category
- Collection
- Material and purity or fineness
- Finish
- Dimensions
- Weight
- Ring size, chain length, bracelet size, clasp type, engraving, stones, or texture where relevant
- Product image alt text
- Stock quantity per product or per variant
- Availability status
- Made-to-order lead time where relevant
- SEO title and meta description

Inventory should be tracked at variant level where variants affect purchase decisions. Rings should be tracked by UK ring size. Necklaces and bracelets should be tracked by length or size if those options exist.

### 21.3 Pricing, Tax, And Promotions

The store sells in GBP only. The business is VAT registered, and displayed prices include VAT or other applicable taxes.

Pricing and tax rules:

- Shipping is free for UK orders.
- Product prices, order totals, and payment confirmations should clearly show GBP pricing.
- Tax display should make it clear that prices include VAT or other applicable taxes.

Clarify before build:

- Whether shipping has any tax reporting implications even when charged at zero cost
- Whether discount codes, sale prices, bundles, gift cards, or store credit are in scope
- Whether products can have compare-at prices or launch pricing
- How refunds, partial refunds, shipping refunds, and cancelled orders should be handled

### 21.4 Checkout Scope And Payment Behavior

Checkout uses account-based purchasing and single-payment orders only.

Defined checkout decisions:

- Supported payment methods include credit card, digital wallet, and bank transfer.
- Supported payment providers will include Stripe, PayPal, Square, and Airwallex.
- Payment can only be completed as a single upfront payment, with no instalments or split payments.
- Billing address can differ from delivery address.
- Checkout must validate required address and payment fields before payment is attempted.
- Payment must fail or be prevented if all required payment information has not been provided, if the payment method used does not hold the required amount of currency or available funds, or if the item is not in stock.

UK address fields:

- Addressee line, meaning recipient's name
- Organization or department, if applicable
- Unit, apartment, or flat number, if applicable
- Building or house number and street
- Locality or dependent locality, if applicable
- POST TOWN or city, stored and displayed in ALL CAPS
- Postcode, such as EH14 5AN

Clarify before build:

- How the required account sign-in or account creation step appears in the checkout flow
- Whether Apple Pay, Google Pay, or other wallet options are enabled through the selected provider
- How abandoned checkout and session expiry should behave
- What exact information appears on the order confirmation page and confirmation email

### 21.5 Order Lifecycle

The site needs a clear order state model.

Recommended order statuses:

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

Clarify who can change each status, which changes trigger emails, and what the customer can see in their account order history.

### 21.6 Transactional Email Requirements

Marketing email is covered, but operational email needs more detail.

Define email templates for:

- Account verification if required
- Password reset
- Order confirmation
- Payment failed
- Order dispatched
- Tracking information
- Order cancelled
- Refund issued
- Return or exchange update
- Back-in-stock notification
- Contact form acknowledgement
- Newsletter subscription confirmation if double opt-in is used

Transactional emails should not include marketing content unless the customer has separately opted in to marketing.

### 21.7 Shipping And Fulfilment Detail

UK-only shipping includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Channel Islands, Isle of Man, and BFPO addresses.

Shipping and fulfilment rules:

- Shipping is free for UK orders.
- Orders should be shipped via carrier services for enhanced security.
- All delivery should be tracked.
- Made-to-order items have an average lead time of 2-10 weeks.
- Mixed carts containing in-stock and made-to-order items must warn customers before checkout that combined shipping will wait until the made-to-order item is crafted.
- If the customer accepts combined shipping, the order ships together when the made-to-order item is ready, and the customer receives an email notification when it is ready to ship.
- If the customer declines combined shipping, in-stock items may ship separately, and the customer still receives an email notification when the made-to-order item is ready.

Clarify before build:

- Exact carrier options
- Dispatch working days and cut-off times
- Standard dispatch time for in-stock products
- Lost parcel, delayed parcel, and damaged parcel handling
- Whether signature on delivery is required for higher value orders

### 21.8 Returns, Exchanges, And Cancellations

Returns have a maximum 14-day return window.

Return process:

- The customer must contact the site first and communicate the return request before sending the item back.
- The buyer pays for return shipment.
- Refunds are issued after the return conditions are met.
- Refund timing is usually 5-14 business days and depends on the original payment method.

Return condition requirements:

- The item must be unworn and unused, with no signs of wear, body oils, makeup, perfume residue, scratching, or damage.
- The item must be unaltered and must not have been resized, engraved, or modified by a third-party jeweller after purchase.
- All original diamonds, gemstones, pearls, and other stones must be securely in place and unaltered.
- Original packaging must be returned, including branded jewellery boxes, pouches, presentation materials, and protective outer boxes.
- Certificates and tags must be returned with the item, including GIA, IGI, or diamond grading certificates where relevant.
- Product and security tags must remain fully intact and attached.

Exchange and cancellation rules:

- Products cannot be exchanged except for ring size exchanges.
- Gift orders can be returned under the same rules as standard orders and cannot be exchanged, except where a ring size exchange is allowed.
- Customers can cancel standard orders before dispatch.
- Customers can cancel made-to-order items after production has started as long as the order has not dispatched.

Clarify before build:

- Whether personalised, engraved, altered, or made-to-order items have any return restrictions beyond the standard condition requirements
- Whether ring size exchanges have a separate time limit or fee

### 21.9 UK Legal And Compliance Content

The site sells precious metal jewellery online, so legal and compliance content should be treated as a launch requirement.

Add or confirm:

- Legal business name
- Business trading address or registered address
- Customer service email address
- Terms and conditions
- Privacy policy
- Cookie policy
- Returns and cancellation policy
- Standard cancellation form where required
- Clear material descriptions for silver and white gold products
- Hallmarking information for precious metal items where legally required
- Online Dealer's Notice or equivalent hallmark explanation
- Marketing consent records and unsubscribe controls
- Data retention rules for customer, order, enquiry, and marketing data

Compliance details should be checked against current UK guidance before launch.

### 21.10 Privacy, Cookies, Analytics, And Tracking

The account and marketing requirements mention data protection, but tracking and analytics are not defined.

Clarify:

- Which analytics tools are used
- Which advertising pixels or remarketing tools are used, if any
- Which cookies are strictly necessary
- Which cookies require consent
- Whether cookie preferences can be changed after initial consent
- Which third-party processors handle customer data
- Data retention periods for accounts, orders, wishlists, abandoned carts, enquiries, and marketing consent
- How customers can request account deletion or data access

### 21.11 Search, Filtering, Sorting, And Navigation

The site does not include an internal product search engine. Product discovery should rely on filters and clear navigation.

Filtering requirements:

- Collection filter: includes each collection name and shows only the items belonging to the selected collection.
- Category filter: includes Necklaces, Rings, and Bracelets.
- Necklace category filter: shows all necklaces in the store.
- Ring category filter: shows all rings in the store.
- Bracelet category filter: shows all bracelets in the store.
- Filters should make it clear when no products match the selected option.
- Infinite scroll is not required and should not be used.

Clarify before build:

- Whether sort options such as newest, price low to high, price high to low, collection, and availability are required
- Breadcrumb behavior
- Empty state copy when no products match filters

### 21.12 Account, Cart, And Wishlist Edge Cases

Defined account, cart, and wishlist behavior:

- Guest carts do not merge with the logged-in customer cart.
- Wishlist items are saved to the customer account and should appear across devices when the customer logs in.
- Duplicate wishlist items must be prevented to keep wishlists organised.
- Customers can add multiple quantities of the same item to their cart, limited by available stock.
- If a cart item becomes sold out, the cart must show a sold out notice and prevent payment until the item is removed.
- If the price of an item changes, the current price must update in the wishlist, cart, and payment step.
- Saved addresses require validation.
- Customers can delete their account and should be warned that deleting the account removes the information saved in it, including saved addresses, wishlist items, saved cart contents, and account preferences.

### 21.13 Inventory Reservation Rules

Inventory behavior is important for limited products.

Defined inventory reservation rules:

- Stock is reserved when an item is added to cart.
- Stock is not reserved when an item is added to wishlist.
- Cart quantity is limited by available stock.
- Overselling is not allowed for stock-tracked items.
- Made-to-order items have production capacity limits.
- Made-to-order capacity is 1-20 pieces per 3-week period.
- Payment must be prevented if the item is not in stock at the point of payment.

Clarify before build:

- How long cart inventory reservations last
- Whether low stock thresholds are fixed or product-specific
- Whether coming soon and sold out products support back-in-stock signups
- Whether the developer/operator can manually adjust stock and through what operational tool

### 21.14 Admin And Support Operations

The current version does not require a dedicated admin management interface. Product, content, inventory, order, refund, fulfilment, customer enquiry, and email preference operations will be handled by the developer/operator.

Define the developer/operator workflow for:

- Creating and editing products
- Uploading and reordering product images
- Managing collections
- Managing inventory by variant
- Viewing, searching, and updating orders
- Issuing refunds
- Adding tracking numbers
- Exporting orders
- Viewing customer enquiries
- Replying to contact form submissions
- Exporting marketing subscribers
- Managing homepage and collection page content
- Reviewing audit history for stock and order changes

### 21.15 Content And Asset Requirements

The spec calls for high quality images, but asset requirements should be more specific.

Clarify:

- Required image aspect ratios and minimum resolutions
- Photography style for product-only, worn, detail, and packaging images
- Whether model releases are required for worn imagery
- Whether every product must have the same minimum image set
- Final product copy ownership and approval process
- Collection story copy
- Homepage merchandising order
- Accessibility-focused alt text
- Empty, loading, error, and confirmation state copy

### 21.16 Accessibility, SEO, And Performance

These are not yet specified but are important for a polished ecommerce site.

Add expectations for:

- Mobile-first responsive design
- Keyboard navigation
- Screen reader friendly forms and product options
- Accessible contrast and focus states
- Accessible error messages
- SEO-friendly product and collection URLs
- Product structured data where appropriate
- Optimised images
- Fast page load on mobile connections
- Sitemap and robots rules
- 404, 500, and maintenance pages

### 21.17 Security And Abuse Prevention

The spec mentions secure accounts, but implementation-level security expectations should be clearer.

Add requirements for:

- HTTPS everywhere
- Secure password reset tokens
- Rate limiting for login, registration, password reset, contact forms, and checkout attempts
- CSRF protection where relevant
- Protection against common injection and cross-site scripting risks
- Secure session expiry behavior
- Developer/operator-only access controls for operational tooling
- Audit logging for sensitive operational actions
- Fraud review flow for suspicious orders
- No storage of raw card details

### 21.18 MVP Versus Later Features

The current scope is broad for a first ecommerce release. Define what must exist at launch and what can be launched later.

Recommended launch-critical features:

- Product listing pages
- Product detail pages
- Variant selection
- Ring size guide
- Cart
- UK checkout
- Secure payment
- Order confirmation email
- Shipping information
- Returns and cancellation information
- Privacy policy
- Terms and conditions
- Contact page
- Developer-managed operational method for managing products, orders, and inventory

Potential later features if launch needs to be smaller:

- Wishlist
- Full customer account area
- Saved addresses
- Newsletter preference centre
- Back-in-stock notifications
- Advanced filtering and sorting
- Discount codes
- Gift messages
- Analytics dashboards
