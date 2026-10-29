# Idea 53 — Worldwide Prior-Art and Materials Research
**Project:** Stocktake Sprint — physical stocktaking, inventory data cleanup, and discrepancy reporting  
**Research pass:** 1 — public sources and implementation evidence  
**Status:** Desk research only; no customer interviews, live field test, or supplier price verification has been completed.

## 1. What this research is for
Before inventing a new solution, study existing products, open-source code, documented workflows, and real-world deployments. This dossier records what similar projects already do, what materials/tools or software they use, how they operate, and which parts could be adapted for a low-cost Uganda pilot.

**Important distinction:** Stocktake Sprint as a service is not a new invention yet. Stock-counting services, barcode-based stocktaking, offline inventory apps, and inventory software already exist. Any differentiation must be tested with customers and not claimed as novel without evidence.

## 2. Similar projects and what can be learned

### A. StockCount Africa — inventory-counting service
**Source:** https://stockcountafrica.com/services  
**Type:** Commercial service, apparently relevant to African businesses.

Publicly described service components:
- Physical counts by location, shelf, bin, batch, and unit of measure.
- Standardization of item names, SKUs, categories, and pack sizes.
- Duplicate-record cleanup.
- Variance and expiry reporting.
- Digitization and transfer of verified opening stock into an inventory workspace.

**What to study/adapt:** The service can be packaged as separate deliverables rather than just “counting”: verified count, cleaned catalogue, variance report, and structured data handover.

**Research still needed:** Confirm operating countries, customer segment, process, equipment, current pricing, service guarantees, and actual case studies directly with the provider. Do not assume its prices or service scope without confirmation.

### B. Quick Stocktaker — open-source/free Android stock-counting app
**Source:** https://github.com/jedipi/Quick-Stocktaker  
**Type:** Source-available software project; verify current licence and build instructions in its repository before reuse.

Documented capabilities:
- Uses a phone camera to scan product barcodes.
- Stores stock-count data locally; internet is not required for counting.
- Exports results to CSV for use in ERP/CRM systems.
- Can send count results by email.
- Does not require expensive dedicated scanning hardware.

**Materials/tools evidenced:** Android phone with camera; barcode labels already present on products; app/software; CSV-compatible computer workflow if further analysis is needed.

**Lesson:** For a first pilot, a phone and spreadsheet may be sufficient. A custom app is not a prerequisite. CSV export is a practical bridge to existing systems.

### C. Pantry Tracker — offline Android inventory app
**Source:** https://github.com/DocGerd/pantry-tracker  
**Type:** Open-source Android implementation.

Documented technical stack:
- Kotlin and Jetpack Compose for the Android app.
- Room/SQLite for local on-device storage.
- CameraX and Google ML Kit for EAN-13, EAN-8, UPC-A, and UPC-E barcode scanning.
- Ktor HTTP client and Open Food Facts lookup for product information.
- Coil for image loading.

**What the components do:** The camera and scanning library read a barcode; local database storage keeps inventory usable offline; an optional product lookup can fill in catalogue information when a connection is available.

**What to reuse conceptually:** Offline-first storage, explicit user confirmation after a scan, product lookup as optional assistance rather than a required dependency.

**Cautions:** This is a pantry tracker, not a proven retail stocktaking workflow. Its dependency choices are examples, not a mandatory bill of materials. Check repository licence and dependencies before copying code.

### D. Stockify — offline-first Android retail inventory
**Source:** https://github.com/Varadha9/Stockify  
**Type:** Open-source Android inventory app.

Documented features/stack include:
- Camera barcode scanning with ZXing Android Embedded.
- Local Room database.
- CSV export and JSON backup/restore.
- Stock change log and bulk quantity adjustments.
- Low-stock thresholds and inventory reports.

**Lesson:** Audit history, backups, and exports matter alongside scanning. For stocktaking, a count should be traceable: who counted, when, what changed, and why.

**Caution:** General inventory management is not the same as a controlled physical stocktake. The project is a reference implementation, not proof of commercial readiness.

### E. AlmacenTracker — offline warehouse inventory
**Source:** https://github.com/rndymi/AlmacenTracker  
**Type:** Open-source Android project.

Documented features:
- Local-first storage that works without internet.
- Barcode/QR scanning.
- Local OCR for reading information from images.
- Item location tracking, CSV tools, and withdrawal history.

**Lesson:** OCR may help with labels or paper records, but it introduces recognition errors and should not silently decide the identity or quantity of stock. Keep manual correction and an “uncertain” state.

