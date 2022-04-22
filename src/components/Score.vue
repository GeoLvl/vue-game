<template>
  <div class="score">Votre score : {{ score }}</div>
</template>

<script>
export default {
  name: "score",
  data: function() {
    return {
      score: 0
    };
  },
  created: function() {
    this.score++;
  }
};
</script>

<style scoped></style>
