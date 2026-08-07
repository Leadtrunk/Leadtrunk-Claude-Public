---
name: ltk-start
description: >
  Ouvre une session de travail sur de bonnes bases, sujet déjà entamé ou tout neuf — même
  quand l'utilisateur ne nomme pas la reprise et repart où on s'était arrêté. Sur un sujet
  existant : retrouve et relit le dernier handoff, vérifie que l'environnement décrit existe
  encore, restitue où on en est. Sur une area neuve : établit le dossier, l'espace GitHub,
  l'objectif et les interdits — sans ce cadrage pour un essai jetable. Déclenche-toi en début
  de conversation dès qu'une demande suppose un historique, un projet ou une area non
  encore vu — dit explicitement (« on reprend », « où en étions-nous », « continue/reprends
  le projet X », « nouvelle area », « on démarre un truc », « LtkStart »/« ltk start »)
  ou implicite (« je reviens de vacances, on avait un truc en cours », un dossier `handoff/`
  détecté). Pas en cours de session engagée (ltk-focus/LtkFocus), pour une simple mention de
  CLAUDE.md sans intention de reprise, ou pour écrire un handoff de clôture — jumelle de
  ltk-exit (LtkExit), qui les écrit.
---

# LtkStart — ouverture de session

## Pourquoi

Le danger d'un début de session n'est pas de manquer d'informations : c'est d'en inventer.
Sans contexte, on reconstruit une version plausible de l'area, on rouvre des décisions déjà
tranchées, on réexplore des pistes déjà abandonnées, et on découvre les pièges une seconde
fois — parfois en les déclenchant.

Sur une area neuve, le danger est symétrique : on se met à produire avant d'avoir nommé où
l'on range, ce qu'on cherche, et ce qu'on n'a pas le droit de casser. Les trois se
découvrent alors trop tard, quand le travail est déjà fait au mauvais endroit.

Cinq minutes de cadrage au démarrage valent mieux qu'une heure de travail dans la mauvaise
direction. Cette compétence rend ces cinq minutes systématiques, dans les deux cas.

## Étape 0 — Reprise ou démarrage ?

Ne pose pas la question tout de suite : cherche d'abord, c'est souvent déjà tranché.

Il s'agit d'une **reprise** si tu trouves l'un de ces signes : un dossier `handoff/`, un
`CLAUDE.md` d'area, un dépôt Git avec un historique, une mémoire area qui nomme le
sujet. Passe alors à l'étape 1.

Il s'agit d'un **démarrage** si tu ne trouves rien de tout cela, ou si l'utilisateur annonce
explicitement un nouveau sujet. Passe à l'étape D.

En cas de doute — un dossier existe mais rien n'y ressemble au sujet annoncé — dis ce que tu
as trouvé et demande. C'est une des rares questions qui valent une interruption : traiter une
area vivante comme une area neuve revient à écrire par-dessus.

---

# A · Reprise d'un sujet existant

## Étape 1 — Retrouver le projet, et le faire choisir

Une area est un **lieu** — un dossier, un dépôt — et elle ne se termine pas. Un **projet**
est un objectif daté à l'intérieur, et c'est lui qui se clôt. Une area a donc souvent
plusieurs projets, dont plusieurs ouverts en même temps : **reprendre une area ne dit pas
lequel on reprend.**

Cherche dans cet ordre, et arrête-toi au premier résultat utile :

1. `handoff/INDEX.md` — s'il existe, il donne pour chaque projet son area, sa date, son
   statut et ce qu'il attend. Choisis dedans, puis n'ouvre **que le ou les fichiers retenus**.
   C'est plus fiable et bien moins coûteux que d'ouvrir les fichiers un à un.
2. `handoff/` à la racine de l'area — le fichier le plus récent dont le nom correspond au
   projet ; à défaut, le plus récent tout court
3. La mémoire de l'area — elle contient les faits durables, pas l'état d'avancement
4. `CLAUDE.md` de l'area et de l'utilisateur — les règles et interdits permanents
5. `README.md` — pour la structure, pas pour l'avancement

### Quand plusieurs projets sont ouverts

**Ne choisis pas à sa place, et ne prends surtout pas « le plus récent » par défaut.** La date
d'écriture ne dit rien de l'urgence : un projet bloqué depuis trois semaines sur une
décision passe pour vieux alors qu'il est le plus pressant.

Présente les projets ouverts en un tableau court, puis laisse choisir — **un, plusieurs, ou
tous** :

```markdown
L'area <nom> a <N> projets ouverts :

| # | Projet | Dernier point | En attente de |
|---|---|---|---|
| 1 | <nom> | <date> | <une décision / une info / du temps> |
| 2 | <nom> | <date> | <…> |

Lequel reprend-on ? Je recommanderais le <n°> : <raison — en général celui qui fait courir
un risque ou qui bloque les autres>. Tu peux aussi en prendre plusieurs, ou tout.
```

