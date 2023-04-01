

## Étape 1 : Détail d'une carte
On ne peut pas accéder au détail d'une carte en cliquant dessus, seul le lien dans le nom le permet. Dans la view cardList.ejs, on trouve 2 fois la balise </a> (ligne 11 et 16) Il faut supprimer la première. Inutile également d'afficher card.name puisqu'il apparaît sur l'image de la carte. 

Plusieurs problèmes dans cardDetails.ejs:
-ligne 8, tu utilises une boucle comme si tu allais afficher plusieurs cartes, alors qu'il n'y en a qu'une.:         
```<% for (const singleCard of card) { %>```

-Le nom de l'objet renvoyé par le contrôleur qui contient les infos cherchées est oneCard, il faut remplacer ce nom dans l'ensemble de la view.
-La balise img l11 
```<img src="/visuals/<%= oneCard.visual_name.toLowerCase() %>.jpg" alt="<%= oneCard.name %> illustration">)```

contient plusieurs erreurs de syntaxe: la méthode toLowerCase() et l'extension .jpg n'ont rien à faire ici.

- Certaines informations affichées ne servent à rien (visual_name) et il n'y a aucune indication sur ce à quoi elle correspondent (par exemple, quelle donnée correspond au niveau?)


## Étape 2 : Recherche
Il y a plusieurs problèmes dans searchController.js:
-La recherche ne fonctionne pas car tu n'as pas importé dataMapper dans searchController.js, alors que tu l'appelle l12:
```const cards = await dataMapper.getElements();```

- Ensuite, la méthode searchElement() ne fonctionne pas car tu y appelles une autre méthode qui n'existe pas (dataMapper.cardElement(), au lieu de dataMapper.getCardByElement()).

- Dans la méthode searchElement(), il y a une erreur de syntaxe dans le chemin de callback:
```response.render('main/element/', {element});```
il faut supprimer le "/" après element car il empêche les résultats de s'afficher
- Toujours dans searchElement, ce n'est pas le résultat de la query qui est renvoyé mais l'élément rentré en paramètre de la recherche.

Dans dataMapper, la méthode getCardByElement() a également des problèmes:
- Elle ne prend aucun paramètre alors qu'il y en a un lorsqu'elle est appelée par le contrôleur. 
- La requête ne gère pas les cas où il n'y a aucun élément en retour.

Concernant la view element.js, je présume que tu n'as pas eu le temps de la faire.

## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Le code secret devrait être une variable d'environnement, cf. le lien vers la documentation fournie dans les consignes:
>A best practice may include:
>
>The use of environment variables to store the secret, ensuring the secret itself does not exist in your repository.
>

### 3.2 Ajouter une carte au deck
Le lien censé ajouter la carte au deck a plusieurs problèmes:        
```<a class="link--addCard" title="Ajouter au deck" href="/card/<%= card.id %>"><%= card.name %>[ + ]</a>```
- Inutile rafficher le nom de la carte, il est déjà indiqué
- Le lien en lui-même renvoie juste à la fiche détaillée de la carte, il n'ajoute pas la carte au deck

### 3.3 Une page pour visualiser le deck !
La route et la view du deck n'ont pas été implémentées. Je t'invite à revoir ces concepts.

### 3.4 Supprimer une carte du deck
Idem

