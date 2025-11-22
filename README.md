# **Itechpro HMCV Frontend Architecture & Project Structure Standard**

**Version:** 1.0\
**Owner:** [Ahmed Amin](https://github.com/ahmedamin20)\
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

   /project-name
├─ /src\
│  ├─ /global\
│  │  ├─ routes.ts                # global routes object (exported)\
│  │  ├─ selectMenus/             # select menus (one file per select menu)\
│  │  │  ├─ countrySelect.ts\
│  │  │  └─ educationLevelSelect.ts\
│  │  ├─ utils/\
│  │  │  ├─ fetch.ts              # HttpClient (must be imported by logic files)\
│  │  │  ├─ loading.ts            # global loading / spinner utilities\
│  │  │  └─ validators.ts\
│  │  ├─ ui/                      # shared UI primitives, tokens\
│  │  └─ hooks/                   # global hooks\
│  ├─ /modules\
│  │  ├─ /<ModuleName>            # e.g., Users, Hotels, Courses\
│  │  │  ├─ components/           # module-private small components\
│  │  │  │  └─ CardHeader.tsx\
│  │  │  ├─ views/                # view pages used by routes (presentational)\
│  │  │  │  └─ ListView.tsx\
│  │  │  ├─ logic/                # logic files (one function per file)\
│  │  │  │  ├─ getAll.ts\
│  │  │  │  ├─ create.ts\
│  │  │  │  ├─ update.ts\
│  │  │  │  └─ delete.ts\
│  │  │  ├─ types/                # TS interfaces and types specific to module\
│  │  │  │  └─ index.ts\
│  │  │  ├─ container.tsx         # composes logic & view, exports default container\
│  │  │  └─ index.ts               # re-exports public module parts (optional)\
│  ├─ /pages (or /app)            # depending on Next.js routing approach\
│  └─ main.tsx                    # root app file\
├─ /public\
├─ /scripts\
├─ jest.config.js\
├─ .eslintrc.js\
├─ tsconfig.json\
└─ package.json\


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

modules/Users/\
├─ components/\
│  └─ UserCard.tsx\
├─ views/\
│  └─ ListView.tsx\
├─ logic/\
│  ├─ getAll.ts\
│  ├─ create.ts\
│  └─ update.ts\
├─ types/\
│  └─ index.ts\
└─ container.tsx\


