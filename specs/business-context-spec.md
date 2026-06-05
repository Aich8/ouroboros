# Business Context Spec: Ouroboros Jewellery Online Store

## 1. Business Overview

The business is a personal brand online jewellery store selling high quality silver and white gold jewellery inspired by the Ouroboros. The Ouroboros is an ancient symbol showing a serpent or dragon swallowing its own tail. For this brand, it represents eternity, cyclic renewal, transformation, and the balance between creation and destruction.

The store focuses on a small number of carefully presented collections rather than a large catalogue. Each product should feel intentional, symbolic, premium, and easy to evaluate before purchase.

The store currently ships only within the United Kingdom and sells exclusively in pound sterling.

The store will use a custom ecommerce storefront.

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

Product and variant data requirements:

- Each product should define a product ID, SKU, URL slug, category, collection, material and purity or fineness, finish, dimensions, weight, availability status, made-to-order lead time where relevant, SEO title, and meta description.
- Products should define stock quantity directly when the product has no purchase-relevant variants.
- Products with variants should define variant records with variant SKU, option type, option value, stock quantity, availability status, and made-to-order lead time where relevant.
- Variant options may include ring size, chain length, bracelet size, clasp type, engraving, stones, texture, or other product-specific choices that affect purchase decisions.
- Inventory should be tracked at variant level where variants affect purchase decisions.
- Rings should be tracked by UK ring size.
- Necklaces and bracelets should be tracked by length or size if those options exist.
- Product images should include descriptive alt text and should be connected to the relevant product or variant where needed.

## 5. Product Detail Requirements

Each product page must give buyers enough information to make a confident purchase decision.

Every product should display:

- Product name
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
- UK shipping information
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

Product imagery should use clean studio product shots and packshots, with products shot against a pure black background using white lighting.

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
- Show selected ring size where applicable
- Show product availability changes
- Show item price in GBP
- Show subtotal
- Show shipping estimate or shipping note
- Persist cart for logged-in users
- Allow guest browsing and cart building before account creation

The cart should prevent checkout for sold out and coming soon products. Made-to-order products should clearly communicate lead times before checkout.

## 9. Wishlist Requirements

Customers should be able to save items to a wishlist when logged in.

Wishlist features:

- Add product to wishlist
- Remove product from wishlist
- View saved products in account area
- Move wishlist item to cart when available
- Show availability status
- Show price in GBP

If a customer is not logged in, they should be prompted to create an account or sign in before saving wishlist items.

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
- Secure payment processing through a trusted payment provider
- No raw payment card details stored by the store
- Clear payment confirmation and error handling

The checkout should clearly show:

- Product price
- Quantity
- Ring size or product option
- Shipping cost
- Taxes where applicable
- Total order cost in GBP

## 13. Shipping Context

The store currently ships inside the UK only.

Shipping information should be visible before checkout and repeated during checkout.

Shipping details should include:

- UK-only shipping notice
- Estimated dispatch time
- Estimated delivery time
- Shipping cost or free shipping threshold if used
- Made-to-order lead times where relevant
- Delivery restrictions
- Tracking availability

Resolved shipping and fulfilment rules:

- UK-only shipping includes England, Scotland, Wales, Northern Ireland, Highlands and Islands, Isle of Man, and BFPO addresses.
- Carrier service options should support secure jewellery delivery.
- Delivery is tracked, and tracking progress should be visible in the customer's account.
- In-stock products should usually dispatch within 1-3 business days.
- Made-to-order products have a 2-8 week lead time, and the buyer should be notified by email.
- If an order contains both in-stock and made-to-order items, checkout should let the buyer choose whether to buy available items separately or wait for the made-to-order item so everything can be shipped together.
- Lost, delayed, or damaged parcel cases should be handled through customer service. The customer should provide proof through customer service, and refunds should require developer approval before being issued.

If a customer enters a non-UK shipping address, checkout should prevent completion and explain that the store currently ships only within the UK.

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

## 15. Inventory And Availability Rules

Availability should be shown clearly on product listing pages and product detail pages.

Availability behavior:

- In stock: product can be added to cart and purchased.
- Low stock: product can be purchased but should show urgency honestly.
- Sold out: product cannot be purchased.
- Coming soon: product cannot be purchased yet, but customers may be able to sign up for updates.
- Made to order: product can be purchased if lead time and production expectations are clearly shown.

Inventory should account for product variants, especially ring sizes.

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

Content and operational management expectations:

- Product catalogue content and product imagery will be managed by the developer.
- Product descriptions, collection pages, and other site content will mostly be edited by the developer.
- Products, images, inventory, orders, refunds, customer enquiries, email preferences, and site content will be managed by the developer.

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

