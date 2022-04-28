<template>
  <div class="hello">
    <header></header>
    <h1>{{ titulo }}</h1>
    <div class="card">
      <ul v-for="pokemon in pokemons" :key="pokemon.name">
        <li>
          <p>
            {{ pokemon.name }}
          </p>
          <span>{{ getImg(pokemon) }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Card",
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
    getImg(pokemon) {
      return pokemon.url.split("/")[6];
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
      display: flex;
      flex-direction: column;
      justify-content: center;

      p {
        color: aliceblue;
        font-size: 28px;
      }

      // span {
      //   // display: inline-block;
      //   // padding-top: 20px;
      //   // color: aliceblue;
      // }
    }
  }
}
</style>
