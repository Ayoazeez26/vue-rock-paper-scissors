<template>
  <div id="app" class="w-screen h-screen">
    <Game />
  </div>
</template>

<script>
import Game from "./components/Game.vue";

export default {
  name: "App",
  components: {
    Game,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap");
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Barlow Semi Condensed", sans-serif;
  background: radial-gradient(ellipse at top, #1f3756, #141539);
}
</style>
