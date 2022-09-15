<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Takedown!",
      types: [],
      input: "",
      sprite: "",
    };
  },
  created: function () {},
  methods: {
    takeDown: function () {
      axios
        .get(`/takedown/${this.input}`)
        .then((response) => {
          console.log(response.data);
          this.types = response.data.types;
          this.sprite = response.data.sprite;
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="home">
    <input type="text" v-model="input" placeholder="Pokemon Name" />
    <button v-on:click="takeDown()">Takedown Pokemon</button>
    <img :src="sprite" />
    <h2>{{ types }}</h2>
    <!-- <img :src="sprite" width="300" height="300" /> -->
    <img src="../assets/Type_Chart.png" height="450" />
  </div>
</template>

<style></style>
