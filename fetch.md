fetch ///card/:id

async function getText(file) {
  let x = await fetch(file);
  let y = await x.text();
  myDisplay(y);
}


Pour expliquer fetch il faut d'abord aborder la notion d'API.

Dans l'exercice que tu viens de faire, ton interface interagit directement avec le serveur qui récupère et trie les cartes dans la BDD.

Mais de nombreux sites fonctionnent différement: prenons l'exemple d'une application qui fait des comparatifs de vols. Il n'a pas accès aux BDD des compagnies aériennes pour aller chercher des informations. Pour les trouver, il foit passer par un intermédiaire qui s'appelle une API. L'API est une interface qui va permettre au comparateur de récupèrer les données sur les vols quand tu fais ta recherche.

Fetch est une méthode javascript qui permet de faire des requêtes aux API.

Dans l'exemple précédent, admettons que ton site n'a pas accès aux BDD mais qu'il existe une API qui te permet de les récupérer. Tu vas devoir utiliser fetch pour le faire.

Voici un exemple, fondé sur l'exercice précédent: Mettons qu'on te demande d'accéder aux données des cartes pour s'en servir pour un autre site (donc sans utiliser ). Voici ce que tu pourrais faire:

dans router.js, ajoute une nouvelle route:
router.get('/cardApi/:id', cardController.fetchOneCard);

dans cardController, ajouter une nouvelle méthode:
  async fetchOneCard(req, res){
    const card = await dataMapper.getOneCard(req.params.id);
    res.status(200).json(JSON. stringify(card))
  },


Ensuite, crée une nouvelle application node.js et crée un fichier fetch.js (tu auras besoin d'installer le paquet node-fetch) avec le contenu suivant:

const fetch = (...args) =>
	import('node-fetch').then(({default: fetch}) => fetch(...args));

const fetchController= {

 fetchTest:  async(req, res) => {

  const url = "http://localhost:1234/cardApi/"+req.params.id.toString();
  console.log("urle", url)
  const options = {
    method: 'get',
    headers: {'Content-Type': 'application/json'}
  };
  const test = await fetch(url, options)
  let responseJson = await test.json()

  console.log("respsdsddsdsds", responseJson)
}
}
fetchTest(4);

module.exports = fetchController;

Si tu lance les deux applications en même temps et que tu 