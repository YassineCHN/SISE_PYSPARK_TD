# PySpark Tutorial — SISE

Ce dépôt contient mes travaux pratiques réalisés dans le cadre du cours PySpark (Master SISE, Université Lyon 2).  
Les notebooks couvrent progressivement les notions fondamentales de Spark, des RDDs jusqu'au Machine Learning.

## Structure du projet

```
├── 1-beginner/              # Python de base (warmup)
├── 2-novice/                # RDDs, opérations Spark, PageRank
├── 3-advanced/              # SparkSQL, DataFrames, MLlib / ML
├── cheatsheets/             # Aide-mémoires (Conda, Jupyter, PySpark RDD/SQL, Python)
├── docs/                    # Supports de cours
├── requirements.txt         # Dépendances Python
└── run_jupyter.bat          # Lancement rapide via Docker
```

## Contenu des notebooks

| Dossier | Notebook | Thèmes abordés |
|---|---|---|
| `1-beginner` | `1-Initiation` | Prise en main Jupyter, Python de base |
| `2-novice` | `1-Initiation-RDD` | Création de RDDs, transformations (`map`, `filter`, `flatMap`, `reduce`), paired RDDs, `reduceByKey`, `join` |
| `2-novice` | `2-Pagerank-RDD` | Algorithme PageRank itératif avec RDDs |
| `3-advanced` | `1-Initiation-SparkSQL` | DataFrames, SparkSQL, statistiques descriptives |
| `3-advanced` | `2-Advanced-SQL-and-ML` | Préparation de données, `StringIndexer`, `OneHotEncoder`, `VectorAssembler`, Logistic Regression (MLlib & ML) |

## Lancement

### Option 1 — Docker (recommandé, aucune installation requise)

Double-cliquer sur `run_jupyter.bat` ou exécuter depuis un terminal Windows :

```bat
run_jupyter.bat
```

Cela lance la commande suivante :

```
docker run -it --rm -p 8888:8888 -p 4040:4040 \
  -v "%cd%:/home/jovyan/work" \
  jupyter/pyspark-notebook \
  start-notebook.sh --NotebookApp.token='' --NotebookApp.password=''
```

Détail des paramètres :

| Paramètre | Rôle |
|---|---|
| `-it` | Mode interactif — affiche les logs du conteneur dans le terminal |
| `--rm` | Supprime automatiquement le conteneur à l'arrêt (pas de résidu) |
| `-p 8888:8888` | Expose JupyterLab sur [http://localhost:8888](http://localhost:8888) |
| `-p 4040:4040` | Expose l'interface Spark UI sur [http://localhost:4040](http://localhost:4040) |
| `-v "%cd%:/home/jovyan/work"` | Monte le répertoire courant dans le conteneur — les notebooks sont donc modifiés directement sur le disque local |
| `jupyter/pyspark-notebook` | Image Docker officielle Jupyter avec PySpark préinstallé |
| `--NotebookApp.token=''` | Désactive le token d'authentification pour un accès local simplifié |
| `--NotebookApp.password=''` | Désactive le mot de passe pour un accès local simplifié |

> **Note de sécurité :** la désactivation du token et du mot de passe est adaptée à un usage local uniquement. Ne pas exposer ce conteneur sur un réseau public.

Ouvrir ensuite [http://localhost:8888](http://localhost:8888) dans le navigateur.  

### Option 2 — Installation locale (Anaconda)

**Prérequis :** Java JDK 17 ou 21

```sh
conda create -n pyspark-tutorial python=3.12
conda activate pyspark-tutorial
pip install -r requirements.txt
```

```sh
set PYSPARK_PYTHON=python
jupyter lab
```

> **Note Windows :** des avertissements `HADOOP_HOME` peuvent apparaître, ils sont sans conséquence pour une utilisation locale.

## Prérequis techniques

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (option recommandée)
- **ou** [Anaconda](https://www.anaconda.com/download/) + Java JDK 17/21

## Origine

Les notebooks (sans réponses) sont issus du cours de PySpark dispensé à l'Université Lyon 2 (Master SISE).  
Les solutions et ajouts (dont `run_jupyter.bat`) sont de ma réalisation.
