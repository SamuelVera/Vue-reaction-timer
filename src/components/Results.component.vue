<template>
  <div class="result">
    <p>Your reaction time is: {{ score }} ms</p>
    <p
      class="quality"
      :class="{
        bad: score > 700,
        medium: score > 450 && score <= 700,
        fast: score <= 450,
      }"
    >
      You are a: {{ quality }}
    </p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      /**Quality of the score */
      quality: null,
    };
  },
  /**On component mounted */
  mounted() {
    this.quality =
      this.score > 700
        ? "Slowpoke"
        : this.score > 450 && this.score <= 700
        ? "Average"
        : "Ninja 🐱‍👤";
  },
};
</script>

<style></style>
