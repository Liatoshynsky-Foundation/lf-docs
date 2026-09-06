# LIATOSHYNSKY PROJECT

## Business Requirements and Project Scope Document

**By:** Oleksii Onatskyi  
**Version:** 2.0

## Revision History

| Date | Version | Description | Author |
| --- | --- | --- | --- |
| 20/06/2025 | 1.0 | Added the Project context section | Oleksii Onatskyi |
| 02/09/2026 | 2.0 | Added the Business requirements section. Reviewed the existing content. | Oleksii Onatskyi |

# 1 Project Context

This section provides the background and business context for the Lyatoshynsky Foundation website project. It introduces the Foundation and key stakeholders, describes the current situation and desired future state, defines the business problem the project aims to address, and identifies the primary target audiences for the website.

## 1.1 Client Background

The client is the Lyatoshynsky Foundation. Tetiana Vasylivna Homon is the head of the organization and its director. The foundation focuses on researching the life and creative legacy of composer Borys Mykolayovych Lyatoshynsky, as well as promoting his work and distributing musical scores.

Although the foundation is based on the figure of Lyatoshynsky, its activities are not limited to him. They are aimed at studying Ukrainian music of the 20th and 21st centuries and promoting academic classical Ukrainian music from those periods both in Ukraine and abroad.

A considerable amount of material related to the composer’s life and work has been preserved. These materials are stored on physical media, mostly paper.

The foundation is also engaged in digitizing these materials and preserving them in digital format — a long and ongoing process.

## 1.2 Client Team

Tetiana Vasylivna Homon is the head of the organization and its director.

Iryna Tukova is a Ukrainian musicologist, lecturer, educator, and author of nonfiction books on the history of classical music.

Mariia Gurska is a content and communications professional specializing in writing, editing, content strategy, and AI linguistic training. She is also a former journalist.

## 1.3 As Is

The Lyatoshynsky Foundation currently has no centralized, modern, and official online platform.

## 1.4 To Be

The Foundation has a centralized, modern, official online presence that improves public visibility, trust, and transparency, while providing a reliable and user-friendly resource for everyone interested in Borys Lyatoshynsky’s legacy.

## 1.5 Problem Statement

The absence of such a resource prevents the foundation from systematically sharing verified information about the composer’s life, works, and artistic heritage, hinders direct communication with audiences and partners, and limits the ability to attract financial and organizational support.

This also results in fragmented and incomplete online representation of Borys Lyatoshynsky’s legacy, both in Ukraine and internationally. Classical music institutions, performers, researchers, and enthusiasts lack a clear and reliable point of access to information, materials, and archives.

## 1.6 The Audience

The primary target audience is the general public. The following user groups can also be identified:

- Students
- Music groups and ensembles
- Individual musicians
- Musicologists (a higher-priority audience than cultural studies specialists)
- Cultural studies specialists
- Listeners, including music enthusiasts and people who, at some point in their lives, decide to explore Liatoshynsky’s music
- Managers and other employees of institutions and organizations where classical music is performed
- Influencers and reviewers in the cultural sphere
- Researchers and academics

# 2 Business Requirements

## BR-1 Unified Official Platform with Public Archive (Single CMS)

### Need

The Lyatoshynsky Foundation requires an official website that delivers institutional and narrative content, as well as a public, searchable digital archive.

### Acceptance at Launch

Public pages and archive pages are searchable and browsable without login.

> **Note:** Institutional and narrative content defines the Foundation’s purpose, values, and history, and supports a coherent information architecture that enables users to easily navigate and find information.

## BR-2 Comprehensive Public Information about Borys Lyatoshynsky

### Need

The Lyatoshynsky Foundation requires the publication of comprehensive information about Borys Lyatoshynsky, including biography, works (performance materials), and photographs.

### Acceptance at Launch

- Dedicated Biography and Works sections are published.
- Pictures are published on website pages with appropriate rights statements and captions where applicable.

## BR-3 Publicly Available Research and Scientific Works Related to Borys Lyatoshynsky’s Life and Work

### Need

The Lyatoshynsky Foundation requires the publication of comprehensive information about Borys Lyatoshynsky’s works (including manuscripts) and related third-party research.

### Acceptance at Launch

A dedicated “Research and Scientific Works” section is published, listing both the Foundation’s materials and third-party research.

## BR-4 Multilingual Availability Now and in the Future (with Manual Duplication Constraint)

### Need

The Lyatoshynsky Foundation requires the website to support both Ukrainian and English. The development team provides the technical capability for multilingual content, including locale-specific pages and URLs, while the Foundation team is responsible for preparing and providing translations.

### Acceptance at Launch

- Ukrainian (UA) and English (EN) versions are supported for all public templates, including Pages, Works, and Item records, with locale-specific URLs.
- Missing translations fall back gracefully and are clearly identified in the admin UI.
- A documented workflow exists for developer-led page duplication and linking for new locales. The Foundation team provides the translated content.

