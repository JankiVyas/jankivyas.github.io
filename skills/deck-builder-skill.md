# Interactive Browser Deck Standard

Use this standard for self-contained, interactive browser presentations built with static HTML, CSS, and JavaScript. Keep the deck accessible, keyboard-friendly, responsive, and usable as a clean print-to-PDF document.

## Slide frame

- Present one slide at a time in a **16:9 widescreen** container. Use a responsive aspect ratio such as `aspect-ratio: 16 / 9`, with a sensible maximum width and a dark or neutral stage around it.
- Keep each slide's content within the widescreen frame and provide a mobile layout that remains readable without horizontal scrolling.
- Use semantic slide sections, meaningful headings, sufficient contrast, and visible keyboard focus states.

## Seven-slide executive narrative

Follow this sequence, keeping one clear takeaway per slide:

1. **Cover** — title, concise framing statement, and presentation context.
2. **3-KPI Executive Summary** — three decision-relevant metrics with labels and brief interpretation.
3. **Before vs. After Comparison** — show the starting state alongside the proposed or observed improved state.
4. **Live Data Chart + Insight** — visualize data loaded from its source and state the interpretation next to the chart.
5. **3-Step Data Flow Diagram** — explain the process from inputs through transformation to usable outcomes.
6. **90-Day Roadmap** — present phased milestones and outcomes across the next 90 days.
7. **Closing CTA** — reinforce the recommendation and provide one clear next action.

## Navigation and status

- Support **Left Arrow** and **Right Arrow** keyboard navigation. Ignore navigation keystrokes while the visitor is typing in an input, textarea, select, or editable element.
- Include accessible **Prev** and **Next** buttons. Disable or otherwise clearly indicate unavailable directions at the first and last slide; do not wrap unexpectedly.
- Show a live slide counter in the format **`1 / 7`**, updating with the active slide. Expose status changes accessibly, for example with `aria-live="polite"`.
- Keep navigation controls available and operable by keyboard, with clear focus indicators and descriptive accessible names.

## Print and PDF export

- Provide a visible **Save / Print as PDF** control that calls the browser's print dialog (`window.print()`).
- Add a clean `@media print` stylesheet: hide navigation and screen-only controls, remove decorative backgrounds and shadows, set print colors for legibility, and print every slide on its own landscape page with page breaks. Preserve the 16:9 slide layout when practical.
- Avoid requiring a server-side renderer or build step; browser print-to-PDF is the export path.

## Quality checklist

- Exactly seven slides, in the narrative order above.
- 16:9 responsive slide framing with no unintended overflow.
- Arrow keys, Prev/Next buttons, and the `current / total` counter remain in sync.
- Print controls disappear in the print layout, and each slide prints as a separate page.
- Honor `prefers-reduced-motion` for any transitions.
