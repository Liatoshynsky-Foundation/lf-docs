# Image Management Concept (MVP)

## Purpose and Scope

Image management allows website administrators to select, replace, and crop images used on Ukrainian and English website pages.

Each image placeholder has a predefined aspect ratio. Administrators can reposition and resize the crop area within that ratio but cannot change the placeholder proportions.

Images can be replaced but not removed from placeholders where an image is required. This prevents published pages from containing empty image areas.

Changes made in the admin panel remain in the working copy and become visible on the public website only after the corresponding language version is published.

## Image Assets and Cropping

An image uploaded to the media library is stored as an **Image Asset** and can be reused across different website pages and placeholders.

The same Image Asset can have different crops depending on where and how it is used. In particular, Ukrainian and English versions of a page can use the same image with independent cropping.

Changing the crop for one language version does not affect the other language version.

When an existing image is opened for cropping, the previously saved crop for the current page, language, and placeholder is used when available. Otherwise, the default crop for the placeholder is displayed.

## Image Actions

Each image block provides two main actions:

- **Змінити зображення** — select another image from previously used images or the media library, or upload a new image.
- **Редагувати зображення** — adjust the crop of the currently selected image.

## Changing an Image

Selecting **Змінити зображення** opens the image selection dialog with the following tabs:

### Використані

Displays images already used in the corresponding placeholder across the Ukrainian and English versions of the page.

Language badges identify the corresponding version. If the same image has different crops in Ukrainian and English, each version is displayed separately.

Selecting an image from another language version reuses both the image and its current crop. The administrator can then keep the existing crop or adjust it before applying the image.

### Галерея

Displays public Image Assets available in the media library.

Administrators can search and sort available images and select one for the current placeholder. After selection, the image opens in the cropping dialog.

### Завантажити

Allows administrators to upload new images from their device.

Multiple files can be uploaded to the media library at once, but only one image can be selected for a particular placeholder.

After an image is selected, it opens in the cropping dialog.

## Cropping an Image

Selecting **Редагувати зображення**, or choosing a new image, opens the cropping dialog.

The dialog displays the image and a crop frame with the predefined aspect ratio of the current placeholder. Administrators can resize and reposition the frame without changing its aspect ratio.

Available actions:

- **Застосувати** — save the crop for the current page, language, and placeholder and return to the page editor.
- **Скасувати** — discard unsaved changes.
- **Х** — close the dialog without applying changes.

Clicking outside the dialog does not apply or discard changes.

After selecting **Застосувати**, the updated image preview is displayed in the page editor. The change becomes visible on the public website only after the corresponding language version is published.

## Working with Ukrainian and English Versions

Ukrainian and English pages maintain independent image crops.

Administrators can reuse an image and crop from another language version through the **Використані** tab. Selecting an image marked with another language initializes the cropping dialog with that version's crop.

The administrator can apply the crop without changes or adjust it for the current language version.

Subsequent changes remain independent. Updating the crop in one language version does not automatically update the other.

## Image Validation

Supported image formats:

- JPG
- PNG
- WebP
- SVG

The following formats are not supported:

- TIFF
- PSD
- HEIC
- GIF

The maximum file size is **20 MB**. Files larger than **5 MB** trigger a warning but may still be uploaded.

Minimum recommended resolution:

- **Hero images and banners:** 2400 px on the longest side
- **Cards and gallery images:** 1600 px on the longest side

Images exceeding **6000 px** on the longest side must be rejected or automatically resized during upload, depending on the selected implementation approach.

Uploaded images are normalized for website use, including orientation and color profile processing where required.

Validation is performed before the upload is completed, and clear validation messages are displayed when an image does not meet the requirements.

If an image is required for a particular placeholder, the page cannot be published without a valid image.