# catalog-products-api

AsyncAPI-first service repository for the Arcadia Editions product catalog
contracts.

## Contents

- [SUMMARY.md](./SUMMARY.md): bounded context description, scope, and main domain elements
- [CHANGELOG.md](./CHANGELOG.md): documentation change history for this repository
- [domain-model.zdl](./domain-model.zdl): source of truth for the product aggregate, lifecycle, and services
- [asyncapi.yml](./asyncapi.yml): AsyncAPI contract generated from the ZDL model
- [openapi.yml](./openapi.yml): HTTP API contract generated from the ZDL model
- [avro/](./avro/): Avro event schemas referenced by the AsyncAPI document
- [.github/workflows/provision-kafka.yml](./.github/workflows/provision-kafka.yml): workflow entrypoint for shared Kafka provisioning
- [scripts/README.md](../api-product-workflows/scripts/README.md): script-specific notes kept in the scripts folder
- [provision-kafka-local.sh](../api-product-workflows/scripts/provision-kafka-local.sh): local Git Bash helper for the generation flow

## Local usage

From Git Bash, after exporting the required Terraform and Confluent environment variables:

```bash
../api-product-workflows/scripts/provision-kafka-local.sh develop
```

To apply the generated Terraform locally:

```bash
APPLY_MODE=true ../api-product-workflows/scripts/provision-kafka-local.sh develop
```
