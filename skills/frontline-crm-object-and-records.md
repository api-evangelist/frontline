---
name: Create a Frontline CRM object and load records
description: Define a CRM object, then create and query its records (rows).
api: openapi/frontline-openapi-original.yml
operations: [listObjects, createObject, getObjectSchema, createObjectRow, createObjectRowsBulk, listObjectRows, countObjectRows]
generated: '2026-07-19'
method: generated
---

# Create a Frontline CRM object and load records

Base URL `https://prod-api.getfrontline.ai/public/v1`. Send
`Authorization: Bearer <USER_API_KEY>` for writes.

## Steps

1. **Survey existing objects** — `listObjects` (`GET /public/v1/objects`) to see
   People/Companies/Deals and any custom objects before creating a new one.
2. **Create the object** — `createObject` (`POST /public/v1/objects`) with the
   object name and fields. A `409 conflict` means the name is taken.
3. **Inspect the schema** — `getObjectSchema` to confirm field ids/types before
   loading data.
4. **Add records** — `createObjectRow` for a single row, or `createObjectRowsBulk`
   to load many rows in one call (prefer bulk to stay under the rate limit).
5. **Read back** — `listObjectRows` with `page` / `page_size` (default 20) to
   paginate; `countObjectRows` for the total.

## Rules

- IDs are custom-prefixed cuid-style strings; pass them back verbatim.
- Validation failures return `400 bad_request` with `error.details.issues[]`
  (zod-style `path`/`message`/`code`); a reference to a missing id surfaces as
  issue `code: not_found`, and a cross-account reference as `wrong_owner`.
- Paginate rather than requesting everything; raise `page_size` within reason.
