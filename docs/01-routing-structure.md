# Routing Structure & Navigation Flow

## Next.js App Router Structure

/src/app
├── layout.tsx                 # Root layout (cart provider, toast notifications)
├── page.tsx                   # Home page (redirect to catalog)
├── loading.tsx                # Global loading UI
├── error.tsx                  # Global error boundary
├── not-found.tsx              # 404 page
│
├── /catalog
│   ├── page.tsx               # Product catalog page
│   ├── loading.tsx            # Catalog loading skeleton
│   └── /components
│       ├── ProductGrid.tsx    # Grid of products
│       ├── ProductCard.tsx    # Individual product card
│       ├── CustomProductForm.tsx # Custom product form
│       └── CartSidebar.tsx    # Sliding cart sidebar
│
├── /checkout
│   ├── layout.tsx             # Checkout layout with progress steps
│   ├── page.tsx               # Main checkout page
│   ├── loading.tsx            # Checkout loading state
│   └── /components
│       ├── CheckoutProgress.tsx # Step indicator
│       ├── ContactForm.tsx    # Email & newsletter signup
│       ├── AddressForm.tsx    # Shipping address form
│       ├── ExpressCheckout.tsx # Express payment buttons
│       ├── CartSummary.tsx    # Order summary
│       ├── PaymentConfirmation.tsx # Final confirmation
│       └── CostCalculator.tsx # Real-time cost calculation
│
├── /confirmation
│   ├── page.tsx               # Order confirmation page
│   ├── /[orderId]
│   │   └── page.tsx           # Specific order details
│   └── /components
│       ├── OrderSummary.tsx   # Order details display
│       ├── ShippingLabel.tsx  # Shipping label component
│       └── PrintManager.tsx   # Printer integration
│
└── /api
├── /zonos
│   ├── calculate/route.ts # Calculate landed cost
│   ├── order/route.ts     # Create Zonos order
│   └── shipment/route.ts  # Create shipment & label
├── /google
│   └── places/route.ts    # Google Places proxy
└── /print
└── label/route.ts     # Print shipping label

## User Journey Flow

### 1. Product Catalog Page (`/catalog`)
- Display 3 Zonos products + custom product option
- Add items to cart with quantity controls
- Cart sidebar opens automatically when items added
- "Continue Shopping" keeps sidebar open
- "Checkout" button navigates to checkout

### 2. Checkout Page (`/checkout`)
- Progress indicator shows current step
- Contact information form (email, newsletter signup)
- Shipping address with Google autocomplete
- Real-time cost calculations when address complete
- Express checkout button placeholders
- Cart summary with totals
- Final confirmation prompt

### 3. Order Confirmation (`/confirmation`)
- Order details and summary
- Zonos order creation
- Shipping label generation
- Print shipping label option
- Order tracking information
