---
name: ltk-exit
description: >
  Clôt **une conversation** — on la quitte, on n'y revient pas — sans rien perdre, et
  **sèchement** : elle produit des fichiers, pas un discours. Contrôle sur le disque ce
  qu'elle va déclarer livré et ce qui a cessé d'exister, découpe la séance en chantiers,
  écrit un handoff par chantier dans le `handoff/` de son projet, met à jour l'index, publie
  si le projet est versionné, propose un titre, et range en mémoire, en CLAUDE.md ou au
  carnet d'idées ce qui doit survivre. **Rien à choisir** : le statut d'un chantier se dérive
  de sa liste de tâches — non vide, il est ouvert. Utilise-la sur « on s'arrête là », « je
  reprends demain », « c'est bon pour moi », « clôture cette conversation », « LtkExit »,
  « ltk exit », « fais un exit » — et de ta propre initiative quand un livrable est vérifié
  et qu'aucun blocage ne subsiste. **Jamais en cours de séance sur un travail qui
  continue** : « récapitule » demande un point, pas une clôture — c'est ltk-focus (LtkFocus).
  Jumelle de ltk-start (LtkStart), qui relit ces handoffs.
---

# LtkExit — clôture de session

## Pourquoi

Une conversation est volatile. Le contexte accumulé pendant une session — les décisions et
leurs raisons, les fausses pistes déjà écartées, les pièges découverts à la dure —
disparaît avec elle. La personne qui reprend (souvent l'utilisateur lui-même, trois
semaines plus tard) recommence à zéro et refait les mêmes erreurs.

**Trois choses à ne pas confondre**, parce qu'elles ne se terminent pas ensemble :

| | Se termine-t-il ? | Ce qu'un `exit` en fait |
|---|---|---|
| La **conversation** | Oui, définitivement — on n'y revient pas | C'est elle qu'on clôt |
| Le **chantier** | Peut-être. Il continuera ailleurs si besoin | On constate son état |
| Le **projet** | Non, il vit | On y range le handoff |

Un `exit` dit donc une seule chose : *je quitte cette conversation, et je ne perds rien.*
Le travail, lui, n'est pas tenu de s'arrêter avec elle.

Un handoff n'est pas un résumé. Un résumé raconte ce qui s'est passé ; un handoff transmet
**ce qui permet de continuer sans se retromper**. C'est la différence entre le compte rendu
d'une garde hospitalière et le journal intime du médecin.

## Étape 1 — Vérifier avant d'écrire

C'est la première étape, et elle n'est pas facultative.

`ltk-start` traitera ce fichier comme une source d'autorité : il en lira les chemins, il
s'appuiera sur ce qui y est déclaré fait. **Une erreur qui entre ici en ressort trois
semaines plus tard, validée par le format.** Écrire « les 301 relevés sont consolidés »
sur la foi de la conversation, alors que la copie a échoué à mi-parcours, est pire que ne
rien écrire du tout.

Avant de rédiger, contrôle donc sur le disque :

- chaque livrable cité **existe** au chemin annoncé, et n'est pas vide
- les compteurs annoncés (nombre de fichiers, de lignes, de tables) correspondent
- ce qui est décrit comme « installé » ou « poussé » l'est réellement

Ce contrôle est le symétrique exact de l'étape 2 de `ltk-start` : l'une vérifie à la
lecture, l'autre à l'écriture. Si une divergence apparaît, ne la corrige pas en silence —
elle se consigne, parce qu'elle est probablement la chose la plus utile du document.

### Et ce qui a **cessé** d'exister

Vérifier que les livrables existent ne suffit pas : il faut aussi chercher les traces de ce
qui a disparu pendant la séance. **Une mémoire ne se sait pas fausse** — elle sera relue à la
session suivante avec la même confiance qu'au premier jour, et rien ne signalera qu'elle
décrit un monde révolu.

Pour chaque fichier, dossier ou compétence supprimé, déplacé ou renommé pendant la séance,
cherche son nom dans :

- le `CLAUDE.md` de l'utilisateur — chargé à **chaque** session de **tous** ses projets
- le `CLAUDE.md` du projet et de ses dossiers parents
- les fichiers mémoire, index compris

