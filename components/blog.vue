<template>
  <div id="blog">
    <h1>Los personajes de SNK</h1>

    <div 
    v-for="currency in info" 
    :key="currency.id"
    >
      <img v-bind:src="currency.img" v-bind:alt="currency.name" />
      <p>{{ currency.name }}</p>
    </div>
  </div>
</template>

<script>
import datos from "../snk.json";

export default {
  name: "blog",
  computed: {
    info() {
      return datos.map((currency) => {
        return currency;
      });
    },
  },
};
</script>

<style>
</style>