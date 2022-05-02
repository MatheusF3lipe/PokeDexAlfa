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

  header {
    padding-bottom: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    img {
      width: 700px;
      margin-bottom: 30px;
      margin-top: 20px;
    }
    
  }
  .container {
    margin: 0 150px;
  }
}
</style>
