# ACMS Player Portal v2.35 — Smart Qualification + Search Identity Reset

GitHub Pages deployment package aligned with **ACMS Admin v4.53 — Normalized Wildcard PQ**.

## Qualification update (v2.34)
- Three-pool wildcard qualification is shown using **Normalized PQ only**.
- Pool #2 candidates from larger pools have the result(s) against the lowest-ranked opponent(s) excluded until every candidate is compared over the same number of matches.
- The Player Portal displays official PQ, excluded match(es), normalized PE/PC/PQ, provisional/tied/qualified state, and the selected wildcard once determinable from published Match Control state.
- Official standings remain unchanged.
- Zero-loss **Twice-to-Beat** is surfaced for Semifinals using the Admin-published match/series fields.
- Twice-to-Beat series score, protected team, decider state, and advancement status are visible in Playoffs and match details.
- Existing Supabase live sync, sponsor assets, schedule color sync, Player Portal QR, Find My Matches, Live Courts, Hospital Championship, and responsive layouts are preserved.

## Tournament rules reflected
- 3 pools: each Pool #1 qualifies + one wildcard from the Pool #2 teams.
- Wildcard: normalize to the smallest pool size, then highest Normalized PQ. **No Win Rate comparison is used for the wildcard.**
- Semifinal Twice-to-Beat: only a team that finished all pool matches with **0 losses** receives the advantage.
- If the undefeated team loses the first semifinal match, the Admin portal creates a decider; medal advancement waits for the series result.

## Deploy
Upload the contents of this package directly to the root of the `ACMS_InterHospital` GitHub repository.

Expected root files/folders:
- `index.html`
- `acms-sync-config.json`
- `.nojekyll`
- `README.md`
- `assets/sponsors/`

## Sync requirement
For the new qualification and Twice-to-Beat displays to update live, publish tournament state from **Admin v4.53 or newer**.

## Security
The browser-safe Supabase publishable key remains in `acms-sync-config.json`. Do not add a Supabase secret/service-role key, database password, or the private ACMS publish key to the Player repository.

## v2.35 — Search identity reset
- Clearing the visible **Find my matches** search field now also clears the saved player selection.
- The **YOU** badge and green team highlight disappear immediately when the search is blank.
- The cleared state is persisted, so the previous player is not silently restored after navigation or refresh.
- The same behavior applies to the shared player search rail and the Schedule player search.
