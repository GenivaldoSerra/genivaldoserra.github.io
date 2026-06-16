# PRD - Portfólio Web: Engenharia de Dados & DevOps

## 1. Visão Geral

### 1.1 Descrição do Projeto
Desenvolvimento de um portfólio web estático e responsivo que apresente projetos e competências nas áreas de **Engenharia de Dados** e **DevOps**. O site servirá como vitrine profissional para demonstrar expertise, destacar projetos realizados e facilitar conexões com potenciais empregadores ou colaboradores.

### 1.2 Objetivo Principal
Criar uma presença online profissional que:
- Apresente de forma clara as duas áreas de atuação
- Showcasear projetos práticos com descrições e links para repositórios
- Utilize design moderno com paleta de cores verde vibrante
- Funcione como site estático (HTML + CSS) sem dependências externas
- Seja facilmente deployável localmente

### 1.3 Escopo do Projeto
✅ Página inicial com apresentação pessoal  
✅ Seção dedicada a Engenharia de Dados  
✅ Seção dedicada a DevOps  
✅ Grid de projetos com cards informativos  
✅ Links para repositórios GitHub  
✅ Seção de contato  
✅ Design responsivo para desktop e mobile  
✅ Paleta de cores verde vibrante  

---

## 2. Requisitos Funcionais

### 2.1 Navegação
- **Navbar fixa/sticky** com links internos para:
  - Sobre
  - Engenharia de Dados
  - DevOps
  - Contato
- **Logo/Brand** no início da navbar
- Links com scroll suave para seções

### 2.2 Seção Hero
- Título de boas-vindas com emoji
- Subtítulo descritivo
- Dois CTA (Call-to-Action) buttons:
  - "Ver Projetos"
  - "Contato"
- Background com gradiente verde

### 2.3 Seção Sobre
- Breve apresentação pessoal
- Descrição de expertise nas duas áreas
- Máximo 150-200 palavras

### 2.4 Seção Engenharia de Dados
- **Header** com título e descrição da área
- **Grid de Projetos** com no mínimo 3 cards, cada um contendo:
  - Título do projeto
  - Badges com tecnologias principais
  - Descrição (50-100 palavras)
  - Tags de tecnologias usadas
  - Link "Ver no GitHub" direcionando para repositório
- Espaço para expansão futura (adicionar mais projetos)

### 2.5 Seção DevOps
- Mesma estrutura da seção de Engenharia de Dados
- **Header** com título e descrição da área
- **Grid de Projetos** com no mínimo 3 cards
- Cards com mesma estrutura de informações

### 2.6 Seção de Contato
- Título e chamada para conversa
- Botões com links para:
  - Email
  - GitHub
  - LinkedIn (ou redes sociais)
- Abre em aba nova quando clicado

### 2.7 Footer
- Copyright
- Ano atual
- Nome do proprietário

---

## 3. Requisitos Não-Funcionais

### 3.1 Design & UX
- **Paleta de Cores:**
  - Verde Primário: `#00D84F` (Verde vibrante)
  - Verde Secundário: `#00A836` (Verde mais escuro)
  - Verde Light: `#E8F9F0` (Fundo claro)
  - Neutro: Branco/Cinza para texto
  - Aceitos: Preto para texto principal

- **Typography:**
  - Fonte moderna e limpa (ex: Inter, Poppins, Roboto)
  - Títulos: Bold 32-48px
  - Subtítulos: 18-24px
  - Corpo de texto: 14-16px
  
- **Espaçamento:**
  - Padding/Margin consistentes
  - Container max-width: 1200px
  - Gaps entre cards: 20-30px

### 3.2 Responsividade
- **Desktop:** Layout de 3 colunas para grid de projetos
- **Tablet:** Layout de 2 colunas
- **Mobile:** Layout de 1 coluna (full-width com padding)
- Navbar colapsível em mobile (opcional, pode ser simples stacked)

### 3.3 Performance
- Arquivo HTML único ou estruturado em sections
- CSS externo (style.css) único para evitar múltiplas requisições
- Sem JavaScript pesado (CSS puro para interações básicas)
- Tamanho total < 1MB
- Carregamento rápido para acesso local

### 3.4 Compatibilidade
- Navegadores modernos (Chrome, Firefox, Safari, Edge)
- Suporte a CSS Grid e Flexbox
- Sem polyfills necessários

---

## 4. Especificações Técnicas

### 4.1 Arquitetura
```
portfolio/
├── index.html          # Arquivo HTML principal
├── style.css           # Estilos globais
└── README.md          # Documentação do projeto
```

### 4.2 Tecnologias
- **HTML5:** Semântico e estruturado
- **CSS3:** Grid, Flexbox, Gradientes, Animações
- **Sem dependências externas:** Sem bibliotecas JS ou CSS frameworks

### 4.3 Estrutura HTML
- Semântica HTML5: `<header>`, `<nav>`, `<section>`, `<footer>`
- Classes bem nomeadas para CSS
- Atributos semanticamente corretos

### 4.4 Estilos CSS
- Variáveis CSS para cores (facilita manutenção)
- Mobile-first approach
- Media queries para responsividade
- Transições suaves em hover
- Sem pré-processadores (CSS puro)

---

## 5. Cards de Projetos

### 5.1 Estrutura do Card
Cada card de projeto deve conter:

