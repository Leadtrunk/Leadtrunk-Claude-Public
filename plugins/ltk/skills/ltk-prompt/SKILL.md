---
name: ltk-prompt
description: >
  Transforme une demande floue en demande exécutable : fait apparaître le périmètre, les
  critères implicites, les interdits applicables, les étapes et les points de validation,
  puis restitue un texte prêt à réutiliser. Utilise cette compétence quand l'utilisateur la
  demande explicitement — « améliore ce prompt », « reformule ma demande », « comment je
  devrais te demander ça », « aide-moi à mieux formuler », « écris-moi un prompt pour… »,
  « LtkPrompt », « ltk prompt » — ou avant de lancer un travail long, coûteux ou destructif
  dont la formulation laisse un trou majeur. Elle est aussi la méthode de référence
  qu'appliquent ltk-start (LtkStart) pour cadrer l'objectif d'une séance et ltk-focus
  (LtkFocus) pour affûter une demande en cours de route : dans ces deux cas, ce sont elles
  qui se déclenchent, pas celle-ci. Utile enfin pour construire des demandes réutilisables —
  tâches récurrentes, consignes d'équipe.
---

# Affûter une demande

## Le principe

Une demande floue ne produit pas un mauvais travail : elle produit un travail *plausible*,
qui rate la cible pour des raisons qu'on ne découvre qu'à la fin. Le coût n'est pas dans la
formulation, il est dans le travail jeté.

Affûter n'est pas rallonger. Une demande affûtée est souvent à peine plus longue —
simplement, elle répond aux questions que l'exécutant se serait posées en silence, et
tranche les ambiguïtés au lieu de les laisser se résoudre par hasard.

## La méthode

### 1. Charger les interdits avant de commencer

Le trou le plus coûteux n'est pas celui qu'on repère dans la demande : c'est celui que
l'utilisateur n'a pas mentionné parce qu'il lui paraît évident. Les interdits sont
exactement de cette nature — on ne pense à les dire qu'après les avoir vus franchir.

Ils sont pourtant déjà écrits. Avant d'affûter quoi que ce soit, relis :

- le `CLAUDE.md` de l'utilisateur — les règles permanentes, tous projets confondus
- le `CLAUDE.md` du projet — ce qui est propre à ce travail
- la mémoire — les pièges d'environnement et les contraintes déjà consignés
- le handoff en cours, s'il y en a un — sa section « Interdits »

Reporte-les dans la section CONTEXTE de la demande affûtée, **même quand l'utilisateur ne
les a pas évoqués**. C'est la différence entre un cadrage qui protège et un cadrage qui
décore.

### 2. Vérifier les prémisses avant d'affûter

Une demande porte presque toujours un « parce que » implicite : *rends ce dépôt public
**parce que** l'équipe ne peut pas l'installer autrement*, *déplace ces fichiers **parce
qu'**ils sont en double*. Affûter une demande sans examiner ce « parce que », c'est rendre
très précise une action fondée sur du faux.

C'est le pire des ratés, parce qu'il est invisible : le travail est propre, cadré, exécuté
sans erreur — et il n'aurait pas dû avoir lieu.

Alors, avant tout le reste : **repère la prémisse, et teste-la.** Un chemin qu'on liste, une
commande qu'on lance, une documentation qu'on lit. Trente secondes, contre un travail entier
à refaire.

**Y compris — surtout — quand la prémisse vient de toi.** Une affirmation technique lancée
en passant à l'échange précédent devient la fondation de la demande suivante, et personne ne
la remet en cause : l'utilisateur te fait confiance, et toi tu ne relis pas ce que tu as
écrit. Cas vécu : « le dépôt privé empêche l'équipe d'installer le plugin » — faux, un
membre de l'organisation avec accès en lecture installe normalement. L'utilisateur a rendu
un dépôt public sur cette base.

Si la prémisse est fausse, **dis-le avant d'affûter quoi que ce soit** : la demande n'a
peut-être plus lieu d'être, et c'est l'information la plus utile que tu puisses rendre.

### 3. Repérer les trous

Relis la demande en te demandant : *sur quoi vais-je devoir inventer une réponse ?*
Les trous les plus coûteux, par ordre de fréquence :

- **Le périmètre** — « mes fichiers », « la base », « le site » : lesquels, où, combien ?
- **Le critère de réussite** — à quoi reconnaît-on que c'est réussi ? Selon quel seuil ?
- **Le format de sortie** — un fichier ? lequel ? un rapport ? une modification en place ?
- **Le degré d'irréversibilité** — lecture seule, ou déplacement, écrasement, suppression ?
- **Les interdits** — ce qu'il ne faut surtout pas toucher, et qu'on n'apprend qu'après.
- **Le niveau d'explication** — travail livré brut, ou pédagogie à chaque étape ?

