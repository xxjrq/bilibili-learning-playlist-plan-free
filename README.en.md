# Bilibili Playlist Learning Plan

Turn visible items in an accessible Bilibili playlist or favorites list into a goal-led viewing order and daily time budget. The result keeps each visible source, description, duration, and missing field; titles are never treated as proof of the video content.

## Input and result

Provide a playlist/favorites URL, learning goal, daily minutes, and a user-selected `browserId`. The Skill returns up to 100 ordered items with visible metadata, source URL, matching rationale, missing-field markers, and a daily plan. It stops for unauthorized private lists, login, CAPTCHA, or risk controls; unavailable durations remain unknown and are excluded from time totals.

## Install

```bash
npx skills add xxjrq/bilibili-learning-playlist-plan-free
```

This browser Skill requires [Easy WebBridge on GitHub](https://github.com/xxjrq/easy-webbridge), with [Gitee](https://gitee.com/xxjrq/easy-webbridge) as a mirror. It uses one user-selected browser and an owned task session only; it never broadcasts across accounts or takes over existing tabs. Default mode is read-only.

## Offline self-test

```bash
node scripts/self-test.mjs
```

Fixtures are offline page-data simulations, not claims of live collection.

## Attribution

Business-purpose references: [OpenCLI](https://github.com/jackwener/OpenCLI) and its [Bilibili adapter](https://github.com/jackwener/OpenCLI/blob/main/docs/adapters/browser/bilibili.md). This repository is original and does not copy their implementation or prose. See [LICENSE](LICENSE).

## Offline success and failure fixtures

[Success input](fixtures/visible-success.json) → [actual script result](fixtures/success-output.md); [failure input](fixtures/failure-private-unauthorized.json) → [actual rejection](fixtures/failure-output.md). The failure input is an unchanged copy under an explicit failure filename. These are offline simulations, not live browser results.

## Mutually exclusive duration fields

Supply either `visibleMinutes` or `visibleDuration` for each item. Providing both is rejected even when equivalent or one is null. [Single-field success input](fixtures/success-duration-exclusive.json) → [actual plan](fixtures/success-duration-exclusive-output.md). [Equal values](fixtures/failure-duration-equal.json), [conflicting values](fixtures/failure-duration-conflicting.json), and [null plus clock](fixtures/failure-duration-null.json) must all be rejected. These are offline tests.
