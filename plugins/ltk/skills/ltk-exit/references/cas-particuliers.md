# Cas particuliers de clôture

Trois situations que l'Étape 2 signale mais ne détaille pas. Lis la section concernée
quand elle se présente — pas avant, elle alourdirait inutilement le corps de la compétence.

## Une conversation qui traverse plusieurs areas

Rare, mais ça arrive : un dépannage réseau touche à la fois l'area `ltk` et l'area
`finance` parce que le montage NAS sert aux deux. Le test de l'Étape 2 (« un projet, un
handoff ») s'applique **par area**, pas globalement :

1. Sépare d'abord par area, pas par projet — chaque area aura son propre `handoff/`.
2. À l'intérieur de chaque area, applique le découpage habituel : un projet, un handoff.
3. Si le travail sur l'une des areas dépend de celui sur l'autre (le montage NAS a été
   corrigé *pour* débloquer le travail Finance), dis-le explicitement dans les deux
   handoffs — chacun doit pouvoir se lire seul, mais ni l'un ni l'autre ne doit cacher
   qu'il existe un lien.

N'écris jamais un handoff unique « à cheval » sur deux areas : il finira rangé dans l'une
des deux, et restera invisible depuis l'autre — exactement le problème que le découpage en
areas sert à éviter.

## Une area dont le `handoff/` ou l'`INDEX.md` manque

Se produit la première fois qu'une area passe par une clôture, ou quand quelqu'un a
supprimé le dossier par erreur. Ne traite pas ça comme une anomalie bloquante — c'est
l'état normal d'une area neuve.

- Crée `handoff/` s'il manque, silencieusement.
- Crée `handoff/INDEX.md` s'il manque, avec le gabarit de l'Étape 5 et une seule ligne :
  celle du projet que tu clôtures maintenant.
- Ne cherche pas à reconstituer l'historique d'avant — un `INDEX.md` neuf commence à zéro,
  et c'est très bien ainsi. Ce n'est pas une perte de données : les handoffs individuels,
  s'ils existent déjà sur le disque sans être indexés, restent lisibles directement. Signale
  simplement que tu as trouvé des handoffs non indexés, sans les reconstruire un à un dans
  l'index — laisse ce travail à l'utilisateur s'il le juge utile.

## Un handoff qui gonfle au-delà de ~5 000 caractères

Le seuil n'est pas arbitraire au sens strict — au-delà, un handoff cesse d'être lu d'un
coup d'œil, ce qui est toute sa raison d'être. Deux causes distinctes, deux traitements :

**Cause 1 — le projet est en réalité plusieurs projets.** C'est le cas le plus fréquent : le
volume vient d'avoir mélangé un « reste à faire » qui ne concerne plus le même travail.
Reviens à l'Étape 2 et découpe — la taille excessive est le symptôme, pas le problème.

**Cause 2 — le projet est réellement long et complexe, et le mérite.** Alors ne comprime
pas en réduisant les phrases : ce serait sacrifier justement ce qui rend un handoff utile
(le pourquoi, les pièges, les alternatives écartées). À la place :

- Coupe ce qui est reconstituable ailleurs (voir « Ce qui mérite d'être écrit » dans le
  corps principal) — c'est souvent là que le gonflement s'est glissé.
- Si le projet a plusieurs phases nettement séparées dans le temps, envisage un handoff par
  phase plutôt qu'un seul document cumulatif — chacun reste sous le seuil, et
  `handoff/INDEX.md` les relie par leur ordre chronologique.
- Ne scinde jamais une section en deux fichiers sans le dire dans les deux : un handoff qui
  renvoie silencieusement à un autre pour être complet se fera oublier à la première lecture
  pressée.