**Caution:** Its own project documentation notes parts of the application were not verified as compiled/run. Treat it as an idea source, not a validated production design.

### F. Inventur / PackScan for Dolibarr — mobile web stock-counting tools
**Source:** https://wiki.dolibarr.org/index.php/Inventur_and_PackScan  
**Type:** Free/open-source mobile web apps linked to an existing Dolibarr ERP installation.

Documented approach:
- Runs in a phone browser.
- Scans barcodes for picking, packing verification, stock counting, and location management.
- Connects to an existing Dolibarr installation through its REST API.
- Avoids a separate application backend/database for the mobile tool.

**Lesson:** If a customer already has an ERP, an integration can be more useful than replacing their system. However, the first pilot should remain independent of complex integration until demand is proven.

### G. Square for Retail — full counts and cycle counts
**Source:** https://squareup.com/help/gb/en/article/8249-conduct-full-inventory-counts-with-square-for-retail  
**Type:** Commercial POS inventory workflow.

Documented practices:
- Full inventory counts and cycle counts.
- Count by category or selected products.
- Camera or compatible barcode scanner.
- Support for configured measurement units and stock-unit conversion.
- Review/confirmation before submitting counts.

**Lesson:** Unit conversion, duplicate items, count sessions, and review before posting adjustments are important design requirements. A service must record whether quantities are in pieces, packs, cartons, kilograms, or another unit.

### H. SAP physical inventory with barcode scanning
**Source:** https://help.sap.com/docs/SAP_S4HANA-ON-PREMISE/91b21005dded4984bcccf4a69ae1300c/df4f15c530384299a4dcec1e9154f207.html  
**Type:** Enterprise workflow documentation.

Documented options include a smartphone camera or external barcode scanner, with inventory documents and count records handled through a controlled workflow.

**Lesson:** Separate counting from approving/posting adjustments. A counter should not silently change the customer's live stock balance; the customer should review and approve the result.

### I. RGIS — inventory preparation guidance and large-scale count case studies
**Preparation guide:** https://www.rgis.ca/tip-insight/how-to-prepare-for-an-inventory/  
**Example QR/drone case:** https://www.rgis.ca/case-study/drone-warehouse-verification-count-with-qr-codes/  
**Example distribution-centre cycle counts:** https://www.rgis.sg/case-study/cycle-counts-for-two-distribution-centres/

Documented practical materials/processes in RGIS preparation guidance:
- Inventory sheets.
- Write-off/damage sheets.
- Calculators.
- Handheld barcode scanners for barcoded stock.
- Shelf/location labels and a defined count direction.
- Physical checking of boxes rather than relying only on carton labels.
- Rechecking discrepancies and updating records after the count.

The QR/drone case describes product QR codes carrying location, barcode, SKU, and quantity information. That is a specialized high-rack warehouse solution, not suitable or necessary for the first small-shop pilot.

**Lesson:** Use zone labels, explicit count direction, no estimates, and discrepancy recounts. Do not buy drones or specialist equipment for a basic shop count.

### J. U.S. Government Accountability Office — physical inventory control guide
**Source:** https://www.govinfo.gov/content/pkg/GAOREPORTS-GAO-01-763G/pdf/GAOREPORTS-GAO-01-763G.pdf  
**Type:** Public-sector control guidance.

The guide describes manual count tags/sheets or computerized location systems to help ensure items are counted once and only once, and recommends numbered tags/cards and supervisory checks in suitable environments.

**Lesson:** Assign count zones and use a clear completion marker. Prevent both omissions and double counting.

## 3. Existing-project comparison

| Project / source | Main approach | Hardware/materials | Software/data | Best lesson for our first version |
|---|---|---|---|---|
| StockCount Africa | Human stocktaking service + data cleanup | Counting team, inventory access; exact equipment not confirmed | Clean catalogue, variance/expiry report, inventory handover | Sell clear deliverables, not only labour |
| Quick Stocktaker | Phone-based barcode stock count | Android phone/camera, existing product barcodes | App, local count data, CSV/email export | No special scanner required initially |
| Pantry Tracker | Offline product tracking | Android phone/camera, product barcodes | Kotlin, Room/SQLite, CameraX, ML Kit | Offline-first design and confirmation step |
| Stockify | Retail stock management | Android phone/camera, barcodes | Room, ZXing, CSV/JSON, stock logs | Backups and audit history |
| AlmacenTracker | Offline warehouse inventory + OCR | Android phone/camera, labels or QR codes | Local database, OCR, CSV, history | OCR needs manual verification |
| Inventur / PackScan | Mobile web app connected to ERP | Smartphone, barcode labels | Dolibarr REST API | Integrate later when a client needs it |
| Square for Retail | POS-based full/cycle count | Phone camera or compatible scanner | POS inventory and unit conversion | Formal count session and approval |
| SAP | Controlled enterprise stocktaking | Smartphone camera or external scanner | Inventory documents and approval workflow | Separate count, review, and posting |
| RGIS manual method | Staff count with zones and controls | Sheets, labels, calculator, optional scanner | Count sheets and final inventory records | Zone control, recounts, no estimates |

