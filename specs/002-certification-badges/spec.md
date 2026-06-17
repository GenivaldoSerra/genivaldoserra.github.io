# Feature Specification: Vitrine de Certificações e Badges

**Feature Branch**: `002-certification-badges`

**Created**: 2026-06-17

**Status**: Draft

**Input**: User description: "gostaria de adicionar um espaço para as minhas certificações, mostrar as badges tipo da cloud practitioner e outras"

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Visualizar Certificações ao Navegar no Portfólio (Priority: P1)

Um recrutador ou cliente potencial visita o portfólio de Genivaldo e deseja verificar suas
qualificações certificadas. Ele rola a página e encontra uma seção dedicada com os badges visuais
de cada certificação, podendo identificar rapidamente as credenciais e a área de expertise.

**Why this priority**: Certificações são prova objetiva de competência. Esta seção é o principal
vetor de credibilidade para recrutadores técnicos e deve estar visível sem precisar sair da página.

**Independent Test**: Pode ser totalmente testada abrindo `index.html` no navegador e verificando
se a seção de certificações aparece com badges visíveis, nomes e emissores listados — sem necessidade
de qualquer outra seção da página funcionar.

**Acceptance Scenarios**:

1. **Given** o portfólio está aberto em um desktop, **When** o visitante rola até a seção de certificações, **Then** ele vê um grid com todos os badges de certificação exibidos com imagem, nome e emissor.
2. **Given** o portfólio está aberto em um smartphone, **When** o visitante rola até a seção de certificações, **Then** o grid de badges adapta-se ao tamanho da tela sem cortes ou sobreposições.
3. **Given** a imagem de um badge falha ao carregar, **When** o visitante visualiza a seção, **Then** um texto alternativo descritivo é exibido no lugar da imagem.

---

### User Story 2 - Verificar a Autenticidade de uma Certificação (Priority: P2)

Um recrutador quer verificar se a certificação AWS Cloud Practitioner exibida é legítima. Ele clica
no badge ou em um link associado e é redirecionado para a página oficial de verificação (Credly,
AWS, etc.) em uma nova aba.

**Why this priority**: Links de verificação aumentam a credibilidade e a confiança do portfólio.
São opcionais por certificação mas importantes como mecanismo de validação.

**Independent Test**: Pode ser testada clicando no link de verificação de qualquer badge e
confirmando que a página de verificação oficial abre em nova aba.

**Acceptance Scenarios**:

1. **Given** um badge possui link de verificação, **When** o visitante clica no link, **Then** a página de verificação da certificação abre em uma nova aba do navegador.
2. **Given** um badge não possui link de verificação, **When** o visitante visualiza o card, **Then** o badge é exibido normalmente sem botão/link de verificação — sem mensagens de erro.

---

### User Story 3 - Navegar pela Seção via Menu de Navegação (Priority: P3)

Um visitante que já sabe que quer ver as certificações clica no item "Certificações" no menu de
navegação principal e é levado diretamente à seção correspondente na página.

**Why this priority**: Acessibilidade e navegação rápida melhoram a experiência, especialmente para
visitantes que já estão procurando especificamente pelas credenciais.

**Independent Test**: Pode ser testada clicando no link de navegação e verificando se a página
rola suavemente até a seção de certificações.

**Acceptance Scenarios**:

1. **Given** o menu de navegação está visível, **When** o visitante clica em "Certificações", **Then** a página rola suavemente até a seção de certificações.
2. **Given** o visitante está em um dispositivo móvel com menu hambúrguer, **When** ele abre o menu e clica em "Certificações", **Then** o menu fecha e a página rola até a seção.

---

### Edge Cases

- O que acontece se não houver nenhuma certificação cadastrada? A seção não deve aparecer vazia
  — ou deve ter um estado de "em breve" ou simplesmente ser omitida.
- Como exibir badges com dimensões originais muito diferentes (ex.: badge quadrado vs. retangular)?
  O layout deve manter consistência visual independentemente do formato original da imagem.
- O que acontece se o link de verificação estiver quebrado ou expirado? O link deve ser opcional e
  a ausência de link não impacta a exibição do badge.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: O portfólio DEVE exibir uma seção nomeada "Certificações" contendo todos os badges de
  certificação profissional de Genivaldo Serra.
- **FR-002**: Cada certificação DEVE exibir: imagem do badge, nome da certificação e nome do emissor
  (ex.: Amazon Web Services, Google Cloud, CNCF).
- **FR-003**: Cada badge DEVE possuir um texto alternativo (alt text) descritivo para acessibilidade
  e SEO.
- **FR-004**: O grid de badges DEVE ser responsivo, adaptando-se corretamente a mobile, tablet e
  desktop sem corte ou sobreposição de conteúdo.
- **FR-005**: Certificações que possuam URL de verificação DEVEM ter um link que abre a página
  oficial em uma nova aba.
- **FR-006**: A seção DEVE ser acessível via âncora no menu de navegação principal.
- **FR-007**: As imagens dos badges DEVEM ser armazenadas localmente (não depender de URLs externas)
  para garantir disponibilidade e performance.
- **FR-008**: O tamanho total dos assets de badges não DEVE ultrapassar 500KB para manter o portfólio
  abaixo do limite de 1MB total.

### Key Entities

- **Certificação**: Representa uma credencial profissional de Genivaldo. Atributos: nome, emissor,
  imagem do badge (local), URL de verificação (opcional), ano de obtenção (opcional).
- **Grid de Badges**: Contêiner visual que organiza as certificações em layout de grade responsiva.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Todos os badges de certificação são visíveis e legíveis em telas de 320px a 1920px
  de largura sem sobreposições ou cortes.
- **SC-002**: A seção de certificações é acessível a partir do menu de navegação em no máximo 1
  clique ou toque.
- **SC-003**: 100% dos badges possuem alt text descritivo (verificável via inspeção de HTML).
- **SC-004**: O carregamento da seção de certificações não adiciona mais de 500KB ao peso total
  da página.
- **SC-005**: Links de verificação, quando presentes, abrem corretamente em nova aba em Chrome,
  Firefox, Safari e Edge.

## Assumptions

- Genivaldo fornecerá as imagens dos badges em formato PNG, SVG ou WebP com qualidade suficiente
  para exibição em tela.
- As certificações iniciais incluem ao menos: AWS Cloud Practitioner e outras a serem confirmadas
  pelo próprio Genivaldo.
- Não há requisito de filtragem ou ordenação dinâmica das certificações nesta versão (exibição
  estática é suficiente).
- A seção de certificações será inserida após a seção de projetos e antes do rodapé (footer) na
  ordem de leitura da página.
- O portfólio continua sendo 100% estático (HTML + CSS puro), sem necessidade de backend ou
  gerenciamento dinâmico de conteúdo.
- Links de verificação externos (Credly, AWS Certification, etc.) são responsabilidade do emissor
  e podem mudar ao longo do tempo — o portfólio não valida a disponibilidade desses links.
