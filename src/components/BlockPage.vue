<template>
  <div class="block" v-if="showblock" v-on:click="stopTimer">Click Me</div>
</template>
<script>
export default {
  name: "BlockPage",
  props: ["delay"],
  data() {
    return {
      showblock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
  mounted() {
    setTimeout(() => {
      (this.showblock = true), this.startTimer();
    }, this.delay);
  },
};
</script>
<style>
.block {
  width: 300px;
  border-radius: 10%;
  background-color: #ac7d88;
  color: #fff;
  text-align: center;
  padding: 100px 0px;
  margin: 20px 600px;
  font-size: 18px;
}
</style>
