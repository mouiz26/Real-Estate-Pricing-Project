# Buildings_Project
<!-- This is the markdown template for the final project of the Building AI course, created by Reaktor Innovations and University of Helsinki. Copy the template, paste it to your GitHub README and edit! -->

# Algerian Real Estate Price Engine

Final project for the Building AI course

## Summary

An AI-driven real estate valuation platform for Algeria that combines web-scraped market listings, geospatial data, and machine learning to estimate true market values, bridging the gap between cash-market prices and official records.

## Background

The Algerian real estate sector suffers from severe information asymmetry and valuation blindspots. Sellers often arbitrarily inflate asking prices, while official bank and notary records underreport actual values due to partial cash payments, low mortgage coverage, and tax declarations.

* **Frequency:** This is a persistent, systemic issue affecting nearly all private and commercial property transactions across the country.
* **Personal Motivation:** Real estate represents one of the largest financial decisions individuals make, yet decisions are currently driven by subjective gut feelings rather than objective data.
* **Importance:** Establishing a reliable pricing engine introduces transparency, assists financial institutions with risk assessment, and helps individuals gauge true market value without being misled by cash-market discrepancies.

## How is it used?

The system operates as a web platform or API module. Users input basic property characteristics (such as Wilaya, Commune, surface area, number of rooms, and paper/deed status) to receive an instant, objective market estimate.

Target users and stakeholders include:
* **Homebuyers & Sellers:** Gain pricing transparency to negotiate fair deals.
* **Real Estate Agencies & Appraisers:** Standardize valuation benchmarks beyond subjective intuition.
* **Banking & Financial Institutions:** Better assess mortgage risks and collateral valuations by bridging the gap between cash market dynamics and official records.

## Data sources and AI methods

Data is gathered from multiple primary, secondary, and open-source channels, processed using machine learning models designed for tabular and natural language data.

### Data Sources
* **Primary Listings Data:** Scraped property listings (asking prices, surface area, room counts, text descriptions) from platforms like Ouedkniss via direct GraphQL API requests or Playwright headless browser automation.
* **Open Demographics & Geospatial Data:** High-resolution spatial population counts (WorldPop / HDX GeoTIFFs), administrative boundaries and postal codes (Data-DZ / UpGrowth for 58 Wilayas), and points of interest like tram lines, schools, and city centers (OpenStreetMap).
* **Secondary Calibration Data:** Bank down-payments, mortgage approvals (e.g., CNEP-Banque, BNA), and notary records to calculate local Cash Delta Ratios.

### AI & Machine Learning Techniques
* **Natural Language Processing (NLP):** Vector embeddings or TF-IDF applied to property descriptions to extract key attributes (e.g., "vue sur mer", "act notarié/livret foncier").
* **Tabular ML Models:** Gradient Boosted Trees (XGBoost, LightGBM) and Random Forests to handle non-linear real estate features and missing fields effectively.
* **Data Cleaning Pipeline:** Hard rule filtering (eliminating dummy prices like 1 DZD or unrealistic ratios), group-wise IQR filtering on price per square meter, and training with Huber Loss or Mean Absolute Error (MAE) to remain robust against noise.

| Data / Technique | Description / Tools |
| ----------- | ----------- |
| Primary Data | Ouedkniss scraping (Playwright, GraphQL) |
| Spatial Data | WorldPop (HDX), Data-DZ, OpenStreetMap |
| Tabular Models | XGBoost, LightGBM, Random Forests |
| Preprocessing | Scikit-Learn, Pandas, GeoPandas |

## Challenges

What the project does *not* solve:
* It cannot legally verify off-market cash transactions that are never posted online or officially recorded.
* It cannot completely replace physical property inspections (e.g., evaluating unlisted structural damage or interior build quality).
* Rapid macroeconomic inflation or sudden policy changes may cause market shifts that historical listing data has not yet captured.

## What next?

Future growth directions for the project:
* Incorporate computer vision models (CNNs) to analyze listing photos and auto-score interior/exterior condition.
* Expand into temporal forecasting models (LSTM, Prophet) to predict neighborhood price appreciation over 3–5 year horizons.
* Integrate directly into bank mortgage portals or prop-tech mobile applications for real-time automated property evaluation.

## Acknowledgments

* **Datasets & Platforms:**
  * [WorldPop / HDX](https://data.humdata.org/) — Spatial population density mapping.
  * Data-DZ & UpGrowth Open Data — Administrative boundaries and Wilaya datasets.
  * UN Data & World Bank Open Data — Macroeconomic demographic indicators.
* **Libraries & Frameworks:** 
  * Python open-source ecosystem: Pandas, GeoPandas, Playwright, Scikit-Learn, XGBoost, LightGBM, and FastAPI.
