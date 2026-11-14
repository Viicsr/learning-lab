# Learning Lab

Repositorio personal para estudiar los tracks de DataCamp y otros cursos,
con notebooks, apuntes y proyectos propios.

## Requisitos

- macOS con [uv](https://docs.astral.sh/uv/) instalado
- VS Code o Cursor (con el comando de shell instalado)
- Git

## Puesta en marcha

```bash
git clone <URL-del-repo> learning-lab
cd learning-lab
uv sync                      # crea .venv e instala dependencias desde uv.lock
uv run pre-commit install    # activa los hooks (ruff, nbstripout)
uv run ipython kernel install --user --env VIRTUAL_ENV "$(pwd)/.venv" --name=learning-lab
cursor .                     # o: code .
```

En el editor: abre un notebook > "Select Kernel" > "Python Environments" >
`.venv/bin/python` (o el kernel `learning-lab`).

## Crear el proyecto desde cero

```bash
uv init learning-lab && cd learning-lab
uv python pin 3.12
uv add pandas numpy matplotlib scikit-learn
uv add --dev ipykernel pytest ruff pre-commit nbstripout
git init
uv run nbstripout --install --attributes .gitattributes
```

## Estructura
learning-lab/
├── pyproject.toml
├── uv.lock
├── .python-version
├── .gitignore
├── .gitattributes
├── .pre-commit-config.yaml
├── README.md
├── tracks/
│   ├── 01-python-for-software-engineering/
│   │   ├── README.md          # objetivos, estado, aprendizajes
│   │   ├── notes/             # tus apuntes en markdown
│   │   ├── notebooks/         # 01-functions.ipynb ...
│   │   └── projects/          # proyectos propios con src/ y tests/
│   ├── 02-building-apis/
│   └── ...
├── data/                      # ignorado por git
└── shared/                    # utilidades reutilizables (paquete)

## Flujo de trabajo

1. Crea la carpeta del track en `tracks/NN-nombre/` con su README.
2. Un notebook por curso o capítulo: `01-functions.ipynb`.
3. Dependencias nuevas: `uv add <paquete>` (o `uv add --dev` para herramientas).
4. Antes de cada commit: `uv run ruff check . && uv run ruff format .`
5. Commits pequeños por curso: `feat(python-se): course 3 notebooks`.
6. Actualiza la tabla de progreso del README del track.

## Comandos útiles

| Acción | Comando |
|---|---|
| Instalar dependencias | `uv sync` |
| Añadir paquete | `uv add <pkg>` |
| Ejecutar tests | `uv run pytest` |
| Lint y formato | `uv run ruff check . && uv run ruff format .` |
| Abrir Jupyter en navegador | `uv run --with jupyter jupyter lab` |

## Copyright y qué se publica

El contenido de los cursos pertenece a sus autores y plataformas.
En este repositorio solo se publica material propio: apuntes con mis palabras
y proyectos originales. No se suben enunciados, textos, datasets ni notebooks
de plantilla de DataCamp.

Los notebooks se guardan sin salidas (nbstripout).

## Progreso

| Track | Estado | Horas | Notas |
|---|---|---|---|
| Python Programming | Hecho | | |
| Python for Software Engineering | En curso | | |
| Building APIs in Python | Pendiente | | |
| Machine Learning Fundamentals | Pendiente | | |
| Associate AI Engineer for Developers | Pendiente | | |
| AWS Cloud Practitioner | Pendiente | | |