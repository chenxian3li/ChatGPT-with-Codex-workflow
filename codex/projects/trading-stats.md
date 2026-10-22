# Trading Stats agent rules

- Extracted from `chenxian3li/market-data` commit `c4541ac94c9dbafdbfaec1b3dd96877a36fdcdc2`.
- Independent Python 3.12/uv project; do not reintroduce Liquidity Snapshots or market_data Python imports.
- Source: read-only PostgreSQL `rc_dw.public`; preserve role audit, SELECT-only guard, UTC boundaries and complete-history/watermark validation.
- Target: **only** `rc_market.analytics`. Keep existing entity tables, PKs, names, signed fee/PnL and atomic publication; preserve `complete/partial/unverified` and emergency guards.
- Table and column DDL must retain Chinese comments. Migrations must be reviewed and explicit.
- No live DB writes, migrations, deployments, service restarts, pushes to other repos or PR merges without authorization. Production Linux operation is DevOps owned.
- Run unit tests and report integration tests skipped for missing credentials; never claim unrun tests passed.
