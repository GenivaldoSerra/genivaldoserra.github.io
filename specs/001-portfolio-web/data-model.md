# Data Model: Portfolio Web

As a static HTML project, there is no persistent backend database. However, the UI structure models the following entity conceptually:

## Entity: Project (Card)
- `Title` (string): Nome do projeto.
- `Description` (string): Breve resumo do projeto (50-100 palavras).
- `PrimaryBadge` (string): Principal tecnologia em destaque (ex: Airflow, Docker).
- `Tags` (array of strings): Lista de tecnologias adicionais usadas.
- `RepositoryUrl` (string): Link para o repositório no GitHub.

*Note: In this initial phase, this data is hardcoded directly into the HTML markup.*
