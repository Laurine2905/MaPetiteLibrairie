<script setup>
function rechercherLivre() {
  //url de l'api pour récupérer les livres
  const url =
    "https://webmmi.iut-tlse3.fr/~pecatte/librairies/public/31/livres?motcle=";

  const fetchOptions = { method: "GET" };
  // récupérer la valeur saisie dans la zone de texte
  let nom = document.getElementById("nom").value;
  console.log(nom);
  // --- la valeur saisie doit être ajoutée à la fin de l'URL
  fetch(url + nom, fetchOptions)
    .then((response) => {
      console.log("test1");
      return response.json();
    })
    .then((dataJSON) => {
      console.log("test2");
      console.log(dataJSON);
      let liste_livres = dataJSON.results; // les personnes sont le tableau "results"
      let resHTML = "";
      for (let l of liste_livres) {
        resHTML = resHTML + "<option>" + l.titre + "</option>";
      }
      document.getElementById("liste_livres").innerHTML = resHTML;
    })
    .catch((error) => console.log(error));
}
</script>


<template>
  <input type="text" id="nom" v-model="search" placeholder="nom du livre" />

  <button @click="rechercherLivre()">Rechercher</button>

  <ul id="liste_livres"></ul>
  <p>recherche</p>
</template>


