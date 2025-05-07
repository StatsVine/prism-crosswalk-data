# PRISM Crosswalk Data

**PRISM (Player Record Identity Standard Mapping)** provides a registry of player identity mappings across major sports data providers. It aims to standardize the messy, inconsistent world of player identity across sports and data providers. By maintaining a clean core dataset, we enable better interoperability for developers, researchers, and sports data enthusiasts. By using automation and strict validation, we can provide timely updates to player data.

Learn more about the full PRISM ecosystem (including the richer roster dataset and tooling for the data repos) at [prism-tools](https://github.com/statsvine/prism-tools). 

This repository contains the authoritative crosswalk/index data and schema files for each sport, designed for clarity, maintainability, and open collaboration.

Tools and other data formats/artifacts are kept in the [prism-tools](https://github.com/statsvine/prism-tools) repo.

## Overview
This repo is the foundational dataset for player identity mappings, acting as the source of truth for standardized player IDs across various sports data sources. This repository contains a minimal, static cross-reference dataset with primarily player identifiers (IDs)  — without performance stats or dynamic team data. It serves as the starting point for adding new players, linking additional data sources, and ensuring consistent player identity mappings. By focusing exclusively on player identity, prism-crosswalk-data provides a reliable, simple foundation for downstream tools and integrations that require consistent cross-data-source player information.

### Philosophy
- **Source of truth**: Strict, flat CSV files — one file per sport/league.
- **Identifiers only**: Focus purely on stable identifiers (where possible!) for players. No team affiliations, injury statuses, or dynamic data is included in the primary source. Metadata is not intended to be authoritative, and is used only for ease of editing.
- **Stable schema**: The schema should remain stable over time, with changes only made when absolutely necessary. This ensures consistent mappings and minimal disruption to downstream systems.
- **Stable data**: Updates to existing player records should be infrequent, primarily limited to incorporating new data sources. New players added as needed.
- **Editing workflows**: Manual edits via pull requests, or assisted edits via Google Sheets.

### Why This Exists
- **Inconsistent player IDs**: Player IDs are often inconsistent across different sports data sources, making it difficult to merge data reliably.
- **Lack of cross-sport solutions**: While there are sports-specific data sources, there is no unified solution for cross-sport player identity mapping.
- **Existing solutions aren't collaborative**: Many existing solutions are closed or lack open collaboration, limiting contributions and improvements.
- **Automation flexibility**: Provides flexibility in data formats, allowing for easier automation and integration with downstream systems.

### Who this is for
If you already have detailed player metadata and are dealing with player identity mismatches across sources:

- **Data Engineers** needing consistent player IDs for their pipelines.
- **Sports Data Enthusiasts** cross-referencing player data.
- **API Builders** integrating player identity mappings into their APIs.
- **Researchers** analyzing player data across sources.
- **App Developers** building sports apps that require consistent player identifiers.

### Who this isn't for
- This repo is a low-level dataset focused on player identity mapping and is generally used for merging and reconciling data from different sources. If you need more detailed player data, we suggest using prism-registry instead, which has richer metadata.
- Historical data is limited: As of now, PRISM primarily focuses on active players and does not provide extensive historical player data.

## Scope
- Currently this covers fantasy-relevant players for the current MLB season, which is mostly a subset of the 25/40-man rosters.

## Roadmap / Future Plans

- **Primary development priorities**:
  - Correction and cleanup of existing player data.
  - Addition of new players for the current in-progress seasons.
  - Expansion to additional major sports leagues.

- **Player focus**:
  - Current focus is current players.
  - Historical/backfill data will be added as time permits, but is not a major short-term priority.

- **Planned sports coverage**:
  - Currently: **MLB** (baseball).
  - Near future: **NFL** (football), **NBA** (basketball).
  - Not currently prioritized: **NHL** (hockey), other sports.

If you'd like to contribute new players, corrections, or new data sources, check out the Contribution section below!

## Repository Structure
- `/data/`
  - Primary source-of-truth CSV files organized by league.
- `/schema/`
  - Contains the schema files for the player files.
- `/ATTRIBUTION.md`
  - Attribution information for upstream sources.
- `/LICENSE`
  - Open data license information.
- `/README.md`
  - Project overview, philosophy, and contribution guidelines (this file)

## Attribution

PRISM Crosswalk stands on the shoulders of giants and builds on open community data projects, including:

- MLB: 
    - [Chadwick Bureau / Register](https://github.com/chadwickbureau/register) (Open Data Commons Attribution License)
    - [SmartFantasyBaseball's Player ID Map](https://www.smartfantasybaseball.com/tools/)

We thank these projects for providing foundational sports research resources.

## License
- Data and schemas in this repo are licensed under the [Open Data Commons Attribution License (ODC-By 1.0)](https://opendatacommons.org/licenses/by/1-0/).
- Any code is licensed under MIT.

## Contributing

Pull requests are welcome!

### We especially welcome:
- Corrections to existing mappings.
- Additions of new players or ID mappings, especially for active players. Historical players also welcome.
- Additional ID sources (where appropriate). Suggest opening up a discussion item before any major work is conducted, as inclusion criteria is currently very subjective.

### Pull Requests Likely to Be Rejected:
- **Changes to the schema**: The schema is intended to be stable and relatively straightforward; and changes will only be considered in exceptional cases. Stability is key to maintaining consistent outputs and minimizing downstream disruptions.
- **Addition of extra metadata**: This project is strictly focused on mapping player identities across data sources. Adding performance data, team affiliations, injuries, or other dynamic metadata is out of scope. The included metadata (such as player names and birth dates) exists purely to aid in accurate ID matching.

When in doubt, open an issue to discuss your proposed change before submitting a PR.