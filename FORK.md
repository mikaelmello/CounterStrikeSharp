# Fork release v1.0.380-fix.1

Upstream v1.0.380 with one difference: `libraries/hl2sdk-cs2` points at
mikaelmello/s2sdk `release/cs2-1.42.0.1`, which is the SDK commit v1.0.380 builds on
(alliedmodders/s2sdk a508eb5) plus alliedmodders/s2sdk#128.

Why: CS2 1.42.0.1 (build 26879581, server version 2000950) inserted one virtual into
`ISource2Server` after `GameCreateNetworkStringTables`. v1.0.380 compiles the old slots, so its
`GameFrame` hook sits on `ApplyGameSettings(KeyValues *)` and the server crashes at map load
(roflmuffin/CounterStrikeSharp#1502).

The publish workflow change lets a `v*` tag on this fork create the release with the upstream
asset names.

Exit: an upstream release whose `libraries/hl2sdk-cs2` contains alliedmodders/s2sdk#128 (or an
equivalent change).
