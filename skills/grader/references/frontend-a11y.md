# Rubric · frontend-a11y

**Category:** `frontend`  
Deep-dive **accessibility**. Visual contrast overlaps `frontend-ui` `color_contrast`—here emphasize operable/understandable access.

## Dimensions & weights

| ID | Dimension | Weight | Sub-criteria |
|----|-----------|--------|--------------|
| `semantics` | Semantics & structure | 18 | `landmarks`, `heading_order`, `control_roles` |
| `keyboard` | Keyboard access | 18 | `tab_order`, `no_traps`, `shortcuts_safe` |
| `focus_visible` | Focus visibility | 12 | `focus_style`, `focus_restore` |
| `name_label` | Names & labels | 16 | `accessible_name`, `form_labels`, `icon_buttons` |
| `contrast_motion` | Contrast & motion | 14 | `contrast_critical`, `reduced_motion`, `flash_risk` |
| `assistive` | Assistive tech support | 12 | `live_regions`, `alt_text`, `announcements` |
| `targets` | Targets & input | 10 | `hit_size`, `pointer_cancellation` |

Weights sum to 100.

## Evidence checklist

- Landmark/`main`/`nav` structure; heading outline
- Interactive elements: native controls vs `div onClick`
- Forms: label associations, error linking
- Modals/menus: focus trap/restore
- Images/`aria-*`/`alt`; `prefers-reduced-motion`
- Prefer axe/keyboard pass if runnable; else static + honest limits

## Sub-criteria

### semantics
| Sub | 0–3 signal | 9–10 signal |
|-----|------------|-------------|
| `landmarks` | No/`div` soup | Clear banner/nav/main/contentinfo |
| `heading_order` | Skipped/misused headings | Logical outline |
| `control_roles` | Clickable non-controls | Buttons/links/inputs correct |

### keyboard
| Sub | Inspect |
|-----|---------|
| `tab_order` | Matches visual order; no surprises |
| `no_traps` | Modals/menus escapable; focus not stuck |
| `shortcuts_safe` | No hijacking without modifiers where harmful |

### focus_visible
| Sub | Inspect |
|-----|---------|
| `focus_style` | High-visibility focus rings not removed globally |
| `focus_restore` | Close dialog → return focus to trigger |

### name_label
| Sub | Inspect |
|-----|---------|
| `accessible_name` | Every control has a name |
| `form_labels` | Labels tied to inputs; errors associated |
| `icon_buttons` | Icon-only buttons have `aria-label`/sr-text |

### contrast_motion
| Sub | Inspect |
|-----|---------|
| `contrast_critical` | Text/UI chrome contrast failures |
| `reduced_motion` | Honor `prefers-reduced-motion` for non-essential motion |
| `flash_risk` | Avoid rapid flashing patterns |

### assistive
| Sub | Inspect |
|-----|---------|
| `live_regions` | Async status updates announced when needed |
| `alt_text` | Informative vs decorative images handled correctly |
| `announcements` | Toasts/errors reachable to AT |

### targets
| Sub | Inspect |
|-----|---------|
| `hit_size` | ~44×44px touch targets where mobile matters |
| `pointer_cancellation` | No accidental irreversible actions on down-only |

## Scoring notes

- Confirmed keyboard trap or unlabeled critical control → those subs ≤3, P0
- Mark runtime-only checks `N/A` if not verified
