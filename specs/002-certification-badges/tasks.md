# Tasks: Vitrine de Certificações e Badges

**Input**: Design documents from `/specs/002-certification-badges/`

**Prerequisites**: plan.md, spec.md, data-model.md, research.md, quickstart.md

**Tests**: Tests are OPTIONAL for this feature — only manual validation per quickstart.md is defined.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Prepare asset directory and conventions for badge images

- [x] T001 Create directory `assets/badges/` per plan.md project structure
- [x] T002 [P] Create `assets/badges/README.md` documenting naming conventions, image specs (200×200px, ≤30KB, WebP preferred), and `.gitkeep` if empty

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Confirm CSS design tokens required by the cert section exist in the existing stylesheet

**⚠️ CRITICAL**: No user story work should assume missing CSS custom properties

- [x] T003 Verify `style.css` contains required CSS custom properties in `:root` for cert section (`--color-bg-white`, `--color-card-bg`, `--color-border`, `--radius-md`, `--radius-sm`, `--shadow-card`, `--shadow-card-hover`, `--color-text-main`, `--color-text-muted`, `--color-primary`, `--color-primary-dark`, `--transition-speed`). Append any missing tokens to `:root`.

**Checkpoint**: Foundation ready — all CSS tokens verified

---

## Phase 3: User Story 1 — Visualizar Certificações na Página (Priority: P1) 🎯 MVP

**Goal**: O portfólio exibe uma seção dedicada com badges visuais de certificações, incluindo imagem, nome e emissor.

**Independent Test**: Abrir `index.html` no navegador — a seção `#certificacoes` deve aparecer com pelo menos o badge AWS Cloud Practitioner visível, nome e emissor legíveis, sem erros no console.

### Implementation for User Story 1

- [ ] T004 [P] [US1] Add `#certificacoes` section HTML to `index.html` (after DevOps section, before Contato) with `.section-header` (badge, h2, desc) and `.cert__grid` containing first `article.cert-card` for AWS Cloud Practitioner, including `img` with `loading="lazy"`, `width="100"`, `height="100"`, and descriptive `alt` text
- [ ] T005 [P] [US1] Add `.cert`, `.cert__grid`, `.cert-card`, `.cert-card__badge-wrap`, `.cert-card__badge-img`, `.cert-card__info`, `.cert-card__name`, `.cert-card__issuer` styles to `style.css` with responsive grid `auto-fill minmax(160px, 1fr)`, card hover effects, and mobile breakpoint `@media (max-width: 600px)`
- [ ] T006 [P] [US1] Add AWS Cloud Practitioner badge image to `assets/badges/aws-cloud-practitioner.webp` (≤200×200px source, ≤30KB, optimized WebP; render at 100×100px in CSS)

**Checkpoint**: User Story 1 fully functional — section renders with visible badge(s)

---

## Phase 4: User Story 2 — Verificar Autenticidade de uma Certificação (Priority: P2)

**Goal**: Badges que possuem URL de verificação exibem um link "Verificar →" que abre a página oficial em nova aba.

**Independent Test**: Clicar no link de verificação do card AWS Cloud Practitioner abre nova aba com a página do emissor (Credly/AWS/etc.).

### Implementation for User Story 2

- [ ] T007 [P] [US2] Add verification link `a.cert-card__verify` inside AWS Cloud Practitioner card in `index.html` with `href="https://www.credly.com/badges/..."` (or confirmed URL), `target="_blank"`, `rel="noopener noreferrer"`, and `aria-label`
- [ ] T008 [P] [US2] Add `.cert-card__verify` styles to `style.css` (font-size, color `var(--color-primary)`, hover color `var(--color-primary-dark)`, transition)

**Checkpoint**: User Stories 1 AND 2 independently functional — section renders and verification link works

---

## Phase 5: User Story 3 — Navegar pela Seção via Menu (Priority: P3)

**Goal**: O menu de navegação principal possui item "Certificações" que leva à seção via âncora `#certificacoes`.

**Independent Test**: Clicar em "Certificações" no navbar rola suavemente até a seção `#certificacoes`.

### Implementation for User Story 3

- [ ] T009 [US3] Add `<a href="#certificacoes" class="navbar__link">Certificações</a>` to `index.html` navbar, positioned between the DevOps link and the Contato/CTA link

**Checkpoint**: User Stories 1, 2, AND 3 independently functional

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Quality assurance, accessibility, performance, and manual validation

