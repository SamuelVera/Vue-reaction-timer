<template>
  <h1>Ninja reaction timer</h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" />
</template>

<script>
/**Block to click component */
import Block from "./components/Block.component";
export default {
  name: "App",
  components: {
    Block,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
    };
  },
  methods: {
    /**Starts a new game */
    startGame() {
      if (!this.isPlaying) {
        //If a game isn't ongoing
        //A game begun
        this.isPlaying = true;
        //Set delay for button to appear
        this.delay = 1500 + 5000 * Math.random();
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
