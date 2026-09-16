# Alt Text Management

## Decision

Alt text is specified for each individual use of an image rather than for the Image Asset itself in the media library.

## Rationale

The same Image Asset can be reused:

- in different content contexts;
- on different pages;
- in different language versions.

Therefore, alt text must describe the image **in its specific context of use** and be localized where applicable. Asset-level alt text could lead to incorrect descriptions and unnecessary duplication.

## Implementation

- **Static content blocks:** Alt text is edited in the block properties next to the image **Upload / Remove** controls.
- **Dynamic content (Новини та події):** Alt text is defined when inserting or editing an image in the content editor (Tiptap Image node).

## Validation

- Alt text is required for visible, non-decorative images.
- Decorative images do not require alt text and are marked as decorative (`aria-hidden`).
