# Studio Clarity — Visual Standard

## Design intent

Studio Clarity is a calm, editorial visual system for making complex ideas feel clear. Give content room to breathe, use deliberate hierarchy, and keep decoration quiet enough that the message remains the focus.

## Color palette

- **Warm gallery cream — `#FAF8F5`:** the primary page background.
- **Pure white — `#FFFFFF`:** cards and raised content surfaces.
- **Deep charcoal ink — `#1E1E1C`:** primary text, strong rules, and high-contrast elements.
- **Muted stone — `#5C5B57`:** secondary copy and supporting labels.
- **Terracotta — `#B85D38`:** restrained accent for emphasis, links, and key data.
- **Hairline — `#E5E0D8`:** fine borders and dividers.

Maintain readable contrast. Use terracotta as an accent rather than a large field of color; pair it with the warm neutral palette.

## Typography

- **Headings:** Georgia, editorial serif. Use expressive but restrained scale and comfortable line-height.
- **Body text:** Inter, sans-serif, for clear and approachable reading.
- **Metadata tags:** JetBrains Mono, uppercase, with modest letter spacing. Reserve this treatment for short labels, dates, and categories.

Use a clear typographic hierarchy. Keep paragraphs at a readable measure and avoid setting long passages in uppercase or monospace.

## Surface and detail

- Use a subtle, low-contrast dot-grid texture in the page background; it should be barely perceptible behind content.
- Cards are pure white with 1px hairline borders in `#E5E0D8`.
- Prefer simple geometry, generous whitespace, and fine separators over heavy shadows or ornamental framing.
- Ensure cards and controls remain legible on the cream background.

## Motion

Use calm fade-up scroll reveals: begin slightly below the final position and transition to full opacity and position over **0.6s** with `cubic-bezier(0.16, 1, 0.3, 1)`. Keep movement subtle, avoid distracting stagger effects, and respect `prefers-reduced-motion` by removing or minimizing animation.

## Consistency checklist

1. Cream canvas, white content surfaces, charcoal text, and sparing terracotta emphasis.
2. Georgia headlines, Inter body, and JetBrains Mono uppercase metadata.
3. Subtle dot grid, 1px `#E5E0D8` borders, and generous whitespace.
4. Scroll motion is calm, brief, and disabled or reduced when the visitor requests reduced motion.