Plusieurs projets d'un coup se justifient quand ils partagent des chemins ou qu'une même
décision les débloque — dis-le alors explicitement. Mais **méfie-toi** : c'est aussi ainsi
qu'on refabrique la conversation fourre-tout que le découpage en projets évite. Si les
projets choisis n'ont rien en commun, signale-le une fois, puis obéis.

Si rien n'existe, dis-le franchement : le sujet est peut-être un démarrage déguisé
(étape D). Ne comble jamais l'absence de handoff par des suppositions — mieux vaut annoncer
« aucun historique trouvé » que restituer un contexte imaginaire.

### Le titre de la conversation, tant que tu y es

Une reprise démarre presque toujours dans une conversation neuve, donc sans titre — ou dans
une ancienne au titre générique. C'est le meilleur moment pour le poser : **tu viens
d'identifier l'area et le projet**, les deux champs dont le titre a besoin. Une heure
plus tard, il faudra les redéduire.

Si plusieurs projets étaient ouverts, ce moment n'arrive qu'**après** le choix de
l'utilisateur — avant qu'il ait tranché, tu connais l'area mais pas encore le projet, et
un titre posé trop tôt devra être refait. S'il en reprend plusieurs à la fois, ou tous, retiens
simplement le nom de l'area : le titre n'a pas besoin de lister chaque projet.

Applique la nomenclature du `CLAUDE.md` de l'arbre — format et règle `Divers` y sont
définis — et donne la ligne prête à coller, car l'outil de renommage refuse la conversation
en cours :

```
/rename AREA · Projet · AAAA.MM.JJ
```

Une seule fois, puis n'y reviens plus : c'est un confort, pas une condition pour travailler.
Et si d'**autres** conversations portent des titres génériques, signale-le sans y toucher —
un titre écrasé ne se récupère pas.

## Étape 2 — Vérifier avant de croire

**Un handoff décrit l'état de l'area au moment où il a été écrit, pas aujourd'hui.**
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
- les commandes de redémarrage sont-elles toujours valides ? Pas seulement la commande en
  elle-même : ses prérequis aussi. Un `netlify dev` sans configuration Netlify dans le
  dossier a autant de chances d'échouer qu'un chemin qui a disparu — le principe est le
  même, seul l'objet vérifié change.
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

Format court. L'utilisateur connaît son area ; il a besoin d'un point de repère, pas
d'un cours.

```markdown
## Reprise : <sujet>
*Handoff du <date> — <REPRISE ou ARCHIVE>*

**Où on en est.** <deux ou trois phrases>

**Décisions à ne pas rouvrir.** <les deux ou trois plus structurantes>

**Interdits sur cette area.** <s'il y en a — toujours les rappeler>

**Tâches restantes.**
1. <…>

**Vérifié à l'instant.** <ce qui a changé depuis le handoff, ou « rien n'a bougé »>
```

Si rien n'a changé, dis-le en un mot : c'est une information, pas un vide à combler.

## Étape 4 — Faire choisir et affûter l'objectif de la séance

Une liste de tâches restantes n'est pas un plan. Termine en demandant laquelle des tâches
ouvertes on traite maintenant, en indiquant celle que tu recommanderais **et pourquoi** —
en général celui qui fait courir un risque, avant ceux qui apportent du confort.

Une fois l'objectif choisi, **applique la méthode de `ltk-prompt` pour l'affûtage lui-même —
pas sa clôture par le titre**, déjà posée à l'étape 1 : vérifie la prémisse derrière
l'objectif si elle ne l'a pas déjà été, tranche toi-même ce qui relève du bon sens, et si des
trous changeraient matériellement le travail, propose-les en raffinements classés et
justifiés — jamais en condition pour commencer. Si l'objectif est déjà net, exécute
directement : affûter une demande claire est une perte de temps qui décrédibilise l'outil.
Si le travail est manifestement récurrent (« chaque mois », « à chaque nouveau client »…),
le point 7 de la méthode s'applique aussi : propose de le figer en template dès cette
première fois.

Ces raffinements restent facultatifs, jamais bloquants : le reste de la séance doit ensuite
avancer sans validation à chaque pas. En cours de route, c'est `ltk-focus` qui prend le
relais.

---

# D · Démarrage d'une area neuve

Cinq choses se décident au départ, et une seule est vraiment coûteuse à changer ensuite :
le dossier. Traite-les dans cet ordre.

## D0 — L'idée était peut-être déjà notée

Avant de cadrer quoi que ce soit, **lis `IDEES.md` à la racine du dossier de travail** s'il
existe. C'est là que `ltk-exit` verse les projets et areas entrevus lors des séances
précédentes, avec ce qui les a fait naître.

Deux cas, tous deux utiles :

- **L'area qui démarre y figure déjà.** Le « venue de » te donne son contexte d'origine —
  ce que l'utilisateur avait en tête, et qu'il a probablement oublié. C'est du cadrage
  gratuit, et il vaut mieux que ce qu'on reconstruirait maintenant.
