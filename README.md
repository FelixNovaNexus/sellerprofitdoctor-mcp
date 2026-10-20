# Seller Profit Doctor MCP server

A free, read-only remote MCP server for people who sell on Etsy, Shopify and Amazon. It runs Seller Profit Doctor's profit check-up for a shop, works out a platform's fees on one sale, prices for a target profit, the shipping gap, ads break-even, which Shopify plan fits, and what a box bills at, and returns each platform's dated, sourced fee table. Every answer links back to the matching page on [sellerprofitdoctor.com](https://sellerprofitdoctor.com), where the seller can check it.

- **Endpoint:** `https://sellerprofitdoctor.com/api/mcp`
- **Transport:** Streamable HTTP
- **Sign-in:** none (no account, no API key)
- **Registry name:** `com.sellerprofitdoctor/free-tools`
- **Docs:** https://sellerprofitdoctor.com/ai-assistants
- **How each tool works, word for word:** https://sellerprofitdoctor.com/ai-assistants/how-it-works

This repository holds the server's description only. The server itself runs on sellerprofitdoctor.com; its source is not public.

## Configure it

### VS Code (GitHub Copilot)

Add it to `.vscode/mcp.json`, or run **MCP: Add Server** and paste the address:

```json
{
  "servers": {
    "sellerprofitdoctor": {
      "type": "http",
      "url": "https://sellerprofitdoctor.com/api/mcp"
    }
  }
}
```

### Claude

In Claude on the web or the desktop app: **Customize › Connectors › + › Add custom connector**, name it Seller Profit Doctor, paste `https://sellerprofitdoctor.com/api/mcp`, and choose no sign-in.

### Any other MCP client

Add a remote server with the address above, transport Streamable HTTP, and no authentication.

## Use it

Ask in plain words, for example:

- "Run a profit check-up for my Etsy shop: about 100 orders a month of a 30 dollar item."
- "What does Etsy take from a 45 dollar sale with 6 dollars shipping?"
- "My label costs 7 dollars and buyers pay 5. What should my item cost to cover it?"
- "At 12,000 dollars of card sales a month, which Shopify plan costs me least?"
- "What are Amazon's fees on one 29.99 dollar kitchen item sent through FBA?"

## Tools (15, all read-only)

**Check-up**
- `sellerprofit_checkup`: the free profit check-up for an Etsy shop, a Shopify store or an Amazon seller: the grade word, what one order and the month keep after fees, ads and costs, and the top 3 losses, each with its fix and what it's worth a month at the seller's numbers if orders hold.

**Etsy**
- `sellerprofit_etsy_fees`: Etsy's fees on one sale, line by line (listing, transaction, payment processing, currency conversion, Offsite Ads).
- `sellerprofit_offsite_ads`: what Offsite Ads cost a shop per order and per month, and the item price that covers the fee.
- `sellerprofit_shipping_gap`: what the label and packaging cost beyond what the buyer pays, and the prices that close the gap.
- `sellerprofit_ads_breakeven`: the ROAS at which Etsy Ads pay for themselves, and what the ads gain or lose a month.
- `sellerprofit_price_for_margin`: the item price at which one Etsy order keeps a target profit, or breaks even.

**Shopify**
- `sellerprofit_shopify_plan_fit`: which Shopify plan (Basic, Grow, Advanced) and billing costs least at a store's card sales.
- `sellerprofit_shopify_order_fees`: every fee on one order of a US Shopify store, line by line.

**Amazon**
- `sellerprofit_amazon_fees`: Amazon's fees on one unit: the referral fee for the category, the media closing fee, and an estimate of the FBA fee.
- `sellerprofit_amazon_ads_breakeven`: the ACoS at which Sponsored Products pay for themselves, outside and inside peak season.

**Any platform**
- `sellerprofit_sale_breakeven`: how many more orders a sale or coupon needs to keep the same profit a month.
- `sellerprofit_compare_fees`: the fees on one sale on Etsy, Shopify and Amazon, side by side.
- `sellerprofit_ads_roas_breakeven`: the break-even ROAS for Facebook, Instagram or Google ads that send buyers to a Shopify store, an Etsy listing or an Amazon listing.
- `sellerprofit_box_billing`: the billable weight of one box with USPS, UPS and FedEx, from its size and weight.

**Fee tables**
- `sellerprofit_rates`: one platform's fee table, the one these tools use: every fee with its value, its source link, the day it was checked, and whether it's official or a third-party estimate.

## Privacy

Nothing sent to the server is stored: not the figures, choices or answers. The logs keep only each call's tool name, how long it took and whether it answered, and the site counts how many times each tool ran each day (no inputs, no address). To stop overload, calls from one internet address are counted for a minute, in memory only, and the address is never logged. Details: https://sellerprofitdoctor.com/privacy

Results are estimates, not financial, tax or legal advice.

## Contact

- Support: support@sellerprofitdoctor.com
- Security: security@sellerprofitdoctor.com
- Published by Gomorra Labs LLC
