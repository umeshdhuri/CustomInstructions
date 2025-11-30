# Code Generation Architecture & Development Guidelines

These guidelines ensure that all code generated through the MCP
Figma-to-Code pipeline using Gemini strictly follows the existing
project architecture, coding conventions, and UI/UX framework.

------------------------------------------------------------------------

## 1. Purpose

The purpose of this document is to provide clear architectural, coding,
and design rules that Gemini must follow when generating code from Figma
ViewControllers via the MCP server.\
All generated code must match the existing project structure, reuse
existing components, and comply with established patterns.

------------------------------------------------------------------------

## 2. Project Architecture Guidelines

### 2.1 Folder Structure

All generated code must be placed in the correct directory:

    src/
      components/
      ViewControllers/
      services/
      hooks/
      utils/
      assets/

**Rules** - UI Screens → `src/ViewControllers` - Reusable components →
`src/components` - Business logic → `src/services` - Shared logic →
`src/hooks` - Helper functions → `src/utils` - No new folders should be
created unless absolutely necessary.

------------------------------------------------------------------------

## 3. Component & Code Structure

### 3.1 Component Architecture

-   Use **functional components only**.
-   Keep UI logic inside ViewControllers.
-   Move reusable UI parts to `components/`.
-   Do not add business logic to UI files.
-   Each component must be small, modular, and reusable.

### 3.2 State Management

Follow the project's **existing state management** approach.\
Do **not** introduce new libraries.

------------------------------------------------------------------------

## 4. Styling & UI Rules

### 4.1 Styling Standards

-   Use the project's **existing design tokens** (colors, fonts, radius,
    spacing, shadows).
-   Avoid hardcoded values.
-   Follow the existing styling method (CSS/Tailwind/Styled
    Components/Moddable skins).
-   UI must match the Figma design exactly while following project style
    rules.

### 4.2 Component Reuse Rules

-   Always reuse existing components before creating new ones.
-   If a component already exists, do not generate duplicates.
-   Create a new component only when there is no existing reusable
    pattern.

------------------------------------------------------------------------

## 5. API & Services Layer Rules

### 5.1 API Pattern Requirements

-   All API logic must live under `src/services/api`.
-   Use the existing API wrapper for requests, error handling, and
    transforms.
-   Do not call APIs directly from components.

------------------------------------------------------------------------

## 6. Naming Conventions

-   **Components:** `PascalCase`
-   **Variables & functions:** `camelCase`
-   **Constants:** `UPPER_SNAKE_CASE`
-   **File names:** `kebab-case` (or project default)
-   **ViewControllers:** `<Name>Screen.swift`

------------------------------------------------------------------------

## 7. Figma → Code Conversion Rules

Gemini must:

### 7.1 Required Behavior

-   Map Figma layout to the project's layout system.
-   Use spacing, typography, and color tokens.
-   Reuse existing components.
-   Keep code consistent with existing architecture.
-   Place new files in the correct folder.

### 7.2 Prohibited Behavior

-   No new libraries.
-   No inline/hardcoded colors.
-   No duplicate components.
-   No changes to folder structure.
-   No altering existing architecture.

------------------------------------------------------------------------

## 8. Error Handling & Logging

-   Use the existing logger service for all logs.
-   Use structured `try/catch` blocks.
-   Show user errors only using the approved UI method
    (Toast/Alert/Dialog based on project).

------------------------------------------------------------------------

## 9. File Documentation Requirements

Each generated file must begin with:

    /**
     * Generated via MCP Figma-to-Code process.
     * This file adheres to the project's architecture, patterns, and coding guidelines.
     */

------------------------------------------------------------------------

## 10. Testing Requirements

-   Follow the existing test folder structure:

```{=html}
<!-- -->
```
    __tests__/
      components/
      ViewControllers/
      services/

-   Each newly generated component must include:
    -   A basic render test.
    -   A snapshot test (if the project uses snapshots).

------------------------------------------------------------------------

## 11. Version Control Rules

### 11.1 Branch Naming Format

    feature/<module-name>-<figma-screen-name>

### 11.2 Commit Message Format

    feat(HMI): Add <screen-name> screen from Figma

------------------------------------------------------------------------

## 12. General Rules for Gemini Code Generation

### MUST Do

✔ Follow architecture\
✔ Reuse components\
✔ Match design tokens\
✔ Keep code modular\
✔ Use existing helpers\
✔ Maintain coding conventions

### MUST NOT Do

✘ Add new dependencies\
✘ Hardcode values\
✘ Duplicate components\
✘ Modify architecture\
✘ Place logic in UI files

------------------------------------------------------------------------

## End of Instructions

Gemini must follow these rules every time it generates code through the
MCP server from a Figma design.