- [ ] T010 [P] Validate HTML structure in `index.html` has no unclosed tags, duplicate IDs, or malformed markup in the `#certificacoes` section
- [ ] T011 [P] Validate responsive grid behavior per `quickstart.md` Validation 3 — test breakpoints 320px, 375px, 600px, 900px, 1200px+ in browser DevTools; confirm no overflow or overlap
- [ ] T012 [P] Validate 100% alt text compliance per `quickstart.md` Validation 4 — confirm every `.cert-card__badge-img` has non-empty `alt` matching pattern `Badge de certificação: [Nome] — [Emissor]`
- [ ] T013 Validate asset performance per `quickstart.md` Validation 6 — confirm `assets/badges/` total ≤500KB and each file ≤30KB
- [ ] T014 Run complete `quickstart.md` validation scenarios 1–6 (Basic opening, Anchor nav, Responsive, Alt text, Verification links, Performance) and confirm all success criteria pass

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies — can start immediately
- **Foundational (Phase 2)**: Depends on Setup — verify CSS tokens before styling tasks
- **User Stories (Phase 3–5)**: All depend on Foundational (Phase 2)
  - Story sequence: US1 → US2 → US3 (sequential due to shared `index.html`/`style.css` file editing)
- **Polish (Phase 6)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2). No dependencies on other stories.
  - T004, T005, T006 are parallel (different files: `index.html`, `style.css`, `assets/badges/`)
- **User Story 2 (P2)**: Can start after US1 completes — requires `.cert-card` structure to exist.
  - T007 (modifies `index.html`) and T008 (modifies `style.css`) are parallel (different files)
- **User Story 3 (P3)**: Can start after US1 completes — requires `#certificacoes` anchor to exist.
  - T009 modifies `index.html` (same file as US1/US2, so sequential)

### Within Each Story

- US1: T004/T005/T006 can run in parallel (different files, no inter-file dependencies)
- US2: T007/T008 can run in parallel (different files)
- US3: Single task (T009) — sequential by nature
- Polish: T010/T011/T012 can run in parallel (independent validations)

---

## Parallel Example: User Story 1

```bash
# Launch all three US1 implementation tasks together:
Task: "Add #certificacoes section HTML to index.html"
Task: "Add .cert, .cert__grid, .cert-card styles to style.css"
Task: "Add AWS Cloud Practitioner badge image to assets/badges/"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup (create `assets/badges/`, README)
2. Complete Phase 2: Foundational (verify CSS tokens in `style.css`)
3. Complete Phase 3: User Story 1 — section visible with badge
4. **STOP and VALIDATE**: Open `index.html` in browser, confirm section renders
5. If badge image is not yet available, use a placeholder or delay T006

### Incremental Delivery

1. Setup + Foundational → ready
2. Add User Story 1 → Section renders with badge(s) → Validate in browser → Demo (MVP!)
3. Add User Story 2 → Verification links active → Validate click-to-new-tab behavior → Demo
4. Add User Story 3 → Navbar fully functional → Validate anchor scroll → Demo
5. Polish → Responsive, accessibility, performance validated → Final check

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: T004 (index.html HTML)
   - Developer B: T005 (style.css CSS)
   - Developer C: T006 (badge asset + optimization)
3. After US1 merge:
   - Developer A: T007 + T009 (index.html — sequential)
   - Developer B: T008 (style.css — verification styles)
4. After all stories: Run Polish validations in parallel

---

## Notes

- [P] tasks = different files, no dependencies on incomplete tasks
- [Story] label maps task to specific user story for traceability
- Each user story is independently completable and testable via browser
- This feature requires no automated tests — manual validation per `quickstart.md` is sufficient
- T006 requires the AWS Cloud Practitioner badge image from Genivaldo; if unavailable, mark blocked and proceed with other tasks using a placeholder `src`
- Commit after each phase or logical group (e.g., after US1, after US2)
- Avoid cross-story file conflicts: `index.html` and `style.css` are shared — coordinate if parallel editing

**Total tasks**: 14
**Tasks per user story**: US1: 3, US2: 2, US3: 1
**Parallel opportunities**: T004/T005/T006 (US1), T007/T008 (US2), T010/T011/T012 (Polish)
**MVP scope**: User Story 1 only (T001–T006)
**Format validation**: ✅ ALL tasks follow checklist format with checkbox, Task ID, [P] where applicable, [Story] label in user story phases, and exact file paths.
