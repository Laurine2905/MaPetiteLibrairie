<script setup>
import { defineProps } from "vue";
// -- il faut déclarer les 2 params (props) du composant
defineProps(["chose", "indexc"]);
</script>

<template>
  <li>
    {{ chose.pourAfficher() }}
  </li>
</template>

<style>
</style>