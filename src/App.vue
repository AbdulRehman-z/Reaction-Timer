<template>
  <h1 class="text-2xl">XenonHunt Reaction Timer</h1>
  <button class="btn" @click="startPlaying()" :disabled="state">Play</button>
  <br />
  <BoxModel v-if="state" :delay="delay" @end="endGame" />
  <result v-if="showResults" :result="result" />
</template>

<script>
import BoxModel from "./components/BoxModel.vue";
import result from "./components/result.vue";
export default {
  data() {
    return {
      delay: null,
      state: false,
      result: 0,
      showResults: false,
    };
  },
  methods: {
    startPlaying() {
      this.delay = 2000 + Math.random() * 5000;
      this.state = true;
      this.showResults = false;
    },

    endGame(reactionTime) {
      console.log(reactionTime);
      this.result = reactionTime;
      this.showResults = true;
      this.state = false;
    },
  },
  components: { BoxModel, result },
};
</script>

<style scoped></style>
