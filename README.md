# Calendar App — Mobile

## Template copy

This repo is one of the name-substituted Expo SDK 53 / Expo Router template
copies in the `bookchaowalit-mobile` org. The canonical template is
[`bookchaowalit-mobile/community-hub-mobile`](https://github.com/bookchaowalit-mobile/community-hub-mobile).
Consolidating or archiving this copy is pending owner decision D5 (BD-033); see
`repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md` in solo-empire.
This copy keeps its own code and its own copy of the CI workflow (no shared package).

React Native mobile app (Expo) for **Calendar App**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Tech Stack

- **Framework:** Expo SDK 53 + Expo Router
- **Language:** TypeScript
- **Navigation:** Expo Router (file-based)
- **UI:** React Native + Ionicons

## Features

- **Month view** (home tab): six-week grid with previous/next month
  navigation, today highlighted and a dot on days that have events.
- **Day agenda**: tap a day to see its events (all-day first, then by time)
  and delete them.
- **Add events** with a title and optional 24-hour `HH:MM` time; input is
  validated.
- Events live in memory for now (`lib/calendar.ts` holds the pure logic);
  on-device persistence is the next backlog item.

## Getting Started

```bash
npm ci
npx expo start
```

## Validation

```bash
npm run validate   # expo lint + tsc --noEmit + vitest
npx expo export --platform android --output-dir dist   # bundle smoke check
```

Pure logic lives in `lib/` and is unit-tested with Vitest (`lib/*.test.ts`).
CI (`.github/workflows/ci.yml`) calls the shared
`bookchaowalit/platform-ci-workflows` v1.1.1 (pinned by SHA): `npm ci`, lint,
typecheck, `vitest run`, then the Android JS bundle export, plus the security
scans (gitleaks, Semgrep, OSV-Scanner, Trivy). Nothing is masked. Reviewed
scanner exceptions, each with a reason and expiry, are in `osv-scanner.toml`
and `.trivyignore`. EAS / Expo cloud builds are not run in CI: they need the
owner's Expo account (`EXPO_TOKEN`), so they stay a manual owner step.

## Build

```bash
# Android
npx eas build --platform android --profile preview

# iOS
npx eas build --platform ios --profile preview
```

## Related

- **Frontend:** [bookchaowalit-website/calendar-app-frontend](https://github.com/bookchaowalit-website/calendar-app-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
