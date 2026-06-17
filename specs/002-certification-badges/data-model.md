# Data Model: Vitrine de Certificações e Badges

**Feature**: `002-certification-badges`
**Date**: 2026-06-17

---

## Entidade: Certificação

Representa uma credencial profissional exibida na seção de certificações do portfólio.

| Campo           | Tipo    | Obrigatório | Descrição                                              | Exemplo                                              |
|-----------------|---------|-------------|--------------------------------------------------------|------------------------------------------------------|
| `id`            | string  | ✅ Sim      | Identificador único para o elemento HTML (`id="cert-..."`) | `"cert-aws-cloud-practitioner"`                  |
| `nome`          | string  | ✅ Sim      | Nome completo da certificação                          | `"AWS Certified Cloud Practitioner"`                 |
| `emissor`       | string  | ✅ Sim      | Organização emissora da certificação                   | `"Amazon Web Services"`                              |
| `badge_src`     | string  | ✅ Sim      | Caminho relativo para o arquivo de imagem do badge     | `"assets/badges/aws-cloud-practitioner.webp"`        |
| `badge_alt`     | string  | ✅ Sim      | Texto alternativo descritivo para acessibilidade/SEO   | `"Badge de certificação: AWS Certified Cloud Practitioner — Amazon Web Services"` |
| `verificar_url` | string  | ❌ Opcional | URL de verificação oficial (Credly, AWS, Google, etc.) | `"https://www.credly.com/badges/..."`               |
| `ano`           | number  | ❌ Opcional | Ano de obtenção da certificação                        | `2024`                                               |

### Regras de Validação

- `id` DEVE ser único na página e usar o padrão `cert-[emissor-abreviado]-[nome-kebab-case]`.
- `badge_src` DEVE referenciar um arquivo local em `assets/badges/` (não URL externa).
- `badge_alt` DEVE seguir o formato: `"Badge de certificação: [nome] — [emissor]"`.
- `verificar_url`, quando presente, DEVE apontar para HTTPS e abrir em `target="_blank"`.
- Imagens de badge DEVEM ter dimensão máxima de 200×200px e tamanho de arquivo ≤ 30KB.

---

## Entidade: Grid de Badges (Layout)

Container visual que organiza as certificações. Não é uma entidade de dados persistida — é
definida exclusivamente por CSS.

| Propriedade         | Valor                              | Descrição                                     |
|---------------------|------------------------------------|-----------------------------------------------|
| Layout              | CSS Grid `auto-fill minmax(160px)` | Responsivo, sem breakpoints fixos de colunas  |
| Gap entre cards     | `24px`                             | Consistente com o restante do portfólio       |
| Alinhamento interno | `stretch`                          | Cards de mesma altura em cada linha           |
| Breakpoint tablet   | ≤ 900px → mínimo 2 colunas        | Via `minmax` automático                       |
| Breakpoint mobile   | ≤ 600px → mínimo 1 coluna         | Via `minmax(140px, 1fr)`                      |

---

## Estrutura de Arquivos de Assets

```text
assets/
└── badges/
    ├── aws-cloud-practitioner.webp      # AWS Certified Cloud Practitioner
    ├── [outras-certificacoes].webp      # A confirmar com Genivaldo
    └── README.md                        # Guia de nomenclatura e especificações de imagem
```

### Convenção de Nomenclatura

`[emissor-abreviado]-[nome-da-cert-kebab-case].[ext]`

Exemplos:
- `aws-cloud-practitioner.webp`
- `gcp-associate-cloud-engineer.webp`
- `cncf-ckad.webp`
- `hashicorp-terraform-associate.webp`

---

## Exemplo de Instâncias

```json
[
  {
    "id": "cert-aws-cloud-practitioner",
    "nome": "AWS Certified Cloud Practitioner",
    "emissor": "Amazon Web Services",
    "badge_src": "assets/badges/aws-cloud-practitioner.webp",
    "badge_alt": "Badge de certificação: AWS Certified Cloud Practitioner — Amazon Web Services",
    "verificar_url": "https://www.credly.com/badges/...",
    "ano": 2024
  }
]
```

> **Nota**: Este JSON é apenas representação conceitual. A implementação será HTML estático
> — não há banco de dados ou geração dinâmica de conteúdo.
