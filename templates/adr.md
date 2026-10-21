<%*
const titre = await tp.system.prompt("Titre de la décision");
const slug = titre.toLowerCase().normalize("NFD").replace(/[̀-ͯ]/g, "")
  .replace(/[^a-z0-9]+/g, "-").replace(/^-+|-+$/g, "");
const nums = app.vault.getMarkdownFiles()
  .filter(f => f.parent.path === "docs/decisions")
  .map(f => parseInt(f.basename.slice(0, 4), 10))
  .filter(n => !isNaN(n));
const num = String((nums.length ? Math.max(...nums) : 0) + 1).padStart(4, "0");
await tp.file.rename(`${num}-${slug}`);
-%>
# <% num %>. <% titre %>

- **Date** : <% tp.date.now("YYYY-MM-DD") %>
- **Statut** : proposé | accepté | remplacé par NNNN

## Contexte

<% tp.file.cursor() %>Quel problème se pose, et quelles contraintes s'appliquent ?

## Options envisagées

- **Option A** : avantages, inconvénients.
- **Option B** : avantages, inconvénients.

## Décision

Ce qui a été choisi, et pourquoi.

## Conséquences

Ce que cela implique : ce qui devient plus simple, ce qui devient plus difficile, ce qu'il faudra surveiller.
