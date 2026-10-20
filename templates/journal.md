<%* const jour = tp.date.now("YYYY-MM-DD"); await tp.file.rename(jour); -%>
---
date: <% jour %>
---

# Semaine <% tp.date.now("WW") %> (<% tp.date.now("YYYY") %>)

<!-- more -->

## Fait

- <% tp.file.cursor() %>

## À suivre

- 
