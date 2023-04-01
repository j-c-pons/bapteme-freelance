

## Étape 1 : Détail d'une carte
- Je t'invite à revoir le concept de route parameters: https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes#route_parameters
https://www.youtube.com/watch?v=QO9rzAPPCWk
La majorité des remarques qui suivent découlent du fait que tu n'as pas encore bien saisi ce dernier.
- La route "/card" doit intégrer l'id de la carte choisie en paramètre. 
- Sur la page d'accueil, la balise html qui permet de cliquer sur la carte dont on veut le détail a un attribut href qui vaut "#":      
```<a class="link--addCard" title="Ajouter au deck" href="#">[ + ]</a>```
Il faut le remplacer par la route /card mentionnée juste avant (une fois celle-ci corrigée).
- Dans la méthode mainController.cardPage(), tu ne récupères pas l'id en paramètre et tu ne l'envoies pas au dataMapper. Or, sans lui tu ne pourras pas retrouver les informations sur la carte sélectionnée.
- Dans dataMapper.getCard(), il manque un paramètre "[id]" à la requête et il y a également plusieurs fautes de syntaxe dans cette dernière, je t'invite à revoir la manière dont ces dernières doivent être codées.
- Toujours dans dataMapper.getCard(), l18: une constante "resultQuery" qui n'existe pas est appelée:
```if (resultQuery.rowCount === 1)```
J'imagine que tu voulais utiliser la constante "queryResult"
- Pour la view card.ejs, censée afficher les résultats, tu as fait un copier coller de cardList.ejs alors qu'il aurait fallu afficher d'autres éléments de la carte choisie. Et la boucle n'est plus nécessaire vu qu'il n'y a qu'une seule carte à afficher.


## Étape 2 : Recherche
Pas de route ni de view pour afficher les résultats.

## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Le paquet n'a pas été installé. Je te conseille de revoir la documentation fournie dans l'énoncé.

### 3.2 Ajouter une carte au deck
Même problème que durant l'étape 1 en ce qui concerne le lien

### 3.3 Une page pour visualiser le deck !
Pas de route ni de view.

### 3.4 Supprimer une carte du deck
/
