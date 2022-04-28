<template>
  <div class="hello">
    <header></header>
    <h1>{{ titulo }}</h1>
    <div class="card">
      <ul v-for="pokemon in pokemons" :key="pokemon.name">
        <li buscarImg>
          <p>{{ pokemon.name }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      titulo: "PokeDex",
      pokemons: [],
    };
  },
  mounted() {
    axios
      .get("https://pokeapi.co/api/v2/pokemon?limit=151")
      .then((response) => {
        this.pokemons = response.data.results;
      });
  },
  methods: {
    buscarImg(pokemon) {
      return pokemon.url.split("/");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card {
  ul {
    display: inline-block;
    list-style: none;

    li {
      width: 400px;
      height: 220px;
      background: rgb(17, 17, 101);
      margin-left: 20px;
      margin-bottom: 20px;
      text-align: center;
      padding-top: 15px;

      p {
        font-size: 28px;
        color: aliceblue;
      }
    }
  }
}
</style>
