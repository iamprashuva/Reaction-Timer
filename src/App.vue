<template>
  <div>
    <h1>Check Your Reaction Time</h1>
    <button v-on:click="start" :disabled="isPlaying">Play</button>
    <BlockPage v-if="isPlaying" :delay="delay" @end="endGame" />
    <ReactionResult v-if="showResults" :score="score" />
  </div>
</template>

<script>
import ReactionResult from "./components/ReactionResult.vue";
import BlockPage from "./components/BlockPage.vue";
export default {
  name: "App",
  components: {
    BlockPage,
    ReactionResult,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      (this.delay = 2000 + Math.random() * 6000), (this.isPlaying = true);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 100px;
}
button {
  padding: 10px;
  background-color: #85586f;
  color: #fff;
  width: 100px;
  font-size: 16px;
  border-radius: 4px;
  cursor: pointer;
  letter-spacing: 1px;
  border: none;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
