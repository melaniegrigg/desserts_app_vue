<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1> All Desserts </h1>
    <div v-for="dessert in desserts">
      <h2>{{dessert.name}}</h2>
      <img v-bind:src="dessert.image_url" v-bind:alt="dessert.name" />
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Lets Make Dessert!",
      desserts: [],
    };
  },
  created: function () {
    this.indexDesserts();
  },
  methods: {
    indexDesserts: function () {
      axios.get("/api/desserts").then((response) => {
        console.log("desserts index", response);
        this.desserts = response.data;
      });
    },
  },
};
</script>