Puis corrige, **dans cette séance**. Reporter, c'est laisser une instruction fausse s'exécuter
demain. Cas vécu : la suppression d'une compétence a laissé pendant une heure deux fichiers
qui ordonnaient de l'utiliser, dont le `CLAUDE.md` global.

### Une clôture n'installe rien, ne répare rien

**Interdit absolu : ne copie jamais une compétence, un plugin ou un outil pendant une
clôture.** Pas dans `~/.claude/skills/`, pas ailleurs. Une clôture *constate* et *consigne* ;
elle ne modifie pas l'environnement de travail.

Le piège est précis, et il est déclenché par les handoffs eux-mêmes : un ancien document
contient souvent une commande de dépannage prête à l'emploi — « restaurer en une ligne :
`Copy-Item …` ». En la relisant pendant la clôture, on est tenté de l'exécuter par sécurité.
On crée alors **une seconde source de la même compétence**, qui prend le pas sur celle du
plugin **en silence** : les corrections publiées ensuite ne redescendent plus, et rien ne le
signale. C'est le pire défaut du système, et une clôture est le dernier endroit où il devrait
naître.

Si tu constates une duplication ou une compétence manquante : **écris-le dans le handoff, ne
la corrige pas.** Et n'écris jamais dans un handoff une commande de copie directement
exécutable — décris le dépannage en une phrase, la prochaine séance décidera en connaissance
de cause.

## Étape 2 — Délimiter le chantier : un chantier, un handoff

Avant tout, décide **de quoi** ce handoff parle. Deux niveaux, et un seul se
clôt :

| Niveau | Ce que c'est | Se termine-t-il ? |
|---|---|---|
| **Projet** | Un lieu de travail : un dossier, un dépôt, un domaine | Non. Il vit. |
| **Chantier** | Un objectif daté à l'intérieur du projet | **Oui** — et c'est ce qu'un handoff clôt |

Le test qui tranche : **deux travaux forment deux chantiers si l'un peut être clos sans que
l'autre le soit.** S'ils ne peuvent se terminer qu'ensemble, c'est un seul chantier ; sinon,
deux — même s'ils ont été menés dans la même conversation, le même dossier et la même heure.

**Écris un handoff par chantier, et clos-le dès que le chantier est fini** — pas à la fin de
la conversation. Une session qui a avancé sur trois chantiers produit trois handoffs, pas un
gros.

Ce n'est pas de la mise en forme. Un handoff qui couvre plusieurs chantiers mélange des
« reste à faire » qui ne s'adressent pas aux mêmes reprises, ne peut jamais passer au statut
`clos` puisqu'une de ses parties traîne toujours, et double de volume — donc cesse d'être lu.
Cas vécu : un handoff de 9 700 octets couvrant quatre chantiers, deux fois la taille des
précédents. Comprimer n'était pas la réponse : il fallait clore au fil de l'eau.

Quand le découpage n'est pas évident, propose-le en une ligne — « je vois deux chantiers ici,
X et Y, je clos les deux séparément » — et n'attends pas de réponse pour continuer.

**Trois cas demandent plus de méthode** : une conversation qui traverse plusieurs projets, un
projet dont le `handoff/` ou l'`INDEX.md` manque, et un handoff qui gonfle au-delà de
~5 000 caractères. Lis `references/cas-particuliers.md` quand l'un se présente — pas avant.

## Étape 3 — Dériver l'état, ne pas le décider

**Il n'y a rien à choisir, et rien à demander.** L'état d'un chantier se calcule à partir
d'un seul fait, celui que tu viens d'établir à l'étape 1 :

> **Reste-t-il quelque chose à faire ?**
> Oui → `statut: ouvert`. Non → `statut: clos`.

C'est tout. La liste « Ce qui reste à faire » du handoff **est** la liste de tâches du
chantier, et son contenu détermine le statut. Une tâche existe, le chantier est ouvert ; la
liste est vide, il est clos.

