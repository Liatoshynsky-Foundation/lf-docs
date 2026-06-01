# Extending the Theme

If a new feature requires colors, typography variants, or component styles that are not currently present in the design system, **do not hardcode them in your components.** Instead, follow this guide to extend the global theme properly.

Since our theme uses TypeScript and strict module augmentation, any additions must be declared in the types first.

## 1. Adding Missing Colors or Tokens

Depending on what kind of color you need to add, follow the appropriate strategy:

### Strategy A: Adding a new raw hex color

If designers introduced a new brand color (e.g., `purple`), add it to the root dictionary in `colors.ts`:

1. Open `~/shared/theme/colors.ts` and add the color to `mainHexPalette`.
2. It will automatically become available via string paths in the `sx` prop (e.g., `color: 'purple.500'`) because `...mainHexPalette` is spread inside the MUI palette configuration.

### Strategy B: Adding a new semantic token group

If you are adding an entirely new component and want to restrict its colors:

1. Define a new token object in `colors.ts` (e.g., `export const tableColors = { ... }`).
2. Import and use this object strictly within your component's `.styles.ts` file or import it into the `theme.md` file if the freshly added component override needs it.

### Strategy C: Adding a new core MUI palette color

If you need to add a brand new semantic color slot (e.g, `quaternary`) that should be supported by standard MUI components like `Button`:

1. Open `theme.ts` and extend the `Palette` and `PaletteOptions` interfaces using module augmentation:

```ts
declare module "@mui/material/styles" {
  interface Palette {
    quaternary: Palette["primary"];
  }
  interface PaletteOptions {
    quaternary?: PaletteOptions["primary"];
  }
}
```

2. If this color should be supported by buttons, extend the button color overrides as well:

```ts
declare module "@mui/material/Button" {
  interface ButtonPropsColorOverrides {
    quaternary: true;
  }
}
```

3. Add the actual color values inside the `palette` object in `createAdminTheme()`:

```ts
    palette: {
      primary: {
        main: buttonColors.primary.filledEnabledBg,
        contrastText: buttonColors.primary.filledNormalText
      },
      secondary: {
        main: buttonColors.secondary.filledEnabledBg,
        contrastText: buttonColors.secondary.filledNormalText
      },
      ...
      quaternary: {
        main: ...         // your color
        contrastText: ... // your color
      },
      ...
    }
```

## 2. Adding Custom Typography Variants

If you need a new typography variant (e.g., a specific mobile header or a unique subtitle):

### Step 1: Extend TypeScript Interfaces

MUI needs to know about the new variant name. Add it to the module augmentation section in `theme.ts`:

```ts
declare module "@mui/material/styles" {
  interface TypographyVariants {
    displaySm: React.CSSProperties; // Your new variant
  }

  interface TypographyVariantsOptions {
    displaySm?: React.CSSProperties; // Your new variant
  }
}

declare module "@mui/material/Typography" {
  interface TypographyPropsVariantOverrides {
    displaySm: true; // Your new variant
  }
}
```

### Step 2: Define Styles in the Theme

Add the actual font configuration inside the `typography` block of `createAdminTheme()`:

```ts
typography: {
  // ... existing variants
  displaySm: {
    fontFamily: fontFamilies.display,
    fontSize: '96px',
    fontWeight: 500,
    lineHeight: 1.1
  }
}
```

### Step 3: Map to a Semantic HTML Tag (Optional)

By default, custom variants render as a `<span>`. If your variant is a header or a paragraph, map it to the correct HTML tag inside the `MuiTypography` component overrides:

```ts
MuiTypography: {
  defaultProps: {
    variantMapping: {
      // ... existing mappings
      displaySm: "h3"; // Will render as <h3> for better SEO and accessibility
    }
  }
}
```

## 3. Adding New Component Overrides or Custom Variants

If you need to change how a standard MUI component behaves globally, or add a completely custom style variant (like we did with `Paper` with `discardChangesModal` variant):

### Scenario A: Modifying an existing global override

Find the component name (e.g., `MuiAlert`) in the components block of `createAdminTheme()`.

- To change base styles, modify `styleOverrides.root`.

- To change a specific state or sub-element, add it to styleOverrides (e.g., `message` or `icon`).

### Scenario B: Creating a brand new custom component variant

If you want to create a reusable visual variant for an existing component (e.g., a special card layout for `Paper`):

1. Declare the new variant in types using module augmentation:

```ts
declare module "@mui/material/Paper" {
  interface PaperPropsVariantOverrides {
    featuredCard: true; // Your new variant name
  }
}
```

2. Add the variant styles inside the component's variants array in `theme.ts`:

```ts
MuiPaper: {
  variants: [
    // ... existing variants
    {
      props: { variant: "featuredCard" },
      style: {
        padding: "24px",
        borderRadius: "16px",
        backgroundColor: mainHexPalette.blue[50],
        border: `1px solid ${mainHexPalette.blue[200]}`,
      },
    },
  ];
}
```

3. Use it anywhere in the project naturally:

```tsx
<Paper variant="featuredCard">
  This card automatically receives global featured styles.
</Paper>
```

> ⚠️ **_Pay attention_**: if you are adding a new component style, try to reuse existing semantic objects (textFieldColors, etc.) before creating a new one to avoid bloating the color dictionary.

---

[ ← **Return to the title**](./README.md)
