# Rubric · frontend-mobile

**Category:** `frontend`  
Score **mobile apps and mobile-first UI** (iOS/Android native, React Native, Flutter, Capacitor, mobile web/PWA).  
Desktop visual craft → `frontend-ui`. General web responsive only → `frontend-ux` `responsive`. Deep a11y → `frontend-a11y`. Motion → `frontend-motion`. JS perf without mobile constraints → `frontend-performance`.

State platform in scope (`ios` / `android` / `cross-platform` / `mobile-web`). Score platform-specific subs `N/A` when out of scope.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `layout_safe_area` | Layout & safe areas | 14 | `safe_insets`, `density_fit`, `orientation` |
| `touch_targets` | Touch & gestures | 16 | `hit_size`, `gesture_affordances`, `conflict_scroll`, `haptics_fit` |
| `navigation` | Navigation model | 14 | `back_stack`, `tabs_ia`, `deep_links`, `system_back` |
| `platform_conventions` | Platform conventions | 14 | `patterns_ios_android`, `system_ui`, `typography_controls` |
| `mobile_performance` | Mobile performance | 14 | `startup`, `scroll_jank`, `battery_network`, `image_memory` |
| `connectivity` | Connectivity & offline | 10 | `offline_ux`, `retry_resume`, `sync_clarity` |
| `input_forms` | Input & forms | 10 | `keyboard_avoidance`, `input_types`, `autofill_paste` |
| `store_release` | Ship readiness | 8 | `permissions`, `adaptive_icons`, `release_hygiene` |

Weights sum to 100.

## Evidence checklist

- Screens / navigators (tabs, stacks, drawers); `SafeArea` / inset usage
- Gesture handlers; scroll vs swipe conflicts
- Platform theme (Material / Cupertino / custom); status bar / nav bar
- Startup path, list virtualization, image caching
- Offline/error banners; permission prompts copy/timing
- `Info.plist` / AndroidManifest permissions; adaptive icon / splash
- Prefer device/simulator preview; if code-only, state confidence

## Sub-criteria

### layout_safe_area
| Sub | Inspect |
|-----|---------|
| `safe_insets` | Notch, home indicator, status bar, cutouts respected; no clipped CTAs |
| `density_fit` | Comfortable on small phones; large phones not sparse voids or stretched chrome |
| `orientation` | Portrait primary works; landscape handled or locked with intent |

### touch_targets
| Sub | 0–3 | 9–10 |
|-----|-----|------|
| `hit_size` | Tiny tap targets | ~44–48pt class targets, spacing between controls |
| `gesture_affordances` | Hidden gestures only | Swipe/long-press discoverable or taught |
| `conflict_scroll` | Scroll vs pager fights | Nested scrolls/gestures resolved |
| `haptics_fit` | Random/missing haptics | Light haptics on meaningful confirms only |

### navigation
| Sub | Inspect |
|-----|---------|
| `back_stack` | Predictable push/pop; state restored sensibly |
| `tabs_ia` | Tab roots clear; no deep mystery hierarchies |
| `deep_links` | Cold/warm link entry lands correctly when claimed |
| `system_back` | Android back / iOS edge-swipe behave as users expect |

### platform_conventions
| Sub | Inspect |
|-----|---------|
| `patterns_ios_android` | Platform idioms honored (or deliberately unified with care) |
| `system_ui` | Status bar, nav bar, sheets, alerts feel native-appropriate |
| `typography_controls` | Dynamic type / font scale doesn’t shatter layout |

**Cross-platform apps:** unified design can score well if touch/nav still feel native enough; fake-iOS-on-Android usually lowers this dimension.

### mobile_performance
| Sub | Inspect |
|-----|---------|
| `startup` | Time-to-interactive; splash not hiding long hangs |
| `scroll_jank` | Lists/feeds stay smooth; virtualization where needed |
| `battery_network` | Polling/wakelocks restrained; payloads sized for mobile |
| `image_memory` | Caching/resizing; no bitmap blowups

Without profiling, score as structural risk and say so.

### connectivity
| Sub | Inspect |
|-----|---------|
| `offline_ux` | Readable offline/empty-error states; cached content when sensible |
| `retry_resume` | Flaky network: retry, resume uploads, idempotent submits |
| `sync_clarity` | User knows what’s pending vs synced |

### input_forms
| Sub | Inspect |
|-----|---------|
| `keyboard_avoidance` | Focused fields not covered by keyboard |
| `input_types` | Correct keyboard (email, numeric, OTP); done/next actions |
| `autofill_paste` | Autofill/OTP paste works; no hostile paste blocks without reason |

### store_release
| Sub | Inspect |
|-----|---------|
| `permissions` | Least privilege; purpose strings; ask-in-context |
| `adaptive_icons` | Icons/splash meet store basics |
| `release_hygiene` | No debug banners/logs in release paths (when visible)

Mark entire dimension `N/A` for internal web-only demos without store packaging.

## Anti-patterns (usually deduct)

- Desktop layout shrunk to phone width
- CTA under home indicator / notch
- Gesture navigation broken by custom headers
- Permission dialogs on first launch with no context
- Infinite loaders with no offline story
- Hover-only affordances on touch devices

## Scoring notes

- **Mobile web / PWA:** still use this rubric; `platform_conventions` emphasizes mobile browser chrome and installability; `store_release` may be partial/`N/A`.
- Pair with `frontend-ui` / `frontend-motion` when visual/motion craft is also in scope.
- Don’t double-count generic WCAG keyboard desktop issues—send those to `frontend-a11y`.
