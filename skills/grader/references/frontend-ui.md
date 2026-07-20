# Rubric · frontend-ui

**Category:** `frontend`  
Score **visual design + UI creativity** (hierarchy, type, space, color, consistency, brand, creative distinctiveness).  
Flows/acceptance → `frontend-ux`. Motion/micro-animations → `frontend-motion`. A11y → `frontend-a11y`.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria (equal avg) |
|----|-----------|--------|---------------------------|
| `visual_hierarchy` | Visual hierarchy | 14 | `focus_clarity`, `competition_control`, `scan_path` |
| `typography` | Typography | 12 | `type_ramp`, `readability`, `type_choice` |
| `spacing_layout` | Spacing & layout | 14 | `spacing_scale`, `alignment_grouping`, `section_rhythm` |
| `color_contrast` | Color & contrast | 12 | `palette_intent`, `text_contrast`, `status_semantics` |
| `consistency` | Consistency | 12 | `component_sameness`, `token_usage`, `copy_tone` |
| `brand_hero` | Brand & first screen | 14 | `brand_signal`, `hero_budget`, `visual_anchor` |
| `ui_creativity` | UI creativity | 22 | `originality`, `concept_fit`, `memorable_detail`, `anti_slop`, `craft_risk` |

Weights sum to 100.  
**Dimension score** = average of non-N/A subs. **Total** = weighted dimensions.

## Evidence checklist

- Page/layout shells, design tokens / theme / Tailwind config
- Hero / primary screens; button & heading styles
- Distinctive layout/composition choices vs template patterns
- Prefer preview/screenshot; if code-only, state that in the summary

## Sub-criteria & anchors

### visual_hierarchy
| Sub | 0–3 | 4–6 | 7–8 | 9–10 |
|-----|-----|-----|-----|------|
| `focus_clarity` | No primary focus | Weak primary | Clear primary action/title | Instant task focus |
| `competition_control` | Many equal shouts | Some rivalry | Controlled secondary | Near-zero noise on critical path |
| `scan_path` | Chaotic | Recoverable | Predictable F/Z scan | Effortless scan |

### typography
| Sub | Inspect |
|-----|---------|
| `type_ramp` | Distinct size/weight steps for H1–body–meta |
| `readability` | Body size, line-height, measure (~45–75ch) |
| `type_choice` | Intentional faces; avoid unmotivated default stacks when brand matters |

### spacing_layout
| Sub | Inspect |
|-----|---------|
| `spacing_scale` | Few stable steps (e.g. 4/8); few magic numbers |
| `alignment_grouping` | Columns/baselines; related items grouped |
| `section_rhythm` | Section padding cadence; not cramped or random voids |

### color_contrast
| Sub | Inspect |
|-----|---------|
| `palette_intent` | Brand/neutrals related; not rainbow clutter |
| `text_contrast` | Body/controls readable (aim WCAG-ish) |
| `status_semantics` | Success/warn/danger distinct and consistent |

**Penalize:** unmotivated purple/glow slop; gray-on-gray controls.

### consistency
| Sub | Inspect |
|-----|---------|
| `component_sameness` | Same-role controls look/behave alike |
| `token_usage` | Shared radius/shadow/spacing tokens |
| `copy_tone` | Voice consistent across UI chrome |

### brand_hero
| Sub | Inspect |
|-----|---------|
| `brand_signal` | Recognizable without nav |
| `hero_budget` | Landing: brand + one claim + CTA + one dominant visual |
| `visual_anchor` | Real product/place/context imagery—not empty gradient filler |

**Admin/tools:** reinterpret as product identity + workspace clarity (same subs).

### ui_creativity
Score **distinctive, fitting creativity**—not randomness or trend cosplay.

| Sub | 0–3 | 4–6 | 7–8 | 9–10 |
|-----|-----|-----|-----|------|
| `originality` | Indistinguishable template | Mild variation | Clear point of view | Memorable visual idea |
| `concept_fit` | Creativity fights the product job | Partially aligned | Serves brand/task | Concept amplifies meaning |
| `memorable_detail` | None / generic stock | One weak flourish | 1–2 sticky details | Details people would recall |
| `anti_slop` | AI-default look (purple gradients, glow piles, badge spam) | Some clichés | Mostly avoided | Fresh without gimmicks |
| `craft_risk` | Chaos mistaken for creativity | Uneven experiment | Controlled boldness | Bold yet polished |

**Do not** reward creativity that destroys hierarchy, contrast, or task completion—cap related subs and call it out under weaknesses.

## Anti-patterns

Card-wall heroes, badge sticker piles, competing H1-level claims, inconsistent radius/shadow systems, novelty that blocks the primary CTA.