| Niveau | Ouvert quand | Se termine-t-il ? |
|---|---|---|
| **Chantier** | Sa liste « reste à faire » n'est pas vide | Oui |
| **Projet** | Au moins un de ses chantiers est ouvert | Non — il vit |
| **Conversation** | — | Toujours, définitivement |

**Pourquoi dériver plutôt que juger.** Un état déclaré à la main dérive de la réalité en une
séance : on marque `clos` un chantier qui garde trois tâches, l'index ment, et la reprise
s'appuie dessus. Un état calculé ne peut pas mentir — au pire la liste est incomplète, et ça
se voit en la lisant.

C'est aussi ce qui rend le système utilisable comme outil de productivité : *toutes les
tâches ouvertes de l'arbre* se lisent d'une commande, sans ouvrir un seul fichier —
`python Partage/scripts/todo.py`.

Annonce le résultat en une ligne par chantier, avec le classement. L'utilisateur corrige
d'un mot si une tâche manque ou traîne pour rien.

## Étape 4 — Écrire le fichier

Destination : `handoff/` à la racine du projet concerné (crée le dossier au besoin).
Nom : `AAAA-MM-JJ-<chantier-en-minuscules-avec-tirets>.md`.

Écrire un fichier plutôt que d'afficher le texte dans la conversation n'est pas un détail :
c'est toute la valeur de l'exercice. Un message se perd avec la conversation ; un fichier se
retrouve, se versionne, se partage, et sera relu par `ltk-start` à la prochaine session.

Ensuite, affiche le chemin du fichier et trois lignes de résumé. Ne recopie pas le contenu
intégral : ce serait le dupliquer au moment précis où l'on cherche à éviter la duplication.

### L'en-tête, dans les deux modes

Tout handoff commence par cet en-tête. Il n'est pas décoratif : `ltk-start` s'en sert pour
vérifier l'environnement automatiquement, au lieu de repérer les chemins à la lecture — donc
de façon exhaustive plutôt qu'attentive.

```yaml
---
projet: <le lieu de travail — dossier, dépôt, domaine>
chantier: <l'objectif que ce handoff clôt, en minuscules avec tirets>
statut: ouvert           # ou : clos — l'état du CHANTIER, pas de la conversation
date: AAAA-MM-JJ
chemins-clefs:
  - chemin: <chemin absolu>
    attendu: present     # ou : absent
    note: <ce qu'on doit y trouver, ou pourquoi il doit avoir disparu>
interdits:
  - <chemin ou action à ne surtout pas toucher — vide si rien>
---
```

Renseigne `chemins-clefs` avec ce qu'il faudrait tester pour savoir si le handoff est encore
valable : les livrables, pas les fichiers de travail. Cinq entrées au maximum ; au-delà,
personne ne les vérifie.

**Le champ `attendu` n'est pas une formalité.** Tous les chemins ne doivent pas exister : un
handoff dit souvent « ceci a été installé » *et* « cela doit maintenant disparaître ». Sans
`attendu`, `ltk-start` teste l'existence des deux, trouve les deux, et conclut « rien n'a
bougé » — alors que la persistance du second était précisément ce qu'il fallait signaler.
Une vérification qui ne peut rien conclure de négatif ne vérifie rien.

**Nomme le chemin précis, jamais son parent** — surtout avec `attendu: absent`. Un dossier
parent survit à son contenu : vider `~/.claude/skills/` en supprimant les quatre
sous-dossiers laisse le dossier lui-même en place, et un contrôle sur le parent conclura
« toujours là » alors que le travail a bien été fait. Écris
`~/.claude/skills/ltk-start`, pas `~/.claude/skills`. La règle vaut dans l'autre sens aussi :
un parent qui existe ne prouve pas que ce qu'on y attendait s'y trouve.

**Avant le premier `push` vers un dépôt**, lis `references/ecrire-pour-durer.md` : un
handoff versionné a un historique permanent, et un dépôt privé peut devenir public bien
après qu'on a cessé d'y penser.

### Le corps — un seul gabarit

