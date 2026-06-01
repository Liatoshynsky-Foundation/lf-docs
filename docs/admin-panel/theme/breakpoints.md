# Breakpoints

The theme overrides the default Material-UI breakpoints to match our specific project grid and responsive design requirements.

Standard MUI breakpoints have been adjusted, and new custom breakpoints (`xxl`, `ultra`) have been added. All breakpoints are fully typed via TypeScript module augmentation.

## Breakpoint Values

| Key         | Value (px) | Target Device (Approximate)                |
| ----------- | ---------- | ------------------------------------------ |
| **`xs`**    | 0          | Mobile devices                             |
| **`sm`**    | 768        | Tablets (Portrait)                         |
| **`md`**    | 1024       | Tablets (landscape) / small laptops        |
| **`lg`**    | 1280       | Laptops                                    |
| **`xl`**    | 1448       | Large laptops (e.g. MacBook 14")           |
| **`xxl`**   | 1728       | High-resolution laptops (e.g. MacBook 16") |
| **`ultra`** | 1920       | Full HD desktop monitors                   |

## Usage Examples

### 1. Using the `sx` prop

```tsx
<Box
  sx={{
    // 100% width on mobile, 50% on small laptops, 25% on large laptops
    width: { xs: "100%", md: "50%", xl: "25%" },

    // Changing flex direction based on screen size
    flexDirection: { xs: "column", lg: "row" },
  }}
>
  Content
</Box>
```

### 2. Usage in isolated styles files

```ts
// ExampleComponent.styles.ts
import { Theme } from "@mui/material";

export const styles = {
  container: (theme: Theme) => ({
    padding: "16px",

    // Applies padding starting from 1024px
    [theme.breakpoints.up("md")]: {
      padding: "32px",
    },

    // Applies padding starting from 1920px
    [theme.breakpoints.up("ultra")]: {
      padding: "64px",
    },
  }),
};
```

> **_Note_**: We follow a Mobile-First approach. Breakpoints defined in sx (e.g., sm: 'block') apply to that breakpoint and all larger screens.

---

[ ← **Return to the title**](./README.md) | [ **Next page** →](./extending.md)
