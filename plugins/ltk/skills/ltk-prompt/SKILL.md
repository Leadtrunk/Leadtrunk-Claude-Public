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

- le `CLAUDE.md` de l'utilisateur — les règles permanentes, toutes areas confondues
- le `CLAUDE.md` de l'area — ce qui est propre à ce travail
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

### 4. Distinguer ce que tu tranches de ce que tu proposes en option

C'est le cœur du métier. **Tranche toujours toi-même en premier** — y compris les points
qui, selon la réponse, mèneraient à un travail *différent*. Une demande affûtée doit être
complète et utilisable telle qu'elle est livrée : personne ne devrait avoir à répondre à
quoi que ce soit avant de pouvoir s'en servir.

Ce qui changerait matériellement le travail ne disparaît pas pour autant — transforme-le en
**raffinement optionnel**, pas en condition. Deux ou trois maximum, classés par ce qu'ils
changeraient réellement (le plus structurant d'abord), et chacun justifié en une ligne :
pourquoi cette réponse vaut la peine d'être donnée, pas seulement qu'elle existe. Un
raffinement sans raison affichée se traite comme une case à cocher ; un raffinement qui
explique ce qu'il débloque se traite comme une vraie proposition.

Une demande affûtée qui s'accompagne de huit raffinements n'a fait que déplacer la charge
sur l'utilisateur — la limite de deux ou trois reste absolue, seul le statut a changé :
facultatif, jamais bloquant.

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
suivante, jusqu'à ne plus avoir besoin de cette compétence. Elle doit être utilisable
immédiatement, sans attendre de réponse à quoi que ce soit — les raffinements du point 4
viennent après, jamais avant.

### 7. Figer en template réutilisable — seulement si ça le vaut

Ne le fais pas par défaut : la plupart des demandes affûtées servent une fois et n'ont pas
besoin d'exister au-delà de la conversation. Fais-le quand l'utilisateur le demande
explicitement, ou quand la demande porte elle-même sa récurrence (« chaque mois », « à
chaque fois qu'un client… », « pour toute l'équipe »).

Repère dans la demande affûtée ce qui **change à chaque usage** — le mois concerné, le nom
du client, le chiffre du jour — et remplace-le par une variable nommée entre chevrons :
`<mois>`, `<nom-du-client>`. Le reste — la structure, les interdits chargés, le format
attendu — ne bouge pas d'un usage à l'autre : c'est justement ce qui fait qu'un template
vaut la peine d'exister.

**Écris-le dans un fichier réel de l'area**, jamais seulement dans la conversation qui va
disparaître : un fichier `templates/<nom-court>.md` à la racine du dossier de travail
suffit, avec la liste des variables en tête. Une conversation qui referme la sienne sans
avoir écrit ce fichier n'a rien produit de réutilisable — elle a juste bien répondu une
fois. Cas vécu, hors de ce système : un outil concurrent gardait ces templates dans un
historique de session plutôt que dans un fichier — trois d'entre eux ont disparu à la
première reconnexion. Un fichier ne disparaît pas comme ça.

Signale l'existence du fichier une fois, dans la restitution — pas de cérémonie, une ligne :
`Template enregistré : templates/rapport-mensuel-ibf.md (variables : <mois>, <franchise>)`.

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

## Raffinements possibles — facultatifs
1. **<le plus structurant>** <question> — <pourquoi cette réponse changerait vraiment le travail>
2. <suivant, même format>
<Vide si aucun trou ne mérite d'être remonté — ne force jamais une entrée ici.>

<Si le point 7 s'applique : une ligne signalant le fichier template créé, avec ses variables.>
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

**Cette section ne s'applique pas quand la méthode est empruntée depuis `ltk-start` ou
`ltk-focus`** : ils gèrent le titre à leur propre moment, et le reproposer ici ferait
doublon. Elle s'applique quand `ltk-prompt` est la compétence directement invoquée.

Un handoff parfait dans une conversation introuvable ne sert à rien. Le titre se pose donc
**maintenant**, tant que l'area et le projet sont sous les yeux : trois semaines plus
tard, il faudrait rouvrir la conversation pour les redéduire.

**Le format et la règle `Divers` sont dans le `CLAUDE.md` de l'arbre de travail**, section
« Nomenclature des titres de conversation ». Ne le redéfinis pas ici — relis-le, applique-le.

Termine par la ligne, en disant que c'est à l'utilisateur de l'exécuter : l'outil de
renommage refuse la conversation en cours, et c'est une contrainte qu'un copier-coller
contourne, pas une impossibilité.

```
/rename AREA · Projet · AAAA.MM.JJ
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
