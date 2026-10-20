# LMDC (Lavaduck Mini Datacenter)

!!! warning "En construction"
    Ce projet et cette documentation sont en cours de construction et peuvent changer à tout moment.

Ce site recueille l'ensemble des notes, schémas, procédures et projets de mon homelab.

Le but de ce lab est de ne pas me restreindre aux couches hautes du modèle OSI comme mon métier de DevOps le voudrait, mais d'également apprendre les couches basses, tel que le réseau, ou l'obscure couche physique.

Il a pour objectif de répliquer au mieux ce qu'on pourrait retrouver dans une (modeste) entreprise, et est également utilisé comme une prod personnelle.

## Organisation

| Section | Contenu |
| --- | --- |
| [Architecture](architecture/index.md) | Matériel, réseau (VLAN, flux, IPAM), conventions de nommage |
| [Décisions](decisions/index.md) | Les ADR : pourquoi chaque choix technique a été fait |
| [Exploitation](exploitation/index.md) | Runbooks, incidents, évolutions et troubleshooting |
| [Projet](projet/index.md) | Roadmap, todo, backlog d'idées et de projets, finances |
| [Journal](journal/index.md) | Le suivi des actions effectuées dans le lab, au fil du temps |

Le code d'infrastructure (Packer, OpenTofu, Ansible) vit dans des dépôts séparés ; ce site documente l'architecture et les décisions, et renvoie vers la documentation de référence du code.

## La place de l'IA

Au début, ce projet de documentation a été mis en place avec de l'assistance de la part de Claude (Pro) avec un profil type Socratique (qui force l'utilisateur à s'interroger).

Désormais, aucune IA n'est utilisée pour coder, documenter, valider ni quoi que ce soit.

Les actions sont effectuées à la suite de recherches et ne seront donc pas toujours parfaites.

## Vos retours

Je suis ouvert à tout retour que vous pourriez me proposer, que cela soit sur du réseau, de la méthode de documentation, du choix de matériel ou un questionnement sur mes choix, ils sont les bienvenus.
