# catalog-products-api

AsyncAPI-first service repository for the Arcadia Editions catalog and product event contract.

This repository contains the service-level specifications used by the shared pipeline to generate Kafka and Schema Registry Terraform for Confluent Cloud.

## Contents

- `asyncapi.yml`: main AsyncAPI contract
- `avro/`: Avro schemas referenced by the AsyncAPI document
- `openapi.yml`: HTTP API contract
- `domain-model.zdl`: domain model source
- `.github/workflows/provision-kafka.yml`: thin workflow that delegates to `asyncapi-ops-pipelines`
- `scripts/run-kafka-pipeline-local.sh`: local Git Bash helper for the same generate and Terraform flow

## Local usage

From Git Bash, after exporting the required Terraform and Confluent environment variables:

```bash
./scripts/run-kafka-pipeline-local.sh develop
```

To apply the generated Terraform locally:

```bash
APPLY_MODE=true ./scripts/run-kafka-pipeline-local.sh develop
```
