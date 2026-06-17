# Implementation Plan: Certification Badges

**Branch**: `002-certification-badges` | **Date**: 2026-06-17 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `specs/002-certification-badges/spec.md`

## Summary

Adição de uma seção dedicada à exibição de certificações profissionais no portfólio estático de
Genivaldo Serra (HTML/CSS puro). A seção apresentará badges visuais de certificações (ex.: AWS Cloud
Practitioner) em um grid responsivo, com nome, emissor, e links opcionais de verificação. A seção
será inserida entre DevOps e Contato, com âncora no menu de navegação.

## Technical Context

**Language/Version**: HTML5, CSS3

**Primary Dependencies**: Nenhuma (Vanilla HTML/CSS) — reutiliza tokens CSS existentes em `:root`

**Storage**: Assets estáticos locais em `assets/badges/` (WebP/PNG/SVG, ≤ 30KB cada)

**Testing**: Validação manual via quickstart.md, inspecção de HTML (alt text), DevTools responsive

**Target Platform**: Web Browsers (Chrome, Firefox, Safari, Edge — Mobile e Desktop)

**Project Type**: Static Website — adição de seção ao `index.html` e `style.css` existentes

**Performance Goals**: Assets de badges ≤ 500KB total; portfólio total ≤ 1MB; `loading="lazy"` em todas as imagens

**Constraints**: Sem JavaScript (exceto o `new Date().getFullYear()` já existente); sem dependências externas

**Scale/Scope**: 1 seção nova, 1+ cards de badge, 1 item de menu, diretório `assets/badges/`

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- [x] Arquitetura estática: Apenas HTML/CSS (sem dependências externas)
- [x] Responsividade: Uso de Flexbox/Grid e abordagem mobile-first (`auto-fill minmax`)
- [x] Design: Uso da paleta Verde Vibrante (#00D84F) aprovada e layout moderno
- [x] Performance: Arquivos otimizados (< 1MB) e requisições minimizadas (`loading="lazy"`)
- [x] Certificações: Badges com alt text descritivo, grid responsivo e assets em `assets/badges/`

*Todos os gates aprovados. Sem violações a justificar.*

## Project Structure

### Documentation (this feature)

```text
specs/002-certification-badges/
├── plan.md              # Este arquivo
├── spec.md              # Especificação de feature
├── research.md          # Decisões técnicas de design
├── data-model.md        # Modelo de dados e convenções
├── quickstart.md        # Guia de validação manual
├── checklists/
│   └── requirements.md  # Checklist de qualidade da spec
└── tasks.md             # (gerado por /speckit-tasks — não criado aqui)
```

### Source Code (repository root)

```text
/
├── index.html              # [MODIFY] Adicionar: nav link, section#certificacoes, article cards
├── style.css               # [MODIFY] Adicionar: .cert-*, responsividade da seção
└── assets/
    └── badges/             # [NEW] Diretório para imagens de badges
        ├── aws-cloud-practitioner.webp   # [NEW] Badge AWS CCP
        └── [outras-certs].webp           # [NEW] Badges adicionais (a confirmar)
```

**Structure Decision**: Extensão mínima da estrutura existente. Nenhum novo arquivo HTML/CSS
principal é criado — apenas blocos adicionados ao `index.html` e `style.css` existentes,
mais o novo diretório `assets/badges/`.

## Design Detalhado

### HTML — Novo item de menu (navbar)

```html
<!-- Inserir entre o link DevOps e o link Contato -->
<a href="#certificacoes" class="navbar__link">Certificações</a>
```

### HTML — Nova seção `#certificacoes`

Posição: após `</section>` da seção DevOps, antes da seção Contato.

```html
<!-- ========== CERTIFICAÇÕES ========== -->
<section class="cert" id="certificacoes" aria-labelledby="cert-title">
    <div class="container">
        <div class="section-header">
            <div class="section-header__badge">Certificações</div>
            <h2 class="section-header__title" id="cert-title">Credenciais & Badges</h2>
            <p class="section-header__desc">
                Certificações profissionais que validam minha expertise em Cloud e DevOps.
            </p>
        </div>
        <div class="cert__grid">
            <!-- Padrão de card de badge -->
            <article class="cert-card" id="cert-aws-cloud-practitioner">
                <div class="cert-card__badge-wrap">
                    <img
                        src="assets/badges/aws-cloud-practitioner.webp"
                        alt="Badge de certificação: AWS Certified Cloud Practitioner — Amazon Web Services"
                        class="cert-card__badge-img"
                        width="100"
                        height="100"
                        loading="lazy"
                    >
                </div>
                <div class="cert-card__info">
                    <h3 class="cert-card__name">AWS Certified Cloud Practitioner</h3>
                    <p class="cert-card__issuer">Amazon Web Services</p>
                </div>
                <!-- Incluir apenas quando verificar_url existir -->
                <a
                    href="https://www.credly.com/badges/..."
                    target="_blank"
                    rel="noopener noreferrer"
                    class="cert-card__verify"
                    aria-label="Verificar certificação AWS Certified Cloud Practitioner no Credly"
                >
                    Verificar →
                </a>
            </article>
            <!-- Repetir article.cert-card para cada certificação -->
        </div>
    </div>
</section>
```

### CSS — Estilos da seção `.cert-*`

```css
/* Seção Certificações */
.cert {
    background: var(--color-bg-white);
}

/* Grid responsivo de badges */
.cert__grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 24px;
}

/* Card individual de certificação */
.cert-card {
    background: var(--color-card-bg);
    border: 1px solid var(--color-border);
    border-radius: var(--radius-md);
    padding: 24px 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    text-align: center;
    box-shadow: var(--shadow-card);
    transition: transform var(--transition-speed) ease,
                box-shadow var(--transition-speed) ease;
}

.cert-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-card-hover);
}

/* Container da imagem do badge */
.cert-card__badge-wrap {
    width: 100px;
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Imagem do badge */
.cert-card__badge-img {
    width: 100px;
    height: 100px;
    object-fit: contain;
    border-radius: var(--radius-sm);
}

/* Área de texto */
.cert-card__info {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 4px;
}

/* Nome da certificação */
.cert-card__name {
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--color-text-main);
    line-height: 1.3;
}

/* Emissor */
.cert-card__issuer {
    font-size: 0.78rem;
    color: var(--color-text-muted);
    font-weight: 500;
}

/* Link de verificação */
.cert-card__verify {
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--color-primary);
    transition: color var(--transition-speed), gap var(--transition-speed);
}

.cert-card__verify:hover {
    color: var(--color-primary-dark);
}

/* Responsividade */
@media (max-width: 600px) {
    .cert__grid {
        grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    }
}
```

## Verificação Pós-Implementação

Executar os 6 cenários documentados em [quickstart.md](./quickstart.md):

1. ✅ Abertura básica — seção visível, badge renderizado, sem erros de console
2. ✅ Navegação por âncora — link "Certificações" no menu funciona
3. ✅ Responsividade — grid adapta-se de 320px a 1920px
4. ✅ Alt text — 100% das imagens com alt descritivo (verificar via JS snippet)
5. ✅ Links de verificação — abrem em nova aba com `rel="noopener noreferrer"`
6. ✅ Performance — `assets/badges/` ≤ 500KB total
