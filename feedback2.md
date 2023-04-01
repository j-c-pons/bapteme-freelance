Pré-requis:
-Erreur 404, outils de développeur du navigateur
concept de balise/ attribut en html

## Étape 1 : Détail d'une carte

Détail : la consigne c'est de créer méthode `getCard` mais tu as créé `getOneCard`.
Doublon dans l'import de database (const client et const database)
Si aucune carte n'est trouvée tu retourne null > à optimiser avec de la gestion d'erreur ou au moins un console.log

## Étape 2 : Recherche
ràs


## Étape 3 : Construire un deck

Dans la view > Il y a un card.price qui n'a rien à faire là
Pas de lien pour supprimer les cartes du deck


## Bonus: finir les recherches

Les formulaires sont correctements codés sauf sur un point essentiel: dans tes <form>, l'attribut "action" ne renvoie à aucune route existante. Etudie celle qu'a créé le stagiaire:

<h3>Par élément</h3>
<form action="/searchResults" method="get">

Toi tu as fais :

<h3>Par valeur</h3>
<form action="/search/values" method="get">

Et /search/values n'existe pas dans router.js. D'où l'erreur 404 quand on lance une recherche.

Les recherches que tu as faites ne renvoient vers aucune view. Il suffisait simplement d'utiliser l'existante

(Je présume qu'il n'a pas pu aller plus loin)