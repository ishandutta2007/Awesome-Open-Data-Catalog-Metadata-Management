# Awesome-Open-Data-Catalog-Metadata-Management

## Top Open Data Catalog & Metadata Management Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Metadata Discovery, Data Lineage & Self-Hosted Catalog Platforms*  

**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Open Data Catalog & Metadata Management**. These tools enable organizations to discover, understand, and govern data assets across heterogeneous systems—providing a searchable inventory of tables, dashboards, pipelines, and models with lineage, ownership, and classification that make data trustworthy and AI-ready.

**Open-source emphasis**: Open Data Catalog & Metadata Management is a domain where open-source tooling is **genuinely mature and production-proven at the catalog layer**, with clear leaders for different architectural philosophies. **OpenMetadata** and **DataHub** lead modern all-in-one governance and event-driven architectures, while **Apache Polaris** and **Apache Gravitino** power Iceberg REST standards and federated metalakes.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS/Hosted Platforms](#saashosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

---

## Sector Overview & Market Dynamics

The global data catalog and metadata management market is estimated at **$3.6 billion to $4.4 billion in 2026** and projected to expand past **$14 billion to $19 billion by the early 2030s**, compounding at ~19%–21% CAGR driven by enterprise data sprawl, compliance mandates (GDPR/EU Data Act), and Generative AI governance needs. 

The sector is **moderately fragmented overall yet concentrated around dual gravitational poles**: hyperscalers (Microsoft, AWS, Google Cloud) and platform providers (Databricks, Snowflake) capture broad baseline metadata share natively, while established pure-play pioneers (Alation, Collibra) and modern active metadata vendors dominate specialized multi-cloud enterprise governance, preventing any single winner-take-all monopoly.

---

## SaaS/Hosted Platforms

| Platform | Company Valuation / Revenue | Starting Tier Pricing | Free Tier / Trial Limits | Key Highlights & Description |
| :--- | :--- | :--- | :--- | :--- |
| **[Microsoft Purview](https://www.microsoft.com/en-us/security/business/compliance/microsoft-purview)** | Market Cap: **~$3.88 Trillion** (Revenue: ~$245B+) | Starting at **$0.0165/asset/day** (Unified Catalog pay-as-you-go) + M365 E5 compliance add-ons | **Permanent Free Tier**: Up to **1,000 annotated assets** (Azure & Fabric sources; 3-month inactivity auto-purge policy) | Microsoft's unified data governance, risk, and catalog service deeply integrated with Azure, Fabric, and Microsoft 365. |
| **[Google Cloud Dataplex Knowledge Catalog](https://cloud.google.com/dataplex)** | Market Cap: **~$3.2–$3.5 Trillion** (Alphabet; Revenue: ~$350B+) | Starting at **$2.00/GiB/month** for custom metadata storage + **$0.089/DCU-hr** processing | **Permanent Free Tier**: First **1 MiB** enriched/custom metadata storage free; **100 DCU-hours/month** standard processing free; automatic technical metadata collection and console search queries are free ($300 GCP credit trial for new accounts) | Google Cloud's built-in intelligent catalog automatically harvesting metadata across BigQuery, Cloud Storage, Vertex AI, and Spanner. |
| **[AWS Glue Data Catalog](https://aws.amazon.com/glue/)** | Market Cap: **~$2.6–$2.7 Trillion** (Amazon; Revenue: ~$600B+) | Starting at **$1.00 per 100,000 objects/month** (storage) & **$1.00 per 1M requests** | **Permanent Free Tier**: First **1,000,000 objects** stored free each month and first **1,000,000 requests** free each month (non-expiring AWS Free Tier) | AWS's managed metadata catalog with native Apache Iceberg REST endpoint (`glue.<region>.amazonaws.com/iceberg`), Lake Formation governance, and Athena/EMR/Redshift integration. |
| **[Unity Catalog (Databricks)](https://www.databricks.com/)** | Valuation: **~$188 Billion** (Revenue Run-Rate: ~$7B+) | Included with Databricks **Premium Tier** at base compute rates starting at **$0.15–$0.22/DBU** | **14-day free trial** with up to **$400 in usage credits** (capped at 1 SQL warehouse up to 50 DBUs/hr; separate from perpetual Databricks Free Edition for learning) | Databricks' centralized data and AI governance platform for tables, volumes, features, and models with Iceberg REST interoperability. |
| **[Snowflake Horizon](https://www.snowflake.com/)** | Market Cap: **~$107–$119 Billion** (Revenue: ~$3.6B+) | Included starting on Snowflake **Enterprise Edition** at **$3.00/credit** consumption + ~$23/TB monthly storage | **30-day free trial** with **$400 in free usage credits** (trial terminates upon credit exhaustion or 30 days, whichever comes first; no credit card required upfront) | Snowflake's built-in governance solution delivering automated lineage, data quality monitoring, and sensitive data classification. |
| **[Snowflake Open Catalog](https://www.snowflake.com/)** | Market Cap: **~$107–$119 Billion** (Revenue: ~$3.6B+) | Consumption billing based on REST API requests to Iceberg endpoints; external S3/GCS/Azure table storage charged directly by cloud provider | **Free Tier during initial rollout / 30-day trial**: Subject to request throttling (capped at avg 5 req/sec, bursts up to 50 req/10s on trial orgs) | Snowflake's managed Apache Polaris service running the vendor-neutral Iceberg REST catalog specification for multi-engine access. |
| **[Collibra Data Intelligence Platform](https://www.collibra.com/)** | Valuation: **~$5.3 Billion** (ARR: ~$150M–$200M+) | Starting at custom enterprise contract (~**$100,000–$180,000/year** base deployment) with **unlimited free Read-Only/Viewer licenses** | **Custom PoC / Sales-assisted trial**: Typically **14 to 30 days** structured proof-of-concept for up to 5 data sources upon sales qualification | Enterprise data intelligence pioneer with deep policy curation, business glossaries, active lineage, and out-of-the-box regulatory frameworks. |
| **[Alation](https://www.alation.com/)** | Valuation: **~$1.7 Billion** (ARR: ~$109M–$120M+) | Starting at **$60,000/year** (AWS/Azure Marketplace base entry) to ~$198,000/year (bundled creator packs) | **15-day sales-assisted evaluation trial** (under standard Alation Trial Use Agreement; or 14-day sandbox via Snowflake Partner Connect) | The category pioneer for behavioral data search, machine-learning data curation, stewardship workflows, and cross-system lineage. |

---

## Open-Source GitHub Projects

The table below lists top open-source metadata platforms, Iceberg REST catalogs, and data lineage engines, sorted descending by GitHub star count:

| Project | Stars | Primary Architecture / Category | License | Core Strengths & Use Cases |
| :--- | :--- | :--- | :--- | :--- |
| **[OpenMetadata](https://github.com/open-metadata/OpenMetadata)** | [![Stars](https://img.shields.io/github/stars/open-metadata/OpenMetadata?style=social&color=white)](https://github.com/open-metadata/OpenMetadata/stargazers) | Schema-First Catalog & Governance | Apache-2.0 | Architectural simplicity (three services for production: Java server, MySQL/Postgres, Elasticsearch/OpenSearch). Includes built-in data quality tests, no-code data profiling, and enforceable data contracts. |
| **[DataHub](https://github.com/datahub-project/datahub)** | [![Stars](https://img.shields.io/github/stars/datahub-project/datahub?style=social&color=white)](https://github.com/datahub-project/datahub/stargazers) | Event-Driven Generalized Metadata | Apache-2.0 | Programmable, Kafka-powered event-driven architecture with 100+ connectors, column-level lineage at massive scale, GraphQL/REST/Avro APIs, and Context Intelligence for AI agents. |
| **[lakeFS](https://github.com/treeverse/lakeFS)** | [![Stars](https://img.shields.io/github/stars/treeverse/lakeFS?style=social&color=white)](https://github.com/treeverse/lakeFS/stargazers) | Data Lake Git-like Versioning & Metadata | Apache-2.0 | Git-like branching, committing, merging, and isolation metadata operations for cloud object storage (S3, GCS, Azure Blob, MinIO), preventing data swamp degradation. |
| **[CKAN](https://github.com/ckan/ckan)** | [![Stars](https://img.shields.io/github/stars/ckan/ckan?style=social&color=white)](https://github.com/ckan/ckan/stargazers) | Open Data Management Portal | AGPL-3.0 | The world's leading open-source data portal platform used by national, regional, and local governments and research institutions to publish and catalog open datasets. |
| **[Amundsen](https://github.com/amundsen-io/amundsen)** | [![Stars](https://img.shields.io/github/stars/amundsen-io/amundsen?style=social&color=white)](https://github.com/amundsen-io/amundsen/stargazers) | Search-First Discovery Platform | Apache-2.0 | Originally built at Lyft; lightweight search-engine-first architecture (Elasticsearch + Neo4j/Atlas) providing fast, Google-like discovery across enterprise tables and dashboards. |
| **[Unity Catalog OSS](https://github.com/unitycatalog/unitycatalog)** | [![Stars](https://img.shields.io/github/stars/unitycatalog/unitycatalog?style=social&color=white)](https://github.com/unitycatalog/unitycatalog/stargazers) | Multi-Engine Data & AI Governance | Apache-2.0 | Donated by Databricks to LF AI & Data; provides an open, vendor-neutral governance specification for tables, volumes, AI models, and functions with Iceberg REST catalog compatibility. |
| **[Apache Gravitino](https://github.com/apache/gravitino)** | [![Stars](https://img.shields.io/github/stars/apache/gravitino?style=social&color=white)](https://github.com/apache/gravitino/stargazers) | Federated Metalake Catalog Broker | Apache-2.0 | Federated metadata lake broker unifying multi-cloud data architectures behind a single hierarchical namespace (`catalog.schema.table`) fronting Iceberg, Hive, JDBC, and Glue backends. |
| **[OpenLineage](https://github.com/OpenLineage/OpenLineage)** | [![Stars](https://img.shields.io/github/stars/OpenLineage/OpenLineage?style=social&color=white)](https://github.com/OpenLineage/OpenLineage/stargazers) | Open Standard for Lineage Collection | Apache-2.0 | Standardized API framework and specification for collecting end-to-end data lineage metadata during job execution across Spark, Airflow, Flink, and dbt. |
| **[Marquez](https://github.com/MarquezProject/marquez)** | [![Stars](https://img.shields.io/github/stars/MarquezProject/marquez?style=social&color=white)](https://github.com/MarquezProject/marquez/stargazers) | Lineage Metadata Collection & Service | Apache-2.0 | The reference backend implementation for OpenLineage; records dataset lifecycle, runs, and job dependencies to render interactive lineage DAGs and track historical lineage shifts. |
| **[Apache Atlas](https://github.com/apache/atlas)** | [![Stars](https://img.shields.io/github/stars/apache/atlas?style=social&color=white)](https://github.com/apache/atlas/stargazers) | Enterprise Metadata & Governance | Apache-2.0 | Scalable metadata and governance platform tailored for big data ecosystems; integrates with Apache Ranger for tag-based security and tracks lineage for Hive, Spark, and Kafka. |
| **[Apache Polaris](https://github.com/apache/polaris)** | [![Stars](https://img.shields.io/github/stars/apache/polaris?style=social&color=white)](https://github.com/apache/polaris/stargazers) | Vendor-Neutral Iceberg REST Catalog | Apache-2.0 | Official Apache Top-Level Project (TLP) delivering an open-source, vendor-neutral implementation of the Apache Iceberg REST Catalog specification across multi-engine environments. |
| **[Dremio OSS](https://github.com/dremio/dremio-oss)** | [![Stars](https://img.shields.io/github/stars/dremio/dremio-oss?style=social&color=white)](https://github.com/dremio/dremio-oss/stargazers) | SQL Lakehouse Catalog & Engine | Apache-2.0 | Open-source SQL engine with integrated semantic metadata cataloging, automated reflections, and Iceberg lakehouse management. |
| **[ODD Platform](https://github.com/opendatadiscovery/odd-platform)** | [![Stars](https://img.shields.io/github/stars/opendatadiscovery/odd-platform?style=social&color=white)](https://github.com/opendatadiscovery/odd-platform/stargazers) | Open Data Discovery & Observability | Apache-2.0 | Open-source active metadata and discovery platform focusing on end-to-end lineage, ML model catalogs, and automated data quality alerts via open APIs. |
| **[Magda](https://github.com/magda-io/magda)** | [![Stars](https://img.shields.io/github/stars/magda-io/magda?style=social&color=white)](https://github.com/magda-io/magda/stargazers) | Federated Data Catalog System | Information Era / Apache-2.0 | Kubernetes-native federated data catalog system originally developed for the Australian government with automated metadata harvesting, authorization, and previewers. |

---

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing tabular and listing formats).
3. Include: name, link, specific pricing/limits or stars badge, and concise descriptions.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Data catalog platforms handling metadata and access policies must comply with applicable privacy regulations (GDPR, CCPA) and organizational governance policies; **permission models do not migrate cleanly between catalogs**—switching requires rebuilding the permission graph by hand, and a period where two systems both think they are authoritative is where incidents happen.
- **Open-source data catalogs are mature but require matching architecture to team capacity**—DataHub provides the most programmable option with the largest community but needs 7+ containers and dedicated infra attention; OpenMetadata provides a simpler three-service deployment with built-in quality; Polaris and Gravitino address Iceberg-native and federated needs respectively. For organizations with a single primary warehouse, native catalogs (Unity Catalog, Snowflake Horizon, AWS Glue) may cover most needs. Choose based on whether you need cross-platform stewardship or Iceberg-native catalog federation.
- Verify license terms for commercial use; most featured projects are licensed under Apache 2.0 or AGPL 3.0.

---

**Made for data governance leads, metadata architects, and organizations building trustworthy data foundations for AI.**  
Let's make data catalog and metadata management more open, but with clear eyes about the operational footprint and permission-migration costs that define each path.
