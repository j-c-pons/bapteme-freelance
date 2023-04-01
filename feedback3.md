

## Étape 1 : Détail d'une carte
Il y a un problème de lien: on ne peut pas accéder au détail en cliquant sur la carte, seul le lien dans le nom le permets. Dans la view cardList.ejs, on trouve 2 fois la balise </a> (ligne 11 et 16) Il faut supprimer la première. Inutile également de garder card.name puisqu'il apparaît sur l'image de la carte. Voilà à quoi devrait ressembler la ligne 11:

  <a href="/card/<%= card.id %>">

Plusieurs problèmes dans cardDetails.ejs:

-ligne 8:         <% for (const singleCard of card) { %>
Tu conserves la boucle comme si tu allais affaicher plusieurs cartes, alors qu'il n'y en a qu'une.

-Le nom de l'objet renvoyé par le contrôleur qui contient les infos cherchées est oneCard, il faut remplacer ce nom dans l'ensemble de la view.
La balise img l11 (<img src="/visuals/<%= oneCard.visual_name.toLowerCase() %>.jpg" alt="<%= oneCard.name %> illustration">)
contient plusieurs erreurs de syntaxe: la méthode toLowerCase() n'a rien à fair eici et l'extension .jpg non plus.
Voilà ce qu'elle devrait donner:                    <img src="/visuals/<%= oneCard.visual_name%>" alt="<%= oneCard.name %> illustration">
- Certaines informations affichée ne servent à rien (visual_name) et il n'y a aucune indication sur ce à quoi elle correspondent (quelle donnée correspond au niveau?)


## Étape 2 : Recherche
Il y a plusieurs problèmes dans dans searchController.js:
-La recherche ne fonctionne pas car tu n'as pas importé dataMapper dans searchController.js, alors que tu l'appelle l12:
const dataMapper = require("../dataMapper");

- Ensuite, dans la méthode searchElement() ne fonctionne pas car tu y appelles une autre méthode qui n'existe pas (dataMapper.cardElement()). Ce que tu cherches c'est dataMapper.getCardByElement().

- Dans la méthode searchElement(), il y a une erreur de syntaxe dans le chemin de callback:

"quote
response.render('main/element/', {element});
"quote
il faut supprimer le "/" après element car il empêche les résultats de s'afficher
De plus, ce n'est pas le résultat de la query qui est renvoyé mais l'élément rentré en paramètre d ela recherche. Il faut remplacer "element" ci-dessus par "result".

La méthode getCardByElement() a également des problèmes:
- Elle ne prend aucun paramètre alors qu'il y en a un lorsqu'elle est appelée dans le contrôleur. 
- La query ne gère pas les cas où il n'y a aucun élément

Concernant la view element.js, je présume qu'il n'a pas eu le temps de la faire.

## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Le code secret devrait être une variable d'environnement, cf. le lien vers la documentation fournie dans les consignes:
"quote
A best practice may include:

The use of environment variables to store the secret, ensuring the secret itself does not exist in your repository.
"quote

### 3.2 Ajouter une carte au deck
Le lien sensé ajouter la carte au deck a plusieurs problèmes:        
<a class="link--addCard" title="Ajouter au deck" href="/card/<%= card.id %>"><%= card.name %>[ + ]</a>
Inutile de remettre le nom de la carte, il est déjà indiqué
Le lien en lui-même renvoie juste à la fiche détaillée de la carte

### 3.3 Une page pour visualiser le deck !
La route et la view du deck n'ont pas été implémentées.

### 3.4 Supprimer une carte du deck
Idem

## Bonus: finir les recherches