## 4. Recommended first-pilot materials list

### Required — minimum manual prototype
| Item | Purpose | Quantity | Price status |
|---|---|---:|---|
| Smartphone with camera | Photograph/identify products when permitted; optional barcode scanning | 1 | Use an existing phone if available; no price assumed |
| Laptop or smartphone capable of spreadsheets | Enter and review counts | 1 | Use an existing device if available |
| Spreadsheet template | Record item, unit, count, recorded quantity, variance, confidence, and notes | 1 | Can be created with existing spreadsheet software |
| Clipboard or firm writing surface | Support paper backup counts | 1 | Local quote required |
| Pens and marker | Mark count sheets and zones | 2–3 | Local quote required |
| Paper count sheets / printed zone labels | Track items and mark completed locations | As needed | Local quote required |
| Calculator | Cross-check totals and conversions | 1 | Phone calculator is sufficient |
| Customer's approved stock list (if any) | Baseline for comparison | 1 copy | Customer-provided with permission |
| Simple scope/consent form | Defines locations, access, data handling, and approval | 1 | Draft locally; legal review if scaling |

### Optional — only after manual pilot demonstrates need
| Item | When useful | Notes |
|---|---|---|
| Bluetooth or USB barcode scanner | Many barcoded items and phone scanning is too slow | Check Android/PC compatibility and connection mode before purchase |
| Low-cost label printer | Customer has no usable SKU labels and wants future repeat counts | Not needed to count products that already have readable labels |
| QR/barcode labels | Track shelf zones or unlabelled internal items | Do not relabel customer goods without approval; distinguish internal labels from manufacturer GTINs |
| Second counter | Independent verification or large/high-value count | Labour cost must be included in pricing |
| Portable power bank | Long count sessions | Only if existing phone battery is insufficient |
| Laptop | Large catalogue cleanup and reporting | Not mandatory if a capable phone/tablet workflow is adequate |

**No electronics prototype is required for this idea.** The core “materials” are a device, count sheets, a structured spreadsheet, zone labels, and a controlled operating procedure. Do not buy RFID readers, drones, custom hardware, or develop an app until a real customer problem justifies them.

## 5. Proposed spreadsheet/data model based on the reviewed projects
Minimum columns:
- Count session ID and date/time
- Shop / zone / shelf
- Item identifier (SKU/barcode, if available)
- Original description and normalized description
- Unit of measure and pack conversion
- Book/record quantity snapshot
- Physical count
- Recount quantity (if needed)
- Final agreed quantity
- Variance
- Count status: confirmed / uncertain / inaccessible / not counted
- Reason/owner follow-up
- Counter initials
- Reviewer/owner approval
- Change history or audit note

Use a frozen copy of the pre-count record. Do not overwrite the baseline. Keep count results and approved inventory adjustments as separate stages.

## 6. Recommended field procedure derived from documented practice
1. Agree the scope, time, zones, unit definitions, access permissions, and data-handling terms with the owner.
2. Save a dated, read-only snapshot of the existing stock records.
3. Label zones and set a consistent direction of travel.
4. Decide how to handle sales and deliveries during the count; pause or log movements so they do not distort comparison.
5. Count every accessible in-scope item; do not estimate carton contents. Open cartons when permitted and safe.
6. Record the unit and pack size; never assume a carton count equals individual units.
7. Mark ambiguous, inaccessible, or damaged stock explicitly instead of guessing.
8. Recount material discrepancies and a sample of other lines.
9. Have the owner review exceptions before any adjustment is posted to their live system.
10. Deliver the count file and report, preserve an agreed audit trail, and delete customer data according to the agreed retention period.

## 7. Low-cost prototype build sequence
**Prototype 0 — paper + spreadsheet:** Use a sample dataset and fictional shop records to test the columns, formulas, and report. No customer data needed.

**Prototype 1 — manual count:** Run a small, authorized count using paper backup plus spreadsheet entry. Measure minutes per line, unclear item rate, and recount rate.

