# Edinburgh photo print price comparison: notes

Prices were collected on 27 October 2026 from each shop's website. Prices change, so check with the shop before ordering.

## Files

| File | What it is |
|---|---|
| `photo_print_prices.csv` | All shops in one sheet (1,025 rows). Sorted by Category, Print kind, Size (smallest first), then price. |
| `print_price_comparison.csv` | One row per Category + Size, with each shop's cheapest single-print price side by side and a "Cheapest" column. Only sizes sold by 2+ shops (35 rows). |
| `photo_print_prices_am_only.csv` | Backup of the A&M-only version, before the other shops were added. |
| `all_prices.csv` | Everything on A&M's price list, including film processing, photo books and calendars. |
| `standard_luster_print_prices.csv` | The first export: A&M Standard Luster prints only. |

### Columns in `photo_print_prices.csv`

- **Shop**
- **Category**: Photo Prints, Fine Art Prints, Canvas Prints, Metal Prints or Mounted Prints.
- **Print kind**: the paper or material, e.g. Luster, Glossy, Ultra Matte, Metal (ChromaLuxe), Mounted PVC 5mm. Group by this column.
- **Size**: smaller side first, e.g. `4x6in`, or an A size like `A4`.
- **Format**: Standard / Square / Panoramic / Enlargement / Poster for prints; Vertical / Horizontal / Square for metal and mounted.
- **Service**: Kodak only, Express (same day) or Next day.
- **Product name**: the shop's own name for the product.
- **Price each (GBP) 1+, 6+, 10+, 11+, 30+, 50+, 51+, 100+**: price per print when ordering at least that many. Blank means the shop has no price at that quantity.
- **Notes**: VAT, how a price was worked out, minimum orders, and similar.

All prices include VAT (see Edinburgh Copyshop below).

## Shops

### A&M Imaging: full data (782 rows)

- Source: https://amimage.photofinale.com/prints/pf/EWAmy879YXR5NOWQpRQDnaeV?category=standard-luster-prints
- The order page fills in its prices with JavaScript, so the data came from the site's full price list template at `https://amimage.photofinale.com/templates/prices` (the "Product & Price List" footer link).
- Includes luster and glossy prints (standard and square), 10 fine art papers, metal prints, and mounted prints (Card 2mm, PVC 5mm, PVC 10mm, MDF 9mm).
- Quantity tiers: 10+ / 30+ / 50+ / 100+ for luster and glossy prints, 6+ / 10+ for fine art papers. Metal and mounted prints have a single price.
- Possible errors on their price list:
  - 30x20in Mounted Card 2mm (horizontal) is listed at **£4,605.00**, far above the other sizes. Probably a typo.
  - 50x50in Mounted Card 2mm (square) is listed at **£0.00**.

### Kodak Express (South Clerk Street, Edinburgh): full data (219 rows)

- Source: https://www.kodakexpressedinburgh.co.uk/store_products.php (the `services.php?service_id=9, 10, 20, 100` pages)
- The site says its prices are for online orders and the South Clerk Street branch, and that the Ocean Terminal branch may charge differently.
- Includes standard, square, enlargement and panoramic prints; 250gsm photo-paper posters; canvas; and ChromaLuxe metal panels.
- Prints have two price tables: **Express (same day)** and **Next day**. Both are in the sheet, told apart by the Service column.
- Quantity bands are 1–5, 6–10, 11–50, 51–99 and 100+, stored as 1+, 6+, 11+, 51+ and 100+. There is a £1 minimum order.
- **Finishes:** Kodak charges the same for Gloss, Satin and Matte. Each print is listed twice in the sheet, as *Glossy* and as *Luster* (standing in for Satin), so it groups with A&M's kinds. Panoramic prints come in High Gloss or Matte, so they are listed as Glossy only.
- Sizes Kodak sells as one product ("8 x 12" / A4", "12 x 16" / A3") appear under both sizes.
- ChromaLuxe panel sizes were matched to the nearest standard size, e.g. 29.5x39.4cm became A3 and 40x60cm became A2. The exact size is in Notes.
- Left out: 90gsm and 180gsm plain matte posters, which aren't photo paper.

