# Tasks: Portfolio Web

**Input**: Design documents from `specs/001-portfolio-web/`

**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, quickstart.md

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [x] T001 Create project structure (create `index.html` and `style.css` empty files) in the root directory

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

- [x] T002 Configure base HTML5 boilerplate with meta tags for SEO/viewport in `index.html`
- [x] T003 Set up CSS variables (custom properties) for the "Verde Vibrante" palette (#00D84F, etc.) and base font settings in `style.css`
- [x] T004 Implement CSS reset and base layout styling (body margins, typography, default links) in `style.css`

---

## Phase 3: User Story 1 - Apresentação Pessoal e Navegação (Priority: P1) 🎯 MVP

**Goal**: Visitante acessa o portfólio, visualiza a Navbar e o Hero, e consegue navegar.

**Independent Test**: Navbar renderizada corretamente e botão do hero redireciona para a seção alvo na página (mesmo sem estilo avançado).

### Implementation for User Story 1

- [x] T005 [P] [US1] Build the `<nav>` sticky bar structure in `index.html`
- [x] T006 [P] [US1] Build the Hero section (saudação, subtítulo, CTAs) in `index.html`
- [x] T007 [P] [US1] Build the "Sobre" section in `index.html`
- [x] T008 [US1] Style the Navbar and Hero components (including hover states and flexbox layout) in `style.css`

---

## Phase 4: User Story 2 - Projetos de Engenharia de Dados (Priority: P1)

**Goal**: Exibir grid responsivo com cards de projetos de Dados.

**Independent Test**: Cards são exibidos e links clicáveis abrem em nova aba.

### Implementation for User Story 2

- [x] T009 [P] [US2] Create the "Engenharia de Dados" `<section>` wrapper structure with appropriate ID in `index.html`
- [x] T010 [US2] Structure the "Project Card" HTML markup based on `data-model.md` inside the section in `index.html`
- [x] T011 [US2] Populate 3 dummy/placeholder project cards for Data Engineering in `index.html`
- [x] T012 [US2] Style the Project Card component (badges, CSS Grid layout, hover border effects) in `style.css`

---

## Phase 5: User Story 3 - Projetos de DevOps (Priority: P1)

**Goal**: Exibir grid responsivo com cards de projetos de DevOps.

**Independent Test**: Seção visível mantendo o mesmo padrão visual e funcional de cards.

### Implementation for User Story 3

- [x] T013 [P] [US3] Create the "DevOps" `<section>` wrapper structure with appropriate ID in `index.html`
- [x] T014 [US3] Populate 3 dummy/placeholder project cards for DevOps (reusing the HTML card structure from US2) in `index.html`

---

## Phase 6: User Story 4 - Contato e Redes Profissionais (Priority: P2)

**Goal**: Links de contato e rodapé organizados na parte inferior da página.

**Independent Test**: Ícones de redes sociais redirecionam externamente ao clicar.

### Implementation for User Story 4

- [x] T015 [P] [US4] Create the "Contato" `<section>` and `<footer>` structures in `index.html`
- [x] T016 [US4] Style the contact links and footer text layout in `style.css`

---

## Phase 7: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [x] T017 Test and refine mobile responsiveness via CSS Media Queries (max-width) to ensure the 1-column layout works properly in `style.css`
- [x] T018 Test accessibility (color contrast, semantic tags, alt texts) in `index.html`
- [x] T019 Update `README.md` with project description and run instructions
- [x] T020 Run `quickstart.md` validation scenarios manually to ensure everything works end-to-end

---

## Dependencies & Execution Order

- **Setup (Phase 1)** & **Foundational (Phase 2)**: BLOCKS all user stories.
- **US1, US2, US4**: Can run in parallel after foundational, as they define distinct HTML blocks.
- **US3**: Depends partially on US2 for the established card HTML structure.

### Parallel Opportunities

- HTML structure tasks (T005, T006, T007) can be built in parallel.
- `index.html` layout tasks can be done before or alongside `style.css` base styling.

## Implementation Strategy

### MVP First (User Story 1 Only)
1. Complete Foundational CSS.
2. Complete US1 (Navbar + Hero).
3. Validate locally.

### Incremental Delivery
1. Add Data Engineering section and CSS Grid (US2).
2. Add DevOps section (US3).
3. Add Footer (US4).
4. Run final responsiveness and quickstart validations.
