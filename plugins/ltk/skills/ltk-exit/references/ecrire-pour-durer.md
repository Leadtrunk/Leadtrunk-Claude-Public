# Écrire pour durer

Un handoff versionné ne se comporte pas comme une conversation. Une conversation se
referme et s'efface ; un commit Git reste, y compris si le dépôt change de statut plus
tard. Ce document précise ce que ça change avant le premier `push`.

## Le principe, en une phrase

**Écris chaque handoff comme si le dépôt était déjà public** — même s'il est privé
aujourd'hui, et même si sa publication n'est pas prévue. Un dépôt privé qu'on ouvre plus
tard rend public *tout son historique* d'un coup, commits anciens compris ; il n'y a pas de
publication partielle rétroactive.

Ce n'est pas de la paranoïa disproportionnée : c'est la même règle que `ltk-start` applique
dès l'ouverture d'un area (D1bis), appliquée ici à son symétrique — la clôture.

## Ce qui ne doit jamais apparaître dans un handoff

- **Aucun identifiant nominatif** — pas de nom de personne au-delà de ce que le contexte
  professionnel justifie déjà publiquement. « Le client » ou « l'équipe Finance » plutôt
  qu'un nom propre, sauf si ce nom est déjà public par ailleurs (un dépôt open source, une
  entreprise citée dans sa propre documentation publique).
- **Aucun chemin d'infrastructure interne** — adresse de serveur, chemin réseau, nom de
  machine. « Le NAS de l'utilisateur » plutôt que l'adresse exacte du point de montage.
- **Aucun identifiant, token, mot de passe, clef d'API** — même partiel, même expiré. Un
  historique Git garde tout, y compris ce qui a été corrigé dans un commit suivant.
- **Aucune donnée métier chiffrée ou sensible** — montants exacts, volumes réels de
  clients, contenu de documents confidentiels. Décris la nature du travail (« consolidation
  de relevés bancaires ») sans reproduire les données elles-mêmes.

## Ce qui reste parfaitement légitime

La règle porte sur l'identifiable et le secret, pas sur l'utile :

- Les décisions techniques et leur raison — c'est le cœur de ce qu'un handoff doit
  transmettre, et rien de tout cela n'identifie qui que ce soit.
- Les pièges d'environnement, décrits génériquement (« un montage réseau qui se déconnecte
  après une veille prolongée » plutôt que le nom exact du NAS).
- Les seuils et arbitrages choisis à la main.

## Au moment du premier `push`

**Vérifie la visibilité du dépôt avant d'envoyer**, et dis-la explicitement à
l'utilisateur — c'est rappelé dans le corps principal, et ça reste la vérification la plus
importante de l'Étape 6. Si le dépôt est privé mais que sa publication future est
envisageable, applique cette règle dès maintenant plutôt que d'attendre ce jour-là : une
réécriture d'historique après coup est possible, mais coûteuse, et casse les clones déjà
faits par d'autres postes ou d'autres personnes.

En cas de doute sur une ligne précise, la question à se poser est simple : *si ce dépôt
devenait public demain matin, cette phrase poserait-elle un problème à quelqu'un ?* Si la
réponse n'est pas un « non » immédiat, reformule avant d'écrire, pas après.
