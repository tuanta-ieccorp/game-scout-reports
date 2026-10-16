# Android market scout — Nut Stack: Sort Puzzle

**Package:** `com.nut.stack.sort.puzzle`  
**Publisher:** Nova Games Technology Limited  
**Evidence date:** 2026-10-16  
**Requested window:** 2026-07-19 through 2026-10-16; latest 30 days emphasized  
**Confidence:** Medium — public Sensor Tower evidence and live package inspection are strong, but paid downloads/engagement/creative exports were unavailable.

## Market result

**Recommendation: proceed with Android-first concept diligence.** Stack Sort is not the largest exact-match Android listing in the public comparison, but it has a strong recent Tier-1 chart trajectory, active advertising, fresh updates, and a visually distinct high-stack/mystery-nut presentation.

| Game | Exact core loop | Sensor Tower WW “Last Month” downloads | Store revenue | Read |
|---|---:|---:|---:|---|
| Nut Sort Puzzle: Sorting Games (`fg.nuts.sort.journey`) | Yes | 300k | < $5k | Scale leader; winner backup |
| Nut Sort Puzzle Games (`nut.sort.color.puzzle.offline.games`) | Yes | 300k | < $5k | Scale leader; older update cadence |
| **Nut Stack: Sort Puzzle** | **Yes** | **200k** | **< $5k** | Best observed recent Tier-1 rank momentum |
| Nut Sort Puzzle - Color Sort | Yes | 200k | < $5k | Mature feature/content comparator |

Source: Sensor Tower public autocomplete/overview accessed through Playwright on 2026-10-16; stored locally in `reverse/sensortower-autocomplete-competitors.json`. “Last Month” is Sensor Tower’s public label; the unauthenticated page did not expose its exact date definition. Revenue is store revenue/IAP only, not ad revenue.

### Worldwide versus US

- **Worldwide:** Sensor Tower public estimate: **200k downloads last month**, **< $5k store revenue**, Google Play install range **500k–1M**. Public overview lists Mexico, Russia, and Brazil as top countries and marks advertising **Active**.
- **US:** download total unavailable without authenticated data. US Casual free rank improved from **#188 on Sep 12** to **#31 on Oct 16**. Casual grossing rank improved from **#414 on Sep 14** to **#120 on Oct 16**.
- **Other Tier-1:** Casual free rank moved **AU #564→#29**, **CA #578→#34**, and **GB #469→#55** from first observed date in the 90-day pull to Oct 16. Sparse early observations mean these are rank trajectories, not download-growth calculations.

