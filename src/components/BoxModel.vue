<template>
  <div class="box" v-if="showModal" @click="stopTimer()">
    <h3 class="text">Click me</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showModal: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
      this.showModal = false;
      console.log(this.reactionTime);
    },
  },
  mounted() {
    setTimeout(() => {
      this.startTimer();
      this.showModal = true;
    }, this.delay);
    console.log("Component mounted");
  },
  updated() {
    // this.showModal = false;
    console.log("component updated");
  },
};
</script>

<style>
.box {
  margin-top: 3rem;
  margin-left: 9rem;
  border-radius: 4px;
  background-color: rgb(52, 183, 1);
  height: 300px;
  width: 350px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.text {
  text-align: center;
}
</style>