### Edinburgh Copyshop (52 St Mary's Street): partial data (24 rows)

- Source: the shop's online store (WooCommerce product data at `https://www.edinburghcopyshop.co.uk/wp-json/wc/store/v1/products`). The inkjet prices match their PDF price list (September 2026).
- Mostly a document and poster print shop. Its photo products are:
  - Large Format Inkjet Photo-Quality Printing, matte or gloss, at A2, A1 and A0 only.
  - Canvas on QuickPro corrugated-card frames, 8x8in to 20x30in.
  - Indoor Mounting on Kappafix, Budgetfix, Correx, recycled honeycomb or solid white PVC.
- **VAT:** the shop lists prices before VAT. I added 20% so they compare with the other shops, and the original price is in Notes. Their price list says some printing may be zero-rated.
- **Mounted prices are my own sums:** mounting is sold without the print, so each mounted price is the inkjet print price plus the mounting price, then VAT. There's no A3 row because they don't list an A3 inkjet print.
- No quantity discounts are listed for these products. Minimum orders are £1 for print only and £5 for print and finish.
- Left out: laser-printed posters (100–250gsm satin or silk paper), which aren't photo paper.

### Crescent Print (301–303 Cowgate): no price data

- Website: https://crescentprint.co.uk/
- Their photo printing page (https://crescentprint.co.uk/photo-printing-edinburgh/) describes the service: Mitsubishi dye-sublimation printers, gloss prints, 6x4 and 8x6 sizes, while-you-wait printing, and posters up to 1m wide. It gives **no prices** and asks customers to upload artwork for a quote.
- Their canvas, poster and foam board pages also have no prices.
- The only prices on the site are leaflet and poster bundle deals on the Special Offers page, which aren't photo printing.
- To get prices: call 0131 556 3582 (Mon–Fri 9:15am–5:15pm) or use the upload/contact form.

### Copy Print Edinburgh (Morrison Street): no price data

- Website: https://copyprintedinburgh.com/
- The site has no prices anywhere. Its Products and Services pages describe digital prints, large format posters (A2 to A0) and mounted / Dibond boards, but the product links go nowhere and nothing is priced.
- It mainly serves business, document and large-format work. It doesn't advertise photo-paper prints.
- To get prices: contact them via https://copyprintedinburgh.com/contact-us

## Findings

Comparing single-print prices from `print_price_comparison.csv`:

- **Small prints, up to about A4 / 8x12in:** Kodak is cheapest. A 6x4 is £0.50 (next day) or £0.60 (same day), against £1.50 at A&M. At 100+ prints Kodak's 6x4 is £0.15–£0.20 and A&M's is £0.24.
- **10x12in:** A&M and Kodak are level at £4.00.
- **10x15in to 12x18in:** A&M is cheaper, e.g. A3 is £5.00 at A&M and £6.00 at Kodak.
- **A2 / A1 posters:** Kodak (250gsm photo paper) and Edinburgh Copyshop (inkjet) are both £12 at A2. Kodak is cheapest at A1 (£20). A&M is £13 at A2 and £24 at A1.
- **Canvas:** Kodak's wooden-frame canvas is cheaper than Copyshop's card-frame canvas at every size both sell (e.g. 8x12in: £20 vs £39.60).
- **Metal prints:** A&M is cheaper than Kodak's ChromaLuxe at every shared size (e.g. 11x14in: £27.80 vs £48).
- **Fine art papers:** only A&M lists them, so there's nothing to compare.

## Caveats

- The comparison file only looks at size and category. It treats Glossy, Luster and inkjet prints as the same thing, and uses each shop's cheapest option, which for Kodak is often next-day service. The "kind" columns say what's being compared.
- I assumed A&M and Kodak prices already include VAT, since both are consumer price lists.
- Delivery, turnaround time and print quality aren't included.
