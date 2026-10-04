# Scanner Action qualification — 4 October 2026

This is a dated follow-up to [scanner kit v0.41.3](https://github.com/counterbranch/alpha-releases/releases/tag/v0.41.3). The release notes correctly state that Action acquisition and controlled pull-request acceptance were pending **at publication on 1 October 2026**. Subsequent Action qualification does not change the kit bytes or rewrite that history.

## Published kit

The immutable Linux x86-64 GNU kit contains Counterbranch 0.41.3 and Discovery 0.24.0. Its archive SHA-256 is `7b070d9d8df04eb5dd19e2af6089142f0c2c1d996edba5c740f192423ed49267` (9,757,266 bytes); the adjacent Sigstore bundle SHA-256 is `15fd3ebdd920ff695eebf52a424f2d29c5b619dddc5ff8009698464edd287bc1` (10,775 bytes). No scanner rebuild or replacement asset is required for Action comment or retention changes.

## Subsequent qualification

- The acquisition revision [`06d374155794a5cb7a202395d2321d8af419f187`](https://github.com/counterbranch/counterbranch-action/commit/06d374155794a5cb7a202395d2321d8af419f187) passed two automatic Ubuntu 24.04 pull-request runs using ordinary caller workflow credentials with `contents: read`. Both independently acquired the authenticated kit; missing-revision negative checks failed as expected. The authored fixtures retained externalized-policy uncertainty, so their complete results were `NEEDS_OWNER_REVIEW`, not `CLEAN`.
- On 3 October, Action [`dee759aff26ad7af445ba7ea74eae5c407041bd9`](https://github.com/counterbranch/counterbranch-action/commit/dee759aff26ad7af445ba7ea74eae5c407041bd9) passed controlled automatic pull-request checks for `CLEAN` and `INCOMPLETE`, opt-in comments and report bundles. Failure results remained `UNKNOWN`; comment updates retained the same comment identity. Read-only comment permission failed with HTTP 403, and disabled delivery remained disabled. These runs used the previous one-day retention request.

These results were recorded in controlled maintainer qualification. They do not qualify later Action changes. Final qualification of the configurable-retention Action and a public installation demonstration remain pending; this record must be updated with their exact revision, public run links and observed results before advertising them as qualified.

## Scope and limits

The scanner compares advisory static source evidence between exact Git revisions. It does not execute an application, determine intended permissions, establish runtime access, or prove exploitability. Synthetic outcomes do not establish exhaustive framework coverage or compatibility with arbitrary repositories. `CLEAN` applies to the scanned and modelled scope; inspect incomplete reasons and unmodelled evidence.

Comment delivery is opt-in and supports same-repository `pull_request` events. Fork comment delivery is unsupported. One publisher workflow per PR must use the documented shared concurrency group; calls within a run must also be sequential. `INCOMPLETE`, `UNKNOWN`, and upload or comment delivery failures need follow-up.

Report ZIPs may contain source excerpts. GitHub's web download requires [GitHub sign-in and repository read access](https://docs.github.com/en/actions/how-tos/manage-workflow-runs/download-workflow-artifacts). Requested retention is subject to repository and organization limits or earlier deletion. Essential findings remain in the comment after a ZIP expires.
