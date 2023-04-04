
Dans l'ensemble le concept est compris, la réalisation est correcte mais il y a un problème de fond: tu dois passer davantage de temps à réfléchir sur le contenu de tes tables.

## Concernant les tables:
- Pour la table ADDRESS: 
* Rajoute une donnée "country"

- Pour la table USER: 
* Rajoute des données "first_name"/ "last_name". 
* Une date de naissance pourrait peut-être s'avérer utile également.
* Il te manque une donnée pour savoir quels sont les produits likés.

- Pour la table PRODUCT: 
* Il te manque le price, ça pourrait servir. 

- Pour la table ORDER:
* Comment sais-tu quel(s) produit(s) sont dans une commande?
* Il serait utile d'avoir des informations concernant les dates (de création, d'envoi). Le status peut-être utile mais pas indispensable, et les dates sont plus précises.
* Je ne suis pas sur de comprendre la donnée "total_amount". Est-ce que c'est le prix total de la commande ou le nombre de produits? Comme il y a aussi un amount et pas de prix dans la table PRODUCT, c'est un peu confus.


Plus généralement, il y a un problème d'interaction entre tes tables: par exemple, comment fais-tu le lien entre une adresse et un user? Pour y parvenir, tu as besoin d'utiliser des clés étrangères (https://www.data-bird.co/sql/cle-etrangere). Dans le cas précédent, tu devrais rajouter une donnée id_user dans ta table ADDRESS. A toi de corriger pour les autres tables.



## Concernant les cardinalités:
- Les USERS ne devraient pas obligatoirement avoir à liker des PRODUCTS, et inversement. Il faudrait donc corriger ta borne minimale de 1 à 0.
- A contrario, et comme tu l'expliques toi-même en commentaire, les USERS devraient pouvoir liker plusieurs PRODUCTS. Ta borne maximale devrait donc être égale à n.



Il existe un grand nombre d'outils qui permettent de réaliser des MCD, je t'invite notamment à regarder draw.io et lucidchart. Mais celui que tu as utilisé m'a l'air bien.