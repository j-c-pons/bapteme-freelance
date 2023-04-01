

## Étape 1 : Détail d'une carte

Dans la view card-item, il n'était pas nécessaire d'afficher les values north/east/south/west puisqu'elles apparaissent déjà sur la carte (même si en terme de code il n'y a pas de problème).


## Étape 2 : Recherche
Ligne 22 dans searchController: 
```title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement)```
Il faut enlever le 2nd "+" sinon ça renvoie NaN comme titre du résultat de la recherche.

Dans dataMapper.js, il y a une méthode searchByElementNull qui ne sert à rien.
Pense à supprimer le code en commentaire dans searchController.

## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Une variable d'environnement SESSION_SECRET est appelée dans index.js mais elle n'est pas définie dans .env, ce qui empêche de lancer node.js.

### 3.2 Ajouter une carte au deck
Il aurait été intéressant de conserver le lien pour rajouter la carte dans la page qui affiche les détails.

### 3.3 Une page pour visualiser le deck !
ràs

### 3.4 Supprimer une carte du deck
ràs

## Bonus: finir les recherches
ràs

## Commentaire additionnel

Pour aller plus loin, je t'invite à remplacer, dans package.json, le script "start" par "dev". Le premier est sensé être utilisé uniquement dans un environnement de production, tandis que l'autre est celui approprié pour les tests. Même si c'est sans conséquence pour l'exercice, c'est une mauvaise pratique qu'il vaut mieux éviter.