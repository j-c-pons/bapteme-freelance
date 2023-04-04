
- Il est peu pertinent de séparer les données user et address : qu'est-ce que ça apporte?
- Concernant les cardinalités:
* Les USERS ne devraient pas obligatoirement avoir à liker des PRODUCTS, et inversement. Il faudrait donc corriger ta borne minimale de 1 à 0.
* A contrario, et comme tu l'expliques toi-même en commentaire, les USERS devraient pouvoir liker plusieurs PRODUCTS. Ta borne maximale devrait donc être égale à n.

Il existe un grand nombre d'outils qui permettent de réaliser des MCD, je t'invite notamment à regarder draw.io et lucidchart. Mais celui que tu as utilisé m'a l'air bien.