
## Principe

Pour expliquer fetch il faut d'abord aborder la notion d'API.

Dans l'exercice que tu viens de faire, ton interface interagit directement avec le serveur qui récupère et trie les cartes dans la BDD.

Mais dans le cas d'une application plus complexe, on peut vouloir séparer la partie serveur et la partie interface en deux applications distinctes, avec par exemple une application react pour le front et une avec express pour le back. Plus généralement, de nombreux sites utilisent des données d'autres applications: prenons l'exemple d'une application qui fait des comparatifs de vols. Il n'a pas accès aux BDD des compagnies aériennes. Pour trouver les informations nécessaires, elle doit passer par une API, qui est un intermédiaire permettant à des applications différentes de communiquer entre elles. 

Fetch est une méthode javascript qui permet de faire des requêtes http aux API.


## Exemple
Admettons que tu veuilles refaire l'exercice précédent mais pour un autre jeu de carte, pour lequel tu n'as pas de BDD à disposition mais qui dispose d'une API. Fetch va te permettre de récupérer les informations sur les cartes du jeu.

Dans cet exemple, on va récupérer les informations sur une carte issue d'un jeu qui s'appelle Magic, en utilisant une API fournie par un site nommé scryfall. Voici ce que tu peux faire :
- Dans l'application de l'exercice précédent, installe le package node-fetch avec npm install, comme pour les sessions.
- Crée un fichier fetch.js à la racine et copie le code ci-dessous:

```
const fetch = (...args) =>
	import('node-fetch').then(({default: fetch}) => fetch(...args));

async function fetchTest(){
  const url = "https://api.scryfall.com/cards/named?fuzzy=aust+com"
  
  const requestOptions = {
    method: 'GET',
    redirect: 'follow'
  };
  
  await fetch(url, requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
}

fetchTest();
```
- Avec le terminal exécute la commande "node fetch.js": tu vas récupérer un ensemble très complet d'informations sur une carte nommée "Austere command". Et tu peux réutiliser le code ci-dessus dans ton application, en l'adaptant à tes besoins.


## Pour aller plus loin
Fetch est un outil très complet, tu peux faire énormément de choses avec. Voici quelques liens qui te permettront de comprendre de façon plus approfondie comment fonctionne le code ci-dessus et comment tu peux le faire évoluer pour écrire d'autres requêtes:
- https://developer.mozilla.org/en-US/docs/Web/API/fetch
- Documentation de l'api utilisée: https://scryfall.com/docs/api/cards/named
- Documentation de fetch-node: https://www.npmjs.com/package/node-fetch
- Une application très utile pour tester des requêtes API: postman (tu peux refaire la requête que je viens de te montrer, il te suffira de reprendre l'url)
