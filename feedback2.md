Pré-requis:
-Erreur 404, outils de développeur du navigateur
concept de balise/ attribut en html

## Étape 1 : Détail d'une carte
La donnée qui correspond au niveau est affichée mais on ne sait pas de quoi il s'agit. Il aurait fallu l'indiquer.

Détail : la consigne c'est de créer méthode `getCard` mais tu as créé `getOneCard`.
Dans dataMapper.js, il y a un doublon d'import de database (const client et const database, l1)
Si aucune carte n'est trouvée tu retourne null > à optimiser avec de la gestion d'erreur ou au moins un console.log

## Étape 2 : Recherche
ràs


## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Le code secret devrait être une variable d'environnement, cf. le lien vers la documentation fournie dans les consignes:
"quote
A best practice may include:

The use of environment variables to store the secret, ensuring the secret itself does not exist in your repository.
"quote
### 3.2 Ajouter une carte au deck
ràs 

### 3.3 Une page pour visualiser le deck !
Dans la view > Il y a un card.price qui n'a rien à faire là

### 3.4 Supprimer une carte du deck
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