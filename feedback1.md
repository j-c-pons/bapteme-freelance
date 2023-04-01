

## Étape 1 : Détail d'une carte

Il n'était pas nécessaire d'afficher les values north/east/south/west puisqu'elles apparaissent déjà sur la carte (même si en terme de code il n'y a pas de problème).

Il n'y a pas de gestion d'erreur côté serveur si l'ID requis n'existe pas > seule une erreur 404 est renvoyée côté front.

## Étape 2 : Recherche
Ligne 22 dans searchController: 

"quote
title: 'Résultat de la recherche : ' + (searchedElement === 'null' ? ' sans élément' : + searchedElement),
"quote
Il faut enlever le 2nd "+" sinon ça renvoie NaN.

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
Il n'était pas nécessaire de faire une route et une mathode pour chaque type de recherche, le code aurait été plus simple en définissant une seule méthode/route. Là le searchController est très confus:
- Trop de code commenté
- Trop de redondances (searchedResults par exemple, qui est déclaré plus ou moins)
