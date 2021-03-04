<template>
  <div v-if="showBlock" class="block">
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
    };
  },
  /**After the component has been mounted in the DOM */
  mounted() {
    /**Start a timeout based on the random delay given as prop */
    setTimeout(() => {
      //Show the block to be clicked
      this.showBlock = true;
    }, this.delay);
  },
  /**When the component data has been changed and re-rendered into the DOM */
  updated() {
    console.log("Component updated");
  },
  /**When the component has been unmounted from the DOM */
  unmounted() {
    //Good for cleanup
    console.log("Component unmounted");
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