**Prototype 2 — phone barcode scanning:** Only if barcode scanning would materially reduce time. Test whether the shop's products have readable barcodes and whether the codes map reliably to its own SKU list. A barcode identifies an item code; it does not automatically reveal the actual quantity on a shelf.

**Prototype 3 — app/integration:** Only after multiple paid pilots establish repeatable requirements. Evaluate offline storage, CSV import/export, access controls, audit logs, backup/restore, and error correction before cloud sync or multi-user features.

## 8. Test plan and measurable results
Test on a small, permissioned sample first:
- Compare the original record to the physical count.
- Randomly select a subset for independent recount.
- Measure percentage of items identified confidently.
- Record count time per line and time spent normalizing product descriptions.
- Track the number of duplicate descriptions, pack-size conflicts, and missing identifiers.
- Test CSV export/import with a copy of the customer's data.
- Verify that no inventory adjustment is posted without owner approval.
- Ask the owner whether the report changed a decision and whether they would pay for another count.

Do not describe an arbitrary threshold as an industry standard. Set a baseline during the first pilot and improve it across later pilots.

## 9. Potential differentiation to validate — not assume
- Works from notebooks or messy spreadsheets instead of requiring a POS migration.
- Fixed, clearly capped scope and price.
- Evening or low-disruption counting.
- Explicit handling of pack sizes, duplicates, and uncertain products.
- Independent recount and sign-off trail.
- Clean CSV handover compatible with the customer's existing system.
- Local-language instructions or reports if customers request them.

These are hypotheses. Ask shop owners which problem they would actually pay to solve.

## 10. What is still unknown / next research actions
- Current competitor pricing, coverage, turnaround, and customer references.
- Whether StockCount Africa or other providers actively serve the intended Kampala segment.
- Actual supplier quotes for a compatible scanner, labels, printing, transport, and consumables.
- The local willingness to pay and acceptable service scope.
- Customer data privacy, contracts, liability, and tax requirements for a commercial service.
- The licensing conditions of each open-source project before reusing code or assets.
- Whether a patent or other intellectual-property search is relevant. A service process alone may not be patentable; do not make novelty claims without specialist review.

## 11. Research references
1. StockCount Africa, “Stock counting and inventory services” — https://stockcountafrica.com/services
2. Quick Stocktaker source repository — https://github.com/jedipi/Quick-Stocktaker
3. Pantry Tracker source repository — https://github.com/DocGerd/pantry-tracker
4. Stockify source repository — https://github.com/Varadha9/Stockify
5. AlmacenTracker source repository — https://github.com/rndymi/AlmacenTracker
6. Dolibarr Wiki, “Inventur and PackScan” — https://wiki.dolibarr.org/index.php/Inventur_and_PackScan
7. Square Support, “Conduct, review, and approve inventory counts” — https://squareup.com/help/gb/en/article/8249-conduct-full-inventory-counts-with-square-for-retail
8. SAP Help Portal, “How to Manage Counting of Physical Inventory with Barcode Scanning” — https://help.sap.com/docs/SAP_S4HANA-ON-PREMISE/91b21005dded4984bcccf4a69ae1300c/df4f15c530384299a4dcec1e9154f207.html
9. RGIS, “How to Prepare for an Inventory” — https://www.rgis.ca/tip-insight/how-to-prepare-for-an-inventory/
10. RGIS, “Drone Warehouse Verification Count with QR Codes” — https://www.rgis.ca/case-study/drone-warehouse-verification-count-with-qr-codes/
11. RGIS, “Cycle Counts for Two Distribution Centres” — https://www.rgis.sg/case-study/cycle-counts-for-two-distribution-centres/
12. U.S. Government Accountability Office, “Best Practices in Achieving Consistent, Accurate Physical Counts of Inventory and Related Property” — https://www.govinfo.gov/content/pkg/GAOREPORTS-GAO-01-763G/pdf/GAOREPORTS-GAO-01-763G.pdf
13. Trimble Spectrum Help, “Perform a Physical Inventory Using a Barcode Scanner” — https://help.trimble.com/doc/spectrum/spectrum/materials/inventory-control/procedures-overview/tell-me-how/perform-a-physical-inventory-using-a-barcode-scanner

## 12. Research quality statement
This is a first-pass synthesis of publicly available project pages and documentation. It is not an exhaustive global search, a product teardown, a field trial, a supplier quotation, a legal opinion, or evidence that the proposed service will be profitable. Links and software versions may change. Before reusing code, verify each repository's current licence and dependency licences.
