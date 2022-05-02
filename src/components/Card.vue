<template>
  <div class="container">
    <input
      type="text"
      name="nome"
      value=""
      placeholder="Busque aqui seu pokemon"
    />
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
    <div v-if="pokeInfo" class="modal" @click="pokeInfo = null">
      <div class="modal_container">
        <p>Nome: {{ caseUp(pokeInfo) }}</p>
        <p>Altura: {{ pokeInfo.height * 2.25 }} CM</p>
        <p>Peso: {{ pokeInfo.weight }}</p>
      </div>
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
      modal: false,
    };
  },
  mounted() {
    axios
      .get("https://pokeapi-215911.firebaseapp.com/api/v2/pokemon?limit=151")
      .then((response) => {
        this.pokemons = response.data.results;
        this.modal = true;
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
          this.pokeInfo = response.data;

          window.scrollTo({
            top: 0,
            behavior: "smooth",
          });
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=VT323&display=swap");
.container {
  font-family: "vt323";

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
  .modal {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 1920px;
    padding: 80px;

    &::before {
      content: "";
      position: fixed;
      top: 0px;
      left: 0px;
      width: 100%;
      height: 100vh;
      background: rgba(0, 0, 0, 0.5);
    }
    .modal_container {
      position: relative;
      z-index: 1;
      background: rgb(17, 17, 101);
      padding: 25px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      border-radius: 15px;
      top: 0;
      bottom: 0;
      width: 500px;
    }

    p {
      font-size: 22px;
      color: aliceblue;
      margin-bottom: 15px;
    }
  }
  input {
    width: 570px;
    padding: 20px;
    border: 3px solid black;
    color: black;
    margin: 20px 350px;
  }
}
</style>
