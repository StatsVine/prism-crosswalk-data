Attribution
===================

This project (prism-crosswalk-data) aggregates data from multiple open and community-driven public sources.
In addition to the sites referenced, we acknowledge and thank the following projects and organizations for their contributions:

⚾ MLB

- **Chadwick Bureau - Register**
  - Source: https://github.com/chadwickbureau/register
  - License: Open Data Commons Attribution License (ODC-By) v1.0
  - Notes: Used for player identity matching, birthdate information, and foundational record linkage.

- **Smart Fantasy Baseball - Player ID Map**
  - Source: https://smartfantasybaseball.com/tools/playerid-map/
  - Notes: Used for supplemental ID mappings across fantasy platforms and MLB data providers.

---

🏈 Football (NFL)

- **nflverse - nflverse-data**
  - Source: https://github.com/nflverse/nflverse-data
  - License: Creative Commons Attribution 4.0 International (CC BY 4.0)
  - Notes: Used for player identity matching, birthdate information, and foundational record linkage.

- **DynastyProcess - Player IDs**
  - Source: https://github.com/dynastyprocess/data
  - License: GNU General Public License v3.0
  - Notes: Used for supplemental ID mappings across fantasy platforms and NFL data providers.

- **Sleeper - Players API**
  - Source: https://docs.sleeper.com/
  - Notes: Used for supplemental ID mappings across fantasy platforms. Consumed via
    our own daily snapshot at https://github.com/statsvine/data-snapshots rather than
    called directly — the docs ask that the players endpoint be pulled at most once
    a day.

- **ffb_ids - Fantasy Football Player IDs**
  - Source: https://github.com/mayscopeland/ffb_ids
  - License: None declared upstream
  - Notes: Used to cross-check the ids it shares with us -- espn, nffc, sleeper and
    yahoo -- and the only upstream map we have found for nffc_id. Consulted as a
    validation source only; no values are imported from it in bulk while its
    licensing is unstated.

- **Wikidata**
  - Source: https://www.wikidata.org/
  - License: Creative Commons CC0 1.0 Universal (public domain dedication)
  - Notes: Used for cross-sport hub identifiers and supplemental record linkage.

🏀 Basketball (NBA)
- *Attribution pending — no external data currently included.*

🏒 Hockey (NHL)
- *Attribution pending — no external data currently included.*

---

General Notes:
- Wherever possible, contributions to this project aim to respect original licenses and terms of use.
- This project does not redistribute raw source data in bulk, only normalized cross-reference mappings.