### 4. Distinguer ce que tu peux trancher de ce que tu dois demander

C'est le cœur du métier. Tranche toi-même ce qui relève du bon sens professionnel et
annonce ton choix. Ne demande que ce qui, selon la réponse, mènerait à un travail
*différent* — pas simplement à un travail *légèrement autre*.

Deux ou trois questions maximum. Une demande affûtée qui s'accompagne de huit questions
n'a fait que déplacer la charge sur l'utilisateur.

### 5. Découper en étapes avec points d'arrêt

Dès qu'un travail comporte une action difficile à annuler, sépare **observer** de **agir** :

1. inventorier / analyser — aucune modification, on regarde
2. proposer — on montre ce qu'on ferait, on attend l'accord
3. exécuter — avec un essai à blanc, puis un journal permettant de revenir en arrière

Ce découpage est ce qui rapporte le plus. Il transforme un pari en série de décisions
informées.

### 6. Restituer

Rends la demande affûtée dans un bloc de code, prête à être copiée ou réutilisée, suivie
d'une explication courte de **ce que tu as changé et pourquoi**. L'explication compte
autant que le texte : c'est elle qui apprend à l'utilisateur à formuler mieux la fois
suivante, jusqu'à ne plus avoir besoin de cette compétence.

## Structure de sortie

````markdown
## Ta demande affûtée

```
CONTEXTE
<le périmètre exact : chemins, volumes, systèmes concernés>
<les contraintes : ce qui est interdit, ce qui est fragile — y compris ce qui vient
 du CLAUDE.md et de la mémoire, non redemandé à l'utilisateur>

OBJECTIF
<ce qu'on cherche à obtenir, et à quoi on reconnaîtra que c'est atteint>

ÉTAPES
1. <observation — sans rien modifier>
2. <proposition — à valider>
3. <exécution — essai à blanc, puis journal réversible>

FORMAT ATTENDU
<fichier, rapport, modification en place... et où>

PRÉFÉRENCES
<niveau d'explication, ton, langue>
```

## Ce que j'ai changé
- **<changement>** — <pourquoi ça évite quoi>

## Ce que je ne peux pas deviner
1. <question dont la réponse changerait le travail>
````

## Exemple

**Demande d'origine :** « Je veux indexer, trier et organiser un grand nombre de fichiers
sur mon disque local. »

**Trous repérés :** aucun chemin, aucun volume, aucun critère de rangement, et surtout
aucune indication sur l'irréversibilité — « organiser » peut vouloir dire *produire un
inventaire* ou *déplacer 500 000 fichiers*. L'écart de risque entre les deux est immense.

**Affûtage :** nommer le disque et l'ordre de grandeur ; séparer explicitement l'inventaire
(lecture seule) de la réorganisation (déplacements) ; exiger un essai à blanc et un journal
d'annulation avant tout déplacement ; nommer les zones interdites — dont le Drive partagé
d'équipe, que l'utilisateur n'avait pas mentionné mais que son `CLAUDE.md` protège.

**Ce que ça a évité, concrètement :** le chemin fourni au départ ne contenait que des
fichiers fantômes du cloud, et une déduplication naïve aurait proposé de supprimer des
originaux vus par deux chemins différents. L'étape d'observation a révélé les deux avant
qu'une seule donnée ne soit touchée.

## Terminer par le titre — la ligne prête à coller

Un handoff parfait dans une conversation introuvable ne sert à rien. Le titre se pose donc
**maintenant**, tant que le projet et le chantier sont sous les yeux : trois semaines plus
tard, il faudrait rouvrir la conversation pour les redéduire.

**Le format et la règle `Divers` sont dans le `CLAUDE.md` de l'arbre de travail**, section
« Nomenclature des titres de conversation ». Ne le redéfinis pas ici — relis-le, applique-le.

Termine par la ligne, en disant que c'est à l'utilisateur de l'exécuter : l'outil de
renommage refuse la conversation en cours, et c'est une contrainte qu'un copier-coller
contourne, pas une impossibilité.

```
/rename PROJET · Chantier · AAAA.MM.JJ
```

Une fois par séance suffit. Reproposer un titre à chaque inflexion est le travers qui fait
désinstaller une compétence.

## Deux pièges à éviter

**Affûter n'est pas s'approprier la demande.** Le résultat doit rester la demande de
l'utilisateur, en plus net. Si tu te surprends à ajouter des objectifs qu'il n'a pas
formulés, tu es en train de redéfinir son travail à sa place — signale-les comme
suggestions séparées plutôt que de les glisser dans le texte affûté.

**Une demande affûtée n'est pas un formulaire.** Si la demande d'origine est déjà claire,
dis-le et exécute. Faire passer un « renomme ce fichier » par une structure en trois
étapes est une perte de temps qui décrédibilise l'outil quand il sert vraiment.
