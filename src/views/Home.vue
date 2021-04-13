

<template>
  <div class="home">
    <h1>{{ brewery }}</h1>
    <p>Enter an address: <input type="text" v-model="searchAddress"></p>
    <button v-on:click="findBreweries()">Find brewery</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      searchAddress: "",
      brewery: {}
    };
  },
  created: function() {},
  methods: {
    findBreweries: function() {
      axios.get("/api/breweries?search=" + this.searchAddress).then(response => {
        console.log(response.data)
        this.brewery = response.data;
      });
    }
  }
};
</script>

