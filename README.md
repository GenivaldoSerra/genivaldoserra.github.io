# Portfólio — Engenharia de Dados & DevOps

Site de portfólio estático responsivo construído com **HTML5 + CSS3 puro** (sem dependências externas), apresentando projetos nas áreas de Engenharia de Dados e DevOps.

## Como executar localmente

```bash
# Opção 1 – Python (recomendado)
python3 -m http.server 8000
# Abra: http://localhost:8000

# Opção 2 – Abrir diretamente no navegador
open index.html     # macOS
xdg-open index.html # Linux
```

## Estrutura

```
/
├── index.html   # Página principal
├── style.css    # Estilos globais com variáveis CSS
└── README.md    # Este arquivo
```

## Validação (quickstart.md)

1. **Responsividade** – Redimensione a janela de 320px até 1400px; o grid vai de 1 a 3 colunas sem scroll horizontal.
2. **Navegação** – Clique nos links da navbar e confirme scroll suave para as seções corretas.
3. **Links externos** – Todos os botões "Ver no GitHub" e redes sociais devem abrir em nova aba.
4. **Design** – Cor de destaque primária `#00D84F` em botões, badges e hovers.

## Paleta de Cores

| Cor | Hex | Uso |
|-----|-----|-----|
| Verde Vibrante | `#00D84F` | Destaque, botões, CTA |
| Verde Escuro | `#00A836` | Hover |
| Verde Light | `#E8F9F0` | Fundos de seção e tags |
| Cinza Escuro | `#1A1A1A` | Texto principal |
