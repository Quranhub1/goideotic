# Idea 53 — Stocktake Sprint
## Engineering and business validation packet
**Status:** Discovery / validation — not yet proven  
**Initial market:** Independent retail shops in Kampala, Uganda  
**Working proposition:** A fast, independent physical stocktake and stock-record cleanup service for small shops that need a reliable picture of what is actually on their shelves, without committing to a full POS migration.

> Important: This is a proposed service concept, not a claim that the market is unserved. Public research found existing inventory software and at least one stock-counting service. Validate the gap with customers before investing.

## 1. The problem to test
Shop owners may not know whether their recorded stock matches the physical stock. Causes can include inconsistent item names, missing opening balances, pack-size confusion, unrecorded breakages, sales not recorded, and staff handovers. The business cost can be cash tied up in slow stock, avoidable stockouts, shrinkage that goes unnoticed, and time spent reconciling notebooks.

These are hypotheses to test, not assumed facts. Interview owners and workers about their most recent stocktake, not just whether they like the idea.

## 2. Competitive landscape — initial public scan
Check product features and current pricing directly before making purchase decisions; web pages can change.

| Alternative | What it appears to offer | Implication for Stocktake Sprint |
|---|---|---|
| [StockCount Africa](https://stockcountafrica.com/services) | Physical stock counting, inventory-data cleanup, variance/expiry reports, and digitized inventory setup | Closest visible service competitor. Study its target customer, scope, turnaround, and price before positioning. |
| [ALJEMPOS](https://aljemtec.com/products/aljempos) | Uganda-focused POS and inventory software; its page lists a one-off price from UGX 1,500,000 | Offer a lower-commitment service for businesses not ready to adopt or configure POS. |
| [VendorPlus](https://www.vendorplusuganda.com/) | Inventory and POS software, with a free tier and paid plans shown on its website | Do not compete by building another generic stock app before discovering a distinct unmet need. |
| [Stoowa POS](https://stoowapos.com/) | POS and inventory, including stock alerts and multi-shop support; pricing shown on its website | Could be a later tool a customer adopts after their item list and opening stock are cleaned. |
| [Bizinesiyo](https://bizinesiyo.com/) | Retail business management, inventory, suppliers and reports | Potential software alternative or partner/referral destination. |

**Competitive conclusion:** The broad idea of counting and digitizing inventory already exists. The opportunity, if validated, is likely in a tightly scoped customer segment or service experience: transparent fixed-scope pricing, after-hours/low-disruption counting, simple owner-readable variance reports, support for messy paper records, or a reliable handover into the customer's existing spreadsheet/POS. Do not claim uniqueness until further research supports it.

## 3. Proposed first customer segment
Start with one segment only: independent general-merchandise shops or mini-marts with roughly 100–1,000 active product lines, paper/spreadsheet records, and an owner who personally feels stock uncertainty. Treat this size range as a targeting hypothesis, not a market statistic.

Avoid pharmacies, medical inventory, high-value electronics, and regulated or safety-critical inventory in the first pilot. Those categories can add traceability, expiry, privacy, or compliance requirements.

## 4. Service offer
**Working name:** Stocktake Sprint  
**Promise to test:** “In one agreed session, get a checked count of agreed stock areas, a clean item list, and a clear exception report you can act on.”

Deliverables:
1. Agreed scope: shelves/rooms, categories, count date, and whether closed cartons/backroom stock are included.
2. Standardized item register: item description, unit/pack size, optional SKU/barcode, physical quantity, and notes.
3. Exception list: count differences against customer records, duplicates/ambiguous products, damaged/expired items if in scope, and items that could not be identified.
4. Owner summary: top discrepancies, missing data, suggested follow-up checks, and a dated copy of the count.
5. Optional CSV/Excel import into the customer's existing system, only after checking its required format.

**Do not promise** that a physical count proves theft, determines profit, or guarantees every item is counted correctly. Differences can result from timing, unit conversion, recording errors, damage, or counting mistakes.

## 5. First prototype — no app required
Tools:
- Smartphone or laptop
- Spreadsheet template with protected formula columns
- Clipboard, pens, removable shelf/aisle labels
- Calculator
- Customer-approved copy of existing stock list, if one exists
- Optional phone camera for item-identification notes only with permission

### Basic workflow
1. Meet owner and agree the counting boundary and time.
2. Export/copy the existing stock list; preserve an untouched backup.
3. Create count zones (for example, front shelves, back room, cartons).
4. One person calls out each item and quantity; a second person records or independently verifies higher-risk counts.
5. Record unit carefully: piece, pair, pack, carton, kilogram, litre, etc. Never silently convert a carton to pieces without confirming the pack size.
6. Mark uncertain items as **needs owner confirmation**, rather than guessing.
7. Recount material discrepancies and selected random items.
8. Compare against a snapshot of recorded stock as of the agreed time. Freeze or log stock movements during the count; otherwise the comparison can be misleading.
9. Review exceptions with the owner before making any changes to their live system.
10. Deliver the report and obtain sign-off on what was counted and what remains unresolved.

## 6. Spreadsheet schema
Suggested columns:
- Count date/time
- Zone / shelf
- Existing SKU (if any)
- Original item description
- Normalized item description
- Brand / variant
- Unit of measure
- Pack size / conversion note
- Recorded quantity (snapshot)
- Physical count 1
- Physical count 2 / recount
- Final agreed physical quantity
- Variance (physical minus recorded)
- Unit cost (only if customer provides it and needs valuation)
- Variance value (only if cost basis is clear)
- Condition / expiry note (only if in scope)
- Confidence: confirmed / uncertain / not counted
- Reason / owner action
- Counter initials

Example formula logic:
- Variance = Final agreed physical quantity minus Recorded quantity
- Variance value = Variance multiplied by agreed unit cost

Do not calculate a monetary variance when the stock unit and cost unit do not match. Keep raw customer data access-limited and delete it according to an agreed retention period.

## 7. Pilot test and success criteria
Run a small, paid or explicitly consented pilot with one shop, then a second independent shop before drawing conclusions.

Record:
- Number of product lines and physical units counted
- Total time on site and time spent cleaning data
- Percentage of lines confidently identified
- Recount disagreement rate on a random sample
- Number of duplicate/ambiguous item records found
- Owner-rated usefulness of the report
- Whether the owner would pay the proposed price again
- Whether the owner actually takes a follow-up action from the report

Suggested initial internal thresholds (adjust after the first pilot; these are not industry standards):
- At least 95% of in-scope lines have a confirmed count or a clearly flagged exception.
- Recount a random 10% of lines; target no more than 2% of recounted lines with a material count discrepancy after reconciliation.
- Deliver the agreed report within 24 hours of finishing the count.
- At least one of the first three pilot customers pays, or gives a specific, credible reason and date for not paying.

If these thresholds fail, improve the workflow and repeat before scaling.

## 8. Customer discovery — first 10 conversations
Ask shop owners:
1. Tell me about your last full stocktake. When was it, and who did it?
2. How do you know the notebook/software matches the shelves?
3. What happens when an item is missing or the quantity looks wrong?
4. Which product categories are hardest to count accurately, and why?
5. How many hours or staff members did the last count require?
6. What do you currently use: notebook, spreadsheet, POS, or a combination?
7. Have you ever paid someone to count or organize stock? What did they deliver?
8. What would make you distrust an outside counter?
9. Would you prefer an after-hours count, a weekend count, or counting one section at a time?
10. What would a useful, trustworthy report need to show for you to pay for it?

Avoid leading with “Would you buy my idea?” Ask for past behavior, real examples, and permission to quote a price for a clearly described pilot.

## 9. Initial pricing experiment — hypotheses, not market quotes
Test two clearly scoped offers with real customers. Do not treat the figures below as established Kampala market rates.

- **Small count pilot:** UGX 50,000–100,000 for a pre-agreed small scope, capped by product-line count and time.
- **Larger count / cleanup:** Quote only after a short scoping visit; price depends on product lines, number of locations, record quality, working hours, travel, and whether a second counter is needed.

State exclusions in writing: taxes if applicable, travel outside the agreed area, data entry beyond the cap, recounts caused by customer stock movement, and work on unopened/unidentified cartons unless included.

Calculate the minimum sustainable price:
Price floor = labour hours × target hourly rate + transport + consumables + data cleanup time + contingency.

Then compare that floor with what the customer will actually pay. If customers will not pay enough to cover delivery, narrow the scope or stop.

## 10. Basic unit economics worksheet
For every job, record:
- Revenue received
- Counter hours × labour cost
- Travel cost
- Data-cleaning hours
- Supplies / printing
- Rework or recount time
- Payment collection time/cost
- Gross contribution = revenue minus direct delivery costs
- Effective earnings per total hour = gross contribution divided by all hours spent

Do not count unpaid founder labour as zero cost when deciding whether the business can scale.

## 11. Trust, privacy, and operating safeguards
- Obtain written or message-based permission to access stock records and enter stock areas.
- Agree whether the shop will pause sales, log sales during the count, or count at a quiet time.
- Never alter live stock records without owner approval and a backup.
- Keep a dated, read-only original of the input stock list.
- Restrict who can access customer files; do not share shop-level stock or supplier data between clients.
- Do not photograph people, receipts, customer records, or restricted areas unnecessarily.
- Use two-person verification for high-value categories or when the owner requests it.
- Give the owner a clear limitations note and a chance to resolve uncertain items.
- Ask a local accountant or lawyer about appropriate contracts, liability, data handling, and tax obligations before scaling.

## 12. Four-week validation plan
**Week 1 — Discover:** Talk to 10 shop owners in one area. Record current methods, recent stocktake pain, and willingness to pay. Do not build software.

**Week 2 — Design:** Create the spreadsheet, scope checklist, count-zone sheet, service agreement, and one-page sample report using fictional data.

**Week 3 — Pilot:** Complete one small, agreed stocktake. Measure time, count quality, exceptions, and owner satisfaction. Charge a pilot price if the owner agrees.

**Week 4 — Decide:** Offer the same defined service to two more shops. Compare delivery cost and willingness to pay. Continue only if the service is accurate enough, operationally safe, and commercially plausible.

## 13. Go / revise / stop decision
- **Go:** Customers pay, count quality is repeatable, and delivery cost leaves a reasonable contribution.
- **Revise:** Customers value the result but scope is too broad, data cleanup takes too long, or pricing is wrong.
- **Stop or pivot:** Owners do not consider the problem important enough to pay for, existing providers already solve the need at a price you cannot match, or trustworthy delivery is not feasible.

## 14. Sources for further investigation
- [StockCount Africa — stock counting and inventory services](https://stockcountafrica.com/services)
- [ALJEMPOS — POS and inventory in Uganda](https://aljemtec.com/products/aljempos)
- [VendorPlus Uganda](https://www.vendorplusuganda.com/)
- [Stoowa POS](https://stoowapos.com/)
- [Bizinesiyo](https://bizinesiyo.com/)
- [WIPO PATENTSCOPE](https://patentscope.wipo.int/) — use if the project later includes a genuinely novel technical method or software/hardware invention; a service workflow alone may not be patentable. Search prior art before making intellectual-property claims.

**Research limitation:** This is an initial public-web scan, not an exhaustive competitor census, customer survey, patentability opinion, legal opinion, or verified price study. Competitor features and prices should be rechecked directly.
