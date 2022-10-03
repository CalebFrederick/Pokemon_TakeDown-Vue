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
      double_damage_from_1: [],
      half_damage_from_1: [],
      none_damage_from_1: [],
      double_damage_from_2: [],
      half_damage_from_2: [],
      none_damage_from_2: [],
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
          this.double_damage_from_1 = response.data.double_from1;
          this.half_damage_from_1 = response.data.half_from1;
          this.none_damage_from_1 = response.data.none_from1;
          this.double_damage_from_2 = response.data.double_from2;
          this.half_damage_from_2 = response.data.half_from2;
          this.none_damage_from_2 = response.data.none_from2;
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
    <!-- <h2>{{ types }}</h2> -->
    <h1>{{ type1 }}</h1>
    <h1>{{ type2 }}</h1>
    <h2>Super Effective {{ double_damage_from_1 }}</h2>
    <h2>Not Very Effective {{ half_damage_from_1 }}</h2>
    <h2>Not Effective {{ none_damage_from_1 }}</h2>
    <h2>Super Effective {{ double_damage_from_2 }}</h2>
    <h2>Not Very Effective {{ half_damage_from_2 }}</h2>
    <h2>Not Effective {{ none_damage_from_2 }}</h2>
    <!-- <img :src="sprite" width="300" height="300" /> -->
    <img src="../assets/Type_Chart.png" height="450" />
  </div>
</template>

<style></style>
