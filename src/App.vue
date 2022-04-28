<template>
  <div id="app">
    <header>
      <img src="./assets/poke.webp" />
      <input
        type="text"
        name="nome"
        value=""
        placeholder="Busque aqui seu pokemon"
      />
    </header>
    <HelloWorld></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
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
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
}

header {
  margin: 0 auto;
  width: 1300px;
  padding-bottom: 50px;
}
</style>