- Custom ecommerce storefront
- UK-only ecommerce store
- GBP pricing
- Silver and white gold jewellery
- Bracelets, necklaces, and rings
- Product listings and product detail pages
- Product availability statuses
- Ring sizing and size guide
- Gift-appropriate jewellery packaging
- Secure customer accounts
- Shopping cart
- Wishlist
- Email marketing opt-in
- Contact support
- Secure checkout and shipping flow
- Developer-managed product, content, inventory, order, refund, enquiry, and email preference operations

Out of scope for the current version:

- International shipping
- Non-GBP currencies
- Marketplace seller accounts
- Large multi-brand catalogue
- Physical store pickup unless added later
- Custom design studio unless added later

## 21. Grey Zones To Resolve Before Build

The spec defines the brand, core ecommerce journey, product requirements, account expectations, wishlist, cart, and UK checkout well. The areas below are not yet fully defined and should be clarified before implementation so the site can be built consistently and operated after launch.

### 21.1 Systems Of Record And Environments

Clarify:

- The system of record for inventory, customers, orders, payments, and marketing consent
- Whether the site needs local, staging, and production environments

### 21.2 Pricing, Tax, And Promotions

The spec confirms GBP pricing, but commercial pricing rules need to be made explicit.

Clarify:

- How refunds, partial refunds, shipping refunds, and cancelled orders should be handled

### 21.3 Checkout Scope And Payment Behavior

Checkout is defined at a high level, but several functional decisions remain open.

Clarify:

- Which payment provider will be used
- How payment failures, abandoned checkout, stock changes during checkout, and session expiry should behave
- What exact information appears on the order confirmation page and confirmation email

### 21.4 Order Lifecycle

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

### 21.5 Transactional Email Requirements

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

### 21.6 Returns, Exchanges, And Cancellations

Returns are referenced, but the operational policy needs to be detailed.

Clarify:

- Return window
- Exchange window
- Whether ring size exchanges are supported
- Who pays return postage
- Refund timing
- Condition requirements for returned jewellery
- Whether worn, damaged, altered, engraved, personalised, or made-to-order items are handled differently
- Whether customers can cancel before dispatch
- Whether customers can cancel made-to-order items after production has started
- Whether gift orders can be returned or exchanged by the recipient

### 21.7 UK Legal And Compliance Content

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

### 21.8 Privacy, Cookies, Analytics, And Tracking

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

### 21.9 Search, Filtering, Sorting, And Navigation

The page list is clear, but product discovery behavior needs to be defined.

Clarify:

- Whether the site has search
- Searchable fields such as product name, collection, category, material, and symbolic meaning
- Filters for category, collection, material, price, availability, ring size, finish, and gift suitability
- Sort options such as newest, price low to high, price high to low, collection, and availability
- Product listing pagination or infinite scroll
- Breadcrumb behavior
- Empty state behavior when no products match filters

### 21.10 Account, Cart, And Wishlist Edge Cases

The core features are defined, but edge cases should be specified.

Clarify:

- Whether carts persist for guest users
- How guest carts merge after login
- Whether wishlist items can be saved across devices
- Whether duplicate wishlist items are prevented
- Whether customers can buy multiple quantities of the same item
- Quantity limits for low-stock or one-of-a-kind products
- What happens when a saved cart item becomes sold out
- What happens when a saved wishlist item changes price
- Whether customers can delete their account
- Whether saved addresses require validation

### 21.11 Inventory Reservation Rules

Inventory behavior is important for limited products.

Clarify:

- Whether stock is reserved when an item is added to cart or only after payment
- How long checkout inventory reservations last, if used
- Whether low stock thresholds are fixed or product-specific
- Whether overselling is ever allowed
- Whether made-to-order products have production capacity limits
- Whether coming soon and sold out products support back-in-stock signups
- Whether admin users can manually adjust stock

### 21.12 Admin And Support Operations

The customer-facing site is described, but internal operations are not.

Clarify whether admins need to:

- Create and edit products
- Upload and reorder product images
- Manage collections
- Manage inventory by variant
- View, search, and update orders
- Issue refunds
- Add tracking numbers
- Export orders
- View customer enquiries
- Reply to contact form submissions
- Export marketing subscribers
- Manage homepage and collection page content
- See audit history for stock and order changes

### 21.13 Content And Asset Requirements

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

### 21.14 Accessibility, SEO, And Performance

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

### 21.15 Security And Abuse Prevention

The spec mentions secure accounts, but implementation-level security expectations should be clearer.

Add requirements for:

- HTTPS everywhere
- Secure password reset tokens
- Rate limiting for login, registration, password reset, contact forms, and checkout attempts
- CSRF protection where relevant
- Protection against common injection and cross-site scripting risks
- Secure session expiry behavior
- Admin-only access controls
- Audit logging for sensitive admin actions
- Fraud review flow for suspicious orders
- No storage of raw card details

### 21.16 MVP Versus Later Features

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
- Basic admin or operational method for managing products, orders, and inventory

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
