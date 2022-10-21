<template>
  <p>Rreaction time: {{ result }} ms</p>
  <h2>{{ rank }}</h2>
</template>
<script>
export default {
  data() {
    return {
      rank: null,
    };
  },

  props: ["result"],
  mounted() {
    if (this.result < 300) return (this.rank = "Just like Vite...");
    if (this.result < 450) return (this.rank = "Ninja reflexes...");
    if (this.result > 650) return (this.rank = "Snail pace...");
  },
};
</script>
