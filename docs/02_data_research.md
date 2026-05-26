# 02 — Data Research and Acquisition

## 2.1 Data Search Process

The search for suitable data was guided by one core requirement: 
real transaction prices from the Jordanian apartment market, not 
listing prices. Listing prices are asking prices that can be 10–20% 
above the final sale value and are therefore unsuitable as a training 
target for a valuation model. Four sources were identified and used.

---

## 2.2 Data Sources

### Source 1 — Company X (Primary Source)
Company X is a Jordanian real estate firm operating across multiple 
cities. The team contacted the company directly and obtained a 
proprietary dataset of apartment transactions in Excel format. 
This was the richest and most structured source, containing verified 
transaction prices alongside detailed property features.

### Source 2 — OpenSooq
OpenSooq is one of Jordan's largest online classifieds platforms. 
Apartment listings were collected manually, including price, size, 
location, bedrooms, and available amenities. While listing prices 
carry some uncertainty, OpenSooq provides broad geographic coverage 
across all Jordanian cities.

### Source 3 — Facebook Marketplace
Real estate groups on Facebook are widely used in Jordan for direct 
property sales. Listings from relevant groups were collected, focusing 
on apartments with clearly stated prices and detailed descriptions. 
This source provided additional coverage for smaller cities and 
informal market segments.

### Source 4 — Court Auction Records
Records from court-ordered property auctions were collected. These 
represent the most directly relevant data for the project's goal — 
mortgaged apartments sold through judicial proceedings. Auction prices 
reflect forced-sale values, which are typically 10–20% below open 
market prices.


> The following are real appraisal reports and court auction advertisements 
> showing how traditional appraisers estimate property values manually.

<img src="../assets/REPORT.jpg" width="280"/> <img src="../assets/REPORT%20(2).jpg" width="280"/> <img src="../assets/REPORT%20(6).jpg" width="280"/>

<img src="../assets/ADV.jpg" width="280"/>

## 2.3 Data Sources Summary

| Source | Type | Access Method | Relevance |
|--------|------|--------------|-----------|
| Company X | Excel file (proprietary) | Direct contact | Primary — verified transactions |
| OpenSooq | Online listings | Manual collection | Broad coverage |
| Facebook Marketplace | Social media listings | Manual collection | Informal market |
| Court Auction Records | Judicial records | Manual collection | Most relevant to project goal |

---

## 2.4 Combined Dataset

All sources were merged into a single Excel file:

| Property | Value |
|----------|-------|
| Total records | 626 apartments |
| After cleaning | 603 apartments |
| Cities covered | 8 cities |
| Neighborhoods | 91 unique locations |
| Price range | 9,975 — 359,800 JOD |
| Features per apartment | 22 original + 4 engineered |

Since records were merged without source tagging, it is not possible 
to attribute individual records to specific sources. The combined 
dataset was treated as a unified pool of Jordanian apartment transactions.

---

## 2.5 Data Limitations

| Limitation | Impact on Model |
|-----------|----------------|
| 603 records only | Small dataset — more data would improve accuracy |
| Mixed listing and transaction prices | Some price noise from OpenSooq and Facebook |
| No transaction dates | Cannot control for market fluctuations over time |
| Missing contextual features | Schools, hospitals, city centers not captured |

---

## 2.6 Why These Sources?

Each source was chosen for a specific reason:

- **Company X** → Verified transaction prices — most reliable
- **OpenSooq** → Geographic coverage across all 8 cities
- **Facebook** → Captures informal market and smaller cities
- **Court Auctions** → Direct relevance to mortgaged property valuation
