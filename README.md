# E-commerce Product & Ad Recommendation System

## Problem Statement

In e-commerce platforms, customers are often overwhelmed with vast product catalogs and generic advertisements. Traditional recommendation methods focus solely on historical purchase or click behavior, while advertising campaigns frequently target high-probability buyers regardless of whether the ad actually influences their decision.  
This results in inefficient product discovery, wasted advertising spend, and missed opportunities to engage customers who could be influenced by targeted ads.  
A solution is needed to combine personalized product recommendations with data-driven ad targeting that measures and maximizes the incremental impact of advertising.

---

## Project Idea

We propose building an integrated recommendation platform that merges multi-module product recommendation algorithms with uplift modeling-based ad targeting.  
The system recommends products through multiple approaches—search-based retrieval, similar item ranking, co-purchase analysis, category-based filtering, and multi-armed bandit for banner optimization—while also identifying the customers most likely to respond positively to ads.  
This ensures that product discovery is relevant and that advertising budgets are allocated to customers where they have the highest incremental impact on conversions and ROI.

---

## System Overview (Pipeline)

1. **Data Ingestion (Local/Cloud)**

    - Collects transactional logs, product metadata, browsing history, and ad exposure records from e-commerce databases.
    - Supports scheduled ingestion to maintain up-to-date recommendation and targeting datasets.

2. **Preprocessing & Feature Engineering**

    - Cleans and normalizes product attributes, user interaction logs, and ad exposure data.
    - Generates product embeddings for retrieval tasks and user behavioral profiles for targeting.
    - Encodes categorical features (e.g., category tags) and applies statistical transformations for uplift modeling.

3. **Product Recommendation Modules**

    - **Search & Retrieval**: Embedding-based vector search for product discovery.
    - **Similar Items**: Vector similarity ranking based on product attributes.
    - **Co-purchase Filtering**: Collaborative filtering to suggest items often bought together.
    - **Recently Viewed → Related Products**: Session-based ranking model for context-aware recommendations.
    - **Category Recommendations**: Preprocessed category-tag matching for personalization.
    - **Banner Optimization (MAB)**: Multi-armed bandit strategy to maximize banner CTR.

4. **Ad Uplift Modeling Pipeline**

    - Compares conversion behavior between ad-exposed and non-exposed groups.
    - Trains models to estimate individual treatment effect (uplift score) for each customer.
    - Uses Qini curve and Uplift@K metrics for evaluation.
    - Outputs high-impact customer segments for targeted ad delivery.

5. **Recommendation & Targeting Service Layer**

    - Integrates product recommendations and ad targeting logic into a FastAPI backend.
    - Supports asynchronous inference for real-time recommendations and targeting calls.
    - Deployable on local servers or cloud environments, with API endpoints for front-end or campaign systems.

6. **Evaluation & ROI Simulation**
    - Runs offline evaluation of recommendation accuracy and targeting impact.
    - Simulates advertising ROI under different targeting strategies before live deployment.