## BR-5 Performer and Institution Access to Materials (Two-Tier Model with Preview/Download)

### Need

The Lyatoshynsky Foundation requires a system that provides performers and institutions with two-tier access: some materials are publicly available, while others are accessible upon request. Digital files must support in-browser preview and download, with clear per-item indicators.

### Acceptance at Launch

- Public items: preview and download are available without login (where permitted).
- Restricted items: a “Request access” flow is implemented according to the approved design.
- Each item clearly indicates available actions (Preview, Download, Request).

## BR-6 Sustainable Support: Donations and Community Contributions

### Need

The Lyatoshynsky Foundation requires a sustainable online fundraising channel via an integrated payment provider (with processing handled on the provider’s side), as well as a parallel pathway for community contributions (time and skills). The Foundation must retain ownership of content and communications in these areas.

### Acceptance at Launch

- Donation flow is integrated with the selected provider; donors see success/failure states and receive confirmation upon return.
- Volunteer/contributor flow is live (skills intake form with admin review workflow).
- Website administrators can create and update campaign pages and volunteer calls directly in the CMS; email notifications are sent to administrators upon new submissions.

# 3 In Scope

The project proposes to develop an official website for the Borys Lyatoshynsky Foundation — a structured, multilingual, and accessible single-CMS online platform that delivers both narrative pages and a public, searchable digital archive (search limited to the archive) containing:

- Biographical materials and verified information about the composer.
- Digitized sheet music, audio recordings, and archival materials.
- A public archive and database of compositions with archive-specific search, filtering, and preview tools. Global search across website pages is not included; visitors navigate website content through the site navigation.
- Forms for public engagement: sheet music requests, feedback, volunteer applications — including the verified two-tier access flow (public vs. upon-request) for restricted materials.
- Tools for collecting financial support and donations via an integrated payment provider with provider-side processing.
- Dedicated sections for the foundation’s initiatives, events, and partnerships.

The website will improve public visibility, trust, and transparency for the foundation’s work, while offering a reliable and user-friendly resource for all interested in the composer’s legacy.

Additionally, an admin panel will be developed to allow the foundation team to independently (without developers' help) manage content on existing pages and within existing locales without breaking the site’s design and structure. Editors will not create new pages; the panel provides minimal, essential functionality. Language additions and page duplication are performed by developers. Basic accessibility considerations will be implemented by SoftServe team.

# 4 Out of Scope

- Content creation.
- Translation.
- SEO settings and marketing campaigns related to website release.
- Website administration by SoftServe team.
- Global search across website pages (visitors navigate website content through the site navigation.)

# 5 Assumptions

The Foundation team will provide prepared and reviewed content for all website pages.

The Foundation team will provide information required for development, consultations, and feedback within five business days. The team is expected to remain available and responsive throughout the project.

A simplified implementation approach is acceptable for the MVP.

The SoftServe team is expected to have sufficient resources to deliver the MVP at an appropriate level of quality within a reasonable timeframe, taking into account the actual effort required to complete the work.

# 6 Dependencies

The project depends on:

- sufficient availability of SoftServe Academy students to participate in project implementation;
- timely delivery of the required content by the Foundation team;
- timely payment and continued availability of third-party services managed by the Foundation, including hosting, the domain name, and the WayForPay payment account.

# 7 Constraints

The project is subject to the following constraints:

- Neither the Foundation nor SoftServe has a dedicated specialist responsible for content preparation and marketing-related activities.
- The Foundation does not yet have all the content required for the initial website launch. Content preparation is still in progress.
- The project must use the technology stack recommended by SoftServe Academy to enable Academy students to participate in implementation. This limits the use of alternative tools that might otherwise meet project needs, such as Webflow.
- As this is a pro-bono project, not all team members can dedicate 40 hours per week to project activities.
- The Foundation has a limited budget for third-party services. The approximate target is no more than USD 20 per month.
- Potential website administrators from the Foundation team have limited technical knowledge. This must be considered when designing the admin panel and preparing documentation for the services and administrative functionality.
- Legal restrictions may apply to the publication and use of certain content on the website.

# 8 Timeline and Delivery Commitments

As this is a pro-bono project, no fixed delivery deadline has been established, and the SoftServe team does not make a strict commitment to a specific delivery date.

# 9 Risks

The following project risks have been identified:

- Insufficient SoftServe team capacity due to limited availability of contributors to the pro-bono project or other resource constraints.
- Limited stakeholder engagement from the Foundation team, which may delay decisions, reviews, or delivery of required information.
- Unavailability of key project roles, including designers, Business Analysts, Project Managers, Technical Experts, or DevOps specialists.
- Third-party service continuity risks, including hosting availability, domain expiration, and payment service account status. The operation of the website may be affected if required subscriptions or services are not renewed or maintained on time.