---
name: ltk-start
description: >
  Ouvre une session de travail sur de bonnes bases, qu'il s'agisse d'un sujet déjà entamé
  ou d'un projet qui démarre. Sur un sujet existant : retrouve et relit le dernier handoff,
  vérifie que l'environnement décrit existe encore, restitue où en est le travail. Sur un
  projet neuf : établit le dossier de travail, l'espace GitHub, l'objectif, les critères de
  réussite et les interdits, puis pose la structure de reprise. Utilise cette compétence au
  tout début d'une conversation — quand l'utilisateur dit « on reprend », « où en
  étions-nous », « continue le chantier X », « nouveau projet », « on démarre un truc »,
  « LtkStart », « ltk start », « fais un start », ou donne un nom de projet sans autre
  contexte — mais aussi de ta propre initiative quand tu détectes un dossier `handoff/`,
  ou quand une demande suppose un historique que tu n'as pas. Pas en cours de session sur
  un travail déjà engagé : c'est le rôle de ltk-focus (LtkFocus). Jumelle de ltk-exit
  (LtkExit), qui écrit les handoffs qu'elle relit.
---

# LtkStart — ouverture de session

## Pourquoi

Le danger d'un début de session n'est pas de manquer d'informations : c'est d'en inventer.
Sans contexte, on reconstruit une version plausible du projet, on rouvre des décisions déjà
tranchées, on réexplore des pistes déjà abandonnées, et on découvre les pièges une seconde
fois — parfois en les déclenchant.

Sur un projet neuf, le danger est symétrique : on se met à produire avant d'avoir nommé où
l'on range, ce qu'on cherche, et ce qu'on n'a pas le droit de casser. Les trois se
découvrent alors trop tard, quand le travail est déjà fait au mauvais endroit.

Cinq minutes de cadrage au démarrage valent mieux qu'une heure de travail dans la mauvaise
direction. Cette compétence rend ces cinq minutes systématiques, dans les deux cas.

## Étape 0 — Reprise ou démarrage ?

Ne pose pas la question tout de suite : cherche d'abord, c'est souvent déjà tranché.

Il s'agit d'une **reprise** si tu trouves l'un de ces signes : un dossier `handoff/`, un
`CLAUDE.md` de projet, un dépôt Git avec un historique, une mémoire projet qui nomme le
sujet. Passe alors à l'étape 1.

Il s'agit d'un **démarrage** si tu ne trouves rien de tout cela, ou si l'utilisateur annonce
explicitement un nouveau sujet. Passe à l'étape D.

En cas de doute — un dossier existe mais rien n'y ressemble au sujet annoncé — dis ce que tu
as trouvé et demande. C'est une des rares questions qui valent une interruption : traiter un
projet vivant comme un projet neuf revient à écrire par-dessus.

---

# A · Reprise d'un sujet existant

## Étape 1 — Retrouver le chantier, et le faire choisir

Un projet est un **lieu** — un dossier, un dépôt — et il ne se termine pas. Un **chantier**
est un objectif daté à l'intérieur, et c'est lui qui se clôt. Un projet a donc souvent
plusieurs chantiers, dont plusieurs ouverts en même temps : **reprendre un projet ne dit pas
lequel on reprend.**

Cherche dans cet ordre, et arrête-toi au premier résultat utile :

1. `handoff/INDEX.md` — s'il existe, il donne pour chaque chantier son projet, sa date, son
   statut et ce qu'il attend. Choisis dedans, puis n'ouvre **que le ou les fichiers retenus**.
   C'est plus fiable et bien moins coûteux que d'ouvrir les fichiers un à un.
2. `handoff/` à la racine du projet — le fichier le plus récent dont le nom correspond au
   chantier ; à défaut, le plus récent tout court
3. La mémoire du projet — elle contient les faits durables, pas l'état d'avancement
4. `CLAUDE.md` du projet et de l'utilisateur — les règles et interdits permanents
5. `README.md` — pour la structure, pas pour l'avancement

### Quand plusieurs chantiers sont ouverts

