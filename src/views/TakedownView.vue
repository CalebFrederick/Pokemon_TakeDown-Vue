<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Takedown!",
      types: [],
      input: "",
      sprite: "",
      type1: "",
      type2: "",
      damage_from_1: [],
      damage_from_2: "",
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
          this.type1 = response.data.type1;
          this.type2 = response.data.type2;
          this.damage_from_1 = response.data.from;
          this.damage_from_2 = response.data.damage_from_2;
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
    <h3>{{ type1 }}</h3>
    <h3>{{ type2 }}</h3>
    <h3>{{ damage_from_1 }}</h3>
    <!-- <img :src="sprite" width="300" height="300" /> -->
    <img src="../assets/Type_Chart.png" height="450" />
  </div>
</template>

<style></style>
