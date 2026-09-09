The feature allows an administrator to select one MP3 file from the existing «Файли» section as the main composition (primary audio track) used first in the site audio player.

## User stories within this feature
[link to 1564](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1564) US_Admin_Main Composition-01 — Displaying the «Зробити головною композицією» Action

[link to 1565](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1565) US_Admin_Main Composition-02 — Selecting the Main Composition 

[link to 1566](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1566) US_Admin_Main Composition-03 — Changing the Main Composition 

[link to 1567](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1567) US_Admin_Main Composition-04 — Displaying the Main Composition Status 

[link to 1568](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1568) US_Admin_Main Composition-05 — Blocking Deletion of the Main Composition 

[link to 1569](https://github.com/Liatoshynsky-Foundation/lf-client/issues/1569) US_Admin_Main Composition-06 — VISITOR Playing the Main Composition in the Audio Player 

## 1. Context
The Lyatoshynsky Foundation website already has an audio player implemented in the site Header. The admin panel also already includes the **«Файли»** section, where the administrator can upload files to the media library.

Within this feature, it is necessary to implement the ability to select the main composition through the admin panel.

The main composition is an audio recording that:

* is displayed first when the audio player is launched for the first time;
* starts playing when the user interacts with the intro section on the homepage.

The administrator must be able to change the main composition independently, without involving a developer.

If the administrator has not selected a main composition, the system uses the default composition set up by the development team. 
> 📝 Note: the exact audio track to be provided by the Foundation team.

## 2. Scope

### In Scope

Within this feature, it is necessary to:

1. Add the **«Зробити головною композицією»** action for MP3 files in the **«Файли»** section.
2. Allow only one main composition at a time.
3. Automatically remove this status from the previous composition when a new main composition is selected.
4. Visually mark the current main composition in the media library.
5. Block deletion of the file that is currently set as the main composition.
6. Use the selected composition as the first one when the audio player is launched for the first time.
7. Use the selected composition when audio is started from the homepage intro section.
8. Use **«Поему про ліс»** as a fallback if the administrator has not selected another main composition.

### Out of Scope

This feature does not include:

* creating a new audio player;
* redesigning the existing audio player;
* developing a file upload mechanism;
* creating a separate playlist editor;
* manual sorting of the playback queue;
* integration with YouTube, Spotify, or other external services;
* implementing an audio file usage tracker;
* changing the already implemented logic of continuous playback between pages.

## 3. Actors

### Website Administrator

A Foundation representative who works with content through the admin panel.

The administrator does not necessarily have technical knowledge, so selecting the main composition must be simple and clear.

### Website Visitor

A user of the public part of the website who can listen to compositions through the already implemented audio player.

## 4. Existing Functionality and Dependencies

The feature uses existing system components:

* audio player in the Header;
* Play / Pause and other basic player controls;
* display of information about the current composition;
* **«Файли»** section in the admin panel;
* uploading files to the media library;
* file context menu;
* continuous audio playback while navigating between pages.

This functionality is not reimplemented but is used as a dependency for the new feature.

## 5. Functional Requirements

### FR-01. Action Display

For MP3 files, the following action must be available in the context menu:

**«Зробити головною композицією»**

For other file types, this action must not be displayed.

### FR-02. Main Composition Selection

After selecting the **«Зробити головною композицією»** action, the system must assign the selected MP3 file as the main composition and save the changes.

### FR-03. Single Main Composition

There can be only one main composition in the system at a time.

If the administrator selects a new main composition, the previous one automatically loses this status.

### FR-04. Status Display

Next to the current main composition in the **«Файли»** section, the following status must be displayed:

**«Головна композиція»**

### FR-05. Deletion Blocking

The system must not allow deletion of a file that currently has the main composition status.

When deletion is attempted, the operation is blocked, and the administrator is shown the corresponding message.

### FR-06. Deletion of the Previous Composition

After another file is assigned as the main composition, the previous file can be deleted using the standard scenario.

### FR-07. Use in the Audio Player

The main composition selected by the administrator must be used as the first composition when the audio player is launched for the first time.

### FR-08. Default Composition

If the administrator has not selected a custom main composition, the system must use the default one set up by the development team. 
> 📝 Note: the exact audio track to be provided by the Foundation team.

## 6. Non-Functional Requirements

### NFR-01. Usability

The functionality must be clear to an administrator without technical knowledge and without additional instructions.

For this purpose, unambiguous labels are used:

* **«Зробити головною композицією»**
* **«Головна композиція»**

### NFR-02. Consistency

The new functionality must use the existing components, styles, and UI patterns of the admin panel.

### NFR-03. Reliability

After successful saving, the selected main composition must not be lost after:

* refreshing the page;
* reopening the **«Файли»** section;
* logging in to the admin panel again.

### NFR-04. Compatibility

The feature implementation must not break the operation of:

* the existing audio player;
* the media library;
* the **«Музичний твір»** form;
* the existing playback logic.

## 7. Business Rule

### BR-01

Only audio recordings for which the Foundation has the necessary rights or permission to use may be used on the website.

## 8. Edge Cases

### EC-01. Sequential Selection of Multiple Files

If the administrator sequentially assigns several MP3 files as the main composition, the last selected file remains the main one.

### EC-02. Re-selecting the Current Main Composition

If the administrator selects again a file that is already the main one, the system must not create a duplicate status or return an error.

### EC-03. Main Composition Not Selected

If the administrator has not assigned a custom main composition, the system uses **«Поему про ліс»**.

### EC-04. Attempt to Delete the Main Composition

If the administrator attempts to delete the current main file, the operation is blocked.