**Ne choisis pas à sa place, et ne prends surtout pas « le plus récent » par défaut.** La date
d'écriture ne dit rien de l'urgence : un chantier bloqué depuis trois semaines sur une
décision passe pour vieux alors qu'il est le plus pressant.

Présente les chantiers ouverts en un tableau court, puis laisse choisir — **un, plusieurs, ou
tous** :

```markdown
Le projet <nom> a <N> chantiers ouverts :

| # | Chantier | Dernier point | En attente de |
|---|---|---|---|
| 1 | <nom> | <date> | <une décision / une info / du temps> |
| 2 | <nom> | <date> | <…> |

Lequel reprend-on ? Je recommanderais le <n°> : <raison — en général celui qui fait courir
un risque ou qui bloque les autres>. Tu peux aussi en prendre plusieurs, ou tout.
```

Plusieurs chantiers d'un coup se justifient quand ils partagent des chemins ou qu'une même
décision les débloque — dis-le alors explicitement. Mais **méfie-toi** : c'est aussi ainsi
qu'on refabrique la conversation fourre-tout que le découpage en chantiers évite. Si les
chantiers choisis n'ont rien en commun, signale-le une fois, puis obéis.

Si rien n'existe, dis-le franchement : le sujet est peut-être un démarrage déguisé
(étape D). Ne comble jamais l'absence de handoff par des suppositions — mieux vaut annoncer
« aucun historique trouvé » que restituer un contexte imaginaire.

### Le titre de la conversation, tant que tu y es

Une reprise démarre presque toujours dans une conversation neuve, donc sans titre — ou dans
une ancienne au titre générique. C'est le meilleur moment pour le poser : **tu viens
d'identifier le projet et le chantier**, les deux champs dont le titre a besoin. Une heure
plus tard, il faudra les redéduire.

Applique la nomenclature du `CLAUDE.md` de l'arbre — format et règle `Divers` y sont
définis — et donne la ligne prête à coller, car l'outil de renommage refuse la conversation
en cours :

```
/rename PROJET · Chantier · AAAA.MM.JJ
```

Une seule fois, puis n'y reviens plus : c'est un confort, pas une condition pour travailler.
Et si d'**autres** conversations portent des titres génériques, signale-le sans y toucher —
un titre écrasé ne se récupère pas.

## Étape 2 — Vérifier avant de croire

**Un handoff décrit l'état du projet au moment où il a été écrit, pas aujourd'hui.**
Fichiers déplacés, dépendances mises à jour, montages réseau absents, travaux menés dans
une autre conversation entre-temps : l'écart est la règle, pas l'exception.

Si le handoff porte un en-tête `chemins-clefs`, teste chacune de ces entrées : c'est
précisément à cela qu'il sert, et la vérification devient alors mécanique et exhaustive
plutôt que dépendante de ta lecture. Sinon, relève les chemins à la lecture.

**Lis le champ `attendu` de chaque entrée, pas seulement le chemin.** Tous les chemins ne
doivent pas exister : un handoff dit souvent « ceci a été installé » *et* « cela doit
maintenant avoir disparu ». Un chemin marqué `attendu: absent` qui est toujours là est un
**écart à signaler**, pas une confirmation. Se contenter de tester l'existence revient à ne
pouvoir conclure que du positif — donc à ne rien vérifier.

Vérifie, avant de t'appuyer dessus :

- les chemins cités sont-ils dans l'état attendu, et contiennent-ils ce qui est annoncé ?
- les commandes de redémarrage sont-elles toujours valides ?
- les volumes réseau ou lecteurs mentionnés sont-ils montés ?
- ce qui est décrit comme « fait » l'est-il réellement sur le disque ?

Une divergence n'est pas un incident : c'est l'information la plus précieuse de la séance.
Signale-la explicitement plutôt que de l'absorber en silence.

### La mémoire se vérifie comme le handoff

C'est la symétrie qui manque le plus souvent : on se méfie du handoff, et on fait aveuglément
confiance à la mémoire — alors qu'elle est **plus vieille** et qu'elle revient
automatiquement, sans que rien ne rappelle depuis quand elle n'a pas été relue.

