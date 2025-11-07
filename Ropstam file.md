SHOPIFY CUSTOM CURTAIN PRICING THEME

A Shopify theme modification that allows dynamic width-based pricing for curtain products
using metafields instead of traditional variant pricing.

LIVE DEMO
---------
https://ropstam-test-sadiq.myshopify.com/products/outdoor-curtains
pass: ropstam-test

FEATURES
--------
- Width selection automatically calculates required fabric panels (hidden from customers)
- Dynamic pricing from metafields
- Real-time price updates without page reload
- Cart shows Width and Drop only (hides technical "Fabric Panels")


Setup
------------

Step 1: Create Metafields

Metafield 1: Width to Panel Map
  Namespace.Key: custom.width_to_panel_map
  Type: JSON
  Example:
  [
    {"width_label": "Up to 1400mm", "panels_required": 1},
    {"width_label": "1401mm - 2800mm", "panels_required": 2},
    {"width_label": "2801mm - 4200mm", "panels_required": 3},
    {"width_label": "4201mm - 5600mm", "panels_required": 4}
  ]

Metafield 2: Curtain Pricing
  Namespace.Key: custom.curtain_pricing
  Type: JSON
  Example:
  {
    "1_180cm": 10000,
    "2_210cm": 22000,
    "3_240cm": 35000,
    "4_210cm": 38000
  }
  Note: Prices in cents (22000 = Rs.220.00)


Step 2: Configure Product
  - Create variants with two options:
    Option 1: Fabric Panels (values: 1, 2, 3, 4)
    Option 2: Drop (values: 180cm, 210cm, 240cm)
  - Add metafield data to your curtain product
  - Set variant prices to match metafield prices


HOW IT WORKS
------------
1. Customer selects Width: "1401mm - 2800mm"
2. System calculates: 2 Fabric Panels needed (hidden)
3. Customer selects Drop: "210cm"
4. System looks up price: pricing["2_210cm"] = 22000 cents
5. Displays: "Add to cart - Rs.220.00"
6. Cart shows: Width: 1401mm-2800mm, Drop: 210cm (no Fabric Panels shown)



PRICING FORMAT
--------------
Key format: "panels_drop" (e.g., "2_210cm")
Price format: Cents (10000 = Rs.100.00)

Why cents? Avoids floating-point errors in calculations.



TECHNICAL DETAILS
-----------------

The system:
- Only affects products with custom.width_to_panel_map metafield
- Regular products continue to work normally
- Uses line item properties to pass data through cart
- Syncs variant prices with metafield prices for checkout


COMPATIBILITY
-------------
Built for: Shopify Dawn theme


SUPPORT
-------
For issues or questions, open an issue on GitHub