# PRISM Crosswalk Data

**PRISM (Player Record Identity Standard Mapping)** provides a registry of player identity mappings across major sports data providers. It aims to standardize the messy, inconsistent world of player identity across sports and data providers. By maintaining a clean core dataset, we enable better interoperability for developers, researchers, and sports data enthusiasts. Automated daily checks cross-reference the data against multiple independent sources to keep it complete and up-to-date.

This repository is the **source data** — the authoritative CSV files and schema. Most consumers should use one of the derivative artifacts below.

## Using the Data

| What you want | Where to go |
|---|---|
| Browse or query player IDs via JSON | [crosswalk.prism.statsvine.com](https://crosswalk.prism.statsvine.com) |
| Consume the data in CSV or other structured formats | [github.com/StatsVine/prism-crosswalk](https://github.com/StatsVine/prism-crosswalk) (build artifacts) |
| Richer player metadata: names, rosters, etc. | [registry.prism.statsvine.com](https://registry.prism.statsvine.com) or [github.com/StatsVine/prism-registry](https://github.com/StatsVine/prism-registry) |
| Contribute data or fix mappings | You're in the right place — read on |

## Philosophy
- **Source of truth**: Strict, flat CSV files — one file per sport/league.
- **Identifiers only**: Focus purely on stable identifiers (where possible!) for players. No team affiliations, injury statuses, or dynamic data is included in the primary source. Metadata is not intended to be authoritative, and is used only for ease of editing.
- **Stable schema**: The schema should remain stable over time, with changes only made when absolutely necessary. This ensures consistent mappings and minimal disruption to downstream systems.
- **Stable data**: Updates to existing player records should be infrequent, primarily limited to incorporating new data sources. New players added as needed.
- **Editing workflows**: Manual edits via pull requests, or assisted edits via Google Sheets.

## Why This Exists
- **Inconsistent player IDs**: Player IDs are often inconsistent across different sports data sources, making it difficult to merge data reliably.
- **Lack of cross-sport solutions**: While there are sports-specific data sources, there is no unified solution for cross-sport player identity mapping.
- **Existing solutions aren't collaborative**: Many existing solutions are closed or lack open collaboration, limiting contributions and improvements.

## Who this is for
If you're working with player data from multiple sources and need a reliable way to join them:

- **Data Engineers** needing consistent player IDs for their pipelines.
- **Sports Data Enthusiasts** cross-referencing player data.
- **API Builders** integrating player identity mappings into their APIs.
- **Researchers** analyzing player data across sources.
- **App Developers** building sports apps that require consistent player identifiers.

## Who this isn't for
- **Need richer metadata?** This dataset is IDs only. For names, rosters, and team affiliations, see [prism-registry](https://github.com/StatsVine/prism-registry) and its [JSON pages](https://registry.prism.statsvine.com), which are built from this dataset.
- **Need historical data?** Coverage is focused on current and recent players. Extensive historical backfill is not a near-term priority.

## Scope

Currently **MLB only** (~1,700+ players). Coverage includes all players who appeared on a 40-man roster during the 2025 or 2026 seasons, with ongoing tracking of active players as rosters change.

See [`schema/schema.md`](schema/schema.md) for field definitions, validation rules, and source details.

## Data Quality & Automation

A suite of automated checks runs daily to keep the dataset complete and accurate, cross-referencing against multiple independent sources:

- **MLB 40-man rosters** — flags players on active rosters who are missing from the dataset
- **Chadwick Bureau register** — cross-references against the community baseball register
- **SmartFantasyBaseball** — validates ID mappings against the SFBB player ID map
- **FanGraphs** (in-season) — detects ID redirects that indicate minor-league-to-MLB promotions

This gives us fast detection of missing players and stale mappings as they happen.

## Roadmap

- **Primary development priorities**:
  - Correction and cleanup of existing player data.
  - Addition of new players for the current in-progress seasons.
  - Expansion to additional major sports leagues.

- **Player focus**: Active/current players first. Historical backfill will be added as time permits.

- **Planned sports coverage**:
  - Currently: **MLB** (baseball).
  - Near future: **NFL** (football), **NBA** (basketball).
  - Not currently prioritized: **NHL** (hockey), other sports.

## Repository Structure

- `/data/` — source-of-truth CSV files, organized by sport/league
- `/schema/` — schema definitions and validation rules (see [`schema/schema.md`](schema/schema.md))
- `/.validation/` — suppression lists for known ID discrepancies (SFBB, Chadwick)
- `/ATTRIBUTION.md` — upstream source credits
- `/LICENSE` — open data license

## Attribution

PRISM Crosswalk stands on the shoulders of giants and builds on open community data projects, including:

- MLB:
  - [Chadwick Bureau / Register](https://github.com/chadwickbureau/register) (Open Data Commons Attribution License)
  - [SmartFantasyBaseball's Player ID Map](https://www.smartfantasybaseball.com/tools/)

## License
- Data and schemas in this repo are licensed under the [Open Data Commons Attribution License (ODC-By 1.0)](https://opendatacommons.org/licenses/by/1-0/).
- Any code is licensed under MIT.

## Contributing

Pull requests are welcome!

### We especially welcome:
- Corrections to existing mappings.
- Additions of new players or ID mappings, especially for active players. Historical players also welcome.
- Additional ID sources (where appropriate). Open a discussion issue first — inclusion criteria is subjective and worth aligning on before doing the work.

### Pull Requests Likely to Be Rejected:
- **Changes to the schema**: The schema is intended to be stable and relatively straightforward, and changes will only be considered in exceptional cases. Stability is key to maintaining consistent outputs and minimizing downstream disruptions.
- **Addition of extra metadata**: This project is strictly focused on mapping player identities across data sources. Adding performance data, team affiliations, injuries, or other dynamic metadata is out of scope. The included metadata (such as player names and birth dates) exists purely to aid in accurate ID matching.

When in doubt, open an issue to discuss your proposed change before submitting a PR.