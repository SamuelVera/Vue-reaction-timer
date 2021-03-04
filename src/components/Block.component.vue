<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
    CLICK ME! FAST!
  </div>
</template>

<script>
export default {
  //Accepted props
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      //Interval to update reaction time
      startTime: null,
      reactionTime: 0,
    };
  },
  methods: {
    /**Starts the timer */
    startTimer() {
      //Set a starting time
      this.startTime = new Date();
    },
    /**Stops the timer */
    stopTimer() {
      /**Time of click of end timer */
      const endTime = new Date();
      //Calculation for reaction time
      this.reactionTime = endTime.getTime() - this.startTime.getTime();
      //Emit custom event for end game and pass custom data
      this.$emit("endgame", this.reactionTime);
    },
  },
  /**After the component has been mounted in the DOM */
  mounted() {
    /**Start a timeout based on the random delay given as prop */
    setTimeout(() => {
      //Show the block to be clicked
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  /**When the component data has been changed and re-rendered into the DOM */
  updated() {},
  /**When the component has been unmounted from the DOM */
  unmounted() {
    //Good for cleanup
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
