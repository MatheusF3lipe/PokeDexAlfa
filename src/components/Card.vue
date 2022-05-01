<template>
  <div class="container">
    <div class="card">
      <ul v-for="pokemon in pokemons" :key="pokemon.name">
        <li @click="handleInfo(getImg(pokemon))">
          <p>
            {{ caseUp(pokemon) }}
          </p>
          <img
            :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${getImg(
              pokemon
            )}.png`"
            alt="pokemon.name"
          />
          <span>{{ getImg(pokemon) }}</span>
        </li>
      </ul>
    </div>
    <div v-if="pokeInfo">
      {{ pokeInfo }}
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
      pokeInfo: null,
    };
  },
  mounted() {
    axios
      .get("https://pokeapi-215911.firebaseapp.com/api/v2/pokemon?limit=151")
      .then((response) => {
        this.pokemons = response.data.results;
      });
  },
  methods: {
    getImg(pokemon) {
      return pokemon.url.split("/")[6];
    },
    caseUp(pokemon) {
      return pokemon.name
        .charAt(0)
        .toUpperCase()
        .concat(pokemon.name.substring(1));
    },
    handleInfo(id) {
      axios
        .get(`https://pokeapi-215911.firebaseapp.com/api/v2/pokemon/${id}`)
        .then((response) => {
          this.pokeInfo = response.data.abilities;
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=VT323&display=swap");
.container {
  .card {
    ul {
      display: inline-block;
      list-style: none;
      font-family: "vt323";

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
        justify-content: space-around;
        align-items: center;
        border: 2px solid rgb(1, 1, 34);
        border-radius: 15px;

        &:hover {
          box-shadow: 5px 5px 5px 2px rgb(4, 2, 15);
        }

        p {
          color: aliceblue;
          font-size: 40px;
        }

        span {
          font-size: 40px;
        }

        img {
          width: 100px;
        }
      }
    }
    
  }
}
</style>
