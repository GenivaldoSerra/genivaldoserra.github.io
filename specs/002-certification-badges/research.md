# Research: Vitrine de Certificações e Badges

**Feature**: `002-certification-badges`
**Date**: 2026-06-17
**Status**: Complete — sem NEEDS CLARIFICATION

---

## 1. Estrutura do Portfólio Existente

### Decision
A seção de certificações será inserida entre a seção DevOps (`#devops`) e a seção Contato
(`#contato`), seguindo a ordem narrativa natural: apresentação → projetos → credenciais → contato.

### Rationale
- É o local de menor interferência na hierarquia de informação atual.
- Recrutadores que chegam aos projetos ficam curiosos sobre certificações — o posicionamento
  aproveita este fluxo natural de leitura.
- Mantém Contato como último CTA, preservando a intenção de conversão do layout.

### Alternatives Considered
- Antes da seção Sobre: descartado — quebra o fluxo apresentação → credenciais → projetos que
  é menos natural para portfólios técnicos.
- Dentro da seção Sobre como sub-bloco: descartado — misturaria conteúdo e dificultaria a
  navegação direta via âncora de menu.

---

## 2. Padrão Visual Existente

### Decision
Reutilizar 100% dos tokens CSS já definidos em `:root` (`:--color-primary`, `--radius-md`,
`--shadow-card`, `--shadow-card-hover`, `--font-family`, etc.) e o padrão `.section-header`
para manter consistência visual.

### Rationale
- Zero custo de manutenção: alterações na paleta verde propagam automaticamente para a seção.
- Consistência visual garantida sem esforço adicional de design.

### Alternatives Considered
- Criar tokens específicos para a seção de certificações: desnecessário para o escopo atual.

---

## 3. Layout do Grid de Badges

### Decision
Grid CSS responsivo com `repeat(auto-fill, minmax(160px, 1fr))` para os cards de badge,
com cada card contendo: imagem do badge (100×100px renderizados), nome da certificação
e emissor. Grid com máximo de 4 colunas em desktop, 3 em tablet, 2 em mobile.

### Rationale
- `auto-fill` + `minmax` é o padrão mobile-first mais robusto para grids de tamanho variável.
- 160px mínimo garante que badges sejam legíveis mesmo no menor breakpoint.
- Consistente com o padrão `.projects__grid` já existente no portfólio.

### Alternatives Considered
- Flexbox com wrap: descartado — CSS Grid oferece alinhamento bidimensional superior para grids
  de badges onde as alturas devem ser iguais.
- Tamanho fixo de card: descartado — `minmax` adapta-se melhor a quantidades variáveis de
  certificações futuras.

---

## 4. Armazenamento de Assets

### Decision
Imagens de badges armazenadas em `assets/badges/` na raiz do projeto, em formato WebP
(fallback PNG para compatibilidade). Dimensão de exportação recomendada: 200×200px para
badges quadrados, mantendo proporção para retangulares. Otimizados abaixo de 30KB cada.

### Rationale
- WebP oferece ~30% de compressão a mais que PNG sem perda visual perceptível.
- 200×200px é suficiente para exibição em tela retina (renderizado em 100×100px) e garante
  sharpness em todos os dispositivos.
- Armazenamento local elimina dependência de CDN externo (Credly embed, etc.) — mais rápido
  e resiliente a mudanças de URLs externas.

### Alternatives Considered
- Usar `<img>` diretamente com URL do Credly: descartado — viola FR-007 e introduz dependência
  externa que pode quebrar.
- SVG direto: adequado para badges vetoriais, mas a maioria dos provedores emite PNG/WebP.
  Aceitar SVG quando disponível como alternativa superior.

---

## 5. Links de Verificação

### Decision
Link de verificação como botão secundário discreto (`Verificar →`) abaixo do nome/emissor,
usando `target="_blank" rel="noopener noreferrer"` por segurança. Visível apenas quando
`href` está presente.

### Rationale
- `rel="noopener noreferrer"` é obrigatório para links externos em nova aba (previne
  acesso ao `window.opener`).
- Botão secundário em vez de tornar o badge inteiro clicável — evita confusão entre
  "clicar para ampliar" e "clicar para verificar".

### Alternatives Considered
- Badge inteiro como link: descartado — ambíguo semanticamente e pode confundir usuários
  que esperam zoom.
- Modal de verificação: desnecessário para o escopo estático atual.

---

## 6. Navegação / Menu

### Decision
Adicionar item `Certificações` no `<nav class="navbar__links">` com âncora `#certificacoes`,
inserido entre "DevOps" e "Contato". O item "Contato" permanece com a classe
`.navbar__link--cta` (verde destacado) como CTA final.

### Rationale
- Segue o mesmo padrão de links existentes, zero código adicional necessário além do `<a>`.
- Posição entre DevOps e Contato espelha a ordem das seções na página.

### Alternatives Considered
- Adicionar "Certificações" após "Contato": descartado — viola a ordem lógica de navegação.
- Dropdown de certificações: desnecessário para o escopo de página única.

---

## 7. Acessibilidade

### Decision
Cada `<img>` de badge terá `alt` no formato `"Badge de certificação: [Nome da Certificação] — [Emissor]"`.
A seção usará `<section aria-labelledby="cert-title">` com `<h2 id="cert-title">`.

### Rationale
- Alt text descritivo garante SC-003 e melhora SEO (Google Images indexa alt text).
- `aria-labelledby` conecta a section ao heading para leitores de tela.

---

## 8. Performance

### Decision
Usar `loading="lazy"` em todas as `<img>` de badge para defer o carregamento fora da viewport.
Budget total de assets de badges: ≤ 500KB (SC-004).

### Rationale
- `loading="lazy"` é nativo em todos os browsers modernos — sem JavaScript necessário.
- Mantém o portfólio dentro do limite de 1MB total da constituição.
