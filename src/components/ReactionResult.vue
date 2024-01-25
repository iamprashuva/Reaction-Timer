<template>
  <div class="result">
    <p>Reaction Time: {{ this.score }}ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>
<script>
export default {
  name: "ReactionResult",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Fingures";
    } else if (this.score < 500) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail pace...";
    }
  },
};
</script>
<style>
.result {
  font-family: Arial, Helvetica, sans-serif;
  letter-spacing: 0.5px;
}
.rank {
  color: #85586f;
  font-size: 18px;
  font-weight: bold;
}
</style>
