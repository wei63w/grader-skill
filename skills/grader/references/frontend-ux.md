# Rubric · frontend-ux

**Category:** `frontend`  
Score **interaction, flows, IA, responsive behavior, and user acceptance**.  
Visual/creativity → `frontend-ui`. Motion/micro-animations → `frontend-motion`. A11y → `frontend-a11y`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `interaction` | Interaction feedback | 16 | `pointer_feedback`, `focus_feedback`, `async_states`, `exception_states` |
| `flow_efficiency` | Flow efficiency | 16 | `steps_to_goal`, `decision_clarity`, `recovery_path` |
| `ia` | Information architecture | 14 | `nav_clarity`, `priority_order`, `labeling` |
| `responsive` | Responsive UX | 14 | `reflow_quality`, `touch_density`, `breakpoint_intent` |
| `content_ux` | Content & microcopy UX | 12 | `guidance`, `empty_copy`, `error_copy` |
| `user_acceptance` | User acceptance | 28 | `cognitive_ease`, `trust_comfort`, `friction_feel`, `audience_fit`, `delight_fit`, `first_use_clarity` |

Weights sum to 100.

## Evidence checklist

- Primary user journeys (signup, create, checkout, search, settings)
- Buttons/forms: hover, disabled, loading, validation
- Nav/IA structure; mobile breakpoints
- Empty/error/success surfaces
- Signals of audience fit (consumer delight vs pro-tool density)

## Sub-criteria

### interaction
| Sub | Look for |
|-----|----------|
| `pointer_feedback` | Hover/active affordances on interactive elements |
| `focus_feedback` | Visible `:focus-visible` (deep a11y in `frontend-a11y`) |
| `async_states` | Loading skeletons/progress; not silent waits |
| `exception_states` | Inline errors, retries, disabled reasons |

### flow_efficiency
| Sub | Look for |
|-----|----------|
| `steps_to_goal` | Short path to primary goal |
| `decision_clarity` | Next step obvious |
| `recovery_path` | Undo/cancel/back; fix-forward after errors |

### ia
| Sub | Look for |
|-----|----------|
| `nav_clarity` | Findable sections; sensible grouping |
| `priority_order` | First screen not stuffed with secondary blocks |
| `labeling` | Labels match user language |

### responsive
| Sub | Look for |
|-----|----------|
| `reflow_quality` | Real layout changes, not shrunk desktop |
| `touch_density` | Controls usable on small screens |
| `breakpoint_intent` | Breakpoints feel designed |

### content_ux
| Sub | Look for |
|-----|----------|
| `guidance` | Just-enough help near complex fields |
| `empty_copy` | Empty states teach next action |
| `error_copy` | Errors say what happened and how to fix |

### user_acceptance
Estimate how willingly a target user would **adopt and keep using** the UI—not vanity novelty.

| Sub | 0–3 | 4–6 | 7–8 | 9–10 |
|-----|-----|-----|-----|------|
| `cognitive_ease` | Overwhelming / cryptic | Manageable with effort | Comfortable | Feels obvious |
| `trust_comfort` | Sketchy, aggressive, or unsafe-feeling | Mixed signals | Calm & credible | High trust chrome |
| `friction_feel` | Hostile friction / dark patterns | Annoying steps | Acceptable effort | Friction only when justified |
| `audience_fit` | Wrong density/tone for audience | Partial fit | Clear audience match | Feels “made for them” |
| `delight_fit` | Irritating gimmicks | Neutral | Appropriate delight | Delight that aids acceptance |
| `first_use_clarity` | New users lost | Slow ramp | Orient quickly | Confident first session |

**Dark patterns** (forced continuity, confirmshaming, hidden costs) ⇒ `friction_feel` / `trust_comfort` ≤3 and P0 when clear.

**Notes:** Consumer marketing can score higher on `delight_fit`; professional tools often win via `cognitive_ease` + `audience_fit` with quieter delight. Motion annoyance belongs primarily in `frontend-motion` `acceptability`, but chronic motion fatigue may also lower `delight_fit` here.

## Scoring notes

- If only desktop mockups exist, mark `responsive` subs `N/A` or score as risk
- Do not re-score color/type/`ui_creativity` here—point to `frontend-ui`
