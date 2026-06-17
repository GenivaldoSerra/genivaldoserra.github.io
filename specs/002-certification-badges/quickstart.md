# Quickstart: Vitrine de Certificações e Badges

**Feature**: `002-certification-badges`
**Date**: 2026-06-17

Este guia descreve como validar que a seção de certificações funciona corretamente após
a implementação, sem qualquer dependência de build ou servidor.

---

## Pré-requisitos

- Navegador moderno: Chrome 90+, Firefox 88+, Safari 14+ ou Edge 90+
- Arquivo `index.html` atualizado com a seção `#certificacoes`
- Arquivo `style.css` atualizado com os estilos `.cert-*`
- Ao menos um badge em `assets/badges/` (ex.: `aws-cloud-practitioner.webp`)

---

## Validação 1 — Abertura Básica

**Cenário**: A seção existe e carrega sem erros.

```bash
# Opção A: abrir diretamente no navegador (sem servidor)
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows

# Opção B: servidor local simples
python3 -m http.server 8080
# Acessar: http://localhost:8080
```

**Resultado esperado**:
- Seção "Certificações" visível na página
- Ao menos um badge renderizado com imagem e texto
- Nenhum erro no console do navegador (F12 → Console)

---

## Validação 2 — Navegação por Âncora

**Cenário**: O link do menu leva à seção corretamente.

1. Recarregar a página e ir ao topo
2. Clicar em "Certificações" no menu de navegação
3. Observar o scroll da página

**Resultado esperado**:
- A página rola suavemente até a seção `#certificacoes`
- O scroll é animado (não instantâneo) — comportamento herdado do `scroll-behavior: smooth`

---

## Validação 3 — Responsividade

**Cenário**: O grid de badges adapta-se a diferentes tamanhos de tela.

No navegador, abrir DevTools (F12) → aba "Responsive" ou "Device Toolbar":

| Largura de Tela | Comportamento Esperado                  |
|-----------------|-----------------------------------------|
| 1200px+         | 4 colunas de badges (ou `auto-fill`)    |
| 900px           | 3 colunas de badges                     |
| 600px           | 2 colunas de badges                     |
| 375px (iPhone)  | 2 colunas compactas sem overflow        |
| 320px (mínimo)  | Colunas adaptadas, sem corte horizontal |

**Resultado esperado**: Nenhum badge cortado, sobreposto ou fora do container em qualquer
breakpoint.

---

## Validação 4 — Acessibilidade (Alt Text)

**Cenário**: Todas as imagens possuem alt text descritivo.

No navegador, abrir DevTools (F12) → Console:

```javascript
// Verificar se alguma imagem de badge está sem alt text
const badges = document.querySelectorAll('.cert-card__badge-img');
const semAlt = [...badges].filter(img => !img.alt || img.alt.trim() === '');
console.log('Badges sem alt text:', semAlt.length);
// Resultado esperado: 0
```

Alternativamente, inspecionar o HTML de cada `<img>` na seção e confirmar o padrão:
`alt="Badge de certificação: [Nome] — [Emissor]"`

---

## Validação 5 — Links de Verificação

**Cenário**: Links de verificação abrem em nova aba.

Para cada badge que possua link de verificação:
1. Clicar no botão "Verificar →"
2. Confirmar que abre em **nova aba** (não na mesma aba)
3. Confirmar que a URL de verificação carrega corretamente

**Resultado esperado**: Nova aba aberta com a página de verificação da certificação.

---

## Validação 6 — Performance (Peso dos Assets)

**Cenário**: Os assets de badges não ultrapassam 500KB total.

```bash
# Verificar tamanho total da pasta de badges
du -sh assets/badges/
# Resultado esperado: ≤ 500K

# Verificar tamanho de cada badge individualmente
ls -lh assets/badges/
# Cada arquivo deve ser ≤ 30KB
```

Alternativamente, no navegador: DevTools → Network → recarregar → filtrar por "badges" →
somar a coluna "Size".

---

## Referências

- [data-model.md](./data-model.md) — Estrutura de dados e convenções de nomenclatura de badges
- [spec.md](./spec.md) — User stories e critérios de aceitação completos
- [research.md](./research.md) — Decisões técnicas de layout, armazenamento e acessibilidade
