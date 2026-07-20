# Rubric · frontend-motion

**Category:** `frontend`  
Score **motion design, micro-animations, and motion acceptability**.  
Static visuals → `frontend-ui`. Flow/IA → `frontend-ux`. A11y motion prefs overlap `frontend-a11y` (coordinate, don’t ignore). Runtime jank without motion intent → `frontend-performance`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `purpose` | Purpose & clarity | 16 | `task_support`, `feedback_role`, `no_pure_noise` |
| `micro_interactions` | Micro-interactions | 18 | `control_response`, `state_transitions`, `spatial_continuity` |
| `timing_easing` | Timing & easing | 14 | `duration_fit`, `easing_quality`, `stagger_discipline` |
| `choreography` | Choreography | 14 | `sequence_logic`, `attention_guide`, `exit_enter` |
| `motion_performance` | Motion performance | 14 | `compositor_friendly`, `no_layout_thrash`, `main_thread_cost` |
| `acceptability` | Motion acceptability | 14 | `fatigue_risk`, `frequency_restraint`, `context_fit` |
| `inclusive_motion` | Inclusive motion | 10 | `reduced_motion`, `vestibular_safety`, `optional_intensity` |

Weights sum to 100.

## Evidence checklist

- CSS/`@keyframes`/transitions; Motion/GSAP/Lottie/Rive usage
- Button/hover/press, modal open/close, list reorder, page transitions
- `prefers-reduced-motion` media queries / Motion `useReducedMotion`
- Prefer live preview; if code-only, score intent + risk and say so

## Sub-criteria

### purpose
| Sub | 0–3 | 9–10 |
|-----|-----|------|
| `task_support` | Motion hides status or delays tasks | Clarifies state/change without delay tax |
| `feedback_role` | Decorative only on critical actions | Confirms cause→effect |
| `no_pure_noise` | Looping attention theft | Quiet unless earning attention |

### micro_interactions
| Sub | Inspect |
|-----|---------|
| `control_response` | Buttons/toggles/inputs feel instantaneous and tactile |
| `state_transitions` | Expand/collapse, tabs, toasts morph coherently |
| `spatial_continuity` | Shared-element / FLIP-like continuity where it helps orientation |

### timing_easing
| Sub | Inspect |
|-----|---------|
| `duration_fit` | ~100–200ms micro; ~200–400ms UI; longer only for narrative |
| `easing_quality` | Natural ease-out/standard curves; avoid linear everything or bounce spam |
| `stagger_discipline` | Staggers short and purposeful; not cascading delays on every list |

### choreography
| Sub | Inspect |
|-----|---------|
| `sequence_logic` | Enter/exit order matches reading/task order |
| `attention_guide` | Motion points to the next decision, not away |
| `exit_enter` | Leaves and arrives without jump-cuts on important surfaces |

### motion_performance
| Sub | Inspect |
|-----|---------|
| `compositor_friendly` | Prefer transform/opacity; avoid animating layout thrash props casually |
| `no_layout_thrash` | No top/left/width storms on scroll |
| `main_thread_cost` | JS-driven frames stay smooth; no scroll jank from listeners |

### acceptability
| Sub | Inspect |
|-----|---------|
| `fatigue_risk` | Won’t annoy on daily use (tooling UIs: lower motion appetite) |
| `frequency_restraint` | Not every hover/page load replays a show |
| `context_fit` | Marketing can be bolder; admin/finance stay restrained |

### inclusive_motion
| Sub | Inspect |
|-----|---------|
| `reduced_motion` | Essential feedback remains; non-essential motion disabled/simplified |
| `vestibular_safety` | No large parallax/zoom/spin that induces discomfort |
| `optional_intensity` | Intensity scaled or skippable when appropriate |

## Anti-patterns (usually deduct)

- Hero autoplay loops that compete with the CTA
- Bounce/elastic on every control
- Page-transition waits that block input
- Scroll-jacking / forced smooth-scroll takeover
- Motion that only exists because a library default was left on

## Scoring notes

- **More motion ≠ higher score.** Reward purpose and restraint.
- Tooling/dashboard products: weight acceptability/inclusive_motion mentally harsher when borderline.
- Cross-link creative static ideas to `frontend-ui` `ui_creativity`; user trust/friction to `frontend-ux` `user_acceptance`.
