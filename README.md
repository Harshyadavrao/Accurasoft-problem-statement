# Tech.Care Patient Dashboard

A single-page patient dashboard that displays health information for Jessica Taylor by fetching data from the Coalition Technologies Patient Data API.

## Tech Stack

- **React 19** + **TypeScript**
- **Vite** (build tool)
- **Tailwind CSS v4** (styling)
- **Recharts** (blood pressure chart)
- **Lucide React** (icons)
- **shadcn/ui** (UI components)

## Project Structure

```
src/
├── assets/          # Static images and SVGs
├── lib/             # Utility functions (cn, etc.)
├── App.tsx          # Root component
├── App.css          # App-level styles
├── main.tsx         # Entry point
└── index.css        # Global styles / Tailwind imports
public/
├── icons.svg        # Icon sprites
└── favicon.svg      # Favicon
```

## API Details

- **Endpoint:** `GET https://fedskillstest.coalitiontechnologies.workers.dev`
- **Auth:** HTTP Basic Auth
  - Username: `coalition`
  - Password: `skills-test`
- Credentials must be Base64-encoded at runtime using `btoa()` — do not hardcode the encoded key.
- The API returns an array of patients. Only **Jessica Taylor's** data is displayed.

## API Response Shape

Each patient object contains:

| Field              | Type     | Description                                      |
|--------------------|----------|--------------------------------------------------|
| name               | string   | Patient full name                                |
| gender             | string   | Gender                                           |
| age                | number   | Age                                              |
| profile_picture    | string   | URL to profile photo                             |
| date_of_birth      | string   | ISO date string (e.g. `1996-08-23`)              |
| phone_number       | string   | Phone number                                     |
| emergency_contact  | string   | Emergency contact number                         |
| insurance_type     | string   | Insurance provider name                          |
| diagnosis_history  | array    | Monthly records (BP, heart rate, resp, temp)     |
| diagnostic_list    | array    | Diagnosed conditions with status                 |
| lab_results        | array    | List of lab test names (strings)                 |

## Page Sections

1. **Patient List** (left sidebar) — scrollable list of all patients
2. **Diagnosis History** (center) — blood pressure line chart over 6 months
3. **Vital Signs Cards** (center) — heart rate, respiratory rate, temperature
4. **Diagnostic List** (center) — table with condition name, description, status
5. **Patient Profile** (right sidebar) — personal details (DOB, phone, insurance, etc.)
6. **Lab Results** (right sidebar) — downloadable list of test names

## Getting Started

### Prerequisites

- Node.js >= 18
- pnpm (recommended) or npm

### Install & Run

```bash
# Install dependencies
pnpm install

# Start dev server
pnpm dev

# Build for production
pnpm build

# Preview production build
pnpm preview
```

## Scripts

| Command         | Description                  |
|-----------------|------------------------------|
| `pnpm dev`      | Start Vite dev server (HMR)  |
| `pnpm build`    | TypeScript check + Vite build |
| `pnpm lint`     | Run ESLint                   |
| `pnpm preview`  | Preview production build     |

## Collaboration

This project is split between two contributors:

| Person 1 (Frontend/UI)              | Person 2 (JS Logic/Data)                  |
|--------------------------------------|-------------------------------------------|
| HTML structure, layout, components   | API fetch + Basic Auth                    |
| CSS / Tailwind styling              | Data filtering (Jessica Taylor)           |
| Responsiveness, design matching      | Chart data transformation for Recharts    |
| Static assets and icons              | Vitals extraction, DOM population logic   |

### Branch Strategy

- `main` — stable, merged code
- `frontend/ui-design` — Person 1's branch
- `backend/data-layer` — Person 2's branch

Both merge into `main` via pull requests.
