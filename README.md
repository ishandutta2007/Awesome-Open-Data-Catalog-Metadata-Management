# Awesome-Open-Data-Catalog-Metadata-Management

# Top Open Data Catalog & Metadata Management Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Metadata Discovery, Data Lineage & Self-Hosted Catalog Platforms*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Open Data Catalog & Metadata Management**. These tools enable organizations to discover, understand, and govern data assets across heterogeneous systems—providing a searchable inventory of tables, dashboards, pipelines, and models with lineage, ownership, and classification that make data trustworthy and AI-ready.

**Examples** include Snowflake Open Catalog, Apache Polaris, Unity Catalog Open Source, Amundsen, DataHub (Acryl Data), Marquez, OpenMetadata, AWS Glue Data Catalog, Google Cloud Dataplex Catalog, and Alation (the category leaders).

**Open-source emphasis**: Open Data Catalog & Metadata Management is a domain where open-source tooling is **genuinely mature and production-proven at the catalog layer**, with clear leaders for different architectural philosophies. **DataHub** is the most programmable and community-adopted option—built at LinkedIn, event-driven via Kafka, with the largest open-source community (16,000+ active members, 3M+ monthly downloads) and validated at 2M+ assets in production . **OpenMetadata** is the most architecturally simple all-in-one platform—three services for production deployment, with metadata, data quality, profiling, and governance in a single schema-defined system . The critical caveat: **for Iceberg-native lakehouses, the catalog landscape is different**—**Apache Polaris** provides the vendor-neutral REST catalog standard (Apache TLP since February 2026) , while **Apache Gravitino** federates heterogeneous catalogs (Glue, Hive, JDBC) behind a unified metalake namespace . For organizations already on a single warehouse, **native catalogs** (Unity Catalog, Snowflake Horizon, AWS Glue) may cover most needs, making a standalone catalog optional .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Snowflake Open Catalog](https://www.snowflake.com/)**  
  Snowflake's managed Iceberg REST catalog and governance layer; enables multi-engine access to Iceberg tables with Snowflake's security and policy enforcement.

- **[AWS Glue Data Catalog](https://aws.amazon.com/glue/)**  
  AWS's managed metadata catalog with native Iceberg REST endpoint (`glue.us-east-1.amazonaws.com/iceberg`, SigV4-signed) . Integrated with Athena, EMR, Redshift Spectrum, and Lake Formation for governance. **Best for AWS-native data estates**—but catalog-level federation with non-AWS engines requires additional configuration.

- **[Google Cloud Dataplex Catalog](https://cloud.google.com/dataplex)**  
  Google Cloud's built-in catalog (renamed from Dataplex Universal Catalog to **Knowledge Catalog on April 10, 2026**) . Automatic metadata from BigQuery, Cloud SQL, Spanner, Bigtable, Pub/Sub, and Vertex AI; column-level lineage via built-in integrations; quality scans, glossary, and natural-language search in the same console . **Best for BigQuery-centric organizations** wanting a working catalog without buying anything new .

- **[Alation](https://www.alation.com/)**  
  The incumbent that defined the data catalog category (founded 2012, first product 2015); behavioral search, deep governance (policy center, classification, masking workflows), strong cross-system column-level lineage, and hybrid/customer-managed deployment options . **Best for large enterprises with a formal governance function** (CDO, stewards, glossary programme)—but it is proprietary SaaS with no free tier and contact-sales pricing .

- **[Unity Catalog (Databricks)](https://www.databricks.com/)**  
  Databricks' native catalog for data and AI assets; **open-sourced in June 2024** and donated to LF AI & Data as a sandbox project. Manages tables, volumes, and models with Iceberg REST API compatibility and credential vending . **Best for Databricks-centric organizations**—but the open-source version is infrastructure-layer, not a full stewardship platform.

- **[Snowflake Horizon](https://www.snowflake.com/)**  
  Snowflake's native governance layer for discovery, classification, and policy enforcement within Snowflake; **optional for organizations already on Snowflake** since native governance covers many needs .

## Open-Source GitHub Projects

### General-Purpose Metadata Catalogs (DataHub, OpenMetadata)

- **[DataHub](https://github.com/datahub-project/datahub)**  
  The **most programmable and community-adopted open-source metadata platform** (Apache 2.0) . Architecture: **event-driven** (Kafka for metadata change events), **graph store** (Neo4j or MySQL) for lineage traversal, Elasticsearch for search, GMS (Generalized Metadata Service) as the API layer . Features: **100+ connectors** (Snowflake, BigQuery, dbt, Airflow, Looker, Iceberg) ; **column-level lineage** matured at LinkedIn scale; GraphQL + REST + Avro APIs; **Context Intelligence** for AI agents (SQL query history as semantic anchors, conflict detection, native evals) . **Community**: 16,000+ active members, 3M+ monthly downloads, production at Netflix, Apple, Visa, CVS Health . **Managed**: Acryl Cloud (~$20k/year) removes operational burden . **Caveats**: **7+ containers minimum** (Kafka, Elasticsearch, graph store, relational store, GMS, frontend, consumers)—10+ with schema registry and monitoring; requires a dedicated infra person for the first quarter . **Best for teams wanting a programmable, event-driven catalog** with the broadest connector coverage and AI-agent context—if you have the operational capacity.

- **[OpenMetadata](https://github.com/open-metadata/OpenMetadata)**  
  The **most architecturally simple all-in-one open-source catalog** (Apache 2.0) . Architecture: **one Java server** (API, ingestion coordination, event processing), **one relational store** (MySQL/PostgreSQL), **Elasticsearch/OpenSearch** — **three services for production** (Airflow optional) . Features: **schema-first** model (JSON Schema defines every entity; API, ingestion, UI generated); **50+ connectors** (growing fast); column-level lineage; **data quality** with automated checks, no-code profiling, and **data contracts** (machine-readable schema and quality guarantees enforced automatically) ; classification and glossary . **Caveats**: **smaller community** (~3.4K GitHub stars vs DataHub's 8.8K+) and fewer connectors than DataHub; advanced features less mature . **Best for teams wanting a unified catalog + quality + governance platform** with minimal operational overhead—"I had OpenMetadata running with real Snowflake ingestion in under two hours" .

### Iceberg-Native Catalogs (Polaris, Gravitino)

- **[Apache Polaris](https://github.com/apache/polaris)**  
  The **vendor-neutral Iceberg REST Catalog implementation** (Apache 2.0, Apache TLP since February 2026) . Provides a standard REST API for Iceberg catalog operations, enabling any compatible engine (Spark, Trino, Flink, Snowflake, Databricks) to access tables without proprietary lock-in . **Key capability**: **federation**—put Polaris in front of an existing Hive Metastore and clients connect to a single endpoint while the catalog resolves namespaces to backing stores . **Caveats**: **permission graphs do not migrate**—Polaris uses principals, principal roles, catalog roles, and privileges; switching from Glue (IAM/Lake Formation) or Hive requires rebuilding grants by hand . **Best for Iceberg-focused multi-engine environments** wanting a neutral catalog standard—not a full stewardship platform with lineage and quality .

- **[Apache Gravitino](https://github.com/apache/gravitino)**  
  The **federated metadata lake (metalake) broker** (Apache 2.0) . Organizes metadata into a metalake providing `catalog.schema.table` namespace, fronting multiple Iceberg backends (**Hive, JDBC, REST, Glue**) behind a single Iceberg REST service . Features: **nested multi-level namespaces**, **vended-credential refresh**, **geo-distributed deployments** (local REST service proxies to remote) . **Best for organizations with many catalogs and engines** needing one logical hierarchy—especially when cross-region latency is the constraint . **Caveat**: a broker in front of Unity Catalog still cannot run maintenance on UC managed tables; the backing catalog still owns the pointer .

### Data Lineage & Observability (Marquez, Amundsen)

- **[Marquez](https://github.com/MarquezProject/marquez)**  
  Open-source **metadata service for data lineage** (Apache 2.0) from the OpenLineage project; collects lineage metadata from Airflow, Spark, dbt, and other tools; provides a searchable graph of dataset and job relationships . **Best for teams wanting dedicated lineage** without a full catalog—pairs well with a catalog for discovery. **Verify current maintenance status** and integration depth before adoption .

- **[Amundsen](https://github.com/amundsen-io/amundsen)**  
  Open-source data discovery platform (Apache 2.0) originally from Lyft; **search-engine-first architecture** for fast table search at scale . **Critical limitation**: default ingestion is **table-level metadata only**—column-level lineage and statistics require custom ingestion plugins . **Best for large-scale table search** where column depth is not required.

### Additional Strong Open-Source Options

- **Apache Atlas** — Open-source metadata and governance for Hadoop ecosystems (Apache 2.0); tag-based access control via Ranger, lineage for Hive/Spark . **Best for Hadoop-centric organizations**—but its HBase/Solr dependencies are a burden if you don't already run Hadoop .
- **CKAN** — Open-source data portal for publishing and discovering open data (AGPL); government and research focus rather than enterprise metadata management.
- **Magda** — Open-source data catalog (Australian government origin) with federation capabilities; **verify maintenance status** before adoption .

**Frameworks for building custom systems**: For a **programmable, event-driven catalog with the broadest connectors and AI-agent context**, DataHub (accepting 7+ container operational burden) . For a **unified catalog + quality + governance platform with minimal overhead**, OpenMetadata (accepting smaller community) . For an **Iceberg-native neutral REST catalog**, Apache Polaris (rebuilding permission graphs) . For **federating heterogeneous catalogs behind one namespace**, Apache Gravitino . **For single-warehouse organizations**, native catalogs (Unity Catalog, Snowflake Horizon, AWS Glue) may cover most needs—a standalone catalog is often optional .

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Data catalog platforms handling metadata and access policies must comply with applicable privacy regulations (GDPR, CCPA) and organizational governance policies; **permission models do not migrate cleanly between catalogs**—switching requires rebuilding the permission graph by hand, and a period where two systems both think they are authoritative is where incidents happen .
- **Open-source data catalogs are mature but require matching architecture to team capacity**—DataHub provides the most programmable option with the largest community but needs 7+ containers and dedicated infra attention ; OpenMetadata provides a simpler three-service deployment with built-in quality but a smaller ecosystem ; Polaris and Gravitino address Iceberg-native and federated needs respectively. **For organizations with a single primary warehouse**, native catalogs (Unity Catalog, Snowflake Horizon, Glue) may be sufficient—a standalone catalog is often optional . Choose based on whether you need cross-platform stewardship (DataHub, OpenMetadata) or Iceberg-native catalog federation (Polaris, Gravitino).
- Verify license terms for commercial use; DataHub, OpenMetadata, Polaris, Gravitino, Marquez, Amundsen, and Atlas all use Apache 2.0 .

---

**Made for data governance leads, metadata architects, and organizations building trustworthy data foundations for AI.**  
Let's make data catalog and metadata management more open, but with clear eyes about the operational footprint and permission-migration costs that define each path.
