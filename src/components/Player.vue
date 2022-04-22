<template>
  <div class="player">id player : {{ greetings }}</div>
</template>

<script>
export default {
  name: "player",
  created: function() {
    this.greetings = this.player ? `Bonjour ${this.player} !` : "Pas de joueur";
  }
};
</script>

<style scoped></style>
