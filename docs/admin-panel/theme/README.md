# Admin Theme — Documentation

A custom MUI theme for the admin panel. Built on top of `@mui/material`, it extends the palette, typography, breakpoints, and overrides component styles.

The theme (components, typography, colors) is mostly based on [the Design System](https://www.figma.com/design/IDQ5XmNo6PQBmBlL3DBm6Q/Admin-Liatoshynsky-Foundation?node-id=1-2&p=f&t=N84XpGtbj4BTkldT-0). Some unique settings (e.g `green` and `darkGray` colors) were taken from [the admin panel designs](https://www.figma.com/design/IDQ5XmNo6PQBmBlL3DBm6Q/Admin-Liatoshynsky-Foundation?node-id=77-8019&p=f&t=N84XpGtbj4BTkldT-0).

## Documentation Sections

| File                               | Contents                            |
| ---------------------------------- | ----------------------------------- |
| [colors.md](./colors.md)           | Color palette and semantic tokens   |
| [typography.md](./typography.md)   | Typography variants and fonts       |
| [components.md](./components.md)   | Component overrides and variants    |
| [breakpoints.md](./breakpoints.md) | Custom breakpoints and their values |
| [extending.md](./extending.md)     | Custom theme extending guide        |

## File Structure

```
app/providers/
└── ThemeProvider.tsx ← React provider, entry point
app/shared/theme/
├── theme.ts ← createAdminTheme(), all component overrides
└── colors.ts ← color tokens and palette
```

## Integration

For the theme to work, the entire application (or the required part of it) must be wrapped in our custom `ThemeProvider`.

```tsx
import { ThemeProvider } from "~/shared/theme/ThemeProvider";

function App({ children }) {
  return <ThemeProvider>{children}</ThemeProvider>;
}
```

`ThemeProvider` creates the theme via `createAdminTheme()` once (using `useMemo`) and passes it to `MuiThemeProvider`.

## How the Theme Works

Once ThemeProvider is mounted at the root, the theme is applied globally and automatically throughout the entire component tree. No imports are required in individual components.

MUI components pick up all overrides, palette values, and typography variants out of the box:

```tsx

<Button variant="filled" color="primary">Save</Button>
<Button variant="outlined" color="tertiary" size="large">Upgrade</Button>

<Typography variant="h7">Hero text</Typography>
<Typography variant="textSm">Caption</Typography>

<Box sx={{ color: 'text.secondary', bgcolor: 'primary.main' }} />
```

Color scale values from the palette are also available directly in `sx`:

```tsx
<Box sx={{ color: "blue.700", borderColor: "yellow.500" }} />
```

### ⚠️ Best Practice: Separate Styles

Directly specifying styles for an element is not recommended! It is best to place all styles in component `style` files (e.g., `PhotoBlock.styles.ts`), then import them and pass them to the `sx` prop:

```ts
// PhotoBlock.styles.ts:
...
export const styles = {
  imageBlock: {
    display: 'flex',
    gap: 3,
    alignItems: 'flex-start',
    minWidth: '366px'
  },
  ...
}
```

```tsx
// PhotoBlock.tsx:
...
import { styles } from './PhotoBlock.styles';
...
<Box sx={styles.imageBlock}>...</Box>
```

---

[ **Next page** →](./colors.md)
