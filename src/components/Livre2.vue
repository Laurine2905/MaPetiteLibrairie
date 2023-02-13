<script setup>
const listItem = reactive([]);
// Afficher le contenu de la librairie
// ======> la fonction qui récupère les livres et les affiche
function getListeLivre() {
  //url de l'api pour récupérer les livres
  const url =
    "https://webmmi.iut-tlse3.fr/~pecatte/librairies/public/31/livres";

  let fetchOptions = { method: "GET" }; // On utilise GET pour récupéré les infos ici le titre de chaque livre

  fetch(url, fetchOptions)
    .then((response) => {
      console.log("test");
      // -- réponse au sens du protocole HTTP
      return response.json(); // -- extraire les données au format JSON
    })
    .then((dataJSON) => {
      // dataJSON = les données renvoyées au format JSON
      console.log("test2");
      let livres = dataJSON;
      let texteHTML = ""; // variable pour contenir le html généré
      for (let l of livres) {
        // boucle sur le tableau des livres
        texteHTML = texteHTML + "<li>" + l.titre + "</li>";
      }
      // insérer le HTML dans la liste <ul id="liste"></ul> du fichier index.html
      document.getElementById("liste").innerHTML = texteHTML;
    })
    // gestion des erreurs
    .catch((error) => console.log(error));
}

// a modifier une fois qu'on aura les boutons avec un add envent listener
getListeLivre();
</script>

<template>
  <ul id="liste"></ul>
</template>

<style>
</style>