# Components

The theme globally overrides styles and behavior for standard MUI components: `Button`, `ButtonGroup`, `TextField`, `Select`, `Checkbox`, `Chip`, `Badge`, `Tabs`, `Alert`, `Accordion`, `ToggleButtonGroup`, `Menu`, `Modal`, `Paper`, and `Tooltip`.
All overrides — including available variants, colors, and sizes for each component — are defined in theme.ts. When using a component, pass the corresponding MUI props (variant, color, size) to apply the themed styles:

```tsx
<Button variant="filled" color="primary" size="large" />
<Chip variant="outlined" />
```

> Note: the project uses a custom Button wrapper where MUI's variant="contained" is exposed as variant="filled".

## Supported Props Reference

To avoid checking theme.ts every time, here is the exact list of variants and colors strictly styled by our theme. Avoid using props outside of this list, as they will fall back to unstyled default MUI looks.

> The following components can be configured via listed properties

### Actions:

#### 1. Button

- variant: `contained` (exposed as `filled`), `outlined`, `text`
- color: `primary`, `secondary`, `tertiary`, `error`
- size: `small`, `medium`, `large` (heights and paddings are strictly locked)

#### 2. ButtonGroup:

- color: `primary`, `secondary`, `tertiary`

---

### Form Controls:

#### 1. Select

- variant: `filled`, `outlined`

#### 2. TextField

- variant: `standard`, `outlined`

---

### Feedback & Data Display:

#### 1. Alert

- variant: `filled`, `outlined`
- severity: `error`, `warning`, `info`, `success`

#### 2. Chip

- variant: `filled`, `outlined`

- size: `medium` (default), `small`

#### 3. Badge

- variant: `standard`, `dot`
- color: `default`, `primary`, `secondary`, `error`

---

### Surfaces:

#### 1. Paper

- variant: `default`, `discardChangesModal` (custom small modal with 32px rounded corners)

> The following components cannot be configured. They are just for use as is.

### Navigation & Layout:

#### 1. Tabs / Tab

- No custom variants or colors — styles are applied globally

#### 2. Accordion

- No custom variants — styles are applied globally

#### 3. ToggleButtonGroup / ToggleButton

- No custom variants — styles are applied globally

---

### Utility:

#### 1. Checkbox

- No custom variants — checked state is yellow by theme default

#### 2. Modal

- No custom variants — all modals are centered by default

#### 3. Tooltip

- No custom variants — italic text, pill shape, dark background

#### 4. Menu / MenuItem

- No custom variants — styles are applied globally

> **_Note_**: Don't see the variant or color you need? Check if it's in [the Design System](https://www.figma.com/design/IDQ5XmNo6PQBmBlL3DBm6Q/Admin-Liatoshynsky-Foundation?node-id=1-2&p=f&t=N84XpGtbj4BTkldT-0). If it is, please open a ticket to update the `theme.ts` or `colors.ts` instead of using global `sx` overrides. Check the [ theme extending guide](./breakpoints.md) first.

---

[ ← **Return to the title**](./README.md) | [ **Next page** →](./breakpoints.md)
