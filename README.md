# Documentação Hostask

Portal acadêmico com a arquitetura e as regras de negócio do Hostask.

## Tecnologias

- MkDocs.
- Material for MkDocs.
- GitHub Pages.

## Preparar o ambiente

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Visualizar

```bash
mkdocs serve
```

## Validar

```bash
mkdocs build --strict
```

## Publicar

```bash
mkdocs gh-deploy
```

## Conteúdo

- Início.
- Arquitetura: diagramas C4 de Contexto e Contêineres.
- Regras de negócio e fluxos.

Autora: Raquel Novelli.