```markdown
# <Projet> · <Chantier>
*<date> — conversation close ; chantier <clos | ouvert>*

## Où on en est
<Deux à cinq phrases. L'état réel, pas l'intention. Ce qui tourne, ce qui est vérifié.>

## Ce qui a été livré
- **<livrable>** — `<chemin>` — <ce que c'est, comment le vérifier>

## Décisions structurantes (ne pas les rouvrir)
- **<décision>** — <l'alternative écartée et pourquoi ; ce que ça implique>

## Ce qui reste à faire
<La liste de tâches du chantier. Elle détermine son statut : non vide = ouvert.>
1. [ ] <action décidée, avec le fichier ou la commande concernée>
<Si le chantier est clos, écris « rien » — jamais une section absente.>

## Limites connues
<Ce que le résultat ne couvre pas, les approximations assumées, les seuils choisis.
C'est la section la plus utile dans un an — ne la bâcle jamais, chantier clos ou non.>

## Pièges découverts
- **<piège>** — <comment il se manifeste, comment l'éviter>

## Interdits
<Ce qu'il ne faut surtout pas faire sur ce projet. Vide si rien.>

## Pour reprendre
<Chemins des fichiers clés, commandes à relancer, état de l'environnement.
Par où commencer, et ce qu'il ne faut surtout pas casser.>

## Vérifié à l'instant
<Ce que le contrôle de l'étape 1 a confirmé — ou démenti.>

## Questions en suspens
<Décisions non prises, en attente de l'utilisateur ou d'un tiers. Vide si aucune.>
```

**« Ce qui reste à faire » et « Questions en suspens » ne se recouvrent pas** :

> **Reste à faire** = des actions **décidées**. Il n'y a qu'à les exécuter.
> **Questions en suspens** = des décisions **non prises**. Personne ne peut avancer sans réponse.

Sans cette distinction, les deux sections se recopient et le lecteur ne sait plus ce qu'on
attend de lui : agir, ou trancher.

**Ne supprime jamais une section parce qu'elle est vide** — écris « rien ». Une section
absente est ambiguë : elle peut signifier « il n'y a rien » ou « je n'ai pas regardé ».

### Où trouver la matière

Les sections « Ce qui reste à faire » et « Questions en suspens » ne se reconstituent pas de
mémoire à la fin d'une longue session : on n'y remet que ce dont on se souvient, c'est-à-dire
les dernières heures. Si `ltk-focus` a tenu le registre des sujets ouverts, **reprends-le tel
quel** — c'est exactement ce pour quoi il existe.

## Étape 5 — Mettre à jour l'index

Ajoute une ligne à `handoff/INDEX.md` (crée le fichier s'il n'existe pas). **L'index est
groupé par projet, et les chantiers ouverts passent en tête** — c'est sur cet index que
`ltk-start` fera choisir la reprise, donc il doit se lire d'un coup d'œil.

```markdown
# Handoffs

## Projet : disque-x
| Chantier | Date | Statut | En attente de | Fichier |
|---|---|---|---|---|
| Consolidation bancaire | 2026-08-05 | **ouvert** | Lecture des PDF | [2026-08-05-consolidation-bancaire.md](2026-08-05-consolidation-bancaire.md) |
| Inventaire des disques | 2026-08-04 | clos | — | [2026-08-04-inventaire.md](2026-08-04-inventaire.md) |
```

La colonne **« En attente de »** vaut le détour : trois mots qui disent pourquoi le chantier
n'avance pas — une décision, une information, du temps. C'est ce qui permet de choisir entre
deux chantiers ouverts sans ouvrir aucun des deux.

Passe à `clos` le statut d'un chantier que celui-ci referme.

Une ligne de plus à écrire ici évite à `ltk-start` d'ouvrir cinq fichiers pour deviner lequel
parle du bon chantier. Avec trois handoffs, l'index ne sert à rien ; avec trente, c'est lui
qui rend la reprise possible.

## Étape 6 — Publier le handoff, si le projet est versionné

**Écrit n'est pas conservé.** Un handoff posé dans un dépôt Git mais jamais commité est
invisible depuis les autres postes et disparaît au prochain clone. Toute la promesse
« une conversation se perd, un fichier reste » ne tient alors que sur une seule machine.

