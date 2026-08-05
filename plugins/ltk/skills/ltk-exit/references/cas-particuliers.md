# Cas particuliers de clôture

Consulte ce fichier quand l'un de ces cas se présente — pas systématiquement. La clôture
ordinaire n'en a pas besoin, et les charger à chaque fois noierait les huit étapes.

### Une conversation qui traverse plusieurs projets

C'est fréquent sur une longue session, et c'est le cas où la clôture rate le plus souvent :
on écrit un handoff unique, dans le projet où l'on se trouve au moment de clore, et le
travail fait sur les autres devient introuvable — rangé sous un nom qui ne le désigne pas.

Fais donc l'inventaire avant d'écrire, dans cet ordre :

1. **Liste les projets touchés** — un projet est un dossier de travail. Relis la conversation
   en cherchant les chemins écrits, pas les sujets abordés : c'est le dossier qui décide.
2. **Dans chaque projet, liste les chantiers**, avec le test d'indépendance ci-dessus.
3. **Écris un handoff par chantier, dans le `handoff/` de son propre projet** — en le créant
   si besoin. Deux projets touchés, c'est au minimum deux fichiers, à deux endroits.
4. **Ne relie par un renvoi que ce qui se tient** : deux chantiers d'un même projet, oui.
   Deux projets sans rapport, non — le renvoi suggérerait une dépendance qui n'existe pas.

Annonce le classement avant d'écrire, en une ligne par fichier : *« projet X → chantier Y →
`X/handoff/AAAA-MM-JJ-y.md` »*. C'est le moment le moins cher pour corriger une erreur de
rangement ; après, le fichier est écrit au mauvais endroit et personne ne le retrouvera.

Un travail simplement **mentionné** ne fait pas un chantier. S'il n'a produit ni décision, ni
livrable, ni piège découvert, il n'a rien à transmettre — une ligne dans le handoff du
chantier principal suffit, ou rien du tout.

### Crée le rangement qui manque, ne t'en passe pas

Le réflexe paresseux est d'écrire dans le `handoff/` qui existe déjà, faute de mieux. C'est
ainsi qu'un dossier de projet accumule des chantiers qui ne le concernent pas, et que la
racine d'un arbre de travail devient un fourre-tout.

**Crée ce qui manque, sans demander :**

- **Le projet a un dossier mais pas de `handoff/`** → crée-le. C'est un `mkdir`, et c'est ce
  qui fera se déclencher `ltk-start` à la prochaine session.
- **Le projet n'a pas de dossier du tout** → c'est qu'il n'est pas encore un projet. Ne le
  fabrique pas d'autorité : dis en une ligne que ce travail mériterait son propre dossier,
  écris le handoff dans le projet le plus proche, et **note l'idée au carnet**. Créer un
  dossier de projet est une décision de rangement durable ; elle appartient à l'utilisateur.
- **Le `handoff/` existe mais n'a pas d'`INDEX.md`** → crée-le en y reportant les fichiers
  déjà présents, pas seulement le tien. Un index partiel est pire qu'aucun : il donne
  l'illusion d'être exhaustif.
- **Un handoff ancien n'a pas d'en-tête** → ajoute-lui-en un pendant que tu y es, avec au
  minimum `projet`, `chantier` et `statut`. `ltk-start` ne sait pas vérifier ce qu'il ne
  peut pas lire, et personne ne reviendra le faire plus tard.

La différence entre les deux premiers cas est la seule qui demande du jugement : **créer un
dossier dans un projet existant est du rangement ; créer un projet est une décision.**

### La longueur est un symptôme, pas une limite

Un handoff qui dépasse **environ 5 000 caractères** te dit quelque chose, et ce n'est presque
jamais « écris moins ». C'est un signal de **mauvais découpage** : tu as réuni sous un seul
chantier ce qui en fait deux.

Alors, dans cet ordre :

1. **Relis avec le test d'indépendance.** Les entrées de « reste à faire » s'adressent-elles
   toutes à la même reprise ? Si deux d'entre elles peuvent être menées par des personnes
   différentes, à des moments différents, ce sont deux chantiers. Scinde.
2. **Le chantier est-il rattaché au bon projet ?** Un handoff qui gonfle parce qu'il doit
   expliquer un contexte étranger signale souvent que le travail méritait son propre projet.
3. **Seulement alors, laisse-le grandir.** Un chantier de trois jours qui a produit huit
   décisions structurantes *mérite* 8 000 caractères.

**Ne compresse jamais pour tenir dans la cible.** Comprimer, c'est retirer les
justifications — la seule chose qui ne se reconstitue pas en relisant le code. On obtient un
document court que personne ne peut utiliser : le pire des deux mondes.

Ce qui doit sortir, quand il faut vraiment tailler, ce sont les entrées **reconstituables** :
la liste des fichiers créés, la chronologie des tentatives, le détail des modifications. Pas
les décisions, pas les pièges, pas les interdits.
