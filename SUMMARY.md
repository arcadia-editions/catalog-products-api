# Product Catalog

## Description

Product Catalog is the bounded context that defines what Arcadia Editions sells.
It owns the commercial identity of each release, including the SKU, description,
pricing, edition size, launch readiness, and publication lifecycle.

It tells the rest of the platform what exists in the catalog, while leaving stock
reservation and scarcity control to Catalog Inventory.

## Scope

- Create and maintain product definitions
- Manage publication and retirement lifecycle
- Own catalog-facing product attributes such as title, description, price, and launch date
- Define inventory tracking mode metadata for each release

## Main domain elements

- `Product`: aggregate for the commercial definition of a release
- `ProductCatalogService`: commands for creating, updating, publishing, and retiring products
- `ProductPublished`: event announcing a release is available to downstream contexts
- `ProductRetired`: event announcing a release is no longer active in the catalog
