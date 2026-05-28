# Color Dictionary

All color logic is extracted into the `colors.ts` file. **Hardcoding HEX values directly in UI components is strictly prohibited.**

## 1. Base Palette (`mainHexPalette`)

This is the root dictionary containing raw HEX values. It should be used for base styling when a specific semantic token is not available.

- **Neutrals:** `white`, `black`, `charcoalGray`
- **Brand Colors:** `blue` (50-900), `adminBlue` (50-900), `brown` (50-900), `yellow` (100-900), `red` (50-900), `burgundy` (50-900), `green` (100, 600, 800)

## 2. MUI Palette Integration

The `mainHexPalette` is integrated into the core MUI `theme.palette`. We also define semantic palette slots for standard components:

- `primary`: Black background
- `secondary`: White/transparent background
- `tertiary`: Custom yellow accent
- `error`: Red semantic elements
- `warning`: Yellow warning elements

## 3. Semantic Component Tokens

Instead of guessing which color to use, `colors.ts` exports specific objects mapped to UI elements.

### Buttons & Button Groups (`buttonColors`, `buttonGroupColors`)

Supports semantic variants with detailed states (enabled, hovered, focused, pressed, disabled) for both `filled` and `outlined` versions.

- `primary`
- `secondary`
- `tertiary`
- `error`

### Inputs (`textFieldColors`, `selectorColors`, `checkboxColors`)

- **`textFieldColors`**: Separated into two main variants:
  - `standard`
  - `outline`
    _(Both contain states for default, hovered, focused, error, and disabled)._
- **`selectorColors`**: Contains specific background and text colors for `filled` and `outline` variants.
- **`checkboxColors`**: Tokens for `default`, `hovered`, `focused`, `selected`, and `disabled` states, including ripple effects.

### Tags & Indicators (`chipsColors`, `badgeColors`)

- **`chipsColors`**:
  - Base states: `filled`, `outline` (with hover/press/disabled modifiers).
  - Semantic specific: `published`, `draft`, `newsChipBg`, `eventChipBg`, `mediaChipBg`.
- **`badgeColors`**: Divided by variant (`standard`, `dot`) and color (`Primary`, `Secondary`, `Error`).

### Feedback & Modals (`alertColors`, `tooltipColors`)

- **`alertColors`**: Divided by variant (`filled`, `outlined`). Each variant supports 4 severities:
  - `error`
  - `warning`
  - `info`
  - `success`
- **`tooltipColors`**: Basic tokens (`defaultBg`, `defaultText`, `defaultShadow`).

### Navigation & Layout (`tabsColors`, `toolbarColors`, `accordionColors`, `menuItemColors`)

- **`tabsColors`**: Tokens for `active`, `unactive`, `hovered`, `pressed`, and `disabled` states + base underline.
- **`toolbarColors`**: Tokens for `default`, `hovered`, `focused`, `border`, and `textColor`.
- **`accordionColors`**: Basic structure tokens (`defaultBg`, `defaultBorder`, `defaultIcon`).
- **`menuItemColors`**: Text and background states (`defaultText`, `disabledText`, `hoveredBg`, `activeBg`).

## Usage Example

The semantic token objects in `colors.ts` were mostly created to be used in `theme.ts` to style the base components. However, there are colors which are not used in `theme.ts`, but in specific component styles (like `newsChipBg` in `chipsColors`). So, if you need to use the relevant semantic token object from `colors.ts`, import it into your file. If you need a bare color from the `mainHexPalette`, you may use it as a string directly (e.g., `"blue.200"`), without additionally importing the `mainHexPalette`:

```ts
// Сomponent.styles.ts
import { chipsColors } from "~/shared/theme/colors";

export const styles = {
  container: {
    backgroundColor: chipsColors.newsChipBg,
    color: "blue.200",
  },
};
```

```tsx
// Сomponent.tsx
import { Box } from '@mui/material';
import { styles } from './Component.styles'

// ✅ Correct (Using imported styles with tokens):
<Box sx={ styles.container } />

// ❌ Incorrect (Hardcoded HEX):
<Box sx={{ backgroundColor: '#B6D0F7', color: '#190d03' }} />
```

In some cases, you might need to use CSS utility functions (like MUI's `alpha()`) to modify standard palette colors. In such cases, string paths won't work inside the function. You must import the mainHexPalette object directly:

```ts
// Сomponent.styles.ts
import { alpha } from "@mui/material";
import { mainHexPalette as colors } from "~/shared/theme/colors"; // Aliased 'as colors' for convenience

export const styles = {
  container: {
    backgroundColor: alpha(colors.blue[200], 0.5), // Pay attention to the bracket notation for numeric keys
  },
};
```

---

[ ← **Return to the title**](./README.md) | [ **Next page** →](./typography.md)