Si le projet est un dépôt Git, commite le handoff et l'index, et pousse. Le message de
commit se contente de nommer le sujet et le mode — le détail est dans le fichier.

**Vérifie la visibilité du dépôt avant le premier envoi**, et dis-la. Ce qui part vers un
dépôt public y reste, y compris dans l'historique ; ce qui part vers un dépôt d'équipe est lu
par toute l'équipe. C'est le moment de relire le handoff avec la règle « écris la règle, pas
les chemins » en tête — après le `push`, la correction coûte une réécriture d'historique.

Si le projet n'est pas versionné, dis-le : c'est une information utile, surtout quand
l'utilisateur travaille sur plusieurs postes.

## Étape 7 — Proposer un titre de conversation

Un handoff parfait dans une conversation introuvable ne sert à rien.

**Le format et la règle `Divers` sont dans le `CLAUDE.md` de l'arbre de travail**, section
« Nomenclature des titres de conversation ». Relis-le plutôt que de le redéfinir : une seule
source, et aucune divergence possible.

Les champs viennent de ce que tu viens d'écrire — `PROJET` est le `projet:` de l'en-tête en
majuscules, `Chantier` le `chantier:` **mot pour mot**, la date celle du handoff. Et tu as
fait l'inventaire à l'étape 2, donc tu as les compteurs sous la main pour appliquer `Divers`.

Termine par la ligne prête à coller, en disant que c'est à l'utilisateur de l'exécuter :
l'outil de renommage refuse la conversation en cours, et c'est une contrainte qu'un
copier-coller contourne, pas une impossibilité.

```
/rename PROJET · Chantier · AAAA.MM.JJ
```

Si d'**autres** conversations mal nommées apparaissent au passage, signale-le en une ligne et
n'y touche pas : un titre écrasé ne se récupère pas, et ce plugin ne propose délibérément
aucun renommage de masse.

## Ce que tu affiches — sèchement

Une clôture produit des **fichiers**, pas un discours. Tout ce qui mérite d'être dit est
déjà dans les handoffs ; le redire dans la conversation, c'est dupliquer au moment précis
où l'on cherche à éviter la duplication — et la conversation, elle, va disparaître.

Ta réponse finale tient en **une dizaine de lignes** :

```markdown
| Projet · Chantier | Statut | Fichier |
|---|---|---|
| ltk · outillage | clos | `Partage/handoff/2026-08-05-outillage.md` |
| ltk · plugin | **ouvert** (3 tâches) | `Partage/handoff/2026-08-05-plugin.md` |

Index à jour · poussé sur `Leadtrunk/ltk` · sauvegarde lancée.

/rename LTK · Divers · 2026.08.05
```

**Ce que tu n'écris pas** : le résumé de ce que contiennent les handoffs, la liste des
décisions, le rappel des pièges, les remerciements, la proposition de continuer. Rien de
tout cela n'aide — l'utilisateur ferme la conversation, c'est le but.

**La seule exception** : une divergence trouvée à l'étape 1. Un livrable annoncé qui
n'existe pas, une compétence dupliquée, un chemin qui ment. Ça se dit en une phrase, en
haut, parce que c'est la seule information que la clôture produit et que les fichiers ne
portent pas encore.

Si tu te surprends à écrire un troisième paragraphe, relis cette section : ce que tu es en
train d'expliquer avait sa place dans un handoff, et tu viens de l'écrire au mauvais
endroit.

## Étape 8 — Trancher où va ce qui doit survivre

« Pousser en mémoire » est un raccourci trompeur : il y a **trois** lieux de stockage, et
c'est le flou entre eux qui produit les doublons — la même règle à deux endroits, et quand
l'une change, l'autre ment.

| Lieu | Ce qu'on y met | Portée | Durée |
|---|---|---|---|
| **`CLAUDE.md`** | Ce que l'utilisateur **impose** : règles, interdits, conventions | Le dossier **et ses sous-dossiers** | Permanent |
| **Mémoire** | Ce que tu as **appris** : contraintes découvertes, pièges d'environnement, décisions et leur raison | Le dossier exact, **pas** ses sous-dossiers | Durable |
| **`handoff/`** | Où en est **un travail** | Un sujet | Le temps du chantier |

