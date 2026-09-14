# MOTION.md - Crossings

MOTION_INTENSITY: **6** (fluid CSS + scroll-driven reveals, no scroll-hijack, no JS).
All motion animates **transform and opacity only**. No scroll listeners, no rAF loops, no libraries.
Implementation is 100% CSS: load cascade + CSS scroll-driven animations (`animation-timeline: view()`), progressively enhanced.

| # | What | Where | Trigger | Spec | Reduced motion |
|---|------|-------|---------|------|----------------|
| 1 | **Hero load cascade** | Hero: h1, subtext, CTAs, figure | Page load | `rise`: 700ms, `cubic-bezier(.16,1,.3,1)`, `translateY(18px) -> 0` + fade. Delays: 0 / 90ms / 180ms / 140ms (stagger reads as "papers laid down") | Disabled. Content renders static |
| 2 | **Route tiles reveal** | 3 route tiles | Tile enters viewport (~34% of entry range) | CSS scroll-driven `step-in`: fade + `translateY(26px) -> 0`. Each tile drives its own timeline, so the asymmetric grid staggers naturally | Disabled via `@supports` + media gate. Content visible |
| 3 | **Process step reveal** | 4 steps on the route line | Each step enters viewport (entry 0-34%) | Same `step-in`. Sequence on scroll = the journey itself (storytelling: the file moves down the route) | Disabled. Content visible |
| 4 | **"FILED" stamp press-in** | Last process step, stamp mark | Stamp enters viewport (entry 20-80%) | `stamp-in`: from `rotate(-16deg) scale(1.7) opacity 0` to settled `rotate(-8deg) scale(1)`, spring ease `cubic-bezier(.2,1.4,.3,1)`. Reads as a stamp being pressed onto the file | Disabled. Stamp renders static in final position |
| 5 | **Hero stamp press** | Hero corner stamp | Pointer hover on the hero figure | Scale 0.92 + 3px press-down, 220ms spring; springs back on unhover. Feedback: "this is a real stamp, it has weight" | Disabled (transition removed) |
| 6 | **Micro-transitions** | Links, buttons, FAQ `+` marker | Hover / active / `details` toggle | Link underline thickens; buttons shift bg 160ms and push `translateY(1px)` on `:active`; FAQ `+` rotates 45deg over 200ms | All transitions removed (`transition: none`) |

## Global rules

- Every animation is gated by `@media (prefers-reduced-motion: no-preference)`; scroll-driven ones additionally require `@supports (animation-timeline: view())`.
- Under `prefers-reduced-motion: reduce`: animations/transitions forced off, `scroll-behavior: auto`. Nothing is hidden, nothing depends on motion to become readable.
- Browsers without scroll-driven animation support simply show static content (feature is additive, never load-bearing).
- Smooth anchor scrolling is gated by the same reduced-motion media query.
- No marquees, no parallax, no infinite loops. MOTION_INTENSITY 6 stays inside "fluid CSS" territory.

## Why these motions (motivation check)

- 1, 2, 3: hierarchy + storytelling. The page is about a process that unfolds in order; the motion mirrors that.
- 4: the brand signature (passport stamp) given physical behavior once, at the natural endpoint of the story ("FILED").
- 5: feedback, tied to the same signature element.
- 6: affordance feedback for interactive controls.
