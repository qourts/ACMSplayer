# ACMS Player Portal v2.37 — ACMSplayer Root Deployment

GitHub Pages deployment package aligned with **ACMS Admin v4.56 — Root Index Deployment**.

## Qualification update (v2.36)
- Three-pool wildcard qualification first normalizes every Pool #2 candidate to the same counted match total, then ranks by **Normalized Win Rate → Normalized PQ**.
- Pool #2 candidates from larger pools have the result(s) against the lowest-ranked opponent(s) excluded until every candidate is compared over the same number of matches.
- The Player Portal displays the official record, normalized W/L, Normalized Win Rate, excluded match(es), normalized PE/PC/PQ, provisional/tied/qualified state, and the selected wildcard once determinable from published Match Control state.
- Official standings remain unchanged.
- Zero-loss **Twice-to-Beat** is surfaced for Semifinals using the Admin-published match/series fields.
- Twice-to-Beat series score, protected team, decider state, and advancement status are visible in Playoffs and match details.
- Existing Supabase live sync, sponsor assets, schedule color sync, Player Portal QR, Find My Matches, Live Courts, Hospital Championship, and responsive layouts are preserved.

## Tournament rules reflected
- 3 pools: each Pool #1 qualifies + one wildcard from the Pool #2 teams.
- Wildcard: normalize to the smallest pool size, then compare **Normalized Win Rate first**; use **Normalized PQ** only when Win Rate is tied. If both remain exactly tied, Tournament Director resolution is required.
- Semifinal Twice-to-Beat: only a team that finished all pool matches with **0 losses** receives the advantage.
- If the undefeated team loses the first semifinal match, the Admin portal creates a decider; medal advancement waits for the series result.

## Deploy
Upload the contents of this package directly to the root of the `ACMSplayer` GitHub repository.

Live Player Portal URL:
- `https://qourts.github.io/ACMSplayer/`

Expected root files/folders:
- `index.html`
- `acms-sync-config.json`
- `.nojekyll`
- `README.md`
- `assets/sponsors/`

## Sync requirement
For the new qualification and Twice-to-Beat displays to update live, publish tournament state from **Admin v4.56 or newer**.

## Security
The browser-safe Supabase publishable key remains in `acms-sync-config.json`. Do not add a Supabase secret/service-role key, database password, or the private ACMS publish key to the Player repository.

## v2.37 — Deployment URL update
- Player Portal canonical URL changed to `https://qourts.github.io/ACMSplayer/`.
- The clickable Player Portal QR target now uses the new repository URL.
- The embedded QR image was regenerated to encode the new URL.
- Existing v2.36 Normalized Win Rate → Normalized PQ wildcard logic is unchanged.
- Existing v2.35 Search Identity Reset behavior is unchanged.

## v2.35 — Search identity reset
- Clearing the visible **Find my matches** search field now also clears the saved player selection.
- The **YOU** badge and green team highlight disappear immediately when the search is blank.
- The cleared state is persisted, so the previous player is not silently restored after navigation or refresh.
- The same behavior applies to the shared player search rail and the Schedule player search.
