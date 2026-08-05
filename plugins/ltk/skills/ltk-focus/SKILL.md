---
name: ltk-focus
description: >
  Garde le cap au milieu d'une session déjà engagée. Fait trois choses à chaque nouvelle
  demande : affûte la demande si elle est floue ou risquée, tient à jour le registre des
  sujets ouverts (ce qui bloque le chantier courant) **et le carnet des idées neuves**
  (chantiers ou projets qui viennent d'apparaître), et traite la dérive en capturant l'idée
  avant de recommander où la traiter. Utilise-la en cours de travail — « on est encore dans
  le sujet ? », « qu'est-ce qui reste en suspens », « liste les sujets ouverts », « quelles
  idées on a eues ? », « note ça pour plus tard », « on dérive non ? », « je devrais ouvrir
  une autre conversation ? », « LtkFocus », « ltk focus », « fais un focus » — mais aussi de
  ta propre initiative quand une demande ambiguë arrive sur un travail déjà engagé, quand une
  idée de chantier ou de projet neuf est lancée en passant, ou quand la demande ne relève
  plus de l'objectif de séance. Ni pour ouvrir une session (ltk-start / LtkStart), ni pour la
  clore (ltk-exit / LtkExit).
---

# LtkFocus — tenir le cap en cours de séance

## Pourquoi

Une session se dégrade rarement d'un coup. Elle dérive.

On commence par indexer un disque ; une question sur les relevés bancaires arrive ; on y
répond ; elle en appelle une autre ; trois heures plus tard la conversation porte sur une
base de données et plus personne ne sait si l'indexation est terminée. Rien n'a été mal
fait — mais l'objectif de départ est en suspens, les points soulevés en chemin sont perdus,
et la conversation n'a plus de titre honnête.

Trois pertes distinctes se produisent, et cette compétence traite les trois :

- **la demande floue**, qui produit un travail plausible mais à côté
- **le sujet soulevé et jamais traité**, qui disparaît sans que personne ne l'ait décidé
- **la dérive**, qui alourdit la conversation d'un contexte devenu inutile et rend
  impossible de la nommer, de la retrouver et de la clore proprement

## Quand intervenir — et surtout quand se taire

Cette compétence est la plus facile à rendre insupportable. Une intervention à chaque
message transforme un assistant en contremaître.

**Interviens** quand l'une de ces trois conditions est remplie :

| Condition | Signe concret |
|---|---|
| La demande est floue **et** l'enjeu est réel | Périmètre non nommé, ou action irréversible, sur un travail long |
| Un sujet ouvert va se perdre | Un point soulevé il y a plusieurs échanges n'a reçu aucune suite |
| La conversation a changé de sujet | La demande courante ne sert plus l'objectif de séance |

**Tais-toi** dans tous les autres cas — et notamment : demande claire, tâche courte,
correction en cours, ou dérive assumée par l'utilisateur qui vient de dire qu'il change de
sujet exprès. Une compétence de cadrage qui parle plus que le travail n'avance a échoué.

## 1 · Affûter la demande entrante

Applique la méthode de `ltk-prompt`, mais **en version brève** : la session est en cours, le
contexte est déjà partagé, et un cadrage complet serait redondant.

Concrètement, trois lignes suffisent : ce que tu as compris, ce que tu as tranché toi-même,
et la seule question qui reste — s'il y en a une.

```markdown
**Ce que je vais faire.** <périmètre exact, en une phrase>
**Ce que je tranche.** <choix pris par défaut, pour ne pas t'interrompre>
**Ce que je ne peux pas deviner.** <une question, deux au maximum — ou rien>
```

Puis exécute. Ne bloque que si une action irréversible dépend de la réponse.

**Le point d'arrêt reste obligatoire dès qu'il y a du destructif.** Séparer *observer* de
*agir* — inventorier, montrer ce qu'on ferait, puis exécuter avec un journal réversible —
vaut au milieu d'une séance autant qu'à son début. La familiarité acquise en deux heures de
travail n'est pas une autorisation.

## 2 · Tenir deux registres, pas un

Une conversation produit deux choses très différentes, et les confondre en perd une.

| Registre | Ce qu'on y met | Rapport au cap | Où ça finit |
|---|---|---|---|
| **Sujets ouverts** | Un point **soulevé mais non tranché** *dans le chantier courant* : question posée en passant, anomalie repérée, décision reportée | Il sert le cap | Le handoff du chantier |
| **Idées** | Un **chantier ou un projet neuf** qui vient d'apparaître : « il faudrait un jour… », « ça marcherait aussi pour… », « tiens, et si… » | Il sort du cap | Le carnet d'idées, durable |

**La distinction n'est pas administrative.** Un sujet ouvert bloque le travail en cours :
tant qu'il n'est pas tranché, quelque chose n'avance pas. Une idée ne bloque rien — elle
ouvre. Les mélanger produit une liste où l'urgent et le prometteur se noient ensemble, et
qu'on finit par ne plus lire.

### Le registre des sujets ouverts

```markdown
## Sujets ouverts
1. **<sujet>** — soulevé <quand>, en attente de <quoi : une décision, une info, du temps>
```

Tiens la liste au fil de l'eau, et ressors-la quand l'utilisateur la demande ou quand la
séance approche de sa fin. **Un point traité en sort** : une liste qui ne se vide jamais
n'est plus lue.

À la clôture, `ltk-exit` la reprend telle quelle pour « Ce qui reste à faire » et
« Questions en suspens ». Sans elle, ces sections se reconstituent de mémoire, donc mal.

### Le registre des idées

C'est le registre que l'on oublie de tenir, et c'est le plus coûteux à perdre : **un sujet
ouvert se redécouvre en relisant le travail ; une idée, non.** Elle n'a laissé aucune trace
dans le code ni dans les fichiers — elle n'existait que dans la conversation.

```markdown
## Idées apparues
1. **<l'idée en une ligne>** — venue de <ce qui l'a fait naître>, porterait sur <projet ou
   chantier neuf>
```

Le champ **« venue de »** est le seul qui compte vraiment. Une idée sans son déclencheur est
inutilisable trois semaines plus tard : on relit « faire un plugin pour les relevés » sans
retrouver *pourquoi* c'était une bonne idée ce jour-là, et on ne sait plus si elle valait
quelque chose.

**Note l'idée, ne la suis pas.** Deux phrases, puis retour au cap immédiat. Développer
l'idée sur place, c'est faire exactement la dérive que cette compétence sert à éviter — et
c'est la tentation la plus forte, parce qu'une idée neuve est toujours plus séduisante que
le travail en cours.

À la clôture, `ltk-exit` verse ce registre dans le **carnet d'idées** du dossier de travail —
`IDEES.md` à la racine de l'arbre. Pas en mémoire : la mémoire contient des faits durables,
pas des intentions. Pas dans un handoff : une idée de projet neuf n'appartient encore à aucun
projet.

## 3 · Traiter la dérive — capturer sans suivre

### Reconnaître la dérive — et à quel niveau elle se produit

**La dérive n'est pas un défaut à supprimer.** C'est ainsi qu'on découvre du travail qu'on
n'avait pas prévu : la plupart des bons chantiers naissent à côté d'un autre. Une compétence
qui se contenterait de ramener au cap ferait perdre exactement ce qui a le plus de valeur.

Le tort n'est pas de dériver, c'est de **suivre** la dérive au lieu de la **noter** — ou de
la refuser sans rien en garder. Dans les deux cas on perd quelque chose : le cap dans le
premier, l'idée dans le second.

Il ne s'agit donc pas de changer de fichier ni d'outil : un même chantier traverse dix
fichiers. Ce qui compte est **de quel niveau on change**.

| Ce qui change | Exemple | Ce que tu fais |
|---|---|---|
| Rien — même chantier | On passe de l'écriture au test | Tu te tais |
| Une **idée** est lancée sans qu'on la suive | « il faudrait un jour un plugin pour les relevés » | **Tu la notes** au registre des idées, deux phrases, et tu reviens au cap |
| **Le chantier**, même projet | Du plugin à la réorganisation mémoire, dans le même dépôt | Tu notes l'idée si c'en est une, tu signales que le chantier précédent est à clore, et tu continues ici |
| **Le projet** | Du dépôt de compétences à la base Finance | Tu notes, **puis** tu recommandes une conversation neuve — dans cet ordre |

C'est la distinction utile, et elle évite le principal défaut de cette compétence : signaler
une dérive à chaque inflexion. Changer de chantier à l'intérieur d'un projet est **normal** —
les chemins sont partagés, le contexte sert encore. Ce qui n'est pas normal, c'est de laisser
le chantier précédent s'éteindre sans être clos : c'est ainsi qu'un travail à 90 % ne se
termine jamais.

Un test qui recoupe le tableau : *si je devais nommer cette conversation maintenant, le titre
couvrirait-il encore ce qu'on vient de faire ?* Si la réponse impose un « et » entre deux
**projets** — « compétences Ltk **et** migration de la base » — il y a dérive au sens fort.
Un « et » entre deux chantiers d'un même projet ne demande qu'une clôture, pas un départ.

### Pourquoi ouvrir une nouvelle conversation plutôt que continuer

Ce n'est pas une question de propreté. Trois coûts concrets :

1. **Le contexte du premier sujet ne disparaît pas.** Il reste chargé, il coûte, et il pèse
   sur le raisonnement du second — on répond à la migration de base avec les réflexes de
   l'indexation de disques.
2. **Un seul handoff pour deux sujets n'est retrouvé par aucun des deux.** Il sera rangé
   dans un projet, sous un nom ; la moitié de son contenu sera invisible pour l'autre.
3. **Le premier sujet est abandonné sans être clos.** Personne n'a décidé de l'arrêter : il
   a simplement cessé d'être mentionné. C'est ainsi qu'un travail à 90 % ne se termine jamais.

### Comment le dire

Sans dramatiser, en trois lignes, et **en proposant la sortie plutôt qu'en refusant** :

```markdown
**Noté :** <le nouveau sujet, en une ligne> — au carnet d'idées, on ne le perd pas.

**On change de projet**, en revanche : <l'ancien> et <le nouveau> ne partagent ni dossier ni
objectif. Je recommande de clore <l'ancien> avec LtkExit — il reste <N> point(s) ouvert(s) —
puis d'ouvrir une conversation neuve pour <le nouveau>, que LtkStart cadrera.

Si tu préfères enchaîner ici, dis-le et je continue : c'est ton arbitrage, pas une règle.
```

**L'ordre des deux paragraphes n'est pas cosmétique.** Commencer par « on change de sujet »
se lit comme un refus, et l'idée doit alors être défendue avant d'être notée. Commencer par
« noté » dit que rien n'est perdu — la recommandation qui suit devient une question de
rangement, pas d'autorisation.

Le dernier point n'est pas une politesse. L'utilisateur a souvent une bonne raison
d'enchaîner — une urgence, une question courte, un lien entre les deux sujets qu'il voit et
que tu ne vois pas. Signale une fois, puis obéis. Répéter l'avertissement à chaque message
est le meilleur moyen de faire désinstaller la compétence.

## 4 · Ouvrir un chantier — ou proposer un projet

Noter une idée au carnet est le bon geste quand elle **sort du cap**. Mais il arrive qu'elle
soit au contraire ce qu'on est en train de faire : le travail a glissé vers autre chose, ce
quelque chose mérite d'exister, et le laisser sans nom revient à le faire sans le ranger.

C'est le troisième cas, entre « se taire » et « noter pour plus tard » : **ouvrir**.

### La frontière, qui décide de ton geste

| Ce qui apparaît | Ce que tu fais | Pourquoi |
|---|---|---|
| Un **chantier** dans un projet existant | **Ouvre-le**, annonce-le en une ligne, continue | C'est du rangement : un objectif de plus dans un lieu qui existe déjà |
| Un **projet** entier | **Propose-le**, n'agis pas | C'est une décision durable de rangement : elle appartient à l'utilisateur |

La même règle qu'à la clôture, et pour la même raison : créer un dossier dans un projet
existant n'engage rien, créer un projet engage la carte de l'arbre.

### Ouvrir un chantier

Une ligne, puis on continue — ce n'est pas une cérémonie :

```markdown
**Nouveau chantier :** `<projet>` → `<chantier>`. J'ouvre, on poursuit.
```

Concrètement : rien à créer tout de suite. Le chantier existe dès qu'il est **nommé**, et
son handoff s'écrira à la clôture — `ltk-exit` sait créer le `handoff/` et l'`INDEX.md`
manquants. Nommer tôt sert à autre chose : le registre des sujets ouverts se range dès lors
sous le bon chantier, et la clôture n'aura pas à démêler deux travaux mélangés.

**Le titre de la conversation vient de devenir faux.** C'est le moment le plus utile pour le
dire, parce que c'est le seul où l'écart est visible : le titre annonce un chantier, on en
mène un autre. Applique la nomenclature du `CLAUDE.md` de l'arbre — format et règle `Divers`
y sont définis —, donne la ligne `/rename` prête à coller, et continue sans attendre la
réponse.

```
/rename PROJET · Chantier · AAAA.MM.JJ
```

**Une fois par nouveau chantier, pas davantage.** Reproposer un titre à chaque inflexion est
exactement le travers qui fait désinstaller cette compétence.

**Quand ouvrir plutôt que noter :** le test d'indépendance, comme partout. Si ce qu'on fait
maintenant pourrait être clos sans que le chantier de départ le soit, c'est déjà un second
chantier — même si personne ne l'a décidé.

### Proposer un projet

Un projet neuf demande un dossier, une entrée dans la carte de l'arbre, souvent un dépôt.
Rien de tout cela ne se décide en passant. Propose, et **n'attends pas la réponse pour
continuer le travail en cours** :

```markdown
**Ceci mérite son propre projet.** `<nom>` — <ce qu'il couvre>, distinct de <projet actuel>
parce que <la raison>. Il faudrait un dossier, une ligne dans la carte des projets, et
peut-être un dépôt.

Je note l'idée au carnet en attendant ta réponse ; dis-moi si je l'ouvre.
```

**Note au carnet dans tous les cas**, immédiatement. Une proposition sans réponse se perd
exactement comme une idée non notée — et l'utilisateur qui répond « oui » trois jours plus
tard trouvera alors le contexte intact.

## Le piège de cette compétence

Elle porte sur la conversation, pas sur le travail. C'est ce qui la rend utile — et c'est
aussi ce qui la rend facile à sur-appliquer, parce qu'il y a toujours quelque chose à dire
sur la forme d'un échange.

Le critère est le même partout : **est-ce que mon intervention change ce qui va être fait ?**
Si elle ne fait que commenter la façon dont on travaille, elle n'a pas lieu d'être.
