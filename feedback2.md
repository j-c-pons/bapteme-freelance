
## Étape 1 : Détail d'une carte
La donnée qui correspond au niveau est affichée mais on ne sait pas de quoi il s'agit. Il aurait fallu l'indiquer (idem pour l'élément).

Un détail : la consigne c'est de créer méthode getCard() mais tu as créé getOneCard().

Dans dataMapper.js, il y a un doublon d'import de database (const client et const database, l1)

## Étape 2 : Recherche
Au niveau de la view searchResult : il aurait été intéressant de rajouter d'autres éléments en plus du nom de la carte (image, niveau, etc)

Pense à rajouter de la gestion d'erreur avec la commande try/catch comme tu l'as fait ensuite.


## Étape 3 : Construire un deck
### 3.1: Activer les sessions
Le code secret devrait être une variable d'environnement, cf. le lien vers la documentation fournie dans les consignes:

>A best practice may include:
>
>The use of environment variables to store the secret, ensuring the secret itself does not exist in your repository.
>

### 3.2 Ajouter une carte au deck
Il est possible d'ajouter 6 cartes ou plus dans le deck, à corriger.

### 3.3 Une page pour visualiser le deck !
Dans la view deck > Il y a un card.price qui n'a rien à faire là. Et une petite coquille l38 avec un "$" qui s'est glissé dans le code. 

Enfin, l'architecture de cette vue est un peu étrange, même si ça n'est pas une erreur de code en soi, le choix de la balise table et sa structure ne sont pas terrible, il aurait été intéressant de reproduire la structure de la vue qui affiche toutes les cartes.

### 3.4 Supprimer une carte du deck
Pas de lien pour supprimer les cartes du deck

## Bonus: finir les recherches

Je présume que tu n'as pas eu le temps de coder les routes auxquelles renvoient les formulaires de recherche.


