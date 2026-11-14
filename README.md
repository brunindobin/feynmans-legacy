# Feynman's Legacy

**Tema:** Identificar locais na Terra que sejam análogos aos locais de uma base lunar permanente e de Marte.

Os estudos são feitos em notebooks (`.ipynb`) e consolidados em uma aplicação web para visualização dos achados.

## Casos de estudo

| # | Caso | Objetivo | Status |
|---|------|----------|--------|
| 1 | Clusterização atual | Identificar locais potenciais com scoring de similaridade | Em andamento |
| 2 | Modelo de previsão | Prever similaridade futura a partir de condições históricas | Planejado |
| 3 | A definir | Pendente | Pendente |

## Estrutura do repositório

```
feynmans-legacy/
├── app/                      # Aplicação web (visualização dos achados)
├── data/
│   ├── external/             # Dados de terceiros
│   ├── nasa/                 # Dados da NASA (perfis de Lua/Marte e afins)
│   └── tratados/             # Dados processados (alimentam notebooks e app)
├── docs/
│   ├── decisions/            # Registro de decisões técnicas (ADRs)
│   └── methodology.md        # Metodologia dos estudos
├── models/                   # Artefatos de modelos treinados
├── notebooks/
│   └── 00_ETL/               # Extração, transformação e carga
├── src/feynmans_legacy/
│   ├── features/             # Engenharia de atributos
│   └── models/               # Clusterização e previsão
├── .github/                  # Workflows e templates
├── Makefile                  # Atalhos de comandos
└── pyproject.toml            # Dependências e configuração
```

## Como começar

```bash
git clone https://github.com/jose-aquino-jr/feynmans-legacy.git
cd feynmans-legacy
make setup
pre-commit install
```

## Criação e ativação da venv

```bash
python -m venv .venv
source .venv/Scripts/activate      # no Windows; em Linux/Mac: source .venv/bin/activate
pip install -r requirements.txt -r requirements-dev.txt
pip install -e .                   # instala o pacote src/feynmans_legacy
python -m ipykernel install --user --name feynmans-legacy
pre-commit install
```

## Fluxo de trabalho

1. **ETL:** dados brutos entram em `data/external` e `data/nasa`; os notebooks de `notebooks/00_ETL` geram os dados em `data/tratados`.
2. **Estudos:** cada caso tem seus notebooks numerados (ex.: `01_01_features.ipynb`). Lógica reutilizável vai para `src/feynmans_legacy`, não fica só no notebook.
3. **Aplicação:** o `app` consome apenas o que está em `data/tratados`.

## Convenções

- **Branches:** `case1/descricao`, `case2/descricao`, `app/descricao`, `setup/descricao`.
- **Commits:** `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`.
- **Notebooks:** sem outputs versionados (`nbstripout`) e com seeds fixas.
- **Dados:** não versionar arquivos pesados; documentar fonte, licença e data de download em `data/README.md`.
- **PRs:** sempre para `main`, com revisão de pelo menos uma pessoa.

## Equipe

| Frente | Responsável |
|--------|-------------|
| Dados / ETL | _a definir_ |
| Caso 1 | _a definir_ |
| Caso 2 | _a definir_ |
| Aplicação | _a definir_ |

## Licença

_A definir._