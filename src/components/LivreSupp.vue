<script setup>
// A CODER

// -- handle pour supprimer une chose à prtir de l'index dans la liste
function handlerDelete(id) {
  console.log(id);
  const fetchOptions = {
    method: "DELETE",
  };
  fetch(url + "/" + id, fetchOptions)
    .then((response) => {
      return response.json();
    })
    .then((dataJSON) => {
      console.log(dataJSON);
      getTodos();
    })
    .catch((error) => console.log(error));
}
</script>

<template>
  <p>livre modification : ajouter un livre</p>
</template>

<style>
</style>