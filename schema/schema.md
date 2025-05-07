# PRISM Player Crosswalk Schema Overview

This document outlines the structure of the CSV player data file and the validation rules. The schema is divided into two parts:
- **Core Schema**: This defines the fundamental player-related fields common to all sports.
- **Sport-Specific Schema**: This defines the sport-specific fields and any overrides to the core schema. Each sport will have a corresponding league-specific schema stored in the `schema/leagues/{league}/sources.yaml` directory.

## Key points
- The core schema is generic and shared across all sports/leagues.
- The sport-specific schema (in `leagues/{league}/sources.yaml`) allows each sport to have its own custom ID fields.
- Validation of data is done by loading both schemas and checking the data against the rules defined.
- The schema structure is extensible to accommodate new sports and data sources easily.

## Schemas
### Core Schema
The core player schema, found in the `players.yaml`, defines the essential fields for all players, regardless of sport or league. This schema is designed to ensure that there is a consistent identity for each player across different sports data sources.

### League-specific Schemas
Each sport will have its own specific sources that define the _id fields in each league file. These sport-specific schemas are stored in `leagues/{league}/sources.yaml`.

## Data Guidelines
### Rules
- **prism_id** must be globally unique across all sports.
- Missing external IDs (e.g., if a player isn't mapped yet) should be empty (``, no `"NULL"`).
- Line endings must be be UNIX (`\n`). UTF-8 encoding.

### Notes
- New external ID columns can be added in the future with versioning.
- While prism_id is deterministic, it should be considered opaque and subject to change for future entries.
- The schema is stable, and changes to the column structure will only occur if absolutely necessary. Stability is a priority to avoid breaking downstream consumers of the data.
- Metadata column order is NOT guaranteed but should be generally in the same order. ID column order is NOT guaranteed and the columns MAY be-reordered when new sources are added.
– Row order is guaranteed to be ordered by prism_id; row numbers must NOT be treated as stable identifiers.
- Additional fields are intentionally excluded to keep the identity dataset simple. This repository should focus on player identity and avoid storing large amounts of additional metadata.
- Updates to existing players should be rare, and limited primarily to adding new data sources or correcting erroneous data.
- Identifying metadata (name, birth info, etc.) is only used for player identification, and should not be considered stable nor authoritative.

### Validation Expectations
- `prism_id` MUST be globally unique.
- ids within a given data source SHOULD be unique.
- Rows must be sorted by prism_id.
- Fields marked as optional provided on a best-effort basis, usually only if needed for disambiguation.