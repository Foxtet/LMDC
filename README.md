# LMDC (Lavaduck Mini Datacenter)

🚧 Ce projet et cette documentation sont en cours de construction et peuvent
changer à tout moment.

Documentation de mon homelab, qui sert à la fois d'apprentissage et de prod
personnelle. Elle est publiée sous forme de site :
**<https://foxtet.github.io/LMDC/>**

## Structure

Les pages sont dans [`docs/`](docs/), rangées par sujet :

```txt
docs/
├── architecture/   # matériel, réseau, nommage
├── decisions/      # ADR
├── exploitation/   # runbooks, incidents, évolutions, troubleshooting
├── projet/         # roadmap, todo, backlog, finances
├── journal/        # suivi des actions (blog)
└── assets/images/
```

## Écrire avec Obsidian

Ouvrir la **racine du dépôt** comme vault, puis régler :

- *Fichiers et liens* : désactiver « Use [[Wikilinks]] », « New link format »
  sur *Relative path to file*, et « Default location for new attachments » sur
  le dossier `docs/assets/images`.
- Plugin communautaire **Templater** :
  - « Template folder location » : `templates` ;
  - activer « Trigger Templater on new file creation » ;
  - « Folder templates » : `docs/journal/posts` → `templates/journal.md`, et
    `docs/decisions` → `templates/adr.md`.

Créer une note dans `docs/journal/posts/` applique alors le modèle journal et
renomme le fichier à la date du jour (`AAAA-MM-JJ.md`). Créer une note dans
`docs/decisions/` demande le titre de la décision et nomme le fichier à partir
de ce titre.

Le dossier `templates/` est hors de `docs/`, il n'est donc pas publié.

### Navigation

Le menu se construit tout seul : une nouvelle page apparaît dans sa section, son
titre est le premier `# Titre` du fichier. Chaque dossier contient un fichier
caché `.nav.yml` qui donne le nom de la section et l'ordre des pages ; les
pages qui n'y sont pas listées sont ajoutées à la suite, par ordre alphabétique
de nom de fichier.

## Construire le site en local

Le site est généré avec [Zensical](https://zensical.org/).

```sh
pip install zensical
zensical serve   # aperçu sur http://localhost:8000
zensical build   # génère site/
```

Chaque push sur `main` publie le site sur GitHub Pages
(`.github/workflows/docs.yml`).
