# catalog-products-api

AsyncAPI-first service repository for the Arcadia Editions product catalog
contracts.

## Contents

- [SUMMARY.md](./SUMMARY.md): bounded context description, scope, and main domain elements
- `domain-model.zdl`: source of truth for the product aggregate, lifecycle, and services
- `asyncapi.yml`: AsyncAPI contract generated from the ZDL model
- `openapi.yml`: HTTP API contract generated from the ZDL model
- `avro/`: Avro event schemas referenced by the AsyncAPI document
- `scripts/README.md`: script-specific notes kept in the scripts folder
- `scripts/run-kafka-pipeline-local.sh`: local Git Bash helper for the generation flow

## Local usage

From Git Bash, after exporting the required Terraform and Confluent environment variables:

```bash
./scripts/run-kafka-pipeline-local.sh develop
```

To apply the generated Terraform locally:

```bash
APPLY_MODE=true ./scripts/run-kafka-pipeline-local.sh develop
```
