<script>
import axios from "axios";

export default {
  data: function () {
    return {
      newPokemonParams: {},
      errors: [],
      party: {},
    };
  },
  methods: {
    submit: function () {
      axios
        .post("/pokemon/", this.newPokemonParams)
        .then((response) => {
          console.log(response.data);
          this.pokemon = response.data.this.$router.push("/login");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="Party_Pokemon">
    <form v-on:submit.prevent="submit()">
      <h1>Add Pokemon To Your Party</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Pokemon Name:</label>
        <input type="text" v-model="newPokemonParams.pokemon_name" />
      </div>
      <div>
        <label>Trainer ID:</label>
        <input type="text" v-model="newPokemonParams.trainer_id" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
  <!-- <h2>{{ party }}</h2> -->
  <img src="../assets/PokeballSuccess.webp" height="500" />
</template>
