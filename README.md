# Files For GitHub

This folder contains the files that must stay synchronized with the remote-config repository used outside the app.

## Main files

- GitHub target: `https://github.com/lawliet8886/blockrush-remote-config/blob/main/remote_config.json`
- Local source of truth: `app/src/main/assets/remote_config_default.json`
- GitHub mirror: `Paragithub/remote_config.json`
- Schema mirror: `Paragithub/remote_config.schema.json`

The two JSON files must always be identical.

## Update flow

1. Edit `app/src/main/assets/remote_config_default.json`
2. Replace `Paragithub/remote_config.json` with the exact same content
3. Update `Paragithub/remote_config.schema.json` if the payload shape changed
4. Commit the same JSON to the GitHub remote-config repository
5. Bump the remote-config `version`

Current remote-config version: `7`

The app checks for updates every 12 hours.

## Annual live-event policy

- The calendar is annual-base and repeats every year.
- Each day can resolve at most:
  - `1 HEADLINE`
  - `1 SUPPORT`
- `HEADLINE` is the flagship seasonal/fixed event.
- `SUPPORT` is the recurring micro-event layer.
- Legacy IDs with `_2026` are still kept for backward compatibility with app code, tests, menu presentation specs and remote text mappings.
- `eventPrograms` stay separate from live events:
  - daily / weekly / monthly programs are internal challenge layers
  - they do not replace the `HEADLINE + SUPPORT` live-event resolver

## Payload model

Each live event now supports these annual fields:

- `slot`
  - `HEADLINE`
  - `SUPPORT`
- `schedule.kind`
  - `ANNUAL_WINDOW`
  - `MOVABLE_HOLIDAY`
  - `FIXED_RANGE` (supported by schema/runtime, not used in the current annual pack)
- `effects`
  - `rewardBoost`
  - `scoreBoost`
  - `trayBias`
  - `comboHook`
  - `bossCadence`
  - `clearMilestoneReward`
  - `boardRule`
- `windowGoal`
  - light per-window objective metadata

`startKey` / `endKey` remain in the payload for backward compatibility and fallback parsing.

## HEADLINE families in the current annual pack

| Event ID | Schedule |
| --- | --- |
| `event_lunar_new_year_2026` | `ANNUAL_WINDOW` 01/29 -> 02/09 |
| `event_valentines_2026` | `ANNUAL_WINDOW` 02/10 -> 02/14 |
| `event_carnival_2026` | `MOVABLE_HOLIDAY` anchored to Carnival Tuesday |
| `event_st_patrick_2026` | `ANNUAL_WINDOW` 03/14 -> 03/20 |
| `event_april_fools_2026` | `ANNUAL_WINDOW` 04/01 -> 04/02 |
| `event_easter_2026` | `MOVABLE_HOLIDAY` anchored to Easter Sunday |
| `event_earth_day_2026` | `ANNUAL_WINDOW` 04/22 -> 04/24 |
| `event_cinco_de_mayo_2026` | `ANNUAL_WINDOW` 05/05 -> 05/07 |
| `event_summer_solstice_2026` | `ANNUAL_WINDOW` 06/20 -> 06/26 |
| `event_independence_2026` | `ANNUAL_WINDOW` 07/04 -> 07/06 |
| `event_beach_party_2026` | `ANNUAL_WINDOW` 07/15 -> 07/31 |
| `event_back_to_school_2026` | `ANNUAL_WINDOW` 08/25 -> 08/31 |
| `event_oktoberfest_2026` | `ANNUAL_WINDOW` 09/19 -> 10/04 |
| `event_halloween_2026` | `ANNUAL_WINDOW` 10/25 -> 10/31 |
| `event_dia_de_muertos_2026` | `ANNUAL_WINDOW` 11/01 -> 11/02 |
| `event_thanksgiving_2026` | `MOVABLE_HOLIDAY` anchored to US Thanksgiving |
| `event_black_friday_2026` | `MOVABLE_HOLIDAY` anchored to US Black Friday |
| `event_winter_holidays_2026` | `ANNUAL_WINDOW` 12/20 -> 12/30 |
| `event_new_years_eve_2026` | `ANNUAL_WINDOW` 12/31 -> 01/01 |

## SUPPORT families in the current annual pack

- `event_weekly_boss_rush`
- `event_combo_challenge`
- `event_mystery_monday`

Disabled support families kept out of the premium rotation:

- `event_speed_run`
- `event_perfect_clear`

## Operational notes

- `FAST_DECAY` is still out of the annual premium live-event pack.
- `trayBias`, `comboHook` and `windowGoal` are present in payload/schema for the annual model, but runtime rollout may still be partial depending on the current app build.
- Any future event-family rename that removes `_2026` from IDs must be coordinated with app code, tests and menu-presentation mappings.
