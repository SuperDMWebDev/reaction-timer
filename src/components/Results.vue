<template>
  <p class="result-reactionTime">Reaction time = {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  data() {
    return {
      rank: "",
    };
  },
  props: ["score"],
  mounted() {
    if (this.score < 250) {
      this.rank = "fast";
    } else if (this.score < 400) {
      this.rank = "normal";
    } else {
      this.rank = "slow";
    }
  },
};
</script>
<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