Donc : **quand un fait en mémoire nomme un fichier, un dossier, une compétence ou un
paramètre, vérifie qu'il existe encore avant de t'y fier.** Une mémoire ne se sait pas fausse.
Si elle l'est, corrige-la dans la séance plutôt que de la contourner — sinon la prochaine
session retombera dessus.

## Étape 3 — Restituer

Format court. L'utilisateur connaît son projet ; il a besoin d'un point de repère, pas
d'un cours.

```markdown
## Reprise : <sujet>
*Handoff du <date> — <REPRISE ou ARCHIVE>*

**Où on en est.** <deux ou trois phrases>

**Décisions à ne pas rouvrir.** <les deux ou trois plus structurantes>

**Interdits sur ce projet.** <s'il y en a — toujours les rappeler>

**Ce qui restait à faire.**
1. <…>

**Vérifié à l'instant.** <ce qui a changé depuis le handoff, ou « rien n'a bougé »>
```

Si rien n'a changé, dis-le en un mot : c'est une information, pas un vide à combler.

## Étape 4 — Faire choisir et affûter l'objectif de la séance

Une liste de tâches restantes n'est pas un plan. Termine en demandant lequel des points
ouverts on traite maintenant, en indiquant celui que tu recommanderais **et pourquoi** —
en général celui qui fait courir un risque, avant ceux qui apportent du confort.

Une fois l'objectif choisi, **applique la méthode de `ltk-prompt`** : si sa formulation
laisse un trou qui changerait matériellement le travail (périmètre flou, critère de
réussite absent, action irréversible non cadrée), affûte-la avant de commencer — sans
transformer ce cadrage en interrogatoire. Si l'objectif est déjà net, exécute directement :
affûter une demande claire est une perte de temps qui décrédibilise l'outil.

C'est le seul moment où des questions s'imposent vraiment : le reste de la séance doit
ensuite avancer sans validation à chaque pas. En cours de route, c'est `ltk-focus` qui
prend le relais.

---

# D · Démarrage d'un projet neuf

Cinq choses se décident au départ, et une seule est vraiment coûteuse à changer ensuite :
le dossier. Traite-les dans cet ordre.

## D0 — L'idée était peut-être déjà notée

Avant de cadrer quoi que ce soit, **lis `IDEES.md` à la racine du dossier de travail** s'il
existe. C'est là que `ltk-exit` verse les chantiers et projets entrevus lors des séances
précédentes, avec ce qui les a fait naître.

Deux cas, tous deux utiles :

- **Le projet qui démarre y figure déjà.** Le « venue de » te donne son contexte d'origine —
  ce que l'utilisateur avait en tête, et qu'il a probablement oublié. C'est du cadrage
  gratuit, et il vaut mieux que ce qu'on reconstruirait maintenant.
- **Il n'y figure pas, mais des idées voisines si.** Dis-le en une ligne : elles éclairent
  souvent le périmètre, et c'est le moment de décider si elles entrent dans ce projet ou
  restent au carnet.

Puis **retire du carnet l'idée qui devient un projet** : elle n'est plus une intention, elle
a un dossier. Un carnet qui ne se vide jamais cesse d'être lu — c'est la même règle que pour
le registre des sujets ouverts.

## D1 — Où ça vit, en local

Nomme le dossier de travail et **vérifie-le avant de créer quoi que ce soit** :

- le chemin existe-t-il déjà, et que contient-il ? Ne réutilise jamais un dossier non vide
  sans le dire.
- y a-t-il assez de place, si le projet manipule du volume ?
- **le dossier est-il sous synchronisation cloud ?** Un projet posé dans un Drive partagé
  ou un OneDrive d'équipe expose chaque écriture à tous les collaborateurs, et chaque
  suppression aussi. Signale-le avant, jamais après.

## D1bis — Où ça vit, sur GitHub

Dès qu'un projet est susceptible d'être versionné ou partagé, **demande l'espace GitHub
avant le premier `git init`** :

