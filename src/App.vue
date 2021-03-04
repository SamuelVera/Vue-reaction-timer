<template>
  <h1>Ninja reaction timer</h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Results v-if="showResults" :score="score" />
  <Block v-if="isPlaying" :delay="delay" @endgame="onEndGame" />
</template>

<script>
/**Block to click component */
import Block from "./components/Block.component";
/**Results component */
import Results from "./components/Results.component";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      //Values of delay
      delay: null,
      //Score
      score: null,
      /**Show results */
      showResults: false,
    };
  },
  methods: {
    /**Starts a new game */
    startGame() {
      if (!this.isPlaying) {
        //If a game isn't ongoing
        //A game begun
        this.isPlaying = true;
        this.showResults = false;
        //Set delay for button to appear
        this.delay = 1500 + 5000 * Math.random();
      }
    },
    /**Event listener for the end of a game (accepts custom data) */
    onEndGame(reactionTime) {
      console.log(reactionTime);
      //Update score
      this.score = reactionTime;
      //End game
      this.isPlaying = false;
      this.showResults = true;
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
