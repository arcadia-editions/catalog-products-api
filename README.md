# catalog-products-api

Product Catalog is the bounded context that defines what Arcadia Editions sells.
Using the same bounded-context lens as the architecture article, this service is
centered on the product definition itself: the commercial description, launch
readiness, and publication lifecycle of each release.

In the broader architecture this context answers questions such as:

- Which SKU exists and what does it represent?
- What name, description, price, and launch date should the business expose?
- Is an edition still a draft, already published, or retired?
- Is the edition quantity-tracked or serialized?

This repository contains the service-level specifications for the product catalog
contract and the events that announce when products become available or leave the
catalog.

## Bounded context scope

- Product creation and maintenance
- Publication and retirement lifecycle
- Ownership of catalog-facing product attributes
- Ownership of inventory tracking mode metadata

This service does not own reservation state or stock availability during checkout.
That belongs to Catalog Inventory.

## Contents

- `domain-model.zdl`: source of truth for the product aggregate, lifecycle, and services
- `asyncapi.yml`: AsyncAPI contract generated from the ZDL model
- `openapi.yml`: HTTP API contract generated from the ZDL model
- `avro/`: Avro event schemas referenced by the AsyncAPI document
- `scripts/README.md`: script-specific notes kept in the scripts folder
- `scripts/run-kafka-pipeline-local.sh`: local Git Bash helper for the generation flow

## Main domain elements

- `Product`: aggregate for the commercial definition of a release
- `ProductCatalogService`: commands for creating, updating, publishing, and retiring products
- `ProductPublished` and `ProductRetired`: events consumed by downstream contexts

## Local usage

From Git Bash, after exporting the required Terraform and Confluent environment variables:

```bash
./scripts/run-kafka-pipeline-local.sh develop
```

To apply the generated Terraform locally:

```bash
APPLY_MODE=true ./scripts/run-kafka-pipeline-local.sh develop
```
