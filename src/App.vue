<template>
  <div id="app">
    <header>
      <img src="./assets/poke.webp" />
    </header>
    <div class="container">
      <Card></Card>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";

export default {
  name: "App",
  created() {
    document.title = "Poke Alfa";
  },
  components: {
    Card,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  list-style: none;
  text-decoration: none;
}
#app {
  background: linear-gradient(to right, lightblue, darkblue);
  width: 100%;
  height: 100%;
  @media (max-width: 450px) {
    display: flex;
    flex-direction: column;
    // max-width: 390px;
    background: white;
    margin: 0 35px;
    width: 100%;
  }
  header {
    padding-bottom: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    @media (max-width: 450px) {
      position: relative;
      top: 0;
      left: 320px;
    }

    img {
      width: 700px;
      margin-bottom: 30px;
      margin-top: 20px;
      @media (max-width: 450px) {
        // margin: 0 120px;
        width: 360px;
      }
    }
  }
  .container {
    margin: 0 150px;
    // @media (max-width: 450px) {
    //   margin: 0 0;
    // }
  }
}
</style>
