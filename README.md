# Buildings_Project
Project Name: AlgérieVal (or DZD Real Estate Price Predictor)  Brief Description: An algorithmic fair-value engine designed to predict realistic property and building prices across Algerian Wilayas and Communes by integrating web-scraped market listings, spatial population/infrastructure metrics, and baseline transaction proxies. 

BackgroundThe Problem: Algerian real estate suffers from high information asymmetry and valuation blindspots. Sellers often arbitrarily inflate asking prices, while official notary and bank records underreport actual values due to partial payments, low mortgage coverage, and tax declarations.

Frequency: This is a persistent, systemic issue that impacts nearly all private and commercial property transactions across the country. 
Personal Motivation: Real estate represents one of the largest financial decisions for individuals, yet buyers and sellers rely on subjective gut feeling rather than objective benchmarks.  

Importance: Establishing a reliable pricing engine brings price transparency, aids financial institutions in risk assessment, and helps individuals gauge true market value without being misled by cash-market discrepancies.  Data and AI TechniquesData Sources:Primary Listings Data: Web-scraped property listings (asking prices, surface area, room counts, descriptions) from local platforms like Ouedkniss via direct GraphQL API requests or Playwright headless browser automation. 

Open Demographics & Geospatial Data: Open-source platforms like WorldPop/HDX (high-resolution spatial population counts in GeoTIFF format), Data-DZ/UpGrowth (58 Wilaya/Commune administrative boundaries, postal codes), and OpenStreetMap (distance to tram lines, schools, city centers).

Secondary Calibration Data: Bank down-payments, mortgage approvals (e.g., CNEP-Banque, BNA), and notary records to compute local Cash Delta Ratios.  AI & Machine Learning Techniques:Natural Language Processing (NLP): Vector embeddings or TF-IDF on property descriptions (extracting key attributes like "vue sur mer", "act notarié/livret foncier").  Tabular ML Models: Gradient Boosted Trees (XGBoost, LightGBM) or Random Forests, which handle non-linear real estate features and missing fields better than linear models. 

Data Cleaning Pipeline: Rule-based hard filtering (eliminating dummy prices like 1 DZD or unrealistic surface ratios), group-wise IQR filtering on price per square meter, and training models using Huber Loss or Mean Absolute Error (MAE) to maintain robustness against noise. 

How it is UsedContext: The system operates as a web platform or API module where users enter basic property characteristics (Wilaya, Commune, surface area, rooms, paper status) and receive an instant, objective market estimate.  Target Users & Affected Stakeholders:Homebuyers & Sellers: Gain pricing transparency to negotiate fairly.  Real Estate Agencies & Appraisers: Standardize appraisal benchmarks beyond subjective estimates. 

Banking & Financial Institutions: Better assess mortgage risk and collateral valuations by bridging the gap between cash market dynamics and official records.  ChallengesWhat the Project Does Not Solve:It cannot legally verify off-market cash transactions that are never posted online or recorded anywhere.  It cannot completely replace physical property inspections (e.g., assessing unlisted structural damage or interior build quality). 

Rapidly changing macroeconomic inflation or unannounced policy changes may cause sudden price shifts that historical listing data has not yet captured.  What NextFuture Growth:Incorporate computer vision models (CNNs) to analyze listing photos and auto-score interior/exterior condition. 

Expand into temporal forecasting models (LSTM, Prophet) to predict neighborhood price appreciation over 3-5 year horizons. 

Integrate directly into bank mortgage portals or prop-tech mobile applications for real-time automated property evaluation. 

AcknowledgmentsOpen Source Datasets & Platforms:HDX / WorldPop: Spatial population density mapping.  Data-DZ & UpGrowth Open Data: Administrative boundaries and Wilaya datasets.

UN Data & World Bank Open Data: Macroeconomic demographic indicators.  Libraries & Frameworks: Open-source Python libraries including Pandas, GeoPandas, Playwright, Scikit-Learn, XGBoost, LightGBM, and FastAPI.  
