# Typography System

The theme uses two primary font families defined via CSS variables:

| Variable        | Font   | Usage                                  |
| --------------- | ------ | -------------------------------------- |
| `--font-mulish` | Mulish | Body text (`body`)                     |
| `--font-oswald` | Oswald | Headings, display variants (`display`) |

These variables are created in `~/shared/providers/body-provider/BodyProvider.tsx`.

## Custom Typography Variants

We have replaced standard MUI typography with our own design system variants. You must use the `<Typography>` component with the `variant` prop.

### Display (Oswald)

Used for massive, attention-grabbing headers.

- `displayXl` (236px)
- `displayLg` (132px)
- `displayMd` (114px)

### Headings (Oswald & Mulish)

- `h1` (116px, Oswald)
- `h2` (64px, Oswald) -> Scales down to 40px on mobile (`max-width: 767px`)
- `h3` (64px, Oswald)
- `h4` (32px, Mulish)
- `h5` (28px, Oswald)
- `h6` (24px, Mulish)
- `h7` (20px, Mulish)

### Body & Text (Mulish)

- `bodyLg` (24px)
- `bodyMd` (20px)
- `bodySm` (18px)
- `textMd` (16px) — **Base standard text**
- `textSm` (14px)
- `subtitle1` (18px)
- `subtitle2` (14px)
- `caption` (14px)

## Semantic HTML Mapping

To ensure accessibility and SEO, custom variants are mapped to specific HTML tags using `variantMapping` in `theme.ts`.

- `displayXl`, `displayLg`, `displayMd` render as `<h2>`.
- `bodyLg`, `bodyMd`, `bodySm`, `textMd`, `textSm` render as `<p>`.

## Custom Variants Usage

To use a specific font variant, use the `variant` prop on the Typography component:

```tsx
// Renders an <h2> tag with 132px font size
<Typography variant="displayLg">Header</Typography>

// Renders a <p> tag with 16px font size
<Typography variant="textMd">Standard text paragraph</Typography>
```

If the existing option does not fully meet your requirements, you should use the option that most closely matches the desired one, and then modify the necessary CSS properties in the component's styles.

For example, you need to use a typography variant with such options:

- Font family - Mulish
- Font size - 14px
- Font weight - 700
- Line height - 1.75

The closest typography variant that the `theme.ts` contains is a `subtitle2`:

```ts
subtitle2: {
  fontFamily: fontFamilies.body, // matches your requirements
  fontSize: '14px',              // matches your requirements
  fontWeight: 500,               // doesn't match your requirements, you need a 700 value
  lineHeight: 1.3                // doesn't match your requirements, you need a 1.75 value
}
```

Pass `subtitle2` into variant prop of a Typography component (no additional import needed) and pass the styles block from the styles file:

```tsx
// Component.tsx
import { Typography } from "@mui/material";
import { styles } from "./Component.styles.ts";

<Typography variant="subtitle2" sx={styles.paragraph}>
  Subtitle
</Typography>;
```

The desired properties must be rewritten in the component's styles file:

```ts
// Component.styles.ts
export const styles = {
  paragraph: {
    fontWeight: 700, // overwritten
    lineHeight: 1.75, // overwritten
  },
};
```

---

[ ← **Return to the title**](./README.md) | [ **Next page** →](./components.md)