Le test tient en une question : *si l'utilisateur changeait d'assistant demain, cette ligne
devrait-elle survivre ?* Oui, c'est une règle → `CLAUDE.md`. Non, c'est une observation faite
en travaillant → mémoire. Elle ne vaut que pour ce chantier → le handoff que tu viens
d'écrire, et rien d'autre.

**Attention à la portée.** La mémoire est indexée sur le dossier ouvert : elle ne suit pas
dans les sous-dossiers. Un fait qui doit valoir dans tous les sous-projets d'un arbre va donc
dans un `CLAUDE.md` posé à la racine de cet arbre — c'est le seul mécanisme qui traverse.

Concrètement, pour chaque fait retenu qui va en mémoire : un fichier, une ligne d'index. Ne
mets jamais le contenu dans l'index — il est chargé à chaque session, il doit rester une
table des matières.

### Le quatrième lieu : le carnet d'idées

Le tableau ci-dessus couvre ce qui est **acquis**. Il manque ce qui est seulement
**envisagé** — un chantier ou un projet neuf apparu en cours de route.

Ça n'a sa place dans aucun des trois : ce n'est pas une règle, ce n'est pas un fait établi,
et ça n'appartient encore à aucun projet — donc à aucun `handoff/`. Ça va dans
**`IDEES.md` à la racine du dossier de travail**, avec ce qui l'a fait naître :

```markdown
## 2026-08-05
- **<l'idée en une ligne>** — venue de <le déclencheur>, porterait sur <projet ou chantier>
```

Si `ltk-focus` a tenu le registre des idées, verse-le tel quel. Sinon, relis la conversation
en cherchant les « il faudrait un jour », « ça marcherait aussi pour », « tiens, et si ».

**Une idée sans son déclencheur est perdue même si elle est écrite** : trois semaines plus
tard on relit la ligne sans retrouver pourquoi elle paraissait bonne, et on ne sait plus si
elle valait quelque chose. Le « venue de » est ce qui la rend réutilisable.

Ne verse pas ce qui a été explicitement écarté pendant la séance — c'est une décision, elle
va dans le handoff. Le carnet est fait pour ce qui n'a été ni retenu ni refusé.

### Sauvegarder ce qui vient de changer

**Si le projet dispose d'un mécanisme de sauvegarde pour ses `CLAUDE.md` et sa mémoire,
déclenche-le ici.** C'est le seul moment où l'on sait qu'ils viennent de changer ; attendre,
c'est compter sur quelqu'un pour y penser plus tard. Ces fichiers vivent hors des dépôts de
projet : rien d'autre ne les couvre.

Le tri est plus sévère qu'il n'y paraît. Un fait mérite la mémoire s'il est **vrai en dehors
de ce travail** : « le Drive partagé est en lecture seule » oui ; « la copie des relevés est
terminée » non, c'est du handoff. Et **la mémoire ne répète jamais une règle du `CLAUDE.md`** :
elle peut en garder le *pourquoi* et l'origine, jamais l'énoncé. En cas d'hésitation, ne pas
écrire : une mémoire encombrée de faits périmés est pire qu'une mémoire vide, parce qu'on lui
fait encore confiance.

## Ce qui mérite d'être écrit

Le réflexe naturel est de tout consigner. C'est une erreur : un handoff de six pages n'est
pas lu, donc il ne sert à rien. Le tri se fait sur un critère simple — **est-ce
reconstituable ?**

Écris ce qui ne se retrouve nulle part ailleurs :
- les décisions **et leur justification** (le code montre le quoi, jamais le pourquoi)
- les pistes explorées puis abandonnées, avec la raison — sinon on les réexplorera
- les pièges d'environnement : chemins trompeurs, montages en double, contraintes réseau
- les interdits, et ce qui les motive
- les seuils choisis à la main, qui paraîtront arbitraires sans explication

N'écris pas ce qu'un `ls`, un `git log` ou une lecture du code redonnerait en trente
secondes : liste des fichiers créés, détail des modifications, chronologie des tentatives.