| Espace | Quand | Conséquence |
|---|---|---|
| `github.com/<compte-personnel>/` | Travail personnel, essai, outil pour soi | Personne d'autre n'y a accès par défaut ; publier plus tard demande un transfert |
| `github.com/<organisation>/` | Travail d'équipe, outil destiné aux collègues | Visible et modifiable par l'organisation dès le premier `push` |

C'est le genre de question qui paraît secondaire et ne l'est pas : **elle détermine qui peut
lire, qui peut publier des mises à jour, et ce qu'il faudra défaire pour en changer.**
Déplacer un dépôt d'un espace à l'autre casse les clones existants et les liens déjà
partagés — ce n'est pas grave le premier jour, ça l'est au bout de six mois.

Trois précautions qui vont avec :

- **Ne jamais inviter quelqu'un dans l'organisation sans accord exprès et
  nominatif.** Une invitation d'organisation donne accès à bien plus que le dépôt concerné.
- Un dépôt d'équipe n'est utile que si l'équipe peut l'installer : prévois-en la diffusion
  (plugin, README d'installation) dès le départ, pas après.
- **Pose la question de la visibilité au premier commit, pas au moment de partager.** Un
  dépôt privé qu'on rend public plus tard rend public **tout son historique** d'un coup. Si
  la publication est envisageable un jour, écris dès le départ comme si elle était faite :
  aucun chemin d'infrastructure interne, aucune adresse nominative, aucun identifiant.

## D2 — Ce qu'on cherche

Fais énoncer l'objectif, puis **applique la méthode de `ltk-prompt`** — c'est ici qu'elle
rapporte le plus, parce que rien n'est encore construit. Un objectif utilisable répond à
trois questions : *quel périmètre exactement*, *à quoi reconnaîtra-t-on que c'est réussi*,
et *quelle est la sortie attendue* (un fichier ? une base ? une modification en place ?).

Deux ou trois questions au maximum, et seulement celles dont la réponse mènerait à un
travail *différent*. Le reste, tranche-le et annonce ton choix.

## D3 — Ce qu'on n'a pas le droit de casser

Demande explicitement les interdits, et relis ceux qui existent déjà dans le `CLAUDE.md`
de l'utilisateur — ils s'appliquent au nouveau projet aussi. Trois questions suffisent :

- quels chemins sont en lecture seule, ou appartiennent à quelqu'un d'autre ?
- quelles données sont irremplaçables ?
- qu'est-ce qui est partagé avec d'autres personnes, donc modifiable par elles ?

Un interdit non écrit au départ est un interdit qu'on découvre en le franchissant.

## D4 — Poser la structure minimale

Crée, dans le dossier de travail :

- `handoff/` — vide, mais il existe : c'est ce qui rendra la reprise possible, et ce qui
  fera se déclencher cette compétence à la prochaine session
- `CLAUDE.md` — court : l'objectif du projet, les interdits, les chemins de référence.
  Pas de documentation du code, elle se périme ; seulement ce qui n'est pas déductible.

Puis **restitue le cadrage en dix lignes** et commence le travail. Ne fais pas valider
chaque ligne : ce qui compte est que le cadre soit écrit, pas qu'il soit parfait.

---

## Cas particuliers

**Handoff en mode ARCHIVE.** Le sujet était clos. Ne le rouvre pas mécaniquement : signale
qu'il s'agit d'une archive, résume ce qui a été livré, et demande s'il s'agit d'une reprise
volontaire ou d'une nouvelle question sur un travail terminé.

**Plusieurs handoffs sur le même sujet.** Lis le plus récent en premier. Ne remonte dans
les précédents que si le plus récent renvoie explicitement à eux — l'historique complet
n'a d'intérêt que pour comprendre pourquoi une décision a changé.

**Travail mené en parallèle ailleurs.** Si le projet mentionne d'autres conversations
actives sur les mêmes fichiers, vérifie l'état réel du disque plutôt que de te fier au
handoff, et dis à l'utilisateur ce que tu constates. Deux sessions qui écrivent au même
endroit sans se voir est le scénario où l'on perd du travail.

**Handoff écrit par quelqu'un d'autre.** Les chemins sont ceux de son poste, pas du tien.
Vérifie-les tous avant d'en citer un seul.