- **Il n'y figure pas, mais des idées voisines si.** Dis-le en une ligne : elles éclairent
  souvent le périmètre, et c'est le moment de décider si elles entrent dans cette area ou
  restent au carnet.

Puis **retire du carnet l'idée qui devient une area** : elle n'est plus une intention, elle
a un dossier. Un carnet qui ne se vide jamais cesse d'être lu — c'est la même règle que pour
le registre des sujets ouverts.

## D1 — Où ça vit, en local

Nomme le dossier de travail et **vérifie-le avant de créer quoi que ce soit** :

- le chemin existe-t-il déjà, et que contient-il ? Ne réutilise jamais un dossier non vide
  sans le dire.
- y a-t-il assez de place, si l'area manipule du volume ?
- **le dossier est-il sous synchronisation cloud ?** Une area posée dans un Drive partagé
  ou un OneDrive d'équipe expose chaque écriture à tous les collaborateurs, et chaque
  suppression aussi. Signale-le avant, jamais après.

## D1bis — Où ça vit, sur GitHub

Dès qu'une area est susceptible d'être versionnée ou partagé, **demande l'espace GitHub
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

Tranche toi-même tout ce qui relève du bon sens et annonce ton choix. Ce qui changerait
matériellement le travail selon la réponse devient un raffinement optionnel — classé, justifié
en une ligne, jamais une condition pour démarrer — deux ou trois au maximum. Si l'objectif
lui-même est récurrent (un rapport à produire chaque mois, une tâche répétée pour chaque
client…), c'est le moment de proposer le point 7 de la méthode : le figer en template dès la
première fois plutôt que de refaire ce travail à la deuxième.

## D3 — Ce qu'on n'a pas le droit de casser

Demande explicitement les interdits, et relis ceux qui existent déjà dans le `CLAUDE.md`
de l'utilisateur — ils s'appliquent à la nouvelle area aussi. Trois questions suffisent :

- quels chemins sont en lecture seule, ou appartiennent à quelqu'un d'autre ?
- quelles données sont irremplaçables ?
- qu'est-ce qui est partagé avec d'autres personnes, donc modifiable par elles ?

Un interdit non écrit au départ est un interdit qu'on découvre en le franchissant.

## D4 — Poser la structure minimale

Crée, dans le dossier de travail :

- `handoff/` — vide, mais il existe : c'est ce qui rendra la reprise possible, et ce qui
  fera se déclencher cette compétence à la prochaine session
- `CLAUDE.md` — court : l'objectif de l'area, les interdits, les chemins de référence.
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

**Travail mené en parallèle ailleurs.** Si l'area mentionne d'autres conversations
actives sur les mêmes fichiers, vérifie l'état réel du disque plutôt que de te fier au
handoff, et dis à l'utilisateur ce que tu constates. Deux sessions qui écrivent au même
endroit sans se voir est le scénario où l'on perd du travail.

**Handoff écrit par quelqu'un d'autre.** Les chemins sont ceux de son poste, pas du tien.
Vérifie-les tous avant d'en citer un seul.

**Chemin-clef qui ressemble à un espace de sortie de session.** Si une entrée de
`chemins-clefs` pointe vers ce qui ressemble à un dossier de travail temporaire d'une
séance claude.ai/Cowork plutôt qu'à un chemin appartenant à l'utilisateur (dépôt, NAS,
poste local), ne conclus rien de sa présence ou de son absence — ce genre de chemin ne
survit généralement pas à la conversation qui l'a créé, et le tester ne prouve ni ne
réfute quoi que ce soit. Signale-le comme non vérifiable plutôt que comme « disparu ».

**Handoff en ancienne taxonomie.** Un en-tête qui porte un champ `chantier:` plutôt que
`projet:`, ou un `INDEX.md` qui parle de « chantiers » plutôt que de « projets », vient
d'avant le passage à la taxonomie Area/Projet. Ne le retraite pas silencieusement — annonce
ce que tu as trouvé, propose le nouveau nommage, et **retraite un fichier à la fois, sur
confirmation** : c'est une réécriture de fichiers existants, pas une simple lecture, et elle
suit la même règle que tout ce qui touche au rangement — l'utilisateur décide, tu exécutes.

```markdown
Ce handoff utilise l'ancienne taxonomie (`chantier:` au lieu de `projet:`). Je peux le
convertir : `chantier: X` devient `projet: X`, l'ancien niveau « projet » (le dossier)
devient `area:`. Je fais la conversion, ou je continue avec l'ancien format pour
aujourd'hui ?
```

Si l'utilisateur confirme, convertis ce fichier et son entrée dans `INDEX.md` — pas les
autres handoffs du même area tant qu'ils n'ont pas été rouverts : retraiter tout un
historique d'un coup dépasse le périmètre d'une reprise, et le fichier archivé n'a de toute
façon plus besoin d'être exact dans le vocabulaire courant.