```
┌─────────────────────────────┐
│ Título do Projeto           │
│ [Badge: Tecnologia]         │
├─────────────────────────────┤
│ Descrição breve do projeto  │
│ em 2-3 linhas...            │
├─────────────────────────────┤
│ [Tag] [Tag] [Tag] [Tag]     │
│ Tecnologias usadas          │
├─────────────────────────────┤
│ Ver no GitHub →             │
└─────────────────────────────┘
```

### 5.2 Informações do Card
- **Título:** Claro e descritivo (3-5 palavras)
- **Badge:** 1-2 tags principais
- **Descrição:** 50-100 palavras explicando:
  - O que foi feito
  - Problema resolvido
  - Tecnologias principais
- **Tags de Tech:** 4-5 tecnologias principais
- **Link:** CTA para GitHub com ícone/arrow

---

## 6. Seções Detalhadas

### 6.1 Hero Section
```
Olá! 👋
Bem-vindo ao meu portfólio

Especializado em [Engenharia de Dados] e [DevOps], 
transformando dados em insights e infraestrutura em eficiência.

[Ver Projetos] [Contato]
```

### 6.2 Engenharia de Dados - Tecnologias Esperadas
- Python, Apache Airflow, dbt
- SQL, Snowflake, PostgreSQL
- Apache Spark, Hadoop
- AWS S3, Google Cloud Storage
- Pandas, NumPy

### 6.3 DevOps - Tecnologias Esperadas
- Docker, Kubernetes, Helm
- GitHub Actions, GitLab CI, Jenkins
- Terraform, CloudFormation, Ansible
- Prometheus, Grafana, ELK Stack
- AWS, Google Cloud, Azure

---

## 7. Fluxo de Navegação

```
┌─────────────────────────────────────────┐
│           NAVBAR (Sticky)               │
│  Logo | Sobre | Eng.Dados | DevOps | Contato
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│          HERO SECTION                   │
│     Apresentação + CTAs                 │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│         SEÇÃO SOBRE                     │
│     Breve descrição pessoal             │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│    ENGENHARIA DE DADOS                  │
│   Grid com 3+ Cards de Projetos         │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│         DEVOPS                          │
│   Grid com 3+ Cards de Projetos         │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│      SEÇÃO CONTATO                      │
│  Email | GitHub | LinkedIn              │
└─────────────────────────────────────────┘
                    ↓
┌─────────────────────────────────────────┐
│         FOOTER                          │
│      Copyright & Nome                   │
└─────────────────────────────────────────┘
```

---

## 8. Paleta de Cores

### 8.1 Cores Primárias
| Cor | Hex | Uso |
|-----|-----|-----|
| Verde Vibrante | `#00D84F` | Accents, CTA buttons, highlights |
| Verde Escuro | `#00A836` | Hover states, borders |
| Verde Light | `#E8F9F0` | Backgrounds, seções alternadas |
| Branco | `#FFFFFF` | Fundo principal, cards |
| Cinza Escuro | `#1A1A1A` | Texto principal |
| Cinza Médio | `#666666` | Texto secundário |

### 8.2 Aplicação
- **Hero:** Gradiente verde (claro → escuro)
- **Cards:** Branco com border left verde
- **Botões:** Fundo verde com texto branco
- **Hover:** Transição de cor verde + leve elevação
- **Seções alternadas:** Verde light (alternando com branco)

---

## 9. Metadados & SEO

### 9.1 Meta Tags
- `<title>`: "Portfólio - Engenharia de Dados & DevOps"
- `<meta name="description">`: Breve descrição do site
- `<meta name="viewport">`: Responsividade mobile
- `<meta charset="UTF-8">`: Encoding UTF-8

### 9.2 Semântica
- Uso correto de headings (h1, h2, h3)
- Links com text descritivo (não apenas "clique aqui")
- Alt text em imagens (se houver)

---

## 10. Critérios de Aceitação

✅ Site carrega sem erros (HTML válido)  
✅ Navegação funciona em todos os browsers modernos  
✅ Design responsivo em mobile, tablet e desktop  
✅ Cores verde vibrantes aplicadas conforme especificado  
✅ Grid de projetos exibe corretamente em todos os breakpoints  
✅ Links para GitHub funcionam e abrem em aba nova  
✅ Seção de contato com links funcionais  
✅ Footer com copyright presente  
✅ Arquivo CSS único e otimizado  
✅ Sem dependências externas (HTML + CSS puro)  
✅ Tamanho total do projeto < 1MB  

---

## 11. Roadmap & Futuro

### 11.1 Fase 1 (Atual)
- ✅ Versão estática HTML + CSS
- ✅ 3 projetos por área
- ✅ Design verde vibrante
- ✅ Responsive design

### 11.2 Fase 2 (Opcional Futura)
- Adicionar mais projetos
- Implementar formulário de contato (JavaScript)
- Dark mode toggle
- Animações CSS avançadas
- Blog/artigos sobre projetos

### 11.3 Fase 3 (Opcional Futura)
- Migração para React/Next.js
- Integração com API de GitHub
- CMS para gerenciar projetos
- Analytics
- PWA (Progressive Web App)

---

## 12. Notas Adicionais

- O site é **estático e local-first**, ideal para rodar em localhost
- Fácil de customizar: basta editar os textos, links e cores no HTML/CSS
- Preparado para ser hosteado em GitHub Pages, Netlify ou Vercel no futuro
- Sem custos de hosting ou dependências pagas
- Ambiente de desenvolvimento: qualquer editor de texto + navegador

---

**Versão do PRD:** 1.0  
**Data:** 2024  
**Status:** Aprovado para desenvolvimento