Source: [Sensor Tower Android overview](https://app.sensortower.com/overview/com.nut.stack.sort.puzzle?country=US) and public category-history response stored as `reverse/sensortower-android-tier1-rankings.json`.

### Growth classification

Recent category-rank gains support a **strong growth signal**, especially after the Oct 8 update. They do not prove download growth. Matched latest-30 versus preceding-30 download rows were not accessible, so the workflow definition of **viral remains unverified**. AppBrain’s separate public snapshot estimated 350k installs in 30 days, versus Sensor Tower’s 200k “Last Month”; this disagreement reinforces estimate uncertainty rather than supplying a valid growth series.

## Product and store facts

- Released worldwide: **2026-06-17** according to Sensor Tower; Google Play/AppBrain evidence places launch in mid-June.
- Inspected Play build: **1.0.26 (26)**, target SDK 36, min SDK 24; installed by `com.android.vending`.
- Package type: Cocos2d-x/native game with base plus four split APKs.
- Pulled size: approximately **305 MB** across inspected APK splits.
- Base APK SHA-256: `f51c2b946795a0be57808d0f744a49be2dfc4c4d1a5db23fbb8fc3cc6a46a8a2`.
- Signing SHA-1: `56E9198E209D6BDE2B66647A6940FA98A0CBB169`; certificate subject `CN=liu`.
- Store description: untimed top-nut transfer; destination must be empty or have matching top color.

Sources: [Google Play](https://play.google.com/store/apps/details?id=com.nut.stack.sort.puzzle), Sensor Tower overview, and local ADB/APK evidence under `reverse/apk/`.

## Level inspection

Fresh level 1 was inspected on BlueStacks (`emulator-5554`, Android 9, x86_64 host translating arm64 package).

![Observed US-signal level 1](media/level1-us-signal.png)

Observed:

- Seven tall primary bolt stacks plus spare bolts; unusually high stack depth from level 1.
- Only top nuts are movable; tapping a bolt lifts its visible top nut.
- Gray `?` nuts hide upcoming colors, adding uncertainty beyond classic open-information sort.
- Three locked bottom slots appear to gate additional help/space.
- Dense vertical presentation is distinctive but materially reduces first-level readability.
- Store reviews independently mention black/locked stacks obstructing progress and developer guidance about unlock order; anecdotal, not aggregate retention evidence.

The asset pack contains **12,631 opaque hashed files** plus an encrypted/packed `mainData`. Static inspection could not establish a trustworthy level count or uniqueness rate. Runtime preference `return_levelType=167` is a configuration/group ID, **not evidence of 167 levels**. Any advertised “thousands of levels” belongs to competitor store copy and is not evidence for this game.

## Tier-1 configuration validation

### Provider discovery

- Firebase Remote Config library is registered.
- Live SDK-style requests for US, GB, CA, AU, and HK all returned `NO_TEMPLATE`, zero entries, zero experiments, and zero rollouts.
- Therefore Firebase is present but is not the observed gameplay-config source.
- Custom runtime endpoints include `ip-api.com`, `appcpi.net`, and `hot-update.redgameservice.com` over cleartext HTTP.

### Runtime triangulation

| Test | Country evidence | Runtime group | Level-1 result | Classification |
|---|---|---:|---|---|
| Clean install, normal network | Public IP and app preference `HK` | `167` | Dense mystery-nut board | Runtime observed; HK context |
| Clean install, controlled US client geo response | App preference `US`; locale en-US | `167` | Same central level layout | Runtime observed; client signal only |
| Firebase direct Tier-1 matrix | Explicit US/GB/CA/AU/HK request parameters | No template | No gameplay values | Verified live Firebase response |

In the normal run, the game reported Android 9, model `NE2211`, `900x1600`, language `en`, country `HK`, and group `167`. Hot-update request used rollout `28` and package ID `2026_07_14_com.nut.stack.sort.puzzle_flower_nut_levels`; server returned no patch/key-value update and no eligible light-package variant.

A controlled proxy changed only the public client geo lookup to US. The app persisted `returnCountry=US`, but retained group `167`; the level-1 core differed by only **0.15% of pixels**, consistent with animation/UI timing rather than a different board. This rejects a simple client-country decoy hypothesis for level 1.

**Limit:** host public egress remained Hong Kong because the installed Surfshark session could not be switched programmatically. Server-side US IP targeting is therefore unverified. No evidence supports calling the observed config intentionally fake. Best statement: **group 167 and the observed level are stable under HK versus US client-country signals, but not verified from true US egress.**

Sources: local `reverse/config/`, `reverse/network/`, `reverse/runtime/`, and `reverse/us-signal-test/` captures. Sensitive raw identifiers remain Git-ignored.

## Ads and monetization

- Sensor Tower public overview marks the game **actively advertised**.
- Creative Gallery redirected to Sensor Tower’s demo page because the Playwright browser had no authenticated subscription session. No spend, Impression Share, network, country allocation, or top-10 creative review was available.
- Official store screenshots emphasize tactile tall stacks, bright hardware pieces, calm/no-timer positioning, mystery nuts, and locked obstacles. These are store assets, **not paid-ad creatives**.
- Package inspection found a broad ad stack: AppLovin, Google Mobile Ads, Pangle, Facebook Audience Network, Unity Ads, ironSource/LevelPlay, Vungle, Yandex, BidMachine, and others.
- Low public store-revenue estimate must not penalize this likely IAA/hybrid design; total revenue and profitability are unknown.

## Android shortlist

1. **Nut Stack: Sort Puzzle — winner:** strongest observed recent Tier-1 rank acceleration and differentiated high-stack/mystery presentation.
2. **Nut Sort Puzzle: Sorting Games — backup:** higher public worldwide monthly scale at 300k; less differentiation established.
3. **Nut Sort Puzzle Games — backup:** 300k public monthly scale and exact mechanics.
4. **Nut Sort Puzzle - Color Sort — mechanic/content reference:** 200k public monthly scale; mystery nuts and special obstacles.

## Gaps

- No authenticated Sensor Tower exports: US downloads, matched 30-day growth, DAU/MAU, retention, time spent, and creative share unavailable.
- No paid creative media was inspected.
- True US public-IP runtime test unavailable.
- Protected asset pack prevents trustworthy level count/uniqueness analysis.
- No Android-to-iOS package-content parity claim.
