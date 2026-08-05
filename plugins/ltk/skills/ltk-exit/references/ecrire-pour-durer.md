# Écrire un handoff qui vieillit bien

Consulte ce fichier avant le premier `push` d'un handoff vers un dépôt, et chaque fois que
tu hésites sur ce qu'il est prudent d'écrire.

### Écris la règle, pas les chemins

**Un handoff versionné a un historique permanent.** Ce qu'on y écrit ne se retire pas en le
supprimant : l'ancienne version reste lisible dans chaque commit qui l'a portée. Et un dépôt
d'équipe peut devenir public bien après qu'on a cessé d'y penser — auquel cas tout
l'historique le devient d'un coup, pas seulement l'état courant.

Avant d'écrire, demande-toi donc : *cette ligne serait-elle gênante si le dépôt devenait
public demain ?* Si oui, écris la **règle** et laisse le détail dans le `CLAUDE.md`, qui lui
ne quitte pas le poste :

| N'écris pas | Écris |
|---|---|
| `\\SERVEUR-NAS\home\Partage équipe\` | « le partage d'équipe est en lecture seule » |
| L'adresse nominative d'un collègue | son rôle |
| Une lettre de lecteur mappée sur une ressource interne | ce que la ressource contient |
| Un identifiant, une clé, un jeton — **jamais**, sous aucune forme | — |

On ne perd rien : la valeur d'un interdit tient à ce qu'il protège, pas à l'énumération des
routes qui y mènent. Un lecteur qui a besoin des chemins exacts les a déjà sur son poste.

Cette précaution ne coûte que si on l'applique trop tard : effacer une ligne d'un historique
public suppose de le réécrire et de forcer la branche, ce qui casse tous les clones existants.
