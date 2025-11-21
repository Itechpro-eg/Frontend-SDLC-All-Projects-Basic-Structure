# Itechpro frontend SDLC + Basic folder structure

# **HMCV Frontend Architecture & Project Structure Standard**

**Version:** 1.0\
**Owner:** Frontend Team Lead\
**Applies to:** All new frontend projects (Next.js / React / TypeScript)

------------------------------------------------------------------------

# **1. Introduction**

This document defines the official frontend **architecture**, **folder
structure**, and **SDLC workflow** for all new projects.

All developers **must follow this standard** to ensure consistency,
scalability, and maintainability across the team.

------------------------------------------------------------------------

# **2. SDLC (Software Development Life Cycle)**

Each new project follows the phases below.\
Deliverables must be completed for every stage.

------------------------------------------------------------------------

## **2.1 Planning & Requirements**

-   Confirm business requirements.
-   List system modules.
-   Define routing structure.
-   Identify needed select menus (static & API-based).
-   Prepare API contract proposals (no integration without approval).

**Deliverables:** - Module list\
- Routing map\
- Select menus list\
- API contracts (draft)

------------------------------------------------------------------------

## **2.2 Design Phase**

-   Create UI wireframes.
-   Define design tokens (colors, spacing, typography).
-   Identify shared UI components.

**Deliverables:** - Wireframes\
- UI tokens\
- Component list

------------------------------------------------------------------------

## **2.3 Architecture & Setup**

-   Initialize project repo.
-   Create folder structure based on **HMCV Model**.
-   Add global utilities (HttpClient, loading, validators).
-   Define routing constants file.

**Deliverables:** - Repo initialized\
- Project scaffold created\
- `/global` folder completed

------------------------------------------------------------------------

## **2.4 Development**

-   Build modules following **HMCV structure**.
-   All logic files must import `HttpClient` from `@/utils/fetch`.
-   No logic inside views.
-   No API integration without approval.

**Deliverables:** - Module-level components, views, logic, types,
container

------------------------------------------------------------------------

## **2.5 Testing**

-   Unit tests for components & logic.
-   Integration tests for page flows.
-   Accessibility tests.

**Deliverables:** - Jest tests\
- Integration tests\
- Accessibility report

------------------------------------------------------------------------

## **2.6 Review & Merge**

PR Checklist: - Follows HMCV structure\
- No API in components/views\
- All logic calls use HttpClient\
- Types are correct\
- Tests included\
- Screenshots added

------------------------------------------------------------------------

## **2.7 Deployment**

-   CI builds\
-   Tests run\
-   Deploy to staging\
-   Manual validation\
-   Deploy to production

------------------------------------------------------------------------

## **2.8 Maintenance**

-   Bug fixes\
-   Documentation updates\
-   Refactoring when necessary

------------------------------------------------------------------------

# **3. Project Folder Structure (Root-Level)**

    /src
    ââ /global
    â  ââ routes.ts
    â  ââ selectMenus/
    â  â  ââ countrySelect.ts
    â  â  ââ educationLevelSelect.ts
    â  ââ utils/
    â  â  ââ fetch.ts
    â  â  ââ loading.ts
    â  â  ââ validators.ts
    â  ââ ui/
    â  ââ hooks/
    ââ /modules
    â  ââ /<ModuleName>/
    â  â  ââ components/
    â  â  ââ views/
    â  â  ââ logic/
    â  â  ââ types/
    â  â  ââ container.tsx
    ââ /pages (or /app)
    ââ main.tsx

------------------------------------------------------------------------

# **4. The HMCV Module Architecture**

Every module must follow the **HMCV** structure:

------------------------------------------------------------------------

## **H --- Module Root Folder**

Location:

    src/modules/<ModuleName>

------------------------------------------------------------------------

## **M --- Components Folder**

    modules/<Module>/components/

Rules: - Components are **private to the module**. - Must be small,
reusable inside module only. - No API calls. - No business logic.

------------------------------------------------------------------------

## **C --- Container**

    modules/<Module>/container.tsx

Responsibilities: - Pulls logic functions. - Passes results to views. -
Handles state & mutations. - Exported as default for routing.

------------------------------------------------------------------------

## **V --- Views Folder**

    modules/<Module>/views/

Rules: - Views = UI layouts/pages for this module. - **No API calls.** -
**No business logic.** - Receive props only.

------------------------------------------------------------------------

# **5. Logic Layer Rules**

Location:

    modules/<Module>/logic/

Rules: - One function per file. - File name = function name. - Must
import HttpClient from '@/utils/fetch'.

------------------------------------------------------------------------

# **6. Module Types Folder**

Contains DTOs, interfaces, API response types.

------------------------------------------------------------------------

# **7. Global Routing Standard**

Location:

    src/global/routes.ts

Exports a constant route object.

------------------------------------------------------------------------

# **8. Global Select Menus Folder**

Location:

    src/global/selectMenus/

One file per select menu.

------------------------------------------------------------------------

# **9. API Integration Policy**

No developer may integrate API calls without approval.

------------------------------------------------------------------------

# **10. HttpClient Global Utility**

All modules must use this client for CRUD operations.

------------------------------------------------------------------------

# **11. Code Conventions**

-   Components: PascalCase\
-   Types: PascalCase\
-   No circular imports\
-   Absolute imports only

------------------------------------------------------------------------

# **12. Testing Standard**

-   Jest unit tests\
-   React Testing Library\
-   Cypress flows

------------------------------------------------------------------------

# **13. CI/CD Requirements**

PR must pass linting, typecheck, tests, and build.

------------------------------------------------------------------------

# **14. PR Template**

(Template included in the main document.)

------------------------------------------------------------------------

# **15. New Project Checklist**

(Full checklist included.)

------------------------------------------------------------------------

# **16. Example Module Structure**

    modules/Users/
    ââ components/
    ââ views/
    ââ logic/
    ââ types/
    ââ container.